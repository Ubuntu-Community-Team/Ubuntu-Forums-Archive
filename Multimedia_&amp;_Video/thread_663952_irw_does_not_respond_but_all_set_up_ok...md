---
title: "irw does not respond but all set up ok.."
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by relay23 on 2008-01-10
Guys, first let me apologize in advance for posting about a topic that has been widely discussed. I have read them all on this forum and others which has been extremely educational. At this point I understand all of the inter-workings of pieces to get the MCE remote (1039, mceusb2) working and have tried everything. Still no response on irw.

Here's what i've got-

   Ubuntu 7.10
   kernel 2.6.22-14-generic
   Followed the lirc mceusb2 install how-to for gutsy gibbon and everything went fine
   ran the lirc-modules-source install and got no errors at all. Have ran the dpkg-reconfigure, extracted the tarball and done the building of the module while pointing to the proper kernel headers and had no issues at all.
   my lircd.conf looks great and is symlinked to /etc/lircd.conf
   my hardware.conf looks great
   I have an lircrc in my home dir
   I am running lircd like this and get no errors: 
      sudo lircd --device=/dev/lirc0 -n /etc/lirc/lircd.conf
   lsusb picks up the Philips and that matches in the lirc_mceusb.c module file (0x0471) which matches what i see in lsusb output
   I can see the red light flashing 
   irw doesn't kill lircd and again i get no errors to the terminal window when starting lircd up.
   irrecord records nothing

I have tried different usb ports thinking that might be it. usb ports pick up other devices no problem and again lsusb shows my device. Windows was accessing this ir receiver and remote without a problem.

I'm usually very reluctant to post my issues and am definitely banging my head against a wall at this point enough to do so. 

Also, I have an MCE keyboard that goes with it. Obviously i have no response from that either but if someone would be so kind to let me know if i'll have to do something special with this as well that would be great.

Thanks,,

Chris

---

### Post by relay23 on 2008-01-11
I'm thinking there could be a slight kernel module / version mismatch issue or something? That part did go totally fine though and i haven't upgraded my kernel. i have -generic and non "-generic" in my headers which could be confusion but see in the lirc_mceusb2.c module file where that would actually be set..  How do I debug that? thx

---

### Post by relay23 on 2008-01-11
this time in doing the whole dpkg-reconfigure process on lirc-modules-source I first deleted the 2.6.22-14 folder and left the -generic folder in /usr/src. When prompted for the kernel source dir i choose the -generic as opposed to the symlinked /usr/src/linux file and re-ran lircd.. still nothing. No complaints from any output that i can see.. i'm running lircd in "-n" mode to watch the output, have checked dmesg, and of course have run irw (which doesn't crash lircd) but no buttons showing up in irw output at all.

I'm banging my head against the wall big time.. somebody saaaave meeeeee! thx

---

### Post by kdeiss on 2008-01-12
hi relay23,

Sorry I can't help, but I was glad to find your posting cause I have exactly the same problem and it drives me crazy ,,,

Perhaps it is a bug, please see my post here: [http://ubuntuforums.org/showthread.php?t=665313](http://ubuntuforums.org/showthread.php?t=665313)

Which kind of hardware do you use ?

thx


Klaus

---

### Post by RawMustard on 2008-01-12
lirc in gutsy is borked!

[http://ubuntuforums.org/showthread.php?p=4122079#post4122079](http://ubuntuforums.org/showthread.php?p=4122079#post4122079)

---

