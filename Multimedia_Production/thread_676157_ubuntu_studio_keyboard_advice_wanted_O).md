---
title: "ubuntu studio keyboard advice wanted :O)"
date: 2008-01-23
forum: Multimedia Production
---

### Post by daveoily on 2008-01-23
I've got ubuntu studio running on a computer I wanted to use to learn about multimedia production type stuff in the linux world, I have to say, i'm very impressed so far, so impressed in fact that I want to learn some musical production stuff.

now i thought I'd better get a keyboard for this type of thing, so, what works well with ubuntu studio? are there keyboards that dont work well yet that i should avoid?

what's the cheapest keyboard I can get that will do a good job?

advice is greatly appreciated

---

### Post by jondecker76 on 2008-01-24
I have an M-Audio Keystation 49e and it does all I need it to do. Its relatively inexpensive as well. They make larger full size versions. Works right out of the box (most midi instruments should)

Also, remember there is a "Virtual Keyboard" application available that displays a keyboard on the screen and you can click the keys - you can compose midi with this as well with zero cost involved and its a good and free way to get your feet wet

---

### Post by daveoily on 2008-01-24
thanks for the info, i think getting a keyboard is kinda necessary, i mean, point and click could never produce a chord could it?

---

### Post by jondecker76 on 2008-01-24
Another nice thing about the M-Audio keystation keyboards is that it has both MIDI and USB interfaces (both which work out of the box)..

Yes, a real keyboard is nice, but most midi is made single note at a time, so you really can use a virtual keyboard to produce about anything (just not live music). Chords you can do one note of the chord at a time.

Definitely don't let not having a keyboard stop you from making music, But you are right, it is nice having the physical instrument.

---

### Post by daveoily on 2008-03-04
ok, I got a keyboard, took a while to get here, but i now have one...

thing is, i can't seem to get a peep out of it, and i know it'll just be because i don't know what i'm doing, or i'm using the wrong program or something, but i 'm  total noob at this so please bear with me...

my main aim is to learn keyboards using ubuntu studio and any info i can find on the web. I had the obligatory play with any of the software i thought might do the job, to see if i could get it to do any noises, but to no avail :(

alsa seems to have picked up my keyboard, the keystation 49e as advised :), now as far as i'm aware, i need to supply the keyboard with an instrument to play, how do i do this using ubuntu studio please?

pressing keys and getting no music is a little on the dull side...

---

### Post by jondecker76 on 2008-03-04
Ok, lets get your keyboard making some sound...

First, open up qJack Control (Sound and Video -> Audio Production ->Jack Control)
Hit the "Start" button on qJack Control when it pops up. This will start your Jack server (If you get any errors, look around for instructions on how to set Jack up for your hardware. Sometimes nothing needs done at all, sometimes its easy, sometimes its a pain).

Now open up ZynAddSubFX (Sound and Video -> Audio Production -> ZynAddSubFx Software Synthesizer).

Make sure your keyboard is plugged in, and the switch is  On in the back.

Now use qJack Control to link your keyboard to ZynAddSubFX (as if it were a virtual midi cord)
To do this, on the qJack Control window, hit the button in the lower-left corner that says "Connect". You will see a connections window appear. On the top, select the "MIDI" Tab. In the left side, you should see your USB Keystation 29e. Select it.
Now on th left side, you should see ZynAddSubFX. Select that as well. Once you have both sides selected, a "Connect" button on the bottom of the Connections window will highlight. Click on it to connect the two pieces of equiptment.

That should be it! You should have sound now. As for ZynAddSubFX - Select Instrument -> Show Instrument Bank, then select from the many presets to find the sound you like.

---

### Post by daveoily on 2008-03-04
yay! I have sounds coming out, hours of fun to be had!

thank you so much jondecker76!

 I was almost there with my guesswork, i had jack open, but obviously wasn't guessing quite luckily enough at the time :)

i'll remember to thank you when i'm a famous musician\\:D/

now all I have to do is go and learn some music :)

---

