---
title: "k3b - video dvd - windows"
date: 2008-05-08
forum: Multimedia Software
---

### Post by adambrd on 2008-05-08
I use Kubuntu 8.04. 

I have burned video dvd in k3b 1.0.4 (kde 3.5.9). I can play it on dvd player. It is ok. 

But when I want to see content of dvd on PC with Windows - I cant see any directory - like empty dvd.

can you help me?

thanks

---

### Post by aarb00 on 2008-05-10
I have the exact same problem using Ubuntu 8.04.  Discs play on set top players, but not in Windows.  I have burned using two different computers with different DVD burners and different blank media.  8.04 and K3b are the common factors.  I did burn an image in Nautilus and got the same result; so I don't think the problem is specific to K3b.  I have seen other threads on this, none with any resolution.

Does anyone have any ideas?  How many of you are experiencing this problem?

---

### Post by aarb00 on 2008-05-11
I found this article on Microsoft's website.

[http://support.microsoft.com/kb/899527/](http://support.microsoft.com/kb/899527/)

It may be related to the problem.  I updated one of my computers to SP3 which updated the udfs.sys file, but it still won't play the discs.  They still show up as blank.

I found another site that suggested that the cdfs.sys was the problem.  Updated that too and no luck.  Another site said they had luck using the cdfs.sys file from Windows 2000 on their XP machine.  Tried that, no luck.

The article says Windows can't read a sparing table longer than 1 sector.  Is there anyway to test my disk to see if that is the problem?

---

### Post by mc4man on 2008-05-11
> 8.04 and K3b are the common factors. I did burn an image in Nautilus and got the same result; so I don't think the problem is specific to K3b
If you can't playback a burned video dvd in windows then then problem is with the iso and the app that created it, in this case K3b. I generally only use imgburn in wine (superior control, info, ect. for iso creation and burning). Occasionally though  I'll use k9copy to transcode and create an iso then cd/dvd creator to burn and they come absolutely fine. There's no problem in playback in windows (xp or vista). If K3b will allow  output to a video_ts try opening that in K9 and creating an iso from there. The only issue I've seen with k9 is sometimes the iso is missing .iso from the name, just use rename and add .iso to end.
Even though I think 8.04 is ill suited when audio and video playback, editing ,creating, ect. is of importance to the user, (particularly if you have 2 optical drives) in this case it's not a factor.

---

### Post by aarb00 on 2008-05-11
I'll try to make ISO files instead of VIDEO_TS folders and see if it makes a difference.  An interesting note is that VLC will playback DVDs that Windows and Windows Media Player see as blank; so any discs that have this problem can still be played on a Windows machine.

---

### Post by aarb00 on 2008-05-11
I made an iso file instead and burned it with cd/dvd creator and it worked in Windows and set top DVD players.  K3b, or one of its components, must be creating code not compatible with Windows.

---

### Post by adambrd on 2008-05-16
> **aarb00 said:**
> I made an iso file instead and burned it with cd/dvd creator and it worked in Windows and set top DVD players.  K3b, or one of its components, must be creating code not compatible with Windows.

where can I find cd/dvd  creator? how do you made an iso file? I am sorry but I have not made an iso in linux yet. thanks

---

### Post by aarb00 on 2008-05-18
CD/DVD creator is built in to Ubuntu.  It is what comes up when you double click on an iso file.  I am not sure if this is the same with Kubuntu.  Bottom line, you need a proper ISO or you will have this problem.

I made the ISO using DVD Decrypter HD.  It is a Windows program that runs under Wine.  You can use it to convert your existing DVD to an ISO file, then double click on the ISO, and burn.  

If you are making your own custom DVD and only have the VIDEO_TS folders that you made in Kubuntu, then you can use ImgBurn (also in Wine).  

It appears that if you ultimately want a DVD to play in Windows Media Player, you need to use Windows tools to create the ISO.  If you only need it to play in Linux, a set top DVD player, or VLC in Windows, then you can use Linux tools.

Hope this helps.

---

### Post by hasinasi on 2008-05-22
> **aarb00 said:**
> I found this article on Microsoft's website.

[http://support.microsoft.com/kb/899527/](http://support.microsoft.com/kb/899527/)

It may be related to the problem.  I updated one of my computers to SP3 which updated the udfs.sys file, but it still won't play the discs.  They still show up as blank.

I found another site that suggested that the cdfs.sys was the problem.  Updated that too and no luck.  Another site said they had luck using the cdfs.sys file from Windows 2000 on their XP machine.  Tried that, no luck.

The article says Windows can't read a sparing table longer than 1 sector.  Is there anyway to test my disk to see if that is the problem?

The problem described in the article only applies DVD-RW and the UDF file system. 
I am pretty sure that video DVDs use an (older version of the) ISO file system. 

This should actually provide another way around the problem: if the same data is burned as a normal ISO data DVD, it should essentially be a video DVD. I just tried that, and it plays in Windows. I don't have a set top DVD player here to test it, but I'm pretty sure it's gonna work. 

I went to "File System" and made a custom setup. I selected ISO level 1, and unselected all the unnecessary exceptions and additions (I unchecked everything--except "Do not check inodes", which I don't know). Can someone with a set top player try if this works? 

Just an idea. 
--hasi.

[EDIT: I forgot to say that the video DVDs must not be multi-session, and I think they have to be finalized/closed (Disk-at-Once, "DAO") in order to work on set-top players.]

---

### Post by bedege on 2008-05-27
Hello

I have encountered the exact same problem as described here on Xubuntu 8.04. For some reason, I googled ubuntuforums, did not find this thread and started my own ([http://ubuntuforums.org/showthread.php?t=801400](http://ubuntuforums.org/showthread.php?t=801400)) with not much success so far.

The iso images I use are created by k9copy. They are readable by Totem on xubuntu, and also vlc and winrar on the Windows side. I burned one iso using k3b on a DVD+R: it reads ok with Totem and xubuntu can mount it. Windows does not recognize it. However, vlc can read it under windows.
OTOH, I burned a second iso file onto a DVD+R using nero 7 under windows, and windows can read it fine.
So, I feel like k3b is the culprit, not k9copy iso files.

Hasi, I've seen your notice on the k3b page on kde-apps.org. Did you get any feedback from the k3b community ?

Cheers

---

### Post by hasinasi on 2008-05-27
Hey bedege!
Unfortunately, I haven't received any feedback from kde-apps.org. 
To make sure I understand you correctly: you just tried to burn an iso image created by k9copy? So you did not use the "New Video DVD Project" function in k3b? Previously, I had thought that the latter would be responsible. 
--hasi

---

### Post by bedege on 2008-05-27
Hello Hasi

You're correct.
1. I created a 4.4 GB iso file using k9copy
2. I used k3b to burn it to a blank DVD+R disk using the iso image (I don't remember the exact name from the k3b welcome screen; this is the option in the low-right part of the screen)
3. k3b burns the DVD but I can't read it using windows

I haven't seen any option that could modify the behavior of k3b and could explain its misbehavior (joliet FS, finalization of DVD).

Can one fill a bug using launchpad on this subject, as it appears to be ubuntu (hardy only ?) specific ?

---

### Post by bedege on 2008-05-29
Hello

Just filled a bug on launchpad ([https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/235738](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/235738)).

Let's see what happens.

---

### Post by bedege on 2008-06-02
I made a second attempt using Gnome's Brasero, instead of k3b.

The result is identical: Video DVD is ok with Ubuntu, but unrecognized by Windows.

Does it mean that the issue is not with the GUI I use (k3b or Brasero) but more with the burning software itself (growisofs ?).

Any hint ?

---

### Post by aarb00 on 2008-06-03
I came to the same conclusion, that the problem is most likely growisofs.  I am using Windows tools under Wine to create my DVD-Video isos.  They burn perfectly under Ubuntu and are playable on Linux, Windows, Mac, and set top boxes.  

Even if you author a VIDEO_TS or ISO image under Linux, you should use a Windows tool to create, or rewrite the ISO image if you need it to work on Windows.

---

### Post by bedege on 2008-06-04
Hello

Some recent news about that thread: from other bugs that exist on Launchpad (see [233942]("https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942") and [219577]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/219577") for instance), it appears that it's more likely genisomimage 1.1.6 that is broken when creating Joliet-type iso files.

Looks like the iso image I made when I was using Gutsy are ok under Windows; now with Hardy and an updated genisoimage 1.1.6, Joliet compatibility is broken.

Solution might be to upgrade to genisoimage 1.1.7 or higher, and possibly recreate the iso images... Has anybody tried that with Hardy ?

Cheers

---

### Post by cjm5229 on 2008-06-07
Let's see, they will play in DVD players, VLC, and just about everything but Windows Media Player, and it's a Linux bug? Of course Microsoft couldn't make a product that has a bug. Maybe it has something to do with DRM. Since simply installing VLC and using it in Windows works why not just do that instead of trying to make WMP work?

---

### Post by ingrid_ozikem on 2008-06-08
Same problem here.. I tried with K3B and DVD95 (similar prog for GNOME) and both create DVDs that play in Ubuntu but cannot even browse in Windows.. shows up as a blank DVD that Media Player, Real player and various other players in Windows do not recognize as a video DVD. 

I've tried K3B's Video DVD project (using VIDEO_TS,AUDIO_TS directory structure), I've tried ISO images created by DVD95... all to no avail.

My suspicion is that these DVDs are not finalized and are multi-session. Windows shows these disks as DVD+R (or DVD-R) when you click on Properties -- while good old commercial DVDs show up as DVD+ROM. 

Is there a way to finalize a DVD using growisofs or mkisofs? (Actually K3B seems to use mkisofs, not growisofs...)  Is there a way to finalize a DVD on to which the movie has been written already?


(It is a linux problem if you can only create DVDs that 90% of DVD players on the planet cannot play.. let's live in the real world.)

---

### Post by bedege on 2008-06-10
> **bedege said:**
> Hello

Some recent news about that thread: from other bugs that exist on Launchpad (see [233942]("https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942") and [219577]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/219577") for instance), it appears that it's more likely genisomimage 1.1.6 that is broken when creating Joliet-type iso files.

Looks like the iso image I made when I was using Gutsy are ok under Windows; now with Hardy and an updated genisoimage 1.1.6, Joliet compatibility is broken.

Solution might be to upgrade to genisoimage 1.1.7 or higher, and possibly recreate the iso images... Has anybody tried that with Hardy ?

Cheers

Well, I installed genisoimage 1.1.7.1 from a Debian package (not from cdrkit sources) and it does not solve the issue... I read that I should install the whole cdrkit package from sources. Does anybody know the difference between cdrkit and genisoimage; what other cdrkit tools k9copy/k3b use that might be broken in the 1.1.6 release installed by Hardy ?

Cheers

---

### Post by jeffunk on 2008-06-11
I am suffering the same problem here.  I've tried a few things that I thought I would share.

As bedge and others have said, I have burned a video DVD with K3B and it plays fine in my stand alone DVD player, but Windows tells me the disc has an error and the disc appears blank when I go to look at the contents.  Interestingly, if I use VLC under Windows and tell it to play the disc, lo and behold the disc actually plays!  And this in spite of the fact that Windows has thrown an error on first reading the disc. 

I tried hasinasi's method of just creating the VIDEO_TS and AUDIO_TS directories manually and burning them to a Data DVD.  When i popped this into the Windows machine it played without a hitch.  Unfortunately, when I popped it into my set top DVD player, it won't read it.  I think it may be due to something to do with the file system, for instance 

"BACKUP FILES: The BUP file of a VTS is a duplicate of the IFO file for that set. This duplicate is used to avoid data being lost through scratches or errors on the DVD-Video disc. The BUP is usually physcially located on the outside rings of the DVD, far away from its original." from  [http://stream.uen.org/medsol/dvd/pages/dvd_format_filestructure.html]("http://stream.uen.org/medsol/dvd/pages/dvd_format_filestructure.html")
leads me to believe there is a little something special about the way video DVD's are put together.  Something that you wouldn't get if you burned the video information as a Data DVD. 

So, no answers here I'm afraid, but perhaps some fuel for discussion.

Just for the record here's the windows Error I see when trying to play one of my linux burned video DVD's
[IMG]http://jeffunk.yi.org/images/windowsError.jpg[/IMG]

---

### Post by jeffunk on 2008-06-11
ok, I have a solution that works for me.  Downgrade.  

Searching through the Debian bugs I came across this [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430558]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=430558")
which looked promising so I downgraded to genisoimage 1.1.2-1 

...and burned my disk and it works in windows, in my set top dvd player and in my laptop.  

This doesn't quite identify the problem, but it does help work around it.
Cheers

Link to current bug in Debian [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=482032](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=482032)

---

### Post by scorchedbysun on 2008-06-11
There is another solution: upgrade ;-)

I just downloaded the 1.1.8 release of cdrkit from [http://cdrkit.org/releases/](http://cdrkit.org/releases/) and compiled it. It installs into /usr/local and keeps the existing wodim etc. ver. 1.1.6 intact (I'm on Kubuntu 8.04). K3b saw the new versions of cdrkit programs and listed them as used by default.

Following this I successfully burned a DVD Video disc using K3b which is readable in Windows and everywhere else.

---

### Post by bedege on 2008-06-11
> **scorchedbysun said:**
> I just downloaded the 1.1.8 release of cdrkit from [http://cdrkit.org/releases/](http://cdrkit.org/releases/) and compiled it. It installs into /usr/local and keeps the existing wodim etc. ver. 1.1.6 intact (I'm on Kubuntu 8.04). K3b saw the new versions of cdrkit programs and listed them as used by default.

Interesting ! What did you start from to create your video DVD ? Was it an exsiting iso file, and MPEG/VOB files that k3b had to digest ?
Reason that I'm asking is that for me it's apparently genisoimage 1.1.6 that is broken, so k3b is not to blame when burning an iso file.
As I mentionned earlier, I upgraded from genisoimage 1.1.6 (Shipped w/ Hardy) to 1.1.7.1 (using a Debian package) but it did not fix the issue. Have to try 1.1.8 though, from an existing Debian package for instance, instead of from the sources.

Cheers

---

### Post by bedege on 2008-06-11
> **jeffunk said:**
> Link to current bug in Debian [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=482032](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=482032)
Apparently, that Debian bug also identifies genisoimage 1.1.7.1 as being buggy...Bummer!
So, two possible solutions could be:
- downgrade to 1.1.2, for which an Ubuntu package exist
- upgrade to 1.1.8, which is now available in Debian repositories.
I'll have to try one of these.

It's revigorating to see that others suffer from the same bug, even if it does not get much attention from the Ubuntu developpers... What is the trick to raise the importance of that bug ?

Cheers

---

### Post by scorchedbysun on 2008-06-11
> **bedege said:**
> Interesting ! What did you start from to create your video DVD ? Was it an exsiting iso file, and MPEG/VOB files that k3b had to digest ?
Reason that I'm asking is that for me it's apparently genisoimage 1.1.6 that is broken, so k3b is not to blame when burning an iso file.
As I mentionned earlier, I upgraded from genisoimage 1.1.6 (Shipped w/ Hardy) to 1.1.7.1 (using a Debian package) but it did not fix the issue. Have to try 1.1.8 though, from an existing Debian package for instance, instead of from the sources.

Cheers

I just answered your post in another thread about this topic on this forum.

I haven't tried burning a pre-made ISO image, only a VIDEO_TS folder prepared by DeVeDE. On genisoimage, wodim, etc at 1.1.6 (what ships with Kubuntu 8.04) the DVDs would come out unreadable in Windows - exactly like described by others. But after compiling cdrkit 1.1.8 the DVD became immediately readable in Windows as well.

I would really recommend that you compile and install cdrkit from sources. It's very fast and doesn't break your exisiting versions of the apps. Also, it seems very probable to me that it's not just genisoimage, but the other apps in the cdrkit suite which need to be at newer versions.

---

### Post by bedege on 2008-06-11
> **scorchedbysun said:**
> I haven't tried burning a pre-made ISO image, only a VIDEO_TS folder prepared by DeVeDE. On genisoimage, wodim, etc at 1.1.6 (what ships with Kubuntu 8.04) the DVDs would come out unreadable in Windows - exactly like described by others. But after compiling cdrkit 1.1.8 the DVD became immediately readable in Windows as well.

My issue at the moment is creating an iso file (w/ k9copy/genisoimage) then burning it to a video DVD+R (w/ k3b/growisofs).

My gut feeling from bug reports floating around is that genisoimage is the culprit. Any idea what other cdrkit programs could be necessary/faulty in my case ?
Is there a way in k9copy to choose the backend software used, as you describe for k3b ?

---

### Post by scorchedbysun on 2008-06-11
> **bedege said:**
> My issue at the moment is creating an iso file (w/ k9copy/genisoimage) then burning it to a video DVD+R (w/ k3b/growisofs).

My gut feeling from bug reports floating around is that genisoimage is the culprit. Any idea what other cdrkit programs could be necessary/faulty in my case ?
Is there a way in k9copy to choose the backend software used, as you describe for k3b ?

I haven't really used k9copy, so I can't help you there.

BUT:
I have just burned an .iso prepared with DeVeDe BEFORE I installed cdrkit 1.1.8 (it also uses genisoimage, it seems) and it also doesn't show any files (on a Mac, now Windows, but the result is the same). So, recording in K3b using newer cdrkit version will not help an .iso made on cdrkit 1.1.6.

Later, I'll try making a new iso image with DeVeDe on the new cdrkit version and I'll tell you what happens.

---

### Post by bedege on 2008-06-11
> **scorchedbysun said:**
> I have just burned an .iso prepared with DeVeDe BEFORE I installed cdrkit 1.1.8 (it also uses genisoimage, it seems) and it also doesn't show any files (on a Mac, now Windows, but the result is the same). So, recording in K3b using newer cdrkit version will not help an .iso made on cdrkit 1.1.6.

So it leans toward using a different genisoimage (either 1.1.2 or 1.1.8, _not 1.1.6 or 1.1.7.1_)
Has one been able to differentiate between *good* and *bad* iso files using isoinfo or similar tool ?

---

### Post by bedege on 2008-06-11
Well, I just tried both solutions
- 1st, upgraded to genisoimage 1.1.8 (from the Debian package; too lasy to actually compile from sources... or more frankly not enough time!). Similar result as earlier: burned DVD unreadable by Windows. This is independent on the burning software/platform I use. The 1.1.8 created iso file is buggy, when I use k3b to burn it, or when I use nero under windows. 
- 2nd, downgraded to genisoimage 1.1.2 from the Ubuntu repositories. Here, that **WORKS !**. Iso file generated with 1.1.2 gives correct AUDIO_TS and VIEDO_TS directories under windows, whatever soft I use to burn the DVD (k3b/linux or nero/windows). Then I can read the video with vlc under windows.

Huggs to jeffunk who proposed that workaround ! :guitar:

---

### Post by jeffunk on 2008-06-12
Glad that worked for you bedge.:)

As suggested early I went through my working iso and my not working iso with isoinfo to see if I could discover what the problem was.  

The ONLY difference I found was this 
in the Video DVD that works in Windows,Linux and Set Top DVD player
(genisoimage 1.1.2-1)
Application id: MKISOFS ISO 9660/HFS FILESYSTEM BUILDER & CDRECORD
CD-R/DVD CREATOR (C) 1993 E.YOUNGDALE (C) 1997 J.PEARSON/J.SCHILLING

in the Video DVD that doesn't work in Windows  (genisoimage 1.1.8-1)
Application id: GENISOIMAGE ISO 9660/HFS FILESYSTEM CREATOR (C) 1993
E.YOUNGDALE (C) 1997-2006 J.PEARSON/J.SCHILLING (C) 2006-2007 CDRKIT
TEAM

Which I reckon for people who are creating the package is probably pretty well known.  SO, I'm stuck as to what the difference is, and why 1.1.8 (1.1.6 or 1.1.7) doesn't work for me.

---

### Post by bedege on 2008-06-17
I just made a quick test last night. I was still puzzled why iso I created with gutsy were ok, when those created under hardy yelled DVDs that are unreadable under Windows.

So, I installed genisoimage 1.1.6-1ubuntu3 from gutsy: it works fine and creates iso that burn to DVD fine and are readable under Windows.

Thus, the bug lies somewhere in the patches between 1.1.6-1ubuntu3 and 1.1.6-1ubuntu6, that very release being part of Hardy.

That narrows down the search.

---

### Post by alegallo on 2008-06-18
I'm having exactly the same problem with Hardy.
I made a nice dvd using a pre-acquired .avi dv file, avidemux and ManDVD, which plays OK on stand-alone players and under Linux, but is reported as full but of nothing under Win XP. 

Tonight (CET) I'll give your solution a try and let you all know.

Regards

---

### Post by alegallo on 2008-06-19
I checked your solution and worked perfectly for me. \\:D/

I had to enable the gutsy repositories, downgrade genisoimage to the gutsy version (locking it, otherwise the system would re-install the newest version) AND to install mkisofs.

Apparently there is a bug in the "part" of genisoimage that provides the mkisofs functions in hardy, whereas the older versions of genisoimage did not substitute mkisofs, which still works.

Thanks everybody for your help

---

### Post by bedege on 2008-06-20
> **alegallo said:**
> I had to enable the gutsy repositories, downgrade genisoimage to the gutsy version (locking it, otherwise the system would re-install the newest version) AND to install mkisofs.

Apparently there is a bug in the "part" of genisoimage that provides the mkisofs functions in hardy, whereas the older versions of genisoimage did not substitute mkisofs, which still works.

Glad it worked out for you too. I don't quite understand why you have to install mkisofs. I thought genisoimage is actually a substitute to mkisofs that Debian and Ubuntu propose, because of issues with the license mkisofs uses. To me those two softs do basically the same job, and I see no reason to install the second if the first one works fine. I don't think mkisofs is installed here on my machine, and apparently it is not part of any Ubuntu repository.

Bye.

---

### Post by Jonie on 2008-06-28
I compiled cdrkit 1.1.8 from source and it works for me (Hardy 64-bit). Disc is now readable in Vista (didn't check in XP, but I suppose the result would be the same). Compilation process is easy, if it complains go to Synaptic, satisfy dependencies, make clean and start again. You can also try to burn "data dvd" i.e. ISO 9660 with VIDEO_TS folder - most set top boxes will accept it, if it shows file manager even after few reloads then it does not.

---

### Post by cjv8888 on 2008-06-29
I also had the same problem with Ubuntu Hardy when DVD burned with k3b cannot be played in Windows.  I downloaded the cdrkit 1.1.8 but do not know how to compile it.  Finally I found the genisoimage 1.1.2-1 back in Ubuntu Feisty's repositories and now the DVDs are playable everywhere.

BTW, how do you compile those files from the cdrkit 1.1.8.tar.gz ?

---

### Post by Jonie on 2008-06-30
In addition to to the compiler packages, the following are required to make genisoimage:

cmake
libcap-bin
libcap-dev
libbz2-dev

The resulting binaries will be put in /usr/local/bin, so there is no conflict between the freshly made build and the standard ubuntu package. It seems if you browse thru the changelog of genisoimage, that there were no changes relating to udf since quite a while. The Debian patches in Ubuntu package don't seem to change a thing about udf either. That's strange, because lfs support that is introduced after 1.1.2 which has apparently broken udf readability in Windows isn't metioned in changelog to be fixed. It must have been silently fixed... or just by chance ;)

---

### Post by bedege on 2008-07-01
> **Jonie said:**
> It seems if you browse thru the changelog of genisoimage, that there were no changes relating to udf since quite a while. The Debian patches in Ubuntu package don't seem to change a thing about udf either. That's strange, because lfs support that is introduced after 1.1.2 which has apparently broken udf readability in Windows isn't metioned in changelog to be fixed. It must have been silently fixed... or just by chance ;)
Yes, that really puzzles me.
- you reported that a freshly built genisoimage 1.1.8 from sources works properly. You're not the only one to report such behavior.
- OTOH, when I tested 1.1.8 from a Debian built package, it is broken.
As you mention, there must be a bug lying somewhere in the Debian/Ubuntu patches that breaks genisoimage since 1.1.6-1ubuntu6.

My 2 cents

---

### Post by alegallo on 2008-07-01
> **bedege said:**
> Glad it worked out for you too. I don't quite understand why you have to install mkisofs. I thought genisoimage is actually a substitute to mkisofs that Debian and Ubuntu propose, because of issues with the license mkisofs uses. To me those two softs do basically the same job, and I see no reason to install the second if the first one works fine. I don't think mkisofs is installed here on my machine, and apparently it is not part of any Ubuntu repository.

Bye.

Well, I don't understand it either, but when I uninstalled genisoimage 1.1.8-1ubuntu6 I had to uninstall also DVDstyler and ManDVD. 
Reinstalling the first forced me to get mkisofs as a dependency.
I noticed also that mkisofs was a dependency of the latter too.

As far as I remember, I did not get this request at the first installation.

I guessed it was because the 1ubuntu6 version of genisoimage (from hardy repositories) already contains the functions from mkisofs, whereas the 1ubuntu3 version (from gutsy) does not.

I got the idea because I saw that mkisofs is no more present in the hardy repos, whereas it can still be found in gutsy's :confused:

Honestly I'm quite new in linux, so I don't have a deep enough knowledge of the system to worry too much; it works, anyway! ;)

---

### Post by Jonie on 2008-07-01
More strange compatibility issues are yet to discover...

This time it's about ISO9660 mp3 cds. ISO with Joliet as usual. Recognized properly in Windows. However, when I put one of those created in Hardy into an old Mediatek 1389 based DVD player, it "thinks" a while and shows that it's got... Video CD 1.1 with PBC :lolflag:

Of course, software in this old crap is not perfect and is no subject to worry for Ubuntu users by any means, but there is only one kind of discs like this - created by famous genisoimage 1.1.6 (roasted the Ubuntu way).

---

### Post by sgt.bilko on 2008-07-15
I downloaded genisoimage 9:1.1.6-1ubuntu3 (amd64 binary) from ubuntu gutsy. Prevented from installing as the newer version was detected on my system. Is there a way of overiding this or am i doing the wrong thing installing this package. I'm a bit intimidated of working with sources.

---

### Post by bedege on 2008-07-29
Hello

To force your system to accept downgrading genisoimage, you should:
1. Download genisoimage deb package for gutsy [here]("http://packages.ubuntu.com/gutsy/genisoimage") onto your harddisk
2. Use dpkg using the command line in a terminal
Go into the directory where you have downloaded the deb file and type
[FONT="Courier New"]sudo dpkg --force-downgrade -i genisoimage_1.1.6-1ubuntu3_i386.deb[/FONT]
The system will ask for your password, and that's all !

Hope this helps

---

### Post by sgt.bilko on 2008-07-29
Thanks bedege - very clear instructions.

Before I downgrade genisoimage - is there a way to reverse this action so that if one day the bug is fixed my system can be upgraded to the latest version of the package?

---

### Post by bedege on 2008-07-31
> **sgt.bilko said:**
> Before I downgrade genisoimage - is there a way to reverse this action so that if one day the bug is fixed my system can be upgraded to the latest version of the package?
Hello

Actually, if you simply downgrade gensisoimage as detailled above, the first thing your system will do afterwards is propose you upgrading to the hardy release of genisoimage ! And it will do so each time it connects to the internet and check that you do not have the latest official hardy release of genisoimage. So yes, it is very easy to upgrade again. But maybe not very friendly...

OTOH, once you'll have the right gutsy release of genisoimage you'll pant not to be annoyed by your system that will propose over and over to upgrade to the buggy genisoimage. To stop the annoyance, launch synaptic with root access, locate genisoimage in the list of installed packages and select its line, go to the Package menu (or equivalent, my system is in French !), and select "Block this version". Now the system will know that you're happy with this old release of genisoimage and won't propose to upgrade again.

Good luck !

---

### Post by fridaythe14th on 2008-08-01
You got it almost right there. It's called "Lock this version".

Thanks!

---

### Post by sgt.bilko on 2008-08-04
I downgraded genisoimage and locked the version as instructed. System no longer tries to download the newer (bad) version. Can now write DVD's correctly - excellent. 

All sorted. Many thanks guys.

---

### Post by ingrid_ozikem on 2008-08-05
Yup.. struggled with this for months.. fixed it now!

Got the old geniso 1.1.6 thing .. works now. Earlier, I had the problem described above on TWO different computers with 3 different installations of Hardy Heron..

---

### Post by wandalalakers on 2008-09-08
I just discovered this bug today.  I burned a dvd-rw and tried two windows machines and there was no file listing.  I'm glad it's not k3b causing this problem because I'm addicted to this software.  Thx for this fix guys!

---

### Post by wandalalakers on 2008-09-10
I just tried this on a Dell optiplex 745 with a dvd rom / cdrw and I still can't view dvds burning using kb3 and geniso 1.1.6.  I'm using a dvd-rw so maybe that's part of the problem.  Anyone able to view dvds burned using a dvd-rw with windows?

---

### Post by wandalalakers on 2008-09-11
Well, on my system when I install geniso 1.1.2 and reboot, I'm unable to run kb3 and k9copy.  I'm going to try 1.1.6 from gutsy again.  I'll try to be patient until a better fix is found.

---

### Post by wandalalakers on 2008-09-11
This is another problem that I have discovered.
[COLOR="Red"]When installing genisoimage_1.1.6-1ubuntu3_i386.deb it removes remastersys from my hard drive[/COLOR].  When I put remastersys back on using Adept Manager it puts genisoimage_1.1.6-1ubuntu6_i386.deb back on.  When I put genisoimage_1.1.6-1ubuntu3_i386.deb back on and I check to see if remastersys is installed, I try to run it and it never opens.

When I run remastersys from the teriminal instead of the program menu I see one of the following errors:
"The following packages have unmet dependencies:
  remastersys: Depends: mkisofs"

So, remastersys is one program that's affected when downgrading genisoimage_1.1.6-1ubuntu6_i386.deb to genisoimage_1.1.6-1ubuntu3_i386.deb.

---

### Post by wandalalakers on 2008-09-11
I was able to view  a dvd using windows now with genisoimage_1.1.6-1ubuntu3_i386.deb but now remastersys doesn't work.

---

### Post by wandalalakers on 2008-09-11
please delete

---

### Post by bedege on 2008-09-12
genisoimage is a debian/ubuntu replacement for mkisofs.

As stated in my messages above
genisoimage_1.1.6-1ubuntu3_i386.deb from gutsy works fine, when genisoimage_1.1.6-1ubuntu6_i386.deb from hardy is broken.

However, it appears that your remastersys soft (where did you get the package from) requires mkisofs. The Ubuntu maintainers have added "Provides: mkisofs to binary package genisoimage" in 1.1.6-1ubuntu5 and above ([http://changelogs.ubuntu.com/changelogs/pool/main/c/cdrkit/cdrkit_1.1.6-1ubuntu6/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/c/cdrkit/cdrkit_1.1.6-1ubuntu6/changelog)), thus your system requires that release of genisoimage or above to satisfy the dependency for remastersys.

Maybe you can force your system to:
- stick to genisoimage_1.1.6-1ubuntu6_i386.deb using synaptic
- force the install of remastersys even if mkisofs/genisoimage_1.1.6-1ubuntu6 is not installed. I do not know remastersys, but maybe you can change the name of the binary to create iso files ?

Hope this helps

---

### Post by wandalalakers on 2008-09-12
Thx for the info Bedge.  I was just posting my info about remastersys in case someone was a user of the program like myself.

**[COLOR="Red"]Sorry for being a pest but I just assumed there were other users on the forum using 8.04 and remastersys.  I was just sharing the info that I found.[/COLOR]**

What is remastersys?

"Remastersys is a tool that I created for *buntu systems that will make a livecd from your installed partition.  The inspiration came from a tool called remasterme in PCLinuxOS which uses the Mandriva used mklivecd tool."

1 - make a distributable copy
and
2 - make a backup of your system

I forwarded my info to the creator of remastersys so that he and other users are aware of this problem.

[http://loscompanion.com/forums/index.php?topic=1672.0](http://loscompanion.com/forums/index.php?topic=1672.0)
I was just wondering if there was anyone on the forum using Kubuntu 8.04 and remastersys?
I read somewhere that some users tried genisosys 1.1.7 and 1.1.8 but still couldn't get dvds to work using windows.
If push comes to shove, I can just reinstall genisosys 1.1.6 (hardy) when I need to create an iso and reinstall genisosys 1.1.6 (gutsy) when I need to windows to read a dvd.
I could also just go back to gutsy.  I've been thinking about going back to gutsy but I guess I'll just wait for 8.10 to see if that fixes my remastersys problem.

---

### Post by kung fu buntu on 2008-10-05
Where can I download genisoimage sources? Including version 1.1.8


More info:
Apparently the [official cdrecord package site]("http://alioth.debian.org/projects/debburn") has a mailing list where [someone mentioned this problem]("http://lists.alioth.debian.org/pipermail/debburn-devel/2008-June/thread.html"), but no solution or interesting comments were given.

This problem was also submited in [debian bug tracking system]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=482032") and it seems that compiling genisoimage 1.1.8 from source solves this problem:
"Solution: I have to compile genisoimage 1.1.8 from source, since this bug, affects only the debian packet and not the software itself."

So... Where can I download genisoimage sources? Including version 1.1.8

EDIT: I must have been blind...
[http://cdrkit.org/releases/cdrkit-1.1.8.tar.gz](http://cdrkit.org/releases/cdrkit-1.1.8.tar.gz)
And remember you need:
cmake
libcap-bin
libcap-dev
libbz2-dev


I will try this latter and let you know if this fixed the error for me.


BTW, just google "genisoimage source" and the [first link]("http://www.nabble.com/-Bug-41285--NEW:-genisoimage-fails-to-produce-a-compatible-Video-DVD-images-td17686370.html") is a report on the problem.

---

### Post by wandalalakers on 2008-10-05
[http://packages.ubuntu.com/search?keywords=genisoimage](http://packages.ubuntu.com/search?keywords=genisoimage)

64 bit
[http://mirrors.kernel.org/ubuntu/pool/main/c/cdrkit/genisoimage_1.1.8-1ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/c/cdrkit/genisoimage_1.1.8-1ubuntu1_amd64.deb)

32 bit
[http://mirrors.kernel.org/ubuntu/pool/main/c/cdrkit/genisoimage_1.1.8-1ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/c/cdrkit/genisoimage_1.1.8-1ubuntu1_i386.deb)

---

### Post by kung fu buntu on 2008-10-05
Problem fixed!

I have compiled genisomage (and the rest of the cdrkit) and overwritten only the genisoimage files installed in my system.
[http://cdrkit.org/releases/cdrkit-1.1.8.tar.gz](http://cdrkit.org/releases/cdrkit-1.1.8.tar.gz)


Now... if only I knew what makes k3b crash everytime when it starts to verify the burnt disk :-/

---

