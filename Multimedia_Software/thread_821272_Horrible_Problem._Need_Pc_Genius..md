---
title: "Horrible Problem. Need Pc Genius."
date: 2008-06-07
forum: Multimedia Software
---

### Post by LoadedBum on 2008-06-07
I had Windows Vista on my PC originally. I partitioned the hard drive, and installed Linux. I then got on Vista and deleted the partition, to make it say Unallocated Space. Then I went to the Extender thing in Vista and it made the C drive combine with the Unallocated Space to recreate one big hard drive. I then tried to restart my PC, and it won't do anything except come up with an error that says something like GRUB NOT FOUND or something like that. I think it has something to do with the dual booter. I need help, fast. I'm using the Linux CD to boot from, and using the try it out feature.

---

### Post by MaindotC on 2008-06-07
I'm assuming you don't want Linux on your machine anymore.  Boot from the Vista CD, open a command prompt and type "fixmbr".  This puts Vista in control of the master boot record and allows you to boot into Vista.

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/722827.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/722827.html)

---

### Post by MaindotC on 2008-06-07
Loaded - I got your PM.  Please keep it in the forum so others can view the process for a solution.

If you don't have a Vista DVD, do you have a floppy drive and if so, do you know how to make a windows bootable floppy?  This will enable you to run the fixmbr command when you boot from the floppy.

---

### Post by LoadedBum on 2008-06-07
I do not have a floppy drive.

I'm using a laptop.

Another alternative I'm thinking about, is to just turn to Linux altogether. I like Linux, but I don't know how to use it well. I need to learn how to install things, and use the Terminals, etc.

---

### Post by MaindotC on 2008-06-07
That sort of information typically isn't implanted in your head overnight - it takes a while to get used to the operating system and how to do what you need to do.  If you don't need the Vista image anymore, then by all means come join us.  Otherwise, download any number of bootable cd's such as the Ultimate Boot CD and burn it to a CD or DVD.  I'm assuming you have burning capabilities, right?

---

### Post by LoadedBum on 2008-06-07
Yeah, but I'll have to do it on a different PC. Also, I'm using Vista. Does that effect anything for the Ultimate Boot CD?

---

### Post by HunterThomson on 2008-06-07
You can also download Super Grub and burn it to a live CD and install it that will boot you into vista without needing the vista CD. Check out there web site for more info. 
If you ask me you are way better off staying with Ubuntu. I was really strange for me when I first started it but it took me like a week or two before I knew how to do everything I needed to do. It really doesn't take that long. I think you should give it a shot:)

---

### Post by MaindotC on 2008-06-07
> I know I'm probably getting on your nerves for asking so many questions. I apologize for the inconvenience, and thank you so much for helping me out so far.

I think I want to stick to Linux, but I need some advice and knowledge about somethings.

Is it possible to do everything with Windows that I can with Linux? I mean stuff like put stuff on my iPod, take files off of my cell phone with Windows Mobile, etc.? I know Wine helps for some of these things, but I don't know about some.

STOP PM'ING ME FOR THE LAST TIME.  Put all of your questions and comments here so if I'm afk someone else can jump in and help you.  I'm going to bed - I'll add what I can later.

---

### Post by HunterThomson on 2008-06-07
You told me in the PM that now when you start the installer it dosn't have the option to resize the window$ partition anymore?

---

### Post by beanhead on 2008-06-07
Is there a thread with just vista related problems? Has any one taken pictures of a vista box burning? Has anyone made a movie or slide show of mad vista users? Thanks :guitar:

---

### Post by cjm5229 on 2008-06-07
> **beanhead said:**
> Is there a thread with just vista related problems? Has any one taken pictures of a vista box burning? Has anyone made a movie or slide show of mad vista users? Thanks :guitar:
Vista Problems have a real simple solution, Ubuntu. Check Youtube for the video.

Loadedbum, System>Administration>Partition Editor, On the live CD, use the partition editor first to set up your Partitions, You can just shrink your Vista Partition, then install Ubuntu to the free partition.That will give you back Grub so that you will be able to boot into Vista as needed untill you learn to use Ubuntu. Once you get used to how things are done in Ubuntu, you'll find Windows is the one that does things the hard way.

---

### Post by MaindotC on 2008-06-07
There are a lot of problems with Vista  and other O/S's shrinking its partition.  I recommend you find the Vista CD and fixmbr as I stated previously.  But then again I avoid all this crap by just using Ubuntu for my base installation and I run anything else in a virtualbox.  Enough of this "dual boot" crap.

---

### Post by gitano on 2008-06-25
this guy is obviously in need of some help.
maybe its just me, but why not just wipe the drive and start again?
you can get gparted as a live cd off of distrowatch.com
it is a must have tool. use it to reformat your hard drive.
start clean. install whatever os you want but something brought you here in the first place-
you are in the ubuntu forums- go crazy and install 8.04
and no- there is really nothing that you cant do with linux.
if you are into gaming, then well dual boot with windows, or do a virtual machine like the man suggested.
i keep a box running xp pro (no need to comment) only because i like my 24 bit sound. anyway i digress.
just wipe the bad boy clean and start again, dude. relax,
its easy. no genius needed.
good luck

---

### Post by Victormd on 2008-06-25
I don't know if this was solved or not. If not, download the supergrub CD and reinstall grub. This will not install ubuntu or anything like that, grub is only a boot manager and can be used with windows alone. Now you'll be able to boot to windows again... :)

---

