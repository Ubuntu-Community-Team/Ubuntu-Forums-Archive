---
title: "Sony Walkman - No USB Connection"
date: 2008-07-18
forum: Multimedia Software
---

### Post by xie on 2008-07-18
So, I have a Sony Walkman NWZ-S616F and on the player's screen is "Connecting". I also have the latest version of Ubuntu (Hardy Heron) if that helps. Any advice to fix this problem?

---

### Post by OMEGA303 on 2008-08-17
Sony Walkman NWZ-S616F ubuntu 8.4

My solution to this problem about mounting the walkman 
From Add and Remove I installed “gnomad2” I restared the computer plug in the walkman and recognize it
Hope this help and sorry for the spelling!!


here is the link to gnomad2 web page [http://gnomad2.sourceforge.net/?]("http://gnomad2.sourceforge.net/?")

:lolflag:

---

### Post by valmorel on 2008-09-08
Here is the fix. It sounds a bit scary, but just follow the instructions. The problem seems to be a bug in Hal. Once you have fixed it, Walkman will automount just fine

[http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)

---

### Post by tattooed_pariah on 2009-12-06
Hey guys, 

I've researched this problem a little bit, but none of the solutions can help me and I was wondering if someone could help me with some special circumstances i'm working with.

I have the NWZ-S616F, when I run lsusb it does in fact show up as "054c:0327 Sony Corp." and the player's screen does reflect that it is connecting. All standard symptoms to this problem from what I can gather.

I'm running Hardy Heron 8.04 because that was the most recent distro when I left the states back in July.

This is where my problem comes in, I'm currently deployed on a ship, so there is no way for me to download updates or install things via "apt-get". I can't plug my laptop into a network basically..

Is there anyway for me to work around the problem with just what is already installed? Or am I SOL until I can get home and plug into my network again (I can't even wait until the next port visit because I have issues with my shitty built in wifi card.

Any help is appreciated!
Thanks

-matt

MC2(SW/AW) Matthew A. Hepburn 
Navy Public Affairs Support Element, West 
currently embarked on USS Chosin (CG 65) 
NIPR: [email]hepburn@cg65.navy.mil[/email] 
SIPR: [email]hepburn@cg65.navy.smil.mil[/email]
--------------------------------------------------------------
"I never trust a fighting man who doesn't smoke, drink, or at least cause a bit of trouble." 
-Fleet Admiral William F. Halsey, USN(ret.)

---

### Post by tattooed_pariah on 2009-12-06
hmm.. not a permanent solution, but I used the following to at least get access through Rhymebox:

from: [http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)

i took the following steps (for anyone else who finds this thread and needs similiar help..)

sudo-i
nano /etc/udev/rules.d/45-libmtp7.rules

add the following to the list of sony players

# Sony Walkman NWZ-S616F
ATTR{idVendor}=="054c", ATTR{idProduct}=="035b", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"


after I rebooted, it still says "Connecting USB(MTP)" on the players screen, but like I said, it appears in Rhymebox and I can edit what's on it again..:D

---

### Post by Kevbert on 2009-12-06
In 8.04 you need to mount the player manually according to [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/PortableDevices/Sony").

---

### Post by tattooed_pariah on 2009-12-06
That's for a different model walkman, and when i ran "killall gvfs-gphoto2-volume-monitor" it returned "gvfs-gphoto2-volume-monitor: no process killed"

With the way I did it above, it made it show up in Rhymebox, and I was able to delete the files that were on it and drag and drog music onto it. but it's severly lacking some things I have taken for granted..

Now all the music I just added is in the root directory, so I can't use the folder view to go through artist then album.. and the old directories are still there, just empty.

I guess this is what I get for frankensteining an old laptop about 2 weeks before leaving the country, haha. it's useable just not as well as i'd like, but I should be home in another 4-7 weeks, so I can deal with it..

Thanks, and if anything else comes to mind, I'm open to ideas!

-matt

---

