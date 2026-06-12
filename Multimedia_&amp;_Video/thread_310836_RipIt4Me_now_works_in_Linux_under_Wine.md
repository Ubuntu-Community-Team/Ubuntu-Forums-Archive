---
title: "RipIt4Me now works in Linux under Wine"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by Trespasser on 2006-12-01
That's right, RipIt4me now is functional under Wine. It seems the RipIt4Me team took notice of Linux and our lack of programs to deal with ARccOS and RipGuard protected DVDs and adapted their code to work under Wine. I can confirm that it does work very, very well.

Here is the link to the home page announcing its compatibility with Linux:
[http://www.ripit4me.org/](http://www.ripit4me.org/)

Here is the download page:
[http://www.ripit4me.org/download.html](http://www.ripit4me.org/download.html)

Download the RipIt4Me Installer. It contains the latest version of RipIt4Me as well as FixVTS. You will also need DVD Shrink and DVD Decrypter (both linked at the above download site).

You will also need Wine installed.

I'm running Dapper with a standard kernel and it works great for me. I just decrypted The Pink Panther which is loaded with ARccOS protection.

There is an offical RipIt4Me forum at this site:
[http://forum.digital-digest.com/index.php](http://forum.digital-digest.com/index.php)
To my understanding they will be adding a RipIt4Me under Linux subforum there soon.

Good luck, and have a good day. :) .

P.S.
There is now a How to install RipIt4Me in Wine at this address:
[http://forum.digital-digest.com/showthread.php?t=74727](http://forum.digital-digest.com/showthread.php?t=74727)

---

### Post by Trespasser on 2006-12-02
Shameless bump...

I hope I didn't choose the wrong forum to post this in because this subject is really important.

---

### Post by adamkane on 2006-12-02
Good work. Much appreciated.

Post this as a HOWTO in the HOWTO section, if you want people to find it. Make it as easy to read and follow as possible.

The forums are really busy. Most new threads don't get the attention they deserve. If you have a lot of thread views, but only a few new posts, that usually means people are finding the info they need from your thread and then are moving on.

---

### Post by Shatrat on 2006-12-02
Really important?
According to [the wikipedia list]("http://en.wikipedia.org/wiki/List_of_DVDs_Protected_by_ARccoS") The Lion, The Witch, and The Wardrobe is protected by ARccOS but I have no problem playing it with Totem with libdvdcss installed.

---

### Post by anjilslaire on 2006-12-02
Weird. 
I have dvdshrink & decrypter running fine under wine. Ripit4me installed fine, too.
But when I launch Ripit4me, and choose Wizard mode, it hangs on Updating Info on the DVD drive.

I'm very familiar with these apps under Windows, so I'm very excited to get them  working under Ubuntu, but I'm stuck right now, any thoughts? ](*,)

---

### Post by mcsix on 2006-12-02
I get it installed fine as well. After I start it though it just stops after it copies the IFOs.

[COLOR="Blue"]FixVTS version: 1.6.0.2 -- All OK

Wizard Step 1
SPTI layer available
UPDATING INFO
12 IFOs copied.
RipIt4Me Version 1.6.0.0[/COLOR]

Under the DVD section it says No DVD and the next button is grayed out.

I too have use it in windows with no problems.

---

### Post by Trespasser on 2006-12-02
You must be using Edgy. I tried it in Edgy as well but experienced that same problem. I normally use Dapper because of little bugs that are still present in Edgy, and besides I think Dapper is just great. I know of two Linux versions that run RipIt4Me in Wine with no problems...one is Mandriva 2007 and the other is Ubuntu Dapper. I know of one guy who claims he got Edgy to run RipIt4Me in Wine by going into winecfg>Drives and click Show Advanced then under Type select Autodetect.

When RipIt4Me 1.6.0.0 was released I was running Dapper with a custom kernel (2.6.16-ck12) but was experiencing the updating info/No DVD problem. On a hunch I installed the standard Ubuntu 686 kernel and suddenly everything works with RipIt4Me. I do a lot of copying purchased DVDs for backup purposes so this release is very big news for me. I was using VMware Player (with 14 gigs set aside) to run XP just so I could use RipIt4Me. Now I don't need to do that. I'm sure as time passes and new releases come out these problems will be resolved.

---

### Post by anjilslaire on 2006-12-02
Yup, Edgy it is.
Just tried Auto detect: no go. It doesn't even recognize anything as in the drive at all :(

Guess I'll be waiting for 1.6.1.0 :-k 

Thanks for the input.

---

### Post by Trespasser on 2006-12-04
OK, I just made a discovery for you people running Edgy with reference to the new RipIt4Me (1.6.0.0). I found an older version of Wine (version 0.9.5), installed it, and now it works great. No more "Updating info" or "No DVD" messages. I had Wine 0.9.5 saved to disc taken from this thread...HowTo Setup Wine:

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine)

but I think the link to that version is now dead. My point is...try an older version of Wine because a lot of things get broken along the way as WineHQ updates this product. If you can't find 0.9.5 then go to this address:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

and try some of the older versions they have listed. If you find one that works then go to Synaptic...click Status (in bottom left hand corner)...click on Installed (local or obsolete)...highlight wine...click on Package (at top left corner)...go down to Lock Version and click on it.

Hope this helps someone. :) .

---

### Post by Trespasser on 2006-12-04
I just found another version of Wine (Dapper 0.9.15) at this address:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

that works just great with the new RipIt4Me 1.6.0.0 (that's compatible with Linux). Totally uninstall your present version and delete the hidden folder .wine in your /home/user folder before installing 0.9.15 (or whatever version you find works for you). Also, make sure you lock the version in Synaptic afterwards.

---

### Post by Trespasser on 2006-12-04
I also discovered that after you first rip a DVD using Wine 0.9.15 and RipIt4Me 1.6.0.0 you can then upgrade to the latest Wine version (0.9.26) without any problems. Just make sure after you upgrade to 0.9.26 you open a Terminal and run:

~$ wineprefixcreate

to adjust Wine settings to the new version.

Hope this helps someone.:) .

How about some feedback if you've tried these instructions.

---

### Post by Rumpanzle on 2006-12-04
It stucks for me under Step 1, too.
But: when you click into the "Target directory for DVD files" and press enter it works.

(Edgy, Ri4M 1.6.0.0, etc.)

---

### Post by Trespasser on 2006-12-04
Did you try an older version of Wine? if so, what version?

---

### Post by Rumpanzle on 2006-12-04
Sorry, forgot to mention, this is with the latest wine 0.9.26. I can live with that glitch, I'm quite new to Linux and happy this took me only a couple of hours to get this to "work". The last days I spend more time gettings things to run than to actually work with them, so I'm happy with the current "solution".

---

### Post by Trespasser on 2006-12-04
Rumpanzle,
Trust me, you  should use Wine 0.9.15 with this new version of RipIt4Me. Works just as good as the Windows version. But that's up to you. Glad you got it at least partially going.

---

### Post by anjilslaire on 2006-12-04
Woot!
Thanks for the tips!
Downgraded to Wine 9.15, installed everything again, then upgraded to the latest .26. Everything's perfect. :-D 

Thanks again Trespasser

---

### Post by Trespasser on 2006-12-11
You people who are running Dapper should try the new Wine version 0.9.27 with the new version of RipIt4Me 1.6.3.0 because it works straight out of the box. No installing an older version of Wine first and then upgrading to the latest. Works great. Give it a try. If someone would try it under Edgy and report back then that would be great also.

Have a good day. :) .

---

### Post by Rumpanzle on 2006-12-12
Latest Wine/Ripit4me (wizard Mode, Use SPTI) still stays at DVD Drive "Updating info", throws a lot of "failed to copy VIDEO/VTS...", but when I put in a foldername between the two slashes for my folder "downloads\\VIDEO_TS" and press return it starts like I know it from Windows and everything is OK from there on. I went the Winedowngrade path (9.15), that didn't change anything, nor did the wineprefixcreate. Is that happening to you, too, or did I miss something?

---

### Post by anjilslaire on 2006-12-12
Just dropped the latest 1.6.3.0 ontop of my existing installation (see above, downgraded wine, installed, upgraded, etc). Seems to work great! Wine is currently 0.9.27

---

### Post by Trespasser on 2006-12-12
Rumpanzle,
If you want to get RipIt4Me to run properly under Edgy then use 0.9.5 linked at this address:

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=wine)

This version just works best for Edgy. Dapper's a different story. The latest Wine version (0.9.27) works great under Dapper.

There's nothing wrong with downgrading to an older version of Wine. Sometimes older is better. I don't know where this mind-set about newer being better came from...at least in the case of Wine. Wine gets broken all the time. The best advice concerning Wine is find a version that works for you and keep it.

wineprefixcreate is only used to adjust Wine setting when upgrading from an older version to a newer. The 0.9.15 version should have worked under Edgy. It did for me. 

Presently I'm running Dapper because my motherboard and power supply went south (using 500mhz Compaq). Waiting for new parts to come in.

Thanks for posting, Rumpanzle. :) .

---

### Post by Rumpanzle on 2006-12-13
Thanks, Mate!

That did the trick. Downgrade Wine to 0.9.5, checked RipIt4Me, worked, updated to latest Wine (0.9.27), wineprefixcreate, works. Prefect!

---

