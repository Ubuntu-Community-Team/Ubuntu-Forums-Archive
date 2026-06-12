---
title: "I need help finishing install of lockersync3"
date: 2008-10-03
forum: Multimedia Software
---

### Post by djfick on 2008-10-03
Here is the readme I am dealing with:

MP3tunes LockerSync 3.0 for Linux
-------------------------------------------------

SYSTEM REQUIREMENTS:
 
In order to use LockerSync on Linux you will need:

Python available at [http://www.python.org](http://www.python.org)

PyQt4 available from Riverbank Software at [http://www.riverbankcomputing.co.uk/pyqt/](http://www.riverbankcomputing.co.uk/pyqt/)

Also required is the PIL library available from [http://www.pythonware.com/products/pil/](http://www.pythonware.com/products/pil/)

Not necessary, but recommended, is the Psyco library available at [http://psyco.sourceforge.net/](http://psyco.sourceforge.net/)

-------------------------------------------------

INSTALLATION INSTRUCTIONS:

If you're reading this README chances are you've already decompressed the archive, and have four files: 

README
global_imports.py
packaging.py
oboe_exe.py

You should always run LockerSync via the command: python oboe_exe.py (This is especially important in the case of desktop icons in desktop environments such as Gnome or KDE). 

Installing LockerSync on Ubuntu Linux: 

It is recommended that you first update your sources.list by typing: "sudo apt-get update" from the console

Then, you can install the required dependencies by typing:

sudo apt-get install python-pysqlite2 python-imaging python-qt4 python-qt4-gl python-qt4-sql python-psyco

If you get an error about python-psyco not being available you can skip it (this is not required). So, you 
would type this instead:

sudo apt-get install python-pysqlite2 python-imaging python-qt4 python-qt4-gl python-qt4-sql 

-------------------------------------------------

RUNNING LOCKERSYNC:

To run LockerSync on Linux you can go to the console and type: 

python oboe_exe.py



I have followed all steps, but when I try to run in the console I get this:

chris@chris-roaddog:~$ python oboe_exe.py
python: can't open file 'oboe_exe.py': [Errno 2] No such file or directory
chris@chris-roaddog:~$ 

please help a humble fool!

---

### Post by djfick on 2008-10-03
So no ideas?  Wrong forum?  Beuller?

---

### Post by cariboo on 2008-10-04
Try:

```
python ./oboe_exe.py
```

when you are in the /s3 directory. If you've installed the dependencies, it will work. I just tried it myself.

Jim

---

### Post by djfick on 2008-10-04
my problem might be that I have the ls3 folder on my desktop.  do i need to move it into the filesystem?  usr?  what's the best way to get the directory where it belongs?

I tried the above command and received same error:

chris@chris-roaddog:~$ cd Desktop
chris@chris-roaddog:~/Desktop$ python ./oboe_exe.py
python: can't open file './oboe_exe.py': [Errno 2] No such file or directory
chris@chris-roaddog:~/Desktop$

---

### Post by djfick on 2008-10-04
I'm banging my head on the desk...knowing there is something simple I'm forgetting.

---

### Post by Life On Mars on 2008-10-08
> **djfick said:**
> my problem might be that I have the ls3 folder on my desktop.  do i need to move it into the filesystem?  usr?  what's the best way to get the directory where it belongs?

I tried the above command and received same error:

chris@chris-roaddog:~$ cd Desktop
chris@chris-roaddog:~/Desktop$ python ./oboe_exe.py
python: can't open file './oboe_exe.py': [Errno 2] No such file or directory
chris@chris-roaddog:~/Desktop$

If the name of the folder that you extracted the lockersync3 download into is ls3 and it's on your desktop, try the following:

```
python Desktop/ls3/oboe_exe.py
```

I extracted my download into the auto-generated folder called oboe-3.0, so if you did the same the command for you would be:

```
python Desktop/oboe-3.0/oboe_exe.py
```

---

