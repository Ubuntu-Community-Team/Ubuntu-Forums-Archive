---
title: "Remote not working"
date: 2008-06-02
forum: Mythbuntu
---

### Post by linedpaper on 2008-06-02
I just switched from Mythdora 4 and seem to be having trouble getting my remote to work.  I have the Radio Shack 15-2116 remote and selected it during the setup process (and have tried again), yet it isn't working.  IR Receiver is the one built into to my PVR-350.  I am also using one serial port (ttyS1) for the usb connection to my directv box.  Upon trying /usr/bin/irw I get not output when pressing buttons on the remote.  Any ideas?

---

### Post by linedpaper on 2008-06-03
Nobody has run into a problem where their remote won't work?  I just reinstalled as it was a fresh install anyway and it still won't work!  I'm not getting anything, and if nobody knows how to get the remote working, I think I'm going to have to switch back to Mythdora, which makes me a bit sad as Ubuntu is my distro of choice for all my computers.  The only thing I can think of is to recompile lirc outside of mythbuntu, but I don't want to break a bunch of stuff doing that!  The only out of the ordinary item I have is the USB>Serial connection for my directv STB, which is my guess as to what is interfering, I just don't have enough experience with serial + linux.  I am going to switch back to Mythdora after work today unless anyone has suggestions before then.  Don't mean to sound bitter in this post because I'm not, I'm just pissed I can't get the damn thing to work, never run into issues like this before, even back before mythdora or mythbuntu existed.

---

### Post by gfowler on 2008-06-03
> **linedpaper said:**
> I just switched from Mythdora 4 and seem to be having trouble getting my remote to work.  I have the Radio Shack 15-2116 remote and selected it during the setup process (and have tried again), yet it isn't working.  IR Receiver is the one built into to my PVR-350.  I am also using one serial port (ttyS1) for the usb connection to my directv box.  Upon trying /usr/bin/irw I get not output when pressing buttons on the remote.  Any ideas?

Check the sequence of the includes for the remote and serial connection.  The serial include needs to come in front of the remote include in /etc/lirc/lirc.conf.  I found this to be true when using an IR Blaster to control my STB (Dish TV).  A reboot may be required, at least a sudo /etc/init.d/lirc restart will be needed.

Jerry

---

