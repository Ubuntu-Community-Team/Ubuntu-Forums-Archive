---
title: "Movie Player and WMA"
date: 2010-06-29
forum: Multimedia Software
---

### Post by sgt.bilko on 2010-06-29
Hi all - this is my first post, hope you can help

I have 2 very similar boxes both using 10.04 amd64.

On box-1 I get an error when trying to play a wma file using Movie Player..

[B]The playback of this movie requires a Windows Media Audio 8 decoder plugin which is not installed.
[/B]

On box-2 it plays correctly, so i'm trying to find the difference.

I have the following gstreamer plugins installed ..

howard@amd-64:~$ dpkg -l gstreamer*|grep ii|awk '{print $2}'
gstreamer-tools
gstreamer0.10-alsa
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-plugins-mp3-partner
gstreamer0.10-gnonlin
gstreamer0.10-nice
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-pulseaudio
gstreamer0.10-tools
gstreamer0.10-x


Also, looking on box-1 ....

howard@amd-64:~$ gst-inspect | grep wma 
typefindfunctions: video/x-ms-asf: asf, wm, wma, wmv



but on box-2 ...

howard@Big-Bertha:~$ gst-inspect | grep wma
ffmpeg:  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
ffmpeg:  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
typefindfunctions: video/x-ms-asf: wmv, wma, wm, asf


Is this the difference that enables box-2 to play wma??

If so, how do i get the missing ffmpeg components onto box-1?

Thanks

Bilko

---

### Post by mc4man on 2010-06-29
when you installed the gstreamer0.10-ffmpeg plugin it would have installed several ffmpeg shared libs, so box 1 should decode the wma files you have.
(nothing special is needed for wma1, wma2
I guess you could search ffmpeg and d. check on libavcodec52, libavutil49, ect.

you could try a restart unless already done/

Was box 1 an upgrade from karmic? 
(if so, remove any unstripped versions of ffmpeg libs if any are installed and re-install the others

Otherwise you could add the gstreamer dev ppa, it's gstreamer0.10-ffmpeg plugin uses  builtin ffmpeg libs, and adds some wma decoding - basically all wma except wmal 

Ex. on lucid with ppa gstreamer plugins
> doug@doug-desktop:~$ gst-inspect | grep wma 
ffmpeg:  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder
ffmpeg:  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
ffmpeg:  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder


The ppa is here
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Note - their signing key doesn't work atm - doesn't matter - just creates a warning when updating
If using I'd do the updates from synaptic - not the update manager and on 64 bit the updated gstreamer-tools may produce an error, still works though or just don't update it.

---

### Post by sgt.bilko on 2010-06-29
Excellent - looks like you fixed it.

I had libavcodec-extra-52, libavutil-extra-49 but not libavcodec52, libavutil49.

Installed those - it also removed vlc, picard, mplayer but i guess i can re-install those later.

I now get this on box-1:

howard@amd-64:~$ gst-inspect | grep wma
ffmpeg:  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
ffmpeg:  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder
typefindfunctions: video/x-ms-asf: asf, wm, wma, wmv


And box-1 now behaves like box-2  

Also, Soundconverter and Rhythmbox no longer search for missing codecs. 

All is well with the world.

I was going crazy with this and you sorted it in an hour - brilliant.

Many thanks

Bilko

---

### Post by mc4man on 2010-06-29
If you decide you need the extra versions of the ffmpeg libs ( mainly add encoding support, not decoding) you should be able to use them now with no issue.

To do so I'd first go 
```
sudo apt-get clean && sudo apt-get update
```

Then open synaptic, search ffmpeg and just mark the extra versions for install - don't mark the current ones for removal. Click apply and there should be no issue.

(if in the future you need wma3(pro) and or wmas(voice) on lucid then remember the ppa - support for those wma's will be enabled by default in maverick

---

### Post by Cavsfan on 2010-06-30
I have added the PPA and gotten the updates:

gst-inspect | grep wma
ffmpeg:  ffenc_[COLOR=Red]wma[/COLOR]v1: FFmpeg Windows Media Audio 1 encoder
ffmpeg:  ffenc_[COLOR=Red]wma[/COLOR]v2: FFmpeg Windows Media Audio 2 encoder
ffmpeg:  ffdec_[COLOR=Red]wma[/COLOR]pro: FFmpeg Windows Media Audio 9 Professional decoder
ffmpeg:  ffdec_[COLOR=Red]wma[/COLOR]v1: FFmpeg Windows Media Audio 1 decoder
ffmpeg:  ffdec_[COLOR=Red]wma[/COLOR]v2: FFmpeg Windows Media Audio 2 decoder
ffmpeg:  ffdec_[COLOR=Red]wma[/COLOR]voice: FFmpeg Windows Media Audio Voice decoder
typefindfunctions: video/x-ms-asf: asf, wm, [COLOR=Red]wma[/COLOR], wmv

All of the above places where "wma" is displayed is red as it shows.

But, I still cannot play WMA files either in RhythmBox or in Movie Player.

RhythmBox just doesn't do anything if I try to play a WMA song and the default movie player gets
this error after it asks to search for plugins:

No packages with the requested plugins found
The requested plugins are:
Advanced Streaming Format (ASF) demuxer

Any clues?
Thanks

---

### Post by sgt.bilko on 2010-06-30
I marked the 'extra' versions for installation but synaptic wanted to remove the standard versions first. Looks like you can only have one or the other??

It's ok though I'll leave things as they are. The main issue was to get Soundconverter & Rhythmbox handling wma. 

Thanks again for your invaluable help.

Bilko

---

### Post by Cavsfan on 2010-06-30
> **sgt.bilko said:**
> I marked the 'extra' versions for installation but synaptic wanted to remove the standard versions first. Looks like you can only have one or the other??

It's ok though I'll leave things as they are. The main issue was to get Soundconverter & Rhythmbox handling wma. 

Thanks again for your invaluable help.

Bilko

Sgt, are you implying that I need to start my own thread or something? I have the exact same problem
and accomplishing the above steps has not fixed my problem with Rhythmbox playing WMAs.

I have libavcodec-extra-52, libavutil-extra-49 installed.

Also, I am wondering what it means that wma is displayed as [COLOR=Red]red[/COLOR] in my output above?

---

### Post by Cavsfan on 2010-06-30
Rhythmbox is now asking for the Advanced Streaming Format (ASF) demuxer plugin.
I have tried everything. I'll apparently have to convert the WMAs to MP3s.

---

### Post by mc4man on 2010-06-30
@ Cavsfan
It would be nice if there was a sample of the wma you're trying to play or at the very least identify the type of wma it is.

If you'd like go here, download a sample and try to play in a gstreamer player

wma3(pro
[http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/](http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/)

wma2 audio with wmv3 video - (in totem
(the weekend.wmv will do
[http://samples.mplayerhq.hu/A-codecs/WMA2/](http://samples.mplayerhq.hu/A-codecs/WMA2/)

Now as a test before playing these I removed libavcodec52 from system
> Commit Log for Wed Jun 30 15:27:56 2010

Removed the following packages:
gpac
gstreamer0.10-plugins-bad-multiverse
libavcodec-dev
libavcodec52
libavdevice-dev
libavdevice52
libavfilter-dev
libavfilter1
libavformat-dev
libavformat52
libmjpegtools-1.9
libquicktime1
libsox-fmt-all
libsox-fmt-ffmpeg

I can still play wma2, wma3(pro, and wmv3

---

### Post by Cavsfan on 2010-06-30
Wow! I downloaded [COLOR=Navy]theweekend.wmv[/COLOR] and it played flawlessly in Movie Player and in Rhythmbox.

Then I downloaded [COLOR=Navy]ffwma2_broken.wma[/COLOR] with the exact same results.

I was trying to play an Alice In Chains song that I had converted from a CD to MP3 and WMA.
The codec says: WMA Version 8 on both files.

The only difference between the one that works and the one that does not is the sample rate and the bitrate.
At least on the file properties that is. The one that does not play is twice the sample rate (44100 Hz) and 
bitrate (65 kbps) of the one that does work (22050 Hz and 22 kbps).

So, what does that tell us? Could it be that the bitrate/sample rate is just too high?
BTW my WMA was created on Windows 7 a while back.
Thanks for your help!

---

### Post by Yellow Pasque on 2010-06-30
Open rhythmbox in the terminal and try to play the song.
EDIT: BTW, that's a really low bitrate. Is there a reason you need it that compressed?

---

### Post by Cavsfan on 2010-06-30
That must be the whole problem! I went into windows 7 (the only way I know of) and converted 
the same MP3 file into a WMA with half the bitrate and half the sample rate and it works great.

With MP3s I like sample rate of 44100 Hz and bitrate of 320 kbps, but because that makes
huge files MP3 players will not hold near as many songs... You probably already know this...

So, Rhythmbox can handle any and all MP3s I can throw at it, but it will only handle low quality WMA files? 
If that's true I can live with that. At least WMAs work and my hearing is not close to perfect anyway!

Is this the answer?
Thanks!

---

### Post by Cavsfan on 2010-06-30
> **Temüjin said:**
> Open rhythmbox in the terminal and try to play the song.

It worked! With the high bitrate and all!

---

### Post by Cavsfan on 2010-06-30
I take that back. It will not open it.

---

### Post by mc4man on 2010-06-30
> .....it played flawlessly in Movie Player and in Rhythmbox.
Plus now you'll also get wmap and wmas decoding if need be. 

As far as your file - " The codec says: WMA Version 8"
That seems a bit curious coming from windows 7 - wma 8 hasn't been used in quite some time.

I don't have win 7, but my son does if you wish to describe what you did I can try to duplicate.

Otherwise - here is a sample of a wma 8 (notice date), used the bangles... to test, I've not doubt you could decode.
[http://samples.mplayerhq.hu/A-codecs/WMA/](http://samples.mplayerhq.hu/A-codecs/WMA/) 

If you also wish mediainfo is quite handy to identify A/V files - if so easiest is to add this ppa
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

Then start mediainfo from Sound & Video menu, drop your file into it.
Then switch the view to HTML for more info and or Text to copy from


Edit : I remember in wmp you can 'protect' your files - you didn't inadvertently do so..?
test

---

### Post by Yellow Pasque on 2010-06-30
> I take that back. It will not open it.
Terminal output please..

---

### Post by Cavsfan on 2010-06-30
> **Temüjin said:**
> Terminal output please..

It wil not open the higher quality WMA, but it will the lower quality one.

I am just typing in "Rhythmbox" into the terminal, it opens and below is what is displayed.

```
@cavsfan-desktop:~$ rhythmbox
** (rhythmbox:4965): DEBUG: Loading the real store page
** (rhythmbox:4965): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

(rhythmbox:4965): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:4965): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:4965): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:4965): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:4965): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:4965): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=480&partner=983

```

---

### Post by Cavsfan on 2010-06-30
> **mc4man said:**
> Plus now you'll also get wmap and wmas decoding if need be. 

As far as your file - " The codec says: WMA Version 8"
That seems a bit curious coming from windows 7 - wma 8 hasn't been used in quite some time.

I don't have win 7, but my son does if you wish to describe what you did I can try to duplicate.

Otherwise - here is a sample of a wma 8 (notice date), used the bangles... to test, I've not doubt you could decode.
[http://samples.mplayerhq.hu/A-codecs/WMA/](http://samples.mplayerhq.hu/A-codecs/WMA/) 

If you also wish mediainfo is quite handy to identify A/V files - if so easiest is to add this ppa
[https://launchpad.net/~shiki/+archive/mediainfo]("https://launchpad.net/%7Eshiki/+archive/mediainfo")

Then start mediainfo from Sound & Video menu, drop your file into it.
Then switch the view to HTML for more info and or Text to copy from


Edit : I remember in wmp you can 'protect' your files - you didn't inadvertently do so..?

I did not protect the files.
I do not even remember which way I ripped the CD, but I have Alice In Chains SAP CD and ripped it to 
MP3 files then used some free software to make the WMAs from the MP3s.

Do you think I still need to do what steps you are saying?
Thanks!

---

### Post by Yellow Pasque on 2010-06-30
> **Cavsfan said:**
> It wil not open the higher quality WMA, but it will the lower quality one.

I am just typing in "Rhythmbox" into the terminal, it opens and below is what is displayed.

```
@cavsfan-desktop:~$ rhythmbox
** (rhythmbox:4965): DEBUG: Loading the real store page
** (rhythmbox:4965): DEBUG: navigation requested to https://one.ubuntu.com/music/store-no-token

(rhythmbox:4965): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:4965): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:4965): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer

(rhythmbox:4965): GLib-GObject-CRITICAL **: g_signal_handlers_unblock_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(rhythmbox:4965): Rhythmbox-CRITICAL **: rb_property_view_set_selection: assertion `RB_IS_PROPERTY_VIEW (view)' failed
** (rhythmbox:4965): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=480&partner=983

```

Ok... now try to play the file in question and then post the terminal output.

---

### Post by Cavsfan on 2010-06-30
> **Temüjin said:**
> Ok... now try to play the file in question and then post the terminal output.

rhythmbox will not open the file in question... the terminal output does not change.

---

### Post by Cavsfan on 2010-06-30
This keeps getting more peculiar. I just opened another WMA that is WMA Version 8, 48000 Hz sample rate and bitrate of 96 kbps. 
It works great. It could be the WMAs from that one CD is my problem. 

I don't think I've ever been able to play WMAs Before now, so adding those codecs must have made the difference.

I am satisfied with what I have learned and I should not have taken over the OP's thread and for that I apologize.
The OPs issue is resolved. I am content. This thread can be resolved if the OP wants.

Thank you all for your expertise!

---

### Post by mc4man on 2010-06-30
> It could be the WMAs from that one CD is my problem.
Undoubtedly - i'd just re- rip and encode the cd.

If you wish a small filesize use ogg or mp3
(honestly any encoder that's using wma8 is seriously outdated..

---

### Post by Cavsfan on 2010-06-30
Just an FYI - I brought up windows 7 - windows media player and ripped the CD.
Windows 7 file properties does not show the codec, so I am back on Ubuntu (my
favorite of course) and looking at the properties it says codec "WMA Version 8".

So, apparently Windows 7 professional 64 bit still uses that codec. And I hate windows media player with a passion.
I never use it, but thought that would yield the best rip (maybe). And I ripped it at a high
bitrate and sample rate and it plays great. So, that one batch of WMAs must have indeed caused my problem.

Like I said I could not previously play WMAs period, so what help you all provided worked and I do appreciate it!

Thank you! :guitar:

---

### Post by mc4man on 2010-06-30
Out of curiosity - 

with default settings in wmp (win7) the resulting wma is not wma8, but the r.click -> properties -> audio in nautilus will incorrectly report it as so 
Actually is 
 
> Format                           : WMA
Format version                   : Version 2
Codec ID                         : 161
Codec ID/Info                    : Windows Media Audio
Description of the codec         : Windows Media Audio 9.2 - 128 kbps, 44 kHz, stereo 1-pass CBR

---

### Post by Cavsfan on 2010-07-01
> **mc4man said:**
> Out of curiosity - 

with default settings in wmp (win7) the resulting wma is not wma8, but the r.click -> properties -> audio in nautilus will incorrectly report it as so 
Actually is
> 
                                                 Format                           : WMA
Format version                   : Version 2
Codec ID                         : 161
Codec ID/Info                    : Windows Media Audio
Description of the codec         : Windows Media Audio 9.2 - 128 kbps,  44 kHz, stereo 1-pass CBR                      

This morning I got some gstreamer updates. Now the WMA files that did not work yesterday work fine today!

So, if nautilus incorrectly reports the codec, where else can you see the codec?
(as you displayed above) And why is WMA red in the output of  "gst-inspect | grep wma"?
Is it because of the "grep wma" part or wma's incompatibility with Ubuntu?
Thanks

---

### Post by mc4man on 2010-07-01
> where else can you see the codec?

From post 15
> If you also wish mediainfo is quite handy to identify A/V files - if so easiest is to add this ppa
[https://launchpad.net/~shiki/+archive/mediainfo](https://launchpad.net/~shiki/+archive/mediainfo)

Then start mediainfo from Sound & Video menu, drop your file into it.
Then switch the view to HTML for more info and or Text to copy from


(This may all be drifting off topic, a new thread would be appropriate
-  I take 'red' as a highlight of what was grepped

---

### Post by Cavsfan on 2010-07-02
Thanks! Took me forever to get the key! I think I am getting lame(r).
The WMA that didn't work, but now does is WMA Version 2.

Thanks for all of your help. I will not post anything else to the OPs thread.
I think we are all satisfied. I hope the OP resolves this thread.

Thanks again!

EDIT: When I clicked on view HTML it showed a video aspect in the file. 
I don't know why as it was an MP3 with no video. 
But, that must be where the version 8 was coming from.

Video 
ID : 2 
Format : WMV2 
Codec ID : WMV2 
Codec ID/Info : Windows Media Video 8 
Description of the codec : Windows Media Video V8

---

