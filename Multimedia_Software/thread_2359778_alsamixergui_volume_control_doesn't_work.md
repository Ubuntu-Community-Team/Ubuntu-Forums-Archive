---
title: "alsamixergui volume control doesn't work"
date: 2017-04-27
forum: Multimedia Software
---

### Post by sgroffman on 2017-04-27
I have recently installed Lubuntu. It's going great, but there is no sound. According to a test I ran, the system recognizes both of my sound cards. Alsamixergui, the sound mixer that comes with Lubuntu, recognized and activated both of my soundcards too. Both channels in alsamixergui are unmuted. The commands for "increase left and right volume" do not produce any response in alsamixergui - I expected to see the faders move up and down in response to the up and down arrows. I have also tried safely reinstalling alsamixergui. 

Anyone have a solution? I have seen pulseaudio mentioned in several places, but am not sure if another program is what I need. 

Below is a link to info on system specs and functioning as regards the alsa mixer.
[http://www.alsa-project.org/db/?f=3f28668d881380e377bd9731adbee6995e20a12a](http://www.alsa-project.org/db/?f=3f28668d881380e377bd9731adbee6995e20a12a)

---

### Post by Dennis N on 2017-04-27
As I recall, in Lubuntu 16.04 the sound did not work until you installed **pulseaudio** and **pavucontrol**. You should try that if you have Lubuntu 16.04.

---

### Post by Xian on 2017-04-27
Install pavucontrol:


$ sudo apt-get install pavucontrol


That'll pull in the required pulseaudio packages. 


Then toggle the sound configurations until it works properly


[IMG]https://freedesktop.org/software/pulseaudio/pavucontrol//screenshot.png[/IMG]

---

### Post by sgroffman on 2017-05-01
Thanks for those fixes... it looks like Lubuntu 16.04 may not support pulseaudio.

Following the install pavucontrol command line, I got: 

E: Package 'pavucontrol' has no installation candidate

And following the install pulseaudio command line, I got: 

The following packages have unmet dependencies:
 pulseaudio : Depends: libfftw3-single3 but it is not installable
              Depends: libspeexdsp1 (>= 1.2~beta3.2-1) but it is not installable
              Depends: libwebrtc-audio-processing-0 but it is not installable
              Depends: libasound2-plugins but it is not installable
              Recommends: pulseaudio-module-x11 but it is not going to be installed
              Recommends: rtkit but it is not installable
E: Unable to correct problems, you have held broken packages.

According to the following thread, Lubuntu 16.04 and audio on Firefox do not get along, but maybe one of you would have an insight into that? 

[https://ubuntuforums.org/showthread.php?p=13617911](https://ubuntuforums.org/showthread.php?p=13617911)

---

### Post by Dennis N on 2017-05-01
I have an installation of Lubuntu 16.04 still on my testing computer I did to test it when it first came out. Decided against it for major use, because of certain bugs. But trying it now, and it seems to have no audio problems, and no pulseaudio is installed on it (so apparently in post #2 I may have confused this with another release of Lubuntu).

I'm aware that new firefox requires pulse audio in order to play audio in the browser. It's included with Lubuntu 17.04! 

I am using Lubuntu 17.04, and as I said, it does have pulse audio installed by default. In my opinion, this is the best Lubuntu release I have seen - they fixed some bugs that turned me off 16.04 and 16.10. 

Can you install pulseaudio on 16.04? I just did the install, and it went ok here. So we know that theoretically, there is no problem with installing it. 

```
dmn@Kayleigh:~$ sudo apt-get install pulseaudio pavucontrol
[sudo] password for dmn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libfftw3-single3 libpulsedsp libwebrtc-audio-processing-0 pulseaudio-module-x11 pulseaudio-utils rtkit
Suggested packages:
  libfftw3-bin libfftw3-dev pavumeter paman paprefs avahi-daemon
The following NEW packages will be installed:
  libfftw3-single3 libpulsedsp libwebrtc-audio-processing-0 pavucontrol pulseaudio pulseaudio-module-x11 pulseaudio-utils
  rtkit
0 upgraded, 8 newly installed, 0 to remove and 4 not upgraded.
Need to get 1,712 kB of archives.
After this operation, 7,824 kB of additional disk space will be used.
Do you want to continue? [Y/n]


``` 

After the installation of pulse audio, I switched the audio plugin in Audacious from ALSA to Pulse Audio to verify it works, and it works fine.

---

### Post by sgroffman on 2017-05-01
Thanks for that. It looks Lubuntu 16.04 does support pulseaudio, I just had to perform 
```
sudo apt-get update
```

before I did the installation, which was 

```
sudo apt-get install --reinstall pulseaudio
```

Now my alsamixergui shows "pulseaudio" as both the card and the chip, so the two programs seem to be working together,
and it allows me to toggle basic sound settings, and the system produces sound. 

I installed Lubuntu 16.04 on the thinking that a 'long-term support' version would require less upkeep. 
Bug fixes on 17.04 certainly sounds appealing, but I'm not sure I want to go through the whole installation process
again so soon after installing 16.04...

---

