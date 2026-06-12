---
title: "microphone not working"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by sbutton on 2006-11-03
Hi,

I've been trying for weeks now to get my microphone working on a very old Fujitsu xS PIII 400 MHz PC. When I speak into the mic. it comes out of the speakers OK, but when I try to use Skype or Sound Recorder nothing happens. Sound recorder stops recoring straight away and if I hit record again it hangs.

I've found Alsamixer and switched on the 20-dB boost.

I've been playing with Multimedia Systems Selector, which I had to enable with "Alcarte". This now hangs, but was OK 10 minutes ago (until I selected OSS for input)

The mic. connector is on the front of this PC, and I've also tried plugging the mic. into the line-in on the back, but that doesn't work at all (nothing comes out of the speakers).

I've been reading through the forums, but there are SO MANY people with similar problems it's hard to see the wood for the trees!!

](*,) 

Any ideas please??

Thanks,

Steve

---

### Post by Phosphoric on 2006-11-05
No help to you Steve, but I have exactly the same problems.  I've been searching for two weeks now and have not found a solution.  There are loads of threads out there with this same problem but nobody's come up with a fix yet.

I've been battling Ubuntu for a couple of months now, everything has been a struggle and I rather fear this is the last straw for me.  I went back to Windows XP yesterday and it was such a relief to have everything working properley.

Have you looked at alsamixer in the terminal?  type in "man alsamixer" without the quotes, for instructions how to use it.

If I look at the capture tab, my microphone is marked for capture but I can't wind the volume up.  I suspect it's trying to tell me something but I'm blowed if I know how to fix it. 

I've enabled the microphone in any number of ways in the GUI but it makes no differnece at all.  Sound recorer dosen't record then crashes, phoning Skype test call tells me my mike is not working. ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Phosphoric on 2006-11-06
Anybody :(

---

### Post by sbutton on 2006-11-06
> **Phosphoric said:**
> I've been battling Ubuntu for a couple of months now, everything has been a struggle and I rather fear this is the last straw for me.  I went back to Windows XP yesterday and it was such a relief to have everything working properley.



Hang in there dude. I'm sure you'll (we'll) get an answer soon and your life will be enriched from the learning experience :-) Win XP may be "easier" in many ways, but that's short term thinking. Win XP is expensive, and Vista is going to be even worse. It's poorly designed (monolithic) and over complicated, therefore security is always going to be a huge problem, whereas Linux/Unix is modular by design and therefore has far less interdependencies.

If you stick with Windows, you could regret it for years to come.

Steve

---

### Post by Phosphoric on 2006-11-07
Hope you're not holding your breath Steve.;) 

Nobody got a clue?

---

### Post by sbutton on 2006-11-07
Nope not holding my breath. After my little evangelising for GNU/Linux my main PC's both use XP, one work PC so no choice and one laptop which I might move over. This sound problem is on my wife's kitchen PC, and it's really only so she can contact me easily while I'm working out in the office (in a converted garage) instead of hollering out the back door. I'm planning on installing TeamSpeak when I finally get the mic working.

Unless I get a large bonus or a small win on the lottery in which case I'll get a nice shiny iMac instead :-) .

Anyway, I'm just waffling to help keep the thread alive in the hope that SOMEONE, SOMEWHERE WILL PLEASE GIVE SOME SUGGESTIONS?????

This is really unusual, as in the past most threads I've seen have been answered really quickly.

H E L P !

Steve

---

### Post by mrts on 2006-11-07
If sound is otherwise working, it's probably just up to selecting the right input -- you have to mute other inputs and leave only mic enabled. At least that's how I solved the problem when mic stopped working after upgrading to Edgy.

How to do it: 
[LIST=1]
[*]fire up gnome-volume-control
[*]Edit -> Preferences
[*]Select tracks to be visible: select all
[*]Check Capture pane -- nothing should be muted
[*]Check Switches pane -- only Microphone capture should be enabled (possibly with boost)
[*]Check Options pane -- choose the right microphone
[/LIST]

Now try to record with gnome-sound-recorder. Report back if it's still not working. Also, people have reported that spurious playback outputs may break mic recording, so you may try turning off line-in, video, phone, aux and other obscure playback things as well.

---

### Post by Phosphoric on 2006-11-07
mrts, thanks for the reply,

I've tried all of that before and I've just tried it again, no luck.  I get lots of feedback between the mike and the speakers but no joy in Skype and Sound recorder dosen't even start to record and freezes after a couple of mouse clicks.  Situation normal here. ](*,)

---

### Post by Phosphoric on 2006-11-08
Steve, 
have you tried alsamixer in the terminal?  I'm convinced what I see there is trying to tell me something.  In the capture tab my microphone input is selected in red for capture but has no volume bar above it.  All my other input devices, when selected for capture, have an adjustable volume bar above them.

Have a look at yours.

If there is anybody else out there that has a working version of Skype, could you also have a look and see if you have a volume bar above mic or mic1.

Thanks

---

### Post by SlySmiles on 2006-11-11
Hi,

I'm getting exactly the same symptoms:
With ALSA: Skype not picking up the microphone, but being able to hear it in the speaker.

alsamixer also has the mic in red with no volume support. SoundRecorder just crashes when I try to record.

However when I choose OSS (Open Sound System), I can get the mic working, although I don't look at this as a correct solution. I've gone though all the inputs/options in Volume Control, and everything seems in order.

This problem only manifested itself since the upgrade to edgy.

---

### Post by SlySmiles on 2006-11-11
got it working :)

After a bit of trawling through other posts, and trying different mic input etc, it looks like ALL of the following need to be set up correctly (this is with a AC97 card (VIA 8235)

Playback Tab:
Microphone (not mute, volume high)
IEC958 Volume Playback (not mute, volume high)

(also as a side note I had to set the VIA DXS 1 - 3 to high volume, no mute otherwise all the sounds were very quiet).

Capture Tab:
Capture (not mute, volume high

Switches Tab:
Microphone capture on
Microphone Boost (+20db) on (this is optional, try it on then remove if input is too high)

Options Tab:
Surround Jack Mode: Shared
Mic Select: 1

I also found that once I got it working, then changed some options which then stopped it working, I had to exit/restart Skype before it would work with the correct options.

Hope this helps.

---

### Post by Kalinda on 2006-11-19
Sorry to bring back an old topic, but I didn't feel like starting a new one.

I suffer from the same problem. My microphone doesn't work at all on my Creative SBLive 24-bit, so I took it out and put in the Creative SBLive 5.1, since we had one from way back when.

Now I hear the mic from the speakers, but I can't record anything and Skype says I have a problem with my device. I've turned on Capture and Mic in KMix and checked them in AlsaMixer (although I'm not sure where to find Capture in there). I've played around with it a bit as per the posts in this thread, but nothing is working.

Anyone have any suggestions?

---

### Post by Phosphoric on 2006-11-20
Kalinda,

I've tried every tab and every setting till I'm blue in the face and still that wretched person in Skype tells me she can't here anything.

I haven't used Ubuntu now for a couple of weeks and the small skills that I'd started to pick up are fading away.

Shame that such a fundamental problem can't be fixed. ](*,) 

Thank goodness for Windows. :-#

---

### Post by rigol on 2006-11-22
*up you go*

Same problem here, I have onboard sound, Asus M2N-E motherboard, and can't get the microphone working. had this same issue in Windows also - sound yes, microphone no.

---

### Post by Choc_Salties on 2006-11-22
Well, having the same problem with my rig as well, I'm running Edgy x86 on an AMD 3200+ with an SB Audigy 4; playback works beautifully, recording (in my case, for skype) doesn't:-?

---

### Post by Kalinda on 2006-11-24
Well.. I do have a plan.. but it might not apply to everyone. I have an onboard sound card.. and it works very well with my mic.. but playing back audio with it sounds like crap, which I assume is because the Linux drivers for my VIA chipset aren't very good; the sound card gave me the same trouble in Suse, too, which led me to put in another one.

Anyway, I recently learned it's possible to have two sound cards.. so I think if I could figure out a way to set it up so that the system default was the Creative one.. but I could use the other one for recording, it'd be AOK. I know in Skype you can define which devices you use.. but I get the feeling aMSN won't go that far once it supports audio conversations.

The first thing I need to do, though, is set it up so that the computer can use both sound cards at once, as oppose to just one. Then I'll just mute the sound on the onboard.

Would that work, do you think? I'll have to give it a go sometime; I have some ALSA stuff that might help.

---

### Post by sparigi on 2006-11-27
I solved this problem.
What actually I've supsected is that the microphone inlet is used also as center outlet for the Dolby Surround configuration. That's way I was able to hear from skype, but I wasn't able to speak.
Following a previous answer to this post I've found that alsamixer allow to configure the role for the microphone inlet.
I did this action to solve the problem.
from Terminal  
>alsamixer
as soon as the program appears, hit tab until in the View: row the [All] item is selected.
press right arrow, until the  "Item: Mic-In Mode" is selected. If your problem is similar to mine, the Item for the mic-in mode should be set to "[Center/LFE Output]", press down arrow until [Mic-In] is selected. You should hear also a kind of spike exiting from the loudspeaker.
Press exit, in order to confirm the choice and the try skype, now should be working.

Hope it help.
Sorry for my poor english.

Sergio

Ubuntu is wonderful:

---

### Post by doobit on 2006-11-27
Thanks for following up!

---

### Post by mdecler2 on 2006-11-28
Sorry, I thought I was at the end of the forum on the first page :). I am reading above now...

---

### Post by dracule on 2006-11-29
i dont have an options tab...

---

### Post by 3kravinarayan on 2006-11-30
2 dys old into ubuntu and i refuse to go bac t windows. my mike not working but speakers are. so in skype i can hera but no one can hear me. sound card is detected

H E L P

Ravi bangalore

---

### Post by Phosphoric on 2006-12-01
Hmmm :-k 

Seems to me that my problem is my Santa Cruz sound card.  I have on board sound with one channel busted so it was disabled.  When I re-enabled it in BIOS, magically Sound Recorder worked and the robot lady in Skype can hear what I'm saying.

Looks like another case of Ubuntu/Linux being rather hardware picky or poor drivers.

I've already had to dispense with my perfectly good on board ethernet card for internet and buy another plug in cad to get the internet to work properly. Now it would appear that I have to but a different sound card.

Not too impressed....:(

---

### Post by mc^2 on 2006-12-02
I had a problem with the mic too. Not only it didn't work in skype but I was also unable to record anything in gnome-sound-recorder. I found a not very nice but working workaround. I've got ALSA over nvidia hda if that changes anything. So:

You go to the Volume Control as described, find Edit->Preferences, mark just about all (what I need is actually: the mic, Analog Mix, Capture and Input Source (but I found it a bit hard to say which input source goes to which capture (I've got three of them) so marking all Input sources might be a good idea).

Now, you turn on the Mic, the Analog Mix (all the way up), one of the captures and select the Input Source to Mix. Done. Now you just have to set up the Mic volume.

---

### Post by muxecoid on 2006-12-03
Didn't work. Any more suggestions?

---

### Post by cccc on 2006-12-03
> **muxecoid said:**
> Didn't work. Any more suggestions?

yep, **I've got recording working under dapper drake**:

according to:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

I've done the following:

```
gedit ~.asoundrc
```

add the following text:```

pcm.skype {
   type asym
   playback.pcm "skypeout"
   capture.pcm "skypein"
}

pcm.skypein {
   # Convert from 8-bit unsigned mono (default format set by aoss when
   # /dev/dsp is opened) to 16-bit signed stereo (expected by dsnoop)
   #
   # We can't just use a "plug" plugin because although the open will
   # succeed, the buffer sizes will be wrong and we'll hear no sound at
   # all.
   type route
   slave {
      pcm "skypedsnoop"
      format S16_LE
   }
   ttable {
      0 {0 0.5}
      1 {0 0.5}
   }
}

pcm.skypeout {
   # Just pass this on to the system dmix
   type plug
   slave {
      pcm "dmix"
   }
}

pcm.skypedsnoop {
   type dsnoop
   ipc_key 1133
   slave {
      # "Magic" buffer values to get skype audio to work
      # If these are not set, opening /dev/dsp succeeds but no sound
      # will be heard. According to the alsa developers this is due
      # to skype abusing the OSS API.
      pcm "hw:0,0"
      period_size 256
      periods 16
      buffer_size 16384
   }
   bindings {
      0 0
   }
}
```
and changed in the skype settings from ALSA to **OSS**

**now the recording works great !**

---

### Post by Phosphoric on 2006-12-07
Just fitted an old Sound Blaster card and it works perfectly in Sound Recorder and Skype although the playback quality is not so good.

This will keep me out of trouble until I can find a fix for my Santa Cruz card.

---

### Post by ansjos on 2006-12-09
I am also sitting here with almost the same problem, however i can faintly hear myself...

What i wonder is if ANYONE has got the microphone to work???

---

### Post by warkro on 2006-12-11
Thanks very much...this worked for me.
However, I just opened up gnome-volume-control
Edit > Preferences > (checked the 3 microphone options) 

Options > Mic-In mode = Mic-in


> **sparigi said:**
> I solved this problem.
What actually I've supsected is that the microphone inlet is used also as center outlet for the Dolby Surround configuration. That's way I was able to hear from skype, but I wasn't able to speak.
Following a previous answer to this post I've found that alsamixer allow to configure the role for the microphone inlet.
I did this action to solve the problem.
from Terminal  
>alsamixer
as soon as the program appears, hit tab until in the View: row the [All] item is selected.
press right arrow, until the  "Item: Mic-In Mode" is selected. If your problem is similar to mine, the Item for the mic-in mode should be set to "[Center/LFE Output]", press down arrow until [Mic-In] is selected. You should hear also a kind of spike exiting from the loudspeaker.
Press exit, in order to confirm the choice and the try skype, now should be working.

Hope it help.
Sorry for my poor english.

Sergio

Ubuntu is wonderful:

---

### Post by dsapoki on 2006-12-13
my sound worked perfectly until 3 days ago. Now my mic stopped. I am quite upset since skype was my only possibility to comunicate with my family. Anyone can help?

---

### Post by brazzmonkey on 2006-12-14
oho, same thing happens to me. maybe something got updated in the meantime ?

---

### Post by dalmolin on 2006-12-14
The following instructions from MC 2 worked for me, thank you for them!!

Quote:

 Re: microphone not working
I had a problem with the mic too. Not only it didn't work in skype but I was also unable to record anything in gnome-sound-recorder. I found a not very nice but working workaround. I've got ALSA over nvidia hda if that changes anything. So:

You go to the Volume Control as described, find Edit->Preferences, mark just about all (what I need is actually: the mic, Analog Mix, Capture and Input Source (but I found it a bit hard to say which input source goes to which capture (I've got three of them) so marking all Input sources might be a good idea).

Now, you turn on the Mic, the Analog Mix (all the way up), one of the captures and select the Input Source to Mix. Done. Now you just have to set up the Mic volume.
Reply With Quote

---

### Post by dalmolin on 2006-12-14
ps.    I did have to set the sound device option to OSS ... ALSA didn't work for some reason.... I used the Skype tar file to install... will give it a whirl with the .deb install and see if that makes a difference

---

### Post by dsapoki on 2006-12-20
heureka, it works, I cannot tell you how comes it stpped working more then a week ago(no update...), but now, only I followed dalmolin, in volume controle in capture, little icon of mic was crossed over. I just uncrossed it, and it works. ASUS A6K-Q023H, edgy eft

---

### Post by shawnlogic on 2007-01-28
Hey Everyone,
I recently installed Ubuntu, and I thought I would add how I got my microphone working.
I have the VIA 8295 sound driver.

I used the alsamixer, and I had to change which microphone I was using. From Mic Select, I had to change it from mic1 to mic2.

Hope this helps anyone in the future.

---

