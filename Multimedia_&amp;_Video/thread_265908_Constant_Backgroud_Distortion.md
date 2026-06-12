---
title: "Constant Backgroud Distortion"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by Bakedbean on 2006-09-26
Hello Everyone,

Forgive me if this issue has previously been addressed but I have 'googled' countless times and read more help files than I care to count and still haven't found a solution. Also, please forgive my ignorance regarding Linux and it's functionality - I am quite the novice when it comes to any Linux distribution (so it would be greatly appreciated if any solution would be written in clear and concise steps).

My problem is that I have a constant background noise or feedback coming from my speakers and headphones alike. This noise is quite similar to a faint hiss. This 'hiss' gets louder with an increase in master volume and also when the PCM slider is moved upward. I've tried multiple settings and slider configurations in KMix but to no avail, the hiss persists. If I decrease the PCM and master volume slider and can reduce the background noise to a softer 'hiss' but consequently all sounds that are played are barely audible.

This background noise also becomes very pronounced when playing games; both those native and foreign to Linux. In-game, I experiences faint pops as well as slightly louder feedback. Also, when I minimise and maximise windows I can hear a sound slightly louder than the background distortion, a sound very similar to the angry sneeze that rhinoceros beetles make when you try to pick them up - except not as loud. Similarly, I hear less than pleasant sounds when using scrollbars, moving them invokes a distorted (faint) background crackle. It's almost like every time the computer has to 'think' it punishes me with annoying feedback.

My headphones and speakers perform marvellously on my laptop running Windows XP and my PC had no sound troubles when it was Windows XP – it seems that this sound distortion is exclusive to Linux. As well as Ubuntu, I have tried Fedora Core 5. Unfortunately Fedora Core 5 produced the same the same sound difficulties.

The details about my sound:

```
Card: Nvidia CK8S
Chip: Realtek ALC655 rev 0
```

I've seen in a few forums and help files that the output of 'aplay -l' has come in handy, here it is:

```
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So, is there a solution to this? Can I reduce the volume of this background noise without reducing volume of all me songs and games – or even better, can I eliminate this background distortion altogether? Any input that anyone can give me would be greatly appreciated.

Thank you for your time,
Bakedbean

---

### Post by Kateikyoushi on 2006-09-26
You wrote the noise became louder when you play games, minimise maximise windows and move the scrollbars. What I find common in these that the power draw of your system is higher than normally so seems to me somewhere you pick up noise from the power rails. :-k 
I had that problem with onboard sound of my A64 mobo 2 years ago.

Did you try to change alsamixer settings ? I would start with the Mic.

---

### Post by pseudonym on 2006-09-26
Have you got digital speakers? If so, I recommend running everything through your IEC958 output. Also, assuming you use the default alsa sound driver, you should create an ~/.asoundrc file for optimal performance. Directions on how to do so are available at [http://www.alsa-project.org/](http://www.alsa-project.org/) . Just search your sound card and the instructions will come up in the result.

For what it's worth, here's one for my nvidia onboard sound -

```
pcm.nforce-hw {
    type hw
    card 0
}
pcm.!default {
    type plug
    slave.pcm "nforce"
}
pcm.nforce {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:0,2"
        period_time 0
        period_size 1024
        buffer_size 32768
        rate 48000
    }
}
ctl.nforce-hw {
    type hw
    card 0
}
```

You'll notice I specified device "hw:0,2" . That says to direct all sound to the digital out.

---

### Post by Bakedbean on 2006-09-26
Hello,

Thank you all for you contributions, unfortunately I still have the background distortion.

Kateikyoushi,

> Did you try to change alsamixer settings ? I would start with the Mic.

I've tried many different settings and played with sliders countless times. I've also ensured that the microphone input and output is muted.

pseudonym,

> Have you got digital speakers? If so, I recommend running everything through your IEC958 output. Also, assuming you use the default alsa sound driver, you should create an ~/.asoundrc file for optimal performance. Directions on how to do so are available at [http://www.alsa-project.org/](http://www.alsa-project.org/) . Just search your sound card and the instructions will come up in the result.

I'm pretty sure that I'm not running digital speakers. Even so, I decided to run everything through my IEC958 output. I'm not entirely how to run everything through my IEC958 output though, but I tried nonetheless. I KMix, there was a drop-down menu titled 'IEC958', I made sure that the option I selected for that menu was 'IEC958'. I'm not sure if that's what you meant for me to do but it didn't solve my problem anyway.

I also created and configured a '~/.asoundrc' file according to [http://www.alsa-project.org/]("http://www.alsa-project.org/") but that didn't have any effect on the background distortion of mine. I even tried your configuration too, but that didn't change anything either.

Nevertheless I appreciate the help you offer.

Thank you all,
Bakedbean

---

### Post by Bakedbean on 2006-09-27
Bump.

Anyone have any clue as to how to solve this distortion issue?

Bakedbean

---

### Post by pseudonym on 2006-09-27
[QUOTE=Bakedbean]I'm pretty sure that I'm not running digital speakers. Even so, I decided to run everything through my IEC958 output. I'm not entirely how to run everything through my IEC958 output though, but I tried nonetheless. I KMix, there was a drop-down menu titled 'IEC958', I made sure that the option I selected for that menu was 'IEC958'. I'm not sure if that's what you meant for me to do but it didn't solve my problem anyway.[/QUOTE]

You won't get anything out of the digital IEC958 output if the proper speakers aren't connected to the special jack at the rear of your machine. And if you don't have speakers which use a digital connection, then this will definitely not work.

One other thing which could be causing your problem is some kind of interference inside your machine. Some TV cards can produce this. Have you added anything like that since you installed linux?

---

### Post by Bakedbean on 2006-09-27
> You won't get anything out of the digital IEC958 output if the proper speakers aren't connected to the special jack at the rear of your machine. And if you don't have speakers which use a digital connection, then this will definitely not work.

I reverted configuration to its original state and made sure that the speakers are plugged into the correct port but I'm still getting that background hum through my speakers *and* my headphones.

> One other thing which could be causing your problem is some kind of interference inside your machine. Some TV cards can produce this. Have you added anything like that since you installed linux?

Nope. My computer is using the exact same hardware it was when I had it running on Windows XP. I took off the computer case to see if it was physical interference that was causing the distortion but everything is as it should be inside my computer. Everything is in place and nothing harmful is touching any of the components. The jacks/ports themselves wouldn't be the problem, would they? Could they be fried or slightly broken?

---

### Post by pseudonym on 2006-09-27
> **Bakedbean said:**
> The jacks/ports themselves wouldn't be the problem, would they? Could they be fried or slightly broken? That is a possibility. It happened to me once on an old soundblaster, and I only realised it was that after many hours of walking up blind alleys before fiddling with the jacks and noticing that's where the problem lay. Definitely investigate that.

Sometimes sound chips do go faulty, too. And onboard audio of any kind is a known candidate for it. But one other thing to try and test is to boot up a live cd (Ubuntu, KNoppix, any one will do), set up your audio, and see if the problem is still there.

---

### Post by Bakedbean on 2006-09-27
pseudonym,

Your help on this matter has been invaluable, thank you very much for all your input. I'm currently downloading the Knoppix live-CD (DVD) and will post the outcome when I get a chance. Unfortunately, I might be a while in posting my results due to slow Optusnet DSL and a terrible modem. If all else fails I shall investigate the possibilities of ruined ports and a dud onboard sound device - perhaps I will invest in an independent sound card.

In the mean time, any thoughts and opinions that anyone at all can offer would be greatly appreciated.

Thank you,
Bakedbean

---

### Post by Bakedbean on 2006-09-29
Sorry about the delayed response but I haven't had a chance to post. I did as recommended and tried testing and altering sound via live CD but that did not seem to help. Has anyone else ever had this problem or have any other solutions?

---

### Post by dilb on 2006-09-30
Bakedbean,

I had exactly the same problem with a SoundBlaster Audigy 2 card, and while I don't think I will be able to directly solve your problem, I think I may be able to point you in the right direction.

The problem I had was that I seemed to have two 'sets' of volumes turned up to maximum in the volume control (I have an onboard sound card as well, but I'm not sure if that's the cause) and this seemed to produce huge amounts of hiss, as the volume was effectively doubled. But, different programmes seemed to use different volume controls, rather than both at the same time, which is why the sound wasn't amplified accordingly. I only stumbled across this by turning down the channel called 'front' and 'rear' without changing the master volume, and found this affected programmes like Rythymbox, but didn't affect DVDs in totem-Xine!

So, it might be worth investigating if you have this same conflict and see if it resolves things for you. I basically tested it by running music from rythymbox and a DVD with totem-xine (set to 4.1 audio output in the preferences), and muting/unmuting each setting and seeing what happened. In my case turning down (but not muting) front and rear got rid of the hiss, without turning down the volume on DVDs so I could still hear them. I was then free to crank the master volume right up to listen to music without hiss either. I'm sure there's a better way to acheive this, but it seems to work.

Sorry that's not a very scientific answer, but I hope it helps.

D

---

### Post by Goronok on 2006-11-30
I am having this EXACT same problem with Edgy,  with the exact same audio chipset (realtek AC97 ALC655) Has anyone else seen this problem, or know of a possible fix?   Ive checked everything in the sound options, unmuted and muted everything I know of to try and fix this.  If you leave the volume very low, the sound is fine, but as soon as you turn it up at all,  the sound gets VERY garbled.   

I'm very impressed with Ubuntu,  but ive never had this problem with Fedora/Mandriva.   

Any thoughts?

---

### Post by x64Jimbo on 2007-02-23
Same issue. Loud hissing coming from speakers. When plugged into other audio source they're fine, so it's not the speakers. When booted from LiveCD, the problem is also not there. Any ideas?

---

