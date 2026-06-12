---
title: "Screen Resolution in VMWare"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by mario.rimann on 2006-06-15
Hi folks

I'm working with VMWare. WinXP is the Host, Ubuntu 6.06 the Guest. Installation worked fine, except one little problem: I can't get the screen resolution set to a higher resolution than 1024x768. That's disturbing, as my Notebook can handle 1400x1050.

What I did:
- Installed Ubuntu from the ISO file
- Installed the VMWare Tools for my VMWare Workstation 5.5.1 (while running X - don't know if this matters). I had to compile it. There were no error messages.
- It's not possible to select higher resolutions in the Gnome Menu Settings, so I tried to change xorg.conf. Added "1400x1050" in front of "1024x768" on all depths. No change after restarting X.
- I reconfigured X by using "sudo dpkg-reconfigure xserver-xorg" command. Nothing changed.

Has anyone of you a hot tip on how to solve this problem? Any help is very appreciated!

Greetings,
Mario

---

### Post by scxtt on 2006-06-15
2 things:

1. your ubuntu guest will use a default video driver, most likely vesa ( which in some cases might not support a resolution higher than 1024x768 ) ...
2. the guest OS isn't going to use your native video hardware - it emulates its own video hardware ...

---

### Post by mario.rimann on 2006-06-15
I think the X-Server is using the right driver (vmware). That's the module I selected while reconfiguring the X-Server.

In the Xorg.log file, I can see that it probes all modes when starting. But on the 1400x1050, it tells me "HSync out of range" - and goes to the next mode.

---

### Post by scxtt on 2006-06-15
could it be a (virtual) "monitor" issue?  see if your /etc/X11/xorg.conf makes use of a HSync definition ...

---

### Post by edoardo on 2006-06-15
[QUOTE=mario.rimann]I think the X-Server is using the right driver (vmware). That's the module I selected while reconfiguring the X-Server.

In the Xorg.log file, I can see that it probes all modes when starting. But on the 1400x1050, it tells me "HSync out of range" - and goes to the next mode.[/QUOTE]

here is my xorg.conf
with plenty of modes for resizing the guest window.

note that i use the vmware mouse driver as well
somewhere (either vmware or ubuntu forums I found a post to the Xorg7 vmware video and mouse driver and those are the one i'm using with dapper guest)

HTH 
Edoardo

---

### Post by tiddlygoose on 2006-06-16
mario.rimann - How did you get the VMWare tools to install correctly? I also had to compile but I'm not sure it works right as it never releases the mouse when I try to go to Windows. I have to hit the ctrl-alt key combo to get it to release. Help!

---

### Post by mario.rimann on 2006-06-16
[QUOTE=tiddlygoose]mario.rimann - How did you get the VMWare tools to install correctly? I also had to compile but I'm not sure it works right as it never releases the mouse when I try to go to Windows. I have to hit the ctrl-alt key combo to get it to release. Help![/QUOTE]

Hi tiddlygoose
You need to start the vmware-toolbox (it's under /usr/bin/vmware-toolbox). I made it an application starter in my panel. Once per day (after shutdown/reboot) I start the toolbox, and minimize it.

You need also to run the toolbox for usb memory sticks to get mounted. With running toolbox it works without problems!

Greetings,
Mario

---

### Post by edoardo on 2006-06-16
[QUOTE=tiddlygoose]mario.rimann - How did you get the VMWare tools to install correctly? I also had to compile but I'm not sure it works right as it never releases the mouse when I try to go to Windows. I have to hit the ctrl-alt key combo to get it to release. Help![/QUOTE]

vmware tools comiple - this means you'll get the kernel optimized  support for network and access to the host folder.

the mouse behavior that we all want is given by the vmware mouse driver.
the vmware tools install fails to recognize xorg 7
you just have to find the mouse driver in the tools
copy to where your x11 input drivers are
edit the xorg.conf to use it

if you search the vmware newsgroup someone posted xorg7 drivers
in the tools you only find drivers up to 6.8 (which woirk fine anyway)

if you look at my xorg,xonf posted in this thread
there i pasted the additional tons of modelines that the vmware script - when was working with xorg 6.7/6.8 was adding to the file automagically.

---

### Post by MTZeon on 2006-11-17
Just follow this and you'll be set to go :)

[http://www.ubuntuforums.org/showthread.php?t=300968&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=300968&highlight=vmware)

---

