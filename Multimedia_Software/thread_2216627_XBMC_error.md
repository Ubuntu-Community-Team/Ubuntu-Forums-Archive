---
title: "XBMC error"
date: 2014-04-12
forum: Multimedia Software
---

### Post by frank18 on 2014-04-12
Hi guys;i 'm trying ti install XBMC fron the software Center, and i get this error!

---

### Post by squakie on 2014-04-13
Try installing synaptic package manager:

sudo apt-get install synaptic

When it's installed, try installing via synaptic not the software center.

You can also try:

sudo apt-get install xbmc

---

### Post by frank18 on 2014-04-14
> **squakie said:**
> Try installing synaptic package manager:

sudo apt-get install synaptic

When it's installed, try installing via synaptic not the software center.

You can also try:

sudo apt-get install xbmc

thanks squakie:i solved my issue by sudo apt-get upgrade,i don't know why cause normally when i use to do a fresh install and sudo apt-get update would install all new solftware this time needed Upgrade,and the iso image was the same i used before,( Ubuntu 14.04 Beta2,)and i could install all the needed software to run the OPS,this time couldn't get most of the software needed.weird.

---

### Post by Adler on 2014-04-14
Hi All,

I've grown tired of playing with XBMX. I have deleted ppas, deleted XBMC, re-installed it, and keep loosing my favorites. The following no longer seem to work:

1Channel, and
Navi-X

I have followed every forum you can thing of, but the results end up being as good as searching on YouTube. That is - why is this application worth my time, and effort? It also seems there has been some type of division amongst those that created it? I've ended up in the alpha-ppa for 14, when 13 isn't even ready yet!

Is there a good, as Interface, to XBMC that* works*?

Adler
Wildwood, New Jersey

---

### Post by squakie on 2014-04-14
I personally gave up on XBMC in Ubuntu quite a while ago.  It does, however, work fantastic on the cheap little Raspberry Pi, an USB hub and an external drive.

I gave up in Ubuntu for a couple of reasons:

1.  Things would pause, go only a frame or 2, and pause again part way through what I was watching.

2.  MANY XBMC crash logs being generated - I assume that it must be aborting, restarting and that's why I saw the pauses.

BTW - Raspberry Pi - $39, USB hub ~ $20 - $30 (it *MUST* have it's own AC adapter - the Pi doesn't have enough current load on the USB ports to support more than 1 device.  Add in an external disk ($50 - $80 for decent sized), keyboard and mouse (I just use wireless - and you don't really need the keyboard but it makes typing things in where needed a lot easier).  The Pi has HDMI output with sound and it also has a composite output and analog sound output (for things like a surround sound system).  The OS is free (several available), and you need a small 8gb or so SD card to put the OS on - even though the info doesn't state it, you can put the system files, etc., on the external disk (I actually just use a 16gb USB flash drive in the hub).

The thing is - so far, for me at least, XBMC in Ubuntu is buggy and just not a good experience.  If you can afford it, the Pi makes a GREAT media center.  There are several free OS's with XBMC already loaded, at least 1 of which will just boot right into XBMC.  XBMC on the PI is great!  It becomes a no-need-to-touch box.

---

### Post by squakie on 2014-04-14
Frank18:  if I'm remembering correctly, sudo apt-get update only updates the package list from the repositories - it doesn't update any software.  You need to run sudo apt-get upgrade to install newer versions of the packages.

---

### Post by frank18 on 2014-04-14
> **squakie said:**
> Frank18:  if I'm remembering correctly, sudo apt-get update only updates the package list from the repositories - it doesn't update any software.  You need to run sudo apt-get upgrade to install newer versions of the packages.

Thanks squakie; i did that and all was ranning great including XBMC but i wanted to run gnome flashback and did these code commands see link; and now i click on XBMC and it opens and stays up for a second and exits, is there anything i can do to over come this thank.


[http://ubuntuforums.org/showthread.php?t=2184682&page=34](http://ubuntuforums.org/showthread.php?t=2184682&page=34)

---

### Post by squakie on 2014-04-14
Don't really know - I didn't read the entire thread, just the first page.  It would appear to be about putting Gnome "classic" as the default and not using Unity.  I have no idea how changing that around may affect XBMC.

First suggestion:

- open a terminal window

- type:

xbmc <press enter>

If it doesn't start xbmc there at least be some error messages that show on the terminal window.  You could try posting those back here to see if we can be of any help.  I suspect you're getting beyond my knowledge base, but please post it back.

---

### Post by Adler on 2014-04-14
Gentlemen,

The point is, is XBMC seems so *buggy*, is there an alternative? Few of the add-ons seem to work anymore, without kicking back an error message.

Even following many, many, forum posts I've deleted ppas, purged (in Terminal) XBMC*, re-installed it, but nothing seems to bring back XBMC to what it once was. Trust me I've worked my way around bugs before (sound, VirtualBox, etc.), but I'd just like to know if there is a simple alternative to XBMC?

I've gotten tired of XBMC...

Adler
Wildwood, New Jersey

---

### Post by frank18 on 2014-04-15
> **squakie said:**
> Don't really know - I didn't read the entire thread, just the first page.  It would appear to be about putting Gnome "classic" as the default and not using Unity.  I have no idea how changing that around may affect XBMC.

First suggestion:

- open a terminal window

- type:

xbmc <press enter>

If it doesn't start xbmc there at least be some error messages that show on the terminal window.  You could try posting those back here to see if we can be of any help.  I suspect you're getting beyond my knowledge base, but please post it back.

thanks again ,i run xbmc in terminal same thing it gets in the xbmc menu and stays there 3 seconds or so and exits by it self, in the terminal i have this crash report.

frank@frank-ThinkCentre-M71e:~$ xbmc
Running DIL (3.22.0) Version
DtsDeviceOpen: Opening HW in mode 0
DtsDeviceOpen: Create File Failed
Segmentation fault (core dumped)
Crash report available at /home/frank/xbmc_crashlog-20140415_080409.log
frank@frank-ThinkCentre-M71e:~$

---

### Post by frank18 on 2014-04-15
> **squakie said:**
> Don't really know - I didn't read the entire thread, just the first page.  It would appear to be about putting Gnome "classic" as the default and not using Unity.  I have no idea how changing that around may affect XBMC.

First suggestion:

- open a terminal window

- type:

xbmc <press enter>

If it doesn't start xbmc there at least be some error messages that show on the terminal window.  You could try posting those back here to see if we can be of any help.  I suspect you're getting beyond my knowledge base, but please post it back.

here the screenshot of the crash report.

---

### Post by squakie on 2014-04-15
I never got the immediate exit you have, but you are getting a lot of xbmc crashes and logs, so I would suspect you would need to go to the XBMC forums and ask for help there.  I tried, but they got a little uppy with me, especially as soon as I mentioned I also had Pi's running XBMC fine.

---

### Post by squakie on 2014-04-15
> **Adler said:**
> Gentlemen,

The point is, is XBMC seems so *buggy*, is there an alternative? Few of the add-ons seem to work anymore, without kicking back an error message.

Even following many, many, forum posts I've deleted ppas, purged (in Terminal) XBMC*, re-installed it, but nothing seems to bring back XBMC to what it once was. Trust me I've worked my way around bugs before (sound, VirtualBox, etc.), but I'd just like to know if there is a simple alternative to XBMC?

I've gotten tired of XBMC...

Adler
Wildwood, New Jersey

Not really in line with the thread here.  You should open your own thread asking about the available media centers available.  I've never used anything other the XBMC, but I have seen others mentioned.  You could also try an internet search with the following in the search string:

Ubuntu media center software

and see what/if anything comes up.

---

