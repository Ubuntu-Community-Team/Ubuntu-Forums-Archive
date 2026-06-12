---
title: "How do I set sound-juicer to open when I insert a CD?"
date: 2009-07-20
forum: Multimedia Software
---

### Post by Bucky Ball on 2009-07-20
Hi all,

I'd like to be able to make Sound-Juicer (Audio CD Extractor) open automatically when I insert a CD. My machines at home all do this but for some reason the in-law's doesn't. 

I have been over here for four days working on their machine and all pretty sweet but now some finishing touches. Go back tomorrow morning so if you'd like to throw some random ideas up for me to try in the few hours I have left here, fire away and thanks in advance!

They are running 8.04

:)

---

### Post by komputes on 2009-07-20
Open a nautilus window and go to Edit->Preferences->Media->CD Audio and then click on "Open with other application" and the point it to sound juicer which should be in /usr/bin/sound/juicer

---

### Post by Bucky Ball on 2009-07-20
Thanks for that. Knew I'd seen it somewhere in the distant past. 'Audio CD Extractor' was there as an alternative option, but oddly, 'Open with another application' wasn't. I wanted to change DVD to VLC but no option.

---

### Post by Bucky Ball on 2009-07-20
I tried the nautilus approach and unfortunately it has made no difference at all. Insert CD and Rhythmbox pops up. 

Any further suggestions? I have used the custom command 'sound-juicer' in 'Preferred Applications' but still nothing.

---

### Post by komputes on 2009-07-20
> **Bucky Ball said:**
> Knew I'd seen it somewhere in the distant past.

Yeah, before it used to be part of "System > Preferences > Removable Drives and Media" before Ubuntu 8.04.

If after setting a autorun preference for Audio CDs it does not work, I would recommend that you start a bug on bugs.launchpad.net. Once this is done, please subscribe me and ping me so that I test it to see if I can reproduce the issue.

Thanks

---

### Post by mc4man on 2009-07-20
In 8.04 you need to manually create choices, easy to do  once you get the idea.
There is a list that can be edited once per line (**and only once and only with a .desktop that's in /usr/share/applications**.

/etc/gnome/defaults.list

this was/is a quick way to add vlc as a default choice for dvd's, and i quess also for sound-juicer

This wouls be the set of lines
> x-content/video-dvd=[COLOR="Blue"]totem.desktop[/COLOR]
x-content/video-vcd=totem.desktop
x-content/video-svcd=totem.desktop
x-content/video-blueray=totem.desktop
x-content/video-hddvd=totem.desktop
x-content/audio-cdda=[COLOR="Blue"]rhythmbox.desktop[/COLOR]
x-content/audio-dvd=rhythmbox.desktop
x-content/audio-player=rhythmbox.desktop
x-content/image-dcf=f-spot-import.desktop
x-content/image-picturecd=f-spot-import.desktop


Replacing what's in blue with sound-juicer.desktop on the cdda line, vlc.desktop on the dvd line would add them respectively


It's far better in the long run to get aquainted with and learn to use 
~/.local/share/applications and ~/.local/share/applications/mimeapps.list (**and safer**

By default neither exist, once you make changes in file management -> media or add any r.click file associations or r.click -> open with -> open with other application -> use a custom command, they're created and lines are added.

Assuming you had a ~/.local/share/applications/mimeapps.list then this would add sound-juicer


```
 cp /usr/share/applications/sound-juicer.desktop ~/.local/share/applications

```

```
gedit ~/.local/share/applications/mimeapps.list

```

Look for this line
> 
x-content/audio-cdda=

If it's not there then enter this
```
x-content/audio-cdda=sound-juicer.desktop;rhythmbox.desktop;
```

If it is there then just add this to end (no spaces between entries
```
sound-juicer.desktop;
```

Audio Cd Extractor should now be a choice in file management->media

While i don't use it just added on a fairly new hardy install, see screen


Edit 
Here's an old post about such things. w/ links

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

### Post by Bucky Ball on 2009-07-21
Thanks people, especially mc4man for that extensive explanation. Excellent and understood. 

The news is I am now 750kms away from that machine after having driven from the in-laws today but I am currently sitting at my wife's machine which also didn't boot sound-juicer when an audio CD was inserted so perfect to play with!

As suggested, I added this line at the bottom:

x-content/audio-cdda=sound-juicer.desktop;rhythmbox.desktop;

Chuck a CD in and works a treat, there's sound-juicer. Terminal->Nautilus->Edit->Preferences->Media and there it is, this time under its other name, Audio CD Extractor.

Thanks a heap, I'll change the other one when I am back there in six months! Seriously, now I have fixed up the hardware problems the in-laws were having with the Ubuntu machine I built them at Christmas (no, the machine is all friendly, see my link in signature, but they had a bunch of not Linux friendly stuff which needed varying degrees of tweaking), my mother-in-law is a fast learner and will be changing that stuff in no time with the aid of the info above.

Cheers; educational and appreciated. :)

---

### Post by komputes on 2009-07-23
I have tried my solution on Ubuntu 9.04 and it seems to work for me. I am able to automate the opening of CDs with sound-juicer and DVDs with VLC.  I do not beleive mc4man's solution is the preferred way of doing this. If this is a bug specific to Hardy, please report it as such on bugs.launchpad.net in hopes of improving Ubuntu 8.04 LTS.

---

### Post by mc4man on 2009-07-23
Well actually now that I think of it audio cd extractor (sound-juicer) would automatically be registered for audio cd's. probably would be available straight up in file-management -> media.

Copying the .desktop and adding the line or entry to to existing line in mimeapps.list is basically doing the same thing. (and is the preferred method for creating autorun/autoplay choices, creating autoplay choices with custom launch commands, ect. ((vs. messing with defaults.list

In hardy vlc isn't registered for dvd's, so one must do manually. (same for many other apps

In addition some apps need a custom launch command to work properly as an auto run choice on removable media (or as an alternative choice for media or files, dir.'s

There are many advantages to seeing/learning how ~/.local/share/applications and ~/.local/share/applications/mimeapps.list work (not just confined to autorun of media


You could file bug reports till the cows come home, isn't going to change how hardy works 
(( and using ~/.local/share/applications ectt. is also very useful in more current releases, even in light of the fact vlc now registers upon install and the inclusion of a "use a custom command" in file management -> media

---

