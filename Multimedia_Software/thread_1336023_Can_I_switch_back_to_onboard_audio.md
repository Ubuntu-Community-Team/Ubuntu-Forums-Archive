---
title: "Can I switch back to onboard audio?"
date: 2009-11-24
forum: Multimedia Software
---

### Post by Man with Hat on 2009-11-24
I thought that this would be relatively easy, but its becoming very frustrating. I have had it with my X-fi card. It was working great, I think that Freedoom has had a hand in disabling my happiness too. For some reason there are times that Freedoom will not exit and then when I force-restart the computer, I have no sound. Every time I try to do something, I lose more of my sound card, it will work with a media player, then it won't, then my input options are gone, then all I have is a little squeak noise every time that an actual sound is supposed to be made (ie opening evolution would normally make a click type noise, now I get a squeak, pressing apply = squeak) Nothing seems to get my sound back unless I completely overhaul linux!!

:cry::cry::cry::cry::cry:

I would like to just use my onboard audio as I am fed up with trying to make this crap work! However, I can't seem to find it. In sound preferences -> hardware, only the x-fi is mentioned (my onboard is enabled in bios too). When I type "aplay -l" I get this:

**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Where did my onboard audio go? Am I just to roam this earth with a week of sound at a time? It's making me want to buy windows just to get some reliable sound!

---

### Post by Yellow Pasque on 2009-11-24
Have you tried OSS4? It doesn't support surround for the X-fi, but it should give you reliable sound assuming your specific model is supported. [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Man with Hat on 2009-11-25
No, I'll check that out. Thanks :)

---

### Post by Man with Hat on 2009-11-25
Just a thought too if anyone is reading these. Before I go all out and switch back, I noticed that there is sound in the guest login (unless I play freedoom for 5 minutes - I'm telling you, something is wrong there). Is there a way to make the sound settings reset to defaults every login (or just reset to how it was after I installed everything)? I think that would fix the problem as I believe ubuntu is trying to be too clever and keep all of my sound the way it was the last login. I'd rather have to move the slider every login (as its default is mute?!?) than have to go through this problem all of the time. Anyone help?

---

### Post by Man with Hat on 2009-12-12
I've finally found a few minutes to try this out. I've installed the OSS4 successfully (I think) however I wasn't able to get the package libcanberra from the PPA source. It doesn't appear anywhere in synaptic nor if I try and apt-get install it. When I ran the test sound, I had that beeeep when I used the onboard and not in the X-fi (which was a good sign I thought). There is a mixer for both my onboard as well as my X-fi in the ossxmixer, but I still have no sound. I ran an audio track to test the media sounds, but I get nothing out of either the onboard or the x-fi. An icon now appears at the top of my screen (I think it says 4front but its hard to read) and it shows that x-fi is selected. I'm not sure how to change this to onboard. Unless of course I just rip the sound card out of the computer, and considering how I feel about my soundcard these days, I may not be too careful in doing it!!! 

Any suggestions?

---

### Post by 73ckn797 on 2009-12-12
Back to your post question.

Switching back to on-board audio may be as simple as a BIOS setting. That is assuming you have a switch and it is off due to the addition of an add-on card.

---

### Post by Man with Hat on 2009-12-12
Thanks for the speedy reply. I did think of this, but I haven't been able to find anything in my bios to do with the X-fi. The AC97 audio is very easy to find, and I have switched that off when I was running Jaunty because it seemed to be interfering with the X-fi. I was hoping that there was a switch or a choice in Ubuntu itself somewhere to make it ignore the X-fi. Otherwise, I will just rip it out I think and then make friends with eBay.

---

### Post by Jaesin on 2009-12-13
As long as you have your onboard audio turned off, you will not be able to use it.  If you enable it in your bios, then you should see it when you right click on the volume control.  Then just select preferences then click Hardware then select your onboard device for everything and that should work.

Make sure that you don't select digital unless you are running a digital output system.  Most people run analog.

---

### Post by Man with Hat on 2009-12-13
Cheers for the reply. The onboard is enabled in bios and is available as a choice along with the x-fi, however it is Karmic that chooses the x-fi without my consent. I was hoping that I could tell it not to somehow. I no longer have the volume control either in the system tray nor in system>preferences>sound as I'm pretty sure that is part of the pulseaudio which I have removed in order to install the OSS4 drivers. Instead there is a mixer that I use called ossxmixer. It is in here that I can see both of the sound cards and their functionality.

---

### Post by Man with Hat on 2009-12-18
Just wondering if you have anymore help out there. I have now ripped the X-fi out of my computer and have the speakers plugged into the onboard audio (AC-97). I am running OSS4 drivers and I still have no sound. I am thinking that something from Freedoom has caused this. As I seem to have this problem after I run the game a few times. I might start a new thread suggesting this and see if a freedoom person helps out. Anyway, any other help would be much appreciated!!!!!!!!

---

### Post by Ubuntaqua on 2009-12-18
Althought they are deprecaterd in Karmic, the old pulseaudio applications still work in karmic. pavucontrol and padevchooser may help you with multiple sound cards.

---

### Post by Man with Hat on 2009-12-18
Thanks mate, I may give them a go. At the moment I have just removed the sound card from the slot because I hate its guts. Maybe when we get some relationship counselling or something I'll put it back in there and try again. At the moment, I seem to have my onboard sound working, but only in games!?!?! Either I really don't understand linux, or linux hates me having sound

---

### Post by Man with Hat on 2010-01-04
Now its just behaving strange again (don't know if I'm just talking to myself). I have Ubuntu sounds and sounds in games. I can't get any noise in videos or mp3s or flash/shockwave. That is unless I switch to a guest account, all sound works in there, with the exception of flash/shockwave (I'm not convinced these are ever going to work properly on mine - or from reading other threads, other people's - systems). Upgrading to Karmic a little while back seemed to temp fix many things. Is there a way I can re-install, or do I have to download and do a complete install again?

---

