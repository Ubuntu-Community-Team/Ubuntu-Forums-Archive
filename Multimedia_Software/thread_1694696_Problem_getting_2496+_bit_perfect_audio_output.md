---
title: "Problem getting 24/96+ bit perfect audio output"
date: 2011-02-24
forum: Multimedia Software
---

### Post by Rizlaw on 2011-02-24
I've spent several weeks researching this on these forum and others across the web. I haven't found a simple, straight forward solution to my issue, so it's time to post:

I'm running Ubuntu 10.04.2 LTS 32bit. I also have an Asus Xonar STX sound card and my EVGA Classified 760 MB has Intel HDA which I have turned off in the BIOS. 

My problem is that while I can get 16/44.1 digital out from the Xonar STX to my external DAC (Wyred4Sound DAC-2), I can not get any of my 24/96 or 24/192 FLAC files to output at the higher bit rates. Ubuntu seems to be down sampling all my HD content to 16/44 digital output according to the display on my external DAC. To confirm this, while playing one of my 24/96 HD files I opened a terminal and ran:sudo cat /proc/asound/card0/pcm0p/sub0/hw_parms

The result, shown in the attached jpg confirms that the 24/96 HD FLAC file is being output as 2 channel 16/44 audio.

Other sniffing around my system shows that Ubuntu seems to have set the default audio output at 16/44.1 and I can find no setting to change this default in alsamixer or gnome-alsamixer.

I tried JACK and with JACK I can set 960000 or 1920000 sampling and it works, but the problem with JACK, as I see it, is that it outputs "everything" at the set rate instead of changing with the actual bit/sampling rate of each individual FLAC file. 

My not so simple question is: how do I get UBUNTU to do what is so easy to do in Windows XP?

P.S. I don't want to remove PULSEaudio, last time I tried that, my entire sound setup got borked.

Thanks for any good answers.

---

### Post by shantiq on 2011-02-25
```

```i really doubt ubuntu is the problem here must be settings

i play 24/96 all the time even 53-bit 192kH w64 files and no problem    see image attached


so it must be something to do with hardware or settings   i have changed nothing from the time i installed maverick and it plays straight off on a very normal computer


you do not say but which player are you running /?


maybe try SoX  ```
sudo apt-get install sox
```  ```
play *.flac
```or whichever extension you are using     at least i hope  it will tell you what you are playing and if it is playing right

---

### Post by Rizlaw on 2011-02-25
> **shantiq said:**
> ```

```i really doubt ubuntu is the problem here must be settings

i play 24/96 all the time even 53-bit 192kH w64 files and no problem    see image attached


so it must be something to do with hardware or settings   i have changed nothing from the time i installed maverick and it plays straight off on a very normal computer


you do not say but which player are you running /?


maybe try SoX  ```
sudo apt-get install sox
```  ```
play *.flac
```or whichever extension you are using     at least i hope  it will tell you what you are playing and if it is playing right

Thanks for the reply. As for players, I tried Rhythmbox, Quod Libet, Potamus and Banshee. They all give the same results.

I tried your suggestion and attached is the result I got. However, I don't think what you are referring to in your screen shot, or in mine, represents the "actual" bit stream output of the Xonar STX to my external DAC. I believe all versions of Ubuntu may be set to down sample audio to standard 16/44.1 regardless of the audio files actual bit rate. I could be wrong about this, but I think what you are reading (referring to in your reply) is the encoded "specification" of the actual soundfile, NOT what is actually being output to the external DAC during playback. My external DAC displays the actual sampling rate received and in all cases it reads 44.1K no matter what SOX says. In Windows XP this does not happen and the file plays back at the correct 24/192 setting.

If you are outputting your HD flac files to an external DAC, does it have a display that confirms it is receiving what you "believe" is being output via your toslink/coax S/PDIF connection?

---

### Post by shantiq on 2011-02-25
hi again    sorry i have no experience of external DAC (sounds cool)

what i suggested was simply to see what you were getting on the ubuntu setup    and clearly your files are read fine    and some info is not going out to the external or maybe it is

can you not tell by listening if it is 24 or 16 ?  there is usually a marked difference in quality


saw your file was SACD   could it be a factor?
:KS:KS will need someone much more knowledgeable than myself; no doubt someone will appear

best of luck

---

### Post by cchhrriiss121212 on 2011-02-25
You are correct, Pulse sets a default sample rate. See this thread to change it:
[http://ubuntuforums.org/showthread.php?p=6225657](http://ubuntuforums.org/showthread.php?p=6225657)

It seems as though (like jackd) it will not change dynamically according to what sound file you play, but I can't see that as a major issue. Upsampling will not use that much in terms of CPU.

---

### Post by samfuzz on 2011-02-25
have look to mpd : Music Player daemon
[http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)
it can output directly to alsa low level options, and more (oss, pulse jack .....)

google : "bit perfect mpd 24/96"
you will find explanations

[http://www.musicpd.org/forum/index.php?topic=2303.0;wap2](http://www.musicpd.org/forum/index.php?topic=2303.0;wap2)

and try perhaps (not sure) 
deadbeef
[http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)

---

### Post by Rizlaw on 2011-02-26
> **samfuzz said:**
> have look to mpd : Music Player daemon
[http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)
it can output directly to alsa low level options, and more (oss, pulse jack .....)

google : "bit perfect mpd 24/96"
you will find explanations

[http://www.musicpd.org/forum/index.php?topic=2303.0;wap2](http://www.musicpd.org/forum/index.php?topic=2303.0;wap2)


Thanks Samfuzz, your links ultimately caused me to retry MPD. The first time around I could not get MPD to work, but after a little more reading I finally got it going. It works well and with the default /etc/mpd.conf file properly edited for my Asus Xonar STX card:

> # An example of an ALSA output:
#
audio_output {
	type		"alsa"
	name		"My ALSA Device"
	device		"hw:0,1"	# optional
#	format		"44100:16:2"	# optional
#	mixer_device	"default"	# optional
#	mixer_control	"PCM"		# optional
#	mixer_index	"0"		# optional
}
#

it outputs bit perfect 16/44, 24/96 and 24/192 audio based on the file playing at the time. Exactly what I expect and want.

The downside to using MPD is the choice of gui clients. I am trying "gmpc" and "ario" from the Ubuntu 10.04 repositories and neither one automatically picks up my album art correctly (I spent weeks scanning all my CD covers and carefully setting up my folders, so this is not good!), nor do they seem to be getting my entire database of music listed correctly. I guess this is really an MPD problem.

My remaining annoyance is that Ubuntu's Pulse Audio implementation is still not set up, by default, to pass raw digital data streams out of the s/pdif jacks (without mixing or re-sampling) so that external DACS and home receiver can properly process the data outside of the computer for a better result. I'm also PO'd that Ubuntu doesn't provide more granular controls in their "Sound Preferences" to allow those who care about these things to easily select unmixed, non re-sampled digital data output via s/pdif and USB.

Thanks to all who answered my post with helpful suggestions.

---

### Post by samfuzz on 2011-02-27
gmpc can retrieve local album art with this plug-ins
[http://gmpc.wikia.com/wiki/GMPC_PLUGIN_MDCOVER](http://gmpc.wikia.com/wiki/GMPC_PLUGIN_MDCOVER)
there are other clients that can do this (quimup .....)
and
[http://gmpc.wikia.com/wiki/GMPC_PLUGIN_EXIFTOOL](http://gmpc.wikia.com/wiki/GMPC_PLUGIN_EXIFTOOL)
[http://gmpc.wikia.com/wiki/GMPC_PLUGIN_COVERAMAZON](http://gmpc.wikia.com/wiki/GMPC_PLUGIN_COVERAMAZON)
[http://gmpc.wikia.com/wiki/GMPC_PLUGIN_DISCOGS](http://gmpc.wikia.com/wiki/GMPC_PLUGIN_DISCOGS)

other ideas perhaps it could help

* you can try gmusicbrowser (can output directly to gstreamer/alsa)
with the latest ppa
[https://launchpad.net/~shimmerproject/+archive/ppa](https://launchpad.net/~shimmerproject/+archive/ppa)

* it seems you can directly output through gstreamer 'alsa with  clementine
[http://code.google.com/p/clementine-player/](http://code.google.com/p/clementine-player/)

* you can try directly modify gstreamer-properties
[http://www.webupd8.org/2010/03/how-to-switch-to-alsa-or-oss-instead-of.html](http://www.webupd8.org/2010/03/how-to-switch-to-alsa-or-oss-instead-of.html)

---

### Post by Rizlaw on 2011-02-27
> **samfuzz said:**
> gmpc can retrieve local album art with this plug-ins
[http://gmpc.wikia.com/wiki/GMPC_PLUGIN_MDCOVER](http://gmpc.wikia.com/wiki/GMPC_PLUGIN_MDCOVER)
there are other clients that can do this (quimup .....)
and
[http://gmpc.wikia.com/wiki/GMPC_PLUGIN_EXIFTOOL](http://gmpc.wikia.com/wiki/GMPC_PLUGIN_EXIFTOOL)
[http://gmpc.wikia.com/wiki/GMPC_PLUGIN_COVERAMAZON](http://gmpc.wikia.com/wiki/GMPC_PLUGIN_COVERAMAZON)
[http://gmpc.wikia.com/wiki/GMPC_PLUGIN_DISCOGS](http://gmpc.wikia.com/wiki/GMPC_PLUGIN_DISCOGS)


Thanks. I have the latest version of gmpc with all plug-ins installed (version 0.20) from the launchpad ppa:gmpc-trunk/gmpc-stable. The "MDCOVER" plugin is included. When I updated the database, I saw it very quickly scan and find 1600+ items (I presume my scanned jpg covers), it simply made 1600+ pretty empty CD covers! Somewhere there is either a bug or I'm doing something wrong. At the moment I'm not sure what to do. 

The interesting thing is that using "Screenlets" I can activate the "Now Playing" widget, set it for MPD and lo and behold I get the cover art for the playing song, but it won't display in the gmpc pop-up notification on each track change. Go figure.

> 
* you can try gmusicbrowser (can output directly to gstreamer/alsa)
with the latest ppa
[https://launchpad.net/~shimmerproject/+archive/ppa](https://launchpad.net/~shimmerproject/+archive/ppa)


I prefer gmusicbrowser to almost all other linux music players, except, perhaps, for Quod Libet which is also excellent but not as pretty with cover art. I have the latest version installed via the ppa you mentioned. I'm not sure that simply selecting "alsa" in gmusicbrowser will accomplish the same thing that MPD does (i.e., playing bit perfect 24/96 music and correctly switching between 16/44.1 and 24/96 on the fly for each track played.


> 
* you can try directly modify gstreamer-properties
[http://www.webupd8.org/2010/03/how-to-switch-to-alsa-or-oss-instead-of.html](http://www.webupd8.org/2010/03/how-to-switch-to-alsa-or-oss-instead-of.html)

This looks interesting, but the post doesn't indicate whether, once the changes are made, that you will be able to obtain on the fly 16/44.1 - 24/96 bit perfect switching audio output.

If I could just get gmpc to show all of the scanned covers in each music folder I would be home free until Ubuntu gets it's audio act together regarding hi-rez audio playback without remixing/re-sampling.

Again, thanks for your help and suggestions.

---

### Post by samfuzz on 2011-02-28
> **Rizlaw said:**
> 
I prefer gmusicbrowser to almost all other linux music players, except, perhaps, for Quod Libet which is also excellent but not as pretty with cover art. I have the latest version installed via the ppa you mentioned. I'm not sure that simply selecting "alsa" in gmusicbrowser will accomplish the same thing that MPD does (i.e., playing bit perfect 24/96 music and correctly switching between 16/44.1 and 24/96 on the fly for each track played.


i'm not sure too, this is something i'd like to know, but in advanced options, you can set the device hw:0,1 for gstreamer/alsa


same for quodlibet (pipeline option : alsasink device=hw:0,1)
and in general options for gstreamer with gconf-editor

(i don't see any reason why gstreamer couldn't be bit perfect)

---

### Post by Rizlaw on 2011-02-28
> **samfuzz said:**
> i'm not sure too, this is something i'd like to know, but in advanced options, you can set the device hw:0,1 for gstreamer/alsa


Looks like we're gaining on the problem. My desktop theme makes "advanced options" so small and difficult to read that I totally overlooked it. The "hw:0,1" works, but I haven't fully tested it with a "mix" of 16/44.1 - 24/96 tracks yet. But, it looks very promising.:D 

> same for quodlibet (pipeline option : alsasink device=hw:0,1)
and in general options for gstreamer with gconf-editor

(i don't see any reason why gstreamer couldn't be bit perfect)

Will try Quod Libet tonight.

---

### Post by shantiq on 2011-02-28
> **cchhrriiss121212 said:**
> You are correct, Pulse sets a default sample rate. See this thread to change it:
[http://ubuntuforums.org/showthread.php?p=6225657](http://ubuntuforums.org/showthread.php?p=6225657)

It seems as though (like jackd) it will not change dynamically according to what sound file you play, but I can't see that as a major issue. Upsampling will not use that much in terms of CPU.



if pulse does not do the  switchover automatically why not pick alsa instead    it is easily done with


```
gtreamer-properties
```


which brings the Multimedia Systems Selector and then pick alsa



does that not work around that problem or am i talking through my hat?:KS

---

### Post by Rizlaw on 2011-02-28
> **shantiq said:**
> if pulse does not do the  switchover automatically why not pick alsa instead    it is easily done with


```
gtreamer-properties
```


which brings the Multimedia Systems Selector and then pick alsa



does that not work around that problem or am i talking through my hat?:KS

Shantiq,

The method you point out was also illustrated in this web link:
[http://www.webupd8.org/2010/03/how-to-switch-to-alsa-or-oss-instead-of.html](http://www.webupd8.org/2010/03/how-to-switch-to-alsa-or-oss-instead-of.html)

As pointed out in the above link, at the very bottom of the instructions, it says:

> However, using this GUI method, you cannot change it individually for audio, video or conferencing so for these, use the command-line tweaks above.

I'm not exactly sure what it means, but changing it individually for each music player I use seems like a more precise method for controlling bit perfect audio playback. For my purposes, everything other than audio, can be run at standard 44.1k/48k through Pulse. Although, I can see how those listening to Bluray movies with HD audio would want bit perfect digital pass through sound as well.

Update: Using "gstreamer-Properties" gui method - making the following changes did not work for Rhythmbox:

Default Output Plugin: custom
Device: Digital
Pipeline: alsasink device="hw:0,1"

Rhythmbox still outputs 24/96 data streams as 16/44.1 streams.

Thanks.

---

### Post by samfuzz on 2011-03-02
another thing for bit perfect :
all volume controls on the computer should be set to 100% or maximum volume

---

### Post by Jeek Elemental on 2011-04-01
try Minion as front for mpd, very nice. Its a plugin for firefox.
You can use it over network, so all your laptops etc. can control your mpd machine.

---

### Post by ronalde@launchpad.net on 2011-11-03
Inspired by [Bit-perfect audio in Linux at 88.2 and 176.4 now possible]("http://www.computeraudiophile.com/content/Bit-perfect-audio-Linux-882-and-1764-now-possible") I created a setup at home which I share at [How to setup a bit-perfect digital audio streaming client with free software (with LTSP and MPD)]("http://www.lacocina.nl/artikelen/how-to-setup-a-bit-perfect-digital-audio-streaming-client-with-free-software-with-ltsp-and-mpd").

In short, my wanted setup had the following requirements:

[LIST]
[*]having bit-perfect audio for all digital formats accepted by my DAC
[*]having the freedom of only using free software
[*]having the freedom of only using open non patent encumbered file formats
[*]having the freedom to use any client device as a streaming digital audio device
[*]having the freedom to use any device for controlling the streaming digital audio device (acting like a “media controller”)
[/LIST]

To achieve these goals I’ve made the following choices:

[LIST]
[*]create a LTSP environment using my desktop PC as the LTSP server
[*]installing a MPD client on the desktop PC or Android client acting as a media controller
[*]using an old HP t5725 thin client as the LTSP client
[*]this thin client will also act as a (headless) MPD server
[/LIST]

The result is whopping! I can plug in any PXE-capable PC or laptop to my LAN and connect it to my DAC with USB. After booting it, 15 seconds later it is a bit perfect audio streaming client. I can use any PC, laptop or PDA to control the media and browse through my playlists and music library.

Have fun!

---

