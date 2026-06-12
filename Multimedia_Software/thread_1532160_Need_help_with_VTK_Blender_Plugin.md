---
title: "Need help with VTK Blender Plugin"
date: 2010-07-16
forum: Multimedia Software
---

### Post by kikislater on 2010-07-16
Hi,

Can you help me to install it on Ubuntu Lucid 10.04 please ?
I put the VTKBlender.py under ~/.blender/scripts, trying to add this :

> VTK_ROOT = /usr/local/lib/python2.6/dist-packages
LIBRARY_OUTPUT_PATH = /usr/local/lib/python2.6/dist-packages
PATH_TO_VTKBlender_MODULE = ~/.blender/scripts
import sys
sys.path.append($VTK_ROOT)
sys.path.append(${LIBRARY_OUTPUT_PATH})
sys.path.append(${PATH_TO_VTKBlender_MODULE})
but it doesn't work !

Can you help me ?

Thanks
Sylvain

---

### Post by kikislater on 2010-07-20
up please !

---

### Post by kikislater on 2010-07-26
:-\"

---

### Post by SqRt7744 on 2010-07-28
Like it says on [http://www.ualberta.ca/AICT/RESEARCH/Vis/VTKBlender/index.html](http://www.ualberta.ca/AICT/RESEARCH/Vis/VTKBlender/index.html) you can check if your paths are correct this way:
start python and enter:
import sys
print sys.path
quit()

I think it's working for me, haven't really tried it. I did this:

in a terminal:
installed python-pyvtk and python-vtk
sudo aptitude install python-pyvtk python-vtk

then:
PYTHONPATH=/usr/share/python-support/python-pyvtk
PYTHONPATH=$PYTHONPATH:/home/peter/bin/python/
export PYTHONPATH

finally I started blender, and loaded the example file from the website, which seem to work.

hope that helps.

---

