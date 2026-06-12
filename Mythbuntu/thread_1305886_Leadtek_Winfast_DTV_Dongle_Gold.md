---
title: "Leadtek Winfast DTV Dongle Gold"
date: 2009-10-30
forum: Mythbuntu
---

### Post by Newy11 on 2009-10-30
hi guys I have just downloaded and done a fresh install of mythbuntu 9.10 and I am following the guide on [http://www.mythtv.org/wiki/Leadtek_Winfast_DTV_Dongle_Gold]("http://www.mythtv.org/wiki/Leadtek_Winfast_DTV_Dongle_Gold") to install the new usb tv dongle I purchased the other day. 

so I have never set this up for this dongle before, and in the guide i get to the line:
```
hg clone http://linuxtv.org/hg/~anttip/af9015/archive/tip.tar.gz
```
and it returns this "abort: HTTP Error 404: Not Found"

i am not really an expert user so if anyone knows how to get this command to work correctly that would be greatly appreited ;)

---

### Post by Newy11 on 2009-10-30
still no luck, and i can't seem to find any info in google about it

---

### Post by David Grigor on 2009-10-30
Seems like it just can resolve your http: link.  You sure you have internet connection on the machine and can get to that address from firefox ?

---

### Post by Newy11 on 2009-10-30
yeah just did a ping [www.google.com](www.google.com) and thats works so im guessing that dns and internet are working correctly. thanks for the reply

---

### Post by owise1 on 2009-10-30
The site [http://linuxtv.org/hg/~anttip/af9015/](http://linuxtv.org/hg/~anttip/af9015/) points to a tips page.  Their does not appear to an archive however this appears to be a link to tips and tricks.  There is at the side of the page links to files that contain the documentation and firmware (which is what you want i assume?).  You could download manually and then read the docs from there

cheers

dave

---

### Post by owise1 on 2009-10-30
oops that link is valid - the gz link on the web page is that address

---

### Post by Newy11 on 2009-10-30
i just ran this command dont know if it helps

```
$ hg -v --debug clone http://linuxtv.org/hg/~anttip/af9015/archive/tip.tar.gz
using http://linuxtv.org/hg/%7Eanttip/af9015/archive/tip.tar.gz
sending between command
abort: HTTP Error 404: Not Found

```

---

### Post by owise1 on 2009-10-30
This is a right click copy of the link on that page [http://linuxtv.org/hg/~anttip/af9015/archive/tip.tar.gz](http://linuxtv.org/hg/~anttip/af9015/archive/tip.tar.gz)

Past it into your web browser and it should ask if you want to save the file or open it

---

### Post by Newy11 on 2009-10-30
yep if i put that into firefox on the myth box it wants to DL the file af9015-32bba41e7337.tar.gz but going off the guide i linked earlier is that what i want to do for this step?

---

### Post by owise1 on 2009-10-31
Now that you have the archive you should be able to use hg - (Mercurial source code management system) on the now local file - see man hg for more options.

I was able to just copy the firmware into lib/firmware for my TV card as the drivers for it are part of the kernel.  Looking at the .gz file it has all code that needs to be compiled to produce the firmware plus the other drivers.  I assume that running hg against that file will do all the hard work for you

---

### Post by owise1 on 2009-10-31
me again - you can download the ready to go firmware from: [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/)

copy it to lib/firmware and plug in the acrd and see if it is picked up using dmesg

I get this

usb 6-1: new high speed USB device using ehci_hcd and address 2
usb 6-1: configuration #1 chosen from 1 choice
usb 6-1: New USB device found, idVendor=2040, idProduct=9941
usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 6-1: Product: WinTV Nova-DT
usb 6-1: Manufacturer: Hauppauge
usb 6-1: SerialNumber: 4028961625

and this

dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
USB Video Class driver (SVN r260)
dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
dib0700: firmware started successfully.
dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
DVB: registering frontend 0 (DiBcom 3000MC/P)...
MT2060: successfully identified (IF1 = 1220)
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
DVB: registering frontend 1 (DiBcom 3000MC/P)...
MT2060: successfully identified (IF1 = 1220)
dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
usbcore: registered new interface driver snd-usb-audio
usbcore: registered new interface driver dvb_usb_dib0700

---

### Post by Newy11 on 2009-10-31
yep its all working now. thanks for you replys ;)

---

### Post by Hayesio on 2010-10-16
Hi guys,

I purchased one of these "Leadtek Winfast DTV Dongle Gold" recently and got it to work on Lucid by simply downloading the latest firmware from [PHP]http://www.otit.fi/~crope/v4l-dvb/af...irmware_files/[/PHP] and coping it to lib/firmware (I overwrote the existing file in that directory). I rebooted (don't think that necessary, but thats what I did) and now its working flawlessly.

Hope this helps someone.

Hayesio

---

