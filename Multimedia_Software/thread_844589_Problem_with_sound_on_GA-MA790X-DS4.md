---
title: "Problem with sound on GA-MA790X-DS4"
date: 2008-06-29
forum: Multimedia Software
---

### Post by »John« on 2008-06-29
Hello everyone.
I've recently bought myself a brand new machine a I've run into a small problem - there's something terribly wrong with sound... Right after I booted the freshly installed system, I noticed the sound GDM plays when the login screen is ready was cycling even after I successfully logged in which has never happened before on any other machine. I disabled that sound in order to get rid of this annoyance but I was unable to get anything else out of my speakers ever since.
According to GIGABYTE the sound codec is ALC889A, which should be supported by ALSA 1.0.16 and the cycling sample shows there's nothing wrong with the sound hardware itself so there must be just some sort of misconfiguration.
I will keep trying getting it to work and I will definitely let everyone interested know if I succeed but if anyone here has any ideas to save me unnecessary struggle, I'll be more than happy to heed his recommandations.[COLOR=#FD6724]
[/COLOR]

---

### Post by icheyne on 2008-06-29
First try here: [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by Bonez56 on 2008-07-18
I have this exact same problem, same mainboard. Did you ever find a fix?

---

### Post by »John« on 2008-09-24
I filed this as a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/251916") to Launchpad. No luck so far with ALSA (installing 1.0.18RC3 from source only makes the problem even worse) but installing [OSS 4]("http://www.opensound.com/download.cgi") can serve at least as a temporary workaround (because quality of the sound provided by the OSS driver isn't exactly perfect - there's this silent crackling and hissing like when you played data tape back in 8bit times; this becomes much more apparent after pluging in USB Bluetooth adapter). The issue is still present in 8.10&#945;6 so anyone who hopes it'll be fixed be the time of a release is probably gonna be disappointed.

---

### Post by Mr.Roland on 2010-05-08
Hi,

had the same problem, found a workaround.

Under WinXP the GA-MA790X-DS4 build-in-soundcard supports free asssignment of in- and out-jacks. May be, that is the problem...

Solved it by changing the position of line-in and mic-in plugs - simply used the default positions. Everything seems ok now for my purposes: Mic-in and Speakers-out in Skype, sound from the Internet and musik from my local music library.
Haven't checked 5.1-surround-sound, yet.

Roland

---

### Post by »John« on 2010-05-08
I think we can close this thread because whatever kernel bug was causing this problem is now long gone and the Launchpad bug report considers it fixed since the 9.04 release. Many thanks to everyone involved in getting rid of this one or providing others with temporary workarounds.

---

