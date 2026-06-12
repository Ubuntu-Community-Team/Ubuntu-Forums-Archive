---
title: "Problems with 5.1 Surround"
date: 2006-01-05
forum: Multimedia &amp; Video
---

### Post by Antithesis on 2006-01-05
I recently got 5.1 Surround speakers, and I've been having problems setting them up to work properly, tried to read up on it, can't seem to make eveything work (namely, center speaker, but more later)

Using the onboard sound from my Asus A8V-E motherboard. System is Logitech X-530, using 3 mini jacks.

The speakers are connected properly as far as I can tell, and work properly under windows xp.

I've played with alsamixer a bunch - nothing is muted, everything is on high volume. I've also made sure 4 channels are on.

If I turn on the "duplicate front" option, I can get sound from the back speakers. Their volume is only controlled by the "surround volume" (and PCM ofcourse), but nothing else.

I can also get some sound from my sub - it doesnt seem very strong, but I can feel it a bit - Sub volume is not affected by muting Surround, LFE or center - to be frank, I'm not sure where it is coming from...

In speaker-test, I only hear noise from front left and right. center, sub and back speakers do not produce any noise. This is still true even if I have music playing from my back speakers.

I've tried to download the driver from asus site, but I'm having a different problem there with installing the patch (If this were to solve the problem, I could elaborate and try to figure it out)

Any help / advice would be appreciated - Thanks! :)

---

### Post by !nkubus on 2006-01-05
I had similar trouble with an onboard card and in alsamixer i've put the surround option to  independant instead of shared and restarted alse then ran :

speaker-test surround51 -c6

in a konsole and it worked fine

note the a mp3 or a cd will not be 5.1 so I had to put the "emulate" button on tu have 5.1 with a mp3.

The best test is a DVD if you hear voice it's because everything is ok.

Hope it helps

---

### Post by Antithesis on 2006-01-05
Thanks for the quick reply.

I gave it a try, didn't help with the problem - speaker test still silent on 4/6 speakers.

I did notice that in idependent, the sub (and overall) volume is lower than in shared

---

### Post by Antithesis on 2006-01-10
Can anyone offer any advice? I'm still in the same situation as before, and I would appreciate the help.

Thanks

---

### Post by Antithesis on 2006-01-18
Any help?

This is quite frustrating....

Thanks

---

### Post by Antithesis on 2006-02-28
*cough* up...

anyone, help with this? I would appreciate it.

Thanks.

---

### Post by VestniK on 2006-03-03
I have exectly the same problem and hope somebody will help.
My system: motheboard Gigabyte GA-7VT600L on board sound Realtek ALC655 Ubuntu 5.10, KDE 3.5

I think that when subwofer works it works not because of signal from sound card in corresponding chanel, but because there is a filter in amplifier of speaker system which redirect low frequensies from front chanels to subwoofer. That's why speaker-test surround51 -c6 don't produce sound on sub, there is no low frequensies in output sound.

---

### Post by Antithesis on 2006-03-07
Help? Anyone?

---

### Post by rigsnet on 2006-03-18
I have the same problem. I can get the rear speakers to play the same as the front with im listening to music and stuff, and the sub puts out sound... but during the sound test, the rears and sub do not make a noise.

---

### Post by brainwrinkle on 2006-03-22
I have the same exact problem- same speakers, different motherboard. I'm using the integrated sound on my MSI Neo 4-F.  At least this thread helped me get sound out of the rear speakers :neutral: .  It seems like the problem lies in the speakers because they seem to be the only common component.

---

### Post by sha_man on 2006-04-13
no surround 5.1 working here neither:(

---

### Post by brainwrinkle on 2006-04-13
I think I've found some settings that work fairly well for the X-530's.  Go into your Volume control, enable all of the settings to be visible in Edit-Preferences, and use these settings:

Turn the knob on the subwoofer all the way up.

In Playback:

Master Volume - ~80% 
PCM - wherever you want it
All of the other settings in the playback tab - 100%

Don't worry about the capture tab.

In Switches-
Check Duplicate front and leave the others unchecked.

In Options- 
Independent Jack
Mic 1
for IEC958: PCM
6ch mode

This isn't a fix, but these settings work fairly well for me.  The master volume seems to control whether the sound comes from the front or back speakers and less master volume gives you more bass.

---

### Post by texasdude on 2006-04-15
i have a 7.1 surround sound system on an Asus p4p800-e.  I have not been able to get the surround sound to work, however, the duplicate front works well.  It gives a simulated surround, but  not true channel support.  My front center channel doesnt work, but the sub and the others work fine.  I am still looking for a good  surround sound solution for the Intel i875P (Intel ICH5R) chipset with the onboard 7.1 channel sound.  If anyone has any ideas please let me know.  Thnx

---

### Post by Selmi on 2006-04-19
5.1 onboard on gigabyte mainboard

3d sound is working in mandrake 10.1 and in windows 98
in ubuntu i hear only front left and front right speaker, others are silent

when i set surround jack mode to shared then there is sound from all directions but wrong - left rear instead of center etc.

i played with settings for hour but i can't make it work :-(

---

### Post by ZeroNeo on 2006-04-21
[QUOTE=Selmi]when i set surround jack mode to shared then there is sound from all directions but wrong - left rear instead of center etc.[/QUOTE]
Same problem here, but not when enabling the surround jack option (this option doesnt seem to do anything for me), this happens with just the normal surround enabled.

Another thing is that when using the speaker-test in a terminal all speakers seem to work (in different order than they should), but when playing a DVD in 5.1 only the from speakers send out the sound, the other speakers dont emit anything at all. ](*,)

---

### Post by .t. on 2006-04-23
I'm running the latest Dapper on my Inspiron 6000 and I'm using an Audigy 2 ZS Notebook card with Creative GigaWorks 7.1 Surround speakers. I'm listing, now, to Franz Ferdinand in stereo MP3 which is being upmixed to 8 channel surround. It's working flawlessly except I sometimes have these ALSA errors:

```

ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.subdevice'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory

```

However, I suggest for y'all that can't get surround to work to have a look at /var/lib/alsa/asound.state (remember you gotta be root to modify).

Google for "asound.state" and choose a result that matches your configuration. I can't post mine here as it's too long for vBulletin to handle.

---

### Post by Prot on 2006-05-07
[http://ubuntuforums.org/showthread.php?t=167986&highlight=5.1+surround](http://ubuntuforums.org/showthread.php?t=167986&highlight=5.1+surround)

remember to use plug:ch51dup when configuring other applications. i.e. amarok.

---

### Post by Selmi on 2006-05-21
problem is that what you write is duplication of channels, this won't solve playing of real  5+1 audio like one on dvds

---

### Post by pt123 on 2006-07-07
> **brainwrinkle said:**
> I
In Playback:

Master Volume - ~80% 
PCM - wherever you want it
All of the other settings in the playback tab - 100%

Don't worry about the capture tab.

In Switches-
Check Duplicate front and leave the others unchecked.

In Options- 
Independent Jack
Mic 1
for IEC958: PCM
6ch mode


Thanks this works for me when playing MP3s.
Remember to - Change Device : chose the Intel CHs (Alsa Mixer) than the Realtek ALC 580 (Oss Mixer), for people with the Gigabyte onboard sound.

---

### Post by lpf on 2006-07-08
> **pt123 said:**
> Thanks this works for me when playing MP3s.
Hello, is it possible to get screenshots of your settings ?
I have x530 & DFI nforce3 250g and I messed everything in alsamixer or Kmix trying to get 5.1 working](*,) ...
as an image may be worth etc...
thanks.

---

### Post by conanm4 on 2006-08-04
This is why linux is going to take a lot of work to even be able to fully use it.

---

### Post by joflow on 2006-12-29
Is there a solution to this problem yet.

Edgy
Logitech x-530s
Audigy 2

I get the upmixed audio in all five speakers while playing mp3s and DVDs.  But no real surround sound.  When I change the setting in VLC to 5.1...I get no audio at all.  During the soundtest in terminal only yields sound from 2 speakers.  Sounds like problems that are very similar to the ones posted in here.  Anyone got a fix?

---

### Post by robenroute on 2007-01-02
When you say Audigy 2, what model is it, exactly. According to the Alsa web pages ([here]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix")), support for Audigy cards varies.... I guess, sticking with older hardware is best: SB Live series seems well-supported.

On a side note: Creative is very unsupportive in the sense that they are not willing to release techical specs to the Alsa developers. Way to go Creative!

---

### Post by robenroute on 2007-01-02
> **robenroute said:**
> 
On a side note: Creative is very unsupportive in the sense that they are not willing to release techical specs to the Alsa developers. Way to go Creative!

I've just been doing a bit more research into Linux support for soundcards and stumbled on the following info (quoted from the OpenSource [page]("http://opensource.creative.com/soundcard.html") from Creative):

***"The X-Fi series of products are not supported under Linux. Closed-source drivers will be available for the X-Fi series of sound cards in the second quarter of 2007. These drivers will have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects)."***

That sounds very promising; I guess we'll have to wait and see. I'll be sticking with the on-board sound for now and then check back with Creative in a month or 4....

---

### Post by MemoryDump on 2007-01-02
this is 1 of my main reasons for not switching to Linux full time :(
I've NEVER been able to get real 4 speaker sound support like I do in WinXP.
(I have a Audigy2 card as well)

here's to hoping some day it'll work :(

---

### Post by Florin Coras on 2008-04-30
I do realize this is a bit late (at best) but maybe it will help others in their endeavours. It is not a complete solution but it does provide surround sound. Not complete because I still have problems with the volume as it is quite low in comparison with Windows and unfortunately some sound quality issues. 

I am currently using Ubuntu 8.04 and i've been using this solution since 7.10. I found it on the ALSA web page and it is meant to do upmixing to 5.1 from stereo and also 5.1 dmixing. Hope it works!

This goes into .asoundrc

```

pcm.snd_card {
     type hw
     card 0 # change to your cards number or name
}

# 6 channel dmix:
pcm.dmix6 {
     type dmix
        ipc_key 1024
        ipc_key_add_uid false # let multiple users share
        ipc_perm 0660 # IPC permissions (octal, default 0600)
        slave {
                pcm snd_card # see below
                rate 48000
                channels 6
                period_time 0
                period_size 1024 # try 2048 against skipping
                buffer_time 0
                buffer_size 5120 # in case of problems reduce this
                                 # in case of skipping, try increasing
        }
     }

# upmixing: 
pcm.ch51dup {
        type route
        slave.pcm dmix6
        slave.channels 6
        ttable.0.0 1
        ttable.1.1 1
        ttable.0.2 1
        ttable.1.3 1
        ttable.0.4 0.5
        ttable.1.4 0.5
        ttable.0.5 0.5
        ttable.1.5 0.5
   }

pcm.duplex {
     type asym
     playback.pcm "ch51dup" # upmix first
#     playback.pcm "dmix6"  # just pass to 6 channel dmix
#     capture.pcm "dsnoop:0" # doesn't work for me
     capture.pcm "snd_card"
}

# change default device:
pcm.!default {
     type plug
     slave.pcm "duplex"
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

```

For further details do check: [http://alsa.opensrc.org/index.php/Dmix]("http://alsa.opensrc.org/index.php/Dmix")
And also, if someone does find a better solution please do share.

---

