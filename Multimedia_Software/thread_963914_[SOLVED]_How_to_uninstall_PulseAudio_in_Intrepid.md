---
title: "[SOLVED] How to uninstall PulseAudio in Intrepid?"
date: 2008-10-30
forum: Multimedia Software
---

### Post by k@e on 2008-10-30
I am using Intrepid and I want to want to uninstall PulseAudio because it is responsible for a steady CPU load, furthermore it causes crackling noises in some applications (e.g. Wine).

In Hardy, I would do this to get rid of PA:

```
killall pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
```

Using this method in Intrepid, I won't be able to login into Ubuntu anymore. Upon entering my password, I am getting told that '/usr/bin/pulse-session' could not be found and I'm thrown back at the login screen. To be able to login, I have to switch to a virtual terminal and reinstall PulseAudio again. How can I remove PA and still be able to login again?

Thanks for your posts.

---

### Post by julien-1993 on 2008-10-30
Hi,
I would like also to know how to remove or disable completely pulse audio.
Reason for that is that im unable to have sound in the game nexuiz (glx version)if pulseaudio is running. If i kill the pulseaudio process, sound is working flawlessly in nexuiz and in everything else i can think of.

I had no problem at all with all this in hardy.

help extremely appreciated since for now i just kill pulseaudio on each reboot.

thanks

---

### Post by akira86 on 2008-10-30
Hello
To be able to login without pulseaudio you have to remove (make a copy first) the file :
/etc/X11/Xsession.d/70pulseaudio

and also I think it's better if you unactive all the pulseaudio thing in System>preference>Session

---

### Post by Chang An on 2008-11-01
> **k@e said:**
> 
Using this method in Intrepid, I won't be able to login into Ubuntu anymore. Upon entering my password, I am getting told that '/usr/bin/pulse-session' could not be found and I'm thrown back at the login screen. To be able to login, I have to switch to a virtual terminal and reinstall PulseAudio again.

I removed pulse and now I can't log in. I had auto login on so I can't use failsafe mode.  Could you tell me how you reinstalled pulse?

---

### Post by kostkon on 2008-11-01
> **julien-1993 said:**
> Hi,
I would like also to know how to remove or disable completely pulse audio.
Reason for that is that im unable to have sound in the game nexuiz (glx version)if pulseaudio is running. If i kill the pulseaudio process, sound is working flawlessly in nexuiz and in everything else i can think of.

I had no problem at all with all this in hardy.

help extremely appreciated since for now i just kill pulseaudio on each reboot.

thanks
You can suspend *PulseAudio* temporarily when running this game, by giving
```
pasuspender nameofyourapp
```
*PulseAudio* will start again when you quit the game.

You can edit the menu item for this game accordingly, of course, so that you don't have to start it from the terminal every time.

Thus, you don't need to take extreme measures and remove *PulseAudio* from your system for just one application that has problems with it. The problem lies with the application or the sound library that it uses and not with *PulseAudio*, if you think of it...

---

### Post by k@e on 2008-11-01
> **Chang An said:**
> I removed pulse and now I can't log in. I had auto login on so I can't use failsafe mode.  Could you tell me how you reinstalled pulse?

Sure. On the login screen, switch to any virtual terminal (CTRL+ALT+F1 to CTRL+ALT+F6), enter your login details and use this command to reinstall PulseAudio:

```
sudo apt-get install pulseaudio
```

---

### Post by Bott on 2008-11-01
> **Chang An said:**
> I removed pulse and now I can't log in. I had auto login on so I can't use failsafe mode.  Could you tell me how you reinstalled pulse?

Did you remove "/etc/X11/Xsession.d/70pulseaudio" as described in the post by akira86?  In terminal, enter the three lines of code (one line at a time) in the first post by k@e to remove pulseaudio and install esound.  Then in terminal, type "sudo Nautilus".  Then browse in Nautilus and move the file to trash.  I've been having this same problem for weeks with 8.10 beta with uninstalling pulseaudio only to not be able to log in.  akira86's suggestion to remove "/etc/X11/Xsession.d/70pulseaudio" worked!

---

### Post by leifjonny on 2008-11-02
certainly did. thanks

---

### Post by bionnaki on 2008-11-02
anyone know how to get alsamixer back?

---

### Post by akira86 on 2008-11-02
hello
sudo aptitude install alsa-utils

---

### Post by bionnaki on 2008-11-02
I guess I should have been clear.

I have alsa-utils installed, but when I run alsamixer, I only have one level when I used to have multiple levels. I see that pulseaudio has now taken over, but I dont understand why I cannot change the EQ settings via alsamixer anymore.

---

### Post by Steve H on 2008-11-20
> **akira86 said:**
> Hello
To be able to login without pulseaudio you have to remove (make a copy first) the file :
/etc/X11/Xsession.d/70pulseaudio

and also I think it's better if you unactive all the pulseaudio thing in System>preference>Session

Brilliant, worked a treat !
:D

---

### Post by psyke83 on 2008-11-20
> **bionnaki said:**
> I guess I should have been clear.

I have alsa-utils installed, but when I run alsamixer, I only have one level when I used to have multiple levels. I see that pulseaudio has now taken over, but I dont understand why I cannot change the EQ settings via alsamixer anymore.

That's normal for Intrepid - the default ALSA device is now "pulse", which directs you to the PulseAudio ALSA mixer.

To gain access to your real sound card:
```
$ alsamixer -Dhw
```

---

### Post by graysky on 2009-01-09
Thanks!  I've been wondering how in the hell to get access to all my speakers!

---

### Post by ldrn on 2009-01-14
Thank you! I was unable to hear any sound with my Thinkpad X60 Tablet after upgrading, and removing PulseAudio and using Alsa let me see the PCM channel and adjust the volume -- apparently it was at zero -- and get sound back.

---

### Post by phillip2 on 2009-01-22
I tried removing the file from Xsession. I've deleted pulseaudio from my gnome-session options. And I've tried deselecting pulseaudio in my gnome-settings. But still it's there. 

This is a real problem for me as it appears that pulseaudio is spontaenously crashing my desktop, often several times a day. At least I get this...


Jan 22 15:44:40 pulseaudio[5974]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 22 15:44:40 pulseaudio[5974]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 22 15:44:40 pulseaudio[5974]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted


in my /var/log/messages. 

The irony is that I have gone to efforts to switch almost all of my sound off. 

Phil

---

### Post by habtool on 2009-01-22
This worked for me:

sudo apt-get remove pulseaudio
(its ok if its says it will remove ubuntu-desktop, that just a metapackage)

sudo rm /etc/X11/Xsession.d/70pulseaudio
(If you worried just do:
sudo mv /etc/X11/Xsession.d/70pulseaudio /etc/X11/Xsession.d/70pulseaudio.org )

sudo apt-get install esound

under menu: > system > settings > preferences > sessions, untick the one pusleaudio start up entry

Reboot and you should be set.

PS
I am running Jaunty Alpha 3, with skype, flash video and pulse audio is working with all of it, so there is a lot of hope for 9.04/Jaunty.

Good Luck

---

### Post by solwic on 2009-02-22
> **kostkon said:**
> You can suspend *PulseAudio* temporarily when running this game, by giving
```
pasuspender nameofyourapp
```
*PulseAudio* will start again when you quit the game.

You can edit the menu item for this game accordingly, of course, so that you don't have to start it from the terminal every time.

Thus, you don't need to take extreme measures and remove *PulseAudio* from your system for just one application that has problems with it. The problem lies with the application or the sound library that it uses and not with *PulseAudio*, if you think of it...

No, the problem is with PulseAudio.  It's garbage.  :(

EDIT:  How would that command work?  I added it to the menu entry, but I'm not sure I did it correctly.  Still same old issues as before.  :(

---

### Post by kengla on 2009-03-14
I removed pulseaudio because some have found it helped get the sound from the microphone in skype working.  I'm on a Thinkpad R61i using built-in mic but it's still not working. Any suggestions?

---

### Post by slimx3m on 2009-04-19
this method actually didn't work for me.  don't get me wrong....... skype did get resolve but i was getting no audio at all (speaking through my microphone). :(

---

### Post by MC_LA on 2009-04-19
I was having all kinds of problems with pulseaudio. It would work fine and then suddenly stop. Applications would hang. All my audio problems went away when I removed it from my system. Here's a good link with instructions for removing it:

[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

---

