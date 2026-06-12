---
title: "Sound issues 10.04"
date: 2010-05-18
forum: Multimedia Software
---

### Post by kaenlsp on 2010-05-18
I've got an HP Pavilion with sound issues. It works fine and sounds perfectly whn connected to the speakers... but nothing works when I connect my headphones into it.
I've tried with several headphones in the two audio output slots the computer has... but it just doesn´t work.

Is there any solution or at least a command with an output that shows what the problem is?
Any other help or suggestions?

Thank you!

---

### Post by aphatak on 2010-05-18
Are you sure you are selecting the right output?  Assuming you are using the default Gnome desktop environment, -
1) Click on the speaker icon in the system tray.
2) In the dropdown that appears, make sure your volume is not muted all the way down
3) Click on the '... preferences'
4) In the window that pops up, select the outputs tab.
5) Make sure you have selected the output into which your headphones are plugged.  When you select an output, a slider will show up.  This controls the output volume, make sure the output volume is not too low to be heard.  If you do not know which output is right, try all of them one by one.
Let me know if this works.

---

### Post by duksis on 2010-05-18
Hi,

I'm having a similar issue just my headphones work but they are so quiet that I can barely hear something.
I use GN 2000 USB OC headphones and the sound before upgrading to 10.4 was ok.

Any suggestion on what could be the cause?

---

### Post by aphatak on 2010-05-19
I suspect the default volume setting - Ubuntu can start with a very low volume setting when installed.  To check / correct it, from the main menu, select System -> Preferences -> Sound.  You should see the Sound Preferences window (see attached screen shot).  Select the 'Output' tab.  Make sure the right output is selected, and that the 'Output Volume' slider is not set too far left.  This usually cures low-volume woes.

---

### Post by lidex on 2010-05-20
> **kaenlsp said:**
> I've got an HP Pavilion with sound issues. It works fine and sounds perfectly whn connected to the speakers... but nothing works when I connect my headphones into it.
I've tried with several headphones in the two audio output slots the computer has... but it just doesn´t work.

Is there any solution or at least a command with an output that shows what the problem is?
Any other help or suggestions?

Thank you!
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by maheanuu on 2010-05-22
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```


uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```

Terminal="Applications->Accessories->Terminal"

**Also helpful is the make/model of your PC/Laptop.**

Please post text output using code tags (the # in toolbar)

I hope that this is where I am supposed to post this, as I did not start this thread and my problem is the polar opposite as my speakers do not work but my earphones do.

I am running Ubuntu lucid Lynx 10.04 and before that was running Koala 9.10 and under both, the speakers have not worked.  My laptop is a Toshiba Satellite A355D-S6930

Here below are the readouts you were requesting for those above who were having very similar problems.  Perhaps they could help with mine, or if you need more information please tell me and I will post it Asap.

maheanuu@maheanuu-laptop:~$ uname -a
Linux maheanuu-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
maheanuu@maheanuu-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
maheanuu@maheanuu-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
maheanuu@maheanuu-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC272

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

Thanking you all in advance for your kind help and guidance.  I am learning step by step and loving what is happening.  

Ken Jackson
CPO USN Ret.

---

### Post by lidex on 2010-05-22
> **maheanuu said:**
> I hope that this is where I am supposed to post this, as I did not start this thread and my problem is the polar opposite as my speakers do not work but my earphones do.

I am running Ubuntu lucid Lynx 10.04 and before that was running Koala 9.10 and under both, the speakers have not worked.  My laptop is a Toshiba Satellite A355D-S6930

Here below are the readouts you were requesting for those above who were having very similar problems.  Perhaps they could help with mine, or if you need more information please tell me and I will post it Asap.

Ken Jackson
CPO USN Ret.

Is this 2-channel or 6-channel? Number of analog audio jacks? Digital?

First I would try an alsa-upgrade using the alsa-upgrade link in my sig.

No help?
Try this and see what you get. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

