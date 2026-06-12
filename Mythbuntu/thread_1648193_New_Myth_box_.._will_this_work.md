---
title: "New Myth box .. will this work?"
date: 2010-12-18
forum: Mythbuntu
---

### Post by oldsoundguy on 2010-12-18
Box is an HP cd7100 convertible tower.
Power supply is stock HP 380w.
CPU is P IV 3.2 hyperthreaded at 400 fsb
1 gb ram (expandable to 4gb if need be)
LiteOn Dual layer DVD/RW with LightScribe
LiteOn DVD/ROM
NVidia 9800 GT GYN 98TOC5121 with 512 and HDMI out PCIe video card (will be driving a Sony Bravia KDL 55HX 800 3D 55" LCD screen)
DiVico Fusion HDTV RT Gold (has IR receiver) capture card
SoundBlaster Live! 5.1 without the front end in/out panel for the audio .. will feed surround sound amp.
D-Link DWL G520 Wireless card to access my home network.

Later want to add a MIMO 9" USB screen to replace the keyboard and mouse and LCD work screen .. but that is LATER

Will all of the above work? and do I have to make any changes in the plan?

Thanks for any input.

---

### Post by thatguruguy on 2010-12-18
That cpu may have a hard time with rendering in high definition, but it seems like the rest of it would be fine.

---

### Post by PhilWig on 2010-12-18
A few initial thoughts (and prejudices), assuming you are using it for a combined frontend/backend:

1. CPU, PSU, graphics all fine.  Lower (cheaper?) graphics like NVidia 8400 would also be fine.

2.  Why 2 DVD devices?

3.  You may find 1GB a bit low and I'd suggest 2GB.  My 2GB was fine when I stressed it with 6 simultaneous recordings, 2 playback and log rotation 'housekeeping'.  Paging file is rarely used at all.

4.  I don't know your tuner card (or the signals you hope to capture) but you need to check carefully.  Ensure positive comments from other subscribers - don't be a pioneer!

5.  If you are using the system only as a PVR then the MIMO screen looks a bit sophisticated.   I use a Keysonic ACK-540RF wireless keyboard/mouse pad which works fine and was in use every time I used Myth until I got a working remote.  The keyboard is now only used for 'development' stuff.  If you can pop the keyboard and mouse out of the way ("Do we have to have all those wires!") then they should be fine too. 

6.  I'm sure that your TV will have a VGA input.  A cable as well as the HDMI cable will be very useful when you need to monitor bios and boot problems and until such time as you get HDMI working smoothly.

7.  Disk not mentioned - volume (and perhaps dissipation and low noise) will be more important than performance.  I use 500GB but recordings have settled at about 250Gb after 12 months so maybe I need to upgrade some time in the next 18 months.  A second drive (modest size about 40GB) may be useful for development without destroying your setup.

8.  If you want sound to both analogue and HDMI output then I'm sure that's possible but it's one I've not cracked yet.

9.  If you can connect to your network via ether you'll find it easier to set up (works first time!) and more reliable.  I've seen many comments about flakey wireless, especially with HD.  I'm actually using ether over mains power until such time as I can get cables run.

HTH
Phil

---

### Post by oldsoundguy on 2010-12-18
Phil .. some answers.

The DVD/ROM is actually a CD/RW..DVD/Rom that came with the box .. I wanted a DVD dual layer burner in there and I had a spare I had pulled from a box that died. The fact that it has LightScribe is just a bounus.

Have my eyebones on some memory right now on eBay .. so will pick up some more .. probably up the box as I can get 4-1gb sticks for under 80 bucks total shipped.

The tuner card is listed as working on the Myth pages.  

I have too many regular computers in this room to be having more keys/mice/monitors taking up room .. but the Mimo option is just that right now, an option .. to be considered at a later date as am dumping enough cash into this thing already!! LOL
I will be using a Logitech wireless kb/mouse initially.

drive is 1tb SATA

not sure if the big screen has a VGA input and not inclined to move that wall away from the wall to check right now. *now, IF I could just find the stinkin' manual!!  Will go looking. 

But, thanks for the suggestion .. at least that will eliminate the monitor.

And, I can hardwire to the net for setup .. I do that anyway all the time when I install boxes as it just WORKS BETTER that way .. then fire up the wireless card as part of the setup operations.

I tried doing this quite a while back on a much more light weight box, but got lost in setup terminology and what options I should install .. this time around it seems the Myth pages have better documentation.

---

### Post by Boppy3125 on 2010-12-21
I have a DVico Fusion Gold something or other.  I use it for recording some HD using QAM.  It works great.  I added a HDHomeRun to get up to three tuners when Chuck, House, and How I Met Your Mother all lined up in the same time-slot.  Anyway, the Fusion works great.  Mine is a hybrid card that claims NTSC capabilities, but without hardware MPEG it was useless for me.

So the question is, what source will you be doing?  Over the Air HD or cable HD using QAM should each work well.

---

### Post by oldsoundguy on 2010-12-21
> **Boppy3125 said:**
> So the question is, what source will you be doing?  Over the Air HD or cable HD using QAM should each work well.

It will be Comcast cable at first.

---

### Post by thatguruguy on 2010-12-21
As mentioned in another thread, you can go to the SiliconDust page [here]("http://www.silicondust.com/support/channels/"), and enter your zip code to see what's available in unencrypted, clear QAM from Comcast in your area.  When you first enter your zip code, it will take you to a page listing what's available via digital antenna.  On the very top of that page you'll see a drop-down menu labeled "Provider"; just choose Comcast Cable from that drop-down.

---

