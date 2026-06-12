---
title: "adaptec videooh pci capture card?"
date: 2009-09-29
forum: Mythbuntu
---

### Post by sdowney717 on 2009-09-29
curious if this was ever supported in mythbuntu.
Regular ubuntu knows it as a video4L2 capture card and I can open video and audio streams with VLC and Mplayer.

I tried running mythbuntu in Vbox, but I cant figure it out. Dont know if it should work or what the settings should be.

does anyone know about this?

hmmm, in /dev there is no video devices listed when running mythbuntu in vbox.
i wonder if you can run mythbuntu in vbox?

---

### Post by stevecartermo on 2009-10-01
I use 2 of these so they definately work with MYTHBUNTU. I think they run as PVR 150's

---

### Post by sdowney717 on 2009-10-01
thanks for getting back on this.
perhaps my issue was running it virtualized in vbox?

when you say pvr-150 is that how you set up the backend?
the backend drop down devicelist shows this?

---

### Post by stevecartermo on 2009-10-01
Lets see if I remember ... when you first set up the mythtv tuners you enter it as a V4L capture device, then you have to edit the tuner and change it to a hardware MPEG device PVR 150 save the changes and it should work

---

### Post by sdowney717 on 2009-10-02
ok, here is a screen shot. it says it cant open the device.
Do I finish this and then what file has to be edited?

---

### Post by stevecartermo on 2009-10-03
I think you finish it and then go back into the tuner setup to change it to the hardware mpeg device.

---

### Post by sdowney717 on 2009-10-03
i dont think it will ever work running in sun virtual box.
I tried vlc to open the video4linux device and it can not. So therefore neither can mythTV.

[http://www.mythtvbook.com/wiki/Virtual_Machine_Images](http://www.mythtvbook.com/wiki/Virtual_Machine_Images)

I even tried a virtualmachine image and it can not see the video device. The site seems to imply you can run it as a virtual machine. But if true I dont know how.

perhaps my video4 linux device is not configured in the virtual machine properly for ubuntu.

it is not showing up in my /dev directory.

---

