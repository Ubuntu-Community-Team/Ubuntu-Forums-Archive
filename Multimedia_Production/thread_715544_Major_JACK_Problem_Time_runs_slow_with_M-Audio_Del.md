---
title: "Major JACK Problem: Time runs slow with M-Audio Delta1010"
date: 2008-03-05
forum: Multimedia Production
---

### Post by dbsoundman on 2008-03-05
I'm running Ubuntu Studio 7.04 with an M-Audio Delta1010 installed. Aside from the fact that the hw id for the delta changes just about every time I boot (which is annoying), I have also noticed something really weird and annoying: when jack (through qjackctl) is running and connected to the Delta, the timecode runs at half speed consistently; meaning that every two seconds of real time, the timecode advances by one second. This is a major problem when I record, because it means all my tracks play at 2x speed when I export them. Curiously enough, this happens ONLY when I connect to the Delta; if I connect to the internal soundcard, all is well. I have not tried reinstalling jack and all that yet, but I probably will soon when I have more time. What can I do to fix this? Is this a known issue?

Thanks,
Dan

---

### Post by Stochastic on 2008-03-05
First, I have NO idea what the root of your troubles are, but I can make some deductions/guesses that might help.  It sounds like it's an issue with the install or config of your Delta card (your alsa files) that's the root of the troubles because of the changing address and jack's normal behavior with the other soundcard.

now for some questions you may try to answer for yourself:
Can you try switching the card into a different PCI slot and possibly looking over your alsa config files?  In System->Preferences->Sound are you able to see the Delta card?  If so, can you try using it for your Ubuntu sounds and see if there's any errors/issues?  If you use Audacity without jack running (using alsa in the preferences) do you still have issues recording?

---

### Post by dbsoundman on 2008-03-05
I do know that I did put the Delta card in a different PCI slot when I installed my new video card, because the way my motherboard is, all the cards go in upside down, so I put the delta card in the second PCI slot so that it wasn't right up agianst the heatsink on the video card. I just did a quick check and I can see the delta card in the sound preferences menu, but I will have to do a little more setup to try it out for my PC sounds, I'll get to that later. I'll also check out Audacity...

-Dan

---

### Post by tgalati4 on 2008-03-05
If the delta card is running at 96 kHz sampling and jack is using 48 kHz sampling then that could account for the 2X time problem.  To keep the delta card in the same virtual slot, you will have to add some magic lines to the bottom of your alsa-base file.

---

### Post by dbsoundman on 2008-03-05
As far as I know, Jack is running at 96k, as is the Delta. At least, in the qjackctl setup menu, I specified 96k sample rate...could something else be on the wrong rate?

I do know that whenever I start up Jack and it happens to be set to the computer soundcard because the hw number changed, it defaults to 48k, but I always reset it when I switch to the right hw device.

I have also tried uninstalling jackd and qjackctl, but it seems that whatever the problem is is not affected by this. So it's either some sort of external configuration file that they both use, or it's something else.

One other thing I have noticed...when I start qjackctl from the menu, it starts up normally, but when I go to the terminal and try to start it, I get an error that says it can't find libjack.so.0 or something like that. Could this be the problem, and if so how do I fix it? The weird thing is is that it only comes up on the command line...

-Dan

---

### Post by dbsoundman on 2008-03-05
OK, so here's something I just tried that maybe sheds some light: I started qjackctl again, set it to the delta1010, but this time, I set the sample rate to 48k instead of 96k. Started the transport, and voila, time runs correctly. So then what might be running incorrectly?

-Dan

---

### Post by tgalati4 on 2008-03-06
My guess is that the motherboard sound card is only capable of 48K and the Delta runs at 96K.  Jack may not be able to handle two different rates so it defaults to 48K.  It just doesn't spit out errors to that effect--which would be a bug that should be reported in jack's bug tracker.

The libjack error could be several things:  many libraries have aliases--pointers to different versions of the same library, or different physical locations of the library file.

Post the output of:

>whereis libjack

You can search the bug tracker for libjack and it will probably turn up clues.

Try turning off the motherboard sound card in the BIOS and you will get better jack performance with the Delta card.

---

### Post by dbsoundman on 2008-03-06
That would make a lot of sense. I suppose disabling my motherboard soundcard wouldn't break my heart either...I just use it for "normal" music playback, and if I could set the Delta to be the default soundcard, I would be ok with that. I have no idea how to do all this though, and I understand that messing with BIOS is a dangerous thing...is there a particular way I should go about this?

Thanks,
Dan

---

### Post by dbsoundman on 2008-03-07
OK, I think I fixed it! I was playing around with various system settings, trying to figure out how to get my PCM output to the delta outputs (which I still haven't gotten), but I found some buttons I could add to the volume control utility for the Delta, one of which involves the default sample rate, which was set to 48k. I set it to 96k, and restarted JACK at 96k, and VOILA, I get 96k resolution and the JACK clock runs correctly!

Now, my new question: how do I get the PCM output to a pair of the multitrack outputs? I can't seem to find anything that will make this happen. I tried setting my default sound device for music and video under the preferences>sound menu to ICE1712, which *appears* to be the Delta, but I get nothing aside from the test tone I can play on that menu. Other than that, any regular audio like music, etc. gets played through the regular soundcard and not the delta. What am I missing?

-Dan

---

### Post by tgalati4 on 2008-03-08
If you shut off the on-board sound card through the BIOS, then the output has no choice but to go through the Delta.  Realize though, that you need to change the patch bay to route the PCM outputs to the hardware outputs channel 1 and 2 for playback.  This can be a pain for editing because you need to constantly switch the input and output patches.

---

### Post by dbsoundman on 2008-03-08
That might be more annoying than I think it might be...so maybe I don't want to do that. Here's what I'd like to be able to do: I would like to be able to route the PCM output basically wherever I want. By PCM I mean the standard computer sounds, audio, video stuff, nothing to do with editing and such. So, let's say I want to record a web radio show on a tape. So I can go and repatch something in the computer, and reroute the PCM out to the Delta's outputs to make a tape. If I could really have it my way, I would have both soundcards going at the same time, so I could listen through the standard card and tape through the Delta, but I'm willing to compromise there. Is there some way to do this? I did finally (inadvertenly) get the delta to keep the same hardware identity by adding some lines to a file, I forget which ones. So now the delta has hardware number 0, and the standard card is number 1. How can I do all of this?

By the way, I started a separate thread for this topic; [if you click here you'll go to it.]("http://ubuntuforums.org/showthread.php?t=718080")

-Dan

---

