---
title: "Streaming Audio"
date: 2014-07-04
forum: Multimedia Software
---

### Post by merlinus on 2014-07-04
I am wanting to stream cd rips and hd downloads from my computer to my sound system. I have a Wi-Fi network but would probably need at least a wireless bridge, since my processor does not have wireless capabilities.

The bridge would also need to have hdmi out capabilities to hook up with the processor, which already has built-in dacs.

Suggestions and recommendations greatly appreciated!

---

### Post by TheFu on 2014-07-05
There are many different ways to solve this issue. But since I don't understand some of your terms, I'll just guess.
A few cautions first - wifi that isn't a perfect connection will probably stutter for hidef video content.  Audio should always be fine on any wifi network with a good connection.  SD quality video should work find too over most wifi (DVD/480p).

So - the way that most people handle what you are asking is by getting a video playing device with wifi. Something like a chromecast, WDTV-line, or no-name Chinese models.  These all have pros/cons.  Chromecast mandates that google "watch" everything you playback. It really wants you to use internet content, not content inside your home already.  It will not work without an internet connection, I've tried.

So - the chromecast is $35 - it is also really, really, really picky about content.  That means your PC will need to have enough power to transcode videos on-the-fly.  Oh - and plex server will need to be installed.  I'd been screwing around with other software for years, it was a happy day when Plex Server was installed. It is the best DLNA server I've used.  Better than MS stuff.

Or you could build/buy a media center PC and connect that.  For SD content, this is easy. Any system in the last 5 yrs can handle it, but for 1080p stuff, you'll want GPU support.

Oh ... if you have a Playstation or Xbox - those can be used as playback devices for Plex too. As do many networked smartTVs and Bluray players. These all support DLNA.

So ... does that help?  Are there complexities that I missed?  What is the source system specs?

---

### Post by merlinus on 2014-07-05
Hi, and thanks for your response -- much appreciated!  I only want to stream audio (cd rips, and tracks extracted from youtube videos via audacity)  from my desktop computer to my sound system.  I have a wireless network, and need hdmi out from any device to my surround processor.

My computer is fairly powerful -- i7-3770 cpu @ 3.40 GHz x 8, 16G RAM, 80G SSD, 500G HDD, 2TB USB WD drive.  It resides in a different room from my sound system, so direct streaming is not possible.  My surround processor does not have built-in Wi-Fi nor USB.

Someone suggested Roku 3, and installing MediaTomb as a server, but I do not yet understand how that will actually stream the audio files to the device.

---

### Post by TheFu on 2014-07-05
mediatomb is a DLNA server, like Plex.
Ruko is a DLNA client, like chromecast, ps3/4, xbox, WDTV, smart-TVs, bluray players, any android device, ... all of these would be connected to the audio receiver.

The client and server would communicate over wifi ... just like any other laptop/server does.

With a Core i7 - I'd load up plex server and call it "done."  No need for any online plex account. I don't have one and it works great inside my LAN from many different DLNA clients.  

Whether your wifi network is fast enough for HD video ... I can't say. Too many variables.  I've designed wifi deployments for 1200+ locations - I use wired at home for every device that can possibly support wired connections.  Heck - my chromebook doesn't have an ethernet port, but does have a USB3 port - which gets a USB3/GigE adapter.  Wifi sucks in comparison.

To me, wifi != wireless.  Wireless is GSM/LTE and completely different.

---

### Post by merlinus on 2014-07-05
Thanks again for the info.  I am not wanting to stream video, only audio, so the speed of my wifi should not be an issue.  Wired connection would of course be best, as you say, but am not wanting to drill holes in walls and closet to run the cable from my desktop to the sound processor, which is in another room.

Is plex server in the repos, or???

And is there any way I can stream audio files directly to my sound processor via an hdmi cable, or do I need a device such as Roku?

---

### Post by TheFu on 2014-07-06
So - I don't know of any cheap audio-only solutions to your issue. Sonos (sp?) comes to mind, but it isn't cheap. Heck, "premium" doesn't describe how expensive they are either. If you have some other device near the stereo that is wifi (DLNA client or local media) and puts out audio over HDMI, then I think that should work too.  

You seem to think that wifi can be magically converted to HDMI and work.  Googled "wifi to hdmi" and the results were for $100-$1500+ solutions ... which means that a $35 chromecast would be much more cost efficient.  Does that make sense? If you go with a consumer-video-DLNA client for less than $80, I think it will do what you want for a reasonable price. Heck, you may want to stream video at some point too.

What do you mean by "sound processor"?  Is that a stereo or a receiver?  If you can stream to it - that would be a major feature and in the manual. I'd suspect it would have a built-in **DLNA client** and a network connection. Lacking a network port, I think not.  Obviously, if you have some device that has an HDMI output and you can get it to put sound down that cable, then a normal receiver will play it back.  But you didn't want to run an ethernet cable through the walls ... so I assumed you didn't want to run a much thicker HDMI cable either.  

I think plex server is in the software center.  My plex machine is only for that - so I was willing to install a .deb file directly from the plex team. It doesn't have much of a GUI on it (nor a keyboard or mouse). I manage it via ssh 99.9999999999% of the time.

Otherwise - no, you cannot magically wifi stream directly to hdmi. They aren't the same technology.  **When I see your bean count, it makes me think I'm missing something.** Am I?

I own these playback devices:
* mediagate 
* WD TV Live HD (non-netflix model)
* chromecast
* roku3
* PC running Ubuntu 12.04 w/ XBMC and Plex
* Android smartphone
* Android tablet
* any laptop running Win/Linux/OSX

To playback audio over hdmi, the chromecast is the cheapest answer. It requires an android device to control it and it will need to be configured when connected to a monitor, but moving it to a pure audio device should work ... I guess.  I don't have any receivers that work with HDMI inputs, sorry. 

I'm a video guy, so video output in hidef is a core requirement in my systems.  All of those devices are DLNA renderers (a client has more capabilities) except the mediagate. That means pushing audio to it from another device on the network is possible (if you allow it in the settings).

For all the time we've chatted here, you could have installed the Plex Server and tried it already. The install was fairly painless. Management is through a web interface ... [http://IP](http://IP) address to plex server:32400/web/
That should be enough for now.

---

### Post by tgalati4 on 2014-07-06
You could hook up a RaspberryPi and use that as your ethernet-to-HDMI audio solution:  [http://www.runeaudio.com/](http://www.runeaudio.com/)

I would drill holes and run an ethernet cable.  WiFi suffers from interference and will result in stuttering of high-bit-rate sources.

---

### Post by merlinus on 2014-07-06
@tgalati4 -- thanks for the suggestion, but I could not figure out from their website if I would still need some sort of device such as Roku.  I tried using my laptop with hdmi out into the surround processor and playing .wav files from Rhythmbox, but it did not work. 

Drilling holes and running a cat5 cable is not an option, because of the distance across the room from where my computer is located to the closet and wall inside it.  I have streamed videos via Kindle and hdmi with few or no problems using my wi-fi network.

---

### Post by merlinus on 2014-07-06
@TheFu:  Thanks hugely for your continuing assistance, advice, and interest -- much appreciated!

> **TheFu said:**
> So - I don't know of any cheap audio-only solutions to your issue. Sonos (sp?) comes to mind, but it isn't cheap. Heck, "premium" doesn't describe how expensive they are either. If you have some other device near the stereo that is wifi (DLNA client or local media) and puts out audio over HDMI, then I think that should work too.  

I tried using my laptop with hdmi out into the surround processor and playing .wav files from Rhythmbox, but it did not work.  I have used a Kindle to stream films from amazon via hdmi using my wifi network, however.

> You seem to think that wifi can be magically converted to HDMI and work.  Googled "wifi to hdmi" and the results were for $100-$1500+ solutions ... which means that a $35 chromecast would be much more cost efficient.  Does that make sense? If you go with a consumer-video-DLNA client for less than $80, I think it will do what you want for a reasonable price. Heck, you may want to stream video at some point too.

  I quite agree.  I am certainly amenable to purchasing a Roku 3 for about $90, and see whether it will work.  If not, amazon has a great return policy, including paying for return shipping.

> What do you mean by "sound processor"?  Is that a stereo or a receiver?  If you can stream to it - that would be a major feature and in the manual. I'd suspect it would have a built-in **DLNA client** and a network connection. Lacking a network port, I think not.  Obviously, if you have some device that has an HDMI output and you can get it to put sound down that cable, then a normal receiver will play it back.  But you didn't want to run an ethernet cable through the walls ... so I assumed you didn't want to run a much thicker HDMI cable either.  

 I have a Classe SP-800 processor for audio and video.  It has hdmi inputs which I use for my video player and Kindle, but does not have a built-in DNLA client of any kind, and no ethernet nor usb inputs.  I use xlrs from my sacd player to it.

As stated above, for some reason it would not work with my laptop.  I have emailed Classe in hopes of finding out why.  Perhaps it is Rhythmbox (which I used for playing the .wav files from the computer), or perhaps the unit will only recognize disc-type material, or streaming video such as films from amazon via Kindle.

> I think plex server is in the software center.  My plex machine is only for that - so I was willing to install a .deb file directly from the plex team. It doesn't have much of a GUI on it (nor a keyboard or mouse). I manage it via ssh 99.9999999999% of the time.

I have installed plexmediaserver, and got it running in my web browser.  But it is probably of no use until I purchase a DLNA-capable unit.

> Otherwise - no, you cannot magically wifi stream directly to hdmi. They aren't the same technology.  **When I see your bean count, it makes me think I'm missing something.** Am I?

 When Ubuntu 7.04 first came out, I ditched Windows and have never looked back.  Most of my beans are from those earlier days, when I was very involved with the forum in terms of helping out with questions about installation, grub, connecting HDs, and such.  Since Canonical has moved to Unity, I have kind of dropped out of sight.  My 12.04 installs use the fallback to Gnome 2.

---

### Post by TheFu on 2014-07-06
Ah ... it is a 7.1 preamp.  Did you force the Ubuntu mixer to output to the HDMI? Has that worked before on the system?
WAV files are probably 2 channel. Have you tried audio with 2, 3, 4, 5, 6, 7, 8 channels?  And raw, DTS, and DD encodings?

I'd test with and without HDCP too.  The roku3 has HDCP on everything, even content that shouldn't be protected.  You may need "other solutions" to get around that aspect too.

As to Unity - that is easily solved.  Just load one of the alternate DEs or a pure WM setup and run with that.  5 minutes after the install and you'll never need to see Unity again.

You can stream videos/audio through the plex web interface from any machine on the LAN.  No DLNA needed.  Just an option.  BTW, out of all the options that I've listed, the Roku is my least used. I dislike the HDCP on all content when it isn't required.  Nothing on NASA TV should be HDCP.  Plus it makes splitting the video and audio to different hardware difficult for absolutely no good reason.  My setup needs connections to a TV, projector, and optical audio THX receiver. I don't want the TV audio return, which down samples to 2.1 audio and can't use audio return on the projector due to cabling complexity.  I am NOT a fan of roku3 hardware for those reasons.

---

### Post by merlinus on 2014-07-06
I did change the system sound setting to use the hdmi output, but this was the first time I tried using the laptop as a source for AV.  I only tried the 2-channel .wav files, since just about all of my audio is in cd or sacd format.

Glad you mentioned HDCP on the Roku.  That makes it a no-brainer, for me, as I cannot in good conscience support such piggish principles!  But chromecast does not sound any better -- sigh.

 As for Unity, as I wrote, I use the fallback to gnome 2 on my four machines.  Not interested in touchscreen and smartphone-type icons!  I much prefer dropdown menus and launchers on the top toolbar.

 Since it seems any android unit will work with plexmediaserver, perhaps I can use the Kindle???

 Also, will plex autodiscover network clients?  The Kindle is connected to the wifi, but I do not see it in plex.  Are there other things I need to activate?  I did notice that plex wanted me to sign in or create an account.  Is that necessary in order for it to work?

Thanks again for your expertise and willingness to help out!

---

### Post by TheFu on 2014-07-06
Any consumer-level device with HDMI sold inside the USA will include HDCP.  

The best solution I know is to avoid HDMI for audio completely and use either digital coax or digital optical connections.  

I don't know anything about your preamp or the limitations it may or may not have. Sorry.

---

### Post by merlinus on 2014-07-06
The processor has both digital coax and toslink inputs.  What sort of device might have these outputs?

---

### Post by TheFu on 2014-07-07
Google found this: [http://www.amazon.com/Play-Media-Player-2013-Model/](http://www.amazon.com/Play-Media-Player-2013-Model/)

I suspect the content providers are forcing hardware makers to only have HDMI outputs - trying to close the "analog hole" as they see it.

---

### Post by tgalati4 on 2014-07-07
Since you have audiophile equipment, I would look for an audiophile streaming solution: [http://www.element14.com/community/community/raspberry-pi/raspberry-pi-accessories/wolfson_pi](http://www.element14.com/community/community/raspberry-pi/raspberry-pi-accessories/wolfson_pi)

Some reviews:  [http://www.element14.com/community/thread/32445/l/my-review-of-the-wolfson-audio-card](http://www.element14.com/community/thread/32445/l/my-review-of-the-wolfson-audio-card)

---

### Post by merlinus on 2014-07-08
> **TheFu said:**
> Google found this: [http://www.amazon.com/Play-Media-Player-2013-Model/](http://www.amazon.com/Play-Media-Player-2013-Model/)

I suspect the content providers are forcing hardware makers to only have HDMI outputs - trying to close the "analog hole" as they see it.

Unfortunately the link you provided leads to an error page.  But yes, it would seem that everything these days is hdmi, except top-dollar so-called "audiophile" gear which has coax, optical, and xlr outputs.

Given what you wrote about Roku and chromecast, they are not on my list, so the search for a usable, low-cost solution continues.

---

### Post by merlinus on 2014-07-08
> **tgalati4 said:**
> Since you have audiophile equipment, I would look for an audiophile streaming solution: [http://www.element14.com/community/community/raspberry-pi/raspberry-pi-accessories/wolfson_pi](http://www.element14.com/community/community/raspberry-pi/raspberry-pi-accessories/wolfson_pi)

Some reviews:  [http://www.element14.com/community/thread/32445/l/my-review-of-the-wolfson-audio-card](http://www.element14.com/community/thread/32445/l/my-review-of-the-wolfson-audio-card)

Thanks for the info.  I am looking for an easy solution. This seems like overkill for my needs, to say nothing of the challenges to set it up.

The vast majority of my audio is cd or sacd, and I am not into downloading HD albums, at least for now.

---

### Post by TheFu on 2014-07-08
Sorry about that link, I was trying to remove the tracking data in the URL and took a little too much. It was the "2013 WD Play Media Player" for about $60. Odd that Amazon search couldn't find it with just those original terms. At least it didn't work for me either.  I have an older model and it works silently and as a DLNA client, we can "play to" it.

---

### Post by merlinus on 2014-07-08
I found this one:

[http://www.amazon.com/gp/product/B005KOZNBW/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=ATVPDKIKX0DER](http://www.amazon.com/gp/product/B005KOZNBW/ref=ox_sc_act_title_1?ie=UTF8&psc=1&smid=ATVPDKIKX0DER)

It has optical out as well as hdmi, and may not even need plexmediaserver.

What are your thoughts?  Thanks!!!

---

### Post by TheFu on 2014-07-08
That is the newer version, right?  If it is only used for audio (not connected to any video output device), then without a DLNA server, you will not be able to tell the media where to play.  Does that make sense?  There is a GUI on the WD device and controlling it without a display will be nearly impossible.  By using the DLNA client/renderer capabilities and a DLNA server, you can use another tool to send media at it.  Do you have a way to do that - any android device will work.

Of course, if it is connected to a monitor or TV, you can use the remote to select media from NFS or CIFS shared storage or any DLNA server.

Plex isn't the only DNLA server. Feel free to try all the others. I've tried 3-4 others over the years and have found plex to be the easiest, most impressive solution.

Of course, if you do buy that device, I'm not responsible if you don't like it. ;)  It isn't perfect (neither is the version I have).  The more I think about this, the more I feel like using my WDTV device as a streaming endpoint just for audio too. Need to move some connections around to test it.

---

### Post by merlinus on 2014-07-08
I believe this is the newer model, but not the expensive one with built-in HDD, etc.  My partner's Google smartphone is android-based, and so is Kindle, so they may work to control the WD, although I could not get plex to recognize the Kindle.

The optical out might be the best bet, in terms of sending the audio to my surround processor.  And if it does not work for my uses, I can send it back to amazon.

Look forward to hearing your experience in hooking up your WD as an audio streamer.

---

### Post by TheFu on 2014-07-08
> **merlinus said:**
> Look forward to hearing your experience in hooking up your WD as an audio streamer.

Ok - stole the audio output from my HTPC for 20 minutes and connected up my "[WD TV Live HD]("http://www.amazon.com/Live-Plus-1080p-Media-Player/dp/B003MVZ60I/")" ($65 new back then). The ethernet connection uses 100base-TX, not wif, though the entire network is GigE, the WDTV is only 100Mbps. Plenty of bandwidth for 1080p video.  No monitor was connected, just the audio to test what I believe will be your config.

There is an Android app from WD for the device, but it is like the remote ... no local visual feedback at all - monitor/TV needed to be of any use. The WD had to be powered on by the included remote, but after that, it showed up on the network as a UPnP DLNA client inside the **BubbleUPnP Android app** (Free).  Now I was off looking for a DLNA server on the network .... found 5 being offered:
* Local
* Plex (photos and video/movies/TV - no music)
* XBMC (same physical machine as the Plex "server")
* a few Win7 machines

Selected the "local" DLNA server and traversed down to the music stuff ... this was all inside the BubbleUPnP from a Nexus4.  Selected U2 - B-sides Greatest .... then "Enqueue and play" .... 

Then ....




....



....



It started playing.  Sounds great - well, as good as this stereo ever sounds with 192Kbps mp3 files through my cheap Infinity speakers.  Thanks for reminding me how much better the Thiels in the other room sound. Gee - thanks. ;)

Ok - the next track played, so the queuing works ... but there is a limited number of tracks that can be queued in the free app. I really need to pay for Bubble... app for all it does.  BTW, the queuing works with video/TV/movies too. Oh - and the volume control on Android controls the volume for the music. No need to enable UPnP on your router - on the same LAN, this stuff "just works."

Now I need to get my music collection "inside" plex's DB. I recall the web-admin pages having that ... just need to make the access to those files over the network seen by Plex.

So - summary is that it works. Three devices included:
* DLNA Server - my Android phone, but this could any from the list above.
* DLNA "Renderer" - WD TV
* DLNA Client - my Android phone (this could also have been the "renderer".

Good luck - enjoy.

---

### Post by merlinus on 2014-07-08
Great that it worked at all!  I am wondering if the renderer (e.g. WD, Kindle) needs to have a resident app of some sort in order for it to be detected by plex?  Or should discovery be automatic?  

I am asking because my Kindle has wifi and is connected all the time to my network, but does not show up in plex.

---

