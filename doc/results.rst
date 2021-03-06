Simulation results processing
=============================

Results form Sailfish simulations can saved to disk for processing in external
applications or visualized in real-time.  These options are not exclusive, so
concurrent visualization and data saving is fully supported.

Data output
-----------

Sailfish supports a number of output data formats.  The data format is selected
using the ``--output_format`` command line option, which can take one of the
values listed in the "Parameter name" column below:

============= ============== =======================
Data format   Parameter name Required Python modules
============= ============== =======================
VTK           vtk            tvtk
numpy archive npy            numpy
MatLab array  mat            scipy
============= ============== =======================

In all modes, the name of the output file is specified using the ``--output`` command
line option.  In the ``vtk``, ``npy`` and ``mat`` modes, multiple files are generated,
each containing the state of the simulation at a specific iteration.  The file names
are generated by appending the iteration number to the base name provided via the
``--output`` option, e.g. if ``--output=poiseuille`` is used, ``poiseuille.0.00400.npz``
will contain data for the 400th iteration.

Data visualization
------------------

Sailfish supports on-line data visualization regardless of whether any results are
written out to files on disk.  The visualization module is disabled by default and
can be turned on via ``--mode=visualization``.

Visualization of 2D data
^^^^^^^^^^^^^^^^^^^^^^^^

2D simulations can be monitored using an interactive pygame-based interface.
The interface supports a number of color maps, which can be changed interactively (see below).

The initial size of the visualization window can be controlled with command line parameters.
One can specify its size explicitly using the ``--scr_w`` and ``--scr_h`` options
to set the width and height, respectively.  Alternatively, the ``--scr_scale`` option can
be used to make the window dimensions directly proportional to those of the lattice, e.g.
if ``--scr_scale=3`` is used the window will be 3 times larger than the lattice and each
lattice site will be visualized as a 3x3 square.

The visualization module can be controlled from the keyboard, and the following
keys are defined:

=====  ============================================================================================
``-``  previous scalar field
``=``  next scalar field
``[``  previous color map
``]``  next color map
``j``  previous subdomain
``k``  next subdomain
``i``  toggle visibility of text info about the state of the simulation (MLUPS, iteration etc.)
``q``  quit the simulation
``s``  take a screenshot
=====  ============================================================================================
