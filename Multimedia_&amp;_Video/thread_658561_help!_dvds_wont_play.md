---
title: "help! dvds wont play"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by dcperkins on 2008-01-04
Hello, we are not familiar with ubuntu, (just starting out)
So, when we put a dvd in, it says we need a codec, we follow the steps for the codec, restart totem, and it says again that we still need the same codec. 
Im a little frustrated and have no clue what to do next. Could someone guide us?
thanks
d&c perkins

---

### Post by taurus on 2008-01-04
What codecs did you install?  Try installing ubuntu-restricted-extras first and see if you can play your DVD now.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by overdrank on 2008-01-04
> **dcperkins said:**
> Hello, we are not familiar with ubuntu, (just starting out)
So, when we put a dvd in, it says we need a codec, we follow the steps for the codec, restart totem, and it says again that we still need the same codec. 
Im a little frustrated and have no clue what to do next. Could someone guide us?
thanks
d&c perkins

HI and welcome, These links should help
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
Good luck!
Edit to slow :)

---

### Post by dcperkins on 2008-01-04
ok, we put that in, clicked ok, it did a bunch of talking and then we clicked ok for liscensures, it counted down and told us it was installed with no errors, so we closed it restarted totem and tried again and it still told us 
"Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc"

---

### Post by taurus on 2008-01-04
Have you tried using vlc instead of totem?  If you don't have vlc, you can install it from System -> Administration -> Synaptic Package Manager.  

It should be in Applications -> Sound & Video.

---

### Post by dcperkins on 2008-01-04
thanks for the help we will be back if we have any more question.

---

### Post by bheku on 2008-01-05
> **taurus said:**
> Have you tried using vlc instead of totem?  If you don't have vlc, you can install it from System -> Administration -> Synaptic Package Manager.  

It should be in Applications -> Sound & Video.

Hi Taurus,

A slight variation to the same problem. Nothing at all happens when I put a DVD in the DVD drive. It's as if I don't actually have a DVD drive. I can however read/view CDs with the DVD drive. I think I've done all the necessary codecs things because I can open just about any file format, I was even surprised that I could view .flv files in VLC.

Sadly neither Totem nor VLC seem to be able to read my DVDs. In Totem, the option under 'Movie' is always greyed out for DVDs. In VLC's "Message" window, I get:

dvdread error: DVDRead cannot open source: /dev/scd1 (tried both scd0 and scd1)

I hope this might give you a clue as to what the problem might be.

Thanks in advance.

---

### Post by lisati on 2008-01-05
[https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html) ,oght be of some help.... keep up with the good questions!

---

### Post by bheku on 2008-01-05
> **lisati said:**
> [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html) ,oght be of some help.... keep up with the good questions!

Thanks for the URL. Unfortunately it came to nothing. Still have the same problem.

I'm positive I have the latest codecs installed, so I'm not sure what else to check. Any help would be much appreciated...

---

### Post by spindlybunion on 2008-01-05
I had a similar issue with DVDs . i installed the restricted codecs and still could not play DVDs in Totem . 
I spoke to a colleague and he suggested trying MPlayer but again still had the same problems . I then installed the FFMPEG codecs and i was then able to play DVDs via MPlayer but still unable via Totem

---

### Post by bheku on 2008-01-05
> **spindlybunion said:**
> I had a similar issue with DVDs . i installed the restricted codecs and still could not play DVDs in Totem . 
I spoke to a colleague and he suggested trying MPlayer but again still had the same problems . I then installed the FFMPEG codecs and i was then able to play DVDs via MPlayer but still unable via Totem

Still no luck on my side. Got MPlayer and FFMPEG codecs installed, but I get the following error:

No stream found to handle url dvd://1

Not sure if the error message is truncated. Did you get this error by any chance?

Thanks for sharing the info, BTW.

---

### Post by myname on 2008-01-05
I am having the same problem.  I installed the codecs and I could watch one of the Harry Potter movies (retail DVD), and it played fine, it did not work before I installed the codecs.

However, I put in the copy of Shoot em Up that I just bought and it does not play.  I put in another retail DVD that is a few years old, and I get the "Missing codec" error message.

I did have this many problems with prior versions of Ubuntu, only in Gutsy.

Anyone have a resolution on how to play retail DVD's?

UPDATE:
I think it may have something to do with the menu structure, I think.  When I put the a DVD (harry Potter 3) in the my Kubuntu system, I get the DVD's menu in Kaffiene, however, in Totem, the movie just plays.  However, some of my movies won't play in Totem.  Does this make sense?  How can I get to the menu of a DVD within Totem?

--Kevin

---

### Post by cor2y on 2008-01-05
Use totem-xine or gxine or xine-ui , just a media player with the xine library for dvd menus.
Or you could try vlc player.

I gave up on totem-gstreamer for dvd playback in this version of Ubuntu i don't know why but it completely refuses to work for me with gstreamer even with all the restricted repos, codecs etc enabled, but it will play with the xine library or mplayer or vlc.

---

### Post by rainwalker on 2008-01-05
I use VLC to play DVDs, and it works fine (including menus). Are you sure you installed libdvdcss?\
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

---

### Post by myname on 2008-01-05
> **rainwalker said:**
> I use VLC to play DVDs, and it works fine (including menus). Are you sure you installed libdvdcss?\
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

I can play some DVD's but others will not play, so I am assuming I installed libdvdcss.  From the URL you gave me, which version should I install?

--Kevin

---

### Post by rainwalker on 2008-01-05
> **myname said:**
> I can play some DVD's but others will not play, so I am assuming I installed libdvdcss.  From the URL you gave me, which version should I install?

--Kevin

Actually, that might be sign that you don't have it installed because not all DVDs are encrypted.
You should install the package that fits your computer's specs; You can't see the whole filename but if you hover your mouse over it and look in the bottom bar of Firefox it shows you the target. Or, here...
AMD64: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_amd64.deb)
i386: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_i386.deb)
PowerPC: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_powerpc.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_powerpc.deb)

---

### Post by myname on 2008-01-05
> **rainwalker said:**
> Actually, that might be sign that you don't have it installed because not all DVDs are encrypted.
You should install the package that fits your computer's specs; You can't see the whole filename but if you hover your mouse over it and look in the bottom bar of Firefox it shows you the target. Or, here...
AMD64: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_amd64.deb)
i386: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_i386.deb)
PowerPC: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_powerpc.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2-dev_1.2.9-2medibuntu2+b1_powerpc.deb)

Just installed it, i386 version, and I get this when I try to play the DVD:

[ATTACH]55441[/ATTACH]

Any idea?  This DVD plays fine in Kubuntu.  Could it be Totem?  I may try the Xine, or VLC to see if it will work.

--Kevin

---

### Post by rainwalker on 2008-01-05
Ug, I hate Totem.
I would recommend trying it with VLC (install with Synaptic)

---

### Post by AdNZL on 2008-01-06
Ok for a start, I'm am completely new to linux and most of the time have no idea what I'm doing, but here's what worked for me. 

I tried everything everyone had suggested and got no where until I installed VLC. That was great, but it was the only player I had that would run DVDs. The others still didn't work no matter what Library's I installed. However I installed a whole bunch of DVD creation and backup software from the repository's and suddenly everything was working. So if all else fails you might want to try this, I know it seems silly, but hell, if it works why not :P

Here's what I installed

VLC
AcidRip DVD Ripper
DeVeDe
Dvd95
dvd::rip
ManDVD
QDVDAuthor

I'm sure you don't need to install all of those, but obviously one of those must come with the codex/librarys needed, and possibly does a few automated set up routines of its own that got things working on my system at least. 

As I said before nothing worked except VLC until I installed those extra programs.

Good luck :)

---

### Post by lewac on 2008-01-08
well it seems that totem doesn't seem to "like" the default gstreamer codec backend. first do this if you haven't already done so  (as previously suggested above): sudo apt-get install ubuntu-restricted-extras... THEN  the simplist way to do it (without using the CLI) is to launch synaptic package manager (system/administration/synaptic package manager) and search on "totem". find the line "totem-xine" and install that. this will automatically UN-install "gstreamer" which is what you want to do. basically you're swapping one backend (gstreamer) for another (xine).

if you still get the error install vlc and forget about totem for playing your movie dvd's! you can auto-launch vlc by changing the following property from totem% to wxvlc: system/preferences/removable drives and media/multimedia (tab)/video dvd discs.. insert the noted command in the edit field and close. vlc will then launch when you insert a movie. just click the right arrow (play button) and a window will launch asking you to open the disc. do so and the movie oughta start playing!

one of my systems still failed in totem but subsequently vlc had no problems. btw either these programs work great on really legacy systems. one of mine loaded with ubuntu gutsy is a pentium lll running at 600mhz with 512mb of some pretty slow memory and it STILL plays full screen without a hitch. (try THAT in windows!) good luck!

---

### Post by Alfred_McGee on 2008-01-09
Lewac's vlc fix doesn't work for me in Feisty. Totem played most DVDs automatically when inserted, except for some very new commercial ones, for which the following error message apeared: "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" My answer was "no." Strangely enough, for one of these DVDs, the error message would only appear when I tried to select a chapter or scene from the DVD menu. Then, as per Lewac's instructions, I installed vlc with no problem and replaced the "Totem %" with  "wvlc," but now DVDs don't play automatically when inserted!

---

### Post by rainwalker on 2008-01-09
> **Alfred_McGee said:**
> Lewac's vlc fix doesn't work for me in Feisty. Totem played most DVDs automatically when inserted, except for some very new commercial ones, for which the following error message apeared: "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" My answer was "no." Strangely enough, for one of these DVDs, the error message would only appear when I tried to select a chapter or scene from the DVD menu. Then, as per Lewac's instructions, I installed vlc with no problem and replaced the "Totem %" with  "wvlc," but now DVDs don't play automatically when inserted!

That should be "wxvlc" not "wvlc"

---

### Post by Alfred_McGee on 2008-01-09
> **rainwalker said:**
> That should be "wxvlc" not "wvlc"

Oops! Sorry! You're right. Vlc now opens automatically when I insert a DVD, but it doesn't pop the DVD scene selection menu up on the screen the way Totem used to. Once I tell it to "Open disk," and click "OK," then it pulls up the menu, but crashes if I try to actually make it play the movie or any part thereof. It works perfectly with older DVDs, though, and it allows you to skip ahead in the movie if you want- which I've never been able to do in Totem with anything that was on DVD. So I have to agree that vlc is a better DVD player once you get it going. Are there DVDs that just won't play in Linux (yet)?

---

### Post by rainwalker on 2008-01-10
> **Alfred_McGee said:**
> Oops! Sorry! You're right. Vlc now opens automatically when I insert a DVD, but it doesn't pop the DVD scene selection menu up on the screen the way Totem used to. Once I tell it to "Open disk," and click "OK," then it pulls up the menu, but crashes if I try to actually make it play the movie or any part thereof. It works perfectly with older DVDs, though, and it allows you to skip ahead in the movie if you want- which I've never been able to do in Totem with anything that was on DVD. So I have to agree that vlc is a better DVD player once you get it going. Are there DVDs that just won't play in Linux (yet)?

There probably are, but I haven't had a problem with it (yet).
What movie are you trying to play?

---

### Post by Alfred_McGee on 2008-01-11
Well, I have *Good Night and Good Luck* in a 2005 Warner Brothers DVD release. It won't play at all, though I once watched it on an older disk using Fedora. The other day I tried a 2007 DVD release, *El topo,* and could only access the DVD menus. Navigating between these menus was no problem using Totem, Ogle or VLC, but when I tried to select "extras," "chapters" or "play video," I never got further than the FBI warning. These are the only DVDs I've had trouble playing in Linux, but I usually watch movies that are at least a couple of years old, so I was wondering if perhaps some sort of new encryption has come out for which there are no Linux codecs yet. The recording industry is apparently plotting to force people to upgrade to blu-ray or something, but that wasn't the problem with the DVDs I was trying to play the other day. Any thoughts?

---

### Post by cor2y on 2008-01-11
try totem with the xine backend aka totem-xine or any of the libxine backend media players like gxine or xine-ui.
I have come to the conclusion that something is wrong with gstreamer and dvd playback.
Mplayer can't handle dvd menus but totem-xine can, vlc shouldn't have any problems handling dvd menus but if its giving a problem try any of the xine based players like i said.

---

### Post by Alfred_McGee on 2008-01-12
Gxine says "Encrypted or faulty DVD," but this 2005 disk is in pristine condition. Totem-xine's drop down menus don't work, but for me that's true with any DVD - Totem only works when I insert a disk- but with this 2005 DVD, Totem doesn't work at all. I tried unistalling all my gstreamer plugins that didn't have a lot of dependencies. As I am able to watch so many DVDs, codecs don't seem to be the problem. Already tried reinstalling libdvdcss... any more ideas?

---

### Post by Alfred_McGee on 2008-01-13
Using mplayer on that problem DVD didn't work either, but it appears to have been a bit more informative. Can anyone tell me what's wrong here?

t@t-lo:~$ mplayer dvd://1
MPlayer 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2080  @ 1.73GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 10 titles on this DVD.
There are 22 chapters in this DVD title.
There are 1 angles in this DVD title.
libdvdread: Invalid title IFO (VTS_01_0.IFO).
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 1 language: en
subtitle ( sid ): 3 language: fr
subtitle ( sid ): 5 language: es
number of subtitles on disk: 3
MPEG-PS file format detected.

EDIT: The problem was regionset. Fixed it.

---

### Post by ubu-for on 2008-01-13
> **dcperkins said:**
> So, when we put a dvd in, it says we need a codec, we follow the steps for the codec, restart totem, and it says again that we still need the same codec.

Yes, it's a [problem with Totem-GStreamer](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/28605). Do you already know Totem-Xine, Ogle or VLC?

---

### Post by AJB2K3 on 2008-01-13
I had this error my self and it was simple to fix.
Googlefor dvd playback in ubuntu 7.10 and it will say to install dvdcss2. I did that and OMG dvd playback of encrypted dvd's now work !!!

---

### Post by raddellee on 2008-02-12
I got it working in mplayer. but 

The odd sudo apt-get install (all of these) might help ( Synaptic package manager )

libdvdcss2

libdvdnav4

libdvdread3

lame

w32codecs

flashplugin-nonfree

xine-ui


and if its still not working try these ( add remove has them )

GStreamer Dirac video plugin

GStreamer extra plugins

GStreamer ffmpeg video plugin

GStreamer fluendo MPEG2 demuxing plugin

GStreamer plugins for aac, xvid, mpeg2, faad

GStreamer plugins for mms, wavpack, quicktime, musepack


hope this helps though probs these have been mentioned in previous post!

---

