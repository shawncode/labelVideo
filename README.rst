LabelVideo
========

LabelVideo is a graphical image annotation tool for video file.

It is forked from tzutalin/labelImg. 
It is written in Python and uses Qt for its graphical interface.

Annotations are saved as XML files in PASCAL VOC format, the format used
by `ImageNet <http://www.image-net.org/>`__.  Besdies, it also supports YOLO format

Installation
------------------

Same as tzutalin/labelImg

Build from source
~~~~~~~~~~~~~~~~~

Linux/Ubuntu/Mac requires at least `Python
2.6 <https://www.python.org/getit/>`__ and has been tested with `PyQt
4.8 <https://www.riverbankcomputing.com/software/pyqt/intro>`__.


Ubuntu Linux
^^^^^^^^^^^^
Python 2 + Qt4

.. code::

    sudo apt-get install pyqt4-dev-tools
    sudo pip install lxml
    make qt4py2
    python labelVideo.py

Python 3 + Qt5

.. code::

    sudo apt-get install pyqt5-dev-tools
    sudo pip3 install -r requirements/requirements-linux-python3.txt
    make qt5py3
    python3 labelVideo.py

macOS
^^^^
Python 2 + Qt4

.. code::

    brew install qt qt4
    brew install libxml2
    make qt4py2
    python labelVideo.py

Python 3 + Qt5 (Works on macOS High Sierra)

.. code::

    brew install qt  # will install qt-5.x.x
    brew install libxml2
    make qt5py3
    python3 labelVideo.py

    As a side note, if mssing pyrcc5 or lxml, try
    pip3 install pyqt5 lxml


**NEW** Python 3 Virtualenv + Binary
This avoids a lot of the QT / Python version issues,
and gives you a nice .app file with a new SVG Icon
in your /Applications folder. You can consider this script: build-tools/build-for-macos.sh

.. code::

    brew install python3
    pip install pipenv
    pipenv --three
    pipenv shell
    pip install py2app
    pip install PyQt5 lxml
    make qt5py3
    rm -rf build dist
    python setup.py py2app -A
    mv "dist/labelVideo.app" /Applications

Windows
^^^^^^^

Untested

Anaconda
^^^^^^^

Unsupported yet.

Get from PyPI
~~~~~~~~~~~~~~~~~

Unsupported yet.

Usage
-----

Steps (PascalVOC)
~~~~~

1. Build and launch using the instructions above.
2. Click 'Change default saved annotation folder' in Menu/File
3. Click 'Open File'
4. Click 'Create RectBox'
5. Click and release left mouse to select a region to annotate the rect
   box
6. You can use right mouse to drag the rect box to copy or move it

The annotation will be saved to the folder you specify.

You can refer to the below hotkeys to speed up your workflow.

Steps (YOLO)
~~~~~

1. In ``data/predefined_classes.txt`` define the list of classes that will be used for your training.

2. Build and launch using the instructions above.

3. Right below "Save" button in toolbar, click "PascalVOC" button to switch to YOLO format.

4. You may use OpenFile to process video file. When finished with single frame, click save.

A txt file of yolo format will be saved in the same folder as your filename+frameNo with same name. A file named "classes.txt" is saved to that folder too. "classes.txt" defines the list of class names that your yolo label refers to.

Note:

- You shouldn't use "default class" function when saving to YOLO format, it will not be referred.

- When saving as YOLO format, "difficult" flag is discarded.

Create pre-defined classes
~~~~~~~~~~~~~~~~~~~~~~~~~~

You can edit the
`data/predefined\_classes.txt <https://github.com/tzutalin/labelImg/blob/master/data/predefined_classes.txt>`__
to load pre-defined classes

Hotkeys
~~~~~~~

+------------+--------------------------------------------+
| Ctrl + r   | Change the default annotation target dir   |
+------------+--------------------------------------------+
| Ctrl + s   | Save                                       |
+------------+--------------------------------------------+
| Ctrl + d   | Copy the current label and rect box        |
+------------+--------------------------------------------+
| Space      | Flag the current image as verified         |
+------------+--------------------------------------------+
| w          | Create a rect box                          |
+------------+--------------------------------------------+
| Ctrl + .   | Next frame                                 |
+------------+--------------------------------------------+
| Ctrl + ,   | Previous frame                             |
+------------+--------------------------------------------+
| del        | Delete the selected rect box               |
+------------+--------------------------------------------+
| Ctrl++     | Zoom in                                    |
+------------+--------------------------------------------+
| Ctrl--     | Zoom out                                   |
+------------+--------------------------------------------+
| ↑→↓←       | Keyboard arrows to move selected rect box  |
+------------+--------------------------------------------+

How to contribute
~~~~~~~~~~~~~~~~~

Send a pull request

License
~~~~~~~
`Free software: MIT license <https://github.com/shawncode/labelVideo/blob/master/LICENSE>`_

Citation: Shawncode. LabelVideo. Git code (2018). https://github.com/shawncode/labelVideo

Related
~~~~~~~

1. `ImageNet Utils <https://github.com/tzutalin/ImageNet_Utils>`__ to
   download image, create a label text for machine learning, etc
2. `Generating the PASCAL VOC TFRecord files <https://github.com/tensorflow/models/blob/4f32535fe7040bb1e429ad0e3c948a492a89482d/research/object_detection/g3doc/preparing_inputs.md#generating-the-pascal-voc-tfrecord-files>`__
3. `App Icon based on Icon by Nick Roach (GPL)` <https://www.elegantthemes.com/> <https://www.iconfinder.com/icons/1054978/shop_tag_icon> __

