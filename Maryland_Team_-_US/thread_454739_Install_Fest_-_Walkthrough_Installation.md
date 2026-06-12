---
title: "Install Fest - Walkthrough Installation?"
date: 2007-05-25
forum: Maryland Team - US
---

### Post by aboutblank on 2007-05-25
Should we show people that come in how to install Ubuntu or just how to use it? 

If we want to show the people how to install it, we should use the typical install CD, but if we don't, we could use the alternate CD and since that doesn't load a GUI, speed things up considerably. I've never done this before, so I don't know how many people we will get to come in. I would like to get the people in and at least through the installation quickly, because they might have somewhere to be, etc. 

If we decide that we should show the user how to install, we cannot use local servers for loading the installation image (also known as PXE). Of course, that is assuming I know what I'm talking about :p We'd be limited to CD's. PXE off a server would be about twice as fast (bandwidth wise) than a 52x CD-rom drive. I have gigabit hardware to use, so if PCs comes in w/ gigabit, we could do that *quite* quickly.

Is the installation too complicated for people? Most people learn how to use Windows before they learn how to install it. Of course, this is different.

You can probably tell I am leaning towards *not* showing the users the installation process for the above reasons.

****************************************************************
Edit - I wish I could recreate this poll. I'd add a third option - Have the user choose. Who could argue with that? CD graphical installation wouldn't be terrible, and for those that don't want to see it, we can install it a bit faster with the network or alternate install.

---

### Post by DARKGuy on 2007-05-25
I don't quite get the idea, but if you show off the desktop CD, it would be a great opportunity to tell the people they can have an entire OS to use while they wait for it to install. The steps aren't very complicated for a common user (except the partitioning if you have more than one drive or want to share windows/linux on the same drive or same computer =/ ) and I personally find a GUI more attractive and user-friendly than a console (don't get me wrong, the alternate CD has a -very- nice console GUI, but for the common, Windows-used user, it would be like WTF!).

In short, if you want to do an impression, get the Typical CD (takes about 30 min - 1 hour in a 933Mhz/256Mb RAM computer), but if you want to do it quick and just show the OS itself, use the alternate CD.

Of course, this is only my opinion... you're free to do what you wish, or what other users here suggest you, since they have more experience than me for sure XD.

I had the chance to participate in a Linux Install Fest that was held here in Venezuela in some international forum thingy around 2005-2006, and for the Knoppix/Debian installs they were using the console installer (with a server for grabbing the already-downloaded latest packages so people would start off with an updated OS). However, the guy who installed Debian (Sarge 3.4, lol) on my computer was kind enough to teach me how to install stuff, what to do when I connected my comp at home and such, so good communication is also the key to make it victorious ^^.

Besides, if users watch how Ubuntu is installed in their computer, they can do it again whenever they wish (something I had happen to myself when I wanted to delete debian.. I didn't know how to reinstall it after =( ).

---

### Post by aboutblank on 2007-05-28
If we don't show the user the installation, we should use [OEM installation]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview") so they can set the language, keyboard, and username stuff themselves.

---

### Post by DARKGuy on 2007-05-28
I've never installed Ubuntu that way, but looking at the link it sounds alright to me :)

---

### Post by aboutblank on 2007-05-28
I wish I could re-make this poll. I'd add a third option - Have the user choose. If they wanted to see how to install it, we'd show them the graphical. If not we could do network or alternate.

---

### Post by ChuckFrain on 2007-05-29
My vote is to let the user perform the install. It allows them to see what is happening and make choices themselves. They can understand the process a little better. They may not care and simply 'do as they're told' but I feel it's important to at least try to teach.

---

### Post by phr0ze on 2007-05-30
I also vote to have the user install with our help. We ensure the user gets hands on, and it's only 7 easy steps even if you want to dual boot. The only time I noticed anything different is on a computer with 3 drives. Then step 4 (partitioning) was more difficult.

---

### Post by aboutblank on 2007-05-30
It looks like most people are leaning towards having the user do the installation and walking them through it. This is just fine for me, majority rules! The installation is pretty easy and shows another strong point of Ubuntu.

I'll still be putting together at least 1 image based server so when SOMEONE walks in with a computer w/o a cd-rom drive, we can accomodate him/her. We'll leave the poll up for a few more weeks, just to keep the debate open.

---

### Post by phr0ze on 2007-05-30
I'm more concerned about the person without a network card.

Many people who sign up for cable or DSL use the USB connection on the broadband modem.

---

### Post by DARKGuy on 2007-05-30
Agreed. What would happen in that case?

---

### Post by dhruva023 on 2007-05-30
hey, when is this festival,

i am using ubuntu since 2 months.  i love it.

i live in baltimore too.

i might participate, if i get time.

---

### Post by floke on 2007-05-30
There should be a graphical layout showing all the steps in the installation process.
Both Pardus and PCLOS do this and its brilliant - not perfect, but puts a lot of mind to rest about what will happen and what the user will see when they press the install button.

A must have feature IMO.

---

### Post by aboutblank on 2007-05-30
Okay, this has clearly been decided! CD based install it is! John (phr0ze) has a cd duplicator and can make many copies of the image. I will be bringing a single server for the people without a cd-rom drive to load an image off of.

As far as the people without a NIC... well if they have a cd rom drive then they are fine. I have never used a usb based modem, so I don't know about support for it.

Does anyone have a USB to Ethernet adapter we could use for the random people that don't have a cd-rom drive OR NIC? I don't really want to get into opening computers.

Chuck if you wish/can you may close the poll.

---

### Post by phr0ze on 2007-05-30
> **aboutblank said:**
> 
Does anyone have a USB to Ethernet adapter we could use for the random people that don't have a cd-rom drive OR NIC? I don't really want to get into opening computers.


I'm going to buy one, but I need to be sure the one I get doesn't require drivers which aren't included with the install CD. I know some USB Wifi adapters work out of the box, but all the compatibility charts are unclear. It must also be a brand that can be found locally.

---

