---
title: "HOWTO: Creative X-Fi 5.1 USB (SB1090) on 8.04 and 9.04"
date: 2009-06-21
forum: Mythbuntu
---

### Post by leaferz on 2009-06-21
Finally found a method to get this card working under 8.04 and 9.04 mythbuntu. I wanted to post the instructions within the forum in case the website ever went down. 

> **[COLOR="Navy"]1. Install packages for PulseAudio[/COLOR]**
$ sudo apt-get install libasound2-plugins pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-lirc pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils paman padevchooser paprefs pavucontrol pavumeter libao-pulse

**In 9.04 apt will complain about the libao-pulse package and offers an updated package libao2, Substitute it and the rest will go through. **

**[COLOR="Navy"]2. Configure Alsa[/COLOR]**
Edit the file /etc/asound.conf as root. Create it if it doesn&#8217;t exist. Enter the following in this file and save:

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

**[COLOR="Navy"]3. Add your user account to the pulse groups:[/COLOR]**

$ sudo gpasswd -a YOURUSERNAME pulse
$ sudo gpasswd -a YOURUSERNAME pulse-access
$ sudo gpasswd -a YOURUSERNAME pulse-rt

**[COLOR="Navy"]4. Configure PulseAudio[/COLOR]**
Click Applications > Settings > PulseAudio Preferences
On the Network Access tab, check:
- Enable network access to local sound devices
- Allow other machines on the LAN to discover local sound devices
- Don&#8217;t require authentication

On the Multicast/RTP tab, check:
- Enable Multicast/RTP receiver
- Enable Multicast/RTP sender

Configure PulseAudio to run as a daemon and allow users to load modules. Edit the file /etc/default/pulseaudio as root.
Change PULSEAUDIO_SYSTEM_START=0 to 1
Change DISALLOW_MODULE_LOADING=1 to 0

Edit the file /etc/libao.conf as root, create it if it doesn&#8217;t exist. Enter the following into that file:
default_driver=pulse

Restart your session or reboot to have changes go into effect.

Original website link: [**Link**]("http://www.samlesher.com/ubuntu/install-pulseaudio-on-xubuntu-810-xfce")

I'm able to receive 5.1 sound via the optical cable.  

Hope it helps. :D

---

### Post by aashay on 2009-06-21
Let me be the first one to thank you for taking the time. I'll try it out and tell you if it works.
Edit: The link is missing a colon (:) after http. Rebooting now... will report back.
Edit2: Huzzah! It works. There is ocassional popping though.

---

### Post by leaferz on 2009-06-22
> **aashay said:**
> Let me be the first one to thank you for taking the time. I'll try it out and tell you if it works.
Edit: The link is missing a colon (:) after http. Rebooting now... will report back.
Edit2: Huzzah! It works. There is ocassional popping though.

Fixed the link. Odd that your getting a popping sound though. :o

---

### Post by aashay on 2009-06-23
Just some quick notes:
If you have more than one card (which probably is the case if you are using the X-fi), use pavucontrol to select the default one.
Also, edit /etc/pulse/daemon.conf and set 
```
default-sample-channels = 6
default-sample-rate = 44800
```
I was getting unbearable popping and static whenever a new app connected to the server. This was resolved by installing the latest version from [here]("https://launchpad.net/~chrisirwin/+archive/cwi-pulseaudio")

---

### Post by perril on 2009-07-27
Hi, need help to install this on ubuntu 9.04 mini.
I tried to use this HOWTO but get ann error:
```

Error: unable to open display
FEH.py: cannot connect to X server
```

---

### Post by GalloGlas on 2009-10-24
This didn't work at all.  Still have 2 channel... plus extra popping sound.

---

