---
title: "Trying to get Dishnetwork 311, s-video, pvr-150 working in harmony"
date: 2008-02-09
forum: Mythbuntu
---

### Post by Phydeaux on 2008-02-09
Have the Hauppauge PVR-150 installed, connected via s-video to my 311 Dishnetwork receiver.  I can see the video and audio just fine, a little smaller than the screen, but fine.  I am using the remote from the hauppauge ok in mythtv itself, but I cannot seem to get the irblaster to control the Dishnetwork box.  I've read so many guides that describe a lot of this stuff, but alas no joy.  Most of what I've found relates to keeping the pvr-150 on channel 3, which doesn't apply, or controlling the box via usb or serial.  Can somebody point me in the right direction?  I have other issues, such as irsend saying the hardware doesn't support sending, which makes no sense, and mythtv not scheduling a recording, but I'm sure these are all related to myth not knowing how to change the channel, etc.  Thanks!

---

### Post by Phydeaux on 2008-02-10
After spending almost two days solid fighting with this, I FINALLY got it working, with much help from the following post:
[http://ubuntuforums.org/showthread.php?t=587732&highlight=gutsy+lirc_pvr150](http://ubuntuforums.org/showthread.php?t=587732&highlight=gutsy+lirc_pvr150)

NOW....
I can send ir commands perfectly to the dish, although it changes channels slowly but still works.  My problem now is my remote won't control mythtv anymore!  If I watch the commands being sent with irw, it recognizes any button I push, just myth does nothing.  Probably something with the ~/.mythtv/lircrc file I can only assume, although I think the remote names match.  irw sees it as a hauppauge pvr 350, and /.mythtv/lircrc has that remote listed.  Any thoughts?

---

### Post by Phydeaux on 2008-02-11
Heh.  Today I booted the system up, and all is working perfectly.  Perhaps something was added to the kernel and needed a reboot.  I was so tired last night I didn't have much time to throughly test after the 20th time.
If anybody else experiences problem similar to mine, I can post my setup files here.

---

