---
title: "Pulseaudio and Apple Airport Express AirTunes client mode"
date: 2010-03-21
forum: Multimedia Software
---

### Post by karhulitos on 2010-03-21
Hi,

I think I have now tried everything and searched everywhere.

Use case:
- I have a working wlan/internet with a ZyXEL adsl/router
- I've always wanted to stream music from this laptop to my stereo
- until now I realized AirPort Express (AEX) can do it
- As I already have internet, I'd like to connect AEX as a client to existing network and use it just as a sound server connected to my amp

Problem:
- pulseaudio (right click speaker icon on tray -> select settings) can see AEX if I configure it as an **wifi access point**
- pulseaudio does not detect AEX if it's in **client mode** in existing network

Any hints how I could tell (IP addr or something else) to pulseaudio to see my AEX in client mode?

---

### Post by karhulitos on 2010-03-22
OK, talking with myself.. guess there's noone wanting to stream audio to stereo with AirPort Express. Or everyone else has it running like a Buick.

I heard from colleague that encrypted wlan causes this in pure Apple setup as well, iTunes cannot see AEX unless wlan is unencrypted. Need to do a test setup with unsecure wlan to see.


[edit] it didn't work in totally unencrypted network either :(

---

### Post by karhulitos on 2010-03-25
If someone tries to find same answer, here's a hint: sudo restart avahi-daemon
and I can hear music while AEX is client to existing wlan.

Not completely solved but getting closer!

---

### Post by karhulitos on 2010-04-10
Still talking to myself. Intermediate report: with cable connection between lappy <--> AEX I can hear clear sound, but only with Amarok. Exaile and Rhythmbox cuts/stutters music so badly that it's useless. Must be some Pulseaudio setting to get it to talk to AEX in smoother way.
Actually, Amarok stutters also in the beginning of playing but it magically "synchronizes" the stream and I get no more cuts in that same Amarok playing session.

---

### Post by bdaman80 on 2010-04-17
I am unable to stream to my airport express, unless using my VBox-Win7-iTunes.  And that setup plays pack better than itunes trying to play over the native ubuntu alsa driver.  The sound is choppy when trying to play over my laptops built in speakers. Let me know what you find out

---

### Post by karhulitos on 2010-04-19
> **bdaman80 said:**
> Let me know what you find out

I think AEX in music streaming use case is too rare, so I nowadays monitor [http://pulseaudio.org/ticket/495#comment:23]("http://pulseaudio.org/ticket/495#comment:23"). Post 23 suggests 802.11n model is too new.. :(

---

### Post by freddez on 2010-04-23
As suggested here : [http://pulseaudio.org/ticket/495#comment:18](http://pulseaudio.org/ticket/495#comment:18) , I've  switched to wicd and removed network-manager. Works prefectly now (I'm on lucid)
Fred.

Ps : I've also switched from discontinued linux song bird to banshee wich has perfect itunes library import support.

---

### Post by karhulitos on 2010-04-23
Interesting.. for test, I stopped network-manager (I assume that is same what you do by replacing it with wicd) for testing purposes. I've cable connection to AEX at the moment. Music from Amarok to AEX is ok, no skipping (except in the start, once it got 'synced' it's flowing fine). Stopping Amarok and trying with Exaile or Rhythmnbox -> sound skipping/stuttering just the same as with network-manager. What on earth Amarok does differently? Phonon?

Freddez, you're running 802.11n version of the AEX?

---

### Post by RENOO on 2010-05-12
Hi there,

I am desperately trying to stream Amarok to AEX with no success. Following your post, I tried to use wicd instead of knetwork-manager ( I'm using KDE ) but it doesn't change anything.
I tried to use my existing network or configure a separate wireless network using AEX but still the sound playing out of the amplifier speaker is very bad.

I have found this blog. It seems this french guy could make it. 
[http://geekboy.fr/apple/utiliser-une-borne-airport-express-depuis-ubuntu/](http://geekboy.fr/apple/utiliser-une-borne-airport-express-depuis-ubuntu/)
But he doesn't say much about its network.

I hope someone could solve this. It makes me nervous hearing this ugly sound

Tell me if I can be of any help ( like translating the french blog )

Cheers

---

### Post by karhulitos on 2010-05-16
This is a bit off topic but I need to report this. With AEX I got kind of final verdict, it won't power on all the time any more. I found many threads telling that AEX power supply unit has a component that is prone to fail. Mine still powers on 1 out of 10 tries but that added to the sound problem led me to place Airport Express to a drawer with tons of old chargers and things. Maybe bad connection internally. I don't care. My first and last Apple product.

Then the good news. Local milk shop here offered Sony A2DP Bluetooth Audio Gateway HWS-BTA2W at 29€. Not being sure if this gadget can offer me wireless audio, I thought what the heck. Already lost 90€ on AEX, so this Sony won't hurt me too badly. And it hurts so good. Now I have clear wireless audio. Distance may not be that long (less than 5m between lappy and amp/BTA2W) but it's enough for me. I was so happy that I bought 2 albums from UbuntuOne music store right away. Boy am I funkin' now!

---

### Post by bzzzzz on 2010-06-26
I get very choppy sound.

All I did using ubuntu 10.04 was to configure local sound server from pulseaudio menu, then tick the two boxes in the network access menu.

You can then see your express in the output of the volume control menu.

Problem is its very choppy (unlistenable at the moment)

---

### Post by Takkat on 2010-08-14
Hi all,

for me streaming to an AEX works smoothly but with a 6s delay having **pulseaudio-module-raop** and **paprefs** installed on Lucid. However Avahi/Zeroconfig does not reliably resolve names :(. Streaming directly to the IP overcomes this issue (see also [pulseaudio ticket #770]("http://pulseaudio.org/ticket/770")).

---

### Post by potrick on 2010-08-17
I got it working with the packages mentioned above, but there's one hiccup: disconnecting from AirTunes doesn't tell the Airport Express to disconnect, meaning no one else can connect to the device after I leave work. Is there some way to achieve this, or should I just be happy to have it working at all?

---

### Post by Takkat on 2010-08-17
Hmm. That's a very good point I was not aware of. I always power off the AE together with my stereo - that of course resets everything. At the moment I don't have an idea of how to perform a remote reset but I'm in good hope to figure that out and implent this. Seems quite important to me. Thanks for pointing at this :-)

Tak

---

### Post by dshrek on 2010-08-18
If you have choppy sound you should try different players. For me, amarok, xine and mplayer are not working properly. Finally, I found totem and rhythmbox to play perfectly, whithout any interruptions.

I hope the amarok guys will fix that soon. I want to have my amarok back!!!

---

### Post by Takkat on 2010-08-18
> **dshrek said:**
>  For me, amarok, xine and mplayer are not working properly. Finally, I found totem and rhythmbox to play perfectly, whithout any interruptions.


very interesting to hear. For me it's just the other way round: mplayer, audacious, exaile, gmusicplayer and guayadeque are playing smoothly whereas totem and rhythmbox are choppy. Did not figure out why, though.

---

### Post by Takkat on 2010-08-18
> **potrick said:**
>  disconnecting from AirTunes doesn't tell the Airport Express to disconnect, meaning no one else can connect to the device after I leave work.

Unfortunately I am unable to reproduce your problems in my setting  here. However the pulseaudio-module-raop needs to be unloaded correctly from PulseAudio. Then streaming to the otherwise untouched AEX is fine for all subsequent users on the same or on a different machine. Maybe it's an issue from your router or your DHCP-server?

By the way I did not find an easy way other than power off to reset the AEX since codes to control the device are not open - too bad.

Loading and unloading the AEX as a RAOP-Device for PulseAudio can easily be done with [stream2ip]("https://launchpad.net/stream2ip") ;-)

---

### Post by dshrek on 2010-08-19
> **Takkat said:**
> very interesting to hear. For me it's just the other way round: mplayer, audacious, exaile, gmusicplayer and guayadeque are playing smoothly whereas totem and rhythmbox are choppy. Did not figure out why, though.

Is it possible that it is just a problem of the right configuration? Maybe different distros have different configuration files. I am using Kububtu 10.04.

---

### Post by Takkat on 2010-08-19
> **dshrek said:**
> Is it possible that it is just a problem of the right configuration?

ACK. It's definitely a matter of config. But what is to configure where?

---

### Post by dshrek on 2010-08-20
> **Takkat said:**
> very interesting to hear. For me it's just the other way round: mplayer, audacious, exaile, gmusicplayer and guayadeque are playing smoothly whereas totem and rhythmbox are choppy. Did not figure out why, though.

This is quite strange. Exaile, guayadeque, totem and rhythmbox all use the gstreamer engine. I would have guessed that if one works, all the others should, too. For me, that is the case, at least for three of them. I have not yet installed and tried to use guayadeque.

But for you, two of them work and two do not. This makes no sense to me, as I don't think that any particular setting of the players should have an influence on the streaming to the AE. Only the settings of gstreamer should be relevant for that.

---

### Post by kyleabaker on 2011-01-08
Any progress on this? I've got an AEX that I'm hoping to share between my desktop (Ubuntu) and my MacBook so I can listen to my tunes over a single stereo.

---

### Post by Takkat on 2011-01-09
Streaming directly to the IP of my AEX is fine here (10.04 LTS am64), playing for hours without any drop-outs. It's only the approx. 6s delay that bugs me.

@kyleabaker: what exactly is not working?

---

### Post by kyleabaker on 2011-01-09
> **Takkat said:**
> Streaming directly to the IP of my AEX is fine here (10.04 LTS am64), playing for hours without any drop-outs. It's only the approx. 6s delay that bugs me.

@kyleabaker: what exactly is not working?

I can't seem to get the AEX to appear as an output option. Any chance you could run through how you set this all up?

---

### Post by Takkat on 2011-01-09
In case you haven't seen it already, there is a [great tutorial at makeuseof]("http://www.makeuseof.com/tag/apples-airtunes-ubuntulinux/") on how to setup PulseAudio in Ubuntu to make the AEX discoverable.

Before you start, ceck if the AEX is recognized in your WLAN (e.g. by a ping to it's IP). If that fails then you need to setup your router or even the AEX first. Next you could check if .local name resolution from Avahi is working. Again, best by:
```
ping name_of_your_aex.local
```
Once everything is setup and running it sometimes gets more stable when connecting directly to the AEX's IP as said above.

---

### Post by kyleabaker on 2011-01-09
Thanks for that link! It certainly helped a lot, however, I've still not been able to stream any sound from Ubuntu.

My single AirPort Express appears 3 times in the list. Selecting any of them results in the same thing. The volume icon changes to disabled for a few seconds, then the list resets to the internal device and the AEX items disappear until I restart PulseAudio.

[IMG]http://img443.imageshack.us/img443/5166/screenshot1dr.png[/IMG]

I'm not sure why it is listed 3 times or why it seems to crash after selecting any of them.

---

### Post by perspectoff on 2011-01-09
I've been streaming to my Airport Express for over a year using Kubuntu.

The instructions have been there for a long time. I'm surprised your google search never found them.

Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#Airport_Express_with_Pulse_Audio](http://kubuntuguide.org/Maverick#Airport_Express_with_Pulse_Audio)

or

[http://kubuntuguide.org/All#Airport_Express_with_Pulse_Audio](http://kubuntuguide.org/All#Airport_Express_with_Pulse_Audio)

Yes, I only use Wicd. Network Manager has not worked for me in several versions of (K)Ubuntu.

---

### Post by Takkat on 2011-01-09
> **kyleabaker said:**
> 
I'm not sure why it is listed 3 times or why it seems to crash after selecting any of them.

Obviously only one entry if any is correct, coming from incomplete removals or erroneous installations of the others.

Try to
```
pulseaudio -k
```
in a terminal to remove invalid modules and sinks and restart PulseAudio server with defaults from /etc/pulse/defaults.pa.

If you are able to **ping your AEX** you may still be able to [stream using the IP]("http://pulseaudio.org/ticket/770") rather than Avahi .local names. This can be done with [stream2ip]("https://launchpad.net/stream2ip"). To avoid multiple entries with stream2ip you should quit the program only after disconnect or by using the quit button to properly remove the audio sinks installed by stream2ip.

---

### Post by kyleabaker on 2011-01-09
Looking through the syslogs, I've spotted what seems to be occuring at the point that I select one of the AEX items in the Output list...

> Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: RTSP/1.0 453 Not Enough Bandwidth
Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: Server: AirTunes/102.2
Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: CSeq: 1
Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: Apple-Response: l88qjnU0/H5EyvpX9a4MscOiOTxuzEch80wR0Hlc/hhxuTOAgd8G+alLgJ6iWBhxqcPiM3lNd0O9OOG++rPv6y15pF3l7HDe3TefilS5j5GAc8Wd3FxfZlbFvfE4HHpqTIPu1lGW7pjhtddXe784ieIciWiEpm1zEcqECqRV+tEe627ZMMw+vt1ZtxYSM9wgtO3i3H1iymjv5pWXhRpcbupsn4wps2kYCOH71FYmKvn2ElgbdtrejlX5J/fOJJdp2gTF7xk+wzO49njRXLFeriWpSCzkY2qkyvXr2N+5c7v1tB+3yZ8c0fUy2R5h52yVF52DYeFLhtR6EaLiyiivug==
Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: 
Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: RTSP/1.0 453 Not Enough Bandwidth
Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: Server: AirTunes/102.2
Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: CSeq: 2
Jan  9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: 
Jan  9 13:43:34 localhost pulseaudio[7360]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Jan  9 13:43:34 localhost pulseaudio[7360]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Jan  9 13:43:34 localhost pulseaudio[7360]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Jan  9 13:43:36 localhost pulseaudio[7360]: ratelimit.c: 7 events suppressed
Jan  9 13:43:42 localhost pulseaudio[7360]: ratelimit.c: 27 events suppressed
Jan  9 13:44:12 localhost pulseaudio[7360]: module-raop-sink.c: Assertion 'u->fd >= 0' failed at modules/raop/module-raop-sink.c:246, function sink_process_msg(). Aborting.


I'm currently trying to get this to function in Ubuntu 11.04 alpha, but unless PulseAudio has changed a lot since Ubuntu 10.10 it should work the same. Here is the version currently in Natty:

> $ apt-cache policy pulseaudio
pulseaudio:
  Installed: 1:0.9.22-0ubuntu3
  Candidate: 1:0.9.22-0ubuntu3
  Version table:
 *** 1:0.9.22-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main amd64 Packages
        100 /var/lib/dpkg/status

I may start a thread in the dev forum if it turns out to be an issue specific to the version in Natty.

---

### Post by Takkat on 2011-01-09
> Jan 9 13:43:34 localhost pulseaudio[7360]: rtsp_client.c: Unexpected response: RTSP/1.0 453 Not Enough BandwidthThe AEX needs quite a good WLAN signal to operate (at least 40%). May this be the cause of not being able to connect?

AFAIK there is no way to address the AEX from two audio servers at the same time. Make sure your iTunes or MAC is turned off when trying to stream from PulseAudio. You may also need to reset the AEX in between. Sorry that I can't test this here - our home is a Windows and MAC-free zone :P.

**Edit:** You could also try to setup your AEX using a static IP. In addition it could also be that Avahi doe not recognize your AEX correctly. This is especially true when the AEX was powered OFF. Then you could disable the &#8220;Make Discoverable Apple AirTunes sound devices available locally&#8221; box from paprefs but still you would be able to ping the IP and connect via this IP. Mind also that after power ON the AEX needs more than 2 minutes to become present in your network.

---

### Post by babuu on 2011-01-22
> **Takkat said:**
> You could also try to setup your AEX using a static IP.

Wohoo, finally I can play to my AEX via pulseaudio! (direct via IP, but thats fine)

Anyways, does anyone know why it works fine with e.g Rhytmbox, but stutters like crazy with Spotify (using wine of course)? The latter is the combo I would really like to get going. Maybe there are some settings to optimize?

---

### Post by puromaster on 2011-04-28
I would like to add to this discussion my experience with Airport Express and Ubuntu 10.10:

Having installed the pulseaudio components, i got it working by doing a "hard reset" on AEX, then, using the AEX as a wireless access point for internet/home network (plugging my cable modem into it and accessing wireless network from the laptop), suddenly the option to select the AEX base station appeared in Sound Preferences.

It did not appear before when i was connected to another wireless router.

Now i'm using the AEX as the wireless internet connection and Airtunes is working great.

If anyone has any questions, send me an email...

:Dan

---

### Post by tomodachi on 2011-09-07
There seems to be a lot of factors here which affect if stuff works or not.

I just installed a airport express for my gf. With the raop module it works fairly painless. But not with all players.

If we all gather together maybe we can see a correlation between models and problems. Recomend ppl using the same template since its easier to "parse" then our rambling :)


----------------------------
Ubuntu version: 11.04 64bit
Aiport fw: 7.5.2
Streaming through: wifi
Banshee: Choppy Sound
mplayer: Perfect sound
--------------------------

there is a newer firmware for the airport available (my gf has a mac and the admin util suggests updating to 7.5.2) but I'm waiting to check out what fw others have before upgrading.

---

### Post by warwickmm on 2012-02-26
I was experiencing all the same issues (choppy sound, etc.), but finally got it to work perfectly with all players thanks to this thread:

[http://forum.videolan.org/viewtopic.php?f=13&t=97111]("http://forum.videolan.org/viewtopic.php?f=13&t=97111")

The key is to run the following command to have VLC capture the pulseaudio stream and send it to the airport express:

```
cvlc pulse://alsa_output.pci-0000_00_1b.0.analog-stereo.monitor :sout='#transcode{acodec=alac,channels=2,samplerate=44100}:raop{host=<ip address of Airport Express>,volume=175}'

```

Using cvlc instead of vlc will run vlc in terminal-mode.  I am running VLC 2.0.0.  Using this method, I do not need to open up paprefs, check the discovery box, and uncheck later, etc.  Just need to run the above in a terminal and kill the process (via ctrl-c) when done.  You can easily write a nice little shell script to make this cleaner if you want.

Previously, using the paprefs discovery method, I would get choppy sound with Banshee, Rhythmbox, Clementine, and just about all other players.  Now, using VLC to capture the stream directly from Pulseaudio has provided perfectly smooth playback.  Perhaps this can be partly attributed to VLC encoding the audio signal with ALAC?  I noticed before that my upload would be between 250-350 KiB/s with choppy sound, but now it can hover between 75-125 KiB/s with no interruption in sound at all, no matter what media player I use.  

Also, for those who have an issue where the raop module locks up the airport express preventing other users from connecting, commenting out the following line in /etc/pulse/default.pa solved that for me, although now using the VLC method I believe that this shouldn't be an issue anymore?

```
#load-module module-raop-discover
```

---

### Post by Takkat on 2012-02-26
How much delay do you experience when using VLC to stream to the AEX?

---

### Post by warwickmm on 2012-02-26
Delay is about 8-10 seconds.

---

### Post by warwickmm on 2012-02-26
Also, I think I just confirmed that using VLC to stream to the AEX, there is no need to edit the /etc/pulse/default.pa file in order to prevent locking up the AEX after disconnecting.

---

### Post by Takkat on 2012-02-26
8-10 seconds is a rather long delay. Sad to hear. Using the IP to stream directly to the AEX via pulseaudio-module-raop (without zeroconfig coming in the way) delay is some less than 6 seconds, This is not good either. In theory the AEX should be capable to stream without a delay.

---

### Post by warwickmm on 2012-02-26
No delay would be really nice, but I think it makes sense that some time is needed to buffer the stream?  Even my apple products exhibit an approximately 4-5 second delay.  

There may be some setting in VLC to control this delay, but I haven't looked into it yet.  If someone has the time to read through the VLC docs, there may be some information in there:

[http://www.videolan.org/doc/streaming-howto/en/ch03.html]("http://www.videolan.org/doc/streaming-howto/en/ch03.html")

At least for now, I'd gladly give up the delay for the uninterrupted playback (I just use it for music, and not videos at the moment).

---

### Post by wulu on 2012-05-06
Works here with 12.04.

I connect to the aex manually using: 
```
pactl load-module module-raop-sink server=192.168.2.5
```
Disabled all options in the paprefs utility, dont like autodetection.

The choppy sound with some players seem s to be related to the bit depth of the audio output.

Using Audacious player 
prefs Audio Plugin: Pulse Audio
Bit depth:32

----------------------------
Ubuntu version: 12.04 64bit
Aiport fw: unknown, but latest i guess
Streaming through: wlan, aex only connect via ethernet
Audacious: perfect sound
--------------------------

---

### Post by Takkat on 2012-05-06
> **wulu said:**
> Works here with 12.04.

I connect to the aex manually using: 
```
pactl load-module module-raop-sink server=192.168.2.5
```
Disabled all options in the paprefs utility, dont like autodetection.


My impression is the same. Connecting via the IP is much more stable than relying on Avahi. 

Just to have mentioned it, we have put quite some effort to add new features to [stream2ip]("https://launchpad.net/stream2ip") where we also use the IP to connect to an AEX. 

[IMG]http://sourceforge.net/projects/stream2ip/screenshots/322344[/IMG]

Features added in the last releases

[LIST]
[*]wait for an AEX to finish booting before we connect
[*]re-connect after intermittent WLAN signal disruption
[*]connect an active stream while playing.
[*]removed dependency on **paprefs**.
[/LIST]

---

### Post by dnglbr on 2012-05-19
> **Takkat said:**
> Just to have mentioned it, we have put quite some effort to add new features to [stream2ip]("https://launchpad.net/stream2ip") where we also use the IP to connect to an AEX. 
Takkat, fantastic work with stream2ip. Works very well, glad to have found it here.

---

### Post by sonicb00m on 2012-12-12
Airport express delay is unavoidable and is part of the protocol the unit uses to stream the sound. 8 seconds seems a long time but 4-5 seconds seems to be the usual delay time even with other products/systems.

I have used Airfoil with Windows and they explain the delay issue in their FAQ.

---

### Post by sonicb00m on 2012-12-13
Finally got arround to testing with stream2ip and it works great :D No more stuttering audio!

---

### Post by heap1 on 2013-01-11
Hi,

Im using stream2ip 0.37, while playing mp3 file i got some choppy sound since time to time but when i play flac its terrible... choppy sound all the time. Any idea? I disabled auto discovery of AE devices in pulseaudio....


thans

---

### Post by Takkat on 2013-01-11
> **heap1 said:**
> 

while playing mp3 file i got some choppy sound since time to time but when i play flac its terrible... 



This may be a network issue from suboptimal wireless signal strength. 

Another possibility may come from the media player you are using. I heard of people having issues with choppy playback for one player but not for the other. Sadly there was no consistency. The player that worked fine for somebody may not work well on another computer. It may still be worth to try if a different player gives better results.

As you experience FLAC to be worse than mp3 it could also be that there is a different workload for pulseaudio while converting to the RAOP signal. See if running
```
top
```
in a terminal gives you an idea on CPU and memory usage. For mp3, is there a difference for high (e.g. 320 kbps) *vs.* low (e.g. 128 kbps) sample rates?

Updating stream2ip to 1.0.3 will likely not resolve the issue as we put much effort to migrate to Python3 and Gtk3 but did not change much of the code for streaming. Also I believe it is more an issue of pulseaudio we have here.

---

