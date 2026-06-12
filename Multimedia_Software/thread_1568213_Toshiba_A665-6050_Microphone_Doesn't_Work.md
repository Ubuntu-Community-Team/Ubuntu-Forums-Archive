---
title: "Toshiba A665-6050 Microphone Doesn't Work"
date: 2010-09-04
forum: Multimedia Software
---

### Post by bluefoxox on 2010-09-04
Hey all, I have a Toshiba A665-6050 with a microphone that does not work.  Could someone walk me through getting it to work please?  Thanks!

---

### Post by lidex on 2010-09-05
Would that be internal or external? The basics:

First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by bluefoxox on 2010-09-05
lidex, thanks for the quick reply.  I followed these instructions but still getting the same results (using the sounds recorder as a gauge).  Do you have any further recommendations?

---

### Post by lidex on 2010-09-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by bluefoxox on 2010-09-05
[http://www.alsa-project.org/db/?f=70fea4e87d0dbf1bda4c007a292f1278d863d64a](http://www.alsa-project.org/db/?f=70fea4e87d0dbf1bda4c007a292f1278d863d64a)

---

### Post by lidex on 2010-09-05
Try this, and if it doesn't help, upgrade your alsa install via the link in my sig and try them both again. Make sure you are thoroughly checking gnome-alsamixer and sound preferences to ensure the hardware settings are correct; the correct mic is chosen and enabled, etc.

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
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


The other model is 'basic'

---

### Post by bluefoxox on 2010-09-05
lidex, I followed the instructions in the upgrade, rebooted and everything works perfectly.  Thank you very much!

I was not expecting so many dev upgrades during the process though.  Do I need to be concerned about upgrading in the future?  This was the last concern I had with using Ubuntu on my notebook.

Thank you again lidex!

---

### Post by lidex on 2010-09-06
You're welcome. Please mark the thread solved using 'Thread Tools' up top.

> Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk).


---

### Post by th33nd on 2010-10-16
I have the same problem on my Toshiba Satellite C650. But adding that line does not help.
Microphone was working fine on ubuntu 10.04, but it stopped working when I installed 10.10. [http://www.alsa-project.org/db/?f=5466d3044df876b313d1c1d19e04b237faab5280](http://www.alsa-project.org/db/?f=5466d3044df876b313d1c1d19e04b237faab5280)

---

### Post by bluefoxox on 2010-10-16
> **th33nd said:**
> I have the same problem on my Toshiba Satellite C650. But adding that line does not help.
Microphone was working fine on ubuntu 10.04, but it stopped working when I installed 10.10. [http://www.alsa-project.org/db/?f=5466d3044df876b313d1c1d19e04b237faab5280](http://www.alsa-project.org/db/?f=5466d3044df876b313d1c1d19e04b237faab5280)

Did you check your levels in alsamixer from the command line and the levels in the sound preferences (I do not mean to insult your intelligence)?

---

### Post by th33nd on 2010-10-16
Sure I did. I`ve solved the problem. I had to make /etc/modprobe.d/sound.conf with that line (options snd-hda-intel model=auto) in it.

---

### Post by th33nd on 2010-11-06
:( microphone isn`t working anymore and I don`t know why. After updating system few weeks ago mic stopped working..

---

### Post by lidex on 2010-11-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by kohlrak on 2010-11-12
I don't know if i should post it here or not (as it's a separate laptop, however i can't find any documentation on the hardware to know if the device itself is different or not), so i'll just post it here anyway. I seem to be having th33nd's exact problem. Everything worked until i upgraded to 10.10.

[Your requested info.](http://www.alsa-project.org/db/?f=a1794d05efe17dd26940db65a43419728484abc3)

By the way, mine's a Satellite L645D-S4025.

As a bit of extra information, i managed to get an external mic working (seemed unusually quiet, though). When looking at the device meters in pulse audio dev chooser, i seem to be getting something small in both left and right channels (the left matches the right one, except the one in the right is much louder, though they're both rather quiet). I can't shut down any possible related drivers, since they're all "in use." In alsa mixer, it seems to acknowledge a "Mic B," however it doesn't have a volume bar. It makes me worried that it could be a hardware issue, since i really have no way of testing it. Even it i can't get it working, i still wish i could find at least something to go on to know that the hardware's ok and that the software may work with it again in the future.

EDIT:

I managed to get a recording of this noise and experiment with it. I can tap the webcam and hear nothing. However, every time i tab the bottom part, every time a sound comes out of my speakers, and every time i click with the left wing under the touchpad, it picks it up. However, i can yell, scream, and blow and absolutely none of that is recorded. It's almost as if the internal speaker is being used as a microphone instead of my microphone.

---

### Post by lidex on 2010-11-12
> **kohlrak said:**
> I don't know if i should post it here or not (as it's a separate laptop, however i can't find any documentation on the hardware to know if the device itself is different or not), so i'll just post it here anyway. I seem to be having th33nd's exact problem. Everything worked until i upgraded to 10.10.

[Your requested info.](http://www.alsa-project.org/db/?f=a1794d05efe17dd26940db65a43419728484abc3)

By the way, mine's a Satellite L645D-S4025.

As a bit of extra information, i managed to get an external mic working (seemed unusually quiet, though). When looking at the device meters in pulse audio dev chooser, i seem to be getting something small in both left and right channels (the left matches the right one, except the one in the right is much louder, though they're both rather quiet). I can't shut down any possible related drivers, since they're all "in use." In alsa mixer, it seems to acknowledge a "Mic B," however it doesn't have a volume bar. It makes me worried that it could be a hardware issue, since i really have no way of testing it. Even it i can't get it working, i still wish i could find at least something to go on to know that the hardware's ok and that the software may work with it again in the future.

EDIT:

I managed to get a recording of this noise and experiment with it. I can tap the webcam and hear nothing. However, every time i tab the bottom part, every time a sound comes out of my speakers, and every time i click with the left wing under the touchpad, it picks it up. However, i can yell, scream, and blow and absolutely none of that is recorded. It's almost as if the internal speaker is being used as a microphone instead of my microphone.

Let's try this and see what we get. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Remove the auto model quirk you added previously. Next insert these lines at the bottom:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
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

### Post by th33nd on 2010-11-13
[ALSA-INFO]("http://www.alsa-project.org/db/?f=273c25711ac3d1e927a62539800e1c12a53fe92a")


> **lidex said:**
> Let's try this and see what we get. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Remove the auto model quirk you added previously. Next insert these lines at the bottom:
```
options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
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

Nope..

---

### Post by lidex on 2010-11-13
> **th33nd said:**
> [ALSA-INFO]("http://www.alsa-project.org/db/?f=273c25711ac3d1e927a62539800e1c12a53fe92a")
Nope..
That was in response to ***kohlrak.*** OK, I see now same codec. But why is yours listed twice in alsa-base.conf?
Try a different kernel, as in an older one known to work or try to locate 2.6.35-23, which should be in the repos. Alternately, 
the linuxant driver: [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by th33nd on 2010-11-14
Because I`ve made /etc/modeprobe.d/sound.conf with the same lines.
I`ll try that.

---

### Post by marcogh79 on 2011-08-15
Hello Lidex, hello Bluefoxfox.

I have the same laptop than Bluefoxox (Toshiba A665) and I am having the same problem with the microphone. Unfortunately, the procedure explained by Lidex does not work in my case.
I am using Ubuntu 10.04.

I uploaded the informations as Bluefoxox did at this address:
[http://www.alsa-project.org/db/?f=f238ca40e3c334cb978dad11a707c92c74497eeb](http://www.alsa-project.org/db/?f=f238ca40e3c334cb978dad11a707c92c74497eeb)

Please, can one of you two check it and tell me what I should do?

Thank you very much.

---

### Post by bluefoxox on 2011-08-15
Yes.  I would upgrade to 11.04, the problem is resolved in this version entirely.


> **marcogh79 said:**
> Hello Lidex, hello Bluefoxfox.

I have the same laptop than Bluefoxox (Toshiba A665) and I am having the same problem with the microphone. Unfortunately, the procedure explained by Lidex does not work in my case.
I am using Ubuntu 10.04.

I uploaded the informations as Bluefoxox did at this address:
[http://www.alsa-project.org/db/?f=f238ca40e3c334cb978dad11a707c92c74497eeb](http://www.alsa-project.org/db/?f=f238ca40e3c334cb978dad11a707c92c74497eeb)

Please, can one of you two check it and tell me what I should do?

Thank you very much.

---

### Post by marcogh79 on 2011-08-23
that's right!
The Ubuntu 11.04 solved the mic problems for me too!
thanks!

---

### Post by bluefoxox on 2011-08-23
> **marcogh79 said:**
> that's right!
The Ubuntu 11.04 solved the mic problems for me too!
thanks!

WwWWWWWwwwwOooooOoOOoO and it is fixed without a bunch of geeky tweaking too!!!!! :^)

---

### Post by diablo465 on 2012-03-17
but my toshiba will be frozen while installing 11 edition....

---

