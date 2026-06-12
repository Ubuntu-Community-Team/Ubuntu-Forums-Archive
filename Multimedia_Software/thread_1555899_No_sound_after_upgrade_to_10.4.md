---
title: "No sound after upgrade to 10.4"
date: 2010-08-18
forum: Multimedia Software
---

### Post by ChiefSmash on 2010-08-18
Hello everyone-
I am relatively new to the world of Ubuntu and I know others have had very similar problems but I have yet to find a solution.  I recently upgraded to 10.4 and lost my sound.  I tried installing and uninstalling PulseAudio and various ALSA utilities but I have not been able to resolve my issue.  Strangely, when I try to play an mp3 in an application like VLC and then open up the PulseAudio volume control, I can see a playback bar as if an audio signal is going out.  I am not, however, able to hear any sound via internal speaker, analog headphones, usb headset, etc.

I ran aplay -l and got the following result:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I also ran an lspci -v and got:

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 12bc
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1000 [size=256]
	I/O ports at 1400 [size=64]
	Memory at fc480400 (32-bit, non-prefetchable) [size=512]
	Memory at fc480600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
```

Any tips or help would be greatly appreciated.  

Thanks in advance

---

### Post by lidex on 2010-08-19
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by Wäschekorb on 2010-08-19
Cool...I got it! Thanks a lot

---

### Post by ChiefSmash on 2010-08-20
Ok thanks again for the help!  Here's a link to the output of alsa-info.sh:

[http://www.alsa-project.org/db/?f=ee7a6bd9ad8a4c67a3968b286c074d22f07c88bc](http://www.alsa-project.org/db/?f=ee7a6bd9ad8a4c67a3968b286c074d22f07c88bc)

---

### Post by lidex on 2010-08-20
You might try upgrading your alsa install using the link in my sig. First uninstall alsa-backports and make sure you have installed build essential:
```
sudo aptitude install build-essential
```

Also, what is the output of this command:
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

---

### Post by ChiefSmash on 2010-08-23
Ok I uninstalled the backports and ran the upgrade download/compile/install script from your sig.  I also ran the build-essential install.  Everything seemed to go well.

The output of the command you mentioned is:

```


sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  myusername    2470 F.... pulseaudio
/dev/snd/pcmC0D0p:   myusername    2651 F...m chrome
/dev/snd/timer:      myusername    2651 f.... chrome

```

So I guess PulseAudio is not gone afterall.

---

### Post by urbinbliss on 2010-08-23
The last kernel update broke my sound. I had to go back to 2.6.32-23.

lspci -v
```
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: ABIT Computer Corp. Device 1c13
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at f000 [size=256]
	I/O ports at ec00 [size=256]
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	[B][I]Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0[/I][/B]
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: ***Intel ICH*** [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: ***Intel ICH*** - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

A little similarity there. I don't mean to high-jack, just suggesting that you might be able to go back to an earlier kernel.

EDIT; solved my problem thanks to this post [http://ubuntuforums.org/showthread.php?t=1557572](http://ubuntuforums.org/showthread.php?t=1557572)
For some reason my user wasn't part of the audio group, witch doesn't seem to matter with the earlier kernel.

---

### Post by lidex on 2010-08-23
> **ChiefSmash said:**
> Ok I uninstalled the backports and ran the upgrade download/compile/install script from your sig.  I also ran the build-essential install.  Everything seemed to go well.

The output of the command you mentioned is:

```


sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  myusername    2470 F.... pulseaudio
/dev/snd/pcmC0D0p:   myusername    2651 F...m chrome
/dev/snd/timer:      myusername    2651 f.... chrome

```

So I guess PulseAudio is not gone afterall.
Try removing your old config files.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**
Ignore any not found errors.

---

### Post by ChiefSmash on 2010-08-24
Ok I just decided to re-test with my headphones plugged into the front jack and, voila, I have sound!  So somewhere along the way my audio started working again through the front headphone port and rear speaker port.  I just need to get it coming through my internal speaker again and I'm all set.  Thanks everyone for the help!

---

### Post by lidex on 2010-08-24
> **ChiefSmash said:**
> Ok I just decided to re-test with my headphones plugged into the front jack and, voila, I have sound!  So somewhere along the way my audio started working again through the front headphone port and rear speaker port.  I just need to get it coming through my internal speaker again and I'm all set.  Thanks everyone for the help!

Is this a laptop? I thought it was a desktop, in which case no internal speakers.

---

### Post by ChiefSmash on 2010-08-25
Yeah I know it's not normal but it's an HP Compaq slim form factor desktop with an internal speaker.

---

### Post by lidex on 2010-08-25
One speaker? How about this control:
> Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]


May need to enable in gnome-alsamixer:
> control.5 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Mono Playback Switch'
		value false
	}
	control.6 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 31'
		comment.dbmin -4650
		comment.dbmax 0
		iface MIXER
		name 'Master Mono Playback Volume'
		value 0


---

### Post by ChiefSmash on 2010-08-30
Thanks very much for the help.  I already have that control enabled in gnome-alsamixer but as I was working on this, a friend came by and gave me a new pair of speakers to use with this box.  So essentially my problem is solved.  Again I really appreciate the time and effort on this issue.

---

