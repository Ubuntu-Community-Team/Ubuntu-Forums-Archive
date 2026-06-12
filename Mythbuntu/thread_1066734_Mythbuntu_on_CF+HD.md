---
title: "Mythbuntu on CF+HD"
date: 2009-02-11
forum: Mythbuntu
---

### Post by ak2534 on 2009-02-11
I'm about to build a MythBuntu system which would be booting off an CF disk and utilizing a traditional HD for storing all the data which gets written regularly like the recorded TV programs and all other temporary data like databases.

Does anyone know which filesystems and/or directories in basic MythBuntu single-box installation get hit hardest byt disk writes?

---

### Post by jayman8547 on 2009-02-11
I boot my mythbuntu frontend to a 4gb SDHC card and I just use ext3.  It has been running great for about 4 months now.  On my backend I have two RAID 1 arrays - 500gb and 1tb.  The 500gb array runs ext3 and I use it to store pictures and documents while the 1tb array runs xfs and I use it for myth recordings and my DVD / BD rips.  I still want to add a 1.5tb or larger array to back it all up but from everything I've read the reliability of the 1.5tb drives leaves a lot to be desired.

---

### Post by ak2534 on 2009-02-11
The thing is that I want to use single machine installation so that the frontend and backend will be on same machine.
In that sense the databases etc. will be installed on a same machine.

Because of that, I want to create filesystems so that the static unchanged data including boot data will reside on the CF and all the stuff that frequently changes will be placed on the filesystems on the HD.

That's why I would like to know which filesystems / directories are under heavy writes.

---

### Post by ian dobson on 2009-02-11
Hi,

I boot my frontend from a 8Gb CF Card in a CF/SATA adapter (Backend runs on a different box).

I would say your recordings should be on the seperate harddisk but the mysql database should be on the CF card. Mythtv writes very often to the MySQL database and if you have it on you harddisk you'll be running the harddisk all the time (rather than powering it down when your out recording/watching a program).

Regards
Ian Dobson

---

### Post by priegog on 2009-02-12
I agree with ian; if you are trying to do this for the mythical beast that is flash degradation I think you're doing it for the wrong reasons. I've read somewhere that for earlier flash this was true, but with current manufacturing processes the amount of writes possible to a flash card is so high you shouldn't be worried at all about it. Think about it: how many of your flash devices have you needed to replace? I personally have both cards and thumb drives that are heavily used on an almost daily basis and are several years old and are just peachy. Sure, they don't compare to a computer's normal usage to a, hdd, but the truth is that there is no real evidence to support this. CF to IDE adapters have been around for a couple of years now (and before then there were guys modding their old powerbooks with CF to pcmcia to do the exact same thing), and NOWHERE have I read any report of anyone's card ever dying because of usage. So, you know, just make a script to image the card's content at the end of each day and save it to the hdd, and let the system run entirely off of it, and if it were to die, you can always buy a new (and cheaper) one. Oh and report it here so that I'll know this phenomenon exists. 
And as ian said too, this would allow your box to power down the hdd's when you're not actively watching something.
I'd tell you about personal experience but I've only been running my tablet off a CF card for a few months.

---

### Post by ian dobson on 2009-02-12
Hi,

Thanks priegog for agreeing with me. I've been running my frontend from the same CF card for about 8 months now and have not seen any problems with "ageing".

I have a 128mb usb stick that is now about 8 years old and has a really hard life (washed atleast 2 times with my jeans) and it's now being used as a opt file system for my dd-wrt linux router and is still going strong.


Regards
Ian Dobson

---

