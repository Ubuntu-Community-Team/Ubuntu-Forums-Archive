---
title: "Quiet audio on new PC (Ubuntu 12.04)"
date: 2014-01-05
forum: Multimedia Software
---

### Post by MrMichaelHill on 2014-01-05
Hello all! I have recently finished building my new TuxBox! :D

All working great! Headphones work when connected to front of machine, mic too!

Now the only issue is the audio is very quiet. I have been into the sound options and turned the volume up past 100%, this has no real gain and only makes the sound a little distorted. I have checked alsamixer & everything is set up right & correctly adjusted.

It is onboard, ***audio HDA Intel PCH ****&**** Realtek ALC892**** chip*****

Running Ubuntu 12.04 64Bit - 3.8.0-35-generic

Any help greatly appreciated, thanks.

---

### Post by Bucky Ball on 2014-01-05
Have you tweaked Pulseaudio Volume Control? You can set the devices in there.

---

### Post by MrMichaelHill on 2014-01-05
Don't think so? How do I do that?

---

### Post by Bucky Ball on 2014-01-05
I'm not on Ubuntu, but should be installed in Multimedia or Audio (sorry, unsure what the category names are in Ubuntu). You can look in the search window for Pulse.

---

### Post by MrMichaelHill on 2014-01-05
Had to install it. But nothing in there helps. Guessing it is a driver issue?

---

### Post by MrMichaelHill on 2014-01-05
So, I booted into my Windows partition before, fresh install and the sound is just as quiet.

As a troubleshooting idea I disconnected the front audio ports from the motherboard. Booted up and still just as quiet :(

---

### Post by king.of.random on 2014-01-05
Sounds like a hardware issue then. Have you tried a second pair of headphones as it maybe a miss-match with the output from the sound card and your headphones. Also do your headphones have volume controls? I know some do.

---

### Post by Yellow Pasque on 2014-01-05
Here'e what I would do:
0. Disconnect headphones, and if your case is easy to open, disconnect the front headphone jack.
1. Boot into BIOS and disable the onboard audio in the BIOS. Save changes and re/boot into Ubuntu.
2. Install latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
3. Reboot into BIOS and enable the onboard audio. Save changes and re/boot into Ubuntu.

If it's still not working, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
You may also want to check that you're running latest BIOS, and you may want to consider resetting the CMOS using the jumper on the mobo (consult mobo manual if you don't know how).

---

### Post by MrMichaelHill on 2014-01-06
> **Temüjin said:**
> Here'e what I would do:
0. Disconnect headphones, and if your case is easy to open, disconnect the front headphone jack.
1. Boot into BIOS and disable the onboard audio in the BIOS. Save changes and re/boot into Ubuntu.
2. Install latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
3. Reboot into BIOS and enable the onboard audio. Save changes and re/boot into Ubuntu.

If it's still not working, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
You may also want to check that you're running latest BIOS, and you may want to consider resetting the CMOS using the jumper on the mobo (consult mobo manual if you don't know how).

Sounds good! I'm just about to have my dinner then I'll get back to the PC with a beer and give it a whirl!

I'll post back results! :popcorn:

---

### Post by MrMichaelHill on 2014-01-06
Still quiet after installing latest driver :(

My headphones have a volume adjuster so I can get the sound to a good level no probs, I'll just have to replace my speakers with some that have a volume dial also I think lol. 
Not sure if resetting the CMOS would help as I haven't adjusted anything in there since it came out of the box!

---

