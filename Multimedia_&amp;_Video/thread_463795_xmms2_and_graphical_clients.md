---
title: "xmms2 and graphical clients"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by joekarl on 2007-06-04
Hi all.

I have d'led and compiled XMMS2 for the purposes of seeing whether I will use it in Ubuntu, and have got as far as using the command line. When I go to use any of the graphical clients listed for use by XMMS2, they all return the message ImportError: No module named xmmsclient.

Can anybody shed any light on what I have to do in order to get them to work?

Cheers,

Joseph.

---

### Post by Earthwormzim on 2007-10-16
I've looked at trying to install XMMS2 as well.  I do love XMMS, and I've seen many screenshots of XMMS2 with graphical clients, and they look amazing!  Although I know how to use the command line somewhat well, I don't particularly like the idea of using it to play music...and getting a graphical client to work with XMMS2 looks confusing as hell (looking at the XMMS2 website's instructions)...heh...even after reading the "getting started" / "quick start" sections, I still don't even know where to start!

So, my question is: does anyone know of a simple, step-by-step tutorial on how to get XMMS2 up and running with a graphical client?

---

### Post by erthian on 2007-10-20
try

 sudo apt-get install gxmms2


then run gxmms2

lemme know if this is what your looking for.

---

### Post by fenian on 2007-10-22
Run the command...

> sudo gedit /etc/ld.so.conf

add this line to the file that opens...

> /usr/local/lib

run the command...

> sudo ldconfig

---

### Post by Earthwormzim on 2007-10-22
I just installed Gutsy on my desktop PC, and xmms2 was actually in the repositories in Synaptic...so, it installed with the click of a button!  Then, I installed gxmms2, like you said.  I then launched xmms2, and then launched gxmms2...and everything seems to have worked!  Right now, I'm currently adding/scanning my library...we'll see how it works when it is done.

The only drawback to xmms2 that I can see is that it does not support crossfade, currently.
:(

---

### Post by clapper65 on 2007-10-22
I loaded gxmms2 from gutsy and tried to get it to start with StreamTuner like xmms does but I get an error saying xmmsd is not running.  What package am I missing?  XMMS works fine for what I need, but I thought I'd give xmms2 a shot.  Is it worth using xmms2 to listen to Internet radio?

---

### Post by Earthwormzim on 2007-10-22
Sounds like you are missing xmms2.  Look in Synaptic for xmms2.  Gxmms2 can't run without xmms2 (from what I can gather).  So, after you install xmms2, launch it by typing "xmms2" in the application launcher.  Then, launch gxmms2 by typing "gxmms2" in the application launcher (you can also launch them from the command line).

Also...when you look for xmms2 in Synaptic...you might see a long list of xmms2 plugins.  You might wanna check to see if the specific plug-in you are looking for is in the list (I'm not sure how to do plug-ins, yet...you might have to do some command line stuff to configure it / get it running...of course, this is just speculation on my part).

Oh, and btw...xmms2+gxmms2 is working great for me!

---

