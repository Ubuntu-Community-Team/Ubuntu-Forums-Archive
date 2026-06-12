---
title: "Tuner Card Recomendation"
date: 2009-11-29
forum: Mythbuntu
---

### Post by zosoMythbuntu on 2009-11-29
I have been using a Hauppauge 250.  It has worked well, but I accidentally broke the cable input by pushing my pc to far back. :(

Now I need to get a card to replace this one.  I was wondering about a card that would be capable of HD recording.  I'm having a hard time figuring out if there is one that will be right for me.  I would like one that will be pretty easy to set up.  From what I've read, they can be a hassle.  Are there any HD Cable Tuner cards that work well and are easily integrated into Mythtv?  Or should I just go with another Hauppauge 250 or a 500?

I believe my computer would play HD TV back just fine.
2.9 GHz CPU
NVidia 9300 GPU
1.5 TB Green HD

---

### Post by brianafischer on 2009-11-29
I would suggest the HDHomeRun.  It is an ethernet-based device that can be used with any computer on your ethernet network, regardless of software (Myth, SageTV, ..) or Operating System.

[LIST]
[*]It is a dual tuner for QAM/ATSC which means cable or OTA.
[*]It is on sale at NewEgg for $129 w/free
[/LIST]shipping until tomorrow:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815327005]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815327005")

---

### Post by am4c130d on 2009-11-29
For me - SilconDust HDHomerun is the best solution, it works a treat.  I have one and use both ports on cable.  I get around 89 channels from cable, and if it wasn't for one or two channels, I'd be canceling my satellite service.  They're also on sale this weekend due to Black Friday if you are in the US.

Main features why I bought HDHR
1. Excellent support in MythTV (they beta trialed the HW with Myth)
2. Connects via Ethernet, not PCI/PCI-E - no driver issues whatsoever.
3. Full digital capture, so digital signal is recorded straight to HDD (no A/D phase unlike 250 - which I also have).
4. Two tuners - can do OTA and cable.

There are a few tricks to making it work excellently - assuming your signal level is fine.  First, scte65scan scans Comcast in band channel map to capture all SD signals on the cable - run this to get the majority of channels.  Then scan for channels in myth itself to get the HD channels.  Lastly, map the channel names to XMLID from Schedules Direct - and arguably move the HD channels to the cable operators channel assignment if you care.

HD is stunning, as you would expect, but SD is pretty good - not least is that most TV stations spend a bit more on the A/D conversion than I, at least, could afford - and that is what is recorded directly.

Now, if only Hauppauge or SilconDust would just make an analog/HD A/D version - then I can dump the PCI cards completely.

There are some negatives (well one that I have come across, and its rare).  Occasionally the HDHR comes up before the DHCP server is running, and that creates a race condition where mythtv-backend starts while the HDHR is waiting for the timeout for the DHCP server - this means Myth misses the HDHR tuners, and a quick restart of Myth is needed.  I've definitely seen it a few times, but its still very rare.

Your HW is more than enough, I use XVMC on a nVidia 6200 and 3800x2 Athlon and HD is very smooth (OSD crack aside).  I believe with vdpau, you should be cruising...

---

### Post by zosoMythbuntu on 2009-11-29
Thanks to both of you for the information.

I have just a couple of questions for am4c130d.

> HD is stunning, as you would expect, but SD is pretty good - not least is that most TV stations spend a bit more on the A/D conversion than I, at least, could afford - and that is what is recorded directly.

Now, if only Hauppauge or SilconDust would just make an analog/HD A/D version - then I can dump the PCI cards completely.I don't understand what you mean by this.  Would I still need a PCI card, like a Hauppauge 250, for some reason?

Does anyone have experience with this and Wowway?  Do I have any reason to worry that I wouldn't be able to pick up digital cable channels depending on the cable provider?

---

### Post by zosoMythbuntu on 2009-11-29
I have one more question.  Would I only get local HD Channels like CBS and Fox or would I get other channels like ESPNHD and DiscoveryHD?  I don't know what is encrypted and what is not.

---

### Post by mitchell2345 on 2009-11-29
> **zosoMythbuntu said:**
> I have one more question.  Would I only get local HD Channels like CBS and Fox or would I get other channels like ESPNHD and DiscoveryHD?  I don't know what is encrypted and what is not.

What you get verys greatly.  Go look at the lineup server.  Its normally extremely accurate.
[http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us)

To make sure you understand this tuner right:
1. Records digital signal only. 
2. Can be OTA antenna or QAM that is NOT encrypted. 
3. Your PVR 250 is analog only.  Just like an older tv it receives channels 1-99 only on cable.  

You may find that you will need a PVR/analog card as well to pick up the SD channels that you cant get digitally or HD channels that are encrypted.  You can find PVR-150 cards (exact same thing as your current card).  Check out fleebay for some cheap cards/deals.

Another route would be the HD-PVR.  This is a much newer tuner that takes component HD in from your STB.  Slightly more complex as you need some way to change channels on your stb.  Could be via firewire or IR blaster.

~Mitchell

---

### Post by am4c130d on 2009-12-06
Mitchell has some sound advice, check out Silcondust's website...

None of the channels are encrypted.  Its basically basic cable channels but the local HD channels (PBS, CBS, NBC etc.) are in both HD and SD - and the HDHR can capture both HD and digital SD (I should have been more clear).  I use a PVR-250 to capture encrypted channels from my satellite receiver via the s-video input (haven't gone HD there yet).  

The comment about the TV stations doing the A/D conversion is that the HDHR simply grabs the MPEG-TS stream and streams it to your mythbackend, which duly writes it to the HDD - no analog between the TV station and your HDD, and if you have DVI/HDMI to a plasma or LCD etc., then no analog until the screen itself.  With an STB and a PVR-250 like card, you obviously add an analog stage between your cable box/satellite STB and myth - which just leads to loss in quality - and trying to work out what recording rate, what image size etc...

The other comment of mine you highlighted was my wishlist.  I'd like a device with the capture capabilities of the PVR-250, or the HD-PVR, but going from analog inputs to Ethernet, not to PCI.  It completely removes all driver issues (like the race condition between my bt-878 card for CCTV and the PVR-250 grabbing /dev/video0 -  easy enough to fix, but easier if I didn't have to) - I just really like the concept of the HDHR, and would happily move all video capture to that method.  Actually, I really want my satellite box to stream over Ethernet to myth - thus eliminating another analog step...

Once you play with the HDHR, I think you'll see what I mean - it really is a great idea.

---

### Post by blackoper on 2009-12-06
you could pickup a soddering iron and repair the card you have if you really don't want to buy something. I've fixed those cable connectors on tvs before and it only takes a few min. You could probably take it by a tv repair shop and they could do it cheaper than you buying a new card

---

