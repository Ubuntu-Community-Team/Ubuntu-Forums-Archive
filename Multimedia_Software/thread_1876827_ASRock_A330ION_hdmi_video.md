---
title: "ASRock A330ION hdmi video"
date: 2011-11-06
forum: Multimedia Software
---

### Post by dulciepercy on 2011-11-06
Hi

I have an Asrock A330ion htpc.  I finally got the hdmi cable but it doesn't give me any video. Should this just work or do I need to do something fancy?  I tested the cable with another device, though the plug on the motherboard is quite loose.

Using Mythbuntu with Oneiric.

Thanks

---

### Post by drawkcab on 2011-11-06
Should just work.  Did you install Oneiric while the television was connected so that it could detect the monitor?

---

### Post by papibe on 2011-11-06
Hi dulciepercy.

I'm no expert on Mythubuntu, but did you install the nvidia proprietary driver? If so, did you use 'Nvidia X Server Settings' to setup the monitor?

Did you install the system using a regular monitor?

Regards.

---

### Post by dulciepercy on 2011-11-06
No I installed it with a regular monitor (well the tv on a d-sub).  

I'm using the proprietary driver that comes with the install, not downloaded from nvidia.  If you open the settings it can detect the monitor, but if I plug it into hdmi I can't see the screen!  Maybe I can plug both in at once and see what it detects.  Will try that later today.

If that doesn't work you think the install will detect it?  That means it should boot from the live disk too, and work with hdmi if that's plugged in, yes?

---

### Post by papibe on 2011-11-07
> **dulciepercy said:**
> Maybe I can plug both in at once and see what it detects.
Yes. That's what I would do: while in the vga connection, connect the HDMI cable. Then I would open 'Nvidia X Server Settings' and try to set the monitor there.

It's going to be a little tricky because it is the same 'monitor'.

Another idea: turn on your machine with only the HDMI cable connected to your TV. Then boot into safe mode. Then choose boot normaly so you get a text mode prompt.

Log in in text mode. Backup your X conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then recreate the file using the active connection:
```
sudo nvidia-xconfig
```
Then restart your machine:
```
sudo reboot
```
Hope that helps. Tell us how it goes.
Regards.

---

### Post by dulciepercy on 2011-11-07
thanks.  I'll get back to you later.  Will pretend to be working again for a while :-)

---

### Post by dulciepercy on 2011-11-12
Well sorry it took a while. Getting nowhere really.  I've reinstalled about 10 times trying different things.

I know it can work because it worked once with the live distro: but install with either opensource or nvidia driver and there is no response.

I haven't tried Papibe's suggestion.  Maybe later.  Don't really understand it.  Might try going back to Natty.  Maybe might try Mint, but it's all for MythTV and nothing is a easy as Mythbuntu.

More later...

---

### Post by zombic on 2012-04-20
Hello. Did you get video using asrock a330ion with HDMI cable?

---

