---
title: "No sound SB Audigy Ubuntu 10.04"
date: 2010-09-03
forum: Multimedia Software
---

### Post by Priswell on 2010-09-03
I recently upgraded to 10.04 on my homebuilt computer. I have Soundblaster Audigy as a soundcard. What little sound I get is horribly scratchy with about 3/4 scratchy, 1/4 sound. 

I have checked to see that the speakers work by testing them on another machine. About halfway through this process, noted below, I bought a new Soundblaster Audigy card and installed that.

aplay -l gives me:

```
** (gnome-alsamixer:2001): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Analog Source"!

** (gnome-alsamixer:2001): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Digital Source"!

** (gnome-alsamixer:2001): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Shared Mic/Line in"!
dennis@tilda:~$ gnome-alsamixer

** (gnome-alsamixer:2008): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Analog Source"!

** (gnome-alsamixer:2008): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Digital Source"!

** (gnome-alsamixer:2008): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Shared Mic/Line in"!
dennis@tilda:~$ gnome-alsamixer

** (gnome-alsamixer:2014): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Analog Source"!

** (gnome-alsamixer:2014): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Digital Source"!

** (gnome-alsamixer:2014): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Shared Mic/Line in"!
dennis@tilda:~$ gnome-alsamixer

** (gnome-alsamixer:2026): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Analog Source"!

** (gnome-alsamixer:2026): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Digital Source"!

** (gnome-alsamixer:2026): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Shared Mic/Line in"!
dennis@tilda:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v  (sound segment) gives me:

```
01:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at ac00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

```

so I know that my module is: snd-ca0106

I have played with the settings under System > Preferences > Sound Preferences and  uninstalled and reinstalled gnome-alsamixer. From there, I bought an installed a new Soundblaster Audigy card. Then, I reinstalled the entire OS, hoping for a miracle. No dice. I keep going round and round. Any help?

---

### Post by lidex on 2010-09-05
Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

---

### Post by Priswell on 2010-09-08
*make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.*

Thank you for responding. The analog/digital check box is unchecked. Any other ideas?

---

### Post by Priswell on 2010-09-30
Can anybody offer any additional help? Here's my lspci -v for my sound:

01:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 1006
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at ac00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

Is there any other information I can give you to help me?

---

### Post by lidex on 2010-09-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Priswell on 2010-12-06
The link you gave me generated this link:

[http://www.alsa-project.org/db/?f=60807b55367181c971968df37d67ea62a1e837ad](http://www.alsa-project.org/db/?f=60807b55367181c971968df37d67ea62a1e837ad)

What do I do next?

---

### Post by AnxietyDrive on 2010-12-08
I took the liberty of using your data gathering script and generating this link to my system  data as well .

I have no sound what so ever On a fresh 10.04 install
An pointers would be greatly appreciated

AD

[http://www.alsa-project.org/db/?f=8e5ee461cacdc948e621b8e7024e2fc55ecd5879]("http://www.alsa-project.org/db/?f=8e5ee461cacdc948e621b8e7024e2fc55ecd5879")

---

### Post by lidex on 2010-12-08
> **AnxietyDrive said:**
> I took the liberty of using your data gathering script and generating this link to my system  data as well .

I have no sound what so ever On a fresh 10.04 install
An pointers would be greatly appreciated

AD

[http://www.alsa-project.org/db/?f=8e5ee461cacdc948e621b8e7024e2fc55ecd5879]("http://www.alsa-project.org/db/?f=8e5ee461cacdc948e621b8e7024e2fc55ecd5879")

Firstly, your code is an AC'97 driver , not hda-intel. More specifically snd-intel8x0, so remove any lines you added to alsa-base.conf and update your alsa install via the link in my sig.

---

### Post by AnxietyDrive on 2010-12-08
Hi Lidex

Couldn't recall the changes made to alsa-base.cfg if any so I decided to put a fresh 10.04 install in and send you a new link.

So apart from the Ubuntu updates after installation this is vanilla.

If you need any further info just let me know.

[http://www.alsa-project.org/db/?f=ca9cf62a4c74a035c17ffd198a8c812c114f6665]("http://www.alsa-project.org/db/?f=ca9cf62a4c74a035c17ffd198a8c812c114f6665")

---

### Post by lidex on 2010-12-08
@AnxietyDrive
OK. Let's try this first. Rather than a full upgrade to alsa try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by AnxietyDrive on 2010-12-09
Hi lidex.

Did all above to no avail! 

I think first before we go on and I end up wasting your time, I need to take a step back and do a little hardware testing.

The  history is that this is a replacement MB that I needed to replace one that died and a new gfx card as i needed one with Model 2 shader capability to run Eve Online.

So this board/cpu is second hand, though from a reputable supplier. The GFX is new though quite an old model.

So before we go an further I'm going to make sure that the MB/sound chip works .... Not sure what's the easiest way.. so I'm going to install XP just to test that the output does work - then put a new install of 10.04 on and get back to you here.

Ill post up all the system tech info and any other details and see where to go.

If however - there's a MB fault - Ill need to raid the piggy bank :(

Thanks for now

AD

---

### Post by otakuj462 on 2010-12-23
> **lidex said:**
> Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.

I was having the same issue with this sound card on Ubuntu 10.04: no sound. Switching the Analog/Digital checkbox in alsamixer solved this problem for me and I now have perfect audio. Thanks for the tip!

---

### Post by moma on 2010-12-23
Hello,
I have also old SoundBlaster Audigy 2 sound card. I that model the settings should be set like [this...]("http://www.futuredesktop.org/#guides") (follow the link to a picture).

Merry XMas.

---

### Post by Priswell on 2011-01-05
Thank you for responding, but I don't have some of those settings. The only thing that gives me any output at all is clicking the IEC958 button, but it's horribly raspy and not very loud. I also get this output in terminal:

(gnome-alsamixer:4745): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Digital Source"!

Here's a screenshot of my alsamixer

[http://tinypic.com/view.php?pic=2cngr39&s=7](http://tinypic.com/view.php?pic=2cngr39&s=7)

---

### Post by Tomlin on 2011-07-25
> **lidex said:**
> @AnxietyDrive
OK. Let's try this first. Rather than a full upgrade to alsa try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Thanx lidex. This is one **BIG** sticky, but your solution got my sound back on 10.10. I wish everyone good luck.

---

### Post by lkjoel on 2011-07-27
Try Sound Troubleshooting in my signature

---

