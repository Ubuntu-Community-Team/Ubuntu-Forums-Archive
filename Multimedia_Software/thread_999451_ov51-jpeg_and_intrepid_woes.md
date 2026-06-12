---
title: "ov51-jpeg and intrepid woes"
date: 2008-12-01
forum: Multimedia Software
---

### Post by happygg on 2008-12-01
not really sure if this the right forum but i guess it falls under video?

i was using ubuntu 8.04 and loved it. bought a webcam and it needed the driver so i learned how, then everything was working good and i was happy with my new os.

then came the upgrade to 8.10 and my webcam stopped working, i read things and realized id have to recompile the driver on every kernel upgrade so i started... only to discover the driver wouldnt compile on this new kernel yet, i had to wait for an upgrade, which came shortly later.

so again i compiled the driver. it compiled, and installed.

checking lsmod saw the module loaded as ov51x-jpeg and also gspca modules which were interfering. so i moved that folder safely to another location and rebooted.

ok now when i put the webca in dmesg shows this

[15909.540099] usb 3-2: new full speed USB device using uhci_hcd and address 5
[15909.741253] usb 3-2: configuration #1 chosen from 1 choice
[15909.744122] ov51x_jpeg: USB OV519 video device found
[15910.096873] ov51x_jpeg: Sensor is an OV7648
[15910.216731] ov51x_jpeg: Device at usb-0000:00:10.1-2 registered to minor 0

and 

$ lsmod | grep ov
ov51x_jpeg            159224  0 
videodev               41344  1 ov51x_jpeg
usbcore               149360  7 ov51x_jpeg,snd_usb_audio,snd_usb_lib,zd1211rw,uhci_hcd,ehci_hcd

yet still the cam isnt found?

not in cheese or skype or ekiga.

someone please help!

edit:

in gstreamer-properties when testing the v4l and v4l2 i get "Could not open device /dev/video0 for reading or writing"

not sure if this helps any but i dont know im baffled.. still sort of new to linux

kernel is latest 27-10

---

### Post by happygg on 2008-12-02
bump, is this the right area for this?

surely i cant be the only one having this problem but google doesnt help

---

### Post by xc3RnbFO8P on 2008-12-02
Did you find this:
[http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page]("http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page")

---

### Post by happygg on 2008-12-02
yes the ov51x-jpeg driver is the only one that really works with this eyetoy camera.

in intrepid the gspca drivers actually load by default but they dont really work even remotely well so i'm forced to use ov51x-jpeg.

the kernel breaks this one

maybe someone could tell me a safe way to reinstall the 24 kernel not the 27?

would that be safe with intrepid?

or maybe another solution

---

### Post by happygg on 2008-12-02
seems the threads here get buried easy,,,

is there a better place i can go to get assistance on this issue?

i would have thought it was bad if it was widespread.

its the only thing stopping me from using ubuntu as my main os.

i need skype to talk to family overseas

---

### Post by happygg on 2008-12-03
whatever happened to the helpful ubuntu community

---

### Post by happygg on 2008-12-03
ok i guess theres no solution.

---

### Post by TremerePuck on 2008-12-08
I have the same problem as well. Hope someone finds a solution. =o/

---

### Post by barney_1 on 2008-12-10
I came across this thread when I was trying to fix this myself.  I got it to work, here's how, I hope this helps:

Resources:
[https://bugs.launchpad.net/ubuntu/hardy/+source/ov51x-jpeg/+bug/190450/comments/40](https://bugs.launchpad.net/ubuntu/hardy/+source/ov51x-jpeg/+bug/190450/comments/40)
[http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedSource)

Step-by-step:

The ov51x-jpeg driver is broken in Intrepid with kernel 2.27.9.  You will need to compile from source version 1.5.9 of the ov51x-jpeg driver.

Open up the terminal and create a directory to work in (I use a directory off of my home directory called "compile" whenever I'm compiling something):
```
cd ~
mkdir compile
cd compile
```

Pull down the sources, unpack them and set into that directory:
```
wget http://www.rastageeks.org/downloads/ov51x-jpeg/ov51x-jpeg-1.5.9.tar.gz
tar -xvf ov51x-jpeg-1.5.9.tar.gz
cd ov51x-jpeg-1.5.9
```

build and install the driver:
```
make
sudo make install
```

Now we must remove some of the old crap:
```
sudo rm -r /lib/modules/2.6.27-9-generic/kernel/ubuntu/misc/media/ov511/
sudo rmmod gspca_ov519
sudo modprobe ov51x-jpeg
```

That should do it.  It's pretty easy to test with Xawtv:
```
sudo apt-get install xawtv
xawtv
```


**Update:** I seemed to have messed up my permissions to /dev/video0 so you may not want to play with the next part.  Now when I plug in the cam there is no group assigned to it at all.  I'll update when I get this solved.

You should see your webcam in a new window now.  If you got an error about permission denied you need to set the group for /dev/video0.  I had to add the group "video" add myself to the group, then log out and log back in and re-establish the settings for /dev/video0 with:
```
sudo chown root:video /dev/video0
```

Hope this helps!

---

### Post by TremerePuck on 2008-12-15
Mine isn't assigned a device file (IE: /dev/video0) when connected anymore. =o/

dmesg output:

[151383.938850] usb 1-5.1: USB disconnect, address 6
[151407.452442] usb 1-5.1: new full speed USB device using ehci_hcd and address 7
[151407.566648] usb 1-5.1: configuration #1 chosen from 1 choice
[151407.567678] ov51x_jpeg: USB OV519 video device found
[151412.600988] ov51x_jpeg: Can't determine sensor slave IDs
[151412.601007] ov51x_jpeg: OV519 Config failed
[151412.601013] ov51x_jpeg: Camera initialization failed
[151412.605065] ov51x: probe of 1-5.1:1.0 failed with error

---

### Post by seaq on 2008-12-16
Hi, i've put in the wiki a list for known bugs with webcam cameras. 


[https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams](https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcams)

---

### Post by TremerePuck on 2008-12-19
Had it hooked up to a hub. lol. Plugged it directly to my USB card and it worked perfectly!

---

### Post by songuke on 2010-05-28
ov51x-jpeg module worked for Creative Live! Cam Notebook VF0470 on Ubuntu Lucid 10.04, after applying the patch at [http://www.afallenhope.com/files/ov51x-jpeg.patch](http://www.afallenhope.com/files/ov51x-jpeg.patch) 

The compilation then proceeded smoothly.

And as TremerePuck mentioned, do not plugin the webcam via a USB hub. Plug it directly to your machine's USB port. 

Cheers.

---

### Post by ulrith on 2012-02-29
> **songuke said:**
> ov51x-jpeg module worked for Creative Live! Cam Notebook VF0470 on Ubuntu Lucid 10.04, after applying the patch at [http://www.afallenhope.com/files/ov51x-jpeg.patch](http://www.afallenhope.com/files/ov51x-jpeg.patch) 

The compilation then proceeded smoothly.

Hi! I'm trying to apply patch but get

```
patch -p1 < ov51x-jpeg.patch 
patching file ov511-decomp.c
Hunk #1 FAILED at 508.
1 out of 1 hunk FAILED -- saving rejects to file ov511-decomp.c.rej
patching file ov518-decomp.c
Hunk #1 FAILED at 1488.
1 out of 1 hunk FAILED -- saving rejects to file ov518-decomp.c.rej
patching file ov519-decomp.c
Hunk #1 FAILED at 1534.
1 out of 1 hunk FAILED -- saving rejects to file ov519-decomp.c.rej
patching file ov51x-jpeg-core.c
Hunk #1 FAILED at 12.
Hunk #2 FAILED at 539.
Hunk #3 FAILED at 678.
Hunk #4 FAILED at 686.
Hunk #5 FAILED at 697.
Hunk #6 FAILED at 709.
Hunk #7 FAILED at 762.
Hunk #8 FAILED at 5733.
Hunk #9 FAILED at 5804.
Hunk #10 FAILED at 5850.
Hunk #11 FAILED at 6355.
Hunk #12 FAILED at 6372.
Hunk #13 FAILED at 6383.
Hunk #14 FAILED at 6624.
Hunk #15 FAILED at 8374.
15 out of 15 hunks FAILED -- saving rejects to file ov51x-jpeg-core.c.rej
patching file ov51x-jpeg.h
Hunk #1 FAILED at 63.
1 out of 1 hunk FAILED -- saving rejects to file ov51x-jpeg.h.rej

```

Could you please help?

---

