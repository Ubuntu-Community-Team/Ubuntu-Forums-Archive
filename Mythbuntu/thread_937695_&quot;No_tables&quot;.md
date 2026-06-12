---
title: "&quot;No tables&quot;"
date: 2008-10-04
forum: Mythbuntu
---

### Post by dsbw on 2008-10-04
Yo, mythbuntd00dz--

   I've got a setup with a KWorld 115 hooked to a pair of rabbit ears (and a Hauppauge 150, but that's not relevant, I don't think). If I understand correctly, the KWorld 115 needs to be set up with a "Card type" of "DVB DTV capture card", so I've done that. (I'm a little concerned that it gives  a "Frontend ID" of Air2PC v2 and a DVB Device Number of 0, and I can't change that.)

   Anyway, after setting up the card and setting a video source for OTA, I got to Input connection and scan. When I scan, I do get "locks", but then I get "no tables". I haven't been able to figure out what that means--is it just poor signal quality? Do I need an external aerial or something? This same set of rabbit ears gets a pretty dang clear picture on a few channels when hooked up to a TV.

   I'm just trying to get a bead on one OTA channel for starters....

---

### Post by newlinux on 2008-10-04
that frontend id is what is usually shown for Kworld. Have you loaded the firmware for the Kworld card?

---

### Post by dsbw on 2008-10-04
> **newlinux said:**
> that frontend id is what is usually shown for Kworld. Have you loaded the firmware for the Kworld card?

Is that still necessary? I thought .21 fixed that. The KWorld seems to be IDed properly (in, like, the V4L card type)!

Dang, I thought I was done with the firmware stuff....

---

### Post by dsbw on 2008-10-04
> **newlinux said:**
> that frontend id is what is usually shown for Kworld. Have you loaded the firmware for the Kworld card?

OK, did it, rebooted, no change. (EDIT: OK, I've included what I did, and I'm still going by .20 KWorld setup. Maybe that's why it didn't help?)

Also, for those interested, this is how to load the firmware:

(UPDATE: THIS APPLIES TO MYTH .20)

```
 Open command line (Ctrl+Alt+F1)
sudo apt-get install unzip

Firmware install:
If Kworld cards are being used:
  sudo aptitude install linux-source
  cd /usr/src
  sudo tar xvjf linux-source-[tab].tar.bz2
  cd linux-source-[tab]/Documentation/dvb
  sudo perl get_dvb_firmware nxt2004
  sudo cp dvb-fe-nxt2004.fw /lib/firmware/

And load the module properly (USE SUDO):
  1. cd /etc/modprobe.d/
  2. sudo nano kworld_atsc_115

  for one card:
    alias char-major-81 videodev 
    alias char-major-81-0 saa7134 
    options saa7134 card=90
    
  for two cards:
    alias char-major-81 videodev 
    alias char-major-81-0 saa7134 
    options saa7134 card=90,90 disable_ir=1

  3. sudo nano /etc/modules to add (USE SUDO):

    saa7134 
    saa7134-dvb
    saa7134-alsa

  4. sudo reboot (remove disc)

```

---

### Post by newlinux on 2008-10-04
firmware still required, the module options shouldn't be. It's a linux/hardware issue not a myth issue. So it is whether or not the kernel supports it. i still had to do it. but you must have another issue. I'll look into it ... Can you use the card digitally outside of myth?

---

### Post by dsbw on 2008-10-04
*Can you use the card digitally outside of myth?*

Got a link? (I have no idea how to do that.)

---

### Post by newlinux on 2008-10-04
Install dvb-utils from the repos...
[http://www.linuxtv.org/wiki/index.php/Scan](http://www.linuxtv.org/wiki/index.php/Scan)

You can then make a channels.conf file, put it in your ~/.mplayer directory, and then tune channels by name in the channels.conf file by doing:
```

mplayer dvb://ChannelName
```

What scan settings are you using? What EIT setting? also, what does:

```
dmesg | grep -i nxt200

```
return?

---

### Post by dsbw on 2008-10-05
> **newlinux said:**
> What scan settings are you using? What EIT setting? also, what does:

```
dmesg | grep -i nxt200

```
return?

I'm using the default EIT settings. (I can't actually see some of them since I can't see the extreme borders of the screens. The screen-adjust doesn't seem to affect the settings screens.)

Scan settings: Full Scan, Broadcast, Terrestrial 8-VSB, 5_1 Underscore Channel Separator, Minimal Updates to Existing Channels

dmesg returns:

[ 9051.215369] nxt200x: timeout waiting for nxt200x to stop. this is ok after firmware upload.
[ 9051.318143] nxt200x: Error writing multireg register 0x08
(This message is repeated about 10 times.)
[ 9051.892376] nxt200x: Timeout waiting for nx2004 to init.
(this message is repeated several dozen times.)

Running the scan again, I get the last message only, dozens of times.

---

### Post by dsbw on 2008-10-05
Pfeh. How do I get the initial file for the scan utility? I've stumbled over this before. I'm in the USA.

---

### Post by newlinux on 2008-10-05
> ...
dmesg returns:

[ 9051.215369] nxt200x: timeout waiting for nxt200x to stop. this is ok after firmware upload.
[ 9051.318143] nxt200x: Error writing multireg register 0x08
(This message is repeated about 10 times.)
[ 9051.892376] nxt200x: Timeout waiting for nx2004 to init.
(this message is repeated several dozen times.)

Running the scan again, I get the last message only, dozens of times.

This is probably the problem. for some reason the firmware doesn't appear to be loading right. for instance my dmesg looks like:

```
[   37.920501] nxt200x: NXT2004 Detected
[   38.049929] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   38.056399] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   41.340786] nxt2004: Firmware upload complete
```

---

### Post by newlinux on 2008-10-05
> **dsbw said:**
> Pfeh. How do I get the initial file for the scan utility? I've stumbled over this before. I'm in the USA.

for ATSC OTA:

```
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
```

---

### Post by dsbw on 2008-10-05
OK, I think I forgot to do the copy step. Duh.

Now I get channel locks and tables, though what I see is crap. (Broken images, blurring, digital artifacts...but that's a separate issue. Sally forth!)

---

### Post by dsbw on 2008-11-02
So...I never got what "no tables" means. I still get that on some frequencies.

---

