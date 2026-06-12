---
title: "Brasero and Lucid"
date: 2010-05-02
forum: Multimedia Software
---

### Post by oboedad55 on 2010-05-02
Hi, I'm running Lucid RC with all updates and Brasero 2.30.0. I can't do a disk copy with this program. It gives me an error that not all libraries are installed. It first gave an error that cdda2wav was not installed but that is not true and now I get this general error. Any ideas? I'm installing K3B as we speak but I prefer to keep a straight Gnome installation.

Thanks!

---

### Post by RavanH on 2010-05-03
same here :(

and we are not alone:

[http://ubuntuforums.org/showthread.php?t=1471350&highlight=brasero](http://ubuntuforums.org/showthread.php?t=1471350&highlight=brasero)

[http://ubuntuforums.org/showthread.php?t=1468585&highlight=brasero](http://ubuntuforums.org/showthread.php?t=1468585&highlight=brasero)

[http://ubuntuforums.org/showthread.php?p=9229840](http://ubuntuforums.org/showthread.php?p=9229840)

---

### Post by oboedad55 on 2010-05-03
> **RavanH said:**
> same here :(

and we are not alone:

[http://ubuntuforums.org/showthread.php?t=1471350&highlight=brasero](http://ubuntuforums.org/showthread.php?t=1471350&highlight=brasero)

[http://ubuntuforums.org/showthread.php?t=1468585&highlight=brasero](http://ubuntuforums.org/showthread.php?t=1468585&highlight=brasero)

[http://ubuntuforums.org/showthread.php?p=9229840](http://ubuntuforums.org/showthread.php?p=9229840)

Wow, OK. Thanks for the post. I finally just bought Nero for $17, which isn't bad. I just hate to pay for software because the Ubuntu defaults won't work. Except for this problem, I'm very impressed with Lucid.

---

### Post by schily on 2010-05-16
Please note that Ubuntu does not come with
cdda2wav, so Brasero is correct with telling
you that cdda2wav is missing.

Ubuntu unfortunately installs a broken and dead fork 
instead of the maintained original software.

If you like to get the working original software,
you may either fetch a recent original source from

[ftp://ftp.berlios.de/pub/cdrecord/alpha](ftp://ftp.berlios.de/pub/cdrecord/alpha)

[http://cdrecord.berlios.de/](http://cdrecord.berlios.de/)

or get one of the various precompiled versions of the
original software that are provided from helpful
people. There is no need to use non-free closed source
software and cdda2wav is even one of the best available
audio extractors.

---

### Post by oboedad55 on 2010-05-16
> **schily said:**
> Please note that Ubuntu does not come with
cdda2wav, so Brasero is correct with telling
you that cdda2wav is missing.

Ubuntu unfortunately installs a broken and dead fork 
instead of the maintained original software.

If you like to get the working original software,
you may either fetch a recent original source from

[ftp://ftp.berlios.de/pub/cdrecord/alpha](ftp://ftp.berlios.de/pub/cdrecord/alpha)

[http://cdrecord.berlios.de/](http://cdrecord.berlios.de/)

or get one of the various precompiled versions of the
original software that are provided from helpful
people. There is no need to use non-free closed source
software and cdda2wav is even one of the best available
audio extractors.

Thanks for the post. I installed cdda2wav using this ppa, [https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)
and although Brasero now runs with no complaint, it makes a corrupt copy of an audio CD. Any ideas?

---

### Post by Chrisco66 on 2010-05-19
Can you direct me to the helpful people with the packages?  I cant find a .deb for any version of Brasero.  I am not getting any complaints about missing software though.  I dont think the cdda2wav thing is causing my problem, but I would like to go back to a version of Brasero that works.  Brasero is so simple and until recently, very reliable too..

---

### Post by andrew.46 on 2010-05-22
Hi oboedad,

> **oboedad55 said:**
> I installed cdda2wav using this ppa, [https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)
and although Brasero now runs with no complaint, it makes a corrupt copy of an audio CD. Any ideas?

If you have Jörg Schilling's cdda2wav *and* cdrecord you may be interested to know that you can easily duplicate audio cds from the commandline using these 2 tools. The syntax comes from the man pages for cdrecord btw. First identify your drive:

```
 cdda2wav -scanbus
```

and use that dev number in the following way to identify album and tracks and rip the cd to wav, I use 1,0,0 which identifies my drive, don't forget to use your own details here:

```
cdda2wav dev=1,0,0 -vall cddb=0 -B -Owav
```

and then burn using cdrecord, again substituting your own dev details:

```
cdrecord dev=1,0,0 -v -dao -useinfo -text *.wav
```

It could not be any easier! I would welcome any comments from 'schily' here whom I am sure knows this software better than me :).

Andrew

---

### Post by cosmolee on 2010-05-22
I tried the brandonsnider repository also but it did not fix the problem.  According to the instructions it provides something called CDRTools, but there wasn't any such thing in the Synaptic after I added the repository.  

It DID have cdda2wav, which I installed. But that was a bust.  As w/ oboedad55's experience, for me Brasero stopped complaining about the lack of cdda2wav, but it still wouldn't make a copy of an audio disc.  

Why does Ubuntu ever disappoint?  A task so basic should just work.  It is because of experiences like this that make it hard for one to believe that Linux will ever be a viable replacement for the Windows on the desktop.  It should be like the Easy Button, not an aggravating test of one's patience in order to accomplish something basic.

---

### Post by cosmolee on 2010-05-23
Thanks for the workaround Andrew.  It worked perfectly.  Still no excuse for Brasero not working out of the box though...

---

### Post by mc4man on 2010-05-23
I'd say if you want to use a gui that actually works with any reliability then try k3b. Brasero always seems to be in some inconsistent state, maybe not for all, but certainly for some. 

(I myself never use other than to test - sometimes it works, other times it doesn't. Atm it refuses to copy an audio cd though it will do a video dvd. I consider it to be a remedial burning app at best.

*You should try what Andrew has posted *- works quite well, I'd say in less time than it takes to post this you could rip and burn an audio cd - 3 - 5 min.'s tops.

If so, I'd suggest a few things - 

run the scanbus command with sudo

Create a folder, cd to it, then run the cdda2wav and cdrecord commands (make sure cdrecord is installed, it's part of what was termed "CDRTools"

This way all your cdda2wav files will be an a folder instead of loose in  home dir.

Read the man for cdda2wav for other  possible options

Possibly replace genisoimage with mkisofs - I not sure there, myself use ImgBurn for most burning tasks

( If you wish to take copying cd's to an extreme then learn and use EAC running thru wine - works quite well.

==================================
I generally just rip and encode rather than copy, atm using cdda2wav in abcde-nero, though I'm not too sure it's any better than using cdparanoia.

( though occasionally like to listen to cd as I rip and encode which cdda2wav does quite well.

---

### Post by andrew.46 on 2010-05-23
Hi cosmolee,

> **cosmolee said:**
> Thanks for the workaround Andrew.  It worked perfectly. 

Well, thanks would be better to go to Jörg as it is not only his software but an example drawn directly from his man pages :). If you are interested in trying cdrdao for copying audio cds as well there is a long-neglected guide on these forums:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

All the best,

Andrew

---

### Post by wkulecz on 2010-06-18
Never had an issue with CD/DVD burning on 6.06 or 8.04, but today with 10.04 copying a data disk failed! :(

Had to copy it using an old 8.04 system.

Brasero automagically called up KPackageKit to download something and after I authentacated it, the install completed but I get an unhelpful error message and the copy fails :(

Are these Brasero problems reported on Launchpad?  If not they will likely never be fixed :(

---

### Post by neu2buntu on 2010-08-16
icedax includes cdda2wav in lucid.

```
sudo apt-get install icedax
```

---

