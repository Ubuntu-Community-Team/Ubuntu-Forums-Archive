---
title: "Remote control woes..."
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by kmullinax on 2008-02-09
Hi all -
I am a complete n00b at linux and ubuntu, having just made the switch from windoze last week.  so far so good - i LOVE ubuntu so far.  
my last great hurdle is with the remote control.
i have an Origin AE X11 case with the VFD/IR by IRTrans.
i have found and followed the intructions on IRTrans' website and the various forum listings here and i have the IRServer running and booting up with the system.
performing a debug_code, the server recognizes my button presses from my logitech harmony remote (set up to emulate an MCE remote, since that's what i used with windoze), so when i press "play", the server knows i pressed play and shows me the correct code in the terminal window.
SO...  what do i do next??   :)

i don't have any interest in running MythTV, but i'd love to be able to control vlc, totem, amarok, etc.  is this possible?  i noticed that vlc has a LIRC plugin, so can i use that, or is there perhaps a piece of software that i need in order to associate the button-presses on the remote with commands in a particular program?

any advice would be GREATLY appreciated!   thanks!!

---

### Post by rich86 on 2008-02-13
This is a fairly good guide to the initial lirc setup: [http://www.g-loaded.eu/2006/01/10/how-to-configure-and-use-lirc/]("http://www.g-loaded.eu/2006/01/10/how-to-configure-and-use-lirc/")
And once its all set up this wiki has some good information about what specific commands are for various programs: [http://gentoo-wiki.com/HOWTO_LIRC#Enabling_software_support]("http://gentoo-wiki.com/HOWTO_LIRC#Enabling_software_support")

Hope that helps

---

