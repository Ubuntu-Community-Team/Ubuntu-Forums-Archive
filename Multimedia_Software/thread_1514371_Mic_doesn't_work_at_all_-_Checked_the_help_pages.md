---
title: "Mic doesn't work at all - Checked the help pages"
date: 2010-06-20
forum: Multimedia Software
---

### Post by galvao on 2010-06-20
Greetings.

I have a headset and everything used to work in 9.10, but now that I'm using Kubuntu 10.04 I can't make the mic to work:

- Checked [this help page]("https://help.ubuntu.com/10.04/musicvideophotos/C/music-microphone.html"). Everything seems to be OK.
- Checked [this help page]("https://help.ubuntu.com/community/Skype#Audio%20Problems"): Tried step one (pavucontrol), but when I run pavucontrol it complains that it can't connect. I've stopped there, since I'm not confident enough to go uninstalling pulse audio (which I THINK it's what my system uses).

Please notice that I never had to uninstall anything related to audio to make it work before, in 9.10 it "just worked".

My sound card is a SiS SI7012. 

I tested with Audacity (by "monitoring" the microphone) and then tested with Skype (tried every device listed on it's options, no success at all). Both softwares used to work with my Kubuntu 9.10.

Please help!

---

### Post by lidex on 2010-06-22
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by coskierken on 2010-06-22
Please check to see (preferences/sound/input) if the mic is muted.  For some reason, the mic is muted by default on 10.04. You have to turn it on.

---

### Post by galvao on 2010-06-22
Preferences->Sound->Input ... where, exactly?

---

### Post by coskierken on 2010-06-22
When you go to input, it should list the hardware which is normally analog input and it should be selected.  You should see the input level bar and on the top is a box for mute.  Just uncheck it.

---

### Post by galvao on 2010-06-24
Sorry for the long delay in my reply (for some reason I'm not receiving replies notifications, maybe my spam box), but anyway:

When I go to System Settings->Multimedia I see two main nodes: "Audio Output" and "Audio Capture". None of them (or it's subnodes) have a mute box.

TIA,

---

### Post by galvao on 2010-06-30
This is the ouput:

```

ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.


```And then it hangs in there...

No real output huh?

Any ideas?

---

### Post by lidex on 2010-06-30
This is what I get:
```
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : 

```
Enter y or n and hit enter

---

### Post by galvao on 2010-07-01
Output located at: [http://www.alsa-project.org/db/?f=8f0fe997737b2751e8ab36087da45adc14193a7b](http://www.alsa-project.org/db/?f=8f0fe997737b2751e8ab36087da45adc14193a7b)

---

