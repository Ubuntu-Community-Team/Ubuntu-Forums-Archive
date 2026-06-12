---
title: "No sound"
date: 2010-04-04
forum: Multimedia Software
---

### Post by Alt-A on 2010-04-04
I am new to Ubuntu, I have just installed 9.10, unfortunately sound is not working.  I have an 275 gtx video card that is connected via HDMI cable.  The spdif is connected via the motherboard and video card.  Not familiar at all with ubuntu, am a total newbie would appreciate help.

---

### Post by gaspros on 2010-04-04
I am new as well and have sound problems that I have not been able to figure out.
I did find a lot of information at the following web pages so it might help you.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Good luck

---

### Post by Alan James on 2010-04-04
Every time I do a clean install of Linux my sound doesn't work. I usually sit around for about two or three minutes wondering why and checking drivers when I remember that on my computer I have to turn up the &#8220;PCM&#8221; channel's volume. I don't know why this is muted after install but it is. I right click on the volume button and select the master channel as PCM. I turn it up, then select the master channel as Master again. After this my sound works fine. I have had to do this on every distro I install so it MAY be worth checking into for you, even though its a simple fix.

---

### Post by Alt-A on 2010-04-05
I am not really sure what you mean by pdm or pcm, when i right ciick all i get is sound preferences or mute.

---

### Post by Alt-A on 2010-04-05
Hope this information can help someone solve my problem

saira@Saira:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
saira@Saira:~$

---

### Post by RedSingularity on 2010-04-05
In a terminal type 

alsamixer

make sure all the volumes are up.

---

### Post by Alan James on 2010-04-06
> In a terminal type 

alsamixer

make sure all the volumes are up.

Exactly what I was talking about. Make sure "PCM" is turned up all the way. That always works for me.

---

### Post by Alt-A on 2010-04-06
Tried didn't fix it for me.

---

### Post by RedSingularity on 2010-04-06
Post the output of 

lspci -v

There will be a lot of output.

---

### Post by lidex on 2010-04-06
Run these commands in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Now reboot and recheck mixer levels.

---

### Post by Alt-A on 2010-04-06
saira@Saira:~$ lspci -v

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 0900 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 0e00 [size=64]
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82f2

---

### Post by lidex on 2010-04-07
Also what is the output of this command:
```
head -n 1 /proc/asound/card*/codec#*
```

---

### Post by RedSingularity on 2010-04-07
Was that all your output?  It seems too short.

---

### Post by Alt-A on 2010-04-10
Thanks Lidex, that solved my problem, i also had to use digital stereo input iec95856

---

### Post by Alt-A on 2010-04-10
i had sound now its gone again, it came back when i switched between sound types on hardware but now it is not coming back... please help

---

### Post by Alt-A on 2010-04-10
saira@Saira:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#3 <==
Codec: Nvidia MCP78 HDMI
saira@Saira:~$

---

### Post by lidex on 2010-04-10
> **Alt-A said:**
> i had sound now its gone again, it came back when i switched between sound types on hardware but now it is not coming back... please help
Check alsamixer.

---

### Post by Alt-A on 2010-04-14
I have to keep changing sound preferences to make it work, how come it isn't working on start up, please help.

---

### Post by Alt-A on 2010-04-15
again no sound even when i switch the sound preference, this is really getting annoying.  can someone help.

---

### Post by lidex on 2010-04-15
OK. Do this for me. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

IEC958:
[http://ubuntuforums.org/showthread.php?t=877811]("http://ubuntuforums.org/showthread.php?t=877811")

---

### Post by genux05 on 2010-04-15
I have no sound coming out of my front speakers, and I also am using a ALC883 .. it is coming out of my rear speaker on my laptop.

The laptop is a ACER 9815, it has 3 speakers ( one bass at the rear and two at the front)

Here is the output of the util_alsa-info.sh for me

[http://www.alsa-project.org/db/?f=8b6a09c7a40a083810c5561eb453da35d6aad057]("http://www.alsa-project.org/db/?f=8b6a09c7a40a083810c5561eb453da35d6aad057")

any advice ? I have tired different things but nothing appears to help.

---

### Post by lidex on 2010-04-15
> **genux05 said:**
> I have no sound coming out of my front speakers, and I also am using a ALC883 .. it is coming out of my rear speaker on my laptop.

The laptop is a ACER 9815, it has 3 speakers ( one bass at the rear and two at the front)

Here is the output of the util_alsa-info.sh for me

[http://www.alsa-project.org/db/?f=8b6a09c7a40a083810c5561eb453da35d6aad057]("http://www.alsa-project.org/db/?f=8b6a09c7a40a083810c5561eb453da35d6aad057")

any advice ? I have tired different things but nothing appears to help.
Kinda gets messy when you hijack a thread. Can you start a new one and PM me the url please?

---

