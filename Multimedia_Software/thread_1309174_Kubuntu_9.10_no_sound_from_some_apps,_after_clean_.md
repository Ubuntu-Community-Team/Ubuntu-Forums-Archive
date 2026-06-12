---
title: "Kubuntu 9.10 no sound from some apps, after clean installation"
date: 2009-11-01
forum: Multimedia Software
---

### Post by xcoder_123 on 2009-11-01
Hello.

I just installed kubuntu 9.10, I didn't upgrade I reinstalled, but now only kde start up sound works, and when vlc or firefox isn't running I can launch amarok, and then in amarok I can hear sounds. But in VLC and Firefox I don t hear anything.

But still in VLC and MPLAYER I can hear scrathcy sounds

My audio chip is ALC888

---

### Post by xcoder_123 on 2009-11-01
Correction: Only one app has sound, but I installed alsa-oss

If I launch skype first, skype only has sound.
If I launch amarok, then amarok has sound

aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



lsmod|grep '^snd' | column -t
> snd_seq_dummy          2656    0
snd_seq_oss            28576   0
snd_seq_midi           6432    0
snd_rawmidi            22208   1   snd_seq_midi
snd_seq_midi_event     6940    2   snd_seq_oss,snd_seq_midi
snd_seq                50224   6   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         6920    5   snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            37920   0
snd_mixer_oss          16028   1   snd_pcm_oss
snd_hda_intel          26920   5
snd_hda_codec_realtek  203328  1
snd_hda_codec          75708   2   snd_hda_intel,snd_hda_codec_realtek
snd_hwdep              7200    1   snd_hda_codec
snd_pcm                75296   4   snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_timer              22276   3   snd_seq,snd_pcm
snd                    59204   20  snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
snd_page_alloc         9156    2   snd_hda_intel,snd_pcm


And here is a picture what amarok shows, when I launched skype before amarok. Skype ,ofcourse, has sound.

[IMG]http://raivucis.lv/amarok.jpg[/IMG]

I don't know what more information can I provide to fix my problem.

---

### Post by TakeoKatsu on 2009-11-01
I have the exact problem. I upgraded Ubuntu Gnome to 9.10 last night. I get some perfect sound at first, then it cuts out and I hear scratchy sounds for every noise. I dont know how to fix it.

---

### Post by TakeoKatsu on 2009-11-01
Have you tried reinstalling you device?

Does the computer detect the device at all? Or is it saying it just doesnt work?

---

### Post by xcoder_123 on 2009-11-01
I have tried to reinstall alsa, If that counts.
I can listen to music, if I run amarok first :D, but that's it, in skype I don't hear anything or in youtube I hear nothing etc.

---

### Post by TakeoKatsu on 2009-11-01
Hmmm...Does the sound just instantly cut off when you go to play some other media?

---

### Post by xcoder_123 on 2009-11-01
It doesn't even start to play in firefox or skype, but in VLC and Mplayer I have scratchy sound If I'm running amarok.

---

### Post by TakeoKatsu on 2009-11-01
I have the exact same problem. Im trying to fix it as well.

Have you gone to System>Admin>System Testing?

---

### Post by xcoder_123 on 2009-11-01
I now went to System setting multimedia, and you know what I was listening to music with amarok, and I pressed test button, and I heard test sound + amarok's played music. So the problem is with other apps - skype, firefox, vlc, mplayer etc. Desktop and amarok can produce sound together :|

---

### Post by KIAaze on 2009-11-01
Same problem for me.
KDE apps have sound, but not vlc or firefox. :(

Actually, after the upgrade (from Kubuntu 9.04 to Kubuntu 9.10), I had no sound at all.
But this helped me get sound back into KDE apps: [http://ohioloco.ubuntuforums.org/showthread.php?t=1306142](http://ohioloco.ubuntuforums.org/showthread.php?t=1306142)

```
killall pulseaudio
sudo alsa force-reload

```

I also added myself to the audio group and on reboot, I had sound in KDE.

lspci:
```
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
        Subsystem: Giga-byte Technology Device [1458:a002]                            
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 32, Cache Line Size: 4 bytes                                                                
        Interrupt: pin ? routed to IRQ 16                                                                    
        Region 0: Memory at fe024000 (64-bit, non-prefetchable) [size=16K]                                   
        Capabilities: [50] Power Management version 2                                                        
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)                  
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-                                                  
        Kernel driver in use: HDA Intel                                                                      
        Kernel modules: snd-hda-intel      

```

---

### Post by xcoder_123 on 2009-11-01
You know, what's the funniest thing just installed ubuntu-desktop, and in gnome, everything works, the problems are only when i'm using kde 4.3 :| ! So it's a bug, no problem with sound devices when using gnome!

---

### Post by xcoder_123 on 2009-11-02
I'm annoyed about not getting sound from vlc or firefox, that's why now I'm using ubuntu :D No problems at all.

Just do aptitude install ubuntu-desktop from terminal (konsole)! Then choose gnome windows manager from login screen :)

Funniest thing is that I have been using kde for 4 years and now kde makes me to use gnome :D

---

### Post by KIAaze on 2009-11-02
> **xcoder_123 said:**
> 
Funniest thing is that I have been using kde for 4 years and now kde makes me to use gnome :D

Correction: Kubuntu makes you use gnome.
I saw installations of openSUSE and Debian with KDE(3) which worked very well and overall I'm impressed by KDE. I won't give up on it so fast now. :)

My biggest problem is that I have absolutely no idea about how audio works under GNU/Linux. This makes it pretty hard to figure out what's wrong. :(

---

### Post by KIAaze on 2009-11-02
For those still having no sound in vlc, firefox & co, this worked for me:
> Open terminal, and start alsamixer. Then, first check that no output is muted (MM on the bottom of the bar), and then turn up the volume for each output channel. Even though the mixer showed no muted channels doing that restored audio on my netbook.
[http://ubuntuforums.org/showpost.php?p=8190010&postcount=10](http://ubuntuforums.org/showpost.php?p=8190010&postcount=10)

---

### Post by meet.aman7 on 2009-11-03
Opening Alsamixer and increasing the master volume to 100% worked for me.. original poster try this and if it works then edit ur 1st post and add this as a soln for others to use..

---

### Post by ~unknown on 2009-11-03
I'm having a similar problem with Ubuntu. Wine somehow "mutes" _all_ the sounds, or messes up the mixer, I don't know. I'd really like to fix this.

---

### Post by raven_ii on 2009-11-03
Hi all,
I solve the problem using alsamixer in terminal as the other people wrote several replies before me. What i saw is that the PCM (wave) channel is mute under alsamixer BY DEFAULT. Some of the applications in KDE 4.3 (as dragon, amarok) are using the master volume as primary audio output channel and the other applications (as VLC, Firefox and so on) are using the PCM (Wave) as a primary audio output channel, that is why the sound from the second ones can't be heard. The other way to check (if you don't know about terminal in Linux), you can go to the volume control (Kmix) in the right corner of the toolbar and with the right click on the mouse you can choose from the menu "Show mixer", then check the PCM (Wave) and Front too. By default PCM is mute, so just unmute it and enjoy.
):P

---

### Post by lukp on 2009-11-03
After some googleing I realized that grub loads old kernel version. The menu.lst was somehow not updated during the system upgrade (probably I did not read some messages carefully and chose somwhere a bad option).

So 'sudo update-grub' should work (in my case for some unknown reason it did not work at the first run and I needed to remove old version of menu.lst and run update-grub again to create menu.lst from scratch).

As of now the proper kernel is loaded and I see much progress (e.g. youtube and skype has sound). There is still some problem with microphone but I will try to work it out tomorrow.

Regards,

lp

---

### Post by verysimple on 2009-11-08
From what I understood about this, KDE doesn't use pulseaudio, but somehow it's been installed after my upgrade to Jaunty. Sound issues experienced by Gnome users after their upgrade (there's always a few out there) aren't necessarily related to KDE sound issues. 

What worked for me (Kubuntu) was to kill pulseaudio and reenable alsa. I also noticed that Amarok2 for some reason launches pulseaudio if it is installed, I don't know why since atm it's not recommended to use pulseaudio on KDE. Pulseaudio somehow prevents other applications (using alsa) from outputting sound (kaffeine, vlc). I therefore purged pulseaudio from my system and everything went back to its old self.

Make sure to stop all applications using pulseaudio before (i.e. all the ones that are able to output some sound prior to these steps).

> rm -r ~/.pulse
killall pulseaudio
sudo alsa force-reload
sudo apt-get purge pulseaudio

I would also suggest to verify that your audio card driver is the primary output device by going to System > System Settings > Multimedia > Device Preference. Select any of the listed driver and click on Test. If the sound plays then that device should probably promoted as the preferred one.

---

### Post by gugushtiuc on 2009-12-29
I had the same problem. My solution was to open Kmix (from sound icon system tray->Mixer) and increase volume for PCM...

---

### Post by Eruaran on 2010-01-16
> **gugushtiuc said:**
> I had the same problem. My solution was to open Kmix (from sound icon system tray->Mixer) and increase volume for PCM...

Yes, worked for me also. Use Kmix or sudo alsamixer and you'll have sound.

This problem is not occurring for KDE users on other distributions. This is a distribution specific issue and not a KDE issue.

On KDE: No desktop or framework is without its flaws but so many people have put so much work into making the KDE SC 4.x truly great. 4.3 is very nice and 4.4 is a polished gem. Whatever your personal preferences are it is certainly very sad to see this continuing trend of people getting on a bandwagon and so eager to bash KDE for non-KDE issues. It is sometimes quite nonsensical and does not help to solve the actual problem.

I have kept abreast of KDE4 developments since the folks first started talking about their vision for a next-generation desktop that would move beyond traditional thinking of the past. The team has moved mountains and deserve the highest praise for their noteworthy efforts that have put KDE at the forefront in a number of still-developing areas.

As Eben Moglen says, "Here, we made this, would you like some? Take it. Its free..."

---

