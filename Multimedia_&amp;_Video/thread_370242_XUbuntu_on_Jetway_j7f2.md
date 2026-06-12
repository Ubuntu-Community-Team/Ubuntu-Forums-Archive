---
title: "XUbuntu on Jetway j7f2"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by pab10 on 2007-02-25
Greetings!

I'm using Xubuntu 6.10 on Jetway J7F2 (been installed for a few days now, installed fine first time apart from no via CN700 graphics drivers)

First I'd say I like it, seems a good distro, especially choosing a lightweight desktop manager xfce which I was using on fedora, but... (apart from the question of subverting/usurping debian which would be a bad thing) 

1. Xubuntu when the volume control is touched using any mixer application sound packs up shortly afterwards (on via 8237R AC97)

was also getting bad interference on audio until I set XFCE to manage the desktop which is what I think cleard it up, now all RF type noise has gone.

ALSA works fine until the mixer/volume (even using the volume control on xmms) is adjusted when sound just stops working shortly (about a minute which is v.weird...???) afterwards (I have tested this repeatedly). 

Is this fixed in XUbuntu Fiesty?  I noticed an article that said sound was broke in fiesty KUbuntu

2. why does Xubuntu do a DNS lookup for google.com after boot/reboot before you even log on or start any apps? Just does a DNS lookup nothing else (I could see...)

(well its one way to pad google's DNS stats..)

Ubuntu seems to occaisionally do DNS lookups on google even if firefox (or any net applications) has not been loaded, about every 30 minutes

also noticed a secure connection to google being made after starting firefox for first time, yet my browser is set to load blank page, I certainly did not ask for it to connect to google, is that firefox or ubuntu's version doing that?

3. is it possible to incorporate a package for the via graphics drivers its a pain to build it each time a kernel is upgraded (via packages) or whatever

VIA have released some XOrg driver source on their website (via arena) that at last supports CN700 and compiles OK can that be included?, it seems to work quite well, but GLXgears while working a lot better complains that 3d driver claims it does not support visual 0x58 and a load of others (not sure what that means exactly)

Or... would it be better to package the openchrome drivers?

I was impressed to see GXINE was only using 20% CPU on a C7 processor with CN700 graphics (Via's drivers) while playing mpeg4 (much better than on FC6 with previous version of drivers from via) but then it started locking up the whole machine for some reason, I dont know what I did but it started working again (after installing mplayer I think or maybe something else like recompiling the drivers again??) but mplayer complains it was not compiled with mp3lib (I see its from an extra repository...) while trying to play some avi files.

---

### Post by pab10 on 2007-02-26
update - 

Firefox regularly contacts google for safebrowsing function built in to firefox2

Why ubuntu does a dns for google before its even loaded the desktop I am still not sure, it does not do a safebrowse update until you load firefox, and then it does another DNS lookup for that anyway.

Sound works until you move volume fader up to max position (or a high volume position) then it fails about a minute later, (wonder if its overflowed or something?) if I dont touch the volume I can play sound for hours on end no problem.  Cant say if it was after the update to edgy, as I only noticed it after the update.

---

### Post by Flecko on 2007-02-28
I am running Xubuntu Edgy on my Jetway j7f2 as well, and guess what, I have this same problem. The only difference is, my sound works if I don't touch the volume at all for about a day, but after that, it'll stop as well.

It doesn't matter if I adjust it or whatever, the sound just stops.
I wish we had some sort of resolution, but I just wanted to confirm that it happens to me as well.

Oh, and for the record, you should look into OpenChrome for your graphics driver. Its been great for me.
-Flecko

---

### Post by Flecko on 2007-03-01
Ok.

I think I've found the answer. I've only test it for 4 hours(but usually if my sound is going to die, it does it in a shorter period of time) but it seems to be working OK.

Just go here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
...and follow the instructions that have you download and install the latest version of Alsa. The only trick is that instead of using ./configure --with-cards=hda-intel or whatever, just make it this: ./configure --with-cards=via82xx

The rest of the steps are the same. Reboot, and your sound should be rock solid.
Maybe it'll still crap out eventually, but I'm happy with the way it works now.
Enjoy!
-Flecko

---

### Post by stuarttaylor on 2007-04-18
Are these issues likely to be sorted in the Fiesty update?

---

### Post by Nightdrive on 2007-05-15
Still a problem on feisty (I'm using ubuntu not xubuntu), and I got loads of compiler errors when trying to recompile alsa 1.0.13 using the VIA82xx option. :(
Looks like I just don't touch the volume control for now.

---

### Post by jhewer on 2007-05-15
i'm running Kubuntu Feisty with a Kernel upgrade to 2.6.21.1, and I'm getting the same issue with the sound.

i've followed the guide to update the alsa drivers, and have done so with version 1.0.14rc4, however i'm still experiencing problems with sound cutting out.

i only tested it once, but the sound did seem to last longer, but only 5-10 minutes.

i'm wondering whether anything needs to be configured in the KDE Sound System... or should the KDE Sound System be disabled entirely?

how should applications be configured to use the alsa sound driver?

thanks

---

### Post by jhewer on 2007-05-18
i've done some further tests with the volume at 75% rather than 100%, and the sound seems to have been stable so far.  if i encounter the problem again, is there any particular information i can provide you guys with to help resolve the issue?

thanks

---

### Post by pab10 on 2007-06-12
Not checked this thread for ages... thanks flecko et al for the comments... I found that audio problem was exactly what you said, just dont touch the volume control and its OK... (works fine under windows, and no intereference/noise on sound when mouse moves either...)

I put it on back burner for a while, and just tried 7.04 today, with exactly the same problem with audio (this was ubuntu not xubuntu so the problem has not been fixed and its common to ubuntu as well)

I'll check openchrome when I have some time and do the update to ALSA and post back once I have done it...

ATB...

---

### Post by pab10 on 2007-06-12
I applaud the new ubuntu 7.04 dual xp boot and partition resizing auto install... its cool!

didnt try the import XP user ID feature but thats cool too... (if it works :)

---

### Post by newkirk on 2007-11-18
> **pab10 said:**
> Not checked this thread for ages... thanks flecko et al for the comments... I found that audio problem was exactly what you said, just dont touch the volume control and its OK... (works fine under windows, and no intereference/noise on sound when mouse moves either...)

I put it on back burner for a while, and just tried 7.04 today, with exactly the same problem with audio (this was ubuntu not xubuntu so the problem has not been fixed and its common to ubuntu as well)

I'll check openchrome when I have some time and do the update to ALSA and post back once I have done it...

ATB...

Any update on this?  I experience the same 'sound cuts off after about 5 minutes' under Xubuntu & Kubuntu, both Gutsy 7.10.  And I'd be thrilled to see 'full support' of Via video (CN700) with both mpeg2 and 3d accelleration enabled.  Without having to rebuild drivers by hand every time a kernel update installs...

j

---

