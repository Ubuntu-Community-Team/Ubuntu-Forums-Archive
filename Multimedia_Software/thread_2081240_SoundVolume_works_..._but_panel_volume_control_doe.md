---
title: "Sound/Volume works ... but panel volume control doesn't."
date: 2012-11-06
forum: Multimedia Software
---

### Post by WinRiddance on 2012-11-06
Aaaaarrrrgh, this has been driving me batty for a week now. I recently did a clean 64bit installation of Xubuntu 12.04 followed by installing the Mate Desktop Environment. My only login to XFCE was the default one, which I used to install Mate. Logged out, then logged into the Mate session which is what I'm using full-time, primarily because of the file manager. I have just about everything working perfectly, except for the following:

Volume works great for mp3, movie, wav, and midi files. I have the volume control icon and I have the keyboard shortcuts for controlling volume levels. That's the stickler though ... because when I use the shortcut keys or the volume control symbol, the slider merely moves back and forth (up/down) without affecting the volume at all.

I did not have this problem with Xubuntu 11.04 but I think it started with 11.10. I have both, Alsa as well as Pulse installed. Alsa was the default and both appear to work just fine between login sessions. I have read what seems like hundreds of articles Online but most of them are about missing volume controls ... as opposed to volume controls that are there, but not working. Following the advice on numerous threads, I did make sure that gstreamer this and gstreamer that is installed properly. Like I said, the sound works just fine on all multimedia files, I just can't get the visual volume controls to work. Any ideas or fixes on this? Thanks in advance ...

.

---

### Post by WinRiddance on 2012-11-08
Bump a di bump ... wow, major bummer, nobody in the multimedia forum has ever encountered this? :shock:

.

---

### Post by WinRiddance on 2012-11-10
OMG, really? I'm the only one who's ever come across this phenomena of the volume not working via keyboard shortcuts or volume button on the panel? Wow, considering the size of this Forum that's pretty hard to believe. But then ... I've been looking everywhere else too, without being able to find an answer ... :confused:

.

---

### Post by pqwoerituytrueiwoq on 2012-11-11
the panel icon has the mute icon right?
i had this issue on my guest account, i just and a script delete ~/.pulse-cookie (root permission required)
this may be helpful to you, you will need to do some editing to it

```
~$ cat /usr/local/bin/xfce-login-script
#!/bin/bash
ogg123 /usr/share/sounds/ubuntu/stereo/desktop-login.ogg &
sleep 1
cd /tmp
if [ $(ls guest-* 2> /dev/null | wc -l) -gt 0 ];then
    guest=$(ls | grep guest-)
    rm ./$guest/.pulse-cookie
fi
exit

``````

~$ cat /etc/lightdm/lightdm.conf 
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
display-setup-script=sh -c "numlockx on;if [ -f /var/log/xbacklight ];then xbacklight -set $(cat /var/log/xbacklight);fi"
greeter-setup-script=sh -c "ogg123 /usr/share/sounds/ubuntu/stereo/system-ready.ogg &"
**session-setup-script=sh -c "/usr/local/bin/xfce-login-script &"**
session-cleanup-script=sh -c "/usr/local/bin/xfce-logout-script;xbacklight -get > /var/log/xbacklight"
```

---

### Post by Yellow Pasque on 2012-11-11
So, just to be clear, you're asking about the MATE volume control? Correct?

---

### Post by WinRiddance on 2012-11-12
Well, I'm using the Mate desktop but the problem began with Xubuntu 11.10 before I ever used Mate. Also, my Mate desktop has the standard Volume Control that I imported from XFCE because I figured perhaps there's a problem with the Mate volume control. Matter of fact, I'm using XFCE panels too since Mate panels don't have 100% transparency.

The system is a laptop that's permanently connected to an HDMI port on the TV. The laptop never moves, always remains in place. The same setup was used with Xubuntu 11.04 without a problem, but ever since upgrading to 11.10 and later a clean installation of 12.04 I've been having these issues where the volume control/sliders work visually on the screen ... but without actually having an effect on the volume that's coming out of the speakers.

I can run the system with alsa controls ... or with pulse audio ... either seem to work just fine but the volume control issue I've described persists regardless what I use. Volume out of the speakers works just fine.

**@pqwoerituytrueiwoq** ... I appreciate the help but I don't think that I understand your script. I'm an Ex Windoze user, so scripts are pretty unfamiliar territory for me. Thanks anyway.

.

---

### Post by Yellow Pasque on 2012-11-12
Well, I had to play with xfconf to get my keyboard to control the headphone output (since my speakers have their own volume dial). A sampling of commands below:
```
$ xfconf-query -c xfce4-mixer -p /active-card
MAudioRevolution51Alsamixer
$ xfconf-query -c xfce4-mixer -p /active-track
PCM Headphone
```
This is on a Debian/xfce system with pure ALSA. I'm not sure how pulse plays into it.

---

### Post by WinRiddance on 2012-11-18
Thanks for all of the input. I've come to the conclusion that this must be conflicting file or package behavior between Xubuntu and the Mate Desktop. I believe this due to the fact that if I run the Mate volume control inside of a Mate panel, it works as expected ... except for the keyboard shortcuts. But if I import that same volume control into the XFCE panel (can be done easily enough), the same volume control then behaves differently.

It doesn't matter if I'm utilizing Pulse, Alsa, or the embedded Intel HDMA option, the volume control always behaves the same way. As stated before, Xubuntu 11.04 didn't have this problem and I didn't start using the Mate desktop until Xubuntu 11.10 was released. All of this leads me to believe that this volume control issue is either directly related to Mate itself, or some kind of conflict between the two desktop managers.

.

---

