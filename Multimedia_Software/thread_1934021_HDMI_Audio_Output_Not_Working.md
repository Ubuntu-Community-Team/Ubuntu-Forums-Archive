---
title: "HDMI Audio Output Not Working"
date: 2012-03-01
forum: Multimedia Software
---

### Post by MrSlaggers on 2012-03-01
I can't seem to get HDMI audio output to work with my HP Pavilion dv6 laptop. Can anyone help me figure this out? My system information is here: [http://www.alsa-project.org/db/?f=75ad5d867f82d5c5cfdeefddea7d6cacd14fcd6e](http://www.alsa-project.org/db/?f=75ad5d867f82d5c5cfdeefddea7d6cacd14fcd6e) and I'm using Ubuntu 11.10.

---

### Post by bryanl on 2012-03-01
In **sound preferences**

on the **hardware tab**, make sure the HDMI audio is selected. click the 'Test Speakers' button to make sure it works.

Then, on the **output tab**, make sure that the HDMI device is selected for sound output.

You can also use the alsamixer program to make sure that the audio levels in and out are appropriate for the HDMI device.

Most of the time from my experience, it is this double whammy in sound preferences that trip people up trying to get HDMI sound output. If that doesn't work, then you have an 'interesting' problem that might take a bit of work to figure out.

---

### Post by MrSlaggers on 2012-03-01
> **bryanl said:**
> In **sound preferences**

on the **hardware tab**, make sure the HDMI audio is selected. click the 'Test Speakers' button to make sure it works.

Then, on the **output tab**, make sure that the HDMI device is selected for sound output.

You can also use the alsamixer program to make sure that the audio levels in and out are appropriate for the HDMI device.

Most of the time from my experience, it is this double whammy in sound preferences that trip people up trying to get HDMI sound output. If that doesn't work, then you have an 'interesting' problem that might take a bit of work to figure out.

Yeah I looked through all those settings before making this post and they are all set correctly. The selected Hardware Device is RS880 Audio Device [Radeon HD 4200] and the Output Device is set to RS880 Audio Device [Radeon HD 4200] Digital Stereo (HDMI). In alsamixer I looked at the HDA ATI HDMI sound card and it shows me this: [http://i.imgur.com/cQ3MU.png](http://i.imgur.com/cQ3MU.png)

---

### Post by BicyclerBoy on 2012-03-01
The open radeon driver has limited hmdi audio support.

[http://www.x.org/wiki/RadeonFeature#Feature_Matrix_for_Free_Radeon_Drivers](http://www.x.org/wiki/RadeonFeature#Feature_Matrix_for_Free_Radeon_Drivers)

Your GPU is the R600 family, seems to be supported.
See footnote 9 about radeon.audio=1

Else you have to use the AMD catalyst driver.

---

### Post by MrSlaggers on 2012-03-02
> **BicyclerBoy said:**
> The open radeon driver has limited hmdi audio support.

[http://www.x.org/wiki/RadeonFeature#Feature_Matrix_for_Free_Radeon_Drivers](http://www.x.org/wiki/RadeonFeature#Feature_Matrix_for_Free_Radeon_Drivers)

Your GPU is the R600 family, seems to be supported.
See footnote 9 about radeon.audio=1

Else you have to use the AMD catalyst driver.

I changed the line in /etc/default/grub to include radeon.audio=1 like this:

```
GRUB_CMLINE_LINUX_DEFAULT="quiet splash radeon.audio=1 acpi_osi=\\\"Linux\\\""
```

And I then ran sudo update-grub and rebooted, however audio is still coming out of my laptop speakers.

---

### Post by bbbgscott on 2012-03-02
I'm having a similar problem, but I have an nvidia card.  I dual boot with windows, and connect to my monitor with an HDMI cable.  I can't get audio to output through HDMI on Ubuntu, but it works fine on Windows.  Ubuntu recognizes my card and driver.

---

### Post by BicyclerBoy on 2012-03-03
@MrSlaggers..
What does this show: 
aplay -l

Run pavucontrol & check your default output device & configuration..

If you are planning to output HDA or AC3/DTS over HDMI then you need to point the player programs at the alsa device directly.

@bbbgscott
Problem may sound similar (bad pun) but likely it isn't..
Are you using the nVidia proprietary driver?
*buntu distro ?
Video card model ?

You need alsa user-space 1.0.24 or later.
speaker-test reveals the version..

---

