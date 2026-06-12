---
title: "nForce2 OSS nvidia drivers"
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by Dracontopes on 2005-11-01
And again I am trying to get the nvidia drivers to work. ESD works fine, but multiple sounds are not working. I have tried a How-To with ALSA, but that didn't work eiter. I read some post where some people did manage to get the nvidia drivers to work. (I know OSS is old etc, but it does use hardwaremixing...)

Here goes: I have no problems making the modules etc, but I need to put some lines in some files and I have no clue where to put them.

Step 1:
This is what I am supposed to do:
> [SIZE=1]If your configuration file already contains an entry for the i810_audio or snd-intel8x0 drivers (open-source audio drivers that supports the nForce audio controller), that entry needs to be commented out with a # or removed:

# alias sound-slot-0 i810_audio

 Add the following lines to the configuration file:

alias sound-slot-0 nvsound
alias snd-intel8x0 off
alias i810_audio off 

 On some distributions, you may need to replace sound-slot-0 with snd-card-0.[/SIZE]

I have found **/etc/modprobe.d/** and **/etc/modutils/** which has some files with aliases (such as the file alsa-base). There is also a file **/etc/modules** where modules can be loaded, but I'm not sure if *nvsound* should be put there. Which one do I edit? And/Or, which file makes snd-intel8x0 to load? If I know which file to edit I will be one step closer to good sound :)

---

### Post by Dracontopes on 2005-11-01
Right now I have accidently made it so that ESD now works with simultanious sounds. So this thread is no longer necessary. ;)

---

### Post by Bogus83 on 2005-11-02
Actually if anyone has the answers I'd be very, very interested in hearing them.  I've been having the same problem for the past several days, and nobody seems to have a straightforward answer.

---

### Post by 2beers on 2005-11-11
I have the same problem - didn't find a sollution yet.
So please post what u did - what u configured - guess that would b some great help - not only for me!

regards

---

### Post by Dracontopes on 2005-11-11
[quote=2beers]I have the same problem - didn't find a sollution yet.
So please post what u did - what u configured - guess that would b some great help - not only for me!

regards[/quote]

Do you refer to the nVidia drivers? I don't use them anymore. I had them installed, but I had troubles with nvmixer and decided that OSS was crap and undid (lol) the changes I had made. Then I rebooted and similtanious sounds were working, very strange. I don't remember exactly what I did, so I can't help u on setting up ESD correctly. I only know that I its configured as it came with Ubuntu. (default)

If you want to install the nvidia drivers, check this thread:
[http://www.ubuntuforums.org/showpost.php?p=462141&postcount=8](http://www.ubuntuforums.org/showpost.php?p=462141&postcount=8)
(it has a how-to! :D)

---

### Post by Teroedni on 2005-11-11
hmm i actually remeber having this problem myself , but that was in Hoary
Are everybody Using Brezzy?
My breezy installation fixed it all no problemo:), but the sound gets very bad if i go over 80% in volume.(Disorted)

---

### Post by 2beers on 2005-11-12
yes i use breezy
Hardware:
Board: Asus a7n8x deluxe + nforce2 chipset => sound onboard

---

### Post by Teroedni on 2005-11-13
I believe this may help for thoose with sound problem. I used it on my hoary before upgrading to brezzy trough apt-get;)

[http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567)


Hope its help

---

### Post by Dearhell on 2006-01-21
This worked fine to me: [http://www.ubuntuforums.org/showthread.php?t=96370&highlight=nvmixer](http://www.ubuntuforums.org/showthread.php?t=96370&highlight=nvmixer)

---

