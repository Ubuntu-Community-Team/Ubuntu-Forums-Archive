---
title: "No sound with Ubuntu 10.04 (Sony Vaio VPCEE3WFX)"
date: 2011-01-02
forum: Multimedia Software
---

### Post by ecmmyers on 2011-01-02
Hello.
I just installed Ubuntu three days ago, so I am a TOTAL novice about troubleshooting Linux.

When I installed Ubuntu on my new laptop (Purchased 5 days ago) I could not play sound from the speakers or from the headphone jacks.

My laptop has the latest Also 1.0.23 thing(read from another post)

I ran ```
cat /proc/asound/version
```
and got
```
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Dec  2 2010 for kernel 2.6.32-27-generic (SMP).

```

I ran ```
aplay -l
```
and got
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I really don't know how to go about solving this problem, but sound is really important to me and I don't want to go back to Windows...

---

### Post by ecmmyers on 2011-01-02
I thought I might also add that I ran
```
lspci | grep -i audio
```
and got
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
```

also: ```
cat /proc/asound/card0/codec#* | grep Codec 
```
returned
```
Codec: Realtek ALC259
```

---

### Post by ecmmyers on 2011-01-02
Perhaps this information will be useful to someone. I found a command on the sound troubleshooting page which uploaded a lot of data about my system. the link is here:

[http://www.alsa-project.org/db/?f=1b92880f8d8796d9b11bd3a8ac3b078cc7fda596]("http://www.alsa-project.org/db/?f=1b92880f8d8796d9b11bd3a8ac3b078cc7fda596")

---

### Post by lidex on 2011-01-02
Let's start here. Try updating your alsa-driver-modules.
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

### Post by ecmmyers on 2011-01-02
Alright. Good news. I got sound to play on my laptop. However, whenever I restart it, the <Speaker> is reset to 0. What do you suggest I do about this?

---

### Post by lidex on 2011-01-02
Use alsamixer to set your levels where you want then run this command:
```
sudo alsactl store 0
```

---

### Post by ecmmyers on 2011-01-02
Alright, and I cannot thank you enough. 

I ran alsamixer and set the speaker to where I wanted then ran the command you posted above. When I restarted it again, it did not seem to have saved it. It was back at 0. I tried saving it twice to little avail. Any ideas?

---

### Post by lidex on 2011-01-03
First try these terminal commands:
Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

### Post by ecmmyers on 2011-01-03
I'm going to go ahead and mark this as solved. When I was working on this and another problem of mine, I accidentally messed up my graphics driver, and had to reinstall Ubuntu. Although I had the same sound problem you were helping me with, i worked it out with this tutorial ([http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/"))combined with the advice you gave me above.

this time I have sound on startup without enabling the speakers with alsamixer.

Many thanks!

---

