---
title: "Pulseaudio: Removed USB speakers now no sound"
date: 2010-04-04
forum: Multimedia Software
---

### Post by LinuxBob on 2010-04-04
I took out some USB speakers that had been working for many months because I needed them on another PC.  I plugged the audio out (lime colored female connector on back of Ubuntu PC) into my stereo receiver's VCR audio in (Red and white jacks), no sound.  Yes, the cable is fine (same cable I took off the other PC which was working fine), and the receiver is set to VCR.


I recall having to go through some hoops to get the USB speakers working way back when.  The Pulseaudio volume control shows left and right pulsating bars when I have on Pandora, but sound is obviously not being sent to the right output.  I also tried the optical audio out on the PC into the receiver's DSB optical in but again no sound. 

Any ideas?

---

### Post by mikewhatever on 2010-04-04
If on 9.10, you can try changing the output under gnome-volume-control, output tab. If not on 9.10, try installing pavucontrol package.

---

### Post by LinuxBob on 2010-04-05
Not sure what gnome volume control is, I tried system preferences sound and wasn;t abel to change anything.  


Also, I have PA Voume control.  Wasn;t there a way to redirect the stream, left and right clicking on volume bar does nothing

---

### Post by mikewhatever on 2010-04-05
Well, gnome-volume-control can be accessed from either the speaker icon in the panel or System->Preferences->Sound. In 9.10, the settings are very similar to those of pavucontrol. Click the 'Output' tab and select an output destination from the drop down menu. For example, in my case there are two options, analog output and headphones. Not quite sure why right click on volume bars at all,:confused:

---

### Post by LinuxBob on 2010-04-06
OK will try when I get home, if memory serves I only have digital stereo output option.


Here is the rear of the PC

[http://zareason.com/shop/product.php?productid=16220&cat=249&page=1](http://zareason.com/shop/product.php?productid=16220&cat=249&page=1)

I am plugged into the light green audio out in between the blue & red output jacks at the bottom.  I had been plugged into USB.

---

### Post by LinuxBob on 2010-04-06
On th eoutput tab there is only one choice (remember the USB speakers have been removed).  It has a dot in the radio button and is entitled 

Internal Audio Digital Stereo (HDMI)

---

### Post by LinuxBob on 2010-04-06
When I set up the USB speakers  I believe I had to change the line in /etc/modprobe.d/alsa-base.conf


options snd-hda-intel probe_mask=8 model=3stack

I had to overwrite whatever was there model=xxxx with "3stack"


What was there?  I have HDA nVidia sound card MCP79   and IEC958 shows up in alsamixer but no volume bars for anything at all, just blank alsamixer with sound card info.

Also, once I update /etc/modprobe.d/alsa-base.conf I then have to shut down or restart alsa and/or pulseaudio, anyone know the sequenc eof commands?

---

### Post by mikewhatever on 2010-04-09
I've no idea what option was originally there, but you could reinstall alsa, which will overwrite the alsa-base.conf config file with the new one.

```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

```

---

### Post by LinuxBob on 2010-04-21
Excellent.  I will try this.

I also wrote to Zareason and they provided me with the original alsa-base.conf file.  Unfortuntely that file and /etc/modprobe.d are owned by root so I am having difficulty su'ing to root, no password.

---

### Post by lidex on 2010-04-21
I'd hold off on removing that option line for a moment. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by LinuxBob on 2010-04-27
I came across an old USB Linex FM Transmitter and the Zareason Ion Breeze desktop sound now works, sending sound out the USB  and I tune my stereo to 107.5 FM.  

I have a similar problem on my Dell 1505n Ubuntu laptop, speakers stopped working.  Will post your command output here.

---

### Post by LinuxBob on 2010-04-27
> **lidex said:**
> I'd hold off on removing that option line for a moment. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

bob@dell-desktop:~$ uname -a
Linux dell-desktop 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux
bob@dell-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
bob@dell-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
bob@dell-desktop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9200

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa



I think the no sound cards found is a problem.  I don;t know why there would be no sound card as I haven;t touched the internals of this Dell Ubuntu laptop.

---

### Post by lidex on 2010-04-27
Try upgrading alsa. Click on the alsa-upgrade-script link in my sig. 
What is the laptop model number? Was this for the 1505n?

---

### Post by bruncit on 2010-04-29
me have the problem too

ummi@ciboi:~$ uname -a
Linux ciboi 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
ummi@ciboi:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ummi@ciboi:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
ummi@ciboi:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B2X5

==> /proc/asound/card0/codec#2 <==
Codec: Nvidia MCP78 HDMI

---

### Post by lidex on 2010-04-29
> **bruncit said:**
> me have the problem too

ummi@ciboi:~$ uname -a
Linux ciboi 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
ummi@ciboi:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ummi@ciboi:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
ummi@ciboi:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B2X5

==> /proc/asound/card0/codec#2 <==
Codec: Nvidia MCP78 HDMI

Please start a new thread and detail the problem.

---

### Post by LinuxBob on 2010-05-03
> **lidex said:**
> Try upgrading alsa. Click on the alsa-upgrade-script link in my sig. 
What is the laptop model number? Was this for the 1505n?

Yes 1505n

I will try the script when I get home tonight

---

