---
title: "Gimp 2.7 and Python [ ImportError: No module named gimp ]"
date: 2010-03-02
forum: Multimedia Software
---

### Post by LepeKaname on 2010-03-02
If you had Gimp 2.6 (with **gimp-plugin-registry** installed) and installed Gimp 2.7 to try its new goodies, but *Layer Effects* are not showing, and when executing "gimp" from console you get these *nasty* errors:

```
This is a development version of GIMP.  Debug messages may appear here.

gimp-user-install: migrating from /home/user/.gimp-2.6
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/layerfx.py", line 23, in <module>
    import gimp, gimpplugin, math
ImportError: No module named gimp

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/palette-to-gradient.py", line 16, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/colorxhtml.py", line 24, in <module>
    import gimp
ImportError: No module named gimp

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/palette-offset.py", line 16, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
GIMP-Error: Calling error for procedure 'gimp-plugin-help-register':
Procedure 'gimp-plugin-help-register' has been called with value '(null)' for argument 'domain-uri' (#2, type gchararray). This value is out of range.

Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/btn4ws.py", line 33, in <module>
    import gimp, gimpplugin, gimpui, gimpcolor
ImportError: No module named gimp

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
 mapped '<Toolbox>/File/Acquire/XSane/Device dialog...' to '<Image>/File/Create/Acquire/XSane/Device dialog...'
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/palette-sort.py", line 16, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/file-openraster.py", line 16, in <module>
    from gimpfu import *
(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
 mapped '<Toolbox>/Xtns/Batch/Batch Process...' to '<Image>/Filters/Extensions/Batch/Batch Process...'
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/foggify.py", line 19, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/cmyk-tiff-2-cmyk-pdf.py", line 13, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/text-brush.py", line 20, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/contactsheet.py", line 25, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error

(file-uri:24512): GLib-WARNING **: g_set_prgname() called multiple times
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/python-eval.py", line 19, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/python-console.py", line 19, in <module>
    from gimpfu import *
ImportError: No module named gimpfu

(gimp:24350): LibGimpBase-WARNING **: gimp: gimp_wire_read(): error
 mapped '<Toolbox>/Xtns/Misc' to '<Image>/File/Create/Misc'

```

The solution is to download the [_[COLOR="DarkRed"].deb file from 2.6 version[/COLOR]_]("http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/"), which may be: **gimp_2.6.8-2ubuntu1_i386.deb** or **_amd64** (depending on your system).

Then uncompress it in a temporally folder (do not install). And uncompress **data.tar.gz**.

Move **usr/lib/gimp/2.0/python** directory (and contents of course) to its respective location (/usr/lib/gimp/2.0/).

[COLOR="Green"]**NOTE:**[/COLOR] If you haven't install the 2.7 version yet... **BEFORE** upgrading, backup "python" directory and then just restore it after installing 2.7.

Start it again and Enjoy :guitar:

---

### Post by revoltism on 2010-03-17
Thanks pal. It worked great!

---

### Post by eamusic on 2010-03-18
Muchas Gracias.

Me fue útil 100% :popcorn:

---

### Post by petejk on 2010-04-16
Worked a treat!

Thanks,
Pete

---

### Post by xrecar on 2010-05-11
Works like a charm! Thank you.

---

### Post by AlexDS on 2010-07-14
I doesn't work for me :( even though i've done everything you say :(

---

### Post by alexan on 2011-08-20
Same issue on Natty using mrw-gimp-svn ppa: proposed fix don't work <_<

---

### Post by verybadidea on 2012-12-23
This does not help, now it outputs:

```
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/plug-ins/text-brush.py", line 20, in <module>
    from gimpfu import *
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 102, in <module>
    PF_REGION      = PDB_REGION
NameError: name 'PDB_REGION' is not defined
...

```

---

### Post by overdrank on 2012-12-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

