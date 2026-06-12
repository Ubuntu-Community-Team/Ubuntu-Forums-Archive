---
title: "Problems Listen"
date: 2009-06-19
forum: Multimedia Software
---

### Post by jolly.roger on 2009-06-19
Hey,
I'm having a problem with Listen on Ubuntu 8.10. When I'm trying to start it nothing happens. In Terminal i got following message:

```
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 36, in <module>
    import gnome,gnome.ui
ImportError: No module named gnome
```Care to help anyone? Just bare in mind that my knowledge of Linux is basic (at most). Just starting to explore it...

                                 In Listen list of dependencies PyGTK 2.6 is mentioned. When I try to install it, after executing "configure" I got message that gtk.glide won't be build. Can't this be source of my problem? If yes how I can solve it?
 
Jolly Roger


EDIT:
  	 	 	 	 	 	  

Ok, some more information. When I'm trying to compile Listen 0.6.2 ('make') I'm getting following output:
 

```
Checking for Python... /usr/local/bin/python 
 Checking Python version: 2.6 
 Checking for PyGTK >= 2.6: found 
 Checking for pyGTK-devel >= 2.6: found 
 Checking for Xlib: found 
 Checking for python-webkit: not found 
 Try pygtkmozembed instead: 
 not found 
 Listen require python-webkit or gnome-python-extras. 
 	(http://code.google.com/p/pywebkitgtk/ or http://ftp.gnome.org/pub/GNOME/sources/gnome-python-extras) 
 make: *** [check] Error 1 
 
```

So, logic indicated to obtain a copy of python-webkit and install it. And here I got another problem:
 

```
checking for DEPS... configure: error: Package requirements (libxslt, 
                   pygtk-2.0) were not met: 
  
 No package 'libxslt' found 
  
 Consider adjusting the PKG_CONFIG_PATH environment variable if you 
 installed software in a non-standard prefix. 
  
 Alternatively, you may set the environment variables DEPS_CFLAGS 
 and DEPS_LIBS to avoid the need to call pkg-config. 
 See the pkg-config man page for more details. 
 
```

And with this I'm completely lost.... Could someone explain it in plain english for me?
 
Jolly Roger

---

