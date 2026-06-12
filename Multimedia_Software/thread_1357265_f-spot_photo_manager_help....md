---
title: "f-spot photo manager help..."
date: 2009-12-17
forum: Multimedia Software
---

### Post by s4n3j4v13r on 2009-12-17
can someone help me this is what i get when i run f-spot in the terminal and when i run it thru apps/graphics/f-spot it tries to open up then it close right back up .. help.. thanks in advance


[Info 22:43:01.373] Initializing DBus
[Info 22:43:01.534] Initializing Mono.Addins
[Info 22:43:01.771] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:6607): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info 22:43:03.040] Starting BeagleService
[Info 22:43:03.066] Hack for gnome-settings-daemon engaged

(f-spot:6607): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial 2031 error_code 11 request_code 53 minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by s4n3j4v13r on 2009-12-18
can anyone help???

---

### Post by Lars Noodén on 2009-12-18
There are some inherent technical problems with that one.  
You might enjoy trying some of the others:

Solang
[https://savannah.nongnu.org/projects/solang/](https://savannah.nongnu.org/projects/solang/)

Digikam
[http://www.digikam.org/](http://www.digikam.org/)

Fotoxx (available in lucid, maybe soon in backports)
[http://kornelix.squarespace.com/fotoxx/](http://kornelix.squarespace.com/fotoxx/)

jBrout (available outside ubuntu repositories)
[http://jbrout.manatlan.com/](http://jbrout.manatlan.com/)

---

### Post by s4n3j4v13r on 2009-12-19
thanks for the help lar's i just went ahead and went with picasa it works pretty well

---

### Post by Lars Noodén on 2009-12-20
@ s4n3j4v13r : Picasa, as you've noticed, is not available for Linux and must be run via WINE.  In addition, it does not support the graphics standard and uses DirectX instead.  Any gain of DirectX, non-standard, over OpenGL, standard and established, ultimately reduces the options for graphics in Linux.  Also, the linux-based digital photo tools benefit from a larger user base.  It's a case of voting with your feet, so to speak.  

I'd recommend again taking a look at one of the linux-based photo management tools, especially [solang](apt://solang) or [digikam](apt://digikam).  If they suck, then that's how it is.  If they are good, then you have gained an advantage.  But you can't know till you try.

---

### Post by vanadium on 2009-12-20
[quote=Lars Noodén]There are some inherent technical problems with that one. [/quote]
Could you tell something more about this?

I am considering to use a photo management application. The reason I did not start using f-spot is that the slide show function has a fade in/out effect that 1) you can't seem to turn off (I like such effect, but you should be able to disable that) and 2) it is jerky on my laptop (hence unuseable).

I will explore some of the alternative options you mention.

---

