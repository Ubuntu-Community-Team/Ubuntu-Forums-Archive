---
title: "&quot;Install.py&quot; is a no-go"
date: 2010-11-22
forum: Multimedia Software
---

### Post by ShinChan01 on 2010-11-22
I'm trying to get Thin Liquid Film operating on my computer (10.04). I'm getting blocked at the last step of installation:


> 
*************************************
      installing thinliquidfilm
*************************************


-------------------------
Checking dependencies ...
-------------------------

pyqt is present

ffmpeg is present

ffmpeg supports xvid

ffmpeg supports h264

using bash as shell

libgpod python bindings are present

mplayer is present

konqueror is present

--------------------------------------------
Checking permissions for install process ...
--------------------------------------------

Permissions OK

------------------------------
Clearing old installations ...
------------------------------
Removing /usr/local/thinliquidfilm directory

Old installations cleared

---------------------------------------------------
Copying /root to /usr/local ...
Traceback (most recent call last):
  File "/home/joseph/Downloads/thinliquidfilm/install.py", line 119, in <module>
    shutil.copytree(current_directory,destination_directory)
  File "/usr/lib/python2.6/shutil.py", line 177, in copytree
    raise Error, errors
shutil.Error: [('/root/.pulse/c848cbcd6524ee7178b1a4464b51ed62-runtime', '/usr/local/thinliquidfilm/.pulse/c848cbcd6524ee7178b1a4464b51ed62-runtime', "[Errno 2] No such file or directory: '/root/.pulse/c848cbcd6524ee7178b1a4464b51ed62-runtime'")]I'm lost, and a newb. Any help?

---

