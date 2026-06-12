---
title: "Ubuntu Audio issues via Nvidia GT 240 HDMI ..I need help"
date: 2010-05-25
forum: Multimedia Software
---

### Post by Ladsoftware on 2010-05-25
my System 

AMD X6 1055T 
2 gb DDR3 
Nvidia GT 240 
500gb 
ASRock 770 EXTREME3 AM3 AMD 770 


Sharp 52in 1920x1080p 

video connection: 
HDMI from NVIDIA GT 240 to Sharp HDTV 

result: 
no sound with ubuntu 
but get sound with Windows 7 

Im new to linux...... I need help...




I typed alsamixer in terminal 
i got alsamixer v1.0.22 
but everytime i press f6 for "select sound card" 
i get options 
-(default) 
0. HDA ATI SB 
1. HDA NVIDIA 

since I have nvidia GT 240. 
i went with HDA nvidia but its then says 
this sound device does not have any controls. 

but some tuto say i need alsa v1.0.23 
that one i cant seem to install. 
i have download them but its not excute file 

i went to nvidia to got card drive which gives me this error 

Could not open the file /home/mediaserver/Downlo…x86_64-195.36.24-pkg2.run. 
gedit has not been able to detect the character encoding. 
Please check that you are not trying to open a binary file. 
Select a character encoding from the menu and try again. 

character: auto detect 
cancle or retry

---

### Post by farbird on 2010-05-26
paste the output for
```

aplay -L
aplay -l
```

also update your nvidia drivers to 256 with this ppa

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install nvidia-current
```

and try the sound again

u shd also install pavucontrol
```

sudo apt-get install pavucontrol

```

the menu item should come out under Sound & Video [ PulseAudio Volume control ]
u can then select the desired output hardware to be hdmi [ under the configuration header tab]

---

### Post by farbird on 2010-05-26
once u done that,

u might want to try out [XBMC](http://sglnx.com/2010/05/opensource-complete-home-entertainment-system-xbmc/) <-----

---

### Post by Ladsoftware on 2010-06-20
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0




aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers

---

### Post by axelsvag on 2010-06-21
I got the same problem. Do you mean that though you installed the 256 driver you just see the ATI soundcard?

---

### Post by Ladsoftware on 2010-06-22
yeah
i wont let me install the nvidia driver from nvidia web site...

even if i let the hardware update, to update the nvidia driver

---

### Post by Ladsoftware on 2010-06-22
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates


Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

---

### Post by lidex on 2010-06-22
You can follow this guide:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")
alsa 1.0.23 is required, so if you need to update follow the alsa-upgrade link in my sig.

---

