---
title: "Finally: Digital AC-3 surround sound with pulseaudio (aka Surround Sound Awesomeness)"
date: 2010-10-29
forum: Multimedia Software
---

### Post by oblib on 2010-10-29
Here is the update to the old thread that somehow disappeared "HOWTO: A52 Encoded 5.1 Surround Sound Awesomeness with PulseAudio and ALSA on Hardy" thread (archived [here]("http://www.allquests.com/question/1709610/HOWTO-A52-Encoded-51-Surround-Sound-Awesomeness-with-PulseAudio-and-ALSA-on-Hardy.html")). See also this [bug report]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348353").

There are two steps here: add the a52 plugin, and tell pulseaudio to use it.

_Step 1:_
Go to a terminal and do the following:
```

sudo bash
echo "pcm.a52 {
  @args [CARD]
  @args.CARD {
    type string
  }
  type rate
  slave {
    pcm {
      type a52
      bitrate 448
      channels 6
      card $CARD
    }
  rate 48000 #required somehow, otherwise nothing happens in PulseAudio
  }
}
" > /etc/asound.conf
cd /tmp
apt-get source libasound2-plugins
apt-get build-dep libasound2-plugins
apt-get install libavcodec-dev
cd alsa-plugins-*
./configure
make
cd a52/.libs
cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/alsa-lib/
cd /tmp
rm alsa-plugins-* -rf

```
_Step 2:_
Either reboot or type the following (while still root):
```

alsa reload
killall pulseaudio

```
Pulse should come back on its own unless you disabled autospawn.

Now pulse should be aware of your digital surround output. Go to System -> Preferences -> Sound. Click on the "Hardware" tab and change the profile to one of the 'Digital Surround 5.1' profiles. Play some sound (I like to test with [www.pandora.com](www.pandora.com)) and enjoy!

If it doesn't show up, it probably means that alsa didn't create it correctly. To test if alsa sees the a52 device, type:
```
aplay -D a52:0
```
If it errors out (audio open error: No such file or directory) then that means it did not like your asound.conf settings. You might learn something by looking at the output of 'sudo alsa reload' or just 'aplay'. 

To see if it works, you can test with this command:```
speaker-test -Da52:0 -c6
```
One other useful debug tool is to disable autospawn in /etc/pulseaudio/client.conf (uncomment the autospawn line) and kill pulseaudio. Then if you run 'pulseaudio -vv' you can see what pulse is doing. Change the number of 'v's for more information.

**Always double check alsamixer if things seem weird.**

---

### Post by craigcoffman on 2010-11-01
This seems to be exactly what I'm looking for but I'm unsure as to whether I am to replace CARD with the card number, name or hw:0 or what?  Also unsure as to whether all instances need to be replaced.

--
craig

---

### Post by mgmeskill on 2010-11-01
oblib!  You are amazing!  Your instructions worked perfectly for my ALC888 on-board sound connected via s/pdif (optical) to my Yamaha.

I followed your instructions verbatim on a freshly installed Ubuntu 10.10.  1 reboot later, digital 5.1 working.

You have really made my day!  I hope you are enjoying the beverage of your choice right now!

-Mike

---

### Post by craigcoffman on 2010-11-02
Still no joy here.  If I leave the asound.conf file verbatim as above, I do see the 5.1 surround setting appear in my pulseaudio configuration, but attempting to play any sound with either audacious or xine simply crashes pulseaudio & alsa.  I have to do a alsa reload & kill pulseaudio & let it respawn.  But still no sound.

Trying these items before  crashing pulseaudio:

aplay -D a52:0 gives no errors (or any output at all)

speaker-test -D a52:0 -c6 likewise gives no errors, but produces no sounds.

syslog does show these errors:

Nov  2 06:32:09 sirguy pulseaudio[2258]: module-alsa-card.c: Failed to find a working profile.
Nov  2 06:32:09 sirguy pulseaudio[2258]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="pci-0000_04_00.1" card_name="alsa_card.pci-0000_04_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

---

### Post by craigcoffman on 2010-11-02
Alright,I figured out that the alsa side of thing WAS working.. after enabling the digital output in the alsamixer, I could hear the 5 speaker test fine.  However, pulse audio still crashes if set to the new setting of Digital 5.1 surround.

Using audacious as my player, I am able to get SOME files to play directly to ALSA & I do hear 5.1 output there.. I gather that is a file-specification issue on the files that will not play.

I really would like to get pulse-audio to use the new setting though.  Appreciate any follow-up ideas any one might have.

---

### Post by oblib on 2010-11-02
I've bolded the final advice I had, to check alsa mixer settings. craigcoffman, your next step should be to tell pulse to stop autospawning and run it verbosley from the terminal. See the second to last tip on how to do that. Hopefully pulse will tell you why it's crashing before it crashes.

---

### Post by som21 on 2010-11-03
i tried to follow your guide;but it informed me the need to download 29MB file.when i pressed 'y' and enter,the process aborted.and now after rebooting ubuntu has no sound at all.please help me.thanks in advance

here is the terminal response:

```
root@som-laptop:~# echo "pcm.a52 {
>   @args [CARD]
>   @args.CARD {
>     type string
>   }
>   type rate
>   slave {
>     pcm {
>       type a52
>       bitrate 448
>       channels 6
>       card $CARD
>     }
>   rate 48000 #required somehow, otherwise nothing happens in PulseAudio
>   }
> }
> " > /etc/asound.conf
root@som-laptop:~# cd /tmp
root@som-laptop:/tmp# apt-get source libasound2-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'alsa-plugins' as source package instead of 'libasound2-plugins'
NOTICE: 'alsa-plugins' packaging is maintained in the 'Bzr' version control system at:
https://code.launchpad.net/~ubuntu-core-dev/alsa-plugins/ubuntu
Please use:
bzr get https://code.launchpad.net/~ubuntu-core-dev/alsa-plugins/ubuntu
to retrieve the latest (possibly unreleased) updates to the package.
Need to get 474kB of source archives.
Get:1 http://in.archive.ubuntu.com/ubuntu/ lucid/main alsa-plugins 1.0.22-0ubuntu6 (dsc) [2,181B]
Get:2 http://in.archive.ubuntu.com/ubuntu/ lucid/main alsa-plugins 1.0.22-0ubuntu6 (tar) [456kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ lucid/main alsa-plugins 1.0.22-0ubuntu6 (diff) [15.5kB]
Fetched 474kB in 1min 13s (6,417B/s)                                           
sh: dpkg-source: not found
Unpack command 'dpkg-source -x alsa-plugins_1.0.22-0ubuntu6.dsc' failed.
Check if the 'dpkg-dev' package is installed.
E: Child process failed
root@som-laptop:/tmp# apt-get build-dep libasound2-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'alsa-plugins' as source package instead of 'libasound2-plugins'
The following NEW packages will be installed:
  autotools-dev build-essential cvs debhelper diffstat dpkg-dev g++ g++-4.4
  gcc-4.4-multilib gcc-multilib gettext html2text intltool-debian lib64asound2
  lib64asound2-dev lib64gcc1 lib64gomp1 libasound2-dev libavahi-client-dev
  libavahi-common-dev libc6-amd64 libc6-dev-amd64 libdbus-1-dev libglib2.0-dev
  libice-dev libjack-dev libmail-sendmail-perl libpthread-stubs0
  libpthread-stubs0-dev libpulse-dev libsamplerate0-dev libsm-dev libspeex-dev
  libspeexdsp-dev libstdc++6-4.4-dev libsys-hostname-long-perl libx11-dev
  libxau-dev libxcb1-dev libxdmcp-dev libxt-dev po-debconf quilt
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev xz-utils
  zlib1g-dev
0 upgraded, 49 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.5MB of archives.
After this operation, 84.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

```
please help me.there is no sound at all.i just now want to get back the sound.is it possible?or do i have to go for a fresh install?

---

### Post by oblib on 2010-11-03
som21, try deleting the asound.conf file and rebooting. ```
sudo rm /etc/asound.conf
```That's the only system change you made, otherwise I can't imagine what went wrong.

---

### Post by som21 on 2010-11-03
ok;i'll try and let you know.but why did it abort?any idea?

---

### Post by som21 on 2010-11-03
ok;i'll try and let you know.but why did it abort?any idea?

---

### Post by som21 on 2010-11-04
yes sound is back.thanks.but why did it abort after pressing 'enter'?any suggestion?

---

### Post by oblib on 2010-11-04
That's just a typical apt-get command, so something must have gone wrong with that. Did your internet disconnect or anything? You can try just the apt-get command again until it works, and then if it does, do all the other steps.

---

### Post by som21 on 2010-11-05
no internet is connected.i tried it 3times before posting;all the times it aborted after pressing enter.
will try the apt-get command separately and let you know
thanks

---

### Post by michikommader on 2010-11-23
Heyho!

Thanks so far. I had to use ```
card 0
``` instead of ```
card $CARD
``` and now I have the possibility to choose new 5.1 devices for sound output.

The bad thing is that I only get scratching noise into my receiver. It displays some digital signal coming in but I can not get clear sound.

Any ideas? Michi

---

### Post by oblib on 2010-11-23
What do you get when you do 'speaker-test -Da52:0 -c6'? It should do noise to each of the speakers in turn.

---

### Post by michikommader on 2010-11-24
Oh sry, I forget to post about that.
```
 aplay -D a52:0
```gives only silence and 
```
speaker-test -Da52:0 -c6
```gives indeed noise.

The thing is that when I was using Ubuntu 9.04 I never had problems even with AC3 passthrough with alsa out of different applications. This does not work in 10.04, neither in 10.10 anymore. It all results in screeching, scratching noise and now I'm trying to get it to work with a52 plugin :-/

Following tips from [http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut) does not improve anything.

Greets, Michi

---

### Post by michikommader on 2010-11-30
Ok,

the a52 stuff works now, I did not change anything, just waited one week and tested again today. But pulseaudio sound server crashes after around 20sec while playing over my new devices. According to my receiver all sound I play comes in as DD 5.1, even stereo and it sounds really nice but breaks off into hissing and cracking and scratching when pulseaudio crashes.

I wish I could get ac3-passthrough to work but this results in hissing sound as well, but already from the beginning.

This all worked once in 9.04 ... 

Greets, Michi

---

### Post by mc4man on 2010-12-16
Two things to note if any issues with this method, (which will work fine

It's quite possible that apt-getting the build-deps will fail from the root terminal prompt - better to just install them first 
```
sudo apt-get build-dep libasound2-plugins
```

Edit: also install these 
```
sudo apt-get install libavcodec-dev libavformat-dev
```

It's also possible that the echo command will fail to add  $CARD to the 12th line, happened here twice on 2 different installs, best to check /etc/asound.conf before restarting to see if this shows, if red isn't there then add
```
channels 6
      card [COLOR="Red"]$CARD[/COLOR]
    }

```

If 2 channel output (fl, fr, sub) for music is desired then both audacious and mplayer can bypass pulse - audacious in pref.'s - audio - set output to alsa, plugin pref. to iec958...
for mplayer in ~/.mplayer/config this
ao=alsa:device=spdif

Also can add this, will be ignored on regular music files
afm=hwac3

---

### Post by prabath_fun on 2010-12-30
Thanks. I will try...

---

### Post by Dr. Kylstein on 2011-01-14
For me this appears to work until I try playing something. Then my surround card disappears from pavucontrol and the app uses the internal stereo instead. I'm using 10.04 with a CMI8768.

P.S. It reappears if I restart pulse, only to repeat the same results.

---

### Post by loeppel on 2011-01-15
Same Problem here (as Dr. Kylstein described it).
It works fine using only alsa, pulseaudio seems to have a problem with a52.
(tested with speaker-test).
Sound Card: 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
Ubuntu 10.04.

greets,
loeppel

---

### Post by elitenoobboy on 2011-01-29
After I kill pulseaudio as root, it doesn't come back. It does not seem to like being started as root and I get a home directory not ours error, but if starting it as a user, I get this:
$ pulseaudio 
E: module-udev-detect.c: inotify_add_watch() failed: Permission denied
E: module.c: Failed to load  module "module-udev-detect" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.


The first time after I did the instructions, nothing in the profiles changed, so I tried changing card $CARD to card 0 to see if that would help, and now I am getting that error. It doesn't seem to go away if I get rid of asound.conf.

---

### Post by Dr. Kylstein on 2011-02-22
My problem seems to be gone after upgrading to 10.10. I'm not sure if it was part of the upgrade or if a package was updated since I last tried.

---

### Post by bigbadbradman on 2011-02-28
I am using 10.10 and cannot get 5.1 surround digital output thru SPDIF to work. 

I am really green and do not understand how to follow this initial post.

This is driving me crazy. I spent a bunch of money on surround speakers and a really mean sub.

Can anyone to me a little better on how to follow the first post.

---

### Post by drejom on 2011-05-10
Just tried this following the instructions on this page:
[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio]("https://help.ubuntu.com/community/DigitalAC-3Pulseaudio")

And it worked perfectively on my inbuilt 82801I (ICH9 Family) HD Audio Controller under Natty.

Cheers!

---

### Post by aglc2005 on 2011-06-11
> **Dr. Kylstein said:**
> For me this appears to work until I try playing something. Then my surround card disappears from pavucontrol and the app uses the internal stereo instead. I'm using 10.04 with a CMI8768.

P.S. It reappears if I restart pulse, only to repeat the same results.

I am having the same issue as well. If I kill pulsaudio and then set it back to Ditigal Stereo Out it works. What info would you need to help me resolve this?

---

### Post by Yfrwlf on 2011-07-25
> **bigbadbradman said:**
> I am using 10.10 and cannot get 5.1 surround digital output thru SPDIF to work. 

I am really green and do not understand how to follow this initial post.

This is driving me crazy. I spent a bunch of money on surround speakers and a really mean sub.

Can anyone to me a little better on how to follow the first post.

The first thing you have to do is go to your sound settings and mess around there.  Select the output hardware you're using, and change the output to digital for if you're using coax or optical.  If optical you should see the light come on when you do that.  If you still don't you might try checking alsamixer and seeing if it is turned off there, but you shouldn't have to do that of course.

Pulseaudio not containing the same variety of digital surround output options when it contains many options for analogue seems really silly.  Does anyone know if this is a hardware profiling issue, i.e. not knowing that some hardware has surround sound available digitally when it does, or something else?  Though if you know a sound system can do analogue surround sound, obviously it can do it digitally as well, so that'd be a lame excuse...

Regardless, I hope this fix is included in future versions of Pulseaudio and Linux systems by default so those options will be available out-of-the-box.  Most all sound systems are going to be digital-only now days, and these options not being available even with brand new hardware on brand new Linux distros is scary.  Anyone know if this is fixed in Ubuntu 11.10?

---

### Post by fu11meta1 on 2011-08-02
Thank you so much. I'm a complete newbie and this worked perfectly for me with HTO Striker 7.1 CM8738 under 11.04.

---

### Post by ACLBandit on 2011-09-03
Amazing that NOTHING else got it at all, and this set of things very nearly got it.

Still not there, though! :(

I have a 7.1 setup; I don't know if my PC hardware supports 7.1, but I'm using the SPDIF output -- 5.1 output mapped to the proper speakers would be enough for me.

Right now, things are coming out as follows:

Front left: ALL left speakers
Rear left : ALL left speakers
Front Center: ALL speakers
Front Right: ALL right speakers
Rear Right: ALL right speakers
Subwoofer: Subwoofer (1 outta 7! It's sad that this is improvement)

The fact that it's more than stereo is a good thing, but I dunno where to go from here.

EDIT: Also, I'm on 11.04 -- I haven't had to ask for help in FOREVER and my tags still say 9.04 -- lawls?

---

### Post by BicyclerBoy on 2011-09-03
This solved thread needs to die because the thread title & the ubuntu wiki page keep talking about "with pulse audio"..

This solution is an alsa based AC3 encoder soln used to output matrix encoded 5.1 AC3 over S/PDIF via digital pass-thru' to an external decoder HT amp.

With 10.04 alsa 1.0.24:
- if you point pulse-audio at the alsa a52 device it will crash.
- channel ordering is still wrong.
- after one hour it stops with horrendous noise
- audio quality does not match direct AC3 output.

---

### Post by ACLBandit on 2011-09-03
> **BicyclerBoy said:**
> This solved thread needs to die because the thread title & the ubuntu wiki page keep talking about "with pulse audio"..

This solution is an alsa based AC3 encoder soln used to output matrix encoded 5.1 AC3 over S/PDIF via digital pass-thru' to an external decoder HT amp.

With 10.04 alsa 1.0.24:
- if you point pulse-audio at the alsa a52 device it will crash.
- channel ordering is still wrong.
- after one hour it stops with horrendous noise
- audio quality does not match direct AC3 output.

I completely understand that this is "alsa-based pass through." I understand that this is relatively crap compared to a functional, true PulseAudio setup.

However, since I have tried everything else I can find on the subject, and this at least produced *some* result, if I could tweak it for my setup it'd certainly be better than the stereo-only I've been stuck with.

There's the chance that there's another solution, though -- I guess I'll start a new thread. Was just hoping that someone watching this one could get me moving in the right direction.

---

### Post by BicyclerBoy on 2011-09-03
I can try to help..
You need to define exactly what you are trying to do..

I assume (totally non-judgemental) you are:
- a gamer
- play games that have 5.1 or 7.1 audio tracks.
- games don't support digital pass-thru' over S/PDIF
- You do not want to use analogue cables.
- You do not have an expensive pointless soundcard 
- You have an external HT amp with HDMI or S/PDIF inputs.
The alsa a52 encoder is a good solution..

If you have HDMI audio inputs on the amp then forget this a52 method.

What have you done so far ?
compiled the a52 encoder plugin ?
tested with speaker-test ?
speaker-test -c 6 -r 48000 -D a52

Use VLC & play a multichannel audio test track..
vlc --aout alsa --alsa-audio-device a52

I have a channel re-ordering/re-routing device setup if you need..

---

### Post by ACLBandit on 2011-09-05
> **BicyclerBoy said:**
> I can try to help..
You need to define exactly what you are trying to do..

I assume (totally non-judgemental) you are:
- a gamer
- play games that have 5.1 or 7.1 audio tracks.
- games don't support digital pass-thru' over S/PDIF
- You do not want to use analogue cables.
- You do not have an expensive pointless soundcard 
- You have an external HT amp with HDMI or S/PDIF inputs.
The alsa a52 encoder is a good solution..

If you have HDMI audio inputs on the amp then forget this a52 method.

What have you done so far ?
compiled the a52 encoder plugin ?
tested with speaker-test ?
speaker-test -c 6 -r 48000 -D a52

Use VLC & play a multichannel audio test track..
vlc --aout alsa --alsa-audio-device a52

I have a channel re-ordering/re-routing device setup if you need..

I play games, yes, but not really on my PC -- it's more for media (DVD/Blu-Ray playback/ripping, music in various places in my home, etc.).

I don't want to use analog cables since the digital option is available. I don't have an HDMI output on my PC at all.

The sound card is onboard -- part of the moBo, not separate.

Pulse Audio device manager shows only analog 7.1 (it's a six-stack sound thing in the back, but my audio receiver doesn't have inputs like that) and digital stereo.

I want true digital 5.1 (or 7.1, if available, for those few things that support it). If 7.1 is not possible with my card, 5.1 is sufficient -- my audio receiver has PLIIx, Neo 6, etc. that will split it to 7.1 effectively (or not -- depends on how picky I'm being any given time). The digital stereo-to-PLIIx method gets the job done, but it's not the same as six or eight discrete channels (obviously). 

I have tried installing the driver from Realtek (hoses the sound entirely, and sucks to remove -- if anyone finds this thread via Google, I recommend not trying it). I've tried tinkering about with module loading for "6stack-dig" to what appears to be no result. I've tried numerous things in .asoundrc, but can't get it exactly right.

Also, it functions properly under Windows via SPDIF (which is, as one might expect, about the only thing Windows does correctly for me), so hardware is fine. 

The sound receiver is an Onkyo HT-S6100, if that's necessary information.

I've been on Ubuntu for a few years now, and I'm not afraid of command line or technical details -- I just know very little about sound hardware. I'm willing to learn, but I don't know where to start. 

Thank you.

---

### Post by BicyclerBoy on 2011-09-06
You should playback any media with AC3 (DD5.1) or DTS directly to the HT amp.
This outputs digital pass-thru' over S/PDIF..
vlc --aout alsa --alsa-audio-device iec958
(vlc has gui preferences setting for spdif pass-thru')
(there are similar cmd line opts for mplayer etc..)
MythTV & XBMC output AC3/DTS direct to iec958
You can not share the alsa spdif iec958.

Pulseaudio does not support pass-thru' in 10.04, situation may have improved.
You do not need any external driver software for normal mobo soundcards.

The alsa a52 plugin is only useful for sharing dmix/volume control or for multi-channel audio (FLAC AAC OGG etc ) & for people without HDMI HT amp. But then the problem is the audio quality is not right & the channel order is still messed up. A patch was made in 2009 which made it worse. And now it will not compile against later ffmpeg.

---

### Post by ACLBandit on 2011-09-06
> **BicyclerBoy said:**
> You should playback any media with AC3 (DD5.1) or DTS directly to the HT amp.
This outputs digital pass-thru' over S/PDIF..
vlc --aout alsa --alsa-audio-device iec958
(vlc has gui preferences setting for spdif pass-thru')
(there are similar cmd line opts for mplayer etc..)
MythTV & XBMC output AC3/DTS direct to iec958
You can not share the alsa spdif iec958.

Pulseaudio does not support pass-thru' in 10.04, situation may have improved.
You do not need any external driver software for normal mobo soundcards.

The alsa a52 plugin is only useful for sharing dmix/volume control or for multi-channel audio (FLAC AAC OGG etc ) & for people without HDMI HT amp. But then the problem is the audio quality is not right & the channel order is still messed up. A patch was made in 2009 which made it worse. And now it will not compile against later ffmpeg.

That's basically what I have been doing. When I encode DVDs with 5.1 mixes, I've always used AC3 to make sure the surround mix works.

However, I just got a bluray drive, and was using MakeMKV to stream the playback to VLC via the "network" (in this case, localhost). I made the assumption that the reason the playback was only in stereo was because of the lack of digital 5.1 output in Pulse, which is not exactly an assumption that I based on anything sennsible, now that I think about it.

I was hoping there was a better solution than what I had been doing. As it is, I guess I'll poke about with MakeMKV's settings and VLC's, and try that command you provided. Worst case I'll research TrHD playback on Linux or rip the blurays I want to play and use AC3 for their sound instead.

Thanks for your help -- I'll let you know what I come up with.

---

### Post by ACLBandit on 2011-09-06
No amount of fiddling with MakeMKV or VLC would get the job done. 

However, passing those options to VLC on startup DID fix my issues. I could almost swear that in old versions of Ubuntu, VLC did that stuff automatically so my surround received what it needed to for the AC3 streams. Ever since the upgrade to 11.04, it's been stereo-only, all the way. 

After a bit more testing, it looks like it's not exclusive to the MakeMKV/VLC combo -- even my pre-encoded files with 5.1 AC3 tracks were only outputting stereo. I don't know if the problem is with Pulse or VLC at this point, but either way, this will certainly do for now.

As long as I start VLC every time with the ALSA options, it works beautifully. I'll start changing over all of my "Open with VLC" settings to that command instead. 

Thanks again -- that fixed my issues.

---

### Post by SL666 on 2011-09-11
BRAR!

thanks for the

> vlc --aout alsa --alsa-audio-device iec958

last update seems to have removed this from my vlc config - mythbox

---

### Post by crparis on 2011-09-15
I'm on Natty 11.04, ran through all of the steps and 5.1 audio is working great--thank you!  Since the changes, I've only noticed one issue and that's with Minecraft (OpenAL).

When I run it with Pulse audio, I get an error:

[INDENT]AL lib: pulseaudio.c:331: PulseAudio returned minreq > tlength/2' expect break up[/INDENT]

When I run it with Alsa (editing the alsoft.conf file and forcing alsa) I get a different error:

[INDENT]AL lib: alsa.c:642: set buffer time near failed: Invalid argument[/INDENT]

I know it's a bit of a stretch to post this here, but my problems only started after following this guide, so I'm hoping just to get a few tips on what I can look at for a fix.

Thanks again for all the tips!

:)

---

### Post by crparis on 2011-09-16
> **crparis said:**
> I'm on Natty 11.04, ran through all of the steps and 5.1 audio is working great--thank you!  Since the changes, I've only noticed one issue and that's with Minecraft (OpenAL).

When I run it with Pulse audio, I get an error:

[INDENT]AL lib: pulseaudio.c:331: PulseAudio returned minreq > tlength/2' expect break up[/INDENT]

When I run it with Alsa (editing the alsoft.conf file and forcing alsa) I get a different error:

[INDENT]AL lib: alsa.c:642: set buffer time near failed: Invalid argument[/INDENT]

I know it's a bit of a stretch to post this here, but my problems only started after following this guide, so I'm hoping just to get a few tips on what I can look at for a fix.

Thanks again for all the tips!

Just a quick update on this.  The fix I came up with seems to work so far, so I thought I'd add it to the thread just in case anyone else has this happen to them:

minecraft has libopenal.so in the ~/.minecraft/bin/native directory.  I backed up this file and then copied /usr/lib/libopenal.so.1 in place of it.  I fired minecraft back up and it worked without any errors or warnings.

minecraft in 5.1 audio is pretty neat as you can hear the rivers and mobs discretely in the surround channels when they are behind you.

\\:D/

---

### Post by am_i_registered on 2011-10-13
Hi all,

This was working great... but after upgrading to 11.10.. it's all gone!!!
Any ideas how to get it working again?

Many thanks in advance, D.

---

### Post by lgmickael on 2011-10-14
Bonjour from France,

[https://bugs.launchpad.net/ubuntu/oneiric/+source/alsa-plugins/+bug/872871]("https://bugs.launchpad.net/ubuntu/oneiric/+source/alsa-plugins/+bug/872871")

;)

---

### Post by Dr. Kylstein on 2011-10-15
I enabled the "proposed" repository and re-ran the steps, but pulse still doesn't show the digital 5.1 option in 11.10. Is there something else I need to do?

---

### Post by BicyclerBoy on 2011-10-15
Digital pass-thru' in pulse audio is now possible as of 3 weeks ago..(Pulse release V1.0).

This will take some time to percolate down into gstreamer, Ubu 11.04 etc..

[http://pulseaudio.org/wiki/Passthrough](http://pulseaudio.org/wiki/Passthrough)

---

### Post by lgmickael on 2011-10-15
> **Dr. Kylstein said:**
> I enabled the "proposed" repository and re-ran the steps, but pulse still doesn't show the digital 5.1 option in 11.10. Is there something else I need to do?

You must uninstall "a52" plugins before:

Delete "libasound_module_pcm_a52.la" and "libasound_module_pcm_a52.so" in usr/lib/alsa-lib/


Then do this again: [http://ubuntuforums.org/showpost.php?p=10044600&postcount=1]("http://ubuntuforums.org/showpost.php?p=10044600&postcount=1") but at the end, copy the a52 plugin to "/usr/lib/**_i386-linux-gnu_**/alsa-lib/" for installing plugin:

sudo cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/i386-linux-gnu/alsa-lib/

;)

---

### Post by Dr. Kylstein on 2011-10-15
> **lgmickael said:**
> You must uninstall "a52" plugins before:

Delete "libasound_module_pcm_a52.la" and "libasound_module_pcm_a52.so" in usr/lib/alsa-lib/


Then do this again: [http://ubuntuforums.org/showpost.php?p=10044600&postcount=1]("http://ubuntuforums.org/showpost.php?p=10044600&postcount=1") but at the end, copy the a52 plugin to "/usr/lib/**_i386-linux-gnu_**/alsa-lib/" for installing plugin:

sudo cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/i386-linux-gnu/alsa-lib/

;)
Still nothing. I'm using 64bit, is this supposed to be in i386?

---

### Post by am_i_registered on 2011-10-15
> **Dr. Kylstein said:**
> Still nothing. I'm using 64bit, is this supposed to be in i386?

I'm using 64bit, too... and it's not working for me either...

---

### Post by wakko000 on 2011-10-15
Not working for me. I using i386. I go back to 11.04.

---

### Post by lgmickael on 2011-10-15
"make uninstall" in /tmp/alsa-plugins-1.0.24/ (in your home when you have built the a52 plugin)

i386 for me.

---

### Post by am_i_registered on 2011-10-15
> **lgmickael said:**
> "make uninstall" in /tmp/alsa-plugins-1.0.24/ (in your home when you have built the a52 plugin)

i386 for me.

Could you please explain in detail what I have to do?
I'm not very good with these stuff... :(

Many thanks in advance, D.

---

### Post by wakko000 on 2011-10-16
Show the iecset command below:

josenilramos@santana-desktop:~$ iecset 
Mode: consumer
Data: audio
Rate: 48000 Hz
Copyright: permitted
Emphasis: none
Category: PCM coder
Original: original
Clock: 1000 ppm

In Natty :

josenilramos@santana-desktop:~$ iecset 
Mode: consumer
Data: non-audio
Rate: 48000 Hz
Copyright: permitted
Emphasis: none
Category: PCM coder
Original: original
Clock: 1000 ppm

I think this the solution. What do you think? In Oneiric i cannot change this how in Natty. 

iecset pro off audio off
snd_ctl_elem_write: Operation not permitted

Thanks in advance

Wakko

---

### Post by wakko000 on 2011-10-16
Back to Natty and now i very happy again :p

---

### Post by wakko000 on 2011-10-16
The best !

---

### Post by Iang123 on 2011-10-17
> **BicyclerBoy said:**
> Digital pass-thru' in pulse audio is now possible as of 3 weeks ago..(Pulse release V1.0).

This will take some time to percolate down into gstreamer, Ubu 11.04 etc..

[http://pulseaudio.org/wiki/Passthrough](http://pulseaudio.org/wiki/Passthrough)
Hi,

You mind telling me how to install it? I a, totally new to Linux and I just want to get this working. I have got the .gz file from the site, but I'm not sure what to do with it after that?

Could you help?

Cheers
Ian

---

### Post by am_i_registered on 2011-10-19
> **Dr. Kylstein said:**
> Still nothing. I'm using 64bit, is this supposed to be in i386?

Hi, I tried this but still no surround... the aplay hungs... w/o giving any results... tell me if it works for you...

sudo bash
echo "pcm.a52 {
  @args [CARD]
  @args.CARD {
    type string
  }
  type rate
  slave {
    pcm {
      type a52
      bitrate 448
      channels 6
      card $CARD
    }
  rate 48000 #required somehow, otherwise nothing happens in PulseAudio
  }
}
" > /etc/asound.conf
cd /tmp
apt-get source libasound2-plugins
apt-get build-dep libasound2-plugins
apt-get install libavcodec-dev
cd alsa-plugins-*
./configure
make
cd a52/.libs
cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/x86_64-linux-gnu/alsa-lib/
cd /tmp/alsa-plugins-*
cd /tmp
rm alsa-plugins-* -rf

---

### Post by wakko000 on 2011-10-19
I already do this but not working. :(

---

### Post by wakko000 on 2011-10-21
I run the script again today and restart the audio services Alsa and Pulse:
service alsa reload
killall pulseaudio 

Pulseaudio show IEC958/AC3 again.


Thanks

---

### Post by am_i_registered on 2011-10-22
> **wakko000 said:**
> I run the script again today and restart the audio services Alsa and Pulse:
service alsa reload
killall pulseaudio 

Pulseaudio show IEC958/AC3 again.


Thanks

Now it works for me, too! Maybe an update to the plugin did the trick? I don't know... but anyway we should mark the thread as SOLVED - but I guess it's already marked ... :)

---

### Post by abudabi on 2011-10-23
So are you guys saying that if I follow the script in the 1st post (along with the $CARD addition) it should work on oneiric after a repo update?

---

### Post by am_i_registered on 2011-10-23
> **abudabi said:**
> So are you guys saying that if I follow the script in the 1st post (along with the $CARD addition) it should work on oneiric after a repo update?

Hi, you should follow the script with the changes I've made.. just 5 posts above.. and add the $CARD to /etc/asound.conf if necessary.. in some systems it adds it automatically in others it doesn't...

But anyway it works in Oneiric 11.10!

---

### Post by abudabi on 2011-10-24
Thanks.. I took the plunge and did it.. and it worked beautifully...   *yay*  
 
 
Thanks all!

---

### Post by wakko000 on 2011-10-26
I discover this link:

[http://aepatrakov.narod.ru/dcaenc/](http://aepatrakov.narod.ru/dcaenc/)


Now is possible to obtain DTS on the fly such AC3.

Not work for me in Ubuntu 10.10.

You might try?

---

### Post by danwood76 on 2011-11-05
Hi All,

I have updated the wiki page with additions for Oneiric including a copy command that will work on all architectures. Hope this fixes the issues some of you are having!

[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

best regards,
Danny

---

### Post by andreas1327 on 2011-11-05
First of all let me say a BIG Hello to ubuntu community. I'm new to linux world and I trully hope that eventually Ubuntu will replace my windows installation that haunts my pc's through the years..

Overall I'm very pleased with Ubuntu and device support but still I haven't been able to make my Audigy 4 value plus my Logitech Z5500 work on digital out mode. I followed your steps and I managed to make Digital out show on pulseaudio hardware panel on my SB0400 Audigy2 Value (it's recognised like this), but it doesn't work. Not on test speakers, not on mp3's not on anything still...

I'm wondering if you've got any idea or any help that would be most helpful.. It's irritating not to be able to enjoy all those AC3 MKV's I got.. 

Thanks in advance..!

---

### Post by BicyclerBoy on 2011-11-05
This thread solution is not to **just** get digital pass-thru' over S/PDIF or HDMI.

The thread is about real-time encoding of PCM to AC3 bitstream over digital pass-thru'. (alsa plugin)

The last couple of threads were about real-time DTS encoder for alsa.

These are solns for folks with no HDMI audio but want to get multi-channel audio.

This thread has nothing to do with pulse audio either..

Outputting AC3/DTS soundtrack over S/PDIF or HDMI should be trivial for *buntu 9.04 and later..

Better to start a new thread..

---

### Post by wakko000 on 2011-11-07
Ok.

I start a new thread, sorry for any inconvenience.

---

### Post by rustyshank1 on 2011-11-10
I used this guide to get my 5.1 pass through over spdif and it worked however now i have no audio in flash videos all other apps seem to play audio fine mplayer and banshee both function. ive tried chromium still no sound... any help would be much appreciated.

---

### Post by dually on 2011-11-12
So, I've managed to follow AC-3 plugin guide and got surround working for my movies and startup jingle, but not for surround from browser, pandora.com etc. 

Any ideas?

---

### Post by MarcT666 on 2012-01-10
Same problem here.
5.1 thought HDMI works fine on Oneiric thanks to this tutorial in most multimedia applications (vlc, banshee, ...) but I have no sound in internet browsers (eg: chromium, firefox, opera,...) For instance I've got no sound when watching flash videos (but that's also the case when trying to listen to a shoutcast audio stream so this is not a flash related issue).
 
 
 
Any idea what the pb is?

---

### Post by TheFeshy on 2012-01-11
5.1 AC-3 in flash working - temporarily.

Using this guide, I was able to get 5.1 AC-3 sound for my media applications, but not for wine or flash.  Last week, I got it working for both.  In my case the trouble was wine and flash were 32 bit, and I am using Ubuntu 64 bit (at the time, 11.04.)  I created a chroot with the 32 bit version of Ubuntu 11.04, then followed the instructions here to build 32 bit versions of the plugins.  Then I copied the resulting files to my 64 bit install in the /usr/lib32 directory - and I got sound in flash and wine!

Unfortunately, this week I finally had the time to upgrade to 11.10, and this no longer works for me with this edition.  I am posting this in the hopes that my past success might help someone else more knowledgeable figure this out.

---

### Post by snoopo71 on 2012-02-06
Same problem here, I can't hear any flash sound.

---

### Post by MarcT666 on 2012-02-06
I found a temporary solution.
If you run firefox from the terminal, you will see in the terminal some error logs as sson as you try to watch a flash video. Mine were related to missing alsa libraries. I uninstalled the libasound library stuff and now it works (but then I dont have any 5.1) I'll try to come up with a solution. I've seen on the wiki page that they are special commands you need to do for Oneiric. That might be related to this....

---

### Post by giukas on 2012-02-20
Hi all
hope I can fin some helpafter reading abot this everywhere.
I had surround sound working very well on my xonar d2x up until about a week ago when a partial upgrade messed up everythinh (I suspect vlc mainly responsible).

However I was able to recreate the 5.1 digital profile but when I try to select it it shifts back automatically to stereo and sometimes analog.....although sound works but not as before of course)

I did everything I could in this thread but no luck
This is my asound.conf:

pcm.a52 {
@args [CARD]
@args.CARD {
type string
}
type rate
slave {
pcm {
type a52
bitrate 448
channels 6
card $CARD
}
rate 48000 #required somehow, otherwise nothing happens in PulseAudio
}
}

sudo apt-get build-dep libasound2-plugins
gives me this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'alsa-plugins' as source package instead of 'libasound2-plugins'
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded

aplay -D a52:0
nothing happens only cursor blinking

Thev system sees the card

any ideas?

---

### Post by giukas on 2012-02-20
anybody? please?

---

### Post by MIchMichou on 2012-03-15
Hi everyone, I tried eveyhting this thread says to do and.... I'm stuck with pulse audio not allowing me to play digital content through the SPDIF.

The A52 does not build has anyone encounters such a thing ?

---

### Post by BicyclerBoy on 2012-03-15
First be sure you want to use this encoder.
Do people with fancy soundcards want to use the AC3 encoder plug?
The modo chipset codec S/PDIF is just as good.
The alsa a52 plug has nothing to do with pulseaudio.

Recent releases of pulseaudio now supports AC3/DTS digital pass-thru' over S/PDIF. This has no bearing on the a52 plug. The alsa a52 plug outputs directly to the iec958 output device (alsa).

If you have a fancy soundcard you have paid for good analogue DACs & noise floor.

AC3 over S/PDIF is an option for those with older AVR HT amps (me) & do **not** want to use 5.1 discrete analogue cabling.
Your AVR may support 640K bitrate AC3.
An alsa DTS encoder (>1Mbps) would be a better option.
The alsa a52 uses ac3_fixed encoder in libavcodec.
The ac3 (float) in libavcodec has had a lot of recent improvements.

The a52 plug has been broken because of changes to libav packages (fixed -float changes).
The alsa code was not initialising some parameter.
At one point you had channel order mixed up or pulse-audio crashing.

Making a52 work: [disclaimer- tried with 10.04 (stock kernel) & alsa 1.0.24 user libraries & libavcodec53-extra-4.09 (JSeverison ppa).]
- Need libavcodec-extra (unstripped package)
- Get the alsa a52 (AC3) plug encoder source code from alsa website.
alsa-plugins-1.0.25.tar.bz2
- unpack & configure (check a52 enabled) & compile.
- copy the (2) lib files as per previous instructions.

Previous builds of this plug had:
- strange hi freq distortion
- fails after about 1 hour (must stop-start playback).
- channel order messed up (even with the libav version patch).

Unknown if:
- libavcodec ac3_fixed has had AQ improvements (as ac3 float)
- will this a52 plug build fail after 1 hr or 2 ..
- AQ good enough ?

---

### Post by MIchMichou on 2012-03-16
Well I don't have a fancy soundcard and I just wish to use both my analog 5.1 setup (a poor creative satellit speakers) and my real digital setup.

There's a coaxial cable going from my motherboard (an Asus p5Q deluxe) to my A/VR and that is why I'd like true digital soundtracks to pass trough !

THe way I seemed to get it to work was to install the a52 plugin. Pulseaudio does not support SPDIF passthrough as I still don't have anything going through my SPDIF output.

---

### Post by BicyclerBoy on 2012-03-16
True digital pass-thru' does not require the a52 plug. I would suggest that a52 plug is not true..

S/PDIF supports PCM stereo up to 96KHz 24bit (192K on pro gear).
Multi-channel audio must be encoded AC3/DTS 48KHz. This is a digital data bitstream & must be unmodified for the AVR HT amp to accept it.

The player s/w must configure the iec958 (S/PDIF) device to use digital pass-thru'.
So you can not have:
- soft vol
- mixers
i.e. no shared sound output.
The a52 plug allows all the above because it is using plughw device for input & iec958 for output

vlc -aout alsa -alsa-device iec958
or similar worked historically.
else use preferences & select spdif output

The recent pulseaudio releases do now support digital pass-thru'.
It is possible it can now support an AC3 encoder plugin..
Pulseaudio always supported PCM stereo over iec958.

speaker-test -c 2 -r 48000 -D iec958
speaker-test -c 2 -r 96000 -F S32_BE -D iec958
You can not use speaker-test to test multi-channel on iec958.

---

### Post by MIchMichou on 2012-03-19
> **BicyclerBoy said:**
> True digital pass-thru' does not require the a52 plug. I would suggest that a52 plug is not true..

S/PDIF supports PCM stereo up to 96KHz 24bit (192K on pro gear).
Multi-channel audio must be encoded AC3/DTS 48KHz. This is a digital data bitstream & must be unmodified for the AVR HT amp to accept it.

The player s/w must configure the iec958 (S/PDIF) device to use digital pass-thru'.
So you can not have:
- soft vol
- mixers
i.e. no shared sound output.
The a52 plug allows all the above because it is using plughw device for input & iec958 for output

vlc -aout alsa -alsa-device iec958
or similar worked historically.
else use preferences & select spdif output

The recent pulseaudio releases do now support digital pass-thru'.
It is possible it can now support an AC3 encoder plugin..
Pulseaudio always supported PCM stereo over iec958.

speaker-test -c 2 -r 48000 -D iec958
speaker-test -c 2 -r 96000 -F S32_BE -D iec958
You can not use speaker-test to test multi-channel on iec958.


THank you for your kind answer. 

Yes i know that pulse support pcim stereo but that is not what I want. I've been succesfully using SPDIF passtrhu in 10.04 for two years using alsa. I would like the same thing working just as well with pulse audio whereas it doesn't. 

I did try to force spdif output in VLC and even in XBMC but there ain't a sound coming out ! And when I try to change the sound preferences in pulse it doesn't allow me anything but stereo.

WHen trying 
speaker-test -c 2 -r 48000 -D iec958
I do have pink noise but on the front channels only and my decoder sees stereo.

Now one step has been accomplished and I thank you, i do have sound on my spdif output but it is still stereo....

---

### Post by BicyclerBoy on 2012-03-19
The latest release of pulseaudio does purport to support digital pass-thru' (AC3/a52, DTS).
But you will have to compile from source or wait 1 year for it appear in *buntu. There could be a pulse audio dev launchpad ppa.

So you can't use repo package pavucontrol etc to setup digital pass-thru'.

Your mobo (asus P5Q) audio works okay (*buntu10.04 alsa user 1.0.24) using:
- 96KHz 24bit PCM stereo
- AC3/DTS (48KHz) dig pass-thru' (AC3 640Kbps okay)
- alsa a52 plug 1.0.25 (640Kbps)

Over the years the a52 plugin has:
- worked almost
- mixed ch order
- crashed
- strange clicking noises after about 1 hr
- kills the pulse audio server
- alsa-1.0.25 sounds promising so far.

Note that MythTV & VLC (& XBMC i think) all build-in the a52 encoder, so they can also upmix &/or encode to AC3 but this only works if they can exclusively open & control S/PDIF output.

So VLC & XBMC can play multi-channel Ogg/AAC/FLAC (&AC3/DTS) & (re)-encode to AC3 & output using digital pass-thru' over S/PDIF.

Do you have azalia HDMI video card ? This can also appear as another S/PDIF.
Maybe you post 
aplay -l
aplay -L

The previous VLC cmd works for the old std version in 10.04..
vlc -aout alsa -alsa-device iec958
play a DVD; select the AC3 or DTS sound track..

---

### Post by MIchMichou on 2012-03-20
> **BicyclerBoy said:**
> The latest release of pulseaudio does purport to support digital pass-thru' (AC3/a52, DTS).
But you will have to compile from source or wait 1 year for it appear in *buntu. There could be a pulse audio dev launchpad ppa.

So you can't use repo package pavucontrol etc to setup digital pass-thru'.

Your mobo (asus P5Q) audio works okay (*buntu10.04 alsa user 1.0.24) using:
- 96KHz 24bit PCM stereo
- AC3/DTS (48KHz) dig pass-thru' (AC3 640Kbps okay)
- alsa a52 plug 1.0.25 (640Kbps)

Over the years the a52 plugin has:
- worked almost
- mixed ch order
- crashed
- strange clicking noises after about 1 hr
- kills the pulse audio server
- alsa-1.0.25 sounds promising so far.

Note that MythTV & VLC (& XBMC i think) all build-in the a52 encoder, so they can also upmix &/or encode to AC3 but this only works if they can exclusively open & control S/PDIF output.

So VLC & XBMC can play multi-channel Ogg/AAC/FLAC (&AC3/DTS) & (re)-encode to AC3 & output using digital pass-thru' over S/PDIF.

Do you have azalia HDMI video card ? This can also appear as another S/PDIF.
Maybe you post 
aplay -l
aplay -L

The previous VLC cmd works for the old std version in 10.04..
vlc -aout alsa -alsa-device iec958
play a DVD; select the AC3 or DTS sound track..


THanks again for all your answers.

Yesterday I had spdif dts/Ac3 passthrough for some time but after a reboot there wasn't anything left and i'm stuck with stereo sound again. 

```
$ aplay -l

**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Intel [HDA Intel], périphérique 0: AD198x Analog [AD198x Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 1: AD198x Digital [AD198x Digital]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0

$ aplay -L

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, AD198x Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Hardware device with all software conversions

```

---

### Post by am_i_registered on 2012-04-26
Hi all,

I've upgraded to Ubuntu 12.04 LTS and as expected my previous configuration for "Digital AC-3 surround sound with pulseaudio" is gone.
I tried to repeat the process (which was working on 11.10), but it gives me several errors and I cannot handle it... could you please help??

This is a copy of terminal:

```

am_i_registered@P5E-WS:~$ sudo bash
[sudo] password for am_i_registered: 
root@P5E-WS:~# echo "pcm.a52 {
> @args [CARD]
> @args.CARD {
> type string
> }
> type rate
> slave {
> pcm {
> type a52
> bitrate 448
> channels 6
> card $CARD
> }
> rate 48000 #required somehow, otherwise nothing happens in PulseAudio
> }
> }
> " > /etc/asound.conf
root@P5E-WS:~# cd /tmp
root@P5E-WS:/tmp# apt-get source libasound2-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'alsa-plugins' as source package instead of 'libasound2-plugins'
NOTICE: 'alsa-plugins' packaging is maintained in the 'Bzr' version control system at:
http://bazaar.launchpad.net/~ubuntu-audio-dev/alsa-plugins/ubuntu.precise
Please use:
bzr branch http://bazaar.launchpad.net/~ubuntu-audio-dev/alsa-plugins/ubuntu.precise
to retrieve the latest (possibly unreleased) updates to the package.
Need to get 347 kB of source archives.
Get:1 http://bg.archive.ubuntu.com/ubuntu/ precise/main alsa-plugins 1.0.25-1ubuntu1 (dsc) [1,797 B]
Get:2 http://bg.archive.ubuntu.com/ubuntu/ precise/main alsa-plugins 1.0.25-1ubuntu1 (tar) [332 kB]
Get:3 http://bg.archive.ubuntu.com/ubuntu/ precise/main alsa-plugins 1.0.25-1ubuntu1 (diff) [14.1 kB]
Fetched 347 kB in 4s (75.2 kB/s)     
gpgv: Signature made Thu 16 Feb 2012 04:48:34 AM EET using DSA key ID D06320CE
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./alsa-plugins_1.0.25-1ubuntu1.dsc
dpkg-source: info: extracting alsa-plugins in alsa-plugins-1.0.25
dpkg-source: info: unpacking alsa-plugins_1.0.25.orig.tar.bz2
dpkg-source: info: unpacking alsa-plugins_1.0.25-1ubuntu1.debian.tar.bz2
dpkg-source: info: applying arcam-av_uses_pthreads.patch
dpkg-source: info: applying use_libavutil.patch
root@P5E-WS:/tmp# apt-get build-dep libasound2-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'alsa-plugins' as source package instead of 'libasound2-plugins'
The following packages have unmet dependencies:
 libjack-dev : Depends: libjack0 (= 1:0.121.0+svn4538-3ubuntu1) but it is not going to be installed
E: Build-dependencies for libasound2-plugins could not be satisfied.
root@P5E-WS:/tmp# apt-get install libavcodec-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavcodec-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@P5E-WS:/tmp# cd alsa-plugins-*
root@P5E-WS:/tmp/alsa-plugins-1.0.25# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgfortran... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
./configure: line 18727: CC_NOUNDEFINED: command not found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... yes
checking for snd_pcm_ioplug_create in -lasound... yes
checking for JACK... checking for pulseaudio... yes
checking for samplerate... yes
checking for AVCODEC... yes
checking ffmpeg/avcodec.h usability... no
checking ffmpeg/avcodec.h presence... no
checking for ffmpeg/avcodec.h... no
checking libavcodec/avcodec.h usability... yes
checking libavcodec/avcodec.h presence... yes
checking for libavcodec/avcodec.h... yes
checking for speexdsp... yes
checking for speex_resampler_init in -lspeexdsp... yes
checking for plugins version... 1.0.25
configure: creating ./config.status
config.status: creating Makefile
config.status: creating oss/Makefile
config.status: creating pph/Makefile
config.status: creating jack/Makefile
config.status: creating pulse/Makefile
config.status: creating mix/Makefile
config.status: creating rate/Makefile
config.status: creating a52/Makefile
config.status: creating rate-lavc/Makefile
config.status: creating maemo/Makefile
config.status: creating doc/Makefile
config.status: creating usb_stream/Makefile
config.status: creating speex/Makefile
config.status: creating arcam-av/Makefile
config.status: creating config.h
config.status: executing depfiles commands

Plugin directory: /usr/lib/alsa-lib
ALSA_CFLAGS: -I/usr/include/alsa  
ALSA_LIBS: -lasound  
JACK plugin:        no
Pulseaudio plugin:  yes
  pulseaudio_CFLAGS: -D_REENTRANT  
  pulseaudio_LIBS: -lpulse  
Samplerate plugin:  yes
  samplerate_CFLAGS:  
  samplerate_LIBS: -lsamplerate  
Maemo plugin:       no
  Using Osso resource manager: no
A52, lavc plugins:  yes
  AVCODEC_CFLAGS:  
  AVCODEC_LIBS: -lavcodec  
  AVCODEC_HEADER: <libavcodec/avcodec.h>
Speex rate plugin:  lib
Speex preprocess plugin:  yes
root@P5E-WS:/tmp/alsa-plugins-1.0.25# make
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/bash /tmp/alsa-plugins-1.0.25/missing --run aclocal-1.11 -I m4
configure.in:15: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body
../../lib/autoconf/lang.m4:194: AC_LANG_CONFTEST is expanded from...
../../lib/autoconf/general.m4:2662: _AC_LINK_IFELSE is expanded from...
../../lib/autoconf/general.m4:2679: AC_LINK_IFELSE is expanded from...
../../lib/m4sugar/m4sh.m4:606: AS_IF is expanded from...
../../lib/autoconf/general.m4:2032: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2053: AC_CACHE_CHECK is expanded from...
m4/attributes.m4:87: CC_CHECK_LDFLAGS is expanded from...
m4/attributes.m4:104: CC_NOUNDEFINED is expanded from...
configure.in:15: the top level
 cd . && /bin/bash /tmp/alsa-plugins-1.0.25/missing --run automake-1.11 --foreign
configure.in:15: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body
../../lib/autoconf/lang.m4:194: AC_LANG_CONFTEST is expanded from...
../../lib/autoconf/general.m4:2662: _AC_LINK_IFELSE is expanded from...
../../lib/autoconf/general.m4:2679: AC_LINK_IFELSE is expanded from...
../../lib/m4sugar/m4sh.m4:606: AS_IF is expanded from...
../../lib/autoconf/general.m4:2032: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2053: AC_CACHE_CHECK is expanded from...
m4/attributes.m4:87: CC_CHECK_LDFLAGS is expanded from...
m4/attributes.m4:104: CC_NOUNDEFINED is expanded from...
configure.in:15: the top level
CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/bash /tmp/alsa-plugins-1.0.25/missing --run autoconf
configure.in:15: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body
../../lib/autoconf/lang.m4:194: AC_LANG_CONFTEST is expanded from...
../../lib/autoconf/general.m4:2662: _AC_LINK_IFELSE is expanded from...
../../lib/autoconf/general.m4:2679: AC_LINK_IFELSE is expanded from...
../../lib/m4sugar/m4sh.m4:606: AS_IF is expanded from...
../../lib/autoconf/general.m4:2032: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2053: AC_CACHE_CHECK is expanded from...
m4/attributes.m4:87: CC_CHECK_LDFLAGS is expanded from...
m4/attributes.m4:104: CC_NOUNDEFINED is expanded from...
configure.in:15: the top level
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure --no-create --no-recursion
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 3458764513820540925
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ANSI C header files... (cached) yes
checking if gcc supports -Wl,--no-undefined flag... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ALSA... yes
checking for snd_pcm_ioplug_create in -lasound... yes
checking for JACK... no
checking for pulseaudio... yes
checking for samplerate... yes
checking for AVCODEC... yes
checking ffmpeg/avcodec.h usability... no
checking ffmpeg/avcodec.h presence... no
checking for ffmpeg/avcodec.h... no
checking libavcodec/avcodec.h usability... yes
checking libavcodec/avcodec.h presence... yes
checking for libavcodec/avcodec.h... yes
checking for speexdsp... yes
checking for speex_resampler_init in -lspeexdsp... yes
checking for plugins version... 1.0.25
configure: creating ./config.status

Plugin directory: /usr/lib/alsa-lib
ALSA_CFLAGS: -I/usr/include/alsa  
ALSA_LIBS: -lasound  
JACK plugin:        no
Pulseaudio plugin:  yes
  pulseaudio_CFLAGS: -D_REENTRANT  
  pulseaudio_LIBS: -lpulse  
Samplerate plugin:  yes
  samplerate_CFLAGS:  
  samplerate_LIBS: -lsamplerate  
Maemo plugin:       no
  Using Osso resource manager: no
A52, lavc plugins:  yes
  AVCODEC_CFLAGS:  
  AVCODEC_LIBS: -lavcodec -lavutil  
  AVCODEC_HEADER: <libavcodec/avcodec.h>
Speex rate plugin:  lib
Speex preprocess plugin:  yes
 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating oss/Makefile
config.status: creating pph/Makefile
config.status: creating jack/Makefile
config.status: creating pulse/Makefile
config.status: creating mix/Makefile
config.status: creating rate/Makefile
config.status: creating a52/Makefile
config.status: creating rate-lavc/Makefile
config.status: creating maemo/Makefile
config.status: creating doc/Makefile
config.status: creating usb_stream/Makefile
config.status: creating speex/Makefile
config.status: creating arcam-av/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
(CDPATH="${ZSH_VERSION+.}:" && cd . && /bin/bash /tmp/alsa-plugins-1.0.25/missing --run autoheader)
configure.in:15: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body
../../lib/autoconf/lang.m4:194: AC_LANG_CONFTEST is expanded from...
../../lib/autoconf/general.m4:2662: _AC_LINK_IFELSE is expanded from...
../../lib/autoconf/general.m4:2679: AC_LINK_IFELSE is expanded from...
../../lib/m4sugar/m4sh.m4:606: AS_IF is expanded from...
../../lib/autoconf/general.m4:2032: AC_CACHE_VAL is expanded from...
../../lib/autoconf/general.m4:2053: AC_CACHE_CHECK is expanded from...
m4/attributes.m4:87: CC_CHECK_LDFLAGS is expanded from...
m4/attributes.m4:104: CC_NOUNDEFINED is expanded from...
configure.in:15: the top level
rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
make  all-recursive
make[1]: Entering directory `/tmp/alsa-plugins-1.0.25'
Making all in oss
make[2]: Entering directory `/tmp/alsa-plugins-1.0.25/oss'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -I/usr/include/alsa   -g -O2 -MT ctl_oss.lo -MD -MP -MF .deps/ctl_oss.Tpo -c -o ctl_oss.lo ctl_oss.c
../libtool: line 831: X--tag=CC: command not found
../libtool: line 864: libtool: ignoring unknown tag : command not found
../libtool: line 831: X--mode=compile: command not found
../libtool: line 997: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 998: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 1141: Xgcc: command not found
../libtool: line 1141: X-DHAVE_CONFIG_H: command not found
../libtool: line 1141: X-I.: command not found
../libtool: line 1141: X-I..: command not found
../libtool: line 1141: X-Wall: command not found
../libtool: line 1141: X-g: command not found
../libtool: line 1141: X-I/usr/include/alsa: No such file or directory
../libtool: line 1141: X-g: command not found
../libtool: line 1141: X-O2: command not found
../libtool: line 1141: X-MT: command not found
../libtool: line 1141: Xctl_oss.lo: command not found
../libtool: line 1141: X-MD: command not found
../libtool: line 1141: X-MP: command not found
../libtool: line 1141: X-MF: command not found
../libtool: line 1141: X.deps/ctl_oss.Tpo: No such file or directory
../libtool: line 1141: X-c: command not found
../libtool: line 1192: Xctl_oss.lo: command not found
../libtool: line 1197: libtool: compile: cannot determine name of library object from `': command not found
make[2]: *** [ctl_oss.lo] Error 1
make[2]: Leaving directory `/tmp/alsa-plugins-1.0.25/oss'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/alsa-plugins-1.0.25'
make: *** [all] Error 2
root@P5E-WS:/tmp/alsa-plugins-1.0.25# cd a52/.libs
bash: cd: a52/.libs: No such file or directory
root@P5E-WS:/tmp/alsa-plugins-1.0.25# cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/x86_64-linux-gnu/alsa-lib/
cp: cannot stat `libasound_module_pcm_a52.la': No such file or directory
cp: cannot stat `libasound_module_pcm_a52.so': No such file or directory
root@P5E-WS:/tmp/alsa-plugins-1.0.25# cd /tmp/alsa-plugins-*
root@P5E-WS:/tmp/alsa-plugins-1.0.25# cd /tmp
root@P5E-WS:/tmp# rm alsa-plugins-* -rf

```Errors appear during the "make" command and the folder a52/.libs is not created...

P.S. The thread was SOLVED for 11.10, but after 12.04 is not. If the administrators/moderators believe that I must create a new thread, I'll do it. I'm just writing here for consistency and hoping that other user of this configuration will be notified.

---

### Post by xzero1 on 2012-04-27
I may have gotten a bit further than you. The end of your compile log shows that libasound_module_pcm_a52.la and libasound_module_pcm_a52.so do not exist to be copied:

```
root@P5E-WS:/tmp/alsa-plugins-1.0.25# cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/x86_64-linux-gnu/alsa-lib/
cp: cannot stat `libasound_module_pcm_a52.la': No such file or directory
cp: cannot stat `libasound_module_pcm_a52.so': No such file or directory
root@P5E-WS:/tmp/alsa-plugins-1.0.25# cd /tmp/alsa-plugins-*
root@P5E-WS:/tmp/alsa-plugins-1.0.25# cd /tmp
root@P5E-WS:/tmp# rm alsa-plugins-* -rf 
```

In my case, this was because they were placed in different folders than the compile script expected. You must determine if and where they were created. If they were created, then the script must be changed to copy them to the correct location. See my post here:
[http://ubuntuforums.org/showthread.php?t=1961140&highlight=spdif]("http://ubuntuforums.org/showthread.php?t=1961140&highlight=spdif")

---

### Post by terran4000 on 2012-04-27
I had it magically working on 11.10, then I upgraded to 12.04 last night and it all worked until I opened the audio settings and clicked on a different profile, now the profile for Digital Surround sound 5.1+ doesn't even show up! Not cool at all.

All myself, as as I found out several others, do not have the profile option for "Digital Output Surround Sound (S/PDIF)" anymore!

> aplay -l

lists all the correct devices and all the surround sound options as well. It's just Ubuntu + the new pulseaudio sound settings control panel thing that are messed up. Haven't found a way around it yet. Even tried using the old tricks that got it all working in 11.10, alas no luck.

---

### Post by xzero1 on 2012-04-27
> **terran4000 said:**
> I had it magically working on 11.10, then I upgraded to 12.04 last night and it all worked until I opened the audio settings and clicked on a different profile, now the profile for Digital Surround sound 5.1+ doesn't even show up! Not cool at all.

All myself, as as I found out several others, do not have the profile option for "Digital Output Surround Sound (S/PDIF)" anymore!

> aplay -l

lists all the correct devices and all the surround sound options as well. It's just Ubuntu + the new pulseaudio sound settings control panel thing that are messed up. Haven't found a way around it yet. Even tried using the old tricks that got it all working in 11.10, alas no luck.

Did you actually hear 5.1 audio? My receiver says I get the 5.1 signal but when I playback a 5.1 channel test file I *hear* the sound downmixed to stereo.

---

### Post by terran4000 on 2012-04-28
Yup, back in 11.04 and 11.10 it was full blown 5.1 surround. Even my receiver was happily saying it was a true digital signal with surround sound! No downmixing or anything ... good stuff.

Worked in 12.04 as well until I touched the settings then my surround sound profile disappeared. >_> So I'm kinda pissed at myself for touching it! BUT ..

Big but (not butt), I found this. It's NOT a problem of us users (well, except for me I was an idiot). The problem is/was that the Ubuntu developer(s) for the control panel app removed the functionality to control profiles better. 

See this Launchpad bug report, my listing (PiotrKrzyzek) details a few things.

[URL="https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/972554"]https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/972554
[/URL]

Basically, the issue is this:

[LIST]
[*]Ubuntu happily and correctly detects all sound devices
[*]Ubuntu happily and easily detects all sound profiles (surround sound, 5.1, 7.1, digital, analog, ect...)
[*]Gnome-Control-Panel in Ubuntu 12.04 does NOT have the functionality anymore (read: removed) to select from all possible profiles
[/LIST]

I'm tempted to dabble into the code myself, though never having done gnome/ubuntu devel I wouldn't know where to start. Python? I could do ... no clue where to start, what to compile or what to edit with this. Meh, might look at it tomorrow though. *shrug*

Hopefully the developers put the proper profiles back in. I want my surround sound back instead of forcing my receiver to up-mix to 'DTS Movie Surround' >_> meh.

---

### Post by BicyclerBoy on 2012-04-28
If you are using mplayer XBMC MythTV VLC etc.. they can all output directly to the a52 AC3 encoder alsa plugin..They don't need the system/pulse audio settings to work..

Granted this doesn't help with games etc..

Considering that ubuntu has moved from ffmpeg/libav to forked Libav/libav..it is suprising the alsa plugin still works.

The previously compiled a52 plugin (about 11.04) would have been built against ffmpeg libavcodec.

speaker-test -c 6 -r 48000 -D pcm.a52

After determining if the plug is broken or just pulse-audio..
if Broken plug then:
- use source code from alsa project & real ffmpeg libavcodec.

Hopefully the latest 1.0.25 a52 encoder uses the better AC3_float encoder code in ffmpeg/libav because it was not the best before..

The a52 plug bitrate can be increased from 448 -->640 (max). check your amp can handle it.

---

### Post by xzero1 on 2012-04-28
I found *my* problem. Its was simply that my receiver was not set properly. I had not used surround sound in a while. The compiled a52 plugin now works (at least initially). I have never used the applet since it has never worked for me before and spdif seems to be stereo only. Why should any spdif be treated as stereo only? There should not be a set number of channels when using spdif it should depend only on the source.

---

### Post by BicyclerBoy on 2012-04-28
You don't understand..
S/PDIF is only stereo PCM, it does not have the bandwidth for multi-channel uncompressed PCM audio.
The maximum is normally 96KHz/24bit (32bit frame). 192KHz in rare cases but not Toslink/optical. So max 12MHz for pro gear.

The a52 plugin & AC3/DTS are methods for sending matrix encoded audio in a digital bit-stream that can be sent over S/PDIF at 48KHz (only) as digital data encoded/compressed.
Both AC3 & DTS are defined with 48KHz bit clock==1.54Mbps.
The actual bitrate for AC3 is 640Kbps (max) & DTS is about 1.5Mbps.

Surround sound is also ambiguous term.
- prologic is analogue stereo with surround sound effects
- HDMI discrete 8 ch PCM is surround sound.

The surround sound settings on AVR HT amps include DSP surround effects from stereo like:
- prologic dinosaur
- dts-neo
- dts-es 5.1 --> 6.1
- DD-EX prologic II
- CS-II mono,stereo --> 6.1 

The best audio connectivity for PC is HDMI or an HT amp with ethernet connectivity

---

### Post by xzero1 on 2012-04-28
> **BicyclerBoy said:**
> You don't understand..
S/PDIF is only stereo PCM, it does not have the bandwidth for multi-channel uncompressed PCM audio.
The maximum is normally 96KHz/24bit (32bit frame). 192KHz in rare cases but not Toslink/optical. So max 12MHz for pro gear.

The a52 plugin & AC3/DTS are methods for sending matrix encoded audio in a digital bit-stream that can be sent over S/PDIF at 48KHz (only) as digital data encoded/compressed.
Both AC3 & DTS are defined with 48KHz bit clock==1.54Mbps.
The actual bitrate for AC3 is 640Kbps (max) & DTS is about 1.5Mbps.

Surround sound is also ambiguous term.
- prologic is analogue stereo with surround sound effects
- HDMI discrete 8 ch PCM is surround sound.

The surround sound settings on AVR HT amps include DSP surround effects from stereo like:
- prologic dinosaur
- dts-neo
- dts-es 5.1 --> 6.1
- DD-EX prologic II
- CS-II mono,stereo --> 6.1 

The best audio connectivity for PC is HDMI or an HT amp with ethernet connectivity

All I am saying is spdif is currently in common use for ac3 including multichannel audio as well as stereo. The encoding (ie computer) determines the format sent over spdif; it is a single digital channel (bitstream). Even stereo is encoded over spdif. If it was decided to build the a52 encoder into Ubuntu, then any number of audio channels up to 6 could be encoded depending on the source. With analog, one normally gets one channel per connection.

---

### Post by BicyclerBoy on 2012-04-28
The common use of S/PDIF does not require a52 plugin..
Once pulse-audio sorts itself out, pass-thru will be possible thru' the system wide audio setup. But it will be exclusive access.

S/PDIF stereo PCM is not encoded, it is lossless PCM digital a bit like serialised WAV file..

The a52 AC3 encoder is non-free.
Is has application for multi-channel audio if you don't have a HDMI AVR & maybe for gaming. So not that useful.
Up-mixing everything to 5.1 must be a personal preference..

Digital pass-thru' is not trivial to get working. The application or plugin must have exclusive access/control. This would make it system wide.
Then a media player would have to decode everything to multi-channel PCM just for the a52 to encode & HT amp to decode.
This method allows system sounds (full sharing of audio output).

The alsa a52 plugin releases iec958 when it is not encoding.
Another way is to point applications at appropriate audio device.

I use digital pass-thru' on a per-application basis.
Stereo & pass thru' for HTPC (default iec958) & upsampled stereo PCM for audio (custom iec958_24_96K).

The a52 encode AQ is questionable, I prefer to use a52/DTS decoder in amp.
I don't want DTS/AC3/DTS-MA etc to be decoded in PC.

The one good thing about the alsa a52 plugin is the ability to dmix (share & control volume).

Volume control can be done over HDMI with CEC or multi-channel LPCM

---

### Post by terran4000 on 2012-04-30
That still doesn't change the fact that in Ubuntu 12.04 you cannot select from the correct list of profiles in the sound card. Thus, it's a bug with no solution thus far.

So either way it's still a question of how do I select "Digital Output 5.1 Surround Sound" like I used to in 11.04/11.10 since that functionality was (see this bug report [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/972554](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/972554)), more or less, taken away?

Even though >pacmd lists all the correct profiles including digital surround sound?

---

### Post by BicyclerBoy on 2012-04-30
So they made the gnome sound more crap (in 12.04) than it already was..

Can you try pavucontrol ?

The main guts of this thread was never about using alsa a52 plugin with pulse-audio, misleading thread title excepted...
If pulse enumerated & worked with the alsa a52 plugin is was good luck..

Does the alsa device surround51 still show up ?
You can redefine the surround51 to output to the a52 plugin:
```

#/etc/asound.conf
# speaker-test -c 6 -r 48000 -D surround51
pcm.!surround51 {
   @args.0 SLAVE
   @args.SLAVE {
               type string
               default "a52"
   }
   type route
   slave {
         pcm $SLAVE
         channels 6
   }
   ttable {
     0.0= 1
     1.1= 1
     2.2= 1
     3.3= 1
     4.4= 1
     5.5= 1
   }
}

```

---

### Post by xzero1 on 2012-04-30
> **BicyclerBoy said:**
> The common use of S/PDIF does not require a52 plugin..
Once pulse-audio sorts itself out, pass-thru will be possible thru' the system wide audio setup. But it will be exclusive access.

S/PDIF stereo PCM is not encoded, it is lossless PCM digital a bit like serialised WAV file..

The a52 AC3 encoder is non-free.
Is has application for multi-channel audio if you don't have a HDMI AVR & maybe for gaming. So not that useful.
Up-mixing everything to 5.1 must be a personal preference..

Digital pass-thru' is not trivial to get working. The application or plugin must have exclusive access/control. This would make it system wide.
Then a media player would have to decode everything to multi-channel PCM just for the a52 to encode & HT amp to decode.
This method allows system sounds (full sharing of audio output).

The alsa a52 plugin releases iec958 when it is not encoding.
Another way is to point applications at appropriate audio device.

I use digital pass-thru' on a per-application basis.
Stereo & pass thru' for HTPC (default iec958) & upsampled stereo PCM for audio (custom iec958_24_96K).

The a52 encode AQ is questionable, I prefer to use a52/DTS decoder in amp.
I don't want DTS/AC3/DTS-MA etc to be decoded in PC.

The one good thing about the alsa a52 plugin is the ability to dmix (share & control volume).

Volume control can be done over HDMI with CEC or multi-channel LPCM

I tried to ignore your misconceptions but I feel I must clarify a few things.

I never said spdif requires the a52 plugin. I said we could encode audio sources via the a52 plugin for surround sound playback (make it a selectable sound sink). There would still be stereo pcm for quality and pass-through available for relavent sources.

Stereo PCM (pulse *code* modulation) *is* encoded. I did not say it was encrypted or compressed. Its called a format. A format is a code. Raw bits [streams] are virtually useless, unless interpreted in some way. The receiver and sender must both know the meaning of the bits.

Digital pass-through implies the data source is sent to the hardware interface untouched. The source is pre-encoded in formats (ac3,dts etc) the receiver can decode. A [pc] media player *cannot* decode digital pass-through. That does not even make sense! Digital pass-through is not a source. A media player can decode the ac3 stream.

The a52 AC3 encoder *is free* (see [http://liba52.sourceforge.net/]("http://liba52.sourceforge.net/")) having been released under GPL although it may be restricted. The a52 plugin encodes audio channels to AC-3, and sends the data by the spdif/toslink interface to the receiver to be decoded.

---

### Post by BicyclerBoy on 2012-04-30
"usage of S/PDIF requires a52 plugin" ..I never said that either.

When all is working (alsa a52 plug, pulse etc) then you can select the a52 plug as an output device along side others..

Is is a selectable audio sink..

Are you suggesting that the a52 plugin is **automatically** available to all audio applications to use as they need it ? i.e PCM or a52 or pass-thru'?
Because that makes good sense..

The a52 does not get a lot of testing because;
- until recently pulse audio did not support pass-thru'
- no one uses it.
- the a52 plug is not shipped with ubuntu, if it were free it would be.
- a52 depends on libavcodec & is broken often.
- pulse is often broken by enumerating a52 plug device.
- vlc mythtv XBMC can use an internal a52 encoder.
- HDMI has made it history/obsolete/deprecated.

I know that in the strictest terms PCM is encoded but in the context of AV codecs it is raw data in a simple frame.
The words matrix encoded multi-channel are in there somewhere. 
The S/PDIF PCM 'encoding' is trivial & done by the audio codec. a52 encoding is avail on some expensive discrete soundcards but here the encoding is still normally performed by software (soundcard driver).

I never said the media player etc would be decoding pass-thru' bitstream..
That's your interpretation..
I know what digital pass-thru' is.

Using a52 plugin for all multi-channel audio would mean that playback results in 2 decoding steps & 1 encoding step; only one is bug free (hopefully).

Sorry if I had misunderstood your comments but I still believe what I have stated is correct in context & in implied meaning.

Use of the a52 encoder is not free & unrestricted.

---

### Post by xzero1 on 2012-05-02
> **BicyclerBoy said:**
> "usage of S/PDIF requires a52 plugin" ..I never said that either.

When all is working (alsa a52 plug, pulse etc) then you can select the a52 plug as an output device along side others..

Is is a selectable audio sink..

Are you suggesting that the a52 plugin is **automatically** available to all audio applications to use as they need it ? i.e PCM or a52 or pass-thru'?
Because that makes good sense..

The a52 does not get a lot of testing because;
- until recently pulse audio did not support pass-thru'
- no one uses it.
- the a52 plug is not shipped with ubuntu, if it were free it would be.
- a52 depends on libavcodec & is broken often.
- pulse is often broken by enumerating a52 plug device.
- vlc mythtv XBMC can use an internal a52 encoder.
- HDMI has made it history/obsolete/deprecated.

I know that in the strictest terms PCM is encoded but in the context of AV codecs it is raw data in a simple frame.
The words matrix encoded multi-channel are in there somewhere. 
The S/PDIF PCM 'encoding' is trivial & done by the audio codec. a52 encoding is avail on some expensive discrete soundcards but here the encoding is still normally performed by software (soundcard driver).

I never said the media player etc would be decoding pass-thru' bitstream..
That's your interpretation..
I know what digital pass-thru' is.

Using a52 plugin for all multi-channel audio would mean that playback results in 2 decoding steps & 1 encoding step; only one is bug free (hopefully).

Sorry if I had misunderstood your comments but I still believe what I have stated is correct in context & in implied meaning.

Use of the a52 encoder is not free & unrestricted.

I won't waste my time time anymore. For those interested [http://ac3filter.net/wiki/AC3Filter_%26_SPDIF#How_sound_cards_handle_SPDIF]("http://ac3filter.net/wiki/AC3Filter_%26_SPDIF#How_sound_cards_handle_SPDIF") is a good explanation on the topic:

---

### Post by BicyclerBoy on 2012-05-02
@ terran4000
pulse in 12.04 supports pass-thru' & the a52 plugin.

Install/run pavucontrol, forget the gnome volume control..

If the a52 alsa plugin is enumerated then the plug will be listed in the [configuration] tab.
 
[configuration]
- (1) Digital Stereo (IEC958) Output
- (2) Digital Surround 5.1 (IEC958/AC3) Output

[Output Devices]
- if (1) then choose pass-thru options AC3 DTS EAC3 MPEG
- if (2) adjust volume mix..

(1) is for stereo PCM & pass-thru' (media player must support)
(2) 6 ch PCM encoded to 5.1AC3/A52.

Note: (1) pass-thru can not be shared/dmixed.

An **alternative** a52 plugin build process for 12.04 64bit:
#get alsa-plugins-1.0.25.tar.gz from alsa-project.org
#extract to folder..

cd alsa/alsa-plugins-1.0.25/
./configure
# check the a52 plug is enabled etc..
make -j4
cd a52/.libs
sudo cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/x86_64-linux-gnu/alsa-lib/

sudo gedit /etc/asound.conf
```

# /etc/asound.conf
# alsa plugin a52
# speaker-test -c 6 -l 1 -D pcm.a52:[CARD]
pcm.a52 {
  @args [CARD]
  @args.CARD {
    type string
  }
  type rate
  slave {
    pcm {
      type a52
      bitrate 640 # 448 is max for most
      channels 6
      card $CARD
    }
  rate 48000
  }
}

```

sudo alsa reload
killall pulseaudio

sudo apt-get install pavucontrol

References:
[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by terran4000 on 2012-05-06
Woot! @BicyclerBoy thanks the reminder n' stuff. Well, whatever update there was recently in 12.04 (there were several updates already) "Digital Surround 5.1 (IEC958/AC3) Output" shows up finally in pavucontrol in the Configuration tab!

Thanks for pointing that one out. Guess I just kept looking at the wrong place, because I did check pavucontrol before and didn't notice it there in 12.04 before.

Either way, thanks BicyclerBoy! Saved my ears!

> **BicyclerBoy said:**
> @ terran4000
pulse in 12.04 supports pass-thru' & the a52 plugin.

Install/run pavucontrol, forget the gnome volume control..

If the a52 alsa plugin is enumerated then the plug will be listed in the [configuration] tab.
 
[configuration]
- (1) Digital Stereo (IEC958) Output
- (2) Digital Surround 5.1 (IEC958/AC3) Output

[Output Devices]
- if (1) then choose pass-thru options AC3 DTS EAC3 MPEG
- if (2) adjust volume mix..

(1) is for stereo PCM & pass-thru' (media player must support)
(2) 6 ch PCM encoded to 5.1AC3/A52.

Note: (1) pass-thru can not be shared/dmixed.

An **alternative** a52 plugin build process for 12.04 64bit:
#get alsa-plugins-1.0.25.tar.gz from alsa-project.org
#extract to folder..

cd alsa/alsa-plugins-1.0.25/
./configure
# check the a52 plug is enabled etc..
make -j4
cd a52/.libs
sudo cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/x86_64-linux-gnu/alsa-lib/

sudo gedit /etc/asound.conf
```

# /etc/asound.conf
# alsa plugin a52
# speaker-test -c 6 -l 1 -D pcm.a52:[CARD]
pcm.a52 {
  @args [CARD]
  @args.CARD {
    type string
  }
  type rate
  slave {
    pcm {
      type a52
      bitrate 640 # 448 is max for most
      channels 6
      card $CARD
    }
  rate 48000
  }
}

```

sudo alsa reload
killall pulseaudio

sudo apt-get install pavucontrol

References:
[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

---

### Post by jc0v on 2012-05-08
Hi

With your help I am able to select the Digital surround sound profile and the sound works correctly for a period but then crashes. I am unsure how to diagnose the problem. Looking online people were suggesting it was my asound.conf but it is the same as in this thread. Any ideas?

THanks

---

### Post by Gremlyn1 on 2012-07-16
Would anyone know why this stops working properly after suspending and resuming the computer? Any ideas on a workaround or fix to stop it from doing so?

I'm running 11.10 and using this to enable me to play surround sound through my receiver.

---

### Post by Pytte on 2012-08-19
the ubuntu 12.04 steps works, if you haven't done any other steps you need to install 2 packages before starting:


sudo apt-get install libasound2-dev libavcodec-dev

---

### Post by wildmanne39 on 2012-08-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

