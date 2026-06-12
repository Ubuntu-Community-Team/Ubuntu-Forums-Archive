---
title: "VLC Sound crackling"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by Aurdal on 2007-04-05
Lately I've been experiencing crackling sound in VLC. The sound is only crackling sometimes, speech and the likes sounds ok, but things like the sirens of an ambulance triggers crackling.

I've tried with Totem and Mplayer as well, and neither of these two have this problem.

So, does anyone have any suggestions?

Thanks.
- Kristoffer

---

### Post by heimo on 2007-04-05
I have the same problem. Haven't investigated what causes it, but I've found that turning down the volume slider in VLC and compensating by turning up master volume (volume controller / volume on my amplifier) mitigates or even gets rid of this annoying problem. Seems it's only VLC (version 0.8.6 / on Feisty), Amarok is working just fine.

---

### Post by Aurdal on 2007-04-05
Yeah, I'm on feisty too.

---

### Post by heimo on 2007-04-06
It's very strange noise too, it's sounds like the signal is clipping very badly. I've tried to delete ~/.vlc to make sure that I have default settings, but the problem stays. Turning up the volume on VLC and down in volume control gives me a low volume, very distorted sound.

I found couple similar posts, but this problem is definitely new to me.
[http://ubuntuforums.org/showthread.php?t=143502](http://ubuntuforums.org/showthread.php?t=143502)

I have a feeling that the problem is lot worse with lower quality, low bit rate MP3s than with higher bitrate files (>128k). It almos feels like it "amplifies", detects all tiny problems and makes them 1000x worse than in original.

---

### Post by Frédéric STEMMELIN on 2007-04-15
Same problem for me, but only under Feisty. Under Edgy i dont have such problems with VLC ... (i am using it watching internet TV over ADSL (Free multiposte).

---

### Post by Lafie on 2007-04-19
Yep, same problem here too. 
Combination of VLC 0.8.6 with ALSA and Feisty makes for good crackling sounds. No problems with Amarok (also ALSA) or any other sound-producing program (flash etc.)
So the problem is definitely in VLC. I'll try older versions of VLC in a sec and see if it's any better.

---

### Post by gerrymoth on 2007-04-19
Aaaah!

Same things happened to me after playing a mp3 in VLC, sounds crackling and DVD's won't play when I load them in.

---

### Post by Lafie on 2007-04-20
I haven't been able to succesfully install previous versions of VLC (sorry), but I have figured out the problem is the ALSA audio output.
A temporary workaround is to change the audio output module to OSS:
1. in VLC go to Settings and then Preferences
2. click on Audio and then on Output Modules
3. now enable Advanced Options at the bottom-right of the screen
4. You should now be able to choose the Audio output module, select Linux OSS audio output
5. Click Save and restart VLC

So the problem is in the ALSA plugin for VLC in combination with Feisty. It could just be a bad VLC package, but considering the low amount of complains I'm guessing it has something to do with a certain hardware setup. 
Could everyone please post their hardware setup, especially soundcard or if onboard sound, the motherboard?

---

### Post by heimo on 2007-04-20
Yes, I can confirm that changing from Alsa output to OSS makes the problem go away. (Kind of - Alsa gives over all better sound when working correctly.)

Running integrated Intel sound. My motherboard is [Asus P5B]("http://www.asus.com/products4.aspx?l1=3&l2=11&l3=307&model=1178&modelmenu=1").
```
lspci | grep -i audio
```
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

---

### Post by Huffalump on 2007-04-20
> **heimo said:**
> I have a feeling that the problem is lot worse with lower quality, low bit rate MP3s than with higher bitrate files (>128k). It almos feels like it "amplifies", detects all tiny problems and makes them 1000x worse than in original.

FWIW, I've just noticed problems with crackling distortion in Feisty only, but not just with mp3;  I have FLACs being ruined during output, too.

Edit: 
> **Lafie said:**
> 
1. in VLC go to Settings and then Preferences
2. click on Audio and then on Output Modules
3. now enable Advanced Options at the bottom-right of the screen
4. You should now be able to choose the Audio output module, select Linux OSS audio output
5. Click Save and restart VLC


Hey, that worked just great for me.  Big difference in sound :] Thanks!  (SoundBlaster Audigy card on Feisty in use, though I could also test an nForce3 onboard if you wanted)

---

### Post by Lafie on 2007-04-20
I've just been able to compile an older version of VLC (0.8.5) and the same problem occurs. So it appears to really be a problem in Feisty, and how it handles ALSA.
On the other hand, Amarok with ALSA has no problems at all, so I don't know what it is anymore. For now just use the OSS audio module.

P.S. it appears to happen with any soundcard or onboard sound, so that's not the problem.

---

### Post by Aurdal on 2007-04-22
With feisty being released next Sunday I'm guessing it'll be fixed pretty shortly after.

---

### Post by Lafie on 2007-04-22
> **Aurdal said:**
> With feisty being released next Sunday I'm guessing it'll be fixed pretty shortly after.

Next Sunday, eeeh, wait a sec, am I the only one under the assumption that Feisty is allready released?

I brought this problem to the VLC forums to seek out a developers response, and this is what he (Rémi Denis-Courmont) had to say:
[QUOTE=Rémi Denis-Courmont]The ALSA issue vanished ages ago, basically when I switched from 1.0.10 to 1.0.11, and I never saw it again. Besides, with no VLC-ALSA maintainer at the moment, unless someone contributes a patch it's not realistically going to change, I'm afraid.[/QUOTE]

So no patching on their end, all hope is on the Feisty developers or contributers now.

---

### Post by Aurdal on 2007-04-24
Well, it's released now. :p

---

### Post by lingnoi on 2007-04-25
I just upgraded my Samsung R55 from Edgy to Feisty and I am getting this exact problem.

---

### Post by Steve H on 2007-04-25
I've noticed this problem under Feisty as well, especially when watching DVD with lots of music on. I presumed it was my crappy old Soundbalster Live! card, not being up to the job. It works fine with Amarok.

I'll try the OSS driver and see how i get on.

---

### Post by Aurdal on 2007-04-26
The problem with the OSS driver is that you can't use other sound applications simultaniously along with VLC.

---

### Post by Azakus on 2007-04-26
I've been having that crackling issue as well.
My card:
```
01:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
```
I'll see if any newer SVN versions of VLC fix this.

---

### Post by Azakus on 2007-04-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Found the bug on launchpad.

---

### Post by Azakus on 2007-04-26
Hmm, I tried switching to the SDL plugin for VLC and the problem seems elminated.
Just install the sdl plugin and switch to it in VLC.
```
sudo aptitude install vlc-plugin-sdl
```

---

### Post by Neuralgia on 2007-04-27
the same thing happened to me

It's not a bug (at least no on my case)

My laptop: dell inspiron 6400

In the VLC go to -> Settings -> Preferences

Modify your "Default Sound Level" to something lower. Mine is in 250 and now sound normal. I had like 650 or something.

Hope this helps. I'll be glad to know if I helped

---

### Post by Lafie on 2007-04-29
> **Neuralgia said:**
> the same thing happened to me

It's not a bug (at least no on my case)

My laptop: dell inspiron 6400

In the VLC go to -> Settings -> Preferences

Modify your "Default Sound Level" to something lower. Mine is in 250 and now sound normal. I had like 650 or something.

Hope this helps. I'll be glad to know if I helped

Nope, that just makes the sound level lower (ofcourse), and it might seem that you don't hear it anymore, but the crackling is still there.
I can confirm that the SDL output module works aswell, but I don't know if the audio quality is better than OSS.
Someone mentioned that they can't hear other sound producing programs when running VLC with the OSS module, but I have no such problem.
Also, you can't expect a newer VLC version to fix the problem, because there is noone maintaining the ALSA module, so no changes will be made (see my previous post).

Greetz,
Lafie

---

### Post by lazork on 2007-05-04
I think I've found a solution to this problem (or at least it fixed mine).
In the VLC go to -> Settings -> Preferences
then choose Audio -> Output Modules -> ALSA
Hit "Refresh List" and under ALSA Device Name choose the right one (for me it was set to "Default" and I had to change it to the one saying "hw:0,0").
Click "Save" and it should instantly fix the sound issue.

---

### Post by Azakus on 2007-05-05
Working for me too! Great fix!
Also, SDL causes audio/video sync issues in most of my files, so I've stopped using it.

---

### Post by heimo on 2007-05-05
Changing ALSA device from Default to specific (hw:0,0) one seems to work for me too. Repeated it couple times using material where the problem was evident. Thanks lazork. Someone please post this fix/workaround to launchpad (if not already done).

---

### Post by Jergar on 2007-05-05
Works here too. Many Thanks!  
I had to set it to hw 0:3 (Multichannel Output) of my Audigy 2 ZS. HW 0:0 crashed the vlc immediately.

Regards
Jergar

---

### Post by kpel on 2007-05-05
Confirming the problem as well, and confirming the fix.  This is on a Gigabyte GA-965P-DS3 motherboard using the onboard audio (Realtek ALC883/HD Audio)

---

### Post by xdarkxanarchyx on 2007-05-05
I used to have this problem too, Never bothered trying to fix it, I just turned the volume in VLC down a bit and everything was fine. 
Using with a ECS Elitegroup C19-A SLI mobo
:guitar:

---

### Post by mrfuzzemz on 2007-05-05
Selecting the device instead of leaving it on Default worked for me too. Thanks.

---

### Post by phansiizwe on 2007-05-06
The fix of Heimo; turning down the VLC volume works for me, but the selection of anything other than default in the ALSA settings leads to no sound...

The choices I have are:

```
Default
Audigy 1 [SB0090]: ADC Capture/Standard PCM Playback (hw:0,0)
Audigy 1 [SB0090]: Multichannel Capture/PT Playback (hw:0,2)
Audigy 1 [SB0090]: Multichannel Playback (hw:0,3)
```

---

### Post by kaede on 2007-05-06
i just turning down the VLC volume and turnin up my system volume. the cracking sound is gone. but i'll try with that hw thing.

---

### Post by Ebuntor on 2007-05-09
> **lazork said:**
> I think I've found a solution to this problem (or at least it fixed mine).
In the VLC go to -> Settings -> Preferences
then choose Audio -> Output Modules -> ALSA
Hit "Refresh List" and under ALSA Device Name choose the right one (for me it was set to "Default" and I had to change it to the one saying "hw:0,0").
Click "Save" and it should instantly fix the sound issue.

It does fix the crackling problem unfortunately it seems to be only a partial solution.
On my system when using the "hw:0,0" ALSA device in VLC you can only have sound for one application at a time. For example if VLC has opened a media file and you pause it, start Firefox and watch a youtube video there's no sound. It's the same with opening multiple VLC windows. 

You first have to close VLC to get any sound with a different app. I have no idea if this is just on my system or a general problem.

---

### Post by Mr Gimp on 2007-05-13
> **Ebuntor said:**
> It does fix the crackling problem unfortunately it seems to be only a partial solution.
On my system when using the "hw:0,0" ALSA device in VLC you can only have sound for one application at a time. For example if VLC has opened a media file and you pause it, start Firefox and watch a youtube video there's no sound. It's the same with opening multiple VLC windows. 

You first have to close VLC to get any sound with a different app. I have no idea if this is just on my system or a general problem.

This happens on my system as well (finding the answer pushed me to join these forums...howdy all by the way :p) so I think it may be a general problem. Hopefully it's not just us :p

---

### Post by Steve H on 2007-05-14
From personal experience I have found that using the OSS driver in VLC works best for me. I'm using a Creative Sounblaster Live!, and had problem using the ALSA driver when listening to DVD's of music, the same as you folks, crackling and popping on the sounds. Once I'd changed it to the OSS driver I have not had any more problems.

:)

---

### Post by Ebuntor on 2007-05-14
> **Mr Gimp said:**
> This happens on my system as well (finding the answer pushed me to join these forums...howdy all by the way :p) so I think it may be a general problem. Hopefully it's not just us :p

Hi Mr Gimp, welcome to the forums! :) Glad I'm not the only one with that problem (not sure if that's the right thing to say in this case :razz:)


[quote=Steve H]From personal experience I have found that using the OSS driver in VLC works best for me.[/quote]

Oh yeah I forgot to mention that I have the same problem when using the OSS driver just as the ALSA driver problem I mentioned in my previous post.

---

### Post by Steve H on 2007-05-14
Hmmm! odd?!

I have found [_this_]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025") which might be of use. It mentions symptoms similar to yours, but again suggests using OSS:

> VLC:
audio output module: standard (poor sound)
audio output module: ALSA (poor sound)
audio output module: OSS (works great even at volume level "440")

Are you restarting VLC after changing the settings?? It is worth restarting VLC in order to set the new modules.

I have also found [this]("http://notes.minty.org/cgi-bin/wiki.pl?TX1XP_-_Multimedia") which mentions:

> I have found that the sound from the built in speakers can be a little crackly at times. These seems to be limited to vlc player, using mplayer appears to not suffer this problem. 

To fix this crackly audio in VLC (v 0.8.4) I did the following: 

 Settings menu -> Preferences
 Audio -> Output Modules -> OSS
 Check "Try to work around buggy OSS drivers"

Let me know if these help, I''l keep looking for an answer.

:)

---

### Post by Ebuntor on 2007-05-14
> **Steve H said:**
> Hmmm! odd?!

I have found [_this_]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/103025") which might be of use. It mentions symptoms similar to yours, but again suggests using OSS:



Are you restarting VLC after changing the settings?? It is worth restarting VLC in order to set the new modules.

I have also found [this]("http://notes.minty.org/cgi-bin/wiki.pl?TX1XP_-_Multimedia") which mentions:



Let me know if these help, I''l keep looking for an answer.

:)

Thanks all of those do work, IIRC most of them have been monioned in previous posts. :)

I'm sorry I think I wasn't quite clear in my pervious post. In post #32 I said: 
> It does fix the crackling problem unfortunately it seems to be only a partial solution.
On my system when using the "hw:0,0" ALSA device in VLC you can only have sound for one application at a time. For example if VLC has opened a media file and you pause it, start Firefox and watch a youtube video there's no sound. It's the same with opening multiple VLC windows. 

You first have to close VLC to get any sound with a different app. I have no idea if this is just on my system or a general problem.So the solutions mentioned earlier and your solutions do fix the crackling problem. It's just that **Mr Gimp **and me don't get any sound when we open multiple VLC windows or VLC in combination with another program such as a browser. (the same applies to Totem and Mplayer)

---

### Post by Steve H on 2007-05-14
Ah! right!, I  should have been paying better attention.....

:)

---

### Post by Mr Gimp on 2007-05-14
> **Ebuntor said:**
> T.... It's just that **Mr Gimp **and me don't get any sound when we open multiple VLC windows or VLC in combination with another program such as a browser. (the same applies to Totem and Mplayer)

I just tried Mplayer, and the same result, if the ALSA driver is set to "hw:0,0" it can't play multiple sounds at once.  However, keeping Mplayer set as being "default driver" instead, allowed multiple sounds, but didn't crackle as VLC does.  

To me at least, that makes it sound like a problem within VLC (though I am a total newbie to all of this :p).  Mean anything to anyone else?

---

### Post by omegamormegil on 2007-05-22
I also have crackly sound playing Wesnoth, which I am assuming is related to the VLC sound issues.  I've been watching the forums, but I don't really see anything addressing this issue.  I see lots of forum help for people with NO sound, but that's not my problem.  Anyone else have any luck fixing the crackly ALSA sound yet?  

I'm using OSS in VLC in the meantime, which DOES let me play movies with PERFECT sound, but it looks to me like ALSA in general needs fixing for other programs - not just VLC.

---

### Post by Azakus on 2007-05-22
Look farther up in this thread.
In VLC, click Settings -> Preferences -> Audio -> Output Modules -> Alsa -> "Refresh List" -> pick hw:0,0 (most likely the output for your speakers, if not, mess with it until you hear sound)

---

### Post by vasilis34 on 2007-05-28
Same problem for me !
Switching to OSS module solves the problem, but with OSS I can't have 5.1 sound. Is there a way to enable 5.1 sound using the OSS driver?
I managed to get it working with ALSA creating a .asounrc file as it is proposed in ubuntuguide.org. Does anyonw know a similar way to enable 5.1 sound in OSS. 
Another thing that seems pretty weird to me. When I enable ALSA drivers vlc, but also totem, seems to get much heavy, whereas with OSS even large movie files play flawless. Is it normal? Maybe, has something to do with the .asoundrc file and the replication of sound to the rear speakers........ , I don't know.

Anyway,the one thing I can tell is that sound setup in linux is a really tough task... It's my 3rd day playing with feisty and still messing up with sound problems...........  

If anyone can suggest a solution, plz plz do so !!

---

### Post by jis on 2007-06-17
I wonder why [VideoLAN site]("http://www.videolan.org/vlc/download-ubuntu.html") guides to use vlc-plugin-esd in Ubuntu. I have not tried the plugin, but sound works. I use Dapper and in my experience there is no other media player than VLC that can output high enough volume from my Creative Labs Sound Blaster Live! Value sound card. However, I still don't understand why the default audio output volume is ranged from 0 to 1024, since value 512 seems to be full volume anyway. For the sound card, output volume of the analog line out 2 connector is controlled by Wave Surround slider (in for example QAMix mixer) and VLC's volume slider (that controls the analog line out 1 connector, too); I don't know another media player that gives such control to the volume of the sound it plays. I don't notice any sound crackling with the sound card.

P.S. Oh, at leat XMMS's ALSA 1.2.10 output plugin can be configured to use software volume control, but with it you can not set that high volume.

---

### Post by Ebuntor on 2007-06-17
> **jis said:**
> I wonder why [VideoLAN site]("http://www.videolan.org/vlc/download-ubuntu.html") guides to use vlc-plugin-esd in Ubuntu.

Holy sh*t, using the vlc-plugin-esd actually worked! Not only did it fix the crackling problem but (instead of using the OSS or ALSA output) it also fixed the problem of only being able to get sound in one VLC window. 

Thank you very much sir, I'll  post a comment about this on Launchpad. :D

---

