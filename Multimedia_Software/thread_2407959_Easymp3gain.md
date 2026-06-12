---
title: "Easymp3gain"
date: 2018-12-11
forum: Multimedia Software
---

### Post by daroba on 2018-12-11
(translated by Google) 
Hi, a few days ago I upgraded from Ubuntu 14.04 to 18.04. And one of the strange things that I found is that I did not have my dear easymp3gain program.

I have read several threads of the forum that deal with the issue but I have not managed to advance.

According to Synaptic I have installed the mp3gain 1.5.2-r2-6 bionic1.0 and easymp3gain-gtk2 0.5.0-2 packages

For this I added the repository [http://ppa.launchpad.net/flexiondotorg/audio/ubuntu](http://ppa.launchpad.net/flexiondotorg/audio/ubuntu)

And I downloaded the GUI easymp3gain-gtk2 .deb file for amd64

I have tried other things but I lost myself in the explanation.
I have installed similar programs but they do not have GUI and I do not find them comfortable to use.

When I type ...

tamaida@tamaida-pc:~$ mp3gain
==4009==ASan runtime does not come first in initial library list; you should either link runtime to your application or manually preload it with LD_PRELOAD.

tamaida@tamaida-pc:~$ easymp3gain
[WARNING] Out of OEM specific VK codes, changing to unassigned
[WARNING] Out of unassigned VK codes, assigning $FF
[FORMS.PP] ExceptionOccurred 
  Sender=EInvalidOp
  Exception=Invalid floating point operation
  Stack trace:
  $00007FE3AF65F8B1
TApplication.HandleException Invalid floating point operation
  Stack trace:
  $00007FE3AF65F8B1
[FORMS.PP] ExceptionOccurred 


The question is: Can it be fixed? Will I be able to use easymp3gain in Ubuntu 18.04? And if so, what do I have to do?

If there is no way I think I will return to 14.04.

Thank you and sorry for the inconvenience. Especially if the subject was already answered, but my knowledge of both English and Linux is very limited.

Thanks again

---

### Post by ra7411 on 2018-12-11
Yeah, I've gone through a number of hassles installing this program, too.

Synaptic and Ub software show "easy" (which is the gui version) as being available, but when installed still no gui.

I did get it installed into Ub 18.04 about a month ago, and possibly you need GDebi Package Installer installed first, then try these:

sudo gdebi easymp3gain-gtk2_0.5.0-2_amd64.deb (64 bit version)
    
sudo gdebi easymp3gain-gtk2_0.5.0-2_i386.deb (32 bit version)

If no luck, try synaptic and Ub software again, maybe reboot.
 Everytime I've had to install it, it wound up being an odd process that required patience and repeated tries.

But, yes, it is usable in 18.04.






[h=1][/h]

---

### Post by daroba on 2018-12-11
Hello, thank you very much for answering so fast.

I have not installed the gdebi, I just installed the i386 with the ubuntu package installer. In fact, I had tried it before and it started but I had not managed to put it to work.

Now I have tried it again more calmly and I have noticed that the button to load folders does not work, but the one to load loose files. And works!!! Of course, with an "old look", as if it were executed by wine, type win98, or something like that. but hey, it works.

One more thing. Is it possible to make it work with the usual appearance and the button to load folders?

Thank you very much again. For now we will continue testing 18.04

---

### Post by ra7411 on 2018-12-11
> **daroba said:**
> Hello, thank you very much for answering so fast.

I have not installed the gdebi, I just installed the i386 with the ubuntu package installer. In fact, I had tried it before and it started but I had not managed to put it to work.

Now I have tried it again more calmly and I have noticed that the button to load folders does not work, but the one to load loose files. And works!!! Of course, with an "old look", as if it were executed by wine, type win98, or something like that. but hey, it works.

One more thing. Is it possible to make it work with the usual appearance and the button to load folders?

Thank you very much again. For now we will continue testing 18.04


I always use it by loading individual files, but I know with 16.04 that it did allow loading a folder. I just tried the folder button and it didn't give the option for individual folders.

---

### Post by vanadium on 2018-12-12
mp3gain is dead. Apparently it has been dropped from the Ubuntu repositories for a while now. Without mp3gain no easymp3gain.

I now use python-rgain. This is a replay gain calculation tool (commandline only, a.f.a.i.k.) that works with most audio formats. It calculates and writes replaygain tags. Nowadays, most players can handle these tags. Installing python-rgain gives you the commands "replaygain" and "collectiongain".

The command can be as simple as

```

replaygain *.mp3

```
This way, it will calculate track gains and album gain considering all files as part of the album.  

What replaygain does NOT do that mp3gain could is use an alternative way of adjusting replay gain, which is mp3 specific. That alternate method involved adjusting the amplification factor for each of the audio frames in the mp3 file. That approach had the advantage that the correction would be applied on any mp3 player, also those that did not support replay gain tags. The disadvantage was that only one correction could be applied, i.e. either track or album but not both, that the correction could only be done in steps of 1.5 db, and that it was only reversible if you knew the gain correction that was applied (mp3gain wrote a tag for that).

---

### Post by daroba on 2018-12-13
Thanks, maybe one day I dare to try those commands but for now I prefer to continue using the program that I already know.

Also, for what you explain, mp3gain seems much more interesting to me ("... any mp3 player ...")

Thanks

---

### Post by vanadium on 2018-12-13
For sure, you should definitely use (or try to use) what you prefer. I think, however, that it is interesting information for other readers stumbling on this thread. There is few information on the state of mp3gain, and users wonder why it is gone from the repos. Have struggled myself with the issue until I settled on python-rgain.

---

### Post by ra7411 on 2018-12-13
>mp3gain is dead. Apparently it has been dropped from the Ubuntu repositories for a while now. Without mp3gain no easymp3gain.<

I've used it for years, lately on an 18.04 install - it works fine.[IMG]https://ubuntuforums.org/asset.php?fid=276395&uid=1907792&d=1544733335[/IMG][ATTACH=CONFIG]281925[/ATTACH][ATTACH=CONFIG]281925[/ATTACH]

---

### Post by ajgreeny on 2018-12-13
I use mp3gain but only as the command line app, which does all I need and is very simple to use.
I also use mp3wrap and mp3splt which I believe were all part of the same suite of apps; they are very useful to me and I hope they don't go the same way as mp3gain seems to have done.

It came from the flexiondotorg-audio ppa as mentioned above.
However I am going to try the python-rgain mentioned as well to see which I prefer.

---

### Post by ra7411 on 2018-12-13
>Thanks, maybe one day I dare to try those commands but for now I prefer to continue using the program that I already know.<

Maybe terminal is a better way to go - saves time wrangling for a gui.

Put the subject mp3 files into an empty folder.

Using Files manager, right click on that folder, look for "open in terminal" and click it, you get a Terminal window on that folder.

Type in mp3gain -r *  to adjust those files as individual files to their own individual adjustment levels, 89 db.

Type in mp3gain -a *  to adjust those files as an album, some artistically intended to be louder than others, 89 db as a sort of center point for the batch. 

To see the various options for analysis / adjustment: mp3gain -h

Apparently, mp3gain is designed to give best quality results if 89 db is the target.

xx

---

### Post by ajgreeny on 2018-12-14
I wasn't aware of that 89db threshold, but I never go to the full suggested degree if I'm amplifying the sound anyway in order to avoid clipping.

Thanks for the info!

---

### Post by nik.charles on 2018-12-20
There is an alternative gui application that uses mp3gain - [qtgain]("https://sourceforge.net/projects/qtgain/")

@Vanadium mentioned that mp3gain can make permanent changes to mp3 audio levels
This is one of the reasons I do not use or recommend mp3gain
a replaygain scan should not be changing mp3 levels in this way - it should just write a couple of metatags to advise a gain level setting for music player
I have had 2 very unhappy people use mp3gain incorrectly and ruin a large number of mp3 files before they realised there was a problem
for one I managed to rescue the files with mp3gain undo options - but it took half a day to fix them
the other guy panicked and started trying anything he could find online and I couldn't fix his

I was using replaygain long before moving to Linux
replaygain in command line on new mp3s are consistent with older mp3s scanned in Windows
mp3gain does not produce same results as replaygain - there is an audible difference in levels and gain adjustment numbers in mp3 tags

As OP has already used mp3gain switching to replaygain would probably require all previous mp3 files to be scanned again to keep levels consistent
(usually not an option if mp3 collections is large and would take days or weeks to re-scan)
Only thing I recommend is use the same scan method for all mp3 files

---

