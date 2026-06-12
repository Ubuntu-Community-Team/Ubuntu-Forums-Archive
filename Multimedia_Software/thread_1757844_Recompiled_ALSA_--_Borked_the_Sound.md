---
title: "Recompiled ALSA -- Borked the Sound"
date: 2011-05-13
forum: Multimedia Software
---

### Post by dogeatery on 2011-05-13
OK, I have an HP Mini 1000 running Ubuntu10.04 (via PeppermintOS)  No distro has ever managed to recognize the internal microphone on this damn thing, and there are no simple workarounds out there.  I finally found [these directions]("http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html") at Ubuntu Geek, followed all steps, and now my ALSA Mixer looks like this: 

[IMG]http://i.imgur.com/ViVZE.png[/IMG]

Running alsamixer in the command line produces this:

```
$ alsamixer
cannot open mixer: No such file or directory
```Sound still worked normally until I ran the recompile command:

```
$sudo m-a a-i alsa-source

```I really don't want to do a re-installation :(

EDIT: I changed all instances of "Jaunty" to "Lucid"

---

### Post by Yellow Pasque on 2011-05-14
Undo what you did:
```
sudo m-a purge -f
sudo apt-get remove --purge alsa-source module-assistant
sudo apt-add-repository  --remove deb http://ppa.launchpad.net/minichoco-team/ppa/ubuntu lucid main
sudo apt-add-repository  --remove deb-src http://ppa.launchpad.net/minichoco-team/ppa/ubuntu lucid main
sudo apt-get update
sudo apt-get install --reinstall alsa-base alsa-utils linux-image-`uname -r`
```

If you're still interested in using latest compiled ALSA, see: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by dogeatery on 2011-05-15
A million thanks!  It's funny because when the sound went I immediately thought, "I wish there was a way for me to undo what I just did."

Sound now works fine.  I will try the new link you suggested as well.

---

