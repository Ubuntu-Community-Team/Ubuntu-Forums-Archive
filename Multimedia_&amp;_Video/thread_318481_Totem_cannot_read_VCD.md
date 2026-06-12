---
title: "Totem cannot read VCD"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by GwadaBreizh on 2006-12-14
Hello,

Totem can't read VCD (reading DVD is OK) :
[INDENT][[IMG]http://img133.imageshack.us/img133/6576/capturetotempz1.th.png[/IMG]](http://img133.imageshack.us/my.php?image=capturetotempz1.png)[/INDENT]
The message is in french, and the translation is something like that:
> There is no graft of entry to manage the site of this film 

I tried with mplayer, gxine and the problem is the same !

Have you ever seen this problem ?

Thanks for your help,

---

### Post by LDRoamer on 2006-12-22
I had the exact same problem here. I finally found a solution through a combination of internet searches and trial and error. I have no idea if this will work for you or anyone else but it is worth a shot. 

I can play a VCD if I open a terminal window and type

#mplayer vcd://2

I tried the following without success but one of these may work for someone else:

#mplayer vcd://
#mplayer vcd://1
#mplayer vcd://3

I saw post on here about modifying a configuration file with gconf but that solution did not work for me.   So far the only thing that works for me is starting from a command line in a terminal window.

---

### Post by rajeev1204 on 2006-12-23
hi

its quite simple

get rid of totem 

use gxine and dont autoplay .just select vcd or dvd from menu after starting gxine


regards

rajeev

---

### Post by mahiyar on 2006-12-27
Hi Rajiv, a big thank u. I have been trying for the past three hours to get some player to play at least my vcd's. I tried the default Movie player, Mplayer, VLC player and then I chanced upon this thread. Both the suggestion of LD Roamer of playing Mplayer form command line and yours of installing gxine worked. I'am very new to linux but I must say that people should not waste hours of getting a simple VCD to play, that is what makes people fleeback to windows.

---

### Post by legolas on 2007-01-09
I am using xine with a vcd, but when I press the vcd button on the graphic controller, it says there is no input plugin.  ???  Any thoughts?

---

### Post by hasannoori on 2007-09-11
That Post in ubuntuForum cannot help me,
because they wrote:
----------------------------
 "hi
  its quite simple 
  get rid of totem 
  use gxine and dont autoplay .just              
  select vcd or dvd from menu after starting gxine"
----------------------------------

But gexine give me the following message:
------------------------------
"hasan@edubuntu:~$ gxine
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect
to the socket?
gxine has suffered a fatal internal error.
To get a backtrace, run gxine in a debugger such as
gdb.
Then, when the error occurs:
  (gdb) thread apply all bt
gxine: error: Fatal error: Segmentation fault
hasan@edubuntu:~$

---

### Post by hasannoori on 2007-09-13
any idea!

---

### Post by jis on 2007-10-31
I suggest you make a bug report about gxine in launchpad.net.

---

