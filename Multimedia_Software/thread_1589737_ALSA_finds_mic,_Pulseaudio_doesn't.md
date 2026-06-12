---
title: "ALSA finds mic, Pulseaudio doesn't"
date: 2010-10-06
forum: Multimedia Software
---

### Post by kjkoec on 2010-10-06
Ahoy hoy,
Since upgrading ,my laptop to Lucid I haven't been able to use my line-in (mic).  I finally looked around trying to find a fix, but couldn't find anyone with the same problem.

Pulseaudio doesn't show any inputs unless I set my card to Duplex (or input + output).  And even when I do, only the volume monitor works; the mute button and volume slider are useless.
**Screenshots**
[ -Setting to Duplex...]("http://picasaweb.google.com/lh/photo/Plu0752EXCZIyvFiC2-WIQ?feat=directlink")
[-Controls won't work...]("http://picasaweb.google.com/lh/photo/mghn6P_3lK7t-d3wMq8DFw?feat=directlink")

ALSA seems to find it, however.  It calls it "Front Mi(c)."  The "ATAPI Mi(c)" is just a cheap stereo mic built in to the laptop (doesn't matter, but also doesn't work).  I'm not sure what "Capture" is...
[IMG]http://lh6.ggpht.com/_nmFSm6mJOHg/TK0cM5Yh0DI/AAAAAAAAAoM/T97TyYc0-Gs/s800/ALSAmix.png[/IMG]

Card is a Realtek ACL861-VD.  Laptop is a 64-bit HP tx1410us.  Any help would be appreciated.  :)

---

### Post by lidex on 2010-10-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by kjkoec on 2010-10-07
Here you are:
[http://pastebay.com/106440](http://pastebay.com/106440)

---

### Post by lidex on 2010-10-07
OK. I want you to remove the alsa-base.conf entries and reboot,

---

### Post by kjkoec on 2010-10-07
cleared and rebooted...

---

### Post by lidex on 2010-10-07
> **kjkoec said:**
> cleared and rebooted...

Any changes?
Try updating your alsa-driver-modules.
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

### Post by kjkoec on 2010-10-08
Alas, no change in functionality from what I can see.  When I set my card to input+output, however, I now see the "input" pulseaudio finds is actually what alsa calls 'Capture.'

---

### Post by lidex on 2010-10-08
Can you run the alsa-info script again please?

---

### Post by kjkoec on 2010-10-08
> **lidex said:**
> Can you run the alsa-info script again please?
[http://www.alsa-project.org/db/?f=da8e74610eaf5e90f01fb7a0d1c6c5edcecc6a11](http://www.alsa-project.org/db/?f=da8e74610eaf5e90f01fb7a0d1c6c5edcecc6a11)

---

### Post by lidex on 2010-10-08
Good. Now re-add only the one line to alsa-base.conf:
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp 
```
Save. Close. Reboot. 
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

### Post by kjkoec on 2010-10-13
Sorry for the delay, 
I was forced to reinstall ubu after a failed hibernation during the update.  Apparently, in alsamixer, one can set the default mic for "capture."  I guess pulseaudio only has control over the mic when it is being accessed by a program.  Without a recording program, I can hear the mic faintly through my laptop's built-in speakers (no way around that, I suppose), not simultaneously through usb ones.  Audacity works, and that's all I wanted in the first place.

Thanks for your help, much appreciated.

---

### Post by yelvington on 2010-10-17
I'm having what may be the same problem. On a system upgraded from Lucid to Maverick, I'm not able to get Skype to hear the microphone. The Pulseaudio sound prefs tool shows no activity.

However, both the Sound Recorder utility and Audacity have no trouble picking up a signal.

Adding autospawn=no to .pulse/client.conf makes Skype see a whole bunch of input options, and "default" works, so it's possible to make Skype calls. 

However it seems to break the Indicator Applet's sound output volume control and does keyboard control of sound volume also fails.

also-info.sh output is at
[http://www.alsa-project.org/db/?f=22ba25f8e8e77fec3822482c8485cea0deb1fb5f](http://www.alsa-project.org/db/?f=22ba25f8e8e77fec3822482c8485cea0deb1fb5f)

---

### Post by lidex on 2010-10-17
> **yelvington said:**
> I'm having what may be the same problem. On a system upgraded from Lucid to Maverick, I'm not able to get Skype to hear the microphone. The Pulseaudio sound prefs tool shows no activity.

However, both the Sound Recorder utility and Audacity have no trouble picking up a signal.

Adding autospawn=no to .pulse/client.conf makes Skype see a whole bunch of input options, and "default" works, so it's possible to make Skype calls. 

However it seems to break the Indicator Applet's sound output volume control and does keyboard control of sound volume also fails.

also-info.sh output is at
[http://www.alsa-project.org/db/?f=22ba25f8e8e77fec3822482c8485cea0deb1fb5f](http://www.alsa-project.org/db/?f=22ba25f8e8e77fec3822482c8485cea0deb1fb5f)

I believe the indicator applet relies on pulseaudio.
Have you seen the 1410 page at linlap.com?
> Microphone
Making the microphone work

Install Alsa Mixer from the Ubuntu Software center and use it to push Capture level to maximum. You will find it in Applications &#8594; Sound & Video &#8594; Alsa mixer). Don't forget to check the Rec checkbox for capture. Sadly there is still some electrical noise (Check with sound recorder)

You may also install the package “linux-backports-modules-alsa-karmic-generic” with the synaptic package manager and the internal microphone should work. (in the Ubuntu system menu under “System” > “Administration” > “Synaptic Package Manager”).

To use the terminal to achieve the same thing type :

sudo apt-get install linux-backports-modules-alsa-karmic-generic

On Ubuntu 10.04 and 10.10, this package doesn't exist. I was able to fix the problem by adding the following line to /etc/modprobe.d/alsa-base.conf:

options snd_hda_intel model=basic

Making the internal microphone work with Skype

To use the internal mic with Skype, start Skype with

/bin/sh -c "PULSE_SERVER=127.0.0.1 skype" &

It can be done automatically by editind the Application menu:
- Right click on the Applications menu (on the upper left side of the screen) and select Edit menus
- Click on Internet in the right panel
- Select Skype
- Click Properties
- Replace skype by /bin/sh -c “PULSE_SERVER=127.0.0.1 skype” &
- Close and check if it works (you need to restart Skype if it was already up and running)

Reference:
[http://www.linlap.com/wiki/acer+aspire+1410](http://www.linlap.com/wiki/acer+aspire+1410)

---

### Post by yelvington on 2010-10-18
> **lidex said:**
> I believe the indicator applet relies on pulseaudio.
Have you seen the 1410 page at linlap.com?

Reference:
[http://www.linlap.com/wiki/acer+aspire+1410](http://www.linlap.com/wiki/acer+aspire+1410)

I tried the bin/sh -c "PULSE_SERVER=127.0.0.1 skype" & trick ... actually, since the menu entry points to a shell script, I used that instead of a direct call to skype. This had some interesting side effects, none of them good. "default" disappeared and a bunch of hardware devices showed up in Skype's configuration, but none of them worked. So I reverted.

Then I stumbled across something very odd. In the PulseAudio volume control tool (applications->sound & video), I clicked on the "Input Devices" tab, clicked on the lock icon to unlock the left and right channels' relationships with one another, and dragged one or other of the sliders up or down.

Suddenly I started getting a bouncy volume indicator.

I tried Skype again, and suddenly I had microphone. I did have to uncheck the option to let Skype control the input level (this was a known workaround for Lucid Lynx). But once I made Skype stop trying to normalize the controls, I was able to use it again.

So far as I know, this laptop does NOT have a stereo microphone. It's behaving as if the left and right channels are crosswired with one another -- in other words, a "left" signal cancels a "right" signal.

It doesn't make any difference whether I run Left up and Right down, or vice versa. Either way makes the audio input start working. The closer they are to matching, the more the input is attenuated, and if they are locked together, there's no sound at all.

Bizarre.

But fixed.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=172778&d=1287444176[/IMG]

---

### Post by Genio on 2010-10-19
Hello,

I had the same problem, the volume of the microphone is too low so you have to force it to more than 100% directly in the PulseAudio Manager. The workaround described at this url resolved the issue:
[https://bugs.launchpad.net/fedora/+source/alsa-lib/+bug/275998]("https://bugs.launchpad.net/fedora/+source/alsa-lib/+bug/275998")

1. sudo apt-get install paman
2. paman
3. Go to devices
4. Double click alsa_input.pci-0000_00_1b.0.analog-stereo
5. Set the volume to ~200% 
6. Click Close

---

### Post by oraqol on 2010-11-04
Mic would work with sound recorder, but once Google Voice was initiated mic would stop working not just for GV, but sound recorder as well until reboot.  Used synaptic to completely remove pulseaudio and install alsa.  Mic now works perfectly.  Also fixed issue with sound suite only allowing either headphone or speakers to function, determined by whichever was set at boot.  Now both work.  Running 10.10 on AMD Turion 2.2 ghz dual core w/ Altec Lansing with SRS Premium Sound.

---

