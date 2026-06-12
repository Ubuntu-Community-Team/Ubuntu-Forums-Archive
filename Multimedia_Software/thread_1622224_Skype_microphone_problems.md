---
title: "Skype microphone problems"
date: 2010-11-15
forum: Multimedia Software
---

### Post by ExemplarUbuntu on 2010-11-15
Yesterday I did a Skype update on a friends Lynx installation. It had problems so I updated to the latest Ubuntu.

The video is working although the self view does not, minor issue.

The big problem is that Skype was not picking up the microphone from the Logitech webcam.

Following lots of threads on this sort of issue I removed Pulseadio (I had to do this on the original Skype install a few years back) and installed alsa. Now skype offers lots of sound sources.

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4)


At my end I can see the Ubuntu user and they can see and hear me but what is odd is that I can hear the echo of my own sounds but cannot hear anything they say.

This may just be heavily distorted sound like clicks and mic tapping but if they play sounds on their end (like the skype test sound) then I can hear it over the skype connection.

This is very frustrating. I have pushed up all the levels in alsamixer and selected various sound sources in skype, all to no avail.

Can anyone help ?

---

### Post by ExemplarUbuntu on 2010-11-15
I reinstalled Pusleaudio and gave that another go but no joy. So I repated the alsa steps and then fiddled about with the devices again and it is now working.

---

### Post by ExemplarUbuntu on 2010-11-19
Of course I spoke too soon.

The machine was booted up today and their webcam mic is no longer being picked up by Skype. Nothing. There was some strange mangled sound but when I picked a few different input devices in Skype and fiddled with alsamixer, even that stopped.

They can see and hear me and I can see them but no sound.

Any suggestions ?

---

### Post by ExemplarUbuntu on 2010-12-06
I know I am not the only one with such problems.

I have now resorted back to pulseaudio but there are lots of problems.

The microphone level was set to 100% but wasn't picking anything up. When I lower the level it works again and I can see the monitor level rising and falling.

Skype is picking up the mic but at the receiving end the audio is very broken up and unintelligable. If I turn the video on then it the audio all but disappears, just the occasional chunk of sound gets through to the recipient.

The skyoe audio output at the Ubuntu end is non-existent but the other audio sounds work fine.

---

### Post by ExemplarUbuntu on 2010-12-26
Some more feedback.

I managed to get a working set-up by completely breaking pulseaudio. I wasn't sure how I had done this but I just stumbled upon the reason. One of the entries in  /etc/pulse/daemon.conf has a dash instead of an = so it does not parse properly.

This makes sure pulseaudio does not start and means I have a working sound and microphone system.

Not a great state of affairs, to have to break the set-up just to get it working.

---

### Post by jbrice on 2010-12-26
Hmm - Skype and Logitec rings a bell. IME there seems to be a cross-platform bug with Logitech drivers that kills the audio signal when you set the mic. gain to 100%. I have had this problem consistently with Logitech web cams under Ubuntu, WinXP and Vista. 

If you then use the web cam with Skype and use Skype's auto control of mic. levels, at some point there will be silence and it will rack audio gain up to 100%, the audio will die and the gain will stay at 100% as there is apparently no sound. So maybe there is nothing amiss with your PulseAudio etc?

See also my posting in this thread:
[http://ubuntuforums.org/showthread.php?t=1506616](http://ubuntuforums.org/showthread.php?t=1506616)

---

### Post by Syed75 on 2010-12-26
Did you enable the microphone?

If not go to System<Preferences<Sound

Then input and change the volume level. Then go to output and see the speaker settings fix them if needed.

---

### Post by Finn bjerke on 2010-12-30
I gave up the build in mic and installed a bluetooth headset connected to a USB dongle. It allows me to skype handsfree which is nice. I use Nokia 115 Bluetooth, worx nicely. It is however annoying that the build in mic on my Compaq PC makes too much noise to be any use. To begin with it said nothing now its sort of working but makes too many crackling noises. Under Windows the mic worked like a charm.  
 
I am considering a USB mic for music recordings  :guitar:

---

### Post by ExemplarUbuntu on 2011-02-13
> **jbrice said:**
> Hmm - Skype and Logitec rings a bell. IME there seems to be a cross-platform bug with Logitech drivers that kills the audio signal when you set the mic. gain to 100%. I have had this problem consistently with Logitech web cams under Ubuntu, WinXP and Vista. 

If you then use the web cam with Skype and use Skype's auto control of mic. levels, at some point there will be silence and it will rack audio gain up to 100%, the audio will die and the gain will stay at 100% as there is apparently no sound. So maybe there is nothing amiss with your PulseAudio etc?

See also my posting in this thread:
[http://ubuntuforums.org/showthread.php?t=1506616](http://ubuntuforums.org/showthread.php?t=1506616)

I have had the problem you describe but only since the upgrade of Ubuntu and Skype just before Xmas. Previously it worked fine.
I had to set the sound below 100% (see 6th Dec)

The current situation with Pulse disabled is that the Ubuntu box is not sending audio over Skype but is receiving ok.


I re-enabled Pulse and re-started Skype. In Skype options all the sound options bar one disappear, leaving just PulseAudio server (local).

The sound output on the windows box that is receiving is just white noise with the occasional buzz. The sound level sometimes increases or decreases in steps.

Several months on and essentially nothing has changed.

---

### Post by ExemplarUbuntu on 2011-03-18
There is still no change in the Skype situation.

I still have to disable PulseAudio to get YouTube to play sound. The mic input to Skype works but when video is enabled on my camera the sound being sent is mangled.

I am tempted to wipe the system and start again but this is a windows solution.

---

### Post by lidex on 2011-03-19
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

[http://blogs.skype.com/linux/2009/09/some_explanations.html](http://blogs.skype.com/linux/2009/09/some_explanations.html)

[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

Seen any of those?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by ExemplarUbuntu on 2011-03-20
Yes I have tried those and more. Installing alsa didn't help but just made things more complicated. Disabling pulseaudio made some things work but most other apps don't work.

I have resorted to wiping the whole system and doing a fresh install and it is no better, slightly worse in fact. This is frankly ridiculous.

When I start skype the other end can see video but gets no sound or very very broken sound until I turn off my video.

I don't want to install alsa again and shouldn't have to if Ubuntu is supposed to be using pulse.

I really think the only solution is going to be to switch to another distro.

---

### Post by lidex on 2011-03-20
> **ExemplarUbuntu said:**
> Yes I have tried those and more. Installing alsa didn't help but just made things more complicated. Disabling pulseaudio made some things work but most other apps don't work.

I have resorted to wiping the whole system and doing a fresh install and it is no better, slightly worse in fact. This is frankly ridiculous.

When I start skype the other end can see video but gets no sound or very very broken sound until I turn off my video.

I don't want to install alsa again and shouldn't have to if Ubuntu is supposed to be using pulse.

I really think the only solution is going to be to switch to another distro.

Ubuntu uses both pulse and alsa. Alsa is the underlying sound base (modules/drivers) while pulse is the sound server that "directs traffic".

---

### Post by marl30 on 2011-03-20
> **ExemplarUbuntu said:**
> Yes I have tried those and more. Installing alsa didn't help but just made things more complicated. Disabling pulseaudio made some things work but most other apps don't work.

I have resorted to wiping the whole system and doing a fresh install and it is no better, slightly worse in fact. This is frankly ridiculous.

When I start skype the other end can see video but gets no sound or very very broken sound until I turn off my video.

I don't want to install alsa again and shouldn't have to if Ubuntu is supposed to be using pulse.

I really think the only solution is going to be to switch to another distro.

Here is an alternative to Skype you can try: imo.im

It's a web messenger that offers text, voice and video calls for Skype, Yahoo, Hotmail, Google, and others.

If you want it to run like a native messenger, install it as an extension form Chrome/Chromium Web Store. Look for IMO. When it installs and the extension icon appears in a new tab, right click on it and then choose to open as Window. When you log in you can go into the settings of the app and select add icon to menu. It will add a launcher to your Ubuntu menu as well as your desktop. When you click on the icon it will launch the app without opening Chrome/Chromium and run it just like a native application. 

Hope it helps.

---

### Post by marl30 on 2011-03-21
Just thought I'd go ahead and make a screenshot of the IMO Chrome app running like a native program on my computer.

---

