---
title: "boot locks up after HVR-950 install"
date: 2008-07-08
forum: Mythbuntu
---

### Post by mrothwell on 2008-07-08
I had 8.04 running on my machine with a PVR-150.  I then followed lunapark6's instructions ( [http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html]("http://lunapark6.com/usb-hdtv-tuner-stick-for-windows-linux-hauppauge-wintv-hvr-950.html") )on how to get Ubuntu to recognize the HVR-950.

upon reboot, the system locks up and I cant get to a console.  I've tried with the USB stick plugged in and un-plugged.  Any ideas what I should try?

I have found that I can SSH into the box, but don't know where to go from there to fix the issue.

---

### Post by ian dobson on 2008-07-08
Hi,

Try logging through ssh then stopping the driver with
rmmod em2880-dvb

then 
locate em2880-dvb

then delete the file em2880-dvb

then 
depmod -a

or you could blacklist the driver by adding it to the blacklist by adding em2880-dvb to /etc/modprobe.d/blacklist.

Your playing with experimental software and things don't always go as expected :(

Regards
Ian Dobson

---

### Post by rqliang on 2008-07-08
Hi, I use this instruction([http://u32.net/MythTV/WinTV-HVR-950/]("http://u32.net/MythTV/WinTV-HVR-950/")). and get it works with mplayer. It runs great! This instruction is very easy. But there is another thing. After I installed this TV card, I cannot use my integrated webcam. Before this, /dev/video0 is the webcam, but now it's the TV. I don't know how to get my webcam works.

---

### Post by ian dobson on 2008-07-08
Hi,

Could it be that your webcam is now dev/video1?
Or the driver for your webcam is compiled against an older version of V4L. If that's the case then you need to recompile the webcam drver.


Regards
Ian Dobson

---

### Post by mrothwell on 2008-07-14
> **ian dobson said:**
> Hi,

Try logging through ssh then stopping the driver with
rmmod em2880-dvb

then 
locate em2880-dvb

then delete the file em2880-dvb

then 
depmod -a

or you could blacklist the driver by adding it to the blacklist by adding em2880-dvb to /etc/modprobe.d/blacklist.

Your playing with experimental software and things don't always go as expected :(

Regards
Ian Dobson


I could not get it to work, ended up having to completely re-install Mythbuntu.  Not a big deal, as it's a "play" system.

---

### Post by mrothwell on 2008-07-14
> **rqliang said:**
> Hi, I use this instruction([http://u32.net/MythTV/WinTV-HVR-950/]("http://u32.net/MythTV/WinTV-HVR-950/")). and get it works with mplayer. It runs great! This instruction is very easy. But there is another thing. After I installed this TV card, I cannot use my integrated webcam. Before this, /dev/video0 is the webcam, but now it's the TV. I don't know how to get my webcam works.

I don't know why this site did not appear in any of the searches I did.  Everything pointed to that lunapark site. 

I followed the directions in the above link and it appears that the 950 is working now.  I still need to do some setup, but mythbuntu recognizes the card now and will address it.

thanks for the link.

---

### Post by Chronon on 2008-10-10
Someone named Sam posted some new instructions in the comments section of the lunapark page that worked well for me (Hardy Heron), so I thought I would update this topic.  I'm using xine to view TV now and it's working nicely.

---

