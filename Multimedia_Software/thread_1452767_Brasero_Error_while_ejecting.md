---
title: "Brasero Error while ejecting"
date: 2010-04-12
forum: Multimedia Software
---

### Post by deeptiman.panda on 2010-04-12
Hi Everyone

I am currently using Ubuntu 10.04 Beta 2 version. Quite happy with the same. Among other issues, I am finding a curious issue with Brasero: After I burn the DVD using Brasero, it gives an error before ejecting. Attached is the error message. No issues with the burn or the data being burnt, but just it won't eject by itself and the program completes with an error as follows : Please eject the disc from "TSSTcorp CDDVDW SH-S223C" manually. The disc could not be ejected though it needs to be removed for the current operation to continue.

Any help is much appreciated.

Attached is the screenshot of the error.

Thanks and Regards

---

### Post by WinterRain on 2010-04-12
Sounds like a bug. Did you report it? Do:
```
ubuntu-bug brasero
```
You will need a launchpad account to do so.

---

### Post by RTrev on 2010-04-12
I just began getting that also.  I assumed it was because I was running Lucid Beta.  Now I have no clue, but you aren't alone! :)

---

### Post by mikeh on 2010-05-05
The bug is still there in the 10.04 release version.

Same hardware for me: TSSTcorp CDDVDW SH-S203D, SB00, max UDMA/100
It did not happen with 9.10.

---

### Post by RTrev on 2010-05-05
Note also this thread which is also running:

[http://ubuntuforums.org/showthread.php?p=9239534](http://ubuntuforums.org/showthread.php?p=9239534)

Mods: Is there an easy way to combine these two threads into one, if people feel that's appropriate?

---

### Post by Lucky LIX on 2010-05-11
Same here in release version (64 bit). Using an LG DVD writer and oddly the burned data dvd is not readable either.

Has the bug been reported?

---

### Post by walterav on 2010-05-11
In my case the disc also FAILS, its not readable after finishing! 

Burning an *.ISO file to a DVD-RW via the "Nautilus context menu", it gives the same error mentioned in this topic, only when selecting the lowest write speed. The resulting DVD is not read-able so burning failed.
Selecting the MAX speed does eject the DVD after writing "without the eject error", but also delivers a DVD which cannot be read by the OS or booting by BIOS!

Solution:
Burning the disc from 'terminal' with the following command works fine, although there is no LABEL:
```

cdrecord -scanbus #look at CD/DVD burner device location nr
cdrecord -v -dao dev=3,0,0 Downloads/lubuntu-10.04.iso #my device nr was 3,0,0 

```

Bug report:
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/578910](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/578910)

---

### Post by Geweten on 2010-05-14
Hmmm... 
Hi guys I have a similar problem but with Ubuntu 9.04... 
(which I found most stable till now) 
Same samsung DVD burner... At the end Brasero says : adding checksum and keeps on burning and burning (?) if I don't hit "cancel"...

Could it be because I put the OS containing HD in a new Amd K9 Gigabyte system ?

It's a bit nasty since I need a new Ubuntu .iso to be burned... 
With the former iso, the system says there is a reading problem : or the CD or the writer...:(

Meanwhile I'll try a usb install...

Knd rgrds

---

### Post by ggerri on 2010-05-15
I'm having similar problems. The issue seemed to come in a couple of month ago under 9.10.

I've been using Karmic ever since I've bought my Acer M5800 and everything worked fine - also the burning. But suddenly a few month ago, when I tried to burn some files on a dvd, burning always failed. Sometimes it burned 'forever'. So I've decided to wait for Lucid.

Set it up yesterday, inserted empty DVD, opend 'Nautilus CD/DVD Creator', dragged in some movie files, hit 'burn'. Burning process started and things looked good. then suddenly the process bar was gone and there was just this nautilus window listing the DVD content and it seemed all files were there, even there was no 'success-message'. the files were not readable though.

Then tried burning some files with brasero on CD. this seemd to work, but got mentioned message at the end 'Please eject the disc from...' . Pressed the cancel button and ejected manually. CD and files are readable....

Funny thing: I'm also using Lucid on my HP 8510P notebook and there, burning is no issue at all.

---

### Post by Geweten on 2010-05-17
Hmmm... Bizar... I believe it has sth to do with the DVDwriter on the one hand...
Since he gives errors on two .iso's that I'm damn sure of (9.04 & 9.10)
(Maybe my hardware is too fancy for the soft at the moment ?! :confused:)

On the other hand writing an .iso to a usb-stick using "***usb startup disk creator***" gives **finally "booterror"**

For **9.04** : Modprob:Fatal:couldn't load /lib/modules/2-6-28-11-generic/modules.dep:no such file or directory.
For** 9.10** : [errno5] I/O error

In some attempts to create a startup usb, I got an errormessage to check **~/.usb.creator.log**

Could someone please specify where that log is situated ? 
I didn't find it in the "log file viewer"
Or as I read somewhere is it better to use another usb creator ?

Thx in advance !

Oh yeah Ggerri, what brand is your DVD-burner ?

---

### Post by walterav on 2010-05-18
> **Geweten said:**
> 
In some attempts to create a startup usb, I got an errormessage to check **~/.usb.creator.log**

Could someone please specify where that log is situated ? 
I didn't find it in the "log file viewer"

It's a 'hidden' file in your 'homedir', open your user folder in 'nautilus' press CTRL-H on your keyboard and you will see all the .* hidden files.

Could you please verify burning the ISO file from the 'terminal' as I did, see my post earlier.

About the USB creator, make sure the Partition table "MBR" is a new one setup with Gparted, with a fat32 filesystem. To install gparted go to 'terminal' and type:
```
sudo apt-get install gparted
```

---

### Post by Chrisco66 on 2010-05-19
I cant get it to burn from nautilus or Brasero.  I started getting the eject fault a few days ago, but it would still burn.  Now, nothing.  I even changed my dvd drive because I thought it was the problem.  No help.  What happened to Brasero, it always worked before the "upgrade" to 10.04.  Is there a replacement for Brasero?

---

### Post by cor2y on 2010-05-24
I dont know what is the problem so i switched to k3b, seems in the end i always have to go back to k3b, in this version of brasero i cant even copy or create an audio/data cds since brasero complains that i am mission the cdda2wav, cdrdao plugins etc some of which are installed and others that dont seem to be in the repo and of course when doing data dvds i get that "please manually eject" popup message and even though the disc seems fine i worry, k3b doesnt give all these problems.

---

### Post by Geweten on 2010-05-24
Hi all,

Thx **Walterav**, I know the hidden folder issue, I always go to 'view' in the filebrowser and tick 'show hidden files.' Even then nothing to see... 
I thought the 'find' app would indicate it, but even this one overlooks the file...

I allways use Gparted for partitioning etc... 
Now strangely enough when I try to 'unmount' the usb-stick through Gparted, Gparted hangs... 
So before I use Gparted I have to unmount the usb on my 'desktop.' 

(It could be that I experimented a little too much with all kinds of softs... Even now I'm amazed that my Ubu-box is still at speed, windhose would have a registry problem by now !:P)

I'll try via terminal as you suggest... 

Yeah **Chrisco66**, this is the reason I don't upgrade too fast... 
I'm in there since Ubuntu 5 so I got smarter ! **lol** 
In order to maintain stabillity many companies keep on turning elder soft that has no 'children-deseases' any more... 
Before I upgrade I read reviews and issue-fora in order to evaluate if the time is right...:) 
(For fun I sometimes install new soft on a spare PC to make further evaluations...)

Thx **Cor2y** think I gonna check this one out too...

Thx all guys and now I'm going to get me some sun !:cool:
Cheers !

---

### Post by Chrisco66 on 2010-05-25
Geweten, I say that every time.  Then I start thinking "what are the chances that they would release a LTR with problems"?  

I went from 7.04 to 7.10--some problems, maybe my own doing

7.10 to 8.04--smooth

8.04 to 8.10--disaster

8.10 to 9.04--total disaster, had to reinstall on 4 machines.

9.04 to 9.10-- smooth, even fixed a few things

9.10 to 10.04--old hardware, no probs, newer stuff, three computers, three different probs.  This eject thing, and the wireless on an MSI wind. Had video probs on my laptop too, but I found a fix for that.   

I think Im just going to stay one behind from now on.  Ill upgrade to 10.10, when 11.04 is released.  I try to stay current, but for the last week, I have been doing nothing but trying to fix problems.  If I want to fix my puters all the time, Ill switch back to windoze..

---

### Post by biscuitboy1980 on 2010-05-28
I have this same freaking problem and I have also noticed when I burn dvd's the color is all yellow it is very annoying.  I have never had this problem before in 9.04, I have tons of problems now.  DeVeDe won't start on the first attempt ever, DVD won't eject after burning with Brasero, can't mount again without a reboot after Brasero can't eject, random x windows crashes, etc.  Pretty freaking annoying and I haven't seen a whole lot of updates.

I just want to be able to encode and burn DVD's again that don't look like crap.  I was so happy with 9.04 I wish I wouldn't have upgrade now.

---

### Post by iansane on 2010-06-06
Same issue here on 10.04  but disc reads fine after I manually eject it and close the error message. 

Doesn't mount automatically though. I have to go to the places menu and click on it to make it mount.

Seems to me like the problem is in the hardware driver since it has problems with eject and mount.

Eject works once I have it mounted. I right click on the dvd icon on desktop and eject and it works at that point.

---

### Post by Chrisco66 on 2010-06-10
10.04 does not work for many reasons. 

If I found a distro that worked on all my machines, I would switch today.  The problem is the kernel.  It is broken and they think it is an "improvement".  Most distros have switched to the new 2.6.3x kernel, but it no longer supports my wireless cards, or some video cards.  

9.10 was not perfect, but it was pretty close.  10.04 is like a copy of windows.  You want drivers, go find them.

---

### Post by DrTebi on 2010-06-11
I do get the same error message, however once I eject the disc manually (via the CD burners button), and close all Brasero windows, everything is OK. The disc plays on Ubuntu (with VLC Media Player) and also worked fine on gf's MacBook Pro.

I haven't changed any of the default settings of Brasero. Maybe it has something to do with the burner itself, mine is a Benq DVD DD DW1640.

Ubuntu 10.04
Brasero 2.30.0

It would be nice if there was a way to get rid of the error message and actually have Brasero eject the disc once burning finished... it seems that a bug report has been filed for this already.

---

### Post by RTrev on 2010-06-11
I was surprised to see that people are still having this problem, as it disappeared for me a long time ago.  Unfortunately I don't remember precisely when.

I currently have five installs of Lucid, both 32- and 64-bit, and one of Maverick.  All of them have the "Backports" enabled, although that's kind of pointless for Maverick at the moment.

Under Lucid, my version of Brasero is 2.30.1.  That's the normal Lucid version, so whatever fixed it may have been some dependency which was backported.

There has been no problem (so far) with Maverick alpha-1.

Unless you feel strongly otherwise, I suggest enabling backports.  My understanding is that all it means is that if, during development of a newer version, they find something that works really well, and they don't believe it will hose your older version, you'll be offered it as an update.  The devs are pretty careful about what they approve to be back-ported.  I'm only speculating, but backports may be why my problem was resolved completely quite a while back.

I'm sorry I can't give a precise time when it was resolved; I don't burn CDs often enough to pin it down for sure.  I'd forgotten about the problem, though, as I said.

Hope this helps someone.  Only enable backports if you're comfortable living a tiny bit on the edge.  I'm running Maverick alpha-1 as my main system, so that gives you some idea of how much I personally worry about breakage. <g>  Just make sure you have backups of your data, and then have fun.  A reinstall isn't that big a deal if something blows up.  But that's just me.  You may have other thoughts on blown up operating systems. :p

---

### Post by Elim_Garak on 2010-08-17
> **RTrev said:**
> I was surprised to see that people are still having this problem, as it disappeared for me a long time ago.  Unfortunately I don't remember precisely when.

I find it odd, too.  I get the ejection problem, but I have absolutely no problem reading the burned data.  It is kind of strange.  If I have a DVD or CD mounted, and I tell the system to eject it (rather than manually ejecting it), it does so without a problem.  I can use the eject command from the shell, too.  So, it's obviously not a problem with the mount/umount or eject commands.

---

### Post by RTrev on 2010-08-17
You know, now that I think about it, I did have the problem once again recently when testing Maverick.  What I found was that if I had a Nautilus winder open, the problems would occur.  If no Nautilus window, no problems.  Go figure.  Nautilus may have been trying to mount, or refusing to unmount, the CD?

Anyway, it would be interesting if you were to try that.  Keep Nautilus locked up in the basement and see if your CD problems go away.  <g>

Good luck,
Bob

---

### Post by wkulecz on 2010-08-17
After a recent update to Brasero, at least CD burning now works.  But I too get the very annoying "Can't eject disk" error at the end.  I can figure it out, but to a user like my wife, well they start looking at advetizements  in the newspaper for new Windows computers :(

---

### Post by Ctrl-Alt-F1 on 2010-08-28
I too am having this problem.  Is there a bug report already?

In my case burning and reading the burned cd (haven't tried dvd yet but I assume it will do the same thing) works fine.  The only problem is that when it finishes burning it says that it can't eject but it needs to.  If I hit "cancel", brasero still reports that the disc was successfully burned (and it would appear that it was since the disc works).

---

### Post by foxmulder881 on 2010-08-28
I get this message but there seems to be no consistency of when it appears and when it does not. I've learned to ignore it due to it not effecting burn quality or readability in any way.

---

### Post by Linuxforall on 2010-08-28
latest Brassero with bug fixes have been uploaded to PPA

sudo add-apt-repository ppa:renbag/ppa
sudo apt-get update && sudo apt-get upgrade

---

### Post by RTrev on 2010-08-28
> **foxmulder881 said:**
> I get this message but there seems to be no consistency of when it appears and when it does not. I've learned to ignore it due to it not effecting burn quality or readability in any way.

In my case, the problem does seem to cause faulty burns.  I've taken to using the script on this page to check final burns:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Usually my md5sums are wrong.  I've taken to not even bothering anymore.  I just give my wife the ISO and ask her to burn it for me.

---

### Post by foxmulder881 on 2010-08-29
> **RTrev said:**
> In my case, the problem does seem to cause faulty burns. <snip> I've taken to not even bothering anymore.  I just give my wife the ISO and ask her to burn it for me.

Why not just try another burning app. ie. K3B

---

### Post by RTrev on 2010-08-29
> **foxmulder881 said:**
> Why not just try another burning app. ie. K3B

I've found that when one is failing in this way, they all seem to.  And when one is working, likewise they all seem to.  I really can't pin this one down yet.

---

### Post by skunkbad on 2010-10-01
> **Linuxforall said:**
> latest Brassero with bug fixes have been uploaded to PPA

sudo add-apt-repository ppa:renbag/ppa
sudo apt-get update && sudo apt-get upgrade

I think this error is keeping me from burning multiple cds at once, so I'm going to try this and report back!

---

### Post by skunkbad on 2010-10-01
> **skunkbad said:**
> I think this error is keeping me from burning multiple cds at once, so I'm going to try this and report back!

No, it didn't work.

---

### Post by Zetheroo on 2010-12-21
Yeah, I have been getting this error with each and ever burn I do. The error would show up once in a while before, but now it's just each time. Very annoying ... is there a fix yet?

---

### Post by jayshomebrew on 2010-12-24
I've got an LG dvd burner, here is the message I keep getting after burning with brasero:

[[IMG]http://img571.imageshack.us/img571/2660/tmpsrkupl.png[/IMG]](http://img571.imageshack.us/my.php?image=tmpsrkupl.png)

and my dvds seem to come out fine.. Will try the upgrade to see if things get fixed.

---

### Post by neigun on 2011-01-16
The updated version of Brasero from the ppa unfortunately did not resolve the error message and the corrupted discs produced. I've also tried Nautilus, but again this didn't work for me.

So far K3b has worked fine. 

It's odd that Brasero which is shipped with Ubuntu should be so problematic/inconsistent. I don't burn discs that often and last December Brasero burnt a dvd containing mp3's just fine. Is this some sort of dependency issue?

---

### Post by 8200 on 2011-01-24
Same problem here with ubuntu 10.10 amd64 and all latest updates.

2.6.35-24-generic
and brasero 2.32

Just burned two faulty CDs because of this bug.


Is there a bug report for it?

---

### Post by ckaili on 2011-02-16
I came here because I got that same error and then the dvd was either completely unreadable or the data was all corrupt.  Went through several dvds and thought my burners were broken.  This was only happening when I made a data disk on a dvd.

Then, rather burning directly to disk, I tried making an image using Brasero.  The image should have been about 700mb but turned out to only be 2mb!  I concluded that it was a software problem.

I downloaded another program, k3b, tried to burn a dvd, also was not working... However, I tried burning an image with k3b and it outputted a file of the correct size.  I then used that image and burned it onto a DVD using Brasero and, lo and behold, it worked.  I still got that "could not eject" error, but this time it did not result in a burn error as well.

So... obviously that is not an ideal solution, but for all of those who were having trouble burning data dvds, try burning an image first, check that the size is correct, and then burn the image onto the dvd.

I know that's not directly relevant to this thread, but I thought I'd put it here since the eject error was the first thing I searched when I came across my problem.

---

### Post by wkulecz on 2011-02-16
Obviously this is a long running bug going back to 10.04beta with no real resolution.
 :(

I still never know if a CD/DVD burn will work or not.  I've gone through multiple cycles of it working, not-working, working, not-working, as a function of the most recent automatic updates during the life of 10.04 so far. 
 :(

Fortunately I don't need to burn CD/DVD much any more, and I still have a Windows machine or dual boot into 8.04 to use when I must, very inconvenient.

CD/DVD burning was so solid on 6.06 and 8.04 I stopped buying Nero updates for Windows, now I need to rethink the issue.

---

### Post by Chrisco66 on 2011-02-16
Well, mine has never burned data incorrectly, but the eject thing is still going on.

Just another in a long line of unresolved issues that started with 10.04.

My wireless still wont work on two different computers. My video wonk work correctly on another.  

I hate to say this, but Ubuntu is going in the wrong direction.  It used to work like magic, now it works like windows.

---

### Post by wkulecz on 2011-02-18
I'm happy to report that Brasero worked today to burn multiple copies of the recent 10.04.2 LTS CD (I need a couple of copies to use as Live CD from time to time).

Inserted blank disk.
Dismissed the blank disk inserted open dialog box.
Navigated to the iso image file and oposite clicked it, chose "Write to disk ..."
Clicked burn multiple copies.

When burn was complete disk ejected and dialog telling burning would resume when another blank disk was inserted.

Inserted blank disk, another blank disk option dialog popped up, which I dismissed and it looked like burning had already begun -- might be bugs here if anything other that cancel is clicked in a moment of confusion, but this is way better than what happend a few weeks ago!

All system updates current as of last night.

Both burned CDs read fine on a random windows box.

---

### Post by LowSky on 2011-05-24
Same issue in 11.04... seriously how long is this bug going to be an issue?

Issue occurs on LiteOn and Samsung drives. all SATA if that helps.

---

### Post by Chrisco66 on 2011-05-24
Mine is a PATA, and the brand is LG.

Im not sure if this a high priority bug.  Most folks can still get the disk burned, its just a problem with the ejection.  From what I understand, there is a whole new crop of bugs in 11.04 that must be keeping the devs busy.

Its annoying, but since its been going on for over a year, I guess Im just used to it.  

Ubuntu is not without its bugs.

---

### Post by Kivech on 2011-05-31
Well, it has gotten worse for me in this case.

First I just had the eject error, but when trying to burn my backups today, any kind of disk (RW, R, DVD, CD) it doesn't matter becomes carbage after trying to burn it.

I lost 6 disks so far, and none of them are even recognized as disks after the several faillures that show up when trying to burn a data disk.

Going to try to create an image first now with K3b, but it is rather annoying that something like this is roaming around for so long and never has been fixed properly over the years.

Guess I'll be going back to Vista. Can't work without being able to backup my work.

---

### Post by makro on 2011-06-06
> **jayshomebrew said:**
> I've got an LG dvd burner, here is the message I keep getting after burning with brasero:

[[IMG]http://img571.imageshack.us/img571/2660/tmpsrkupl.png[/IMG]](http://img571.imageshack.us/my.php?image=tmpsrkupl.png)

and my dvds seem to come out fine.. Will try the upgrade to see if things get fixed.

Same here but DVD is unreadable.... I've HP ProBook 4520s with HP GT30L

---

### Post by karhulitos on 2011-06-26
> **Ctrl-Alt-F1 said:**
> ...  If I hit "cancel", brasero still reports that the disc was successfully burned (and it would appear that it was since the disc works).

Wow! Almost gave up. Hitting Cancel saved my data (ejecting lost it) or I just got lucky. Anyway, bits on the disc now. Pioneer BDR-TD01 on a Sony Vaio.

---

### Post by sites on 2011-07-28
I've experienced this several times.  Only once was the disc unreadable & that was on a Mac.  Still, an annoying little bug.

---

### Post by mrego on 2011-10-02
> **makro said:**
> Same here but DVD is unreadable.... I've HP ProBook 4520s with HP GT30L

Same here! With external HP DVD burner..

---

### Post by mrego on 2011-10-02
> **mrego said:**
> Same here! With external HP DVD burner..
But with K3b works fine..

---

### Post by Ken UK on 2011-10-02
I have the same problem with my Macbook. I have to restart it to eject.

---

### Post by neigun on 2011-12-13
Hi 

I can't believe this is still an issue.

The gui for Brasero is really simple but the problem being is that it does not work for so many people.  Here we are on 11.10 and the bug has still not been resolved!

However, I should say K3b works really well.  Maybe its time to try Kubuntu for a bit of a change......

Neil

---

### Post by ezsit on 2011-12-15
+1 to dump Brasero

I have never had any luck getting Brasero to burn a successful CD or DVD. When using Brasero to burn data CDs and DVDs, from 10.04 through 11.10, I get a disc with no readable data when inserted into the same computer or any other computer.

When I use K3B I get a successful burn every time, no failure whatsoever. When I have tried Gnomebaker, I get successful burns every time.

I have used PATA DVD burners from Pioneer, Asus, Sony, and Lite-On over the past couple of years, and Brasero has failed to work properly on each drive I have used. K3B has worked on every drive, every speed, every disc type.

Conclusion, I will never trust Brasero and can not for the life of me see why it is included in Ubuntu. Ubuntu should stick to Gnomebaker. Yet now I see Gnomebaker is no longer in the repos because it has not been updated in over two years. The way I see it, if Gnomebaker can work well and does not need updating, and Brasero gets constant updating but never works well, what the hell is Ubuntu doing by including the crud that is Brasero?

---

### Post by Kn13htmare on 2012-01-04
For me a work around is to disable checksum plugin from brasero-edit-plugins menu.

---

### Post by tgwaste on 2012-05-05
*SIGH*

Here we are on 12.04 and this bug STILL exists.

and Ubuntu wonders why its software installs are going way way down.

Heres a hint guys: Its not all because of unity.  Instead of working on flash, FIX YOUR BUGS!

---

### Post by watgrad on 2012-09-11
> **Kn13htmare said:**
> For me a work around is to disable checksum plugin from brasero-edit-plugins menu.

Yes - disabling this plugin also fixed this problem for me.

---

