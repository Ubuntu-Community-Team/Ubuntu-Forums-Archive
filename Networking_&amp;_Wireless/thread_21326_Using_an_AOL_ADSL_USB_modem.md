---
title: "Using an AOL ADSL USB modem?"
date: 2005-03-21
forum: Networking &amp; Wireless
---

### Post by jnoreiko on 2005-03-21
I'm with AOL in the UK, and I've got my ADSL modem to work on Windows without running the AOHell software.
So in theory, I should be able to do the same on ubuntu, right?

Except the new network connection wizard on ubuntu doesn't suggest the ADSL modem as a connection option, just the built-in 56k modem, ethernet, and so on.
The device manage shows the ADSL modem as connected to the USB port, but doesn't show anything else about it, so I suspect Ubuntu doesn't have drivers for it.

Any idea what to do?

---

### Post by paiva on 2005-03-21
i have the same problem with another modem, but no one seem to know about this.....

---

### Post by MrFunster on 2005-03-25
If you both post the type of modem (manufacturer/model) someone may be able to help.

I personally installed a speedtouch 330 with no proir knowledge at all.

---

### Post by jnoreiko on 2005-03-26
It's a BT Voyager 105.

---

### Post by MrFunster on 2005-03-28
Not sure whether this will help, have a look here:
[http://eciadsl.flashtux.org/index.php?lang=en](http://eciadsl.flashtux.org/index.php?lang=en)

Apparently the voyager is a bit of a pig to set up under linux.

---

### Post by jnoreiko on 2005-03-28
Yeah, looks like you're not wrong. :(

I'm getting this so far:

```
root@ubuntu:/home/joachim/Documents/adsl # eciadsl-start | tee log.tx 
[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

ERROR: modem not found
root@ubuntu:/home/joachim/Documents/adsl #

```

The ECI forum has a post on installing it: [http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2713](http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2713)

pretty heavy stuff for a linux n00b...

---

### Post by jnoreiko on 2005-03-28
Guess which OS I'm posting this on....  =D>

---

### Post by MrFunster on 2005-03-31
[QUOTE=jnoreiko]Guess which OS I'm posting this on....  =D>[/QUOTE]


So I guess congratulations are in order :-D

---

### Post by spicypixel on 2005-04-02
Hello, it seems as if u have had a successful transfer to linux :-P 
I have the same modem and AOL BB, and ive used Mandrake, SuSE and now im going to use Ubuntu. Im a linux novice, and a clear explanation of how it was set up would be grateful.

One question, does it alter the firmware so windows can't use it? :shock:  :-k

---

### Post by jnoreiko on 2005-04-02
The second post in the eciadsl forum thread linked to above is mine ( [http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2713](http://eciadsl.sourceforge.net/scripts/forum/viewtopic.php?t=2713) )

I more or less followed the tutorial ([http://eciadsl.flashtux.org/tutorial.php?lang=en](http://eciadsl.flashtux.org/tutorial.php?lang=en)) except I installed the deb file from the nortek ftp directory ([http://eciadsl.flashtux.org/download/nortek-2021/](http://eciadsl.flashtux.org/download/nortek-2021/) ) ("sudo dpkg -i filename") rather than the regular one.
You'll need to get ppoe too, as eciadsl has a dependency.

The bit about the dabusb module you can probably skip, as my warty just said it didn't have such a module.

Download and open the tar.bz2 file in the same directory and put the synch files from that into /etc/eciadsl/ (the tutorial forgets to tell you about this bit!)

Then run eciadsl-config-tk, select the BT Voyager 105 from the list and set the synch file to gs7470_synch03.bin.

Good luck :)

PS. Should I make a page in the wiki about this? And where?

---

### Post by spicypixel on 2005-04-02
Ok cool, im a complete new user when the console is involved, only used KDE with built in programs. I will try it, any more help and if u could do a Wiki with screen shots i would be very thankful

thanks in advance

---

