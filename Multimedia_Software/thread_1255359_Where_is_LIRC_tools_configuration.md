---
title: "Where is LIRC tools configuration?"
date: 2009-09-01
forum: Multimedia Software
---

### Post by azemerov on 2009-09-01
Hi,
I use Ubuntu 8.04 (hardy).
After installation of lirc package I've got a configuration dialog and configured lirc to use "Windows Media Center Remote (new)". To my surprise it started to work immediately! I can move cursor in mc running in console, I can move mouse in X, I also have some control in mplayer.
But I don't understand where bidning between lirc commands and applications is configured. I don't have .lircrc file in my home directory, nor lircrc file in /etc/lirc directory. I searched for a *lircrc* files through my file system and found nothing relevant.
What I really need is to extend already existing binding. Also I want to understand how it works. Lirc documentation gives only two locations - ~/.lircrc and /etc/lirc/lircrc
Thank you

---

### Post by azemerov on 2009-09-01
BTW, another strange symptom of my situation - when I run irw it exists immediately, without any message. It looks like lirc socket is unavailable. But it still works somehow!

---

### Post by siren09 on 2009-09-02
I think you'll find that the remote is working through the HAL rather than through LIRC. Do a search for remotes and lshal and see what you find.  You can disable it in the lirc.fdi file, and you'll probably find the remote stops working.  I'm working through issues with my remote (and am a newbie so won't be of much help to you, I'm afraid), but I had the same experience so thought I would share.

---

### Post by azemerov on 2009-09-02
I don't believe remote control can work directly through HAL without LIRC. In any case, lshal doesn't return any mention of lirc. Also, I couldn't find lirc.fdi file on my machine. BTW, what is lirc.fdi file about?

---

### Post by azemerov on 2009-09-04
The answer is very simple. In my case LIRC was not working at all! Every response from remote I had was a result of simple keyboard key pressing. The secret is - my remote was recognized by OS as an USB keyboard and USB mouse.
The "lsusb" command shows it as "Chaplet Systems, Inc." 
I don't know how original Microsoft remote control behaves without LIRC (don't have one). My one was bought on eBay and looks different. On the bottom it has "PC remote" logo. 
[IMG]http://www.uauctionsource.com/picture/SKU004156_0.jpg[/IMG]

I don't know right now how to disable the IR receiver to be recognized as a keyboard and if it's supported by LIRC, but it is a different question. For a while I happy to have a "remote micro keyboard", while some mappings are missing. So I definitely can recommend this remote to anyone who doesn't want to install/configure LIRC.

---

### Post by sem7ex on 2009-10-17
Hi there,

i have the same problem with the same remote. did you manage to disable the os to recognize it as a keyboard or use it with lirc?!

thanx

---

### Post by RichardK3 on 2009-10-18
I recently bought this remote also.  Like others, I haven't been able to make it work with lirc.

In theory, it could be used with Mythtv by using the numlock key and sending alphabetic keystrokes, e.g. "P" for "pause".  I've experimented with having a separate learning remote learn essential commands.  I.e., I would assign the "pause" button on the remote to send a "P".  However, the key will send 7, p, q, r, or s, depending on how many times it is pressed.  So it's pretty easy to send the wrong command.

I bought this remote as an MCE-compatible remote, but obviously it doesn't really simulate an MCE remote.  

I'd love to hear anyone's ideas on how to make this work with Mythtv.  But I'm beginning to think I need to buy a different product.

---

### Post by nite_man on 2010-01-29
Did somebody manage to configure that remote with LIRC? My friend has the same remote and the same problem. It's recognized by system as USB keyboard and mouse.

---

### Post by pejcao on 2010-06-21
I'm looking toward this remote. Anyone tryed [[COLOR="Red"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=805876&highlight=pc-remote+lirc") guide with the "pc-remote" one? Any progress?

---

### Post by pejcao on 2010-06-24
Answering myself: 
I did follow that guide (the udev portion) and my remote works like any other LIRC remote (not a keyboard).

Use /usr/share/lirc/extras/more_remotes/generic/devinput.conf as /etc/lirc/lircd.conf and as soon as irexec (and/or irxevent) starts up, the remote starts taking ir signals (avoiding being a keyboard).

I use the yellow button to enter tvtime mode (change channels, volume, fullscreen, etc) instead of going to tty4 via its hardwired Ctrl+Alt+F4.

Now the mouse stoped working. I'll try to fix it via lircmd or some udev voodoo.

Cheers!

---

