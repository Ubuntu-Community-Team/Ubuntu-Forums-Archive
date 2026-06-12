---
title: "can't get all my comcast stations."
date: 2011-11-17
forum: Mythbuntu
---

### Post by rmjohnson144 on 2011-11-17
I just got my system working with Mythbuntu 11.10 and only get about a third of my comcast limited basic channels.

after I setup everything I go in and setup my Input connections to scan for channels.  In the frequency table I get a lot of options and none have worked very well.

broadcast gets nothing
cable high get most of the hd channels, but not all.
cable gets only a few hd as well.

not sure what else to try.

is there a way to just try them all at once?

under my capture card options, only the dvb found my card's tuner (Samsung S5H1411).

I have the Hauppauge HVR-2250 PCIe tuner card.

Thanks in advance
-=Mark=-

---

### Post by ian dobson on 2011-11-18
Hi,

Maybe try using w_scan to scan for your channels and create a channels.conf, which you can then import into mythtv.

Regards
Ian Dobson

---

### Post by cbanakis on 2011-11-18
You will only get unscrambled channels unless you have one of these
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815706001](http://www.newegg.com/Product/Product.aspx?Item=N82E16815706001)
Along with a cable card (Provided By Comcast)

Not sure if thats your problem though

---

### Post by LowSky on 2011-11-18
Ceton doesn't work on Linux. sadly if you want all your channels, you will need a cable box provided by your cable company.

People you need to read up on this stuff completely. I find too many people on here make decisions based only on half-read, skimmed, or ill-gotten knowledge.

The HVR-2250 is a great card. I love mine. But when i got it I knew it could only watch TV that was not protected, when I first got it I knew only the digital tuner worked in Linux at the time, I knew if I wanted to record premium channels like HBO or heck Comedy Central I needed something like a HD-PVR.

Cable companies only have to offer local stations unscrambled. Mostly the local affiliates for stations like NBC, CBS, ABC, and Fox. Sorry if you feel cheated but its the truth. You would have known this if you read up before building your own HTPC.

---

### Post by thatguruguy on 2011-11-18
The easy way to test this (if you have a digital-ready TV) is to hook the cable directly up to your TV.

Any channel you get with the TV should show up in MythTV, although it may take some tweaking to get it.  Channels that are scrambled on your TV will be scrambled on MythTV.

One solution is to set up an IR blaster on your MythTV box, which can send a signal to your cable box to change channels.  The downside is you won't be able to record multiple shows at once with this setup, nor can you watch one thing on your TV while recording something else.

---

### Post by rmjohnson144 on 2011-11-18
I have limited basic from comcast which doesn't need a box.  For some reason I only get about a dozen channels when I should be getting over 40. I at least should be getting 13 digital channels, plus all the local channels in digital as well, which should be no less than 18 digital channels total.

I also have over 20 SD channels, but not sure if I need the antenna mode for that?  I assumed all channels were digital with the new law.  the 18 above I'm talking about are from the digital package.

even in windows I don't get them all, but they are on 3 different programs, so each one may be working differently than the other.  I tried to use one program to search all channel types and ended up with over a 100 channels, but I was getting triplicate or more of channels.

anyway, do anyone know which freq. table I should be using?  or if there is a way to scan them all at once?

-=Mark=-

---

### Post by klc5555 on 2011-11-18
> **rmjohnson144 said:**
> I have limited basic from comcast which doesn't need a box.  For some reason I only get about a dozen channels when I should be getting over 40. I at least should be getting 13 digital channels, plus all the local channels in digital as well, which should be no less than 18 digital channels total.

I also have over 20 SD channels, but not sure if I need the antenna mode for that?  I assumed all channels were digital with the new law.  the 18 above I'm talking about are from the digital package.

even in windows I don't get them all, but they are on 3 different programs, so each one may be working differently than the other.  I tried to use one program to search all channel types and ended up with over a 100 channels, but I was getting triplicate or more of channels.

anyway, do anyone know which freq. table I should be using?  or if there is a way to scan them all at once?

-=Mark=-

The 2009 law cutting over to digital that June only applied to over-the-air broadcasting; the cable companies were left to their own schedules as to when they wished to implement the cutover from analog to digital and reclaim the frequencies. 

The process isn't complete with Comcast. They vary from town to town; even street to street. I just lost the analog version of one non-local PBS station as recently as a couple of weeks ago, over 2 years after the cutover started. The History Channel left analog only 10 months ago. So check the "basic" channel list for your street address  at comcast.com See which of these "basic" channels in the list lack the footnote that says: "Available in all digital format. Digital capable equipment required." These are still being piped in to you in analog.

Because it is still (barely) possible that in your area Comcast has not cut over all (or even most) of the analog channel set that  used to reside on channels 21-99 to digital. In this circustance, your "missing" channels would still to be found in analog with an analog scan.

With "basic" service, the locals (those which would be available otherwise in digital over the air) should be provided SD via clear QAM. Not necessarily HD. In Input Connections you should find these in a QAM256 (or possibly QAM64) scan starting around channel 30-something and then in a couple of clusters around 70-something to 80-something. Maybe one or two channels as high as around 118-120. So do a full scan (not high) for QAM 256, then QAM 64. You should start getting locks for encrypted digital channels by the 20s, if these frequencies have been reassigned to digital.

---

### Post by nickrout on 2011-11-18
> **LowSky said:**
> Ceton doesn't work on Linux. 


Yes it does.

---

### Post by cbanakis on 2011-11-18
> **LowSky said:**
> Ceton doesn't work on Linux. sadly if you want all your channels, you will need a cable box provided by your cable company.

People you need to read up on this stuff completely. I find too many people on here make decisions based only on half-read, skimmed, or ill-gotten knowledge.

The HVR-2250 is a great card. I love mine. But when i got it I knew it could only watch TV that was not protected, when I first got it I knew only the digital tuner worked in Linux at the time, I knew if I wanted to record premium channels like HBO or heck Comedy Central I needed something like a HD-PVR.

Cable companies only have to offer local stations unscrambled. Mostly the local affiliates for stations like NBC, CBS, ABC, and Fox. Sorry if you feel cheated but its the truth. You would have known this if you read up before building your own HTPC.

Um, Yes it does.

[http://cetoncorp.com/infinitv_support/linux-drivers/](http://cetoncorp.com/infinitv_support/linux-drivers/)

People you need to read up on this stuff completely. I find too many people on here make decisions based only on half-read, skimmed, or ill-gotten knowledge.

---

### Post by LowSky on 2011-11-20
The Ceton doesn't work in Linux because of DRM. You'll be lucky if maybe 15 of your channels can be recorded from. Sure it might have driver support. But it suffers from the same flaw as a direct firewire connection of my cable box. 

[http://www.gadgetwisdom.com/2010/08/16/some-cablecard-content-will-be-available-to-linux/](http://www.gadgetwisdom.com/2010/08/16/some-cablecard-content-will-be-available-to-linux/)

---

### Post by nickrout on 2011-11-20
> **LowSky said:**
> The Ceton doesn't work in Linux because of DRM. You'll be lucky if maybe 15 of your channels can be recorded from. Sure it might have driver support. But it suffers from the same flaw as a direct firewire connection of my cable box. 

It works, it does what it says on the box, but you are never going to get a device in the US that does not obey the DRM flags.

---

### Post by thatguruguy on 2011-11-21
While this thread certainly contains some interesting discussions about the switchover to digital cable, DRM, and hardware, it really doesn't get the OP any closer to solving his problem.

To the OP: I posted this earlier:
> **thatguruguy said:**
> The easy way to test this (if you have a  digital-ready TV) is to hook the cable directly up to your TV.

Any channel you get with the TV should show up in MythTV, although it  may take some tweaking to get it.  Channels that are scrambled on your  TV will be scrambled on MythTV.

You then wrote about how you don't get all the channels in Windows, either, but you never actually responded to whether you can get all of the channels you want by simply hooking your cable up directly to your TV.  For the purposes of this post, I'm going to assume that you can.

I use Insight Cable rather than Comcast, so YMMV.  However, I had the same problem you are experiencing with my Insight Cable set up, which is also boxless.  Despite all my efforts using the default tools provided by MythTV, I couldn't get all channels.  The following describes what I did to fix that problem.  The disadvantage of this procedure is that it is very tedious.  The advantage is it works.

First, we're going to install a couple packages.  Since Mythbuntu doesn't come with a default text editor, I use mousepad (the default text editor for Xubuntu).  You can select something else if you prefer, but you do want a text editor for this. The main thing is to install a package called "w-scan".
```
sudo apt-get install mousepad w-scan
```
NOTE: although the package name is "w-scan", it is run from the command line by using "w_scan".  For w_scan to work, you'll need to shut down the mythbackend, so that it releases control of your tuner card.  The easiest way to do this is to close all instances of mythfrontend that may be open, and then run the mythbackend setup, which is available by choosing "MythTV Backend Setup" from the System menu under Applications.  Do that now, before going to the next step.

w_scan will give a listing of all transports (i.e., the frequencies that the cable signals travel on).  To run it, type the following in a terminal:
```
w_scan -fa -c US -A 2 -X
```
... if you really want to know what all the command line arguments mean, feel free to type "man w_scan" in a terminal.

w_scan will take a while to run.  When it's finished, it will output several lines to the terminal, which look like this:
```
dumping lists (381 services)
service_id 1:57000000:QAM_256:2179:0:1
service_id 2:57000000:QAM_256:2184:0:2
service_id 3:57000000:QAM_256:2181:0:3
service_id 21:63000000:QAM_256:2302:0:21
service_id 22:63000000:QAM_256:2299:0:22
service_id 23:63000000:QAM_256:2296:0:23
service_id 1:69000000:QAM_256:2007:0:1
service_id 2:69000000:QAM_256:2009:0:2
service_id 3:69000000:QAM_256:2004:0:3

```
... and so forth.  You will also get the occasional entries that look like this:
```
WHAS HD:507000000:QAM_256:1984:0:1
AccuWea:507000000:QAM_256:2048:0:2

```
... those will be the HD versions of your local channels.

Just copy everything in the terminal from "dumping lists" to the end (by highlighting it all and clicking Ctrl+Shift+v) and paste it into mousepad or whatever text editor you're going to use.  (If you want, you can remove all the duplicated entries; for example, in the stuff posted above, you'd only need one entry for 57000000, one for 63000000, etc.  You don't really care about the service_ids.) That's your new listing of transports. Save it for future reference.

Now is where it gets tedious.  Since you still have mythbackend setup running, go into the Channel Editor and choose "Edit Transports".  Remove any of the ones that are there, because we're going to rebuild it all from scratch.

After you've removed all transports listed in MythTV, put in all the ones you've found using w_scan.  You'll need to do them one at a time. Make sure that each one is set as QAM-256 in the modulation part.

You should now be able to scan for channels in the MythTV backend, and get everything available.  If you really want, you can scan each transport individually.

HTH

---

### Post by jlp_engineer on 2011-12-19
Does this mean that the "analog" channel scanner works, or is only the digital side of the channel scanner working for MythTV?:confused:

---

