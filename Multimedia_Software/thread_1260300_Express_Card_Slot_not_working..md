---
title: "Express Card Slot not working."
date: 2009-09-07
forum: Multimedia Software
---

### Post by chinoy on 2009-09-07
I have installed the latest version of Jaunty.
My machine is a Dell XPS M1530
The Chip Set is a PM965
The Graphics card is a Nvida 9600GT
I was able to download and install my Nvida driver and its working.

Allmost everything on my Laptop works.
Stuff that is working

- USB2 External HDD
- Integrated Creative Web Cam
- Wif-Chip from Intell
- Marvel Net Card
- All Nvida special functions including ext. Display
- All the custom buttons on the laptop & LEDs
- Stac 92xx Audio works fine
- CD/DVD works fine
- Touch pad and mouse both work fine.


BUT
Express card isnt working 
The card is a LifeView M5 T2A2 Express Card this uses the Philips TV Tuner IC by NXP

Somebody please help.
If I cant get my Express card to work its back to Windows for me and i HATE windoze

---

### Post by HappyFeet on 2009-09-07
Post the output of
```
lspci
```
Btw, what does an Express card do?

---

### Post by HappyFeet on 2009-09-07
Found the following, do:
```
sudo modprobe pciehp pciehp_force=1
```

---

### Post by chinoy on 2009-09-08
A very informative link on TV cards
[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)

---

### Post by chinoy on 2009-09-08
what I should have said
FATAL: Module pciehp not found
when I try to run the command you provided.

Simple google gives
[https://lists.ubuntu.com/archives/kernel-bugs/2009-March/048295.html](https://lists.ubuntu.com/archives/kernel-bugs/2009-March/048295.html)

Any idea what I should do ?

---

### Post by chinoy on 2009-09-08
My lspci-lsusb-lshw  output.
Wanted to add the complete usb -v but I am a few K over the limit.
Will figure out a way to share it

Does this help ?
pci@0000:03:09.4              generic     Illegal Vendor ID
Found in hardware.txt

ExpressCard:
Company Name: LifeView
Modell: FlyTV Express M5 MST-T2A2

This is a DVB TV Tuner card with FM and with Svideo and Composite Video in.
You can watch either Digital TV or Analogue TV.
It has two RF inputs so you can either hook up 2 Analogue or 2 Digital or 1 Analogue and 1 digital.
You can watch one TV programe while recording another.
I only want it to accept composite Video in so I can record my VHS tapes to the hard disk.
Its a superb card too bad the company folded

---

### Post by chinoy on 2009-09-10
Anybody ? 
Bump
Found this info which indicates I have re-compile Kernel. And add drivers.
Sad for a card that was launched over 4-5 years ago.
[http://www.jusst.de/hg/saa716x/summary](http://www.jusst.de/hg/saa716x/summary)

---

### Post by chinoy on 2009-09-12
I striped open the card cover it has a huge IC labeled 
Philips SAA7162E/G

---

