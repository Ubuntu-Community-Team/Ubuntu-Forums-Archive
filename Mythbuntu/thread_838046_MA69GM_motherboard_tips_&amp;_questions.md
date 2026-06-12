---
title: "MA69GM motherboard: tips &amp; questions"
date: 2008-06-23
forum: Mythbuntu
---

### Post by dsbw on 2008-06-23
I know Volksie and some others around here have this motherboard, but I think there may be many different experiences as far as installing it. As it is, I'm trying to figure out whether it's usable for my purposes.

Installation-wise, contrary to some earlier reports, it's actually pretty easy with 8.04 (64-bit). 

[LIST]
[*] First install 8.04.
[*] Download the latest drivers from ATI (all have worked so far).
[*] You may find that activating the restricted (ATI) drivers causes problems with X. 
[*] Installing the newer drivers seems to fix it, though you may have to reboot.
[*] IMPORTANT: If you're trying to hook up an analog source, either through the optional S-Video or Component output, you *must* not have anything plugged into the digital (VGA for sure, probably the DVI and HDMI as well).
[/LIST]
This last was a sticky point for me, as the ATI CCLE was wonky about detecting my TV hooked up via S-video (sometimes would, sometimes wouldn't, pretended to activate it, etc) and didn't see anything hooked up to the component at all.

Problems:

[LIST]
[*]No HDMI audio out. I've tried everything.
[*]I'm not getting good throughput via HDMI. I get noticable tearing playing a DVD.
[*]Component out is only giving my black & white: I really want to make the component out work.
[*]I get noise via the line-out (a hum); I've gotten this enough with different machines to make me wonder if it's my TV but I can hook up, say, a Nintendo and not hear it.
[*]Occasional horizontal banding. This doesn't concern me just yet because I discovered recently that it happened especially when the S-Video and Component are hooked to different TVs.
[*]No serial port! How the heck am I supposed to control my STB? USB IR?
[/LIST]

The last is the killer at the moment, second most important is getting color on the component (I need the S-Video for my Nintendo! :lolflag: ), and the digital throughput issue is irritating as I may move the machine from time to time. The audio hum is irritating but I haven't investigated throughly.

I was hoping we could gather some tips & solutions in a thread here, because it seems like this is a fairly popular board, but not a lot of collected info on it.

---

### Post by netslacker on 2008-06-23
I just finished a setup using a MA78G (ATX).  While not the same board I did struggle with many of the same issues you mentioned:

> No HDMI audio out. I've tried everything.
I believe this is rather tricky, but what I did was direct mythtv to output all audio via the card/device that correlated to the HDMI audio.  To do this, type "aplay -l" in a bash window and look for ATI HDMI Audio Device (something like that).  Note it's card number and device number (1,0 or 1,3 is what I've seen on other posts).  Then in Myth change the Audio Output Device to: ALSA:hw:1,0 (or whatever numbers correlate to yours) this is probably currently set at ALSA:default.  Worked for me right off and many others have it working this way.  However, apparently there is trouble with MP3's this way and other audio formats.  For digital TV in general this should work.  YMMV.

> I'm not getting good throughput via HDMI. I get noticable tearing playing a DVD.
Ah yes, ATI video tearing.  My mobo has the ATI HD3200 and digital tearing was my biggest issue to resolve.  After many hours I gave up and bought a 27.00 nvidia card (7200GS) and fixed my video in 5 minutes.  I had to give up the audio over hdmi, but that's a small price for clean video.  Here's my thread on this issue: [http://ubuntuforums.org/showthread.php?t=827232](http://ubuntuforums.org/showthread.php?t=827232)  Also, have you looked at recent ATI drivers? Catalyst 8.6 was just released. If you're using the drivers from the repository they are a few releases behind.  Try the latest from ati.amd.com.. who knows, maybe you'll get lucky.

> I get noise via the line-out (a hum); I've gotten this enough with different machines to make me wonder if it's my TV but I can hook up, say, a Nintendo and not hear it.
Check your cables/connections.  Low hum is almost always a bad connection or grounding issue.

> No serial port! How the heck am I supposed to control my STB? USB IR?
Lots of IR receivers have IR transmitters, like many of the MCE remotes.  Check newegg.  Also, you may want to see if there is a serial port header on your mobo.  Although mine does not have the external connector there is an internal COM1 header that you could use.  Easiest is the MCE remote tho.... (I also don't use/need this, but my MCE remote has transmitters and I've seen others use them).

---

### Post by dsbw on 2008-06-23
> **netslacker said:**
> I believe this is rather tricky, but what I did was ... 

Intriguing. Not sure I tried that. Heh.

> **netslacker said:**
> Ah yes, ATI video tearing.  My mobo has the ATI HD3200 and digital tearing was my biggest issue to resolve.  After many hours I gave up ... 

Ick. I haven't tested with the new driver. I figured it was a TV issue. I know VW is using this board, though; hard to believe he'd put up with tearing. 


> **netslacker said:**
> Check your cables/connections.  Low hum is almost always a bad connection or grounding issue.

The grounding issue... I've seen that come up before but don't really get how to fix it.


> **netslacker said:**
> Lots of IR receivers have IR transmitters, like many of the MCE remotes.  Check newegg.  Also, you may want to see if there is a serial port header on your mobo.  Although mine does not have the external connector there is an internal COM1 header that you could use.  Easiest is the MCE remote tho.... 

There is an internal one; I have no clue how I would use it without the external port to get to it.

I did get an MCE remote, but it came with a separate transmitter with an 1/8" jack--no idea what to do with that.

---

### Post by volkswagner on 2008-06-24
> **dsbw said:**
> Intriguing. Not sure I tried that. Heh.



Ick. I haven't tested with the new driver. I figured it was a TV issue. I know VW is using this board, though; hard to believe he'd put up with tearing. 

When I had DVD working, there was no tearing.  I lost DVD playback in Myth with .21 updates, or other update.  Sound issues mostly.  This machine never really went into full use.  Almost did.  I still use it as a backend for my hit or miss slave BE/FE.  




> **dsbw said:**
> There is an internal one; I have no clue how I would use it without the external port to get to it.

You can get a serial breakout bracket.  It takes up a pci slot opening.  I was not able to find on on Newegg.  I have seen them included with some MOBO's.  You can also try a USB to serial adapter if supported.


> **dsbw said:**
> I did get an MCE remote, but it came with a separate transmitter with an 1/8" jack--no idea what to do with that.
The IR transmitter/blaster attaches to the 1/8" port on the USB receiver.  The blaster will need to be adhered to the component you want to control (close to the receiver on the STB, not to block it from your normal remote).  It can get ugly.

My SA3250HD set top box has an IR port 1/8".  I wonder if you have the same.  My 15yr old Kenwood receiver has these ports to daisy chain compatible components, using one master RC.  I wonder if the same type of male to male 1/8" cable can be used.  Provided you have the IR jack.  I use the firewire port to change the channels, so no IR needed here.

Back to the thread title.  I know most Linux Gurus cringe at ATI based boards.  I researched for weeks before purchasing this board.  It has it all.  At the time and in the same price range the only Nvidia board had no firewire port, another had no optical out.

I am willing to participate in any way possible.  I have several unsolved issues.  Check my threads.  It seems for me the board worked better in stock 7.10amd 64.  I did not try 8.04 as I have seen issues with pulse on this board.  I also want to use my unopened plextor convertX, which also has had thread started on 8.04.

Where do we start to get this awesome board pleasing all?

---

