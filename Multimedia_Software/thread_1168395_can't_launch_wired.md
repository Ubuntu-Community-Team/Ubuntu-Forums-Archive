---
title: "can't launch wired"
date: 2009-05-24
forum: Multimedia Software
---

### Post by logos34 on 2009-05-24
I compiled it ok...But I get this error trying to start it up:

> $ wired
[COLOR="Red"]wired: error while loading shared libraries: libWiredWidgets.so: cannot open shared object file: No such file or directory[/COLOR]

libWiredWidgets.so is in /usr/local/lib.  So then I check the [sourceforge page]("http://wired.sourceforge.net/index.php?option=com_content&task=view&id=30&Itemid=25"):

  >  Launch Part :
          If a simple "wired" doesn't work, you have to adapt your environment with your "--prefix=directory" variable.
          If you don't know what is it, the default is the directory /usr/local/.
 
          [COLOR="Blue"]If you have an error like this : 
           bash: wired: command not found
 
          or like this :
           [COLOR="Red"]/usr/local/bin/wired: error while loading shared libraries: libWiredWidgets.so.0: cannot open shared object file:
            No such file or directory[/COLOR]
 
          You need to add in your ~/.bashrc :
           For first error :
           PATH=/usr/local/bin:$PATH
 
           For second error :
           LD_LIBRARY_PATH=/usr/local/lib/:$LD_LIBRARY_PATH
 
        
         After all modifications in .bashrc, you need to reload it with "source ~/.bashrc" [/COLOR]

So I add add 

LD_LIBRARY_PATH=/usr/local/lib/:$LD_LIBRARY_PATH

to bottom of .bashrc and run 

source ~./bashrc

Same error.

What to do next?

---

### Post by logos34 on 2009-05-24
SOLVED:

in .bashrc, not this:

> LD_LIBRARY_PATH=/usr/local/lib/:$LD_LIBRARY_PATH

but this:
> 
[COLOR="Red"]export [/COLOR]LD_LIBRARY_PATH=/usr/local/lib/:$LD_LIBRARY_PATH

---

