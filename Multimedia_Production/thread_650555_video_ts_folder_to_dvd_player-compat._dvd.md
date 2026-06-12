---
title: "video_ts folder to dvd player-compat. dvd"
date: 2007-12-26
forum: Multimedia Production
---

### Post by kefurd06 on 2007-12-26
i have a VIDEO_TS folder, which is a rip of one of my movies. only problem is, when i burn that folder to a dvd (using the cd/dvd creator that comes wiht ubuntu, utilizes nautilus interface), i get no movie in my dvd players. works on my computer, but not on the standard dvd players. i read somewhere that i may have to add the AUDIO_TS folder to make it work. is this all i need to do? i'd like to find out exactly what i need to do so i don't make another coaster. thanks.

---

### Post by rgb1701 on 2007-12-27
Try K3B using the DVD Video project

Just add your VIDEo_TS folder and burn.

Install K3B via Synaptic.

---

### Post by yabbies on 2007-12-27
make sure your dvd player is dvd-r(w)/dvd+r(w) compatible or to whatever media you are using.

---

### Post by mellowd on 2007-12-27
```
mkisofs -dvd-video -o dvd.iso /vob_folder 
```

That will create an ISO image which you can then burn. that iso image will be in the correct format

---

### Post by kefurd06 on 2007-12-27
> **rgb1701 said:**
> Try K3B using the DVD Video project

Just add your VIDEo_TS folder and burn.

Install K3B via Synaptic.

tried this and it worked like a charm. tnx to everyone for the input!

---

### Post by rgb1701 on 2007-12-29
> **mellowd said:**
> ```
mkisofs -dvd-video -o dvd.iso /vob_folder 
```

That will create an ISO image which you can then burn. that iso image will be in the correct format

While we appreciate your contribution to the forum, command line responses are what scare off Linux newcomers or XP/VIsta refugees ;)

At this point in time, I think most  tasks an average non-tech user/consumer would do in XP/Vista have a GUI/graphical tool and/or method in Linuxland, particularly with the major "human rated" distros like Ubuntu, Mint, PCLinuxOS, Zenwalk, etc.

While you and I are comforatble with term windows and commandlines, Windows refugees aren't, so I tend to find graphical ways to do things (that wouldn't require a registry edit in Windows ;) )

---

### Post by mellowd on 2007-12-29
> **rgb1701 said:**
> While we appreciate your contribution to the forum, command line responses are what scare off Linux newcomers or XP/VIsta refugees ;)

At this point in time, I think most  tasks an average non-tech user/consumer would do in XP/Vista have a GUI/graphical tool and/or method in Linuxland, particularly with the major "human rated" distros like Ubuntu, Mint, PCLinuxOS, Zenwalk, etc.

While you and I are comforatble with term windows and commandlines, Windows refugees aren't, so I tend to find graphical ways to do things (that wouldn't require a registry edit in Windows ;) )

But now the user knows 2 ways to do it ;)

---

### Post by kefurd06 on 2007-12-30
i appreciate the command liney version of the solution too, and i think plenty of other people who see this thread will. in the last few months since my conversion to linux i've learned that there are two ways to do most everything in linux: the gui way, and the command line way. i think it's great that both are posted here on ubuntuform.org.

---

### Post by disturbed1 on 2007-12-30
> **mellowd said:**
> ```
mkisofs -dvd-video -o dvd.iso /vob_folder 
```That will create an ISO image which you can then burn. that iso image will be in the correct format

I knew the CLI option, but I thanked you anyways for it.

It was extremely rude of the poster to down rate you for posting a CLI option, which is the correct and most compliant way to do what the OP wanted. If people understood the hacks that went into using K3B and bug ridden growisofs/CDRKit/Wodim/genisoimage, it would never be offered as an option.

---

### Post by rgb1701 on 2007-12-31
> **disturbed1 said:**
> I knew the CLI option, but I thanked you anyways for it.

It was extremely rude of the poster to down rate you for posting a CLI option, which is the correct and most compliant way to do what the OP wanted. If people understood the hacks that went into using K3B and bug ridden growisofs/CDRKit/Wodim/genisoimage, it would never be offered as an option.

If you are referring to my friendly jibe, no rudeness was intended.

However, I think as the number of Windows refugees appear on Linux distro forums like this, we need to be tolerant of their brainwashed Win-centric ways.  I am a very tech-oriented user, and catch myself often in WIn-centric user-interface memes, which I am trying to free myself from.

Also, the FOSS community needs to recognize that some GUI operations are now very fundamental, basic parts of using a computer- any operational computer.  Burning a DVD disc for set top playback is one of those basics, or a basic data file DVD backup.

I just tried to burn a 4.3GB file using K3B and Brasero in Mint 4.0 Xfce edition (Ubuntu derivative).

Neither would allow me to burn a >4GB file, whether I chose UDF format or not!

I ended up installing Windows IMGBurn under Wine- here is a guide.

[http://forum.imgburn.com/index.php?showtopic=5317](http://forum.imgburn.com/index.php?showtopic=5317)

While it appears to basically work as it does under Windows, the burn speed varies wildly, as does K3B, per a lot of other folks:

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/31709](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/31709)

You can burn VIDEO_TS folders to make a set top DVD in IMGBurn, IMO, the best burning software out there.  I have burned over a thousand discs, video and data, with IMGburn over the past several years.

I may have to stay in XP for burning until Ubuntu/Mint disc burning gets stabilized and has performance parity with XP.

---

### Post by disturbed1 on 2007-12-31
> **rgb1701 said:**
> 
I just tried to burn a 4.3GB file using K3B and Brasero in Mint 4.0 Xfce edition (Ubuntu derivative).

Neither would allow me to burn a >4GB file, whether I chose UDF format or not!.

That's the exact bug/hack I was talking about with K3B and murdered growisofs ;) 

 growisofs --version
* growisofs by <appro@fy.chalmers.se>, version 7.0.1,
  front-ending to genisoimage: genisoimage 1.1.6 (Linux) <-- dirty hack :roll:

Make sure you have the real packages and not the bug ridden cdrkit hacks from **_J&#65533;rg Schilling_**'s 2004 package.

 mkisofs --version
mkisofs 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1993-1997 Eric Youngdale (C) 1997-2007 **_J&#65533;rg Schilling_**

 cdrecord --version
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 **_J&#65533;rg Schilling_**


K3B explicitly calls growisofs, which in turn calls genisoimage, which is the bug ridden dirty hack of mkisofs from 2004. 

**IF** you where to do -
*mkisofs -V "VOLUME_NAME" -o /path/to/image.iso -dvd-video /path/of/folders/*
Then the image file would have been built correctly, implying you bothered to install the real mkisofs ;)

Also, the newest version of K3B (1.0.4) *finally* fixes this issue, by checking if you have the real versions of mkisofs installed.

Considering you're willing to use non Open-Source (IMGburn which an A+++++ app) NeroLinux uses it's own burning API based off the Nero 6.6 windows code.


Command line exists in Windows as well. If a person has ever attempted to contact ISP support, after restarting the PC and Modem, that's the next step -
run - cmd - ipconfig :D

If we teach users to be stupid and uninformed, we end up with a slew of mindless clicking imbeciles. GUIs are nice if they correctly do the task at hand.

---

### Post by rgb1701 on 2007-12-31
> **disturbed1 said:**
> That's the exact bug/hack I was talking about with K3B and murdered growisofs ;) 

...

If we teach users to be stupid and uninformed, we end up with a slew of mindless clicking imbeciles. GUIs are nice if they correctly do the task at hand.

I agree 100% re: ignorant/uninformed users, which MS is guilty of creating and encouraging the past decade or so.

We can fix ignorance.  As for stupidity, well...;)

I hope the fixed K3B hits the Synaptic repositories soon.  Is there a straightforward way to updae to the fixed K3B now?

Even if that addresses the >4GB file issue, what about the wildly varying burn rate issue?

On XP, when you set a burn speed, like 4x or 8x, Nero or IMGburn does the complete burn at exactly that speed, depending on the feed rate of your source files.  If the source files can't be fed that fast, the buffer underrun protection kicks in only when that happens.  In practice, you set your burn rate to a speed your network and/or source drives can feed without buffer underruns.

I have burned hundreds of DVD's at 4x on this P3 1GHz box on XP.  On Mint (Ubuntu 7.10 derivative), I set the burn speed to 4x, but the write rate varies wildly, from the same USB hard drive source files I burn under Xp on the same machine.

I may have to try Linux Nero if K3B or some other burning app can't do 4x burns at a consistent rate.

---

### Post by disturbed1 on 2007-12-31
I'm not sure about the varied write rates. I burn from internal PATA/SATA drives (all JFS) to PATA DVD/CD. I use command line - cdrdao writing in raw mode for karaoke cds, then at first Braero and now NeroLinux. I found NeroLinux to be worth the $25(USD), but only with version 3. Version 2.x wasn't that good. There is a free demo available and a support forum [HERE](http://club.cdfreaks.com/f104/)

The newest K3B is in Gusty backports and Hardy repos. Ubuntu (*thankfully*) has the real versions of mkisofs and cdrecord available in synaptic. I haven't tried it, but the K3B change log states that this problem was fixed.
> 
k3b (1.0.4-1) unstable; urgency=low

  * New upstream release:
    - allow burning of files larger than 4 GB (closes: #444856) 

You can physically delete genisoimage and symlink mkisofs to genisoimage so that mkisofs is always called instead of genisoimage. The same can be done with wodim and cdrecord. Both wodim and genisoimage are just the 2004 versions of cdrecord and mkisofs with a couple of hacks. The use commands and even the help context is exactly the same. Use caution before you attempt the above. If something goes wrong just do a reinstall of wodim, genisoimage, DVD+rw-tools, then mkisofs and cdrecord if desired.

---

### Post by rgb1701 on 2008-01-01
I tried NeroLinux 3.x last night- WOW!

Appears to burn as well as it does under XP writing files from the external USB2 hard drive.

I got rock solid 4x DVD data disk burns on several disks I tested last night, and I tried to make the buffers underrun- I started OpenOffice Writer then Spreadsheet, and launched other apps and operations to try to trip it up/ slow it down.  The Nero guys did their native Linux coding homework :D.  Makes the FOSS burner software look REALLY bad, especially re: CPU utilization and process sensitivity.  

When writing burner software/API's, you need to really know and understand your buffer stream and process priority P's an Q's, ensuring your burn process priority and buffers are NEVER disturbed by ANY OTHER PROCESS, short of turning off the power to the computer ;)

I would recommend trying NeroLinux 3.x to anyone serious about burning a lot of DVDs on Linux.

It's unfortunate there is no native IMGburn for Linux yet, but I suspect there will be a native IMGburn or IMGburn-quality freeware and/or FOSS app for linux before 2008 is over .  The Linux growth rates through 2008 will be too much for all the best XP developers to ignore  :D


I hope the closed/commercial software market for Linux really takes off, if NeroLinux is any indication.

---

### Post by disturbed1 on 2008-01-01
:guitar:

Glad you liked it.

The thing about Linux burning apps, they are all just GUI's to the same command line tools. cdrecord (cdrtools), cdrdao, and now some use the new kid on the block libburn. As stated above, the new wodim (cdrkit) (Ubuntu, Debian, and others) is actually an old version of cdrecord (cdrkit) because of CDDL licensing. The same as Sun and MPL (mozilla public license). In other words not upto DFSG standard :(

---

### Post by rgb1701 on 2008-01-01
> **disturbed1 said:**
> :guitar:

Glad you liked it.

The thing about Linux burning apps, they are all just GUI's to the same command line tools. cdrecord (cdrtools), cdrdao, and now some use the new kid on the block libburn. As stated above, the new wodim (cdrkit) (Ubuntu, Debian, and others) is actually an old version of cdrecord (cdrkit) because of CDDL licensing. The same as Sun and MPL (mozilla public license). In other words not upto DFSG standard :(

If freeware tools like IMGburn appear to burn so well, why can't the linux FOSS guys  (cdrkit/cdrecord/cdrdao/etc) write burner code as least as good as IMGBurn's?

While IMGburn is not FOSS, it is freeware, and I assume uses its own burn code, which appears as robust and rock-steady as Nero's.  IMO, IMGburn was a breakthrough in freeware burner apps on the Windows side.  Prior to IMGburn, most burner apps worth anything were shareware/nagware or commercial paid software.

Can any Linux burner front end use the new libburn?

I guess the Linux FOSS burning situation showcases the fickleness of FOSS licensing schemes, and highlights some of the disadvantages of the "Unix/Linux Way", where the same low level simple tools are called by higher level software in the chain, thus propagating the same problems across a lot of different front ends, which normal, nontechie users see as "different programs".  Just goes to show that sometimes a closed binary blob that does its own thing can often be a better option ;)

---

### Post by disturbed1 on 2008-01-01
> 
Can any Linux burner front end use the new libburn?Brasero can. It requires some gconfig edits though :( Google search brasero+libburn should get you started. I *_believe_* Nautilus uses libburn as well? Gtoaster as well, but I've never used it.

A few Windows programmers have no interest in writing Linux code. They say it works in Wine .... Good enough. If I where a programmer that attempted to make some money, Linux definitely would not be my choice platform. Not enough users, and of those users you have to think about how many are against closed source, and figure in the piracy factor. You're left with 5-10% of the Linux user base, of which Linux only accounts for ~20% of total PC users (and that's being nice :D) 10% of 20% isn't much of an incentive. My numbers are probably off, but you get the picture.

Burning in Linux requires much more system knowledge than it would in Windows. Nero is the only GUI that supports setting the book type on DVDs, but requires root access in order to do so. You can always use DVD+rw-tools to do the same from the command line. I always thought it strange that no GUI was ever made to do this.

---

### Post by ~LoKe on 2008-01-02
I'll have to use that sometime.  I love command line utilities.  I've been going the long route all this time.

---

### Post by Pygi on 2008-01-06
> **disturbed1 said:**
> Brasero can. It requires some gconfig edits though :( Google search brasero+libburn should get you started. I *_believe_* Nautilus uses libburn as well? Gtoaster as well, but I've never used it.

.


Neither NCB (Nautilus-cd-burner) nor Gtoaster use any of the available libburnia libraries. From Brasero 0.7.0 things are getting better wrt libburnia libs, since that backend is/will be a plugin, and won't need gconf modifications.


Also, you can use cdrskin, which is a CLI frontend to libburn compatible with cdrecord command-line arguments.

KR,
M.

---

### Post by lewac on 2008-01-07
first I apologize for straying just a tad off topic here but believe a point requires a bit of emphasis. take for example a copy of a file from /home/anybody to anywhere that requires root  privilege. how to do that using gooey without actually signing in as root? so isn't it a LOT safer (and perhaps even easier) using sudo via CLI?

yes it certainly is a lot more convenient to use the gooey if something you wanna do happens to be supported. thus if you know "it" use "it". whatever that "it" tool is that you currently know best. however if one does not know one simply needs to ask. look. this is a gigantic learning curve even for so-called power user tech savvy from within the windows world. however for those migrating from unix (mostly techies many from the "old" days) the snow isn't falling nearly as badly.

thus I personally appreciate the CLI references but for those that don't simply keep learning and wait awhile. live and learn and b4 one knows it we'll wonder why and how we EVER tolerated all those window crashes! 

finally please remember too that we are all benefiting from the work of thousands (most of which are being paid very little or nothing) to bring the gpl to the world:)

---

