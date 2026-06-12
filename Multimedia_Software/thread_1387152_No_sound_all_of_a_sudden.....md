---
title: "No sound all of a sudden...."
date: 2010-01-21
forum: Multimedia Software
---

### Post by Enigmapond on 2010-01-21
I have had Ubuntu since early last year and have never had a sound issue. Today, I have no sound. I checked the threads and followed the "sticky" tutorial with no results. I have uninstalled both Alsa and Pulse and re-stalled them...still nothing. I am at a loss. I checked the alsa mixer and nothing is muted and all volumes are up.

Any Suggestions?:confused:

---

### Post by Enigmapond on 2010-01-21
Ok...let me re-phrase. I did something to the sound...I have no idea what. Is there anyway I can find out what I did and fix it...it had something to do with Alsa Mixer but I don't know. Also if I just upgrade to Karmic, will it solve the problem? I mean the sound worked this morning....any help would be appreciated.

---

### Post by Enigmapond on 2010-01-21
:confused:

---

### Post by Enigmapond on 2010-01-21
I love this I'm running my own thread...however talking to myself..just isn't doing it...

So I just did an upgrade to 9.10 thinking that the problem would fix itself..well it hasn't. Can someone throw some suggestions out to I can fix this...still no sound.

Thank you in advance...:(

---

### Post by Steve H on 2010-01-23
Yeah, weirdly I'm having same problems.

I've checked my ALSA settings and tried various media players iplayer etc but no sound on anything all of a sudden. I haven't changed anything in PulseAudio or any of the configs.

What updates have gone on recently?

I've tried removing PulseAudio (the usual culprit) using:
[B]
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer[/B]

But that hasn't worked...

I've now tried reinstalling Pulse but that hasn't worked either.

This is annoying because it all worked the other day, the only thing that has changed is the updates from yesterday...

---

### Post by decmulhall on 2010-01-23
I'm having exactly the same issue. I did all shenanigans with pulseaudio and alsa. When I had pulseaudio on, the output meters responded as thought there was sound coming out the speakers.
This is so annoying, I'm on the verge of installing fedora.
Can someone help?
Dec

---

### Post by Steve H on 2010-01-23
Yeah, I noticed the monitors were moving as well.

:confused:

---

### Post by LuridCinema on 2010-01-23
Sound chip on MoBo dead or External Sound card dead ?? <<<<< OR updates not compatible w/

---

### Post by Steve H on 2010-01-23
Nah! Can't be my sound card because it works perfectly in XP.

I've got an M-Audio2496 which uses ICE1712 driver.

I managed to get sound out by killing pulse and loading the ASLA modules, but that caused other problems (like my USB mic not working).

---

### Post by papahonk on 2010-01-23
same here sound was working just before updates  and now they are not.  how do i go back and double check what i updated?

---

### Post by Steve H on 2010-01-24
I've got a bit further with this.

I upgraded ALSA to 1.0.21 as instructed [here]("http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/"). Then changed Default Output on gstreamer-properties to Auto Detect.

Which at least allowed YouTube, Audacious and iPlayer to get some sound.

Now I can't get RhythmBox, Songbird or VLC to play anything. They all look like they are playing, as the progress bar is moving, but there is no actual output through the analogue speakers.

I'm starting to think it something to do with Pulseaudio mishandling the ICE1712 drivers.

Well, I'll keep looking for a complete fix.

---

### Post by Steve H on 2010-01-24
Finally got it all sorted!!

It would appear that Pulseaudio wasn't playing nice with the multiple channels of the M-Audio 2496 card, using the ICE1712 driver. It would only allow output through the digital outputs, no analogue stereo out. I noticed it played fine from ALSA, but once routed through Pulse then no sound output.

I found a post [**_here_**]("http://help.lockergnome.com/linux/Audio-Sound-Card-Fix-Ubuntu-10-karmic-SOLVED--ftopict508767.html") and added the required lines to  /usr/share/alsa/cards/ICE1712.conf

```
sudo gedit /usr/share/alsa/cards/ICE1712.conf 
```

then place the following lines after the <confdir: pcm/front.conf> replacing the lines already in there

```

ICE1712.pcm.front.0 {
@args [ CARD ]
@args.CARD {
type string
}
type route
ttable.0.0 1
ttable.1.1 1
slave.pcm {
type hw
card $CARD
}
slave.format S32_LE
slave.channels 10
}
``` 

Worked for me, after a few tweaks in Pulse Volume Control to set the Internal Audio (Configuration tab) to Analog Stereo Output.

Bingo! I have sound in all my media players again!!

---

### Post by edmonds on 2010-01-27
hi steve tried this - still didn't work .
tried many many suggestions over last couple of days.
still got the same problem.
pulse works - when i plat a tune Pulse Volume controller recognises it and has a sound graphic bouncing  up  and down. (but dummy output)
i have an Envy/ice driver installed. (but Envy 24 controller blank)

But i have no sound card?:
aplay -l: aplay: device_list:223: no soundcards found...

How do i get my sound card M-audio 2496 found?
It was working  fine and has for years. I often get sound problems with upgrades, normally fixed by now.

tom

---

### Post by Steve H on 2010-01-29
I don't want to sound trite here but what have you tried so far? I'll have a better idea of how to help if you can narrow down my search options a bit.

Have you got any onboard sound chips conflicting?

Have you removed and reinstalled the ICE1712 driver via synaptic/cli?

Have you got analogue outputs available through sound properties? If so are they selected?

;)

Let me know and I'll do my best to help you out

---

### Post by edmonds on 2010-01-29
no problem 
i have reintsalled alsa following  this:
[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

i have edited pulse and alsa conf following  this:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)

i have an onboard sound card but it turned it off in  bios and it does not show:
lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
05:01.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

i cant work out if alsa exists:
cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

but
sudo /etc/init.d/alsa-utils start
 * Setting up ALSA...        [ok]

cat /etc/modules.conf
cat: /etc/modules.conf: No such file or directory

 lsmod
Module                  Size  Used by
nfs                   271816  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetadp             78536  0 
vboxnetflt             85032  0 
vboxdrv               121352  1 vboxnetflt
nfsd                  241104  9 
lockd                  67724  2 nfs,nfsd
nfs_acl                 2844  2 nfs,nfsd
auth_rpcgss            36672  2 nfs,nfsd
sunrpc                191776  13 nfs,nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                4412  1 nfsd
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
asus_atk0110            8252  0 
psmouse                56500  0 
serio_raw               5280  0 
nvidia               9586440  26 
sbp2                   22888  0 
ieee1394               86596  1 sbp2
lp                      8964  0 
parport                35340  2 ppdev,lp
floppy                 54916  0 
sky2                   46560  0 
intel_agp              27676  0 
agpgart                34988  2 nvidia,intel_agp

aplay -l
aplay: device_list:223: no soundcards found...

i do still have:
Create a file /etc/udev/rules.d/ice1712-pulseaudio-workaround.rules with the following contents:

---
SUBSYSTEM!="sound", GOTO="ice1712_end"
ACTION!="change", GOTO="ice1712_end"
KERNEL!="card*", GOTO="ice1712_end"

SUBSYSTEMS=="pci", ATTRS{vendor}=="0x1412", ATTRS{device}=="0x1712", ATTRS{subsystem_vendor}=="0x1412", ATTRS{subsystem_device}=="0xd634", ENV{PULSE_PROFILE_SET}="via-ice1712.conf"

LABEL="ice1712_end"
---

but it made no difference form what i can tell pulse has always workd fine - ie if i play some thing  and og to Pulse vilume contril the device is seen and the volume level bounces up  and down.

what i cant work out is:is alsa there, where i smy soundcard??

it all worked fine until last weeks update - is karmic was ok , but a more recent upgrade has killed something.

thanks for replying

---

### Post by zhenbanjiezhuan on 2010-03-08
> **Steve H said:**
> Yeah, weirdly I'm having same problems.

I've checked my ALSA settings and tried various media players iplayer etc but no sound on anything all of a sudden. I haven't changed anything in PulseAudio or any of the configs.

What updates have gone on recently?

I've tried removing PulseAudio (the usual culprit) using:
[B]
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer[/B]

But that hasn't worked...

I've now tried reinstalling Pulse but that hasn't worked either.

This is annoying because it all worked the other day, the only thing that has changed is the updates from yesterday...


it's not working to you??? it's working to me!!!! thank you!!

---

### Post by Sam Fallow on 2010-03-09
> **Steve H said:**
> Yeah, weirdly I'm having same problems.

I've checked my ALSA settings and tried various media players iplayer etc but no sound on anything all of a sudden. I haven't changed anything in PulseAudio or any of the configs.

What updates have gone on recently?

I've tried removing PulseAudio (the usual culprit) using:
[B]
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
sudo apt-get install alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base alsamixergui
sudo apt-get install esound esound-clients esound-common libesd-alsa0 gnome-alsamixer[/B]

But that hasn't worked...

I've now tried reinstalling Pulse but that hasn't worked either.

This is annoying because it all worked the other day, the only thing that has changed is the updates from yesterday...

Thanks for this. 
Lost my sound while going into hibernation while playing a game? Sound was there at login screen but not in desktop. 
Used the above sequence and all is well again.

---

### Post by sudoCrushMS on 2011-02-07
I had the same issue with this, and found a solution (after accidentally uninstalling my desktop environment with PulseAudio).

Code:
sudo apt-get remove --purge pulseaudio gstreamer0.10-pulseaudio

Then:
gstreamer-properties

Set all defaults to ALSA

This worked for me (Dell Latitude e5500); however, I've been working on a Macbook Pro with the same problem and this solution has not worked (still working on it).

---

