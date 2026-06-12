---
title: "SIGMATEL STAC 92XX  audio in Ubuntu 9.1"
date: 2010-03-27
forum: Multimedia Software
---

### Post by maycom on 2010-03-27
Hi :)
I've a Dell Inspiron 1720 with a SIGMATEL STAC 92XX audio chipset.
But I'm not able to chose my mic (line in or the integrated mic in the lid)
Any suggestion how to fix this? 
 
Thanks!!
PS!: I'm almost a beginner with linux :\

---

### Post by maycom on 2010-04-14
> **maycom said:**
> Hi :)
I've a Dell Inspiron 1720 with a SIGMATEL STAC 92XX audio chipset.
But I'm not able to chose my mic (line in or the integrated mic in the lid)
Any suggestion how to fix this? 
 
Thanks!!
PS!: I'm almost a beginner with linux :\

No one?

---

### Post by lidex on 2010-04-14
Can you provide some more info please? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by maycom on 2010-04-20
> **lidex said:**
> Can you provide some more info please? Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

OK, here's the result:
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

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=ddef86d817a7b4b87816d8329a5ce953de19f92b

Please inform the person helping you.


```

---

### Post by Yellow Pasque on 2010-04-20
```
gksu /etc/modprobe.d/alsa-base.conf
```
Copy/paste this line to the end of the file:
```
options snd-hda-intel model=dell-m44
```
Save. Quit. Reboot.

When you log back in, check volume levels in:
```
alsamixer
```
(You may need to hit 'F6' to select your device).

If that doesn't help, you may need to upgrade ALSA itself (by installing linux-backports-modules-2.6.31 package).

---

### Post by lidex on 2010-04-20
> **Temüjin said:**
> ```
gksu /etc/modprobe.d/alsa-base.conf
```


Actually that command should read:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by maycom on 2010-04-21
Thanks a lot!!! :)
Had to install the linux-backports-modules-2.6.31 package.

Now it's working :)

---

### Post by lidex on 2010-04-21
Hi maycom,
Could you please edit your last post to show everything you did to get it working and then mark as 'Solved'? That way anyone with the same issue could find a working fix. Thanks!

---

### Post by Graemej on 2010-04-30
Hi Lidex and Temujin,

I followed your instructions and got the input working exactly as you said. I did not need to install Linux-Backports but did anyway.

I just wanted to thank you and post some further information.

I have had Ubuntu 10.04 RC (Last ver) on my machine for about a week and the audio set up perfectly at installation with a separate line and mic channel showing in alsamixer - just what I hoped for as I could not get that at Ubuntu 8.??

Now, I do have stereo input which works, but there is only "Capture" with no Mic or Line shown in alsamixer. It seems that the input provided at present is a mic one as it has a bias voltage of 3 Volts or so on each channel which I guess is for electret microphones.

I would be grateful if you could comment on this

Cheers, Graeme

---

### Post by lidex on 2010-04-30
Perhaps try gnome-alsamixer and make sure all elements are enabled in 'Edit>Sound Card Properties'.
In regular alsamixer I have 2 'Input Source' entries that can be toggled between line/mic/front mic

---

### Post by Graemej on 2010-05-01
Thanks for your response,

I have installed gnome-alsamixer and under sound card properties I have:

Master
PCM
Capture
Mux
IEC958
IEC958 Default PCM

All checkboxes are ticked

---

