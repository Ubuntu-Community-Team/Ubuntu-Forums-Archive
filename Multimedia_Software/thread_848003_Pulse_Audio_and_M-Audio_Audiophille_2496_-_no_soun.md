---
title: "Pulse Audio and M-Audio Audiophille 2496 - no sound!"
date: 2008-07-03
forum: Multimedia Software
---

### Post by blackcoatman on 2008-07-03
Hello people

I haven't managed to get my Audiophille 2496 working properly with Pulse Audio in Hardy. It seems the sound card is working (i get no errors), but I have no output, no matter what I select or deselect in Pulse Audio manager etc. I have to switch to Alsa to get it working ok. but this produces some other problems with some applications (for example, Audacity becomes extremely slow).

I would really appreciate any help from someone who got the 2496 working OK on Pulse Audio, since the rest of the information i've found around didn't help much. :(

---

### Post by okivonish on 2008-08-24
I have an error message regarding my 2496 too: 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument

What is the problem, and how do i solve it? I don't know that much about code stuff. And I'm very new to Ubuntu, just installed it and am trying to get it running smoothly.

---

### Post by musicinmybrain on 2008-12-21
> **okivonish said:**
> I have an error message regarding my 2496 too: 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument

What is the problem, and how do i solve it? I don't know that much about code stuff. And I'm very new to Ubuntu, just installed it and am trying to get it running smoothly.

I have this problem too, and I'm not new to Ubuntu; I've been using it since Hoary Hedgehog. I'm ticked off... sound is the one thing that is completely nonnegotiable for me.

This is on a fresh install with all old sound configuration files deleted from my home directory. Right now I'm trying removing PulseAudio and replacing it with, say, ALSA. Maybe that will keep me from having to switch to another distribution. Seriously, though... this card has worked on Linux for *years*, and it's one of the major cards people use with Ubuntu Studio. It darn well ought to work.

---

### Post by markbuntu on 2008-12-21
For some unfathomable reason, many critical packages necessary for getting sound working properly were left out of the Hardy and Intrepid desktop seed. I have writted a guide here for fixing that

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you are using UbuntuStudio there is more extensive help for you here for getting jack and pulseaudio working together properly.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

There is really no need to remove pulseaudio.

---

### Post by musicinmybrain on 2008-12-22
Hmm, maybe. Although you say, "If you have just upgraded to or installed Intrepid and you have some sound somewhere, but not everywhere for everything, this is a fast way to get all the missing stuff you need and give you some tools to figure out what is going on," and I didn't have any sound anywhere I tried. In fact, usually I had one of various error messages, as okivonish described.

Anyway, switching back to ALSA did work for me for now, and I don't presently feel like rebreaking my audio. Perhaps someone else with the same card and problem can indicate whether your method works for them. I hope so! Thanks for the suggestion.

---

### Post by Nic Robinson on 2008-12-31
I have just the same problem.  No sound at all.  I've followed Mark's excellent guide (thanks Mark) and I'm sure that with pulse working it will be a fabulous system.

System/Preferences/Sound can see the MAudio 2496 and I've set all according to Mark's guide.  However in the Pulse Volume Control the only device shown is "ALSA PCM on front:0 (ALC883 Analog) via DMA"

I assume this is the on board sound card?  There doesn't seem to be a way to get Pulse to check for other connected sound cards.

Any help would be appreciated.  Upgrading Ubuntu always seems to throw up sound problems!

Cheers,

Nic.

{EDIT - I've connected ob board sound to the speakers and it's working.  Now all I need is to get the 2496 in the picture.  Help!}

---

### Post by Nic Robinson on 2008-12-31
Well here's an update...

I've had a frustrating few hours with this.  First of all I followed Mark's guide above and installed all the remaining relevant software, checked user access, set up Pulse etc.  Sadly nothing.  Pulse simply said it could see the onboard card but not the MAudio 2496.  Plugging the onboard sound up to the hifi confirmed this.

I've tried the following (bear in mind I'm not too Ubuntu savvy to say the least;)).

1. Followed rickard's advice [here]("http://ubuntuforums.org/showthread.php?t=302698") on ordering preference for soundcards.  Still nothing from the M Audio and the computer resolutely continued to play music out of the onboard even though it showed the MAudio at "0".  I even set the onboard to "-2" same result.
2. Killed the onboard sound in BIOS.  Now the machine was silent on all fronts.
3. Checked and re-checked the Pulse settings and Sound settings (in System/Preferences).  I tried lots of combinations and re-booted endlessly to no avail.
4. Finally in desperation I removed all the Pulse elements from the machine.  Hey Presto - it works perfectly!  

Just using Alsa now.  Still, thanks to Intrepid/Mark I can now listen to Internet radio which I couldn't before, plus audio cd and DVD.

I'd like to think I could go back to Pulse which looks a super system but this is how I got things to work for me.

Cheers,

Nic.

---

### Post by ratdog on 2008-12-31
hello,
I was having the same problem and just got it fixed yesterday with help from this post: [http://ubuntuforums.org/showpost.php?p=6449370&postcount=989](http://ubuntuforums.org/showpost.php?p=6449370&postcount=989)
good luck!

---

### Post by markbuntu on 2008-12-31
I have added a link to that post in the 10,000 page guide. One more hardware problem fixed...

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Thanks again,
Mark

---

### Post by Nic Robinson on 2008-12-31
I'll give that a try tomorrow.

Happy New Year,

Nic.

---

