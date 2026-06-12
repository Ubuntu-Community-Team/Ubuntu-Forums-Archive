---
title: "[SOLVED] sound recording clip problem"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by gregbryant on 2007-11-20
I just encountered a new problem with hard-clipping (total square-wave distortion) when I try to record above about .35 on the vertical scale. For the record, the same problem happens both in audacity and in ardour. I just recently upgraded to the Gopher and that's about when it happened. here is a screenshot of the problem:
[IMG]http://www.robinsonkansas.org/recording_clip.png[/IMG]
Of course I can be careful to keep my input levels below .35 and amplify them later, but that's less than desirable.
     My sound card is an SB Live 5.1. It doesn't make any difference whether I choose ALSA for my input device in the mixer and in audacity's preferences, or OSS in both.
     Also, I can load recordings I made before the upgrade and the levels are fine, and play back fine.
     On the mic monitor, the input levels look healthy as always.  They just hard clip at .35 in the actual recording track and make a voice sound like a needle dragged sideways across an LP.
     It just seems like the gopher might be the problem. Can anyone suggest anything that might fix this?

---

### Post by deadgobby on 2007-11-20
Check input device recorder. It may that it is on mic or phono. Check to see if it is set to line in. If on Mic or Phono. It may be the cause distortion. Other than that. It a bug in the testing version of Ubuntu. Then do the testing team a favor and post the bug.

---

### Post by gregbryant on 2007-11-20
Okay, I should have mentioned that. It's set to line in. I'm using a preamp. But the same thing happens if I just plug the mic into the card directly and select the mic input. And I can reduce levels and make clean recordings... it's just that they're sort of low level. It's like buimping my head on the ceiling, so I stay stooped over.
I'll post the bug.

---

### Post by deadgobby on 2007-11-20
Do not use a pre amp for line in or mic/phono. No need for that if you have the correct input settings to record sound.   Other than that I think it may be user error. Check your ALSA mixer settings, check your volume going to the input of line in and mic in. All so check your ou put sound too. If you have your speakers or head phones set to 11. 
Gobby

---

### Post by gregbryant on 2007-11-21
I needed the preamp to get a dynamic mic up to line level, but for the following test I plugged the mic directly into the mic input on the card. I never use a preamp there, of course. I am always ready to believe user error, but in this case I think I've covered a lot of the bases you're referring to. These attachments are screenshots of the mixer settings and the track I recorded for this test:

[ATTACH]50933[/ATTACH]

[ATTACH]50934[/ATTACH]

[ATTACH]50935[/ATTACH]

[ATTACH]50936[/ATTACH]

The output sound (speakers/headphones volume) doesn't affect the distortion, which is a result of square-wave distortion in the track, not overdriving the output amp or speakers.

I tried the same test with the capture set lower, the mic level set lower, just every possible combination. It comes to this: I can record clearly as long as the amplitude on the recorded track does not exceed about .35.

---

### Post by deadgobby on 2007-11-21
Do you get distortion using a sine wave? Are you using the on board sound or a sound card? 
 
Gobby

---

### Post by gregbryant on 2007-11-23
> **deadgobby said:**
> Do you get distortion using a sine wave? Are you using the on board sound or a sound card?
A good question! I hadn't thought of that. So I had audacity generate a 440 sine wave at the default amplitude of .8. presumably this bypasses the sound card and driver and creates the tone digitally. And there's no distortion. I zoomed in so you could see it:

[ATTACH]51191[/ATTACH]

And I'm using an SB Live! 5.1 sound card. There's a card on the motherboard but we couldn't get it to work back in the gentoo days so we disabled it in the BIOS.

Greg

---

### Post by gregbryant on 2007-12-01
Okay, it was user error -- in a way. Apparently you have to get the AC97 slider to display in the mixer and slide it all the way up. I'd never heard of it and didn't know what it meant, but apparently the mixer ships -- or ubuntu ships -- with the slider turned partway down. This limits the output of the audio codec (AC) so that if you try to turn the input up to get enough volume, all you get is more square waves.
     I'm guessing people who have trouble with extremely low levels may also find this is the solution. bring up the mixer, go to Edit / Preferences, and make sure to check AC97. Turn it all the way up. Then set your inputs to get the levels you want.
     Sure worked for me. I found this solution on [THIS PAGE]("http://www.hydrogenaudio.org/forums/index.php?showtopic=46365") in the Hydrogen Audio forum.

---

