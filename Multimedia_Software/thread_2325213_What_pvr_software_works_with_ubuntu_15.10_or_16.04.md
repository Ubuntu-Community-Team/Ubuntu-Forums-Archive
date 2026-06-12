---
title: "What pvr software works with ubuntu 15.10 or 16.04 'out of the box'?"
date: 2016-05-20
forum: Multimedia Software
---

### Post by ultragamer2 on 2016-05-20
What pvr could I use (for a dvb-t usb stick) with Lubuntu 15.10 currently or I could install 16.04 if necessary.

I tried tvheadend but it won't work, apparently it's hard to get it to work in 15.10 or 16.04.

Is there any one I can just install without having to go through lots of complex workarounds that I can't get to work? Can anyone recommend one that they confirm works with dvb-t sticks?
I'm a newb.

Or should I buy a stand alone pvr?

---

### Post by TheFu on 2016-05-20
> buy a stand alone pvr
This.

As is normal in the Linux world, lots of separate projects are used to make an amazing, flexible, system to provide a solution.  This isn't always easy, since finding a clear set of instructions that is also easy to follow (especially for a noob), isn't always easy.  I've tried tvheadend myself and failed to get it connected and working with the PVR software and the appropriate drivers to my tuners. There are at least 3 parts to make this work, IME.
1) supported drivers (highly dependent on the tuner device(s))
2) driver interface like tvheadend (Perhaps a mythtv back-end or some other equiv tool)
3) GUI/Interface for humans (MythTV, PVR-addon for Kodi, NextPVR addon for Kodi, ... ) you get the idea.

For about 7 yrs, I've been using Win7 Media Center to record TV (runs inside a VM). I tried to get MythTV working 3 times since 2002 and failed each time with different tuners, though I haven't tried with any release newer than 14.04.  I'm an LTS-only guy and won't touch 16.04 for a few more months. Need to let 3rd party devs catch up with the new release.

For playback, I use Ubuntu and Debian-based systems.  Played with NextPVR (windows-only) for a few months last year. The lack of schedule data made it less-than-ideal for my needs. It was easy to get a connection working from my Kodi systems using the NextPVR system as the recording box.

If you want a PVR that *just works* without any real setup, get a TiVo. You will pay much for it and for the monthly schedule data (N. America schedules are NOT free).  

Sorry I don't have an easy answer.  If you post the exact tuner and which local you are in, folks might be able to help more.  TV stuff is very regional. What works for me, likely won't work for others in a different country.

---

### Post by Bucky Ball on 2016-05-20
I use Me-tv. It's in the repositories (Software Centre). I don't use it to record, but it has that functionality. I've recorded with it for a test and works fine. In general, Me-TV works great for me and has done for a few years.

One of the bonuses of it is, on first run, it will ask if you'd like to do an autoscan for TV stations. Some other apps you need to fiddle around with that yourself. Good luck. ;)

---

### Post by TheFu on 2016-05-20
Installed Me-tv here.  Says it doesn't find any DVB tuners.  Looking over [https://ubuntu-mate.community/t/how-to-watch-digital-tv-with-kaffeine-or-me-tv-in-ubuntu/906](https://ubuntu-mate.community/t/how-to-watch-digital-tv-with-kaffeine-or-me-tv-in-ubuntu/906) ... have both Hauppauge 950Q and HDHR-3US network tuners (but haven't installed any drivers).  Would be nice to get some ATSC OTA signals working.

---

### Post by Bucky Ball on 2016-05-20
Hmm. They are USB? Unplug both. Reboot the machine. Once at a desktop, plug one in, open a terminal and

> dmesg

At the bottom of the output should be info about the USB dongle, specifically, whether it is configured and ready to go.

I get this:

> [ 1635.775144] usb 1-9: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected

---

### Post by TheFu on 2016-05-20
950Q is USB. 
```
[397005.534098] usb 1-2.3: USB disconnect, device number 20
[397028.531349] usb 1-2.3: new high-speed USB device number 21 using xhci_hcd
[397028.639658] usb 1-2.3: New USB device found, idVendor=2040, idProduct=7200
[397028.639682] usb 1-2.3: New USB device strings: Mfr=1, Product=2, SerialNumber=10
[397028.639700] usb 1-2.3: Product: WinTV HVR-950
[397028.639712] usb 1-2.3: Manufacturer: Hauppauge
[397028.639724] usb 1-2.3: SerialNumber: 45xxxxxxxxx

```
I cannot alter the kernel on this device any farther.

The HDHR3 are networked-based tuners - much, much, much, much more flexible. The vendor is silicon dust. [https://www.silicondust.com/hdhomerun/](https://www.silicondust.com/hdhomerun/) These are amazing devices.

---

### Post by ultragamer2 on 2016-05-24
Thanks for all the suggestions.

I installed Me-tv and it works (well almost). It's just what I wanted an easy to use program.

I only have one problem, after scanning it only gets some of the channels in Australia (this has been a common problem in windows as well when choosing Australia - in windows I had to choose scan all regions for it to detect all the channels but in Me-tv there is no option to scan all regions), what could I do to force it to do a complete scan of everything to detect all the channels?


Also I assume me-tv isn't doing live recording while watching anything to my ssd be default like some windows apps were?

---

### Post by Bucky Ball on 2016-05-24
I doubt that it is recording unless you set up a recording.

I have been having a few issues with channel scans in Me-TV over the last week or two. Before then, fine. Also in Australia and a couple of channels changed so, even though I have all the other channels fine, did a scan for the new ones and it found no channels at all!

That is odd because it will always find some. Never experienced that before. 

Which channels are you missing? I could post you my channels.list file, but it is for Adelaide and I also have a couple of channels missing (most notable SBS and its channels).

---

### Post by ultragamer2 on 2016-05-24
Thanks, I'm missing most of them. It seems to get the abc ones and a couple but most aren't there.

The same problem happened in a windows tv program and I had to choose scan all regions instead of Australia and then it found them, can't seem to do that in Me-Tv though.

---

### Post by Bucky Ball on 2016-05-25
Copy and paste this in to a plain text document and save it as 'channels.conf' in your /.me-tv hidden directory in /home. 

In case you don't know how to find that, go to your /home directory, hit control+h to see hidden files/folders. You will see /.me-tv in there. Open that folder and plop the channels.conf file in there. Launch Me-TV and see what it gives you (you shouldn't need to scan, channels should just be there). 

 ```
ABC News 24:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2314:0:592
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:593
ABC2 / ABC4:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2307:2308:594
ABC1:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:595
ABC3:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:2311:2312:596
Double J:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2317:598
ABC Jazz:226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:0:2318:599
7 Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1360
7 Digital 1:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1361
7TWO:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1313:1314:1362
7mate:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1329:0:1363
7 Digital:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1281:1282:1364
TV4ME:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1393:1394:1367
Fresh Ideas TV:177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:1409:1410:1368
Nine Adelaide:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1105
GEM:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:0:1112
GO!:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:652:1106
EXTRA:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:516:653:1107
EXTRA2:191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:517:655:1109
ONE:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1617
TEN Digital:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1621
TVSN:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:518:690:1622
ONE:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:0:1623
ELEVEN:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:516:681:1624
SpreeTV:219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_1_2:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:520:700:1625
44 Adelaide:564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_1_2:QPSK:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:100:101:3585
Nine Adelaide:191500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:512:650:1105
GEM:191500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:513:0:1112
GO!:191500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:514:652:1106
EXTRA:191500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:516:653:1107
EXTRA2:191500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_3_4:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE:517:655:1109
SBS HD:184500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:853
```

Let me know what you get and what you don't. I haven't used these for awhile but I have another which has more entries. Might be able to steal the ones you're missing from there. Good luck.

---

### Post by ultragamer2 on 2016-05-25
It's working now with the other generic tv stick. When going through the usb hub it only worked sometimes and only with some channels, but direct to a usb 2 port it works, it doesn't work at all with the usb3 ports. So it's all working now, all channels only when directly connected to a usb2 port.

But one small problem, the de-interlacing isn't working at all even though it's on, what video driver (in preferences) type should I be using it's on 'xshm' (I'm using a Gigabyte Brix 3000 mini pc with "Intel[SUP]®[/SUP] HD Graphics")?
Also for scheduled recordings should I put the computer in sleep or shutdown?

---

### Post by Bucky Ball on 2016-05-25
Ah, yes. That old chestnut. Straight into the box rather than through a hub is definitely the go, as you've discovered. ;)

See the attached screenshot for what I have in the preferences window. It may have something to do with the actual GPU driver you have installed for the OS rather than the setting in Me-TV. Can you watch, say, a video via VLC without issue or any other video in another app without issue?

You could try some other settings in preferences (opengl?) and see if it makes any difference. I'd be curious to know, but I am using xshm also but no deinterlacing issues. :-k

As for putting the machine in suspend or shutdown: don't think shutdown would work as your machine is literally switched off. Experiment with suspend is my advice. Schedule a recording, hit suspend, see if it wakes up.

---

### Post by ultragamer2 on 2016-05-25
Thanks, that's the same as the settings I have.

I've also been having some problems with unresponsiveness, when you press a menu button it takes a long time for anything to happen. But I'll have to test some other settings.

Does anyone else have the same problem, if you put number of channels and number our hours ahead in preferences to 100 the program lags and you can't click anything anymore?

---

### Post by ultragamer2 on 2016-05-26
I don't know, now I'm getting nothing but 'failed to lock to stream' errors with the usb stick that was working before (I have two of them) and the asus one works but it has blips all the time. I have another one but that doesn't detect at all.

Can anyone recommend a low cost current dvb-t usb stick that works in linux with me-tv without any bugs or issues?

---

### Post by Bucky Ball on 2016-05-26
I am using an EzyCap, [this one]("http://www.dx.com/p/mini-dvb-t-digital-tv-usb-2-0-dongle-with-fm-dab-remote-controller-92096") to be precise. 

No idea if they are still available. I picked mine up by chance about five or six years ago. Then, by chance once more, I happened to wander in to the same shop again about five years later and there was another, neglected and the box covered in dust, so I bought that, too, as a spare. :)

---

### Post by ultragamer2 on 2016-05-27
Ok sounds cool.

I ordered a cheap RTL2832U since it seemed to say it was compatible if I was reading the linux tv page right.
[IMG]http://i.ebayimg.com/00/s/MTAwMFgxMDAw/z/bfUAAOSw3mpXNtFA/$_57.JPG[/IMG]


This is the one I was using before (I had two of them) but all of a sudden they wouldn't work anymore (they didn't work at first either) I don't know why.

[IMG]http://i.imgur.com/FnV5Ul.jpg[/IMG]


But I have an old Asus mycinema u3000 which works but often seemed to have frequent blips.

I also had a mini type one but that wasn't compatible at all.

Has anyone noticed when you increase the number of hours ahead for the epg display in me-tv it causes lots of lag? I want to be able to look through the tv shows for the next few days to set things to record.

---

### Post by Bucky Ball on 2016-05-27
The RTL2832U is exactly what I'm using in the Ezycap. ;)

It should work 'out of the box' on all releases from 12.04 LTS up. Just plug it in and run 'dmesg' in a terminal. Check to see it is recognised and configured.

---

### Post by ultragamer2 on 2016-05-27
Ok sounds like it might work this time. Can me-tv recording work with two tuners? (not that there is probably enough on tv to have to record two shows at once, but might happen occasionally)

---

### Post by Bucky Ball on 2016-05-27
Experiment and tell us. ;)

---

### Post by ultragamer2 on 2016-05-30
Ok I'll test it with the asus and this new one when it arrived in couple of weeks (I only ordered one because I have 5 tv tuners already that won't work) so if this works I'll order another one of these then.

Could anyone do a quick test, change the EPG span to 100 hours and see if you get massive lag in the whole program? I want to see if it's just my system or not.

---

### Post by ultragamer2 on 2016-06-09
Ok I got one of the new RTL2832U dvb-t sticks (the white one in the picture above) it works well (haven't recorded yet cause I only have an 8gb ssd so far (need another drive)) but if it works I might add another stick and test dual tuners.

The old asus u3000 one doesn't seem to want to change to a different signal broadcast (set of channels) unless you restart the application so it wouldn't be a good test of dual tuner recording.

---

### Post by Bucky Ball on 2016-06-09
Good to hear the new dongle is working fine. ;)

Unsure if Me-TV can handle two tuners. If you're thinking of recording one channel and watching another. I suggest you experiment with one first and set a recording on one channel while watching another. It will probably give a message the recording is about to start and prevent you from watching the other channel, but ...

With two tuners, guess you could open two instances of Me-TV or whatever other app you're using.

---

### Post by ultragamer2 on 2016-06-10
It would be mainly for recording two things at once, but with the fairly limited number of shows that I would watch on offer it would probably happen rarely.

One thing though, I wish there was a better epg where you can view only the shows for one channel over the next week. I liked using Kodi but installing tvheadend (tv backend) and getting it to work seems to require a linux expert to do, or a very specific older version of linux.

---

### Post by TheFu on 2016-06-10
Schedule data is a **highly** local issue. Every region has to deal with it separately.  For example, in the US, stations broadcast only 2 hrs of upcoming schedule data and there are not any free sources for Linux users except websites with tonnes and tonnes of javascript - nearly impossible to programmaticly parse. The tuner software has to scan every channel to capture that schedule data ... which takes about 8 minutes for my tuner to hit the 70 channels.  Doing that every hour or two basically locks up 1 tuner while that happens, preventing it from being used to capture a complete show.  I know this is how it works (NextPVR on Windows tested) here.  People in USA/North America pay US$25/yr for schedule data from ¨schedules direct¨ to get 10-14 days of schedule data in advance. 5 yrs ago, it was possible to grab data from a free web site (tvnow.com? - I don´t remember), but they´ve made changes to prevent that AND altered their ToS to disallow it.

I understand that in other parts of the world, especially Europe, there are free sources of schedule data available, but that each country/region has different sources.

I like to think I´m a Linux expert after 23 yrs (15 as an administrator and 10 as a C/C++ programmer), but was unable to get TVheadend working following the instructions on both a P-pi and a normal x86 Ubuntu machine. Guess I´m not an expert.

Anyway - when it comes to schedule data, please include your location to get any help.

---

### Post by ultragamer2 on 2016-06-10
Yes that is a small problem I am having that it sort of freezes (plays tv but I can't do anything in the me-tv gui) in the beginning while it's updating the schedule data.
So if I get a second tv stick using me-tv it will use the second tuner to get the schedule data, will it still freeze the interface?

I've always had 2 tuners before but there are way less channels than 70 and I never really noticed any delays in nextpvr through kodi but have noticed other problems like buffering on hd channels. I used to just select view epg for one channel and scroll through all the shows for the next 6 days and select things to record and it seemed to get the data in the background and I didn't really notice it causing any problems. I wish there was a single channel view in the me-tv epg. So I'll have to select shows to record every couple of days instead.

---

### Post by Bucky Ball on 2016-06-10
Not exactly what you're looking for, and may not be of any help, but under View> Preferences, what about 'EPG span' and 'EPG page size'? Can you tweak that to help? 

Also, you can delete channels you don't watch (I get rid of info channels) and rearrange where the channels are in the channel list (View> Channels and just drag and drop channels to where you want them to appear on the list). This might give you all your favoured channels in one group, making it a little easier. 

Just thought I throw it in ...

---

### Post by ultragamer2 on 2016-06-12
OK yeah that makes it a bit better but add more delay.

Another problem is I can't get it to work with HD channels.

---

### Post by Bucky Ball on 2016-06-12
That doesn't give much information to go on. How does it 'not work'?

As you seem to have had you original question answered on this thread, for your own benefit as it may improve your chances of support, it might be better to mark this one solved and start a new thread for your new problems as they are veering away from your original question and thread title and in to new territory. ;)

Just a thought. You can always post a link here to the new thread.

---

### Post by ultragamer2 on 2016-09-24
As an update to this. I got everything to work except for waking to do a scheduled recording.

It will record only if the computer is on, if it is in suspend mode it won't wake to record.
Has anyone got me-tv to wake to record?

---

### Post by Bucky Ball on 2016-09-24
You never got back to this with a reply then so please don't wake an old thread to [post a duplicate]("https://ubuntuforums.org/showthread.php?t=2337625") now. Thanks.

*Thread closed. *

---

