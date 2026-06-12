---
title: "MIDI question."
date: 2007-09-03
forum: Multimedia Production
---

### Post by CapitanYochua on 2007-09-03
I just bought a MIDI compatible synth. I was wondering what kind of equipment (cables, interfaces, or whatever) I should buy to record/edit music from the synth to my computer (that runs on ubuntu, obviously)? Some programs I could use would also be helpful. Thank you.

---

### Post by xhilyn on 2007-09-03
Hi. For basic MIDI I/O you will need a cheap sound card with a games port and a Games Port to MIDI lead. Both of which can be got from e-Bay. Alternatavley you can buy a Pro Sound Card like the M-Audio 2496 which also has MIDI in and out sockets. Or a USB/Firewire based audio/MIDI interface.

As far as software is concerned I am very new to Linux and have just installed UbuntuStudio.

[http://ubuntustudio.org/](http://ubuntustudio.org/)

So far I have experimented with using Rosegarden, which is a Cubase like programme which comes as part of UbuntuStudio along with 'Ardour' and 'Audacity' and a load of other software.

There are other people who know loads more about it than I do as I am very new to Linux and Audio/MIDI on Linux, though I know a fair bit about it on Windows and Older Macs.

xhi.

---

### Post by stmiller on 2007-09-03
Just buy any of the various MIDI-USB cables, like the Yamaha UX16. Works in Linux and connects midi devices via USB.

That will send midi signals (only) from your synth. To record audio from the device, you'll need something like a Presonus Firepod or similar device.

---

### Post by CapitanYochua on 2007-09-03
> **stmiller said:**
> Just buy any of the various MIDI-USB cables, like the Yamaha UX16. Works in Linux and connects midi devices via USB.

That will send midi signals (only) from your synth. To record audio from the device, you'll need something like a Presonus Firepod or similar device.

 Any links please? And I'm new to MIDI in general. So I have no clue what a Presonus Firepod is. I know my synth (microKorg) has some free software from the korg site for windows. I haven't really been able to try it through wine yet because I don't have the MIDI cables. Is my best bet to find the cables at a store like best buy or just get it through ebay or something? what is the signficance of "midi signals (only)"? Also,  the Yamaha UX16 doesn't show compatibility from what I am looking at. But it still works?

---

### Post by jondecker76 on 2007-09-05
There are 2 things you need to consider - 

1) MIDI is nothing but data describing how to reproduce music - it is not audio. It is simply data telling a midi device (hardware or software) which sound to play, which note, how long the note is held, etc. You may already know this, but just in case you needed a primer.

2) Audio is what you hear.  Again, i'm sure you know this

the key is to tie the two together. To do this you will need a couple of things to turn your MIDI data into Audio you can hear.

With your microKorg, you will have a lot of options.
1) Use the keyboard as a midi device to control software synthesizers, drum sequencers etc, and record that audio right in your ubuntu box.

2) Route Audio only through your microKorg and let its built-in filters change the sound (vocoding etc), route that sound back into your computer and record it.

3) Have the microKorg process its own MIDI data and record its Audio output.

4) Any combination of the above.

What you need is a decent sound card that has MIDI in/out on board - this would be the simplest solution. I recommend the M-Audio Delta series of cards (Delta 44, Delta 66, Delta 1010) but there are many inexpensive ones that would do just fine for you.

Other than that, a couple of MIDI cables and whatever audio cables you will need and your in business. UbuntuStudio will provide you all the software you will need to interface your microKorg to your computer, record it etc.

Just take your time, do a lot of reading and start playing around with it. But first thing is first, get your cables and a sound card to hook it all up.

---

### Post by stmiller on 2007-09-05
> **CapitanYochua said:**
> 
 Also,  the Yamaha UX16 doesn't show compatibility from what I am looking at. But it still works?

That Yamaha thing is just a MIDI to USB cable. It works with ANY MIDI device. Just attach your current keyboard with this and all Linux audio programs will instantly see the MIDI device.

And as jondecker76 states, recording audio into your computer is something different.

There are many software synthesizers for Linux that work like a real keyboard/synth, but all in software. So using your present keyboard as a MIDI controller you can 'play' and trigger the software synths all inside Linux. Rosegarden is a good program for this. This actually works quite well, and you don't have to go to the trouble of routing and recording audio from your hardware keyboard.

---

### Post by CapitanYochua on 2007-09-08
> **jondecker76 said:**
> There are 2 things you need to consider - 

1) MIDI is nothing but data describing how to reproduce music - it is not audio. It is simply data telling a midi device (hardware or software) which sound to play, which note, how long the note is held, etc. You may already know this, but just in case you needed a primer.

2) Audio is what you hear.  Again, i'm sure you know this

the key is to tie the two together. To do this you will need a couple of things to turn your MIDI data into Audio you can hear.

With your microKorg, you will have a lot of options.
1) Use the keyboard as a midi device to control software synthesizers, drum sequencers etc, and record that audio right in your ubuntu box.

2) Route Audio only through your microKorg and let its built-in filters change the sound (vocoding etc), route that sound back into your computer and record it.

3) Have the microKorg process its own MIDI data and record its Audio output.

4) Any combination of the above.

What you need is a decent sound card that has MIDI in/out on board - this would be the simplest solution. I recommend the M-Audio Delta series of cards (Delta 44, Delta 66, Delta 1010) but there are many inexpensive ones that would do just fine for you.

Other than that, a couple of MIDI cables and whatever audio cables you will need and your in business. UbuntuStudio will provide you all the software you will need to interface your microKorg to your computer, record it etc.

Just take your time, do a lot of reading and start playing around with it. But first thing is first, get your cables and a sound card to hook it all up.

 um. I have an HP with an integrated sound card. Would I be able to get another sound card to work with for recording, MIDI, etc.. purposes?

---

### Post by Em-Buntu on 2007-09-08
> **CapitanYochua said:**
> I just bought a MIDI compatible synth. I was wondering what kind of equipment (cables, interfaces, or whatever) I should buy to record/edit music from the synth to my computer (that runs on ubuntu, obviously)? Some programs I could use would also be helpful. Thank you.

Here's what you want.[http://www.newegg.com/Product/Product.aspx?Item=N82E16823143018](http://www.newegg.com/Product/Product.aspx?Item=N82E16823143018)

I still use the old DIN style MIDI cables attached to a Sequential Circuits Six-Trak, A LIN Drum machine, and a couple of Casios and Yamahas.
I've just begun to use Ubuntu for music production, straight Ubuntu, not Studio. 

This one looks interesting. I won't try it because I'm sure wireless must have some effect on latency.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16823143004](http://www.newegg.com/Product/Product.aspx?Item=N82E16823143004)

I have my synths, drum machines and mics patched into one of these,
[http://www.newegg.com/Product/Product.aspx?Item=N82E16823143013](http://www.newegg.com/Product/Product.aspx?Item=N82E16823143013)

It's supposed to be supported under FreeBob (BeBob) but I haven't gotten any Ubuntu programs to recognize it yet. I dual boot into Windows XP 64 to run Cakewalk Sonar.
Here's FreeBob connecting an Eidrol FA-66 (thru Jack), which a smaller version of mine. It sees and captures the units analog capture inputs, but it still lacks MIDI support. Good news is, it's coming.
[https://sourceforge.net/project/screenshots.php?group_id=117802&ssid=12444](https://sourceforge.net/project/screenshots.php?group_id=117802&ssid=12444)

I've been playing with the Hydrogen Advanced Drum machine and it sounds pretty good and is very easy to use. I save the track as MIDI and had no problem importing it into Sonar. [http://www.hydrogen-music.org/](http://www.hydrogen-music.org/)

---

### Post by CapitanYochua on 2007-09-09
I'm trying to figure out how to record with Jack. Not going to well any help is appreciated. Should I get a new sound card to record (not MIDI in this case) since so far it hasn't worked well? Would I be able to with an integrated sound card?

---

### Post by geoffBEAM on 2007-10-03
Don't get discouraged!

In my early teens I tried to do the computer/midi chain thing and for years it just kept me from being a real musician.

IF I WERE YOU:

1)Buy a drum machine/sampler and a 4 channel mixer. Roland/Boss drums are great.

2)Plug drum machine and KORG in the mixer.

3)Run MIDI OUT from your computer to the MIDI IN on your Korg.

4)Run MIDI THRU from your KORG to Your Drum Machine.

4)Find SEQUENCER software on your computer.

5)Set KORG and Drum Machine MIDI CHANNELS (check manuals).

6)Set SEQUENCER Software to send MIDI to KORG/Drum Machine

=-=-At this point you should have everything you need to SEQUENCE music on external hardware with your computer. This means you can compose songs on your computer that are actually being played on your external KORG/Drum Machine into your mixer. Your computer is only sending MIDI notes at this point, it is not making any noise.

Why Use this Set Up?
Because dedicated analogue synths like your KORG are superior to the sounds your Ubuntu can make with software synths. They sound better. The reason you buy external hardware like your MICROKORG is for the sound quality and control of that sound quality.

With a drum machine and a MICROKORG you can bang out some crisp hip/hop or techno style beats.
=-=-=

Actually 'Recording' your audio should be LAST priority to learning how to program beats. If you make hard beats then you can go find a 128 track Pro-Tools studio to record your stuff...or you can just take your gear to a club and play it for everyone ; )

You should be able to find a decent used drum machine and mixer for the same price as a nice full duplex 1/4'' sound card, and you will have so much more fun. Recording is for Audio Engineers.

---

