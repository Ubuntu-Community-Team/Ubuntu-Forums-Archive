---
title: "edubuntu &amp; wireless network"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by thefamousnomo on 2006-04-19
hello people

found this

*[http://www.ubuntuforums.org/showthread.php?t=162587](http://www.ubuntuforums.org/showthread.php?t=162587)*

sounded ok, thought id give it a go!

no probs right up to

*$ sudo modprobe ndiswrapper*

then after 2 secs the machine freezes!

im running an hp e-vectra (@566mhz) with a generic usb dongle, with edubuntu for my 3 year old son. would like to into the net as gcompris isnt holding his attention as once twas! .inf & .sys files on the cd, begging for me to try this.

any ideas how i can troubleshoot?

thanx

ps. *sudo ndiswrapper -l* shows both driver & hardware present, SiS163u from memory

---

### Post by thefamousnomo on 2006-04-20
c'mon guys!

tried disabling acpi & pnpbios by modifying the grub boot entry as this helped with my laptop wireless issues but im really just clutching...

thanx

---

### Post by thefamousnomo on 2006-04-21
update!

does no-one reply because im using edubuntu?

after trying the xp versions of SiS163u.inf & .sys the machine no longer freezes after *sudo modprobe ndiswrapper*. still doesnt work though!

would like to try updating ndiswrapper but im not sure how i can do this without a connection!

any ideas / advice would be appreciated!

thanx

---

### Post by thefamousnomo on 2006-04-21
92 views and no ideas?

would really appreciate any ideas / advice.

thanx

---

### Post by thefamousnomo on 2006-04-22
totally disheartened guys.

why does no-one reply? normally its almost instant, is this because im using edubuntu, or some other reason?:confused:

---

### Post by RedFoxEvan on 2006-04-22
i will reply just for you </3 , I dont have a clue what your on about, but on my first look i will reply :D

---

### Post by az on 2006-04-22
[QUOTE=thefamousnomo]totally disheartened guys.

why does no-one reply? normally its almost instant, is this because im using edubuntu, or some other reason?:confused:[/QUOTE]
You probably don't have the correct .inf driver for your device.  Even the one that came with your device in the box may be too old.

Probably no one replied because they are not familiar with that device - it is not too common, AFAIK.

---

### Post by ubuntu27 on 2006-04-22
I cannot help you since I don't know about WirelessNetwork. 

I have seen that the hardware section gets slower response than the other forum.

How about if you re-post in another forums such as Ubuntu Gnome SUpport Forum? 

After all EDUBUNTU is UBUNTU+Educational packages... 


Good Luck!

---

### Post by thefamousnomo on 2006-04-23
[QUOTE=azz]You probably don't have the correct .inf driver for your device.  Even the one that came with your device in the box may be too old.[/QUOTE]

is it more likely to be this than the version of ndiswrapper im using? if so i can track down the latest .inf from the web, but im concerned that ndiswrapper from the 5.10 install cd may be too old also. not having a connection is making it difficult to install the latest (1.14). got the binaries with build-essential installed but struggling with the 'headers' concept!

any ideas, thanx for replying people!

---

### Post by az on 2006-04-23
Look at the ndiswrapper changelog and see if support for your card was added or changed since the 1.1 version.  If there is no mention, it is either unfixed, or an .inf problem.

---

### Post by thefamousnomo on 2006-04-27
hello people

quick google search for sis163u.inf turned up this

*[http://www.smallwhitecube.com/php/dokuwiki/doku.php?id=howto:tew424ubv2](http://www.smallwhitecube.com/php/dokuwiki/doku.php?id=howto:tew424ubv2)*

now, seemed pretty straight forward. installed *build-essential* and kernel headers (*2.6.12-9-386*) from the cd. then i hit problems. referring to the above link

*export today=`date +%Y.%m.%d`*

being pretty comfortable with php scripting i assumed that this should expand into todays date. didnt. got rid of single quotes (in php single quotes return explicit). didnt. used double quotes (php again). didnt. is my assumption correct, this should expand?

but more problematic was the fact that

*mv /lib/modules/`uname -r`/net/ndiswrapper /usr/local/src/Ndiswrapper_$today/ndiswrapper-old*

returned there was no */lib/modules/`uname -r`/net/ndiswrapper*. also, i substituted 2.6.12-9-386 for *`uname -r`* (expansion?). still no such directory.

setting the link seemed to work ok, but make && make install just returned errors and no joy ](*,) 

summarised - is this link do-able? should it work? is the info accurate? if not, what should i do to install the latest ndiswrapper. according to this link, if i install that i should have wireless connection (ultimate goal!)

thanx

---

### Post by thefamousnomo on 2006-04-28
c'mon guys, i have to persevere with this!

in some threads i see people encouraging other people not to give up...

any ideas?

thanx

---

### Post by thefamousnomo on 2006-05-03
not one person, not one idea...?

---

### Post by thefamousnomo on 2006-05-11
*** anyone? ***

---

### Post by thefamousnomo on 2006-05-15
305 and no-one has any clue?

this is breaking my heart and spirit...

---

### Post by thefamousnomo on 2006-05-16
totally let down guys, i know someone must be able to help, with the questions if not the answer.

*** gutted ***

---

