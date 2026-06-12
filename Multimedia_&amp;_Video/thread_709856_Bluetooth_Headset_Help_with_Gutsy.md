---
title: "Bluetooth Headset Help with Gutsy"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by senecaso on 2008-02-27
For those of you who are still struggling with getting your bluetooth headset working, I figured I would post what ultimately worked for me.  There is a lot of information out there, but none of it seems to work.  I finally got my Plantronics Voyager 510 connected to my ThinkPad T61, and working through Skype on Gutsy.  To do this:

1. Use kbluetooth to connect/pair to the headset.  When doing this the first time, you should be prompted to enter your pin number (on my device it was 0000, I hear a lot of others are 1234)

2. Once you are connected, the little kbluetooth icon in your system tray should turn blue and when you hover over it, the tooltip should indicate you are connected to the device

3. ensure snd-bt-sco is loaded:  sudo modprobe snd-bt-sco

4. You can verify the module loaded correctly by checking dmesg

5. Bind the device with rfcomm: sudo rfcomm bind 0 00:00:00:00:00:00 1
  You will have to replace all those 0's with the address of your headset.  You can find that by right clicking kbluetooth -> Configuration -> Paired/Trusted Devices

6. fire up btsco: btsco -f -r 00:00:00:00:00:00 2

7. Test it by trying to play some sound to it: aplay -B 1000000 -D plughw:Headset /usr/share/sounds/KDE_Startup.wav

if you heard any sound through the device, it should now be working.  At least this worked for me.  I'm posting this in the hopes that some variation of it will help someone else out there who has been struggling as I have.  I know its not a clean solution, but at least it works.  Before attempting this solution, I recommend trying to use gbtsco first (google it).  If that doesnt work, then try this.

You can also put the above steps into a script (headset.sh) and run it as root after you complete Step 2.

  #!/bin/bash

  modprobe snd-bt-sco
  rfcomm release 0
  rfcomm bind 0 00:29:7A:21:AB:49 1
  btsco -f -r 00:29:7A:21:AB:49 2

---

### Post by georgefairbanks on 2008-04-07
Thanks, this worked for me.

If I accidentally pull out my bluetooth dongle, however, the cpu goes to 100%.

---

### Post by webdoctors on 2008-04-10
once your computer is paired with your headset, how did you get Skype to recognize it?

Did you change the device under preferences to headset or something?

---

