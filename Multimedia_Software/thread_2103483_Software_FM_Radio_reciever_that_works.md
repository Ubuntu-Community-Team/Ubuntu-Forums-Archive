---
title: "Software FM Radio reciever that works?"
date: 2013-01-10
forum: Multimedia Software
---

### Post by MakOwner on 2013-01-10
For my own personal time-shift use, I record a talk show from a local FM Radio station.

My current solution is to take a small table top radio with 2.5mm earpice/headphone jack, connect a cable from that to the mic jack on a Ensonic PCI Sound card in a very old Dell server -- a PE 350, Pizza box, 1GHZ processor and 1 GB of memory.

I use arecord and lame to record from the default sound device and then convert the raw recording to mp3 format.

This has been working for years, but as the server and the sound card are getting long in the tooth, I have tried several times converting to a newer server with a PCIe type sound card.  I have never been able to get this to work since something breaks with the command line stuff.  I can never get the input set properly in the sound cards from CLI utilities.

On top of this is the issue of tuning -- any drift in the station signal doesn't get corrected until I hear the recording later and realize I have one or more bad recordings because of the tuning.  

I know there are a fair amount of TV cards out there that include FM receivers, but I have never been able to get any of them to work, esepcailly from the command line.  

I need to stay with a command line interface, because even if I do upgrade the server hardware it will still be memory and processor limited and will run headless and be managed via ssh.


I'd like to find a software solution that allows me to set up a tuner to track the FM signal to avoid the need to check the signal daily and allow command line recording of the output, or find a PCIe sound card that will work out of the box like the old PCI sound cards do.  I can live with the tuning issue if I have to, as I have for several years now.   


Has anyone done anything like this at all?  Please help!

---

### Post by haqking on 2013-01-10
> **MakOwner said:**
> For my own personal time-shift use, I record a talk show from a local FM Radio station.

My current solution is to take a small table top radio with 2.5mm earpice/headphone jack, connect a cable from that to the mic jack on a Ensonic PCI Sound card in a very old Dell server -- a PE 350, Pizza box, 1GHZ processor and 1 GB of memory.

I use arecord and lame to record from the default sound device and then convert the raw recording to mp3 format.

This has been working for years, but as the server and the sound card are getting long in the tooth, I have tried several times converting to a newer server with a PCIe type sound card.  I have never been able to get this to work since something breaks with the command line stuff.  I can never get the input set properly in the sound cards from CLI utilities.

On top of this is the issue of tuning -- any drift in the station signal doesn't get corrected until I hear the recording later and realize I have one or more bad recordings because of the tuning.  

I know there are a fair amount of TV cards out there that include FM receivers, but I have never been able to get any of them to work, esepcailly from the command line.  

I need to stay with a command line interface, because even if I do upgrade the server hardware it will still be memory and processor limited and will run headless and be managed via ssh.


I'd like to find a software solution that allows me to set up a tuner to track the FM signal to avoid the need to check the signal daily and allow command line recording of the output, or find a PCIe sound card that will work out of the box like the old PCI sound cards do.  I can live with the tuning issue if I have to, as I have for several years now.   


Has anyone done anything like this at all?  Please help!


not really what you are looking for but doesnt the radio station have a online live stream (most do) then use streamripper or similar to rip the audio ?

I listen to all my radio via the web these days

---

### Post by MakOwner on 2013-01-10
> **haqking said:**
> not really what you are looking for but doesnt the radio station have a online live stream (most do) then use streamripper or similar to rip the audio ?

I listen to all my radio via the web these days

They stream through the IHeartRadio app/program.  
I'm not aware of alinux client for that, much less one that would run from command line.

---

### Post by haqking on 2013-01-10
> **MakOwner said:**
> They stream through the IHeartRadio app/program.  
I'm not aware of alinux client for that, much less one that would run from command line.

[http://pyther.net/2010/08/iheartradio-command-line-mplayer/](http://pyther.net/2010/08/iheartradio-command-line-mplayer/)

You can also use mplayer with an IP address

---

### Post by MakOwner on 2013-01-10
> **haqking said:**
> [http://pyther.net/2010/08/iheartradio-command-line-mplayer/](http://pyther.net/2010/08/iheartradio-command-line-mplayer/)

You can also use mplayer with an IP address

I have played around with that, and forwhater reason it does not work.
It appears to me that the wget command in all those script variants return a null value that is required to point to the rtmp:// address.

---

### Post by tgalati4 on 2013-01-10
What is the actual radio show that you are trying to record?  Do you have a link?

---

### Post by MakOwner on 2013-01-10
> **tgalati4 said:**
> What is the actual radio show that you are trying to record?  Do you have a link?

This is the link to listen to the station in a browser.

[http://www.iheart.com/live/971-The-EAGLE-Rocks-2241/](http://www.iheart.com/live/971-The-EAGLE-Rocks-2241/)


The script doesn't find anything there, either.


In any event, I'd rather record the over the air signal as I get a really good signal, and it has worked for some time for me -- plus, if I can get a software tunable radio working, I could record some stuff from other local radio that isn't on a web stream.

---

### Post by tgalati4 on 2013-01-10
```
apropos pulse
```

Perhaps you can record the stream through pulseaudio.  Pulseaudio allows you redirect streams to other programs, even to other machines.  Then all you have to do is figure out how to start the IheartRadio player at the appointed time.

---

### Post by ron999 on 2013-01-11
> **MakOwner said:**
> ... In any event, I'd rather record the over the air signal as I get a really good signal...
It's easy enough to record that EAGLE stream with VLC, but it's up to you if you prefer to use some other method.
:p

---

### Post by MakOwner on 2013-01-11
> **ron999 said:**
> It's easy enough to record that EAGLE stream with VLC, but it's up to you if you prefer to use some other method.
:p

Can you share exactly how you set that up?

---

### Post by haqking on 2013-01-11
> **MakOwner said:**
> Can you share exactly how you set that up?

I am sure they will post back, never done it myself but i expect you can do it using something from here:

[http://wiki.videolan.org/Documentation:Streaming_HowTo/Receive_and_Save_a_Stream](http://wiki.videolan.org/Documentation:Streaming_HowTo/Receive_and_Save_a_Stream)

[http://wiki.videolan.org/Documentation:Streaming_HowTo/Command_Line_Examples](http://wiki.videolan.org/Documentation:Streaming_HowTo/Command_Line_Examples)

---

### Post by MakOwner on 2013-01-11
> **haqking said:**
> I am sure they will post back, never done it myself but i expect you can do it using something from here:

[http://wiki.videolan.org/Documentation:Streaming_HowTo/Receive_and_Save_a_Stream](http://wiki.videolan.org/Documentation:Streaming_HowTo/Receive_and_Save_a_Stream)

[http://wiki.videolan.org/Documentation:Streaming_HowTo/Command_Line_Examples](http://wiki.videolan.org/Documentation:Streaming_HowTo/Command_Line_Examples)

Thank you.  I'll try this.
Sure would be nice to find a software controllable FM recevier that doesn't cost $1k though.

---

### Post by ron999 on 2013-01-11
> **MakOwner said:**
> Can you share exactly how you set that up?
Use **--stop-time** to set duration in seconds.

For the original aac stream:-
```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); cvlc --stop-time=[COLOR="Red"]30[/COLOR] http://www.surfmusic.de/media/kegl-fm.m3u --sout="#std{access=file,mux=mp4,dst='$NOW-The_EAGLE_Rocks.m4a'}" vlc://quit

```
If you prefer mp3, use one of these methods:-
```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); cvlc --stop-time=[COLOR="Red"]30[/COLOR] http://www.surfmusic.de/media/kegl-fm.m3u --sout="#transcode{acodec=mp3,ab=128,channels=2,samplerate=44100}:std{access=file,mux=raw,dst='$NOW-The_EAGLE_Rocks.mp3'}" vlc://quit
```

```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); cvlc --stop-time=[COLOR="Red"]30[/COLOR] http://www.surfmusic.de/media/kegl-fm.m3u --sout="#transcode{acodec=s16l,channels=2,samplerate=44100}:std{access=file,mux=wav,dst=-}" vlc://quit | lame -V 4 - $NOW-The_EAGLE_Rocks.mp3
```

---

### Post by MakOwner on 2013-01-11
> **ron999 said:**
> Use **--stop-time** to set duration in seconds.

For the original aac stream:-
```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); cvlc --stop-time=[COLOR="Red"]30[/COLOR] http://www.surfmusic.de/media/kegl-fm.m3u --sout="#std{access=file,mux=mp4,dst='$NOW-The_EAGLE_Rocks.m4a'}" vlc://quit

```
If you prefer mp3, use one of these methods:-
```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); cvlc --stop-time=[COLOR="Red"]30[/COLOR] http://www.surfmusic.de/media/kegl-fm.m3u --sout="#transcode{acodec=mp3,ab=128,channels=2,samplerate=44100}:std{access=file,mux=raw,dst='$NOW-The_EAGLE_Rocks.mp3'}" vlc://quit
```

```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); cvlc --stop-time=[COLOR="Red"]30[/COLOR] http://www.surfmusic.de/media/kegl-fm.m3u --sout="#transcode{acodec=s16l,channels=2,samplerate=44100}:std{access=file,mux=wav,dst=-}" vlc://quit | lame -V 4 - $NOW-The_EAGLE_Rocks.mp3
```



I was trying the direct-to-mp3 version and I'm running into an issue.
I'm missing the mp3 codec?

```

cvlc --stop-time=30 http://www.surfmusic.de/media/kegl-fm.m3u --sout="#transcode{acodec=mp3,ab=128,channels=2,samplerate=44100}:std{access=file,mux=raw,dst='Test.mp3'}" vlc://quit
VLC media player 2.0.3 Twoflower (revision 2.0.2-93-g77aa89e)
[0x12c18d8] inhibit interface error: Failed to connect to the D-Bus session daemon: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
[0x12c18d8] main interface error: no suitable interface module
[0x1489f78] main interface error: no suitable interface module
[0x1291108] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x1489f78] dummy interface: using the dummy interface module...
[0x7ff4400021a8] mux_dummy mux: Open
[0x7ff440008bd8] es demux error: cannot peek
[0x12a5c98] main playlist: stopping playback
[0x7ff4400019a8] mux_dummy mux: Open
[0x7ff440004cd8] access_http access: Raw-audio server found, m4a demuxer selected
[0x7ff440007878] packetizer_mpeg4audio demux packetizer: AAC channels: 2 samplerate: 44100
[0x7ff440001538] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mp3 ). Take a look few lines earlier to see possible reason.
[0x7ff440001538] stream_out_transcode stream out error: cannot create audio chain
[0x7ff44000a028] main decoder error: cannot create packetizer output (mp4a)
[0x7ff440001538] idummy demux: command `quit'

```

However, if I use mux=wav, I can use lame to convert that to mp3 and it works, or hat least has for short periods.  

I take it this stream originates in .mp4a format?

What's the deal with surfmusic.de? 
Will I find US Stasi at my door for not going through the I-hate-Radio interface?  (I'm in the US).

---

### Post by MakOwner on 2013-01-12
I'm hijacking my own thread here, because I desparately still want a software scriptable/controllable FM receiver.

How did you arrive at the .m3u link for that radio station?
I looked up another station on there that I'd like to record a show from and I can't find a link with that sort of format. 
I can't even find that link for the station I'm recording.

---

### Post by tgalati4 on 2013-01-12
Typically, you run the player in firefox then use tools-->web developer-->page source.

Scroll through the page source until you find a link that might have the source feed.

There are several tools you can use.  You have to install them and look at the switches available, then write a script.

Some radio programs publish in RSS or podcast form.  Check the Radio station's website and see if any of the past shows are available as podcasts.  Then you can use gpodder to download them and put them on an mp3 player.  If not available, then ask the radio station to publish them.

tgalati4@Dell600m-mint14 ~ $ apt-cache search streamripper
fadecut - toolset to rip audiostreams, cut, fade in/out and tag the resulting audiofiles
kradioripper - internet radio recorder
rhythmbox-radio-browser - Internet radio browser plugin for rhythmbox
streamripper - download online streams into audio files
streamtuner2 - Browser for Internet Radio Stations
tunapie - Lists audio and video streams from Shoutcast and Icecast

---

### Post by MakOwner on 2013-01-12
> **tgalati4 said:**
> Typically, you run the player in firefox then use tools-->web developer-->page source.

Scroll through the page source until you find a link that might have the source feed.

There are several tools you can use.  You have to install them and look at the switches available, then write a script.

Some radio programs publish in RSS or podcast form.  Check the Radio station's website and see if any of the past shows are available as podcasts.  Then you can use gpodder to download them and put them on an mp3 player.  If not available, then ask the radio station to publish them.

tgalati4@Dell600m-mint14 ~ $ apt-cache search streamripper
fadecut - toolset to rip audiostreams, cut, fade in/out and tag the resulting audiofiles
kradioripper - internet radio recorder
rhythmbox-radio-browser - Internet radio browser plugin for rhythmbox
streamripper - download online streams into audio files
streamtuner2 - Browser for Internet Radio Stations
tunapie - Lists audio and video streams from Shoutcast and Icecast

The level of obfuscation in the web pages on surfmusic.de, I heart Radio and the home page of that stations are way over my head.

I have searched through a fair amount of the page source on surfmusic and I don't see any links that look like the one posted earlier in this thread.

---

### Post by MakOwner on 2013-01-13
> **MakOwner said:**
> The level of obfuscation in the web pages on surfmusic.de, I heart Radio and the home page of that stations are way over my head.

I have searched through a fair amount of the page source on surfmusic and I don't see any links that look like the one posted earlier in this thread.



Interestingly enough, after further digging, I came up with the akacast.akamaistream.net source stream.   I can record directly from there too.

I'm trying to understand what I'm doing here.
```

[0x7ff988007388] access_http access: Raw-audio server found, m4a demuxer selected
[0x7ff988008e28] packetizer_mpeg4audio demux packetizer: AAC channels: 2 samplerate: 44100

```

The first line indicates a raw audio stream, and because of the command line I used with cvlc, I get the 'm4a demuxer' selected, or does vlc select that demuxer based on the content of the stream?


I think I need to start a new thread.

---

### Post by tgalati4 on 2013-01-13
m4a is a "container" format, the actual data stream is AAC.  As long as vlc detects it and selects the correct codec, then it should record OK.  It's quite obvious when vlc encounters a stream that it can't decode.

---

### Post by MakOwner on 2013-01-19
> **tgalati4 said:**
> m4a is a "container" format, the actual data stream is AAC.  As long as vlc detects it and selects the correct codec, then it should record OK.  It's quite obvious when vlc encounters a stream that it can't decode.

I can't get any of it to record more than about 15 minutes from a cron job.
I can't see any reason for it to stop, but the recording just terminates without error after about 15 minutes.


Anyone idea how I can get cvlc to actually record the amount of time specified on the command line?

---

### Post by ron999 on 2013-01-19
> **MakOwner said:**
> Anyone idea how I can get cvlc to actually record the amount of time specified on the command line?

```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); cvlc --stop-time=[COLOR="Red"]1800[/COLOR] http://www.surfmusic.de/media/kegl-fm.m3u --sout="#std{access=file,mux=mp4,dst='$NOW-The_EAGLE_Rocks.m4a'}" vlc://quit
```

> [SIZE="1"]General
Complete name                            : 2013-01-19-19h24m-The_EAGLE_Rocks.m4a
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 13.6 MiB
Duration                                 : [COLOR="Red"]30mn 0s[/COLOR]
Overall bit rate mode                    : Variable
Overall bit rate                         : 63.5 Kbps
Encoded date                             : UTC 2013-01-19 19:54:18
Tagged date                              : UTC 2013-01-19 19:54:18
Writing application                      : vlc 2.1.0-git stream output
Comment                                  : QuickTime 6.0 or greater

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 30mn 0s
Source duration                          : 30mn 0s
Bit rate mode                            : Variable
Bit rate                                 : 61.6 Kbps
Maximum bit rate                         : 113 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 13.2 MiB (97%)
Source stream size                       : 13.2 MiB (97%)
Language                                 : English
Encoded date                             : UTC 2013-01-19 19:54:18
Tagged date                              : UTC 2013-01-19 19:54:18
mdhd_Duration                            : 1800150[/SIZE]

---

### Post by Merrattic on 2013-01-19
As an alternative route, see here:

[http://ubuntuforums.org/showthread.php?t=1330728](http://ubuntuforums.org/showthread.php?t=1330728)
and a gui version
[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)

You'll have to get the stream playing on your server, the above will then record?

---

### Post by MakOwner on 2013-01-19
> **ron999 said:**
> ```
NOW=$(date +"%Y-%m-%d-%Hh%Mm"); cvlc --stop-time=[COLOR="Red"]1800[/COLOR] http://www.surfmusic.de/media/kegl-fm.m3u --sout="#std{access=file,mux=mp4,dst='$NOW-The_EAGLE_Rocks.m4a'}" vlc://quit
```

This is pretty much exactly what I have been doing just in a cron job in a korn shell script.  I have even tried several sources that will record audio, just not for more than 15 minutes or so.  I can run the script while logged in and it seems to work, at least for longer than 15 minutes.

cvclc seems to have issues with the shell created from the cron job; or at least that's what I think it is, unless the stream itself is terminating somehow.

---

### Post by occasional expert on 2013-05-10
> **MakOwner said:**
> For my own personal time-shift use, I record a talk show from a local FM Radio station.

My current solution is to take a small table top radio with 2.5mm earpice/headphone jack, connect a cable from that to the mic jack on a Ensonic PCI Sound card in a very old Dell server -- a PE 350, Pizza box, 1GHZ processor and 1 GB of memory.

I use arecord and lame to record from the default sound device and then convert the raw recording to mp3 format.

This has been working for years, but as the server and the sound card are getting long in the tooth, I have tried several times converting to a newer server with a PCIe type sound card.  I have never been able to get this to work since something breaks with the command line stuff.  I can never get the input set properly in the sound cards from CLI utilities.

On top of this is the issue of tuning -- any drift in the station signal doesn't get corrected until I hear the recording later and realize I have one or more bad recordings because of the tuning.  

I know there are a fair amount of TV cards out there that include FM receivers, but I have never been able to get any of them to work, esepcailly from the command line.  

I need to stay with a command line interface, because even if I do upgrade the server hardware it will still be memory and processor limited and will run headless and be managed via ssh.


I'd like to find a software solution that allows me to set up a tuner to track the FM signal to avoid the need to check the signal daily and allow command line recording of the output, or find a PCIe sound card that will work out of the box like the old PCI sound cards do.  I can live with the tuning issue if I have to, as I have for several years now.   


Has anyone done anything like this at all?  Please help!

I've been dong almost exactly the above for a decade now.

I think you have two problems.  

The first is drift in your radio's tuner.  I'd solve this by buying a  used FM tuner off of eBay.  Get one with digital tuning where the  frequency readout is a number, not a pointer on a dial, as digital  tuners just don't drift.  I bought a used Denon a decade ago for about  $50, set it to the frequency I wanted, and haven't touched it since.   You'll need a RCA plugs to stereo 3.5mm plug cable from Radio Shack or  whereever to connect the outputs of the tuner to the line level input of  your sound card.  You'll also need to supply some sort of antenna for  the tuner, but if you're in a good signal area this can be as simple as a  piece of wire hung on the wall.  

You could probably use one of the little Sony portable earphone-only radios that are sold in Wal-Mart, but I haven't tried one.  They'd be cheaper and a lot smaller than a full sized tuner.

The second issue is one I hit when I first started using arecord.  When  arecord is started, the system seems to set the mixers on the sound card  to some default state where I record only silence.  I had to use amixer to  set up the sound card AFTER arecord is started.  Also, I found the  proper things to set using amixer to be rather non-obvious and had to do  some detective work.

In the shell script I use for recording, I do something like:

  arecord -d <seconds> -f cd -t raw | lame --abr 128 -m j -S -r -s 44100 - <program>.mp3 &
  # Set up the sound card
  amixer -q sset Mic 0%,0% mute
  amixer -q sset Line 0%,0% cap
  amixer -q sset AC97 90%,90% unmute
  amixer -q sset Capture ${LEVEL}%,${LEVEL}% cap
  # wait for arecord to exit
  wait

This works on a 10.4.4 LTS system using a Creative SoundBlaster Live  card.  The $LEVEL for the Capture you'll have to find out by experiment.  Using CD style PCM and 128 kbit ABR mp3 files yields sound I find quite good enough for even classical music.

You can discover what channels your particular card has with the command "amixer scontrols".  

A few debugging hints:

With a known good .wav file, do "aplay file.wav".  This will play the  file over your PC speakers and usually works on my system without  mucking with the mixer levels.  If that works, in one terminal window,  run 

   arecord -f cd -t raw | aplay -f cd -t raw

with your tuner or radio plugged in to the sound board and tuned  properly.  In another window muck with the simple input controls on the  sound board with amixer (you can try alsamixer also) until you get good  quality sound out of your PC speakers from the tuner/radio.  Then put  calls to amixer in your script to set up the sound card similar to what I  do above based on what gives good sound.

Have fun.

In reference to using streamripper or VLC or mplayer to capture the  stream from the station(s) I'm interested in, well...  Using an external  tuner Just Works.  When I started doing this the OTA signal I was  interested in (WNYC in New York) sounded a lot better than any of their  streams.  That's no longer the case, but the above is a lot more  reliable than the web streams I capture from other places.

Another note:  To get the .m3u file for a particular source, I usually  poke around on the source's Web site for a link that's for streaming to  Winamp and do a "copy link location" in Firefox.  I then use wget to  actually pull down the file.  The in-browser players aren't usually  helpful here, I usually look for a page on "Other Formats" or some such.   The .m3u playlist format was created by the Winamp folks.

Dan

---

### Post by MakOwner on 2013-05-10
> **occasional expert said:**
> I've been dong almost exactly the above for a decade now.

I think you have two problems.  

The first is drift in your radio's tuner.  I'd solve this by buying a  used FM tuner off of eBay.  Get one with digital tuning where the  frequency readout is a number, not a pointer on a dial, as digital  tuners just don't drift.  I bought a used Denon a decade ago for about  $50, set it to the frequency I wanted, and haven't touched it since.   You'll need a RCA plugs to stereo 3.5mm plug cable from Radio Shack or  whereever to connect the outputs of the tuner to the line level input of  your sound card.  You'll also need to supply some sort of antenna for  the tuner, but if you're in a good signal area this can be as simple as a  piece of wire hung on the wall.  

You could probably use one of the little Sony portable earphone-only radios that are sold in Wal-Mart, but I haven't tried one.  They'd be cheaper and a lot smaller than a full sized tuner.

The second issue is one I hit when I first started using arecord.  When  arecord is started, the system seems to set the mixers on the sound card  to some default state where I record only silence.  I had to use amixer to  set up the sound card AFTER arecord is started.  Also, I found the  proper things to set using amixer to be rather non-obvious and had to do  some detective work.

In the shell script I use for recording, I do something like:

  arecord -d <seconds> -f cd -t raw | lame --abr 128 -m j -S -r -s 44100 - <program>.mp3 &
  # Set up the sound card
  amixer -q sset Mic 0%,0% mute
  amixer -q sset Line 0%,0% cap
  amixer -q sset AC97 90%,90% unmute
  amixer -q sset Capture ${LEVEL}%,${LEVEL}% cap
  # wait for arecord to exit
  wait

This works on a 10.4.4 LTS system using a Creative SoundBlaster Live  card.  The $LEVEL for the Capture you'll have to find out by experiment.  Using CD style PCM and 128 kbit ABR mp3 files yields sound I find quite good enough for even classical music.

You can discover what channels your particular card has with the command "amixer scontrols".  

A few debugging hints:

With a known good .wav file, do "aplay file.wav".  This will play the  file over your PC speakers and usually works on my system without  mucking with the mixer levels.  If that works, in one terminal window,  run 

   arecord -f cd -t raw | aplay -f cd -t raw

with your tuner or radio plugged in to the sound board and tuned  properly.  In another window muck with the simple input controls on the  sound board with amixer (you can try alsamixer also) until you get good  quality sound out of your PC speakers from the tuner/radio.  Then put  calls to amixer in your script to set up the sound card similar to what I  do above based on what gives good sound.

Have fun.

In reference to using streamripper or VLC or mplayer to capture the  stream from the station(s) I'm interested in, well...  Using an external  tuner Just Works.  When I started doing this the OTA signal I was  interested in (WNYC in New York) sounded a lot better than any of their  streams.  That's no longer the case, but the above is a lot more  reliable than the web streams I capture from other places.

Another note:  To get the .m3u file for a particular source, I usually  poke around on the source's Web site for a link that's for streaming to  Winamp and do a "copy link location" in Firefox.  I then use wget to  actually pull down the file.  The in-browser players aren't usually  helpful here, I usually look for a page on "Other Formats" or some such.   The .m3u playlist format was created by the Winamp folks.

Dan

Ah, finally - someone that has successfully done this! 

I purchased a digital tuner - a Rolls HR78 PLL FM tuner rack mountable unit that has a 75ohm FM antenae connector -- I ran the 75ohm cable out of the room to an FM antennae to help get signal aquisition away from potential interference from the computers.  The HR78 indicates that I have a good stereo signal locked in (but I wish I had a good way to verify signal strength rather than just what I can hear from output).

The HR78 has two outputs, L/R (Red/White) RCA jacks and a 3.5mm "Head Phone out" jack. 

I got alsa working on the CLI with 12.04 LTS and the Xonar DX sound card.  

My issue is that it is well over a month into this and I'm stil looking for the right settings and getting actual stereo captured.

If I use line-in on the sound card (line-in and the mic jack are the same physical connectors - you have to seelct the active input with alsamixer) the audio level is too low at the settings where Rolls indicates the unit should be for 'line level output'.  Cranking it up higher cause tearible fuzz-like static in the quieter sections of the audio.

Using the mic capture on the sound car lets me jockey the output of the HR78 against gain in the mic jack.  That produces _better_ sound, but finding that sweet spot is _really_ freaking hard.
And, I can't seem to get stereo captured on this card -- when you run arecord manually from the command line with the --vumeter=stereo you see everything is recorded in the left channel.

I'm using "-f cd -t wav -d $SECONDS $NAME.wav" as the arecord parameters.  When capturing 415 minutes of audio, the l output grows beyond 2Gb and arecord starts a second file.
I'm using wav output so that I can just point sox at the files to create a single file and that I convert to mp3.

I'm still recording off the older hardware using the cheapo generic sound card too.  I get drift from the cheap table top radio, but I get gnerally better sound quality and in stereo.  Go figger.


The Rolls unit wasn't dirt cheap, but it is AM/FM only and not $3 - $10k like some of the other tuners with HDRadio capabilities.  But don't by the bit where they call it a "half-rack size unit".  It's more like "quarter size" - and you have to have thier special shelf to fit it in, and you get two side by side mounts in the shelf.  So, if you were so inclined, you would be able to mount two side by side in the front of a rack and two side by side in the back.  And not mount on eat all without thier special shelf.  To me "half rack" indicates half depth of a standard 19" rack, not half width...

---

### Post by occasional expert on 2013-05-12
> **MakOwner said:**
> Ah, finally - someone that has successfully done this! 

I purchased a digital tuner - a Rolls HR78 PLL FM tuner rack mountable unit that has a 75ohm FM antenae connector -- I ran the 75ohm cable out of the room to an FM antennae to help get signal aquisition away from potential interference from the computers.  The HR78 indicates that I have a good stereo signal locked in (but I wish I had a good way to verify signal strength rather than just what I can hear from output).

The HR78 has two outputs, L/R (Red/White) RCA jacks and a 3.5mm "Head Phone out" jack. 

I got alsa working on the CLI with 12.04 LTS and the Xonar DX sound card.  

My issue is that it is well over a month into this and I'm stil looking for the right settings and getting actual stereo captured.

If I use line-in on the sound card (line-in and the mic jack are the same physical connectors - you have to seelct the active input with alsamixer) the audio level is too low at the settings where Rolls indicates the unit should be for 'line level output'.  Cranking it up higher cause tearible fuzz-like static in the quieter sections of the audio.

Using the mic capture on the sound car lets me jockey the output of the HR78 against gain in the mic jack.  That produces _better_ sound, but finding that sweet spot is _really_ freaking hard.
And, I can't seem to get stereo captured on this card -- when you run arecord manually from the command line with the --vumeter=stereo you see everything is recorded in the left channel.

Welcome to the banging of one's head against the wall that seems to go with learning a new sound card under ALSA.  Been there, done that.  Mongo frustrating.

But I have some ideas.  

Be aware that one major difference between a line level and mic input on a computer is that the mic input is MONO.  Yep, the mic may have what looks like the exact same stereo plug/jack (with tip, ring, and sleeve), but the ring on the plug carries not the right audio signal as it does on a line input but is often used to send power to the microphone.  If you're only getting sound on the left channel it means that the sound card hasn't fully put the input in line in mode.  Your freaking hard job just got a little harder.  You're going to have to learn to use amixer to dump all the capabilities of the card and set the right one.

Look at the output of "amixer scontents".  There will probably be something connected with the input that has "Capabilities: enum" with a list of possibilities.  I hope.  This is something I barely know anything about.  You'll have to play with "amixer sset ...".  Google might be your friend.

> 
I'm using "-f cd -t wav -d $SECONDS $NAME.wav" as the arecord parameters.  When capturing 415 minutes of audio, the l output grows beyond 2Gb and arecord starts a second file.
I'm using wav output so that I can just point sox at the files to create a single file and that I convert to mp3.

Sigh.  I've hit this limitation too.

It's actually a limitation in the design of the .wav header.  There's a field in the header that contains the length of the audio data in bytes, and it's a 16 bit unsigned integer.  The maximum value that size integer can hold corresponds to the 6 hours and change limit in CD-style PCM (44100 samples/second, each sample being 2 bytes for each channel of the stereo).

You can cheat if you just write raw PCM data into a file, at least if you use redirection e.g. "arecord -f cd -t raw -d $SECONDS >$NAME.raw".  I don't use sox, but if you have LAME you can then get one mp3 with "lame <compression options> -r -s 44100 $NAME.raw $NAME.mp3" or some such.

> 
I'm still recording off the older hardware using the cheapo generic sound card too.  I get drift from the cheap table top radio, but I get gnerally better sound quality and in stereo.  Go figger.


I assume you've tried using the new tuner with your old sound card and setup.  It should work.


> 
The Rolls unit wasn't dirt cheap, but it is AM/FM only and not $3 - $10k like some of the other tuners with HDRadio capabilities.  But don't by the bit where they call it a "half-rack size unit".  It's more like "quarter size" - and you have to have thier special shelf to fit it in, and you get two side by side mounts in the shelf.  So, if you were so inclined, you would be able to mount two side by side in the front of a rack and two side by side in the back.  And not mount on eat all without thier special shelf.  To me "half rack" indicates half depth of a standard 19" rack, not half width...

My experience with HD says you done good.  The HD tuners I've used crash periodically, and if you have a reasonably good signal there's little gained from HD over the analog signal.

---

### Post by occasional expert on 2013-05-13
Another thought I had at 4 AM while not being able to sleep.

When I first started recording a tuner using Linux, I was using a system built around an Asus motherboard, using the sound "card" on the mobo.  I found that even with all the mixer channels wide open the tuner would not drive the line input to the sound system on that mobo well enough to get a decent recording.  

The upshot is that there are line inputs and line inputs.  There's little standardization.  My tuner expects a fairly high impedance load on its line level RCA outputs.  But some sound cards' line inputs have significantly lower input impedance (around 1K ohms) and load such a source unacceptably.  I had to use a headphone amplifier I built from a Ramsey kit between my tuner and that mobo to get decently well modulated mp3 files.  Mic inputs on PCs usually have ~600 ohm impedance I think.

For me, the problem was solved when I switched over to using SoundBlaster cards which have separate line input jacks that don't load my tuner at all.

For you, have you tried using the headphone out jack on your new tuner to drive the input of your new sound card?  The headphone output expects a load impedance of a typical set of headphones or earbuds (10 to 50 ohms).  Using that output to drive a somewhat higher impedance load such as your new sound card will work and the signal should be plenty strong to drive any line level sound card input I've seen.  Give it a try.  You can't hurt anything doing it.

---

### Post by MakOwner on 2013-05-13
I have been mucking about and have tried a number of combinations of mic and line input with output being the RCA jacks to 3.5mm converter and 3.5mm direct from the headphone jack too.
I need to start keeping track of which ones I have tried so as not to go over old ground again.

I had looked at the capabilities of the sound card and thought I was pretty sure it shoudl be able to record at least stereo, but you may be right.
I had originally tried a PCIe SoundBlaster or whatever they are called these days and spent more time than I wanted to get it to work, took it back and got the ASUS card.

The host I'm using has one PCI-e and one PCI-X I/O slot available.  I actually tried a couple of external USB audio things but that didn't work for input or output.

amixer output:
```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right
  Limits: Playback 67 - 127
  Mono:
  Front Left: Playback 107 [67%] [-20.00dB] [off]
  Front Right: Playback 107 [67%] [-20.00dB] [off]
  Rear Left: Playback 107 [67%] [-20.00dB] [off]
  Rear Right: Playback 107 [67%] [-20.00dB] [off]
  Front Center: Playback 107 [67%] [-20.00dB] [off]
  Woofer: Playback 107 [67%] [-20.00dB] [off]
  Side Left: Playback 107 [67%] [-20.00dB] [off]
  Side Right: Playback 107 [67%] [-20.00dB] [off]
Simple mixer control 'Front Panel',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Line',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 14 [45%] [-13.50dB] [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Mic Source',0
  Capabilities: cenum
  Items: 'Mic Jack' 'Front Panel'
  Item0: 'Mic Jack'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Aux',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 23 [74%] [0.00dB] [off]
  Front Right: Capture 23 [74%] [0.00dB] [off]
Simple mixer control 'Analog Input Monitor',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 1
  Mono: Playback 0 [0%] [-6.00dB] [off]
Simple mixer control 'DAC Filter',0
  Capabilities: penum
  Items: 'Fast Roll-off' 'Slow Roll-off'
  Item0: 'Fast Roll-off'
Simple mixer control 'Stereo Upmixing',0
  Capabilities: enum
  Items: 'Front' 'Front+Surround' 'Front+Surround+Back' 'Front+Surround+Center/LFE' 'Front+Surround+Center/LFE+Back'
  Item0: 'Front+Surround+Center/LFE+Back'

```


This

Simple mixer control 'Line',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [off]


means my sound card only has mono even on line in?

---

### Post by occasional expert on 2013-05-14
When given a problem like yours, my "guy who makes things work" mind can't let go.  I spent some time with Google.

On an open suse forum, there's a thread ASUS Xonar DX :=> Headache".  Poking around there has me asking whether when you run "amixer scontents" you get something like this in the middle -

Simple mixer control 'Line',0
Capabilities: cswitch cswitch-joined
Capture channels: [COLOR=#ff0000]Mono[/COLOR]

If so, I now know just enough about alsa to be reasonably sure there's a problem in the driver for your card.  The behavior of alsamixer and arecord off the input in line in mode tells me this is what you'll most likely see.

The Line control SHOULD have capture channels of "Front Left - Front Right" in order to grab stereo.  That's what the Line channel says on all my cards.  But the alsa config dump I happened on for your card, along with a bit of info on alsa driver development I saw gives me the strong notion that there's an error is in the driver where it enumerates and registers all the control elements on your card.

I'd recommend poking around on alsa-project.org for filing a bug if you see the above.  If you don't see this, well......I'm stumped.

PCI-X was new to me, so I also did a bit of reading on it.  You're using a server grade system in contrast to all of mine being consumer.  I confess I've yet to try any PCI-e or PCI-X sound cards - all the sound stuff I've poked at was either on the mobo or old 5 volt legacy PCI stuff.

EDIT:  Didn't see your edit of your most recent post until after I wrote the above.  We seem to be thinking along the same lines.

I very seriously doubt that the line in provision in your sound card hardware is mono only...that'd be taking a step backward a few decades.  I think it's far more likely there's a problem in the driver.  I would see if there's a forum on the alsa website you can file your issue on.

---

### Post by MakOwner on 2013-05-14
Well, this is the amixer output from the old PCI sound card -- it may be the driver as you say, but comparing this with the PCIe card the capture section here indicates stereo capture I suppose -- I see the 'Capture' device is in the 'on' state and when running arecord with stereo vumeter you see activity on both channels.

Time to look for another sound card?  Pulse aduio maybe?  I have never messed with it except in some of the desktop stuff and I cna't say I know anything about it.



Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]




```

amixer 
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'PCM Out Path & Mute',0
  Capabilities: enum
  Items: 'pre 3D' 'post 3D'
  Item0: 'pre 3D'
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Line In->Rear Out',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]


```

---

### Post by occasional expert on 2013-05-14
> **MakOwner said:**
> Well, this is the amixer output from the old PCI sound card -- it may be the driver as you say, but comparing this with the PCIe card the capture section here indicates stereo capture I suppose -- I see the 'Capture' device is in the 'on' state and when running arecord with stereo vumeter you see activity on both channels.

Time to look for another sound card?  Pulse aduio maybe?  I have never messed with it except in some of the desktop stuff and I cna't say I know anything about it.



On your old board, everything I see that might be in the capture path from line in to Capture is marked as stereo, so you're recording stereo.

If I were in your place I'd definitely be looking at another board for recording.  

Are you running any other PCI-X boards in your new machine?  If not, you might be able to use your legacy PCI card in one of the PCI-X slots in the new machine.  From what I read, one problem is that if you do that the legacy board drags all the other PCI-X cards down to its slower bus speed, which might make a fancy fiber optic network interface or a hot disk interface on the bus run a lot slower.

What I've learned from this exercise is that I'll part with my old legacy SoundBlaster emu10k-based PCI boards when they're pried from my cold dead machines.  I'm now even willing to try legacy PCI to PCI-e adapters for them in a new machine rather than replace them with newer, much "smarter" cards that might entail the kind of troubles you're having.  

I haven't the foggiest idea what to recommend for you to buy.  There are a few recommendations on the alsa web site, so you might look there.  You also might Google the model you're considering along with the keyword linux and spend some time reading the threads. 

As for PulseAudio or JACK or any number of audio systems available for Linux, if alsa can't deal with your sound card they won't help as they use alsa as a backend to get to the sound card.  The first seems to be a way to allow multiple processes access to the sound card at the same time without blocking.  The second attempts to put a completely format independent front end over all the sound equipment using an internal uber-format for all the sound (double precision floating point), giving a lot of processing overhead and other junk I simply don't need.

I looked at both as I needed a way to send the output of arecord to two places at the same time - one making a standard mp3 of the audio, and the other making an Apple iOS compatible HTTP Live Stream for listening on my IToys.  I ended up writing my own simple server and client using a Unix domain socket instead of using PulseAudio or JACK.  Streaming to iToys from linux is as bad a tar pit as the one you're in, but that's another story.

---

### Post by MakOwner on 2013-05-14
Double post.

---

### Post by MakOwner on 2013-05-15
Putzing about with it here this monring... Thinking that the issue was in the ASUS sound card or drivers or whaterver, I switched the HR78 from being the input to the new sound card to being the input to the old sound card.  I had to increase the gain on the capture device but it does look like I am captuing stereo from it now.  I went ahead moved the table top radio output to the ASUS card and tried a recording there, just for grins.  It looks like the table top radio is being recorded in stereo too.  I think.  Just started looking at it.  

Could this be a side effect of the impedance or lack thereof?

---

