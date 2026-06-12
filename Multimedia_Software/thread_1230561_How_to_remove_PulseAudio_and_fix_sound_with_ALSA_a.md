---
title: "How to remove PulseAudio and fix sound with ALSA and ESound"
date: 2009-08-03
forum: Multimedia Software
---

### Post by igorzwx on 2009-08-03
it works on Ubuntu 8.04 and it is likely to work on 8.10 and 9.04


**coldReactive** delivered howto
[http://coldreactive.tumblr.com/post/154554366/ubuntu-how-to-remove-pulseaudio-and-install-esound](http://coldreactive.tumblr.com/post/154554366/ubuntu-how-to-remove-pulseaudio-and-install-esound)

and I gave it a try.

I installed **Ubuntu 8.04** on the old box
and updated it:

sudo apt-get update

sudo apt-get upgrade

Reboot the system.


[B]Purge PulseAudio
[/B]
Since PulseAudio deserves a special treatment, I removed it following this howto:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)


sudo killall pulseaudio

cp /etc/X11/Xsession.d/70pulseaudio ~/

sudo apt-get purge pulseaudio


**NOTE 1:** The file /etc/X11/Xsession.d/70pulseaudio  does not exist on Ubuntu 8.04 (nothing to copy)

**NOTE 2:** Removing of the package ubuntu-desktop* does not make any harm. It is a dummy package.


[B]Install the Enlightenment Sound Daemon (ESD)
[/B]
sudo apt-get install -y esound esound-clients esound-common libesd-alsa0


System -> Preferences -> Sessions -> Startup Programs

uncheck PulseAudio and something else (which you do not need)

**Reboot**

System -> Preferences -> Sound

and select what you need


Then you can install your multimedia apps
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.[/B]

I have not tested everything yet.

---

### Post by demarshall on 2009-08-03
I would really like to know whether this works on 9.04 before I do it. Is there anybody who is braver than I am who will step up to the plate and follow igorzwx's instructioins and then report what happened?

Does the update and upgrade mean that you were using 9.04?

---

### Post by coldReactive on 2009-08-03
Just so that you're aware, I have posted a thread about this in the tutorials & tips forum, but since that forum is under moderation, we may never see that thread.

To the thread opener, just because apps work for you, doesn't mean they'll work for everybody.

Also, don't give them a tutorial or information about OpenSound, when the default is ALSA for Ubuntu.

---

### Post by igorzwx on 2009-08-03
"To the thread opener, just because apps work for you, doesn't mean they'll work for everybody."

You are absolutely right!
That is why I published it here.
Everyone can re-use it, or re-publish how he want.

By the way, many thanks for your tutorial.

It should work for Ubuntu 9.04.
And, if it does not work, it is easy to roll back:
deinstall ESound and install PulseAudio.

---

### Post by igorzwx on 2009-08-03
"Does the update and upgrade mean that you were using 9.04?"

NOT!!!

sudo apt-get upgrade 

would not upgrade your distro.
it would upgrade apps inside the distro you have.

To upgrade distro, you have to apply another command

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
QUOTE:
**Maintenance commands**

 
[LIST]
[*]apt-get update Run this command after changing */etc/apt/sources.list* or */etc/apt/preferences* . For information regarding */etc/apt/preferences*, see [PinningHowto]("https://help.ubuntu.com/community/PinningHowto"). Run this command periodically to make sure your source list is up-to-date. This is the equivalent of "Reload" in Synaptic or "Fetch updates" in Adept.
[*]apt-get upgrade This command upgrades all installed packages.  This is the equivalent of "Mark all upgrades" in Synaptic.
[*]apt-get dist-upgrade This command upgrades the entire system to a newer release. The same as the above, except add the "smart upgrade" checkbox. It tells APT to use "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. [BR]("https://help.ubuntu.com/community/BR") attachment:IconsPage/warning.png This is not the recommended way to perform a distribution upgrade. See [[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) upgrading] for more information.
[/LIST]

---

### Post by demarshall on 2009-08-05
I followed igorzwx's directions to change from Pulse Audio to ESound and it's working fine. Now my only problem is getting my old Logitech webcam working again.

After doing this, I found that Apt wanted to remove many files and then my Gnome apps wouldn't work anymore. I reinstalled Gnome with Synaptic and that problem was fixed. I just realized that sound won't work in YouTube videos any longer. Do I have to reinstall Flash? That's my first thought. Anybody else having any problems?

---

### Post by demarshall on 2009-08-09
Please, can anyone tell me the steps to get the video in YouTube working again. Is it necessary to uninstall Flash and reinstall it?

---

### Post by coldReactive on 2009-08-09
> **demarshall said:**
> Please, can anyone tell me the steps to get the video in YouTube working again. Is it necessary to uninstall Flash and reinstall it?

Don't hijack threads.

Do you have flashplugin-nonfree installed, or one of those other swf players such as gnash/swfdec?

---

### Post by demarshall on 2009-08-09
I wasn't meaning to hijack the thread. My message was related to the change of sound system.

I have Adobe's Flash installed and it was working fine before I changed my sound system.

---

### Post by demarshall on 2009-08-10
I have now done a reinstall of Flash in Synaptic and I still get no sound in Firefox.

Does anybody have any ideas as to how to get audio working in Firefox again after changing from Pulse to ESound?

---

### Post by Jonas thomas on 2009-08-22
Thanks..

---

### Post by Tankerdog2002 on 2009-09-25
deMarshall,

Open synaptic.

See if you have [gstreamer], [mpeg123-esd], and [libalsaplayer] installed.

---

### Post by Jonas thomas on 2009-09-26
I replaced pulse with esound per this thread and I've been very happy with the result.  The only thing is that it seems my SDL games are working..
Does anyone have any thoughts on this??

---

### Post by demarshall on 2009-09-27
> **Tankerdog2002 said:**
> deMarshall,

Open synaptic.

See if you have [gstreamer], [mpeg123-esd], and [libalsaplayer] installed.

Thanks Tankerdog2002. I installed those files as well as Shiretoko (a version of Firefox 3.5.3) and everything seems to be working now.

---

### Post by coldReactive on 2009-09-27
Just remember that pulseaudio is more integrated in Ubuntu 9.10, it may not be as easily replaced.

---

### Post by Jonas thomas on 2009-09-27
> **coldReactive said:**
> Just remember that pulseaudio is more integrated in Ubuntu 9.10, it may not be as easily replaced.
I'm still on 8.04, Isn't wanting to obliterate pulse less of an issue because it basically been properly configured to work out of the box,err..distro cd... yah know what I mean..

Any thoughts on the SDL and Esound??

---

### Post by coldReactive on 2009-09-27
> **Jonas thomas said:**
> I'm still on 8.04, Isn't wanting to obliterate pulse less of an issue because it basically been properly configured to work out of the box,err..distro cd... yah know what I mean..

For best sound on my netbook (Toshiba nb205) I need to replace the sound system with OSS sadly.

---

### Post by AlexanderDGreat on 2010-04-27
> art@systema:~$ sudo apt-get remove pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pulseaudio **ubuntu-desktop**
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
After this operation, 1880kB disk space will be freed.
Do you want to continue [Y/n]? n
 - ok now that's scary, **REMOVE ubuntu-desktop?** I really want to try ALSA and Esound coz I want to improve "maybe" the sound quality of my HDA Intel sound card, but I can't because of removing ubuntu-desktop with pulseaudio, anyone can comment?

---

