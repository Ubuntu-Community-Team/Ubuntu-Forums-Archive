---
title: "No Sound After Update to 10.10"
date: 2011-05-13
forum: Multimedia Software
---

### Post by HDTimeshifter on 2011-05-13
I have no sound after upgrading to 11.04.  Sound control panel and test speakers emits no sound.  The new music player won't play sounds from music CDs either.

I thought I had listened to a music CD since upgrading early last week, but not sure.  I definitely don't have sound today even after rebooting.

---

### Post by lidex on 2011-05-14
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by HDTimeshifter on 2011-05-15
I reset my pulse configuration and reselected my hardware profile and tried several other profiles - still no sound.

---

### Post by lidex on 2011-05-15
Have you tried a suspend/resume cycle?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by HDTimeshifter on 2011-05-15
Yes, I just retested after a hibernate/resume cycle.

The following link is the ALSA output (looks similar to the first time I ran it and posted in another thread):
[http://www.alsa-project.org/db/?f=d1754400f2b6796416e70426fa1d5081e9a3903d]("http://www.alsa-project.org/db/?f=d1754400f2b6796416e70426fa1d5081e9a3903d")

---

### Post by lidex on 2011-05-15
Please do not open multiple threads for the same issue. The question I asked in the other thread, can you answer here?
What is the make/model of computer or at least motherboard?

---

### Post by HDTimeshifter on 2011-05-15
Sorry, I kept getting the version wrong and couldn't rename the title.  It's Natty whatever - the latest version of Ubuntu.

It an ASUS P5Q Pro LGA 775 Intel P45 ATX Intel motherboard.  I'm using the digital in and out hardware option to an Altec Lansing 4.1 system.  I do have a splitter with 2nd cable to the coax digital input to a JVC A/V receiver.  I think I have the input unplugged to the receiver since the input was too low for that to work - I can try unplugging the splitter to see if maybe it's attenuating the main signal to the AL too much, but it worked under the last Ubuntu version.

---

### Post by lidex on 2011-05-15
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=6stack-digout" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by HDTimeshifter on 2011-05-15
Well, I ran that command, and didn't notice the part below about rebooting.  So, no sound still, but I disconnected the cable to the A/V receiver, and get sound now.  So it's either a case of signal attenuation or maybe it does requires some sort of loopback handshaking like HDMI.  I think I'll try plugging the other cable back into the splitter and into the receiver to see what happens (on both my AL PC soundsystem and the A/V soundsystem).

Thanks for the help so far, and I'll let you know the results of the test.

---

### Post by HDTimeshifter on 2011-05-21
Wasn't getting sound again today and I went to the back and bumped the cables, and suddenly the sound came on.  I plugged in the other coax cable to the splitter and checked to make sure all the cables were tight.  So somewhere there is a bad connection inside the cable.  I can actually now get sound from the PC through the A/V receiver as well to my 3.1 audio system.  The Altec Lansing 4.1 PC sound system is more of a backup to my 3.1 audiophile system when I don't feel like turning on my amplifier.

---

### Post by HDTimeshifter on 2011-06-18
Found out that jiggling or unplugging and replugging a cable connection will get the sound working with either my PC or CD/DVD player in my A/V system.  However, whenever I get one source working, the other one doesn't even if I turn off the source I don't want.  So it probably locks on to the source and I really need an A/B switch instead of a splitter.  For now, my solution is to unplug the splitter and just use my A/V system with my A/V sources and the PC system with my PC sound system.  Works ok since my PC 4.1 Altec Lansing powdered system, while not audiophile grade, is quite good.  Just can't get rid of my PC sound system and just run all sound through my A/V amplifier.

---

