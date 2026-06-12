---
title: "[solved] sound over hdmi ubuntu 9.10 nvidia 9300"
date: 2009-11-20
forum: Multimedia Software
---

### Post by madscot on 2009-11-20
I'm posting this as hopefully it will save others the frustration I had trying to get audio over hdmi working on my zotac 775 itx board!

I was using 9.04 & had got *some* audio going over hdmi by following various guides, breaking it a few times and finally unmuting the IE958 switch, vlc, banshee etc worked but no joy with firefox which was irritating for iplayer, youtube etc

I did a clean install of 9.10 in the hope that it would sort my audio issues, still no audio over hdmi & all of the guides were for 9.04 or earlier

This is how I eventually got it working after a few more breaks and a re-install & was shocked at how easy it was!

In the sound/volume manager had my audio set as digital out (hdmi)

In a terminal type

```

alsamixer

```

if alsamixer is not installed it can be with the follwing command

```

sudo apt-get install alsamixer

```

once you have the alsa mixer open in the terminal use the arrow keys to move across to the IE958 1 switch, which in my case was muted

Bit of frustration ensued here as arrow keys did nothing, then hit 'm' out of experiment, this unmuted it & voila everything now works! :biggrin:


Hope this saves someone the frustration I had!

---

### Post by kaland on 2009-11-20
Nice!! So simple, i have tried to use alsamix to fix this problem myself. But i did not know option m=mute :P 

Thanx Man!

---

### Post by Raptor Ramjet on 2009-11-25
But the real question is why is HDMI audio muted by default ?  That's just dumb.

I too had tremendous difficulty getting HDMI audio to work under 9.04 (which involved finding out this "trick" plus lots of other stuff)  

But after upgrading to 9.10 it was fundamentally broken again so I've simply given up with Ubuntu & HDMI for the moment as it just doesn't work (well not without sacrificing far, far too much of your time)

Shame really but there you go.

---

### Post by zulli1942 on 2009-11-28
Unfortunately in the same boat as raptor. I was able to get it to work in 9.04. Running Mythbuntu 9.10 with MSI Digital board.

---

### Post by SpareXX on 2009-12-03
Oh, god i love you mate, works like a charm :)

Finally i can find the popcorn, thanks!
:popcorn:

---

### Post by sites on 2009-12-03
Nice tip!  This gives me a beep when i "Test" it in Sound Preferences.  But i still don't hear anything through VLC, flash, or xbmc.  It works through Movie Player, but i need it in the other apps.  Anyone got an idea what to do here?

---

### Post by sites on 2009-12-04
Ok i fixed it with...

Custome Device : hdmi

Still no navigation sounds though.

---

### Post by chandragaajula on 2009-12-23
Works like a charm. Thanks a lot for posting this. You saved me from a ton of frustration.

---

### Post by lenkiatleong on 2009-12-26
> **madscot said:**
> I'm posting this as hopefully it will save others the frustration I had trying to get audio over hdmi working on my zotac 775 itx board!

I was using 9.04 & had got *some* audio going over hdmi by following various guides, breaking it a few times and finally unmuting the IE958 switch, vlc, banshee etc worked but no joy with firefox which was irritating for iplayer, youtube etc

I did a clean install of 9.10 in the hope that it would sort my audio issues, still no audio over hdmi & all of the guides were for 9.04 or earlier

This is how I eventually got it working after a few more breaks and a re-install & was shocked at how easy it was!

In the sound/volume manager had my audio set as digital out (hdmi)

In a terminal type

```

alsamixer

```if alsamixer is not installed it can be with the follwing command

```

sudo apt-get install alsamixer

```once you have the alsa mixer open in the terminal use the arrow keys to move across to the IE958 1 switch, which in my case was muted

Bit of frustration ensued here as arrow keys did nothing, then hit 'm' out of experiment, this unmuted it & voila everything now works! :biggrin:


Hope this saves someone the frustration I had!

Hi,

May i ask the following questions?

Q1. What audio card are you using that has HDMI and works with ubuntu 9.10? I am using optical cable from my Intel DP35DP mobo into AV and i can only get Stereo, i.e., 5.1 dolby/dts cannot make it thru the optical cable. It would be good to know which brand/model of audio card that you are using.

Q2. Now that you could get audio over hdmi, is it Stereo or 5.1 dolby/dts or both? From sound preferences, i could only select digital stereo which uses the optical path. I could see 5.1 analogs option but they are not going the optical path.

Q3. Have you tried streaming HD codecs over hdmi, i.e., movies from blu ray  disc that has Dolby TrueHD or DTS HD MA codecs? I am wondering if ubuntu 9.10 supports these HD codecs or not. If anyone tried, it would be good to know which audio/video card you're using over hdmi.

I am still struggling to stream dts/dolby over optical cable to my AV. Hope to hear from gurus in this forum but if hdmi is the way to go, i guess i will just skip the optical path.


Cheers
Len

---

### Post by joeyfarmer74 on 2009-12-30
i have an acer revo and do not get sound with any of my web browsers...i am running kubuntu 9.10....sound works in dragon player but not for video on websites i tried the alsamixer it was not muted and hda nvidia is at top of output device preferences.

---

### Post by chandragaajula on 2010-01-09
Strangest thing happened this morning. On my Ubuntu 9.10 I did an update using the "Update Manager". Now, video driver is giving me trouble and my sound has stopped working.

Has anybody solved this problem?

---

### Post by metjay on 2010-01-12
> **madscot said:**
> ...
Hope this saves someone the frustration I had!

DUDE! Yes it did, thank you! Sir, I'm glad to hand you 1k internets for this.

---

### Post by sffndude on 2010-01-19
THANKS!
This worked great for getting HDMI audio to work on my Zotac Mag running Ubuntu 9.10

Because of your solution I was only frustrated for 15 minutes or so - before I found this thread of course :D

TRS

> **madscot said:**
> 

This is how I eventually got it working after a few more breaks and a re-install & was shocked at how easy it was!

In the sound/volume manager had my audio set as digital out (hdmi)

In a terminal type

```

alsamixer

```if alsamixer is not installed it can be with the follwing command

```

sudo apt-get install alsamixer

```once you have the alsa mixer open in the terminal use the arrow keys to move across to the IE958 1 switch, which in my case was muted

Bit of frustration ensued here as arrow keys did nothing, then hit 'm' out of experiment, this unmuted it & voila everything now works! :biggrin:


Hope this saves someone the frustration I had!

---

### Post by cutleryman on 2010-02-05
I'm afraid I am a complete first timer with Linux although reasonably proficient on MS OS.  However I'm finding it all a little frustrating.  I'm also not getting any sound through the HDMI from a Acer Revo running Ubunto 9.10; this is after having tried the 'unmuting' on the Alsamixer terminal.  Does any one else have any clues - but please be gentle with me as I really don't know my way round here yet!:confused:

Sorry about jumping onto the thread too....

Thanks in advance,

Cut

---

### Post by dlabelle11 on 2010-02-06
sweet...  this solved my problem.
you have to select the proper hardware under sound preference


Also when your unmuting, do the one with a "1" at the end...

theres my two cents

---

### Post by luchtzak on 2010-02-19
Got the same problem, hdmi sound out not working on my tv . 

when in sound preferences I select R700 Audio Device [Radeon HD 400 Series] Digital Stereo (HDMI) no more sound on the laptop either. 

Any suggestions ?

---

### Post by autumnraine on 2010-02-23
Thank you! This solved it for me. Instead of using the command line/terminal, I installed the Gnome Alsa Mixer, and put a check beside the third IEC958 option. Suddenly the sound was pumpin' out of my monitor speakers over HDMI, using both Songbird and Amarok (haven't tried others yet, I'll let you know if they don't work). Prior to doing this I'd also completely uninstalled all the pulseaudio stuff I could, I'm not sure if that was necessary though, I just figured it might be since I hear pulseaudio is really muddled. :popcorn::D:KS

To the original poster, you deserve a ton of beans!

---

### Post by autumnraine on 2010-02-23
Spoke a bit too soon, the audio won't work in any video player.... I'll keep you posted. :(

---

### Post by autumnraine on 2010-02-24
Reinstalled the pulseaudio so that both that and alsa are on the system, and now the video players' sound works but not the audio players' sound, or Firefox's. This is ridiculous. :confused:

---

### Post by DanceR0b0t on 2010-03-14
OMG, I LOVE YOU! Been trying to figure this out for two days! I can now watch the Mighty Boosh, Darkplace, and Snuff Box with digital audio, Cheers! \\:D/

---

### Post by brad080283 on 2010-05-16
Thanks!!! Solved my HDMI sound problem on the NT-330I netbox on ubuntu 10.04.
Hope this helps someone else that might be searching.

---

### Post by diogosales on 2010-05-27
Thanks, solved!

---

### Post by 375311 on 2010-08-09
For anyone using Ubuntu 10.4 + you might find it as this in the 
aslamixer "S/PDIF 1" instead of "IE958 1", just remove mute off
it and all should work!

@Thread Starter
Thanks! this really helped!

---

### Post by dakkar9999 on 2010-08-09
Well, not sure why, but my HDMI sound is dead.  Used to work until a day or two ago.  Not sure if it was broken by a new package.

I've looked into AlsaMixer, but the S/PDIF 1 is set on 00 (green) not MM, so it should be working.

Suggestions?

---

### Post by 375311 on 2010-08-09
What "new" package did you install?
Have you tried uninstalling that particular package?

---

### Post by dakkar9999 on 2010-08-10
Nevermind.  Someone had pulled the cables...  It was a "hardware" problem... ;)

Fixed.

---

### Post by FokkerCharlie on 2010-08-28
Hmmm....

I have a problem here.  I also have nVidia graphics (GT220) and HDMI-out and no sound, but when I open alsamixer and choose the nVidia card, all the levels are at 00.  I can mute and unmute, but never increase any level above 0!

Any ideas?

Charlie

```
$ lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```

EDIT:

solved:

Upgraded alsa using the ppa described here:
[http://ubuntuforums.org/showthread.php?t=1547688](http://ubuntuforums.org/showthread.php?t=1547688)

Added this line:
load-module module-alsa-sink device=hw:1,9
to:
/etc/pulse/default.pa

and this line:
enable_msi=0 probe_mask=0xffff,0xfff2 
to:
/etc/modprobe.d/sound.conf

---

### Post by lidex on 2010-08-28
It probably won't work without the proper driver versions. have a look here:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

### Post by bartlomiejp on 2010-10-06
Thanks madscot, thanks to you I didn't throw a laptop through the window !!

---

### Post by as2003 on 2010-11-08
> **madscot said:**
> I'm posting this as hopefully it will save others the frustration I had trying to get audio over hdmi working on my zotac 775 itx board!

Hope this saves someone the frustration I had!

OP FTW! Thx.

This worked for my Zotac Mag HD-ND01 ION & Ubuntu 10.04 LTS. Was labelled 'S/PDIF 1' instead of 'IE958 1' though.

---

### Post by bignellrp on 2011-01-28
> **as2003 said:**
> OP FTW! Thx.

This worked for my Zotac Mag HD-ND01 ION & Ubuntu 10.04 LTS. Was labelled 'S/PDIF 1' instead of 'IE958 1' though.

This worked for me, although as someone else posted, no navigation sounds within XBMC.  Only just got general sound working thx to this thread so i will post again once i figure out the navigation sounds.

---

### Post by bignellrp on 2011-01-28
> **bignellrp said:**
> This worked for me, although as someone else posted, no navigation sounds within XBMC.  Only just got general sound working thx to this thread so i will post again once i figure out the navigation sounds.


Fixed,

Just add this to the top of your .asoundrc file:

pcm.!default {
type plug
slave {
pcm "hdmi"
}
}

---

### Post by bignellrp on 2011-01-28
Btw, im running xbmc.live.Dharma10.0 which has Ubuntu 10.10 for a backend on my new Zbox HD-ND22

---

