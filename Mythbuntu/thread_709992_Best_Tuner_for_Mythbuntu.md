---
title: "Best Tuner for Mythbuntu?"
date: 2008-02-28
forum: Mythbuntu
---

### Post by Lutiana on 2008-02-28
Okay guys, I have my rig setup and working. Right now it is using a Pinnacle 800i tv tuner, and I sorry to say this card sucks for this application, the sound is horrible and the image is terrible.

So here is my question. What is the best TV Tunder card to use that will give good performance and a decent picture. Preferably one that can do  ATSC aswell (so I don't need to replace it in February next year).

Also, what is the best remote to use. Right now I am using a Windows MCE (version 2) remote and I am not wild about how the buttons work.

---

### Post by tedder on 2008-02-28
'best' is debatable, but for analog, I'd recommend the PVR-500. It's easy to use and has two tuners.

For digital, you can go with the HDHomeRun or the PCHDTV-5500. I believe the latter gives you the option of using analog or digital (but not both!).

The Streamzap is a pretty easy basic remote to use:
[http://amazon.com/dp/B00008XETO/](http://amazon.com/dp/B00008XETO/)

---

### Post by newlinux on 2008-02-28
For digital broadcasts, all the capture cards pretty much do the same thing - they capture the mpeg2 stream coming in, so there is no picture quality difference. The main difference is the chipset used, and some of them are more sensitive tuners than others, but for most this makes no difference.

Analog broadcasts have lots of sources of disturbances, so getting good picture quality for them has a lot of different factors.

For analog go with the PVR-150 or PVR-500 for dual tuners. For digital I'd recommend the Kworld ATSC 110/115 as the least expensive solution (does QAM/ATSC/NTSC and can switch back and forth between digital and analog (but can't record two things at the same time) just like the pchdtv 5500. Or if you just want ATSC you can try and find one of those cheap Air2PC rev .2 or something models on ebay. People were getting those for $20. if PCI slots are a problem, HDhomerun for dual digital tuner, and it is a network device.

What do you not like about how your MCE buttons work? You can always remap them how you want them to work, unless you just don't like the buttons on the remote.

---

### Post by Lutiana on 2008-02-28
As far as the remote goes it is more to do with my transition from Windows MCE. The more I use it the more I think it will be fine. I may look into changing the mapping.

Okay, I am liking the look of the ATSC115, but I cant seem to work out if it has a hardware MPEG2 encoder for the analog side of things. It is a good price (around $80) and won't need to be replaced next year. But I think the major problem I am having with this tuner card is that it does not do the hardware MPEG2 encoding, thus relying on the cpu to do it, and this seems to slow EVERYTHING down, sometimes making MythTV unresponsive.

I am thinking that purchasing a Haupauge PVR500 is not a good option as they seem to be around the $100+ mark, and it will become more or less useless in Feb '09.

So for now I am looking for a card that is better supported my MythTV, one that does not produce a tinny sound or a scrambled bar at the top (about 10pixels high).

Thanks for the advice, it has pointed me in the right direction. I would appreciate any more recommendations from other users.

---

### Post by newlinux on 2008-02-29
You probably won't find a hardware encoding analog card that also does digital and is supported in Linux. And by today's standards, the CPU power required for analog encoding is minimal,  Considering a PIII 700Mhz can encode analog... My P4 2.6Ghz doesn't skip a beat while recording analog. CPU usage is less than 15%. I see no noticeable difference between analog capture with my Kworld and my PVR-150.

Mine doesn't produce tinny sound, you just have to adjust the audio parameters appropriately.

And you can get the kworld for 20 or 30 dollars less than that at newegg...

If you want to look at other cards:

[http://www.linuxtv.org/wiki/index.php/ATSC_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_Devices)

The PVR-500 and other analog cards won't become useless in 2009. The all digital 2009 mandate only applies to broadcast (over the air). Cable companies can continue to transmit analog (or they can get rid of analog at anytime before then as well, as they have done in Chicago).

---

### Post by Lutiana on 2008-02-29
The Kworld PCI-115 is $65 from tiger direct. (it was $85 canandian) [http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=2927658&sku=O38-2010](http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=2927658&sku=O38-2010)

I have adjusted the audio options and have made the sound better, but its still very high pitched. And my wife says she can't stand the "fuzzy" picture.

I am thinking I am going to either buy a Kworld or a Happauge MCE-150.

I am running a P4 3.0Ghz w/ 1024Mb of RAM and the TV performance is not that great, I get stutters every now and again. I also notice some performance issues with Divx playback (very slight stutters). I thought the TV issue was the tv turner, but now I am thinking it is something different because what you are telling me is that this rig should run very well.

Do you have hyper threading enabled on your machine?

---

### Post by newlinux on 2008-02-29
My audio was tinny at first but I was able to get it to sound good, but part of that may be my audio receiver doing a good job with it too...

I think it is something else. A P4 3.0Ghz (HT or not) should be able to display HD signals, which is way more intensive than encoding or decoding analog. My P4 2.6Ghz is Hyperthreading, and it is using a Geforce 440MX. I can decode HD on this machine. I have a laptop that is a 1.4 Ghz Celeron M that can decode analog recordings without a problem, and that isn't much of a different load on a CPU than encoding it.

 What graphic card do you have? HAve you enabled the restricted drivers? You should have no problems with SD playback with that machine, and very little problem with HD playback. Does your machine struggle to play these back in just myth or in all programs (like mplayer and vlc). Just trying to see if it is a machine/OS configuration problem or a myth configuration problem.

---

### Post by Caps18 on 2008-02-29
I have two pcHDTV-5500s and I am very happy with the quality of HD content over-the-air.  The ten pixel black&white data bar (is it closed captioning on 640x480 streams?) can be removed by adjusting the offset in MythTV I believe.

I was real impressed with how easy it was to add a second one, but getting the right settings for the first one needs to be a little clearer.  I should take some screenshots of my setup and send it to the pcHDTV guys.

I haven't tested the pcHDTV with analog cable yet, but I might when I take it over to a friends house.  There is no reason to use analog over-the-air currently (or previously).

One other thing I like is that the broadcast flag isn't implemented with this card.  I'm not sure if it is with other cards, or if MythTV wouldn't play back stuff if it gets used in the future, but I don't have to worry about it.

They might not be the cheapest, but they work.  And that counts for something.

---

### Post by Lutiana on 2008-02-29
I am using an NVidia GeForce 6300 with the NVidia (restricted?) issued drivers.

should I be using the open source drivers?

I will try to play the content with other players tonight, and report back.

---

### Post by newlinux on 2008-02-29
In general, you should definitely use the nvidia drivers, especially if you are going to do HD playback.

It will be interesting to see if the other players have the same problem. But I'm sure that CPU power should not be the issue. You should also check your CPU utilization when doing these activities... You can use top (I prefer htop, its in the repos). If your CPU is getting eaten up when playing these something is wrong...

---

