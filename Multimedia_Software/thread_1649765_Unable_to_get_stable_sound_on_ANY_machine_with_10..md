---
title: "Unable to get stable sound on ANY machine with 10.04 or 10.10 - what next?"
date: 2010-12-20
forum: Multimedia Software
---

### Post by akameswaran on 2010-12-20
Ok, I have several machines, a lot of disk space, and a penchant for VM's.

At this point I'm about to say goodbye to ubuntu(been standardized on ubuntu for the home since 7.x) after 2 weeks of working on a very simple problem.

I want to use amarok on my HDTV as a music player.  Prior to the ps3 update, I was using ubuntu for ppc on my ps3 and managed to do this stable and effectively.

I have tried using ubuntu, kubuntu, xine backend, gstreamer backend, 32 bit install vs. 64 bit install although with 16GB of ram, 32 bit install is a big waste.  The closest thing to stable I've found is running ubuntu as a VM Guest under windows 7.  That way I get a couple of hours of playback without glitches.  
I've tried removing pulseaudio, I've tried purging it.  I've tried re-installing pulseaudio.  I have not gotten anything resembling a working/stable environment on a bare metal install, only as a VM, can I get reasonable audio performance.  Oh BTW - for any other amarok 1.4 fans - it's not worth it anymore, the latest amarok 2.3 brought back a working lyric and replay gain, and I didn't get 1.4 to be stable anywhere.  In fact when I purged the old 1.4 stuff I had been adding back in, some other odd glitches disappeared, and kubuntu became usable.

I honestly don't even know what to ask or what to try anymore.  I'm about to go back to rolling my own audio distro, which I haven't done since planet-ccrma came out on fedora.  But ubuntu has spoiled me, not even sure I could compile a kernel from scratch anymore.  All of my audio is flac 44.1 16bit (ok I have a few 24bit flac LP rips - but I don't expect those to play stable and are not part of my test.)

Anyway instead of whining, I'd like to know if anyone has any suggestions?  I tend not to think it's a driver issue (different hardware) although all my machines are using nvidia based hdmi cards and intel sound cards (different specific hardware, and even chipsets)  Once I get those driver issues resolved and stable, I'm still stuck with an unstable audio stream.  Below I discuss some more of the things I've tried.  If the question is lacking specifics, it's because I've had no luck chasing down drivers, plugins, and sound engines.  I need to go to the top level and re-examine my troubleshooting.


For some background:
I also had no problem with an older t61 lenovo laptop (it didn't do HDMI though) 

So at this point I've tried about 6 different setups on 2 different laptops.  Now both laptops are quad cores with 16 GB ram, decent on board audio, onboard HARDWARE raid and SSD drives.

Keep in mind in all tests I am running nothing other than the desktop manager, services I wasn't 100% sure I could disable, and samba (music is on a NAS - and no the NAS  is not the source of the problem - I can run two (evil os based) players off the nas with 0 skipping.
Only as a VM (go figure) can I get a stable audio stream.

---

### Post by cchhrriiss121212 on 2010-12-20
What exactly is the problem? Glitches meaning skipped sound or something else?
> 
I'd like to know if anyone has any suggestions?
The first thing I would try is to switch to another player. Can't say I've been impressed with Amarok in the past.

---

### Post by akameswaran on 2010-12-20
Good point, I should have spent more time describing the sound issue.  ALthough the exact symptom is a little different on the two different hardware, I suspect there is something similar going on.

It's not your traditional D/A artifacts, or the constant skipping of a truly badly configured stream.  More like every 2 to 5 minutes of playback there is a pause, of anywhere from 200ms to about 1 second.  No I'm not timing it ;) Also it is consistently worse if the monitor gets turned off ( I disabled power saving after wards)  But once the monitor is switched off, I have to reboot.  

In the instance of replacing amarok, I'd be open to it, except I haven't found another player that so nicely integrates lyrics, wikipedia, and replay gain, and handles the funky tags in my flac files (flac does not use ID3 - or at least isn't supposed to)  The other issue, is I am having sound glitches in vlc as well as amarok.

I have no problems trying another player just to figure out if it's amarok (I don't think so) any recommendations?  I really like having on screen lyrics and replaygain - its great for party juke box.

---

### Post by cchhrriiss121212 on 2010-12-20
> I have no problems trying another player just to figure out if it's  amarok (I don't think so) any recommendations?  I really like having on  screen lyrics and replaygain - its great for party juke box.
I use Quod Libet, it handles all my FLAC files OK (tags are fine, and I have a few 24/96 vinyl rips myself) and does everything else you like except for lyrics. I think Guayadeque has all those features though.

If it is not the player then I would say this is HDMI related, I have no experience with that myself but have seen numerous threads on here where it has been an issue. You could easily test that by running the audio through another source.

---

### Post by akameswaran on 2010-12-20
Thanks for the suggestions, I really don't want to go to preubuntu days of compiling everything myself and manually replacing oss with latest svn compiles of alsa.  Ha, does OSS even get used by anything anymore?

Tomorrow I will have to install and try out QuodLibet.  The fact that I'm pretty good with python is a definite incentive to try something new.  For tonight, I'm just going to have a nice evening listening to my flac over a pure digital signal chain.  THat's really why I want HDMI - none of the laptops have a digital out except HDMI, and I'm no longer willing to use my desktop DAW for essentially a party jukebox.  It doesn't help that my new TV has no DVI, which is what my DAW has.

I am almost certain it is HDMI related or soundcard to HDMI related, but it is something in either linux or ubuntu, as I can get a stable sound when I let windows manage the audio drivers (via running ubuntu as a vm).  I'd just really rather not run the windows period, and projectM just looks like garbage on a VM - no 3d acceleration, no matter what VMware claims about enabling 3d through tools.

Still, if I can narrow down the issue to amarok (vlc still shows the same behavior so I'm not hopeful) but if it's just amarok, I can move on from what used to be my favorite media player ever.  I will reply once I've tried the other player.  Thank you for not suggesting rythmbox.  I hated that thing, although I haven't tried it in years.

---

### Post by BicyclerBoy on 2010-12-21
You need to clarify your problems a bit more

I have been using amarok1.4 from *buntu8.04 no problems at all.
The only limitation it has for me is it will not play multi-channel ogg files.
I'm using a 3rd party ppa for amarok1.4.

I have 4 *buntu machines:
1 64 bit 10.04   s/pdif pass thru to ht amp
2 64 bit 10.04  analogue out
1 32 bit netbook analogue out

All have pulseaudio & alsa ..all absolutely perfect audio.
One box is even running jack & rosegarden (not RT kernel) 
One box runs mythTV so handles DTS, AC3, LATM_AAC, mp2,mp3 PCM 
The hdmi audio works as well (alsa 1.0.23).

The latest mythtv 0.24+ fixes now supports audio EAC3 & DTS-MA over hdmi...

So your problems are related to your kernel or OS configuration

Another thing: Wine can & does work extremely well. You need to do some tweaking/fiddling for some apps but one the whole it is very impressive considering..

---

### Post by akameswaran on 2010-12-21
OK, fair enough.  I wasn't clear, because I've literally tried this on 3 systems, and close to 8 or 9 if you add in VM attempts and 32 vs 64 bit tests.

Let me focus on one environment - What is frustrating is that I've had a similar setup for years on far less powerful machines with no issue. 

SO - here is my latest attempt, and I will attempt to include anything that could be relevant.

Dell m6500, clean and fresh install of standard ubuntu 10.10 x64.  Nvidia Quadro FX 2800M Video Chipset (HDMI)with the ubuntu proprietary driver version 260.19.06
Sound card according to aplay:
HDA Intel STAC92xx Digital
In sound properties, I can use either the analog duplex or digital duplex and still get sound over HDMI
In total Sound Preferences lists 5 hardware devices
Analog Stereo Input
Digital Stereo Duplex
Digital Stereo output + analog stereo input
Analog Stereo Output
Analog Stereo Duplex

lsmod shows:
snd_hda_codec_idt
snd_hda_intel
snd_hda_codec
snd_hwdep
and the rest of the expected mods for seq, midi, pcm, etc.
Interestingly enough I see no snd_codec_hdmi or something similar, which I'm not sure is a concern or not.


I have been using analog stereo Duplex, although I probably should just go digital, since I've been muting my analog speakers.

Now, I chose the default installation, then added medibuntu repositories before grabbing Amarok 2.3 (It was hard to move on from 1.4, but the latest on 10.10 is good enough to make me move to current)

I have both gstreamer and xine phonon backends installed.  Both show the same behavior.  I guess I could try adding the mplayer backend, but I'm trying not to cloud up my repos at the moment.  I'm trying to reduce complexity ;)

On this machine, I have not updated to latest alsa outside of ubuntu repos (I did that for a different box) so in this instance I have not done a lot of customization etc.

I am playing almost exclusively self made flac from a DNS-323 nas.  I am not streaming, the nas is mounted using cifs.  I have seen no indication that nas performance is not up to snuff. 
The HDMI is playing through an onkyo tx-sr707, which is what nVidia detects as the display.  And it's a samsung series 7 tv, although I doubt this matters at all.

Now the only thing in the chain I can think of I haven't played with at all is pulseadio.  I must admit I've never really understood why pulseaudio is used, and up until now, I haven't really cared, since with earlier versions of ubuntu on my other machines, I've not had this much trouble.  Or really any. I'm suddenly bothered by not understanding this point in my signal chain. 

So for next steps I'm not entirely sure
1) kernel - all needed modules seem to be loaded.  Is there somemthing in dmesg, or syslog that I should look for.  Casual grep/perusal did not reveal anything - that's not to say it isn't there, but if it is I don't know what I'm looking for
2) OS - as opposed to my other attempts I haven't really done anything except add medibuntu and my desired software, and this is a completely clean install.
3) Pulseaudio - being spoiled by ubuntu for years I'm not even sure what to look for in pulseaudio - or how to determine if it's the "problem" component.  On other systems that I'm having similar skip/pause errors removing pulse, removing pulse and switching to kubuntu, or even reinstalling pulse seemed to have no effect.

Now for side notes.
My wife's System76 laptop has had it's own sound issues ever since jaunty, but are not like this, she's hasn't been able to get sound working since her 10.04 upgrade.  I haven't tried to help her on that yet, I suspect it's a conf/upgrade issue. Also she usually is able to fix things on her own using the system76 forums.
And wine - I already have a working environment dependent on windows, ie the VM.  Personally I don't want to admit I need windows in this scenario.  Call it pride.

---

### Post by akameswaran on 2010-12-21
I switched my output to use digital only, and thought I had fixed it.  Had about 30 minutes of glitch free playback, but it started again, and I still get a skip or a pause approximately every 5 minutes, but it varies widely.

I'm wondering if adding ubuntu-studio might be a good or bad thing.  It certainly would change my kernel.

Thoughts?

---

### Post by cchhrriiss121212 on 2010-12-21
> I'm wondering if adding ubuntu-studio might be a good or bad thing.  It certainly would change my kernel.
Won't make any difference, the current studio release actually uses the generic kernel. If I were you I would only consider these 2 options just because I always prefer the easiest options:
Use Windows
Use analogue output

This seems like a shortcoming of Ubuntu/Amarok/ALSA/HDMI to me so I don't think tweaking things will get you any results. But if you still want to test this, try something simple like shown here:
[http://www.linuxquestions.org/questions/ubuntu-63/hdmi-audio-not-working-786707/#post3859565](http://www.linuxquestions.org/questions/ubuntu-63/hdmi-audio-not-working-786707/#post3859565)

You also could try a custom asoundrc to set the device as default:
[http://alsa.opensrc.org/index.php/DigitalOut#Set_digital_out_as_default](http://alsa.opensrc.org/index.php/DigitalOut#Set_digital_out_as_default)

---

### Post by akameswaran on 2010-12-21
Progress is being made.

I ripped out pulseaudio and went direct to digital device.  Played with no glitches, nothing, sounded great.  One problem, amarok UI stays greyed out for about 59 seconds of every minute.

I was doing that as a last resort before compiling my own RT kernel (i had found out what you said about ubuntu studio about 5 minutes after my post)

So now, I know kubuntu 10.10 uses pulse, but perhaps I can replace pulse in kubuntu.  Going direct to device had no bugs in the audio... feels so close.

---

### Post by akameswaran on 2010-12-22
For reasons that aren't entirely clear, I have managed to get a stable audio stream.  well 90% of the way there.  There are still occasional pauses when new apps launch etc, but I do have clean glitch free sound when playing amarok.  I should also mention that my input devices have disappeared, but that is not a problem for me on this system.  Others might find that an unacceptable situation.

So what I have done is this.
Installed the ubuntu studio packages, all of them, except linux-rt since it doesn't exist.  I did not compile an RT kernel, or perform any manual configurations.  Jack does NOT work.

I installed kubuntu and switched to KDM.
PulseAudio now only shows 1 digital output device in the volume control.  Phonon, does not show it as pulse audio in the ui, but pulse is running and outputing the stream.

I also enabled real time scheduling instead of timer based in /etc/pulse/daemon.conf and /etc/pulse/default.pa

I'm honestly not sure if ubuntu studio did anything or not, but i'm not touching it ;)

in any case, it appears that switching to rt scheduling (which did not clear up the issue in gnome) and using kde has made output work.

For me this is solved, for other users, this may be worse than what I had before.  Considering the glitches I had on playback, i don't have any confidence that the inputs were working either, but now they definitely aren't.

---

### Post by BicyclerBoy on 2010-12-28
Noticed that your audio is 44.1KHz 16 bit flac, do you mean you made flac files from CD ? Were you trying to avoid up-sampling or is the flac sample rate 44.1KHz ? 
Are you up-sampling ?
What happens with AC3 or DTS at 48KHz as digital pass thru' s/pdif ?
And as analogue pcm output 48KHz or 96KHz?
 
Pulseaudio came about AFAIK to allow sharing of the sound card i.e. digital & analogue mixing from multiple apps/sources just like windoze.

There are many people using alsa/pulse with *buntu running mythtv/mplayer/XBMC successfully. Granted that many will be using alsa device directly (no sharing).

---

