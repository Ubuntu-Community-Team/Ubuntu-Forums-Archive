---
title: "New card. Or try Pulse. That is the question..."
date: 2008-07-12
forum: Multimedia Software
---

### Post by Roasted on 2008-07-12
Running an onboard realteak audio card. It aint bad, but I have to keep my PCM at 75% or lower. Anything higher and I can hear some static on certain high notes. 

What would be more likely to work? A 30 dollar PCI sound card, or to give pulse audio a shot? I've looked at some tutorials of pulse audio and it just makes me want to eat nails instead of tackling yet. Yet, I have car inspection due this month, so I'm on the fence either way.

But nonetheless, what would be more likely to help? 

New sound card, keep alsa?
Keep onboard realtek, try pulse?

Of the sound cards, I'm looking at:

Turtle Beach Riviera
Diamond Multimedia XtremeSound xs71
SoundBlaster Audigy SE

---

### Post by kostkon on 2008-07-13
> **Roasted said:**
> Running an onboard realteak audio card. It aint bad, but I have to keep my PCM at 75% or lower. Anything higher and I can hear some static on certain high notes. 

What would be more likely to work? A 30 dollar PCI sound card, or to give pulse audio a shot? I've looked at some tutorials of pulse audio and it just makes me want to eat nails instead of tackling yet. Yet, I have car inspection due this month, so I'm on the fence either way.

But nonetheless, what would be more likely to help? 

New sound card, keep alsa?
Keep onboard realtek, try pulse?

Of the sound cards, I'm looking at:

Turtle Beach Riviera
Diamond Multimedia XtremeSound xs71
SoundBlaster Audigy SE
I would recommend you to try PulseAudio first. Follow this [how-to]("http://ubuntuforums.org/showthread.php?t=789578"). I believe it's simple enough and it allows you to easily restore your previous configuration any time you want.

You can skip Part D, it's not necessary.

I believe 90% or more of your applications will work fine right away with PulseAudio. Thus, you may need to configure some to make them to work with it.

If you decide to follow the PulseAudio road and you have problems don't hesitate to ask here for help.

---

### Post by Roasted on 2008-07-13
Hm. I just tried PulseAudio.

It gave me identical results ALSA did.

I have to wonder, if Pulse is meant to be the default sound format in Hardy, why in the world is it so hard to set up? Why is there a bunch of random strings of commands? I figure if it's a standard, it'd be like... an apt-get package or something...

---

### Post by Roasted on 2008-07-14
Another thought that I just can't get out of my head... everybody shreeks that, ooo yay pulse audio can play audio streams from multiple sources at once!

I'm not at home to test this, but I don't know how many times I had to pause audacious or vlc with a video or mp3 I was playing in order to watch a video on youtube. The reason I had to pause it was because I don't want to listen to 2 things at once. I have used ALSA since the beginning of time.

So, do I dare ask, am I an oddball, or what?

And I just have to know, does Pulse typically result in better sound quality and/or louder volume levels? Or am I just wasting my time?

---

### Post by markbuntu on 2008-07-14
Pulse will not improve your sound quality. It sits on top of alsa. However, with some sound cards you are able to set the volume for individual streams at more than %100 in the Pulseaudio Manager.
Here's how.

Open the Pulse Audio Manager, go to devices. the application playing will be listed as 

#something, 

highlight it and click properties. A new window will pop up. At the bottomn of the info is a volume slider usually set at 100% (0.00db). You can drag it to the right for more volume.

This is a handy way to equalize the volume of different players and you can avoid maxing the pcm volume in the mixer.

Sometimes I like to stream the same station through 2 different players. Like using streeamtuner with xmms and tunapie with rythmbox. The difference in the eq and the slight time delay make for a very interesting sound that I enjoy with some music.

---

### Post by Roasted on 2008-07-16
Just some thoughts to throw out here...

I'm running Alsa and my onboard card still. Things seem to be where I want them, now. I thought about Pulse more, but I really don't need the added features it offers. Alsa does what I need already, so I'll just roll with that for the time being.

Now, I have some questions about PCM levels and such. I kept thinking, oh man, Audacious' volume level is so low, even when maxed, blah blah... I compared Audacious to Amarok and I noticed something.

Amarok and VLC act very similarly in terms of how it reacts to PCM level. If PCM on Amarok or VLC is really high, these applications tend to result in distorted sound. However, by default, their volume level seems higher.

Audacious, on the other hand, can handle MUCH higher PCM levels while retaining clarity, yet, the volume level is lower than that of VLC or Amarok.

So, Audacious (lower volume) + High PCM as well as Amarok (higher volume) + lower PCM... pretty much even each other out.

But, hey, one question I do have that I would loooooove to be answered is this.

When you go to terminal and hit alsamixer, you can see the exact levels of your PCM level... at the top where db gain is listed.

When it says db gain = 0.00, does that mean that I should have perfectly clear audio without any additional "power boost" that PCM offers? So, by the book, and logically speaking, you'd think that anything higher than 0.00 db gain would result in a potentially clipped signal. Correct?

I used to be in car audio heavily, so I understand clipped signals and high "gain" levels that are often the result of clipping. But when I see that string of numbers there that says db gain = 0.00, I have to wonder if that means that there is no additional power being pushed beyond its limits.

Make sense? It's kind of hard to explain... I hope somebody gets my drift and has an answer... :guitar:

---

### Post by markbuntu on 2008-07-16
Well. as far as I can determine, various apps have various default volume levels so really 0.0db in the volume control is kind of meaningless, especially if you can go above that without distortion.

When I was into analog recording we could often run +3 to +6db peaks without clipping or distortion. It all depended on the quality of the equipment, good stuff had the headroom, cheap stuff did not.

---

### Post by Roasted on 2008-07-16
Yeah, I sense distortion with some songs at 90%, and others are clear up to 100%. However, I leave it at 0.0db gain, which is listed as 74... 

It's still plenty loud, and if I'm listening to a clean song that can get that extra oomph and not distort, I know it's there. But for the time being, it works fine as it is. 

I assume when you talk about the equipment, you're talking about a sound card in relation to my question. I'm betting if I upgraded the sound card I could peak at 100% with little-to-no distortion.

But, ah, when I want to blow windows out, I'll consider it.

---

### Post by markbuntu on 2008-07-17
Just get a good external amp and some really good speakers. I run my computer sound through my stereo, no need to turn anything up all the way. I basically use Pulse Audio Manager to equalize the volume of the various apps I run so I don't have to keep reaching for the remote to adjust the volume on my stereo.

---

### Post by Roasted on 2008-07-18
I let my stereo at 30/50 on volume, and just use the system volume to control the volume level I want. :guitar:

---

### Post by Roasted on 2008-07-26
Throwing this idea out there again, since I just got paid and want to spend my money on something technologically beneficial to me.

Would adding a 30 dollar PCI sound card to my system offer better sound quality and/or sound volume levels while still using Alsa?

---

### Post by markbuntu on 2008-08-02
I just got a SIIG Soundwave 7.1 PCI card and it is a definite improvement over my AC97 on board. Its does 96khz playback and up to 7.1 surround sound and spdif in/out. Only 16bit/48khz recording though. 

But it was only $40 and it works OOB!!!
No drivers to download, no dicking around in the file system.

---

### Post by Roasted on 2008-08-03
Have you tried rebooting several times?

That card only worked for me about 50% of the time. Sometimes I'd reboot and it'd kick on, other times it wouldn't and I'd have no sound unless I reboot again. 

I returned it, and I'm expecting a Turtle Beach Montego on monday. :)

---

### Post by markbuntu on 2008-08-04
I have had no problems at all with the card and have rebooted about a zillion times this week fixing my mutiple install/multiple grub issues. 

I just got UbuntuStudio and the midi part of the card works pretty good with jack and hydrogen so far, can get rid of the dread xruns which my on board AC'97 could not do no matter what I tried.

I can tell pulseaudio to use my on board sound card with my headphones plugged in and jack to use the SIIG card with my speakers and they both work at the same time! Something completely unexpected and a total surprise.

---

### Post by Roasted on 2008-08-04
Man. That's weird. I had completely random issues with that card.

Ironically, I have some issues with the Turtle Beach Montego I just got that I've heard from nearly ALL resources is 100% supported out of box.

Somehow, my max volume is lower than my onboard card... yet PCM and master volume are maxed. Blahhhh...

Fresh install. Same problems.

insertguninmouth

AHH!

---

### Post by markbuntu on 2008-08-05
Sometimes PCI cards will act whacky if they are not in the right slot which you can never tell except by moving them around. My card is in the very last slot, which was the only one left on my mobo.

---

### Post by Bucky Ball on 2008-08-05
> +3 to +6db peaks without clipping or distortion. It all depended on the quality of the equipment, good stuff had the headroom, cheap stuff did not.


Without getting too technical, that just about says it. 0.00 is a dead cert clarity though, and if it is not clear sound when playing there, something is wrong with your listening hardware, not the software I would say.

---

### Post by Bucky Ball on 2008-08-05
> Somehow, my max volume is lower than my onboard card... yet PCM and master volume are maxed.

Roasted, sounds silly perhaps, but is there a seperate GUI for the card itself? Any driver which has a seperate control for the card?

---

### Post by Roasted on 2008-08-05
I don't know why I didn't think of this before... but I had Ubuntu 64 bit installed. I guess Alsa's support in 64 bit with this particular chipset just wasn't completely there yet.

I installed 32 bit, and the card works beautifully. :guitar:

---

### Post by Bucky Ball on 2008-08-06
Great news! :)

I like it when a plan comes together and well pegged ... ;p

Just contemplating my audio workstation which I haven't used for awhile, dual booting nicely with XP and UStudio Gutsy. I have the Hardy UStudio install disk ready, but can I find the time right now??? So many other things I should be doing, I know, but ... lol. What makes it worse is I have three drives in there and another to add. The permutations! Hours of fun in the planning.

Has me a bit stumped though why alsa is not working with onboard sound, nothing exotic. (?) I am using alsa right now on my HP laptop (64 bit) no problem. Unless you have something unusual in there it is odd. Have you done a search for your particular card and Ubuntu? Or is that a silly question?? You may be just unlucky with the card, as you say.

You may find the section entitled "Testing the Soundcard with 64 Bit Hardy Heron" on the page below of some interest;

[http://linux.eaton.net.nz/](http://linux.eaton.net.nz/)

Have fun and I guess your problem is solved kinda ...

---

### Post by Bucky Ball on 2008-08-06
Why do the forums keep doing this? I get an error and my post doesn't go up, so I re-write and post and there is my previous post? sorry everyone ... refer my last post! ;p

---

### Post by Megatog615 on 2008-08-06
Keep in mind most high-dollar sound cards have a lower pre-amp volume because you get a better sound quality that way through speakers(sound isn't being overdriven).

---

### Post by Roasted on 2008-08-06
I noticed with my onboard sound card by Realtek, anything beyond 75% PCM would start to distort. I noticed in alsamixer in the setting that the dbgain of 75% PCM was 0.00... and if I went above, it added db to it. I guess it's some sort of artificial "dirty power" to exceed the existing limit.

Whereas... My Turtle Beach Montego I just threw in, 100% PCM is 0.00 dbgain... and 100% PCM and 100% system volume yield NOOOOOOOOO distortion whatsoever through the speakers.

I'm tellin ya's, when McCready hits that high noted solo of "Black", it just rocks my ears... Pearl Jam fans will know what I'm talkin about. :guitar:

---

### Post by Bucky Ball on 2008-08-06
Rockin' Roasted!

You may find this page interesting;

[http://www.phys.unsw.edu.au/jw/dB.html](http://www.phys.unsw.edu.au/jw/dB.html)

You will find that adding 3db is not as straightforward as it might seem as the calculation shows that 3db is in fact not adding 1,2,3 but something very different! Adding 3db is not adding 3% more volume ... thus, 0.00 is what you would be aiming for (if your original source signal is low, adding 3db (to get it to 0db effectively) is not a problem - if your original source is sitting at 0db already, you are effectively blowing out the source ... ). :)

Although rather technical, this page is the bomb as far as understanding how it all works;

[http://www.avatar.com.au/courses/PPofM/](http://www.avatar.com.au/courses/PPofM/)

Have fun but don't kill your ears, they are very delicate! (smallest bone in the body is in there, and when you think about it, unbelievable what it can take - apparently one of the most robust bones also).

---

### Post by markbuntu on 2008-08-07
db is not linear, it is logarythmic. 3db is double, 10db is ten times.

---

### Post by Bucky Ball on 2008-08-08
> **markbuntu said:**
> db is not linear, it is logarythmic. 3db is double, 10db is ten times.

[http://www.avatar.com.au/courses/PPofM/intensity/Intensity3.html](http://www.avatar.com.au/courses/PPofM/intensity/Intensity3.html)

---

