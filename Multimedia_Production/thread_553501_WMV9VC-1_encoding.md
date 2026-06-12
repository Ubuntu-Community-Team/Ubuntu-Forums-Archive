---
title: "WMV9/VC-1 encoding"
date: 2007-09-17
forum: Multimedia Production
---

### Post by joker on 2007-09-17
Is it possible to encode video to WMV9 or VC-1 in linux?  

Thanks

---

### Post by Judo on 2007-09-18
Natively?  Not yet, I think.  I ran across [this wiki article]("http://wiki.multimedia.cx/index.php?title=FFmpeg_Summer_Of_Code#VC-1") a while ago.  At that time, it had already been accepted.  To be honest, I don't exactly when, but I think it was three months ago.  I don't know about the progress, but I think we can expect good things, as usual, from FFMPEG.

I wouldn't think it's possible to do with WINE since Microsoft is checking for WINE in many of their new programs, which they have the audacity to call Windows Genuine _Advantage_.  Then again, I've never tried.

May I ask why you would want to use VC-1?  It's good, but not the best.

---

### Post by joker on 2007-09-18
The reason I ask is that I am looking into buying a MP3/Video player (the new Creative Zen) which says it only supports WMV9 or MJpeg in the US market.  Although the on the asian product description is says it also supports XvID and DivX.  While I am hoping that DiVX functionality has not actually been removed from the product fot the US market, I wouldn't know for sure until I actualy had it in my hands.  Now, If I could encode to WMV9 in linux, it wouldn't matter either way.  That's why I asked.

The new ZEN, for those who care,  is very much like the new iPod nano in size and function, but with a bigger screen, expandable storage, and an FM tuner.

---

### Post by vinutux on 2007-09-18
it is possible ........ with a tool called "Winff"

it is not in ubuntu repos 

install it from [http://biggmaatt.com/winff]("http://biggmaatt.com/winff")

it cooool for converting videoes especially for mobile devices....


try it..................:guitar:

---

### Post by stmiller on 2007-09-18
> **vinutux said:**
> it is possible ........ with a tool called "Winff"



VLC is also a frontend for ffmpeg.

---

### Post by joker on 2007-09-19
Unfortunately ffmpeg does not encode WMV9 yet, they just recently incorporated MWV9 decoding, but have not yet released an encoder.  

Last night I set up VMware and was able to map my 'nix partitions so they can be used seamlessly in windows.  While I would have preferred a more native solution this will work, at least I won't have to reboot.  Unfortunately, it looks like whatever player I choose, there is always some function that requires Windows.  Oh well.  

I have to say, that winff looks like an easy way to do batch conversions, if I end up going with the iPod I will have to give it a whirl.

---

### Post by stmiller on 2007-09-19
Microsoft does not give out specs to anyone to do WMV9 encoding other than their software.

I would say you should avoid that Creative player, and get a Cowon or other player that is not tied to Windows and WMV.

---

### Post by joker on 2007-09-19
From my limited research I have found that WMV9 is VC-1.  Microsoft decided to push VC-1 as a standard to be used  for encoding high def video disks.  Because they wanted it to be a standard, they had to document it .  So VC-1 may actually make it to the 'nix world.   I thought I read somewhere that the ffMpeg guys are working on it. 

Anyway, I have looked at the Cowon players and they didn't have what I am looking for.  I want a small (iPod nano-ish) flash based player with a good amount of memory (8gb-16gb), a decent screen, and preferably linux compatable.  Right now my choices seem to be the sandisk sansa view, the ipod nano, or the creative zen.  

I won't count out the Zen until I can confirm what video codecs it can use, if it does play xVid (like the asian version) it would still be just fine.  The sandisk view may also work out.  The iPod nano screen is smaller than I would like, but I will take it if the UI of the other players is not user friendly.

Anyway, if you know of any other player that fits my criteria I will definitely check it out.

---

### Post by magret55 on 2007-11-18
I just bought the sansa view and it's not working out so well. Primarily, no msc mode, and mtp doesn't support it (yet). I also broke the home button in under an hour and it continually restarts when it is plugged into my computer (maybe it thinks that if it closes its eyes and tries again, it'll find windows, I don't know).

Other people have been having the same problems. Maybe somebody will find a solution soon? It won't be me.

I'm looking for the same thing though so let me know if you're successful.

---

### Post by Creative2 on 2007-11-19
winff or ffmepg can encode into wm2 or wmv1 but not in wma so you can do at the top 

for video wmv2 with mp3 audio.

edit

now ffmpeg can encode into wma

---

### Post by lane32x on 2007-12-16
ha ha ha. that was an awesome quote...about opening its eyes and hoping to find windows... love it.

ok. so my sansa and a couple other usb devices used to exhibit similar behavior of restarting constantly in linux, OR another glitch was that in XP it would tell me that the device was not plugged into a hi-speed hub and that it was capable of much faster transfers...yadda yadda...

you know what fixed my problem? a usb POWERED hub. my ports didn't have enough juice. that's it. that was the only problem. 15 bucks from wal-mart and my transfer rates are great and my hard drive and my players and my bluetooth all work fine now.

hope that helps at least one person.

---

