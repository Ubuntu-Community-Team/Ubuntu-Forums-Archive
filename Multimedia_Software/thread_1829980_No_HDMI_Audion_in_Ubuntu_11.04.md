---
title: "No HDMI Audion in Ubuntu 11.04"
date: 2011-08-21
forum: Multimedia Software
---

### Post by adiasd on 2011-08-21
Hi Folks,

After upgrading to 11.04 I noticed that HDMI audio stopped working. When I connect the HDMI cable to the TV the image is transfered but there is not sound. 

I tried several things, starting with checking the sound preferences. I have there two devices, one for internal audio and another for HDMI. When I select the HDMI output I have no sound. I tried to run gnome-alsamixer and it shows two devices as well, but for the HDMI it gives me no parameter at all there. 

Device configuration seems ok and aplay -l gives me the follwoing info:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I also tried some troubleshooting pages like [this]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") but couldn't solve the problem (in fact when trying one of the suggestions of this page it messed up the whole sound configuration of my laptop and had to reinstall alsa driver modules as explained [here]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules") to come back to the previous state with only the HDMI problem).

What makes me really upset is that with the previous Ubuntu version (10.10) HDMI audio worked just fine then after upgrading to 11.04 it stopped working. 

Another interesting thing about this problem is that when I play a video from a web page, for example from youtube, and try to use HDMI audio, the video runs much faster than normal with no sound. If I switch to internal audio, while still sending the video over HDMI, it works fine with the audio playing in the laptop and the video in my TV.

Does anyone have any clue on this problem?

Thanks

---

### Post by tjones00 on 2011-08-24
What are the results from

```
aplay -D hw:1,3 /usr/share/sounds/alsa/Front_Center.wav

aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav

aplay -D hdmi /usr/share/sounds/alsa/Front_Center.wav
```


If any of these produce sound see.

[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

And go to Step 4 replacing the default.pa edit with whatever works for you.

---

### Post by adiasd on 2011-08-28
I tried the three commands and none of them played any sound. The 1st and 3rd showed errors:

aplay -D hw:1,3 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:1065: Channels count non available

aplay -D hdmi /usr/share/sounds/alsa/Front_Center.wav
aplay: main:660: audio open error: No such file or directory

The second ran but didn't play any sound.

So still no clue so far :-(

---

### Post by blackcatblack on 2011-08-28
Sounds like you have the same issue i have semi fixed.

Check and see under nvidia xserver settings and see if you have the 174driver if so you need to update it try that. 

After update and reboot see if it have changed to 280 under nvidia x server settings if no then run additonal drivers and get the nvida current and reboot now try the comands to test out put that others listed 


    sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update && sudo apt-get dist-upgrade 
sudo apt-get install nvidia-current

---

### Post by adiasd on 2011-09-18
No solution yet. My card is ATI Radeon and I tried to re-install the proprietary drivers that I used before but had to switch to the open source after the upgrade to 11.04. However I couldn't manage to boot after installing the proprietary. It seems it doesn't work yet with 11.04. So I gave up to fix this problem. My guess is that is a bug with the open source driver for my card, but I can't use the proprietary so I have to live with the problem. 

Honestly, I'm very disappointed with Ubuntu 11.04. Unity is too buggy and featureless to be usable (the lack of configuration options is a shame and every time I boot the system I see a different glitch in the launcher) and other problems like this with HDMI audio output and a few others I started having after the upgrade make me feel this is the worst Ubuntu release I remember, since I started using this distribution 6 years ago.

---

### Post by gururise on 2011-10-12
I'm having the exact same problem under Ubuntu 11.10!!

aplay -l:
> card 0: SB [HDA ATI SB], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


No HDMI audio using the xorg radeon driver on my HD4200 IGP motherboard.  I got working Audio previously in 11.04 using fglrx, but since fglrx doesn't work with Gnome-Shell, I switched to the open source drivers when upgrading to 11.10

---

### Post by GraemeUK on 2011-10-13
Hi Guys,

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1811760](http://ubuntuforums.org/showthread.php?t=1811760)

I believe we have solved this there.  Forcing a driver update fixed this for mose people, I personally did this and switched to Pulse Audio to resolve the problem.

Hope this helps.

---

