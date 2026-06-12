---
title: "Radio Streaming Problem"
date: 2009-01-28
forum: Multimedia Software
---

### Post by satans aunt on 2009-01-28
Relatively new to Ubuntu but still very much enjoying the experience.

My only complaint is that I didn't take to it sooner.


Anyhow, 

My problem today is that I can't currently stream live radio from Classical FM.

So far this has been the only radio stream with which I have had a problem

To clarify, a pop emerges calling for player capable of playing Windows Media content (i.e. Mplayer- which I have).

I ran a search and found a post from 2007, sadly there was no solution to the problem to be found then. I'm hoping that someone here can help me.



Thanks

---

### Post by Metaljaz on 2009-01-28
Well i couldn't get it to work for me either and I have mplayer installed as well. I installed the gstreamer plugins and all is good now:

Go to Applications>Add/Remove
select the all available applications at the top and click the following:
gstreamer plugins for mms, wavpack,quicktime,musepack
gstreamer plugins for ffmpeg video plugin
gstreamer plugins for extra plugins

That should do it.

---

### Post by birddog165 on 2009-01-28
For my radio, I stream online .m3u files on my screenlet app called "Radio"

---

### Post by satans aunt on 2009-01-28
I already have all the necessary plugins.

I tried a reinstall, just to be sure, no change.

---

### Post by andrew.46 on 2009-01-28
Hi satans aunt,

> **satans aunt said:**
> 
My problem today is that I can't currently stream live radio from Classical FM.

Can you give an address for this stream?

Andrew

---

### Post by kostkon on 2009-01-28
Do you have the windows codecs package that is provided by the [*Medibuntu*]("http://medibuntu.org/") repository (called *w32codecs* for 32 and *w64codecs* for 64bit systems) installed?

But, yes, it would be good if you could give the url of the stream (or url of the site, etc.) to us in order to check if it plays ok on our systems or not.

---

### Post by satans aunt on 2009-01-29
Apologies for not including the url in the initial post.

Here's the url for the pop-up that should contain the streamed content- [http://mediaweb.musicradio.com/player/default.asp?s=2&e=0](http://mediaweb.musicradio.com/player/default.asp?s=2&e=0)

Classic FM- [http://www.classicfm.co.uk/Default.asp#](http://www.classicfm.co.uk/Default.asp#) (in case the above doesn't work, look for the listen live option)

Thanks


P.S.
Have installed the w32codecs.

---

### Post by kostkon on 2009-01-29
Actually, the url of the stream is the following
```
http://mediaweb.musicradio.com/Playlist.asx?StreamID=2
```
Nevertheless, if you press *Listen Live* a pop-up indeed appears that says:
>  From what we can tell, you are accessing our player using a computer that is running a version of Linux. To enjoy our Listen Live service, you'll need to have a media player capable of playing Windows Media content installed. One such player is MPlayer, further details can be found here.
but also says:
> If you already have a compatible player installed, click here to access the audio / video you've requested.
thus, what happened when you clicked the *Click Here* link?

I have *Totem-Xine*, the *Totem Firefox* plugin and the *w32codecs* and when I pressed the link I could play the stream just fine.

Thus, since you are using *Mplayer*, make sure that you have the windows codecs (i.e. the *w32codecs* or *w64codecs* package from the [*Medibuntu* repository]("http://medibuntu.org/"). Instructions on how to add this repository to your sources list are [here]("https://help.ubuntu.com/community/Medibuntu")) and also install the *Mplayer Firefox* plugin (the package is called *mozilla-mplayer*).

Then try again. 

You can obviously, either select the *Listen Live* option on the page and then the *Click Here* link in the pop-up or try to use the url of the stream directly, if you want.

---

### Post by andrew.46 on 2009-01-29
The svn Mplayer can play this stream directly:

```

andrew@skamandros:~$ mplayer -playlist http://mediaweb.musicradio.com/Playlist.asx?StreamID=2
MPlayer SVN-r28378-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
[.... *[COLOR="Red"]snipping a lot of searching[/COLOR] *.....]
Connecting to server mediasrv-the.musicradio.com[81.20.48.50]: 80...
Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Audio stream found, -aid 2
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16002->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


```

Andrew

---

### Post by satans aunt on 2009-02-01
Thanks for all your help guys.

Finally have it working-

However, if you look closely the working url is different from the url provided if you select the listen live option from the classical.fm website:

[http://img159.imageshack.us/img159/4046/screenshotplaylistasxvicy5.png](http://img159.imageshack.us/img159/4046/screenshotplaylistasxvicy5.png)


Here's the what I get when I click the listen live option...

[http://img159.imageshack.us/img159/3255/screenshotclassicfmwebplq5.png](http://img159.imageshack.us/img159/3255/screenshotclassicfmwebplq5.png)


It would appear that I had all of the necessary plugins but was provided with the wrong url.

---

