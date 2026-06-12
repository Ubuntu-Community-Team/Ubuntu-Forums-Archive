---
title: "HOWTO: Compiling Audacity from source to work with JACK"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Ng Oon-Ee on 2008-11-14
Hi all,

Feels like I've been through every google page on the given title, and none really helped. Most blog-posts just said "ah, set this and it'll work" and the directions are skimpy because this will only work on THEIR setup. The mailing-lists were a bit more helpful, but most advocated just killing JACK to use Audacity, which obviously doesn't make sense if you're using Audacity in conjunction with other sound programs, especially the extremely cool assortment of JACK software, as well as for very very low latency.

So, anyway, I assume if you're reading this you already know about JACK and Audacity and why you'd want them. If you don't, and only want to use Audacity without the hassle of JACK (this means Audacity can be the only thing playing sound/recording sound at the time you're using it), then just kill JACK, or better yet, don't have it installed. Audacity will work fine with 'padsp audacity', which stops Pulseaudio (another thing which doesn't work well with Audacity).

As a side-note, before I even got to this I followed [this terrific guide]("http://ubuntuforums.org/showthread.php?t=843012") to setting up Pulseaudio and JACK properly. I'd suggest you do this first, if you think there's something wrong with your current configuration.

If you want to use JACK for professional recording, I hear Ardour is leagues better than Audacity. I've never used it, though I have it installed as part of Ubuntu Studio, simply because my recording needs are very simple, low-latency and recording in conjunction with playing back, with some optional running of additional filters/playing of background music external to Audacity.

So, on to the (admittedly brief) instructions. First,you'll need to uninstall and totally remove audacity if its already been installed. You may want to start downloading the latest audacity source at this time from [their sourceforge here.]("http://audacity.sourceforge.net/download/beta_source") It can take a while, depending on your connection. While waiting for that, continue on.

```
sudo apt-get purge audacity
```.

Then, you'd need to install the following packages. Not all of them may be needed, as I said, I spent a day on this, so some of them may not be required, but unless your hard disc is REALLY full they won't make a difference.

```
sudo apt-get update
sudo apt-get install libwxgtk2.8-dev libvorbis-dev libflac-dev libflac++-dev libmp3lame-dev libmad0-dev libid3tag0-dev libsoundtouch1-dev liblrdf0-dev portaudio19-dev libportaudio0 libportaudio2 libportaudiocpp0 libjack-dev libjackasyn0 libjack0.100.0-dev
```

The first dependency is for the GUI of Audacity. Thanks to mocha for his help in pointing this out.

The next few, up to liblrdf0-dev, are codec-specific. I include them there just so your compiled audacity will have as near to full ability to decode/encode audio files. However, some of those come from the medibuntu repository, which you should add if you haven't already. If this is illegal for you in your country, then please remove the offending packages, it won't affect the final result except for the decoding/encoding capabilities.

As for the 4 portaudio packages, I'm not sure they're required, since the downloaded audacity has its own Portaudio sources within. I have them, though, maybe you'd like to run through the install WITHOUT them first to see if its fine. If it is (and please ensure you do not have those packages beforehand) then please tell me, I'll modify this post. The final libjack-dev, libjackasyn0, and libjack0.100.0-dev are, I think, the most important.

After that, download the latest Audacity if you have not done so from [their sourceforge here.]("http://audacity.sourceforge.net/download/beta_source"). Untar the file to a folder in your home directory (this makes it easy, for permissions sake). Change directory to the directory you untarred audacity's source to. Assuming you untarred to your home directory, then:-

```
cd ~/audacity-src-1.3.6
```

Obviously, replace the version number/folder with whatever you have.

Then, simply run:-

```
./configure
```

Now, check all that output, the last lines should start with "Finished configure:" and list down all your libraries, whether using local or system libraries. You can go through this to check if something you wanted was not configured. Scroll up a bit more, beyond some lines that looks like this:-
```
configure: ---------------------------------------
configure: Including support for OSS
configure: Including support for ALSA
configure: ---------------------------------------

```
You'll also come across some lines looking like this:-
```
=== configuring in lib-src/portmixer (/home/ngoonee/audacity-src-1.3.6/lib-src/portmixer)
configure: running /bin/bash ./configure '--prefix=/usr/local/'  '--with-wx-config=/usr/bin/wx-config' '--with-pa-include=../portaudio-v19/include' --cache-file=/dev/null --srcdir=.

```
About twenty lines past that, you'll come to something like this:-
```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for JACK... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes

```
The line you're looking for is the middle one, which says that JACK is detected on your system. After that, run:-

```
make
sudo make install
```

And start-up your brand-new Audacity (Jack will need to be running). Go the Edit->Preferences. Under Audio I/O, set Playback to JACK Audio Connection Kit: system and Recording to JACK Audio Connection Kit: system.

Hope that works for you. If you have any questions or suggestions please let me know, I'll see what I can do to help.


P.S - If you do decide to undo what you've done, its very simple, just run

```
sudo apt-get purge libvorbis-dev libflac-dev libflac++-dev libmp3lame-dev libmad0-dev libid3tag0-dev libsoundtouch1-dev liblrdf0-dev portaudio19-dev libportaudio0 libportaudio2 libportaudiocpp0 libjack-dev libjackasyn0 libjack0.100.0-dev
```

If you've completed your install, go to your source code directory and run

```
sudo make uninstall
```

P.S 2 - I'd suggest, again, that you check out [this very cool thread]("http://ubuntuforums.org/showthread.php?p=6173793") for running Pulseaudio with JACK. With that, you can do really cool things like using Jack's patchbay to connect Pulseaudio's playing music directly to Audacity's recording function, for perfect, no-loss recording of something you're playing. Please remember that piracy is BAD, however. Ubuntu stands for freedom, not anaXrchy =)

EDIT 22nd Nov 2008: Added suggested corrections by mocha. Thanks loads!
EDIT 16th Nov 2008: Added another plug for Markbuntu's guide to Multiple Sound Solution (ALSA w Pulseaudio)

---

### Post by mocha on 2008-11-21
Thanks for the guide, I've been wanting to make Audacity work with Jack.  In your dependancies installation line you are missing the "install" switch, and libsoundtouch1.dev should be libsoundtouch1-dev.  You also need libwxgtk2.8-dev to build Audacity.  Although I didn't try, I believe an "apt-get build-dep audacity" will take care of all the dependancies.  Finally, in your "undo" guide, you will need to do a "make uninstall" from the source directory.  You didn't build and debs with your guide, so using apt-get isn't going to work.

---

### Post by mocha on 2008-11-21
Here's a quick guide to use the newly compiled Audacity with Jack to record the "stereo mix" (audio coming out of your speakers):


Start Jack Control and the jackd server.  Start Audacity.

Begin playback of the audio source (webpage audio, streaming audio, etc).  Open the PulseAudio Volume Control, move the source's playback stream to the PulseAudio Jack sink.

In output devices, set the Jack sink as default.  In input devices, set the Jack source as default.

Open one each of the PulseAudio playback and recording VU meters, move both of their streams to the PulseAudio JACK Sink.

Start the recording in Audacity, then go to the Jack Control connections box and connect the PulseAudio JACK Sink output port to the PortAudio Input Port.

I noticed that the PortAudio Input Port doesn't show up in the Jack connections box until you press record in Audacity, so just start the recording, make the connection, and later you can cut out the first few seconds of silence.

:popcorn:

---

### Post by Ng Oon-Ee on 2008-11-21
> **mocha said:**
> Thanks for the guide, I've been wanting to make Audacity work with Jack.  In your dependancies installation line you are missing the "install" switch, and libsoundtouch1.dev should be libsoundtouch1-dev.  You also need libwxgtk2.8-dev to build Audacity.  Although I didn't try, I believe an "apt-get build-dep audacity" will take care of all the dependancies.  Finally, in your "undo" guide, you will need to do a "make uninstall" from the source directory.  You didn't build and debs with your guide, so using apt-get isn't going to work.

Thank you, especially concerning your 'make uninstall'. As you can see, I'm prone to typos =).

---

### Post by cwsnyder on 2008-11-25
This looks to be the place to ask this question:  I didn't know about the conflict between Audacity and Jack, and I installed both.  Neither worked and using the Synaptic manager to delete both and re-install either Audacity or Jack/Ardour still did not allow me to record from the line-in jack on my motherboard sound system.

What is my next step to get one or the other to record?

---

### Post by Ng Oon-Ee on 2008-11-25
> **cwsnyder said:**
> This looks to be the place to ask this question:  I didn't know about the conflict between Audacity and Jack, and I installed both.  Neither worked and using the Synaptic manager to delete both and re-install either Audacity or Jack/Ardour still did not allow me to record from the line-in jack on my motherboard sound system.

What is my next step to get one or the other to record?

Just a note, on Ubuntu (and other Linux distros) uninstalling and reinstalling programs isn't very likely to help with most issues. Its the configuration files (which aren't uninstalled) which make the difference.

Anyway, apologies if I'm mistaken, but the way you're asking your question leads me to believe that you're not very familiar with Jack or sound on Linux. If this is so, I doubt your initial problem is Jack and/or Audacity. Please run soundrecorder and see if it records. If it does, then I'd hazard a guess that Pulseaudio is in control of your device, and Jack has no access to it (how do you startup Jack, using qjackctl or jackd?).

In case that's what you're seeing, then please read up these two howtos:-

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
[http://ubuntuforums.org/showthread.php?t=843012]("http://ubuntuforums.org/showthread.php?t=843012")

Those are very detailed and would explain things much better than I ever could. If you have further problems you can either ask there or here. This thread is specifically for getting a version of Audacity that works with Jack. It assumes that Jack is already working, if that is not the case the threads above would help more.

---

