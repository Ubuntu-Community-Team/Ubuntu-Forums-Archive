---
title: "Satellite L30 Sound"
date: 2008-10-09
forum: Multimedia Software
---

### Post by Negwoh on 2008-10-09
I know this has been brought up over and over but i have tryed all the fixes that i have been able to find like update your alsa drivers to the latest and add "options snd-hda-intel model=lenovo" to /etc/modprobe.d/alsa-base and others like model-3stack, fix_position=1 model=lenovo, model=Toshiba etc but none have worked i get absolutly no sound from speakers or headphones. Im running 8.04 (Hardy Heron) on a Toshiba Satellite L30 Model Number PSL30A-00100E. I am so stuck and frustrated. Any help is appreciated.

---

### Post by christianvaldes on 2008-10-09
System --> Preferences  -->  Sound

Do all the tests fail?

---

### Post by christianvaldes on 2008-10-09
> **Negwoh said:**
> I know this has been brought up over and over but i have tryed all the fixes that i have been able to find like update your alsa drivers to the latest and add "options snd-hda-intel model=lenovo" to /etc/modprobe.d/alsa-base and others like model-3stack, fix_position=1 model=lenovo, model=Toshiba etc but none have worked i get absolutly no sound from speakers or headphones. Im running 8.04 (Hardy Heron) on a Toshiba Satellite L30 Model Number PSL30A-00100E. I am so stuck and frustrated. Any help is appreciated.

Not sure if something in this thread might help.

[http://ubuntuforums.org/showthread.php?t=706450](http://ubuntuforums.org/showthread.php?t=706450)

---

### Post by thomson2008 on 2008-10-10
I just bought a brand new laptop (Satellite L30 PSL33E-02S01LBT). It had Windows Vista installed but it was horribly slow.I installed Windows XP SP2 on it made the updates. I installed all the drivers from toshiba website I could find for my model.
_________________________________________________
[Find a florist in Phoenix](http://www.florist-flowers-roses-delivery.com/arizona/phoenix_az.html) [cheapest loans](http://www.cheaponline-loans.co.uk/) [casas vilafranca](http://www.vilafrancadelpenedes.com/-1/posts/1_Habitatge/0/) [ringtone downloads](http://www.myringtoneshub.com/)

---

### Post by joseph2008 on 2008-10-10
The Satellite L30 series is the latest entry level notebook. from Toshiba offering a blend of home-use or business. he Satellite L30 notebook PC comes with the ATI Radeon Xpress 200M graphics chipset technology designed for DirectX 9.0 and OpenGL compatible games.
___________________________________________________________________
[LA Flowers](http://www.florist-flowers-roses-delivery.com/california/los_angeles_ca.html) [low rate loans](http://www.cheaponline-loans.co.uk/) [penedes](http://www.vilafrancadelpenedes.com) [ringback tones](http://www.myringtoneshub.com/)

---

### Post by GeorgeVita on 2008-10-10
Hi, I also have a Toshiba Satellite **L30-113** (PSL33E) and the sound works a little bit by adding a line at the bottom of alsa-base:

From a terminal window execute the command:
**sudo gedit /etc/modprobe.d/alsa-base** (give your password)

go to the end of the file and **after** the line **options snd-cmipci mpu_port=0x330 fm_port=0x388** add
**options snd-hda-intel model=3stack**
(also remove any other lines that you have entered in your previous tries)

Save file, exit and reboot.

The result in my case is: sound from speaker OK, sound to headphones NO (switch works), medium sensitivity on MIC, CD is working as PCM sound, PC Speaker works (you can test with backspace at terminal prompt).

Note that the chip in my laptop is **ALC861-VD** and the lspci command list it as
Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

Regards,
George

---

### Post by Negwoh on 2008-10-11
@ christianvaldes - Yes all thoes tests fail

@ thomson2008 - Cool

@ GeorgeVita - I have already tryed this fix as stated in my first post

---

### Post by GeorgeVita on 2008-10-11
EDIT: I edit all message because I thing is useless to give you more links as you probably have tried all these. Some thoughts trying to help:
The ALSA project makes some fixes for a sound chip to work on different h/w giving names like "lenovo" or "6 stack digout". Our L30s possibly have different motherboards with the same sound chip but with different wiring on audio I/O channels. I checked the two datasheets (PSL30E, PSL33E) they state the same "Realtek HD audio" but is it ALC861-VD? You can try the terminal command **aplay -l** and **lspci** to get some info (Audio device:...). Then you could try all "names of fixes" for the specific chip. These tests are painful because you must edit the alsa-base and reboot every time (all volume controls must be at maximum).

From the ALSA-Configuration.txt file (I found it through google) the fixes for ALC861-VD are:
3stack
3stack-dig
6stack-dig
lenovo
dallas
hp
auto

Regards,
George

---

### Post by Negwoh on 2008-10-13
lspci | grep Audio returns

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

aplay -l returns

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And all thoes options fail

---

### Post by GeorgeVita on 2008-10-13
From the ALSA-Configuration.txt file these are the possible parameters for **ALC861** or ALC660 (parameter is bold):

**3stack** 3-jack
**3stack-dig** 3-jack with SPDIF I/O
**6stack-dig** 6-jack with SPDIF I/O
**3stack-660** 3-jack (for ALC660)
**uniwill-m31** Uniwill M31 laptop
**toshiba** Toshiba laptop support
**asus** Asus laptop support
**asus-laptop** ASUS F2/F3 laptops
**auto** auto-config reading BIOS (default)

In my case I tested all possibilities (the other set for 861VD) using the following procedure:
a. **sudo gedit /etc/modprobe.d/alsa-base**
b. add (or change) last line: **options snd-hda-intel probe_mask=1 model=XXXXX** (where XXXXX was the parameter to check)
c. **Save** & **Exit** from gedit
d. **Shut down, boot**
e. **Test Speakers** Audio: Insert an Audio CD, start Playing using Rythmbox music player, double click to "speaker icon" and adjust volume controls to mixer (PCM, Front, Master, PC Speaker all to Maximum with no mute)
f. [B]Test Headphones[B] Audio: the same as above but insert headphones in appropriate front connector.
g. **Test PC Speaker**: Open a Terminal window and press backspace at prompt
h. **Write down result** (parameter, speakers ok/no, headphones ok/no, etc)

In my case, sometimes I had audio only from headphones. The "reboot every time" was painful but now I HAVE SOUND! (all good except headphones)

Possibly there are not so many Linux users using Satellite L30 making "hard to find" the proper fix...but we have the L30!

---

### Post by Negwoh on 2008-10-14
would it have anything to do with what device i am useing? I mean when i double click on the speaker in the top right hand corner to get the volume control then go to file -> change device, there are 4 devices they are as follows
0: Realtek ALC861 (OSS Mixer)
1: Playback: ALSA PCM on front:0 (ALC861 Analog) via DMA (PulseAudio Mixer)
2: Capture Monitor source of ALSA PCM on front:0 (ALC861 Analog) via DMA (PulseAudio Mixer)
3: Capture: ALSA PCM on front:0 (ALC861 Analog) via DMA (PulseAudio Mixer)

its been on 0 the whole time i believe and i am trying all thoes options slowly atm

Thanks for all the help guys options snd-hda-intel probe_mask=1 model=uniwill-m31 did it for me in the end, headphones i havent tested but at least i have speakers working for my music, thanks

---

### Post by GeorgeVita on 2008-10-14
Well done!

If you want the default Alsa Mixer (which has many controls and runs automatically) you must have: **0- HDA ATI SB (Alsa mixer)**

I think you can reinstall defaults via Synaptic (System > Administration > Synaptic Package Manager). First check if in column S (on upper window at right) you have installed (green box) at least alsa-base and alsa-utils. Double click on both and **Mark for Reinstallation** then tick **Apply** and **Apply**.

After finishing reboot and see if you have the selection 0-HDA ATI SB (Alsa mixer).

Regards,
George

P.S. the best you are going to hear is "the sound of drums" at log-in screen!

Full description of "Trying to make sound working on a Toshiba Satellite L30-113
with Ubuntu 8.04" at [http://www.acomelectronics.com/GeorgeVita/](http://www.acomelectronics.com/GeorgeVita/)

---

### Post by Negwoh on 2008-11-03
Just formatted to install 8.10 and got an error on boot "kernel panic - cannot load root fs kernel not syncing" i think lol anyway thats not the point so i put 8.04 back on and came back to this page to fix my sound again and then tryed to get that mixer working and i already have alsa-base and alsa-utils installed but no mixer =\

---

### Post by GeorgeVita on 2008-11-04
Hi, check in **System > Administration > Synaptic Package Manager** if you have the following installed:
[B]
alsa-base
alsa-utils
linux-sound-base
[/B]
Tick them and reinstall just in case that something is missing (alsamixer is inside alsa-utils).
Then reboot and edit again the alse-base file (look previous posts sudo gedit /etc/modprobe.d/alsa-base)
adding **options snd-hda-intel probe_mask=1 model=uniwill-m31** at the end.

How did you "came back to 8.04"? A full install from an ISO CD should place anything right.
ISO file to download is **ubuntu-8.04.1-desktop-i386.iso** or **ubuntu-8.04.1-alternate-i386.iso** starting from [www.ubuntu.com](www.ubuntu.com)
If you want to check the image file you already have (8.04 or 8.10) follow the instructions at:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

