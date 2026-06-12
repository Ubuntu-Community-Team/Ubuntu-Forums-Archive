---
title: "ARRRGH!!!...Gimp 2.7.3 won't start. =("
date: 2011-09-25
forum: Multimedia Software
---

### Post by Truckerpunk on 2011-09-25
I've been trying to upgrade to gimp 2.7.3, on ubuntu 11.04, for a while now.. And it always fails to start. (I know it's an development version, but people seems to be able to run it).

I add this PPA: ppa:matthaeus123/mrw-gimp-svn

And then install gimp form synaptic or terminal.

When I start the application this is what I get (warning. loads of errors):

> truckerpunk@truckerpunk-System:~$ gimp
This is a development version of GIMP.  Debug messages may appear here.

GIMP-Error: Failed to load data:

Fatal parse error in palette file '/home/truckerpunk/.gimp-2.7/palettes/color_wheel-2-rgb.aco': Missing magic header.

GIMP-Error: Failed to load data:

Fatal parse error in palette file '/home/truckerpunk/.gimp-2.7/palettes/color_wheel-2-cmyk.aco': Missing magic header.


(gimp:8885): Gimp-Widgets-CRITICAL **: gimp_device_info_set_device: assertion `(info->device == NULL && GDK_IS_DEVICE (device)) || (GDK_IS_DEVICE (info->device) && device == NULL)' failed
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/palette-sort.py", line 16, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/colorxhtml.py", line 24, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/text-brush.py", line 20, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/foggify.py", line 19, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/palette-offset.py", line 16, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/py-slice.py", line 30, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/file-openraster.py", line 16, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/python-console.py", line 19, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/palette-to-gradient.py", line 16, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/python-eval.py", line 19, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 76, in <module>
    import gimp
ImportError: /usr/lib/gimp/2.0/python/gimp.so: undefined symbol: PyGimpItem_Type

(gimp:8885): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
 mapped '<Toolbox>/Xtns/Misc/Labels/CD label...' to '<Image>/File/Create/Misc/Labels/CD label...'
 mapped '<Toolbox>/Xtns/Misc/Labels/Rect label...' to '<Image>/File/Create/Misc/Labels/Rect label...'
gimp: fatal error: Segmentation fault
gimp (pid:8885): [E]xit, [H]alt, show [S]tack trace or [P]roceed: p

(script-fu:8900): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error

 

No matter what I press the program fails... 

Any help is appreciated.

Truckerpunk

---

### Post by searchfgold6789 on 2011-09-25
Wrong PPA.
```
*http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu lucid main*
```

---

### Post by searchfgold6789 on 2011-09-25
You can also try installing from source, or just grabbing the source and [making a deb file from it]("http://ubuntuforums.org/showthread.php?t=825560").

---

### Post by Truckerpunk on 2011-09-25
Looks like the ppa you suggested is for Lucid... I'm on Natty. Does matter?

Thanks for the fast reply

---

### Post by Truckerpunk on 2011-09-25
seems to be a new problem now... Looks like gimp 2.7.3 depends on libpoppler-glib4, but I have a new version installed on my system, libpoppler-glib5. And I can't manage to install libpoppler-glib4... Used so much time trying to get this running... I think I'll just have to wait for Gimp 2.8.. =(

---

### Post by Truckerpunk on 2011-09-25
Yay!! I got it working! Don't really know what the problem was before...
used; 

sudo apt-add-repository ppa:matthaeus123/mrw-gimp-svn

sudo apt-get update

sudo apt-get install gimp

after a reboot of my system. (I'm pretty sure it's the same ppa as I used in the 1st post, something is strange here. Maybe they fixed it during the couple of hours  used trying to get it to run?)

---

### Post by searchfgold6789 on 2011-09-26
Yeah, this somewhat reeks of a bug fix.
Glad you got it working.
 - search

---

