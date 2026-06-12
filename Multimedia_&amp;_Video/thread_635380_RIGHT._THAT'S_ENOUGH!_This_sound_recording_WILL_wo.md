---
title: "RIGHT. THAT'S ENOUGH! This sound recording WILL work, or so help me...!"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by stoodleysnow on 2007-12-08
No more Mr Nice Guy.:mad: I have been trawling up and down umpteen forum posts, websites and other things for 6 months now, trying to get Audacity to record anything from the Line Input of the following sound card (details from Dohickey):
> 82801H (ICH8 Family) HD Audio Controller Intel Corporation
Manufacturer:Intel Corporation
System InformationID:/pci0000:00/0000:00:1bType ID:chipset:8086:284B
and from Hardware Info: see soundcard.png (attached)
I've tried altering every volume control Ubuntu has, including ALSAMIXER, ALSAMIXERGUI and Jack, with ESD on and off, with channels muted or not. I have my hifi connected from its headphone socket to the Line In on my Asus P5B's built it Intel ICH8 HD Audio. Playback works fine. Playback of the tape through the sound card to the PC's speakers works fine. 
But for who knows what reason, amongst all the paraphernalia I have yet waded through in my attempts to get this working, I have yet to find a satisfactory solution that will get Audacity, Sound Recorder or any other program to actually put the sound into a playable waveform. (see audacity-no-rec.png (attached)).
ALL I  WANT TO DO IS RECORD FROM A TAPE TO A CD!:mad: 
I really must press for a solution now, as Christmas fast approaches and I need this to work!
THERE CAN BE NO MORE SILENCE FROM MY LINE-IN! I'm ready to go totally even madder! (since I'm already mad, it makes little difference, but you know what I mean)

In short: AAAAAAAARRRRRRRGGGGHHHH!!!!!!!!!!!

So, any ideas?:)

---

### Post by ron999 on 2007-12-08
Hi
Try using **arecord** instead.
See my post here:-[http://ubuntuforums.org/showthread.php?t=622067]("http://ubuntuforums.org/showthread.php?t=622067")
8):guitar:8)

---

### Post by stoodleysnow on 2007-12-08
```
daniel@heart-of-gold:~$ arecord -f cd out.wav
ALSA lib confmisc.c:769:(parse_card) cannot find card '&#65533;        d'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
arecord: main:545: audio open error: No such device
daniel@heart-of-gold:~$ 

```
is arecord's reply.:(

---

### Post by ron999 on 2007-12-08
Hi
I've no ideas about that error. I'm not much use in this department. Maybe someone else will help.

If you sort it out then arecord should be just what you need.
When it's set up it works a treat. It's the mutts nuts, records whatever is coming through the sound channel. CD, internet radio, DVD whatever. So if you're playing your tape deck it should record that. Less hassle than audacity.

All you have to do is enter 
**arecord -f cd out.wav**
and it will create a file named out.wav in your home folder.
If you type
**arecord -f cd -t raw | lame -x - out.mp3**
it will create a file named out.mp3 instead.

Hang on in there.
8-)

---

### Post by stoodleysnow on 2007-12-08
Thanks. It may be less hassle than Audacity for you, but I prefer a GUI where I can see what's going on and edit the files before saving.
But I digress.:popcorn:

---

### Post by daXkat on 2007-12-08
I understand your frustration, I've been trying to get Audacity to work properly since last August. I had a similar problem and downloading a dozen packages was not the best idea, I'd suggest to uninstall them, especially ESD, and start from scratch if possible.

First download alsa-oss and run audacity this way: aoss audacity. Make sure you don't have *any* audio apps running, get rid of residents apps and restart the sound system if necessary. My settings: Playback OSS /dev/dsp and Recording: ALSA: HDA ATI SB: ALC861 Analog (hw:0,0), Channels: 1. No playthrough or anything out of the ordinary. Other settings doesn't seem to work, and no one seems to have a good explanation why, you have to try all the different combinations.

After that, my problems continued. I thought this was the end of it but shortly after that I came across another issue, I can only record for a limited amount of time. I tried increasing the swap partition and then installed swapspace but nothing works. It records either 20 minutes or 20 seconds, you never know. After that, nothing at all, it keeps overwriting the previous data. The strange issue is I have a 500mb swap partition and a 10GB partition for the temporary audio files, none of them is used properly, only 100k of the cache is being used, which is ridiculous. I have 1GB of ram and a 2.8 dual core, this was enough for recording 2-3 hours without any inconvenience, it's very frustrating to boot to xp back and forth, not the booting itself, the fact that I can't get rid of windows.

Other apps show the same problem, I tried CDeX via Wine for instance, so any software suggestion won't help me either. The rest is almost as you describe it, I can listen, play synth keyboards etc, but recording is always a mess. So, rather than starting a new thread I'm posting this as a follow-up, I'm sure there must be someone out there able to help us. I made my winmodem work thanks to a guide posted here, that was waaay more complicated, so I'm pretty sure someone here knows how to fix this.

-daX (using Kubuntu 7.04)

---

### Post by coskierken on 2007-12-08
I had loads of hair pulling to figure out why the mic would not capture anything when I loaded Gutsy 64 bit.  I could hear it, but no recording in the sound recorder.  I finally loaded Gnome-alsamixer and it activate the software capture for the mic.  This might help, it might not.  Just a thought :lolflag:

---

### Post by Whiffle on 2007-12-08
So if you open up alsamixer, hit tab, and then look at which channel has the words "capture" under it, which one is it?  It should be on whatever you're trying to record...

---

### Post by stoodleysnow on 2007-12-10
Tried that. see audacity-no-rec.png; it's the same with the settings you just suggested. Tried installing Gnome-alsamixer, nothing changed.:confused:

---

### Post by DoctorMO on 2007-12-12
the best thing to do in these times is instead of messing up your installed version, boot up the live cd (insstall disk) and mess about with that instead.

You can install packages, change settings and learn what the problem is and how to fix it; and if you need to reset the computer and start with a new clean slate.

I've always found alsa to be a real pig when recording stuff. the hope is that pulse-audio will solve a lot of these problems; but you know what they say about pipe dreams: I'll believe it when I see it.

P.S. I'm glad Dohickey was helpful (in a way)

---

### Post by bayvista on 2007-12-12
Interesting thread. I also cannot record from 'Line in' after trying all of the above. Is it just a Linux bug?

I boot up Windows, start Audacity and it just works without any fiddling. Come on you Linux Gurus, I can't throw Windows out of the door until I can record.

Dave

---

### Post by stoodleysnow on 2007-12-12
> **DoctorMO said:**
> 

P.S. I'm glad Dohickey was helpful (in a way)

Yeah, I love Dohickey. It just needs to be brought up to a level at which it can be safely included in Ubuntu. Can I help with hardware verification?:idea:

This may be a way of solving problems such as this one (sound)!

---

### Post by daXkat on 2007-12-12
As I mentioned, I'm using Kubuntu. I haven't used Ubuntu for a while but I think Gnome has ESD as default, (correct me if I'm wrong). Also, Audacity uses OSS as default like most of the older sound applications but I don't think it can handle ALSA or ESD out of the box. I know for a fact that it can be used with ALSA but I don't know about ESD. I use ESD libraries to play sounds with Enlightenment but is not the same thing. To be able to use ALSA with Audacity you have to download the alsa-oss package, this is a must, otherwise it doesn't work. I don't know exactly what sound libraries are installed by KDE and not by Gnome but I've noticed a couple of ESD/ALSA and ESD/OSS libraries, perhaps they might help you in your case.

My system settings,

Sound System -> Enable the sound system
Run with the highest possible priority (realtime priority)
Auto suspend if idle after 60 seconds
Hardware. Audio device -> ALSA. Full duplex and the rest all off.
Audacity settings as described previously.

I'm also using both ALSA and OSS at the same time, otherwise my Line-in does not get listed as a Recording device, from the Kmix handbook:

/*
 Tips and Tricks
Using ALSA and OSS driver at the same time

KMix on Linux can use either the ALSA driver or the OSS driver, not both. If you really need to use both drivers at the same time (a very rare situation), you can do it as follows: Quit KMix and add the following line to your kmixrc file in the global configuration section: MultiDriver=true. Start KMix again. If you click Help->Hardware Information you should see "Sound drivers used: ALSA0.9 + OSS" and "Experimental multiple-Driver mode activated". Warning: You will probably see all of your mixers doubled. There is no support for this kind of configuration.
 */

and from the mentioned alsa-oss package:

/*
  This package contains a program loader, aoss, which wraps applications written for OSS in a compatibility library, thus allowing them to work with ALSA.

  There are two ways of getting an application to work with ALSA if the application was written for OSS. The first way is to load the special ALSA drivers that emulate the OSS kernel interface; these allow the application to open /dev/dsp0 and other OSS device files. The second way is to wrap the application in the libaoss library provided in this package; the wrapper causes the application to access native ALSA device files such as /dev/snd/pcmC0D0c instead of OSS device files.
  .
  Use of the alsa-oss library is recommended over the use of OSS-emulation drivers if you want to use ALSA's PCM plugin layer.
*/


So, in my case I run a OSS application with the following audio flow:

ALSA (System) - > ALSA-OSS (Library) -> OSS (Audacity)

In yours, it might be

ESD (System) - > [Intermediate library, probably ESD-ALSA] -> ALSA-OSS (Library) -> OSS (Audacity) or
ESD (System) - > [Intermediate library, probably ESD-OSS] -> OSS (Audacity)

assumming that alsa-oss and those libraries behave similar and you are not missing any other essential libraries. I don't think is a hardware specific problem by the way. I've attached a pic of Audacity working with the settings I posted. As you can I see I got RAM, space and swap, nevertheless it stopped shortly after I took the snapshot. After recording for 12 minutes my .audacity_temp directory contains 154 temporary .au files, 1MB each, those ~150MB were also loaded onto memory. That shouldn't happen, this is only mandatory while exporting, not before, that's a major inconvenience. I can't believe no one came across this problem before, I don't think I'm doing anything out of the ordinary, I mean, I'm not recording video and like I said my system resources are reasonable. I searched everywhere, I asked everyone, "add more RAM" is not an answer, I've been doing this with XP and only half of my current resources, it can't get any weirder than that. I still can't believe that a mediocre bloated OS beats Linux on this one, and it does it by far to say the least, that is really annoying. So any suggestion will be appreciated. I don't mind reading dozens of manuals if that's what it takes. There are no guides on this issue so if I make any progress I will post it here, I think I'm not alone on this one. 

- daX

---

### Post by daXkat on 2008-01-09
So, any luck guys? No success on my side but I'm not giving up. Any tips anyone?

---

### Post by stoodleysnow on 2008-03-07
Not yet. Will either wait for an ALSA update including a bugfix or try a different (new, need money, will have to wait) sound card.

---

### Post by bullfrog2 on 2008-03-07
this works for me change line in to Mix hope this works i didnt add any thing to it on fresh installs .  bullfrog

---

