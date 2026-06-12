---
title: "Winfast 2000XP Expert TV-tuner very quiet, bad quality sound"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by NobeyamaGP on 2007-03-05
I am running Kubuntu Edgy Eft and am trying to get my Winfast TV2000XP Expert tv tuner working. I currently have TVtime, kdetv, xawtv and mplayer installed. I have gotten video working in tvtime, kdetv, and mplayer. Xawtv just gives me a black screen and static. On tvtime, kdetv, and mplayer though, I am getting very quiet, poor sound quality. I have the audio jumper connected to my onboard sound AUX connecter. I have turned Aux all the way up in alsamixer and still the sound is very poor. My sound system's volume setting I use for listening to music in Amarok is around 12, but to get any sound at all from tvtime, etc. I have to set it to at least 26 (30 is max)! The sound is also very high pitched with almost no low tones at all. Even through the Composite input with my PS2 I get no increase in sound quality over cable tv. Does anyone have any idea what I can do to make this work? 

Kernel version: 2.6.17-11-generic
Tuner uses cx88xx driver
(sound specs according to alsamixer):
Sound Card: NVidia CK8S (onboard a ASUS K8N-E Deluxe mobo)
Sound Chip: Realtek ALC850 rev 0

Thanks. Let me know if you need anymore information.

---

### Post by david_2001 on 2007-03-05
Do you have alsa-oss installed?  Just a thought, as the likes of tvtime and xawtv want to use oss devices (/dev/dspN and /dev/mixerN) rather than alsa for sound.

---

### Post by NobeyamaGP on 2007-03-05
Actually, I did not have alsa-oss installed, but after installing it, there was no change in sound quality. Do I have to configure it or something? Thanks.

---

### Post by david_2001 on 2007-03-06
Hmm.  Googling around suggests that there were sound problems with this card, though this was a year or two ago.  Can you just confirm that the card is being detected correctly by the cx88 driver.  According to the cx88 pages on LinuxTV, it should be card
> 5 -> Leadtek Winfast 2000XP Expert                       [107d:6611,107d:6613]
Also, now that you have alsa-oss, there should be an oss mixer for the motherboard sound chip.  Check that aux is not muted in the oss mixer.

EDIT: While I'm thinking about this, what's the effect of muting any line-in while the TV card is playing through aux?

---

### Post by NobeyamaGP on 2007-03-06
Ok, lspci -v gives me this: ```
02:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: LeadTek Research Inc. Leadtek Winfast 2000XP Expert
        Flags: bus master, medium devsel, latency 64, IRQ 209
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
```

I can't seem to find the oss mixer to check what it says. Muting line in does nothing to the sound coming from the tuner through Aux. Thanks for the help.

---

### Post by david_2001 on 2007-03-07
This is a bit of a puzzler but let's assume that there's nothing broken in the cx88 driver and carry on.  I used to use a Leadtek PVR2000 card that was connected to the motherboard aux input and never had a problem getting sound.  To check the card identity, see what you get from the following:
```
dmesg | grep card=
```
Regarding the oss mixer for the motherboard sound, open the Gnome Volume Control and select File | Change Device.  In the attached screenshot the oss mixer for the motherboard sound on my PC is the third entry.  While you're there, make sure that all of the possible sound inputs/outputs are showing by selecting Edit | Preferences for each sound device.

---

### Post by NobeyamaGP on 2007-03-07
```
dmesg | grep card=
``` gave me this ```
[17179595.420000] CORE cx88[0]: subsystem: 107d:6613, board: Leadtek Winfast 2000XP Expert [card=5,autodetected]
```
As for the mixer, I'm using Kubuntu so that means KDE and kmix doesn't have that option that I can find.

---

### Post by david_2001 on 2007-03-08
Ok, the card identity is correct.  Now try this.  Create a file in /etc/modprobe.d containing the following (it doesn't matter what the file is called - "tda9887" will do):
```
options tda9887 port1=0 port2=0
```
The following command will do the job:
```
sudo sh -c 'echo "options tda9887 port1=0 port2=0" > /etc/modprobe.d/tda9887'
```
If the TV standard where you are is SECAM, try
```
options tda9887 qss=1 port1=0 port2=0 secam=1
```
Reboot  and then have another go.

EDIT: I've just had a rummage through my old backups from when I was using the PVR2000.  In addition to the port1=0 port2=0 options for the tda9887 tuner, I was also using a couple of cx88 options that, modified for your card, would be:
```
options cx88xx i2c_scan=1 card=5
```
Either put them in the tda9887 file or make another one in /etc/modprobe.d.

---

### Post by NobeyamaGP on 2007-03-09
Neither the tda9887 options nor the cx88xx options had any effect. The tv standard here is NTSC.

---

### Post by david_2001 on 2007-03-09
Change the options for tda9887 to "options tda9887 port2=0" and reboot.  After that, I'm afraid that you'll have to do what Google suggests that others have had to do to get sound when there has been a problem: Basically, just fiddle about with the settings in KMix until it works.  For example, muting Surround has been reported as a solution in one instance.

Just out of curiosity, does KMix allow you to select a cx88-alsa device?

---

### Post by NobeyamaGP on 2007-03-12
Sorry I haven't replied sooner. I'm at home for spring break and there isn't much of an internet connection here. I just tried your suggestion and no luck. I've also tried muting and unmuting various options in both kmix and alsamixer, neither of them changed anything. As near as I can tell, kmix doesn't allow for changing devices and there is no cx88-alsa device present. The only device that changes anything dealing with the tuner is "Aux".

Do you think it would be worth looking into getting a different tuner? I have some friends who would probably buy this one. Or do you think I should just wait and see if the next version of Kubuntu fixes things? I may also try booting knoppix and see if the sound works there. Thanks for all your help.

---

### Post by rea on 2007-05-03
AUX in Leadtek 2000xp expert:

```
gedit /etc/tvtime/tvtime.xml
```

and change 

```
<option name="MixerDevice" value="/dev/mixer:line"/>
```

to

```
<option name="MixerDevice" value="/dev/mixer:line1"/>
```

---

### Post by beefbowel on 2007-11-11
can you describe how you got your card the 2000xp expert to work?  i cannot get any type of signal in any player.  i have the same card.  thanks.

---

