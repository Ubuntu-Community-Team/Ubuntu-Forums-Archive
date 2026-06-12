---
title: "Can not do channel scanning"
date: 2009-11-13
forum: Mythbuntu
---

### Post by thusgaard on 2009-11-13
Hi. 

I just blanked my 9.04 install, and installed 9.10. 
In 9.04 my tuner worked. But now I cant tune a single channel. 

My tuner is a ASUS TV-FM 7134 (SAA7134) Using the analog V4L.

In "input connections", the "scan for channels button" is grayed out. 

In the "Channel Editor" the cursor jumps over the "Channel Scan" button.

Can anyone please help or do I need to install Mythbuntu 9.04 again.

Kind regards J;-)

---

### Post by steevc on 2009-11-13
I've got the same problem. I had Mythtv working fine on 9.04. I upgraded and it was still working, but I've messed it up now. It somehow lost the setting for the video card, so I set that again, but needed to set up channels again. I've tried using the Video Sources screen with an XML source, but after telling it what channels I wanted (several times) the screen went blue and didn't save anything. I have been trying to get it to use the EPG data from the signal, but can't scan channels.

I have to say that the MythTV configuration screens have not improved much in the years I've been using it. Many of the options are very cryptic. There should be wizards or something to allow for a quick start. I appreciate that the developers have limited resources, but many people will give up when confronted by complicated setup that stops them from being able to do anything with the application.

---

### Post by thusgaard on 2009-11-14
> **steevc said:**
> I have to say that the MythTV configuration screens have not improved much in the years I've been using it. Many of the options are very cryptic. There should be wizards or something to allow for a quick start. I appreciate that the developers have limited resources, but many people will give up when confronted by complicated setup that stops them from being able to do anything with the application.

Much of the settings in a TV are predefined. If you buy a TV in Denmark it will support PAL BG. So a country selection that defaulted a lot of settings could be nice. Ofcause there should also be the option to modify if you have special requests. 

I think I'll be down grading tonight. Just too bad. 

J;-)

---

### Post by petedawg on 2009-11-24
I have the same thing with a Hauppauge WinTV-HVR 950Q on Ubuntu 9.10, 64 bit.  I tried Mythbutu and Ubuntu + MythTV with the same results.  Kaffeine works OK, not a problem once the codecs were installed.  This is with OTA reception of digital channels.

Myth picked up the tuner device OK and read in the SchedulesDirect info OK.  But when I get to 'Input Connections' the capture device is OK, V4L: /dev/video0..  Input is Television (OK).  I set the video source to the tuner and pressed the 'Fetch channels from listings source' button.

But after that the 'Scan for channels' button is inactive.  Starting channel has 'Please add channels to this source'.  There are no other selections for starting channel.

Any ideas how to scan for channels or get the list of channels in there?  All the hardware is OK.  This seems to be a common thread for Myth on 9.10.

---

### Post by Lido on 2009-12-02
Same here. Scan For Channels button is greyed out. I've deleted the cards a couple of times but no help there. Anyone?

---

### Post by nickrout on 2009-12-02
I understand this has been fixed, so update your mythtv (daily builds) and try again :)

---

### Post by Lido on 2009-12-05
Is it possible that the firmware is still required? I thought that the kernel somehow had support for the capture cards built in now. I've got a kworld 115.

---

### Post by Lido on 2009-12-05
> **nickrout said:**
> I understand this has been fixed, so update your mythtv (daily builds) and try again :)

How do I get the daily builds? AFAIK, I'm up to date on the standard installation.

---

### Post by nickrout on 2009-12-06
[http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

---

### Post by rwreed on 2009-12-06
I updated to the daily build .23 but still have the problem. The Scan for Channels button remains grey. I have deleted the capture device and recreated it, just to be sure but still no joy. I am using a hauppauge 250.

Randy

---

### Post by Lido on 2009-12-07
> **nickrout said:**
> [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

Thanks. I installed and ran it, selecting 0.22, but when I ran the update manager, it had a long list of myth upgrades in the window but it gave me the "partial upgrade" message and some files were unchecked. Any idea how to get it to do a full update (the partial upgrade didn't fix the problem)?

---

### Post by nickrout on 2009-12-07
> **Lido said:**
> Thanks. I installed and ran it, selecting 0.22, but when I ran the update manager, it had a long list of myth upgrades in the window but it gave me the "partial upgrade" message and some files were unchecked. Any idea how to get it to do a full update (the partial upgrade didn't fix the problem)?

you need to give us the EXACT messages!

---

### Post by iamlindoro on 2009-12-07
Analog channel scanning is disabled in .22.  It has not yet been rewritten in the context of the new channel scanner.

---

### Post by Lido on 2009-12-08
> **nickrout said:**
> you need to give us the EXACT messages!

It's working now. My mistake.

The message is the standard error that Update Manager gives you if there's some reason it can't update all the files that are out of date. It seemed to update everything ok today, but I still could't do a channel scan after the update (no error message, "scan for channels" is just grayed out in MythTV Backend Setup).

What I was doing wrong was not paying attention to the card type when I set up the card. As soon as I saw "Kworld" on the screen, I thought I was done, but that was the setup for the analog ports on the card. When you set it up for DVB, it doesn't say "Kworld" as the card type so that threw me. Anyway, once I selected DVB, I can do a channel scan. Not sure if my homemade antenna will pick anything up, but at least things seem to be working as far as MythTV goes.

iamlindoro, thanks for the reply. That's what got me to look at the set up again.

---

### Post by OffAxis on 2009-12-11
bug report:
[http://svn.mythtv.org/trac/ticket/6530](http://svn.mythtv.org/trac/ticket/6530)

---

### Post by phreakshew on 2009-12-15
Same problem here. Was using TVTime in 9.04 but now with 9.10 TVTime is not working so I am trying Myth TV but can't scan for channels. Grrrr. 

At least Zapping seems to work, although I'm having an issue getting with it not going to fullscreen mode.

BTW, the page for that bug report just keeps loading.......

---

### Post by diskmaster23 on 2009-12-30
Has there been a fix yet? I noticed this thread is still open.

---

### Post by rajanski on 2012-03-01
Just follwo the procedure exacly as described in [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

The first place where you have to scan for channels to avoid the greyed out button is "Input Connections"

---

### Post by ijumpship on 2012-03-03
Oops you are answering a three old post.Stay of the Whites.I heard it help creativity but like me I only used it When the code gets Ruff..Rough

---

