---
title: "Problem: VIDEO/X-MS-ASF streams"
date: 2009-12-05
forum: Multimedia Software
---

### Post by kle on 2009-12-05
I would like to watch/listen to the news on the Icelandic national broadcasting channels on RUV.is. Apparently,the problems I have with RUV also apply to the Norwegian national broadcasting channels on NRK.no, except that NRK allows streaming of live radio in mp3 and ogg.
[I]
I am using KDE 3.5 (Kubuntu 8.04) with a Mozilla browser (Seamonkey 2) MPlayer and Mozilla MPlayer plugin. (I don't think my problem is limited to KDE users.) [/I]
I encountered the same problems as described below on my old MAC using flip4Mac in lieu of Windows Media Player, and I hear this also applies to newer MAC users.

VIDEO/X-MS-ASF seems to be a real hassle! I would like to emphasise that I have no trouble watching these streams fromWindows XP, so the links seem to be ok.

**Preparations**
I started by following the recommendations for Ubuntu users on RUV's  FAQ page,[http://dagskra.ruv.is/faq/]("http://dagskra.ruv.is/faq/")
and installed
gstreamer0.10-ffmpeg, 
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
Then I conscientiously followed the guide on Ubuntu forums:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

**Result Radio**
Live radio  [http://dagskra.ruv.is/ras1/streymi/beint/?5]("http://dagskra.ruv.is/ras1/streymi/beint/?5")
"Getting playlist... connecting... buffering..." Streaming starts, but stops after a while, sometimes only a few seconds. Does not start again on its own, but has to be called again.

_Radio programs_ (for instance [http://dagskra.ruv.is/ras1/streymi/4492850/](http://dagskra.ruv.is/ras1/streymi/4492850/) )
Same as for radio live, except that when it is called again it starts from the beginning

**Result TV**
Live TV: (Basically only the news is available live from RUV)

_Previous news_ (for instance [http://dagskra.ruv.is/sjonvarpid/4497831/2009/12/04/]("http://dagskra.ruv.is/sjonvarpid/4497831/2009/12/04/") )
"Getting playlist...,
Connecting to server http.0.muli.rs.ruv.is[194.105.226.39]:80..." is all I can see in the MPlayer screen. Eventually, the stream starts playing, but it inevitably stops after a minute or two. The progress bar gives me the following information:" 2:58 / 27:06 / 17%". This I take to mean that I have managed to play almost three minutes of a stream that lasts 27 minutes, What the 17 % means I don't know. Eventually, the programme starts again from scratch. 

**In VLC**
If I copy the URL [http://dagskra.ruv.is/sjonvarpid/streymi/4497831/]("http://dagskra.ruv.is/sjonvarpid/streymi/4497831/") to VLC, the following baffling address is resolved:
mms://http.0.muli.rs.ruv.is/video.ruv.is/4497831$1.wmv?MSWMExt=.asf
Again the stream starts playing, but after a couple of minutes it stops, and the following error messages are subsequently generated:
pulse error: Failed to connect to server: Connection refused
pulse error: Pulse initialization failed
ffmpeg error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)
ffmpeg error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)
access_mms error: cannot receive media data (aborting)

I don't think I have a "slow computer" (see attachment)
And I think this "pulse error" must be pretty much the essence of the problem. Any ideas out there???

If (K)ubuntu is to become mainstream, it will have to cope with windows "advanced streaming/system format", because there are very many people out there who want to watch the news. Unless, of course, the broadcasters understand that sooner or later people are going to prefer Linux to Windows :-)

---

### Post by xc3RnbFO8P on 2009-12-05
In Synaptic Package Manager install **gecko-mediaplayer**
see if that works, if not you need to install some codec.

---

### Post by kle on 2009-12-07
> **Ringi said:**
> In Synaptic Package Manager install **gecko-mediaplayer**
see if that works, if not you need to install some codec.

In what way would Gecko be better than MPlayer? 
I believe I have already installed the relevant codecs (cf. above problem description).

---

### Post by xc3RnbFO8P on 2009-12-08
> In what way would Gecko be better than MPlayer?
MPlayer and Vlc gives me errors that I cant solve.
I can play all these link in Firefox.
This is how I install codecs (yes DVD to):
> sudo wget \
  --output-document=/etc/apt/sources.list.d/medibuntu.list \
  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list &&
sudo apt-get --quiet update &&
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get --quiet update
> sudo apt-get install libdvdcss2
> sudo apt-get install w32codecs
> sudo apt-get install libdvdread3
> sudo /usr/share/doc/libdvdread3/install-css.sh
> sudo apt-get install ubuntu-restricted-extras
in Synaptic Package Manager install:
flac
libfaad0
vorbis-tools
ffmpeg 4:0.5
gecko mediaplayer

---

### Post by Henrikx on 2009-12-08
Works with SMPlayer and Totem-Plugin (Firefox)

[Install Mplayer/SMPlayer ( by rvm)]("http://ppa.launchpad.net/rvm/testing/ubuntu/pool/")

---

### Post by kle on 2009-12-09
Thank you, Hendrikx, I shall try that out and return here within a day to let you know how it turned out (The pics you attached certainly were convincing enough!)

---

### Post by kle on 2009-12-09
I see from other discussions that Gecko is considered better than Mplayer. So is SMPLAYER. 

So I removed my old Mplayer, and installed new Mplayer2 and SMPlayer from launchpad (ppa or "rmv"). So far, so good. Then I needed the plugin. I tried Totem, but no go. I am not using Gnome and my Mozilla applications did not give me the option to use Totem for asf-streams, as yours obviously did.

So I am back to mozilla mplayer plugin, and the result is basically the same as it was, meaning that VLC is still the best option, but hnot good enough, 

Ringi: I shall try your Gecko solution next. But I will not be able to do so the next couple of days. I shall give it a try this weekend. 

Thanks, both of you! I will report the results.

---

### Post by kle on 2009-12-12
The solution proposed by Ringi:

sudo apt-get install libdvdread4
Result:
"Couldn't find package libdvdread4"
But I have libdvdread3 installed. 

Other than that, I followed your instructions, but the result is basically the same. One reason for that may be that while gecko is now listed as the plugin to be used for most kinds of files, mplayer remains the defined plugin for asf files. How do I change that? A dropdown list gives me only two options, none of them GEcko.

Now my question is how to change the default plugin. Help please!

---

### Post by kle on 2009-12-12
OK, now I discovered the "about:config" and the "about: plugins" 

The reason I do not get a Gecko option for the asf files is that Gecko does not support asf files. 

Mplayer does, at least in theory, but as I have described in my initial message it does so very poorly. 

I cannot get the smplayer to resolve the url, but VLC does, but stops playing after about 2 min. So I copied the resolved URL to smplayer, and IT DID NOT STOP! It has been transferring my stream without blinking for 5 minutes. 

Now this is a breakthrough!!!!

**SMPLAYER handles asf files**

Now, next question: How to resolve the URL without going through VLC? For instance:
[http://dagskra.ruv.is/sjonvarpid/streymi/4472081/](http://dagskra.ruv.is/sjonvarpid/streymi/4472081/)
resolves to
mms://http.0.muli.rs.ruv.is/video.ruv.is/4472081$1.wmv?MSWMExt=.asf
Are there any tools to do this?

---

### Post by kle on 2009-12-12
... **KMPLAYER resolves the URL **, **and plays the stream to the bitter end** (31 minutes without hesitation. 

I'll settle for that!

Thanks Ringi and Henrikx. 
It may well be that the procedure I used following Ringi's instructions gave me some codecs I wasn't aware of having missed. The only thing that was wrong there was the Gecko.

---

