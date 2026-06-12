---
title: "nee help with sound input and/or Creox"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by zami on 2007-07-15
I'm trying to get Creox working on my husbands machine.  It all LOOKS to be running, but we aren't getting any sound.

What I've got
--------------
-Creative Labs Audigy2 sound card 
-ye old electric geetar, pluged into soundcard line in 
-qjackctl - gui for jack
-creox
Other "jack" related items that show up in Synaptic
-jackd
-ladcca2
-libasound2-plugins
-libjack0.100.0-0
-libjack0.100.0-dev
possibly more, but perhaps I'm missing something vital?

What I've done
--------------
-I start up qjacktctl and press start
-Fire up creox and press "start"
-Un-muted and cranked up the volume of all the input/recorder sources in the Volume Control panel
-Turned up speakers and master volume
-Play the guitar, and hear nothing.

If I try "connect" in qjackctl I can see that Creox is interfacing with jack.

In System > Preferences > Sound Preferences, I see
Default Mixer Tracks Device = Audigy 2 Platinum, so it appears I've got the right sound card.

I don't have any problems playing sounds, movies, midis, mp3s, frozen bubble music, etc, but I don't seem to be capturing sound.

There's no mic on this machine if that affects anything.  The sound-input jack seems to work just fine in Windows (for example the online guitar tuner at workshoplive.com "hears" the guitar) so it's not a  physical issue with my card.

Sorry this post got so long.  Any help would be very appreciated!

-zami

edit:
Still need help with this.
I'm not sure what alsa relations I might need installed.  Right now I've just got 
alsa-base
alsa-utils
gnome-alsamixer
gstreamer0.10-alsa
and a medly of lib files that intalled along with other programs

Also, after tinkering with a TON of settings, I can get feedback noise from Creox if also running something like Amarok - has nothing to do with the guitar but.. hell I don't know if that's progress or if I've no broken something further.
Uhg.
Five hours of my Sunday - gone!

-zami

---

### Post by raydar on 2007-12-02
On my first real foray into using an electric guitar with UbuntuStudio (which is to say with any Linux audio app other than Audacity), I wanted to try Creox, and I have it running on the realtime 2.6.22-14 kernel in Gutsy, with Jack and Ardour.

I can hear the clean signal of my guitar, plugged into my sound card's Line In (equal success plugged directly in or connected through a compressor pedal as an ad-hoc preamp). But I cannot seem to get any guitar signal out of Creox; maybe the signal is not getting *into* Creox, but I can't tell (it has no level meter, that I've found). The only output I can get from Creox is a loud, something-is-not-right feedbacky/laser-gun type noise, by bringing the "Drive" slider of Creox's "Distortion" tab's "Main Drive" section up beyond 50%. (My mic input is muted, line-in is at 2/3, and it didn't really sound like feedback-proper; if you've ever turned the delay-time knob on a delay pedal while a note is playing, it sounds kind of like that.) No other Creox controls, including levels, seems to have any effect.

In the Jack connections, I made sure the signal was routed from alsa_pcm-capture to Creox, Creox to Ardour, and Ardour to alsa_pcm-playback; and with the QAMix mixer, I made sure no volume levels were zeroed that shouldn't be. But recording in Ardour gave me either a flatline or that very loud, crazy noise from Creox. So I went back to Jack's connections and took Creox out of the path, hooking alsa_pcm-capture directly to Ardour's audio input; and *that* gave me a nice, clean guitar signal at a normal volume level.

Since I'm a newb at this, I'm sure I'm just doing something wrong; I wish I could attach a screenshot of my Jack connections to make giving me the clue I need easier. Anyone encounter similar Creox trouble, and hopefully a solution?

---

### Post by zettberlin on 2007-12-02
First:

You need to connect alsa_pcm_in (your soundcard) to creox_in to make it work 

and:

Creox is not actively developed (wich is quite sad - I like it a lot) so it does not fit perfectly into the jackd ecosystem of today and I did not get real good results with my guitar and it either...

So you may want to try something else? I made up a patch for alsa modular synth (search for ams in synaptic) called ams-guitrack, get it here:

[http://gnupc.de/~zettberlin/law/patches/ams/ams-guitrack_RC1.ams](http://gnupc.de/~zettberlin/law/patches/ams/ams-guitrack_RC1.ams)

once you have installed ams:

1.) start jackd with qjackctl
2.) start ams 
3.) load the patch ams-guitrack_RC1.ams and open View/Parameter View
4.) connect alsa_pcm_in with ams_in and ams_out with alsa_pcm_out
5.) connect your guitar and adjust the gainsettings in the parameter-view


for me this gives the results I would expect from a middleclass- Marshall-Stack with a 19"-MultiFX involved. If everything is set just right, you should be able to control distortion by turning the volume-knob on the guitar ;-)
If unbearable hiss/noise spoils the party try to fiddle with the gain/threshold/ratio-faders of the compressor-section in tab CAPS-AMP of the Parameter-View. 
You can also store your own presets here - since I strongly abhor from such vices as factory-presets, I got only 2 very basic ones in the patch itself...


enjoy, and as always: any comments are welcome :-)

---

