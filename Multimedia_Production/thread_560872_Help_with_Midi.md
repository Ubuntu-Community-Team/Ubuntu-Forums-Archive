---
title: "Help with Midi"
date: 2007-09-26
forum: Multimedia Production
---

### Post by PlatoFunFactory on 2007-09-26
Hey all, 

I'm running Ubuntu Studio and I'm rather baffled by Midi.  I'd really like to do some composition in Rosegarden and use Virtual Keyboard with one of the soft synths to just see what kinds of sounds I can coax out.  The problem is, right now, neither seems to be working. 

-I can play midi files using Timidity
-When I open a midi file in Rosegarden it shows up fine, but I get no audio when I play it. 
-Haven't managed to get crap out of the Virtual Keyboard yet. 

I'm an absolute beginner with Linux--I only started using it about three weeks ago--so please be very gentle with me.  I know almost none of the terminology. I can use Synaptic and can at least cut and paste code into the terminal but that's about it. 

Finally, does there exist a true beginner's tutorial to using Jack, or even a basic explanation of what on earth it is? I get the basic idea of linking up inputs and outputs, but beyond that I'm lost. 

Thanks so much for taking the time to read this and for any replies you might have. 

Just trying to learn, 
jp

---

### Post by stmiller on 2007-09-27
Hey here's some quick stuff:

Look into getting a USB midi keyboard, if possible. Most all work automatically in Linux. Plug it in and it works. I have an Edirol keyboard and it works great.

Also,** install the low-latency ubuntu kernel**, or else audio latency will be very bad.
```

sudo apt-get install linux-image-low-latency

```

**Then the next step is to get jack running ok.** You must start jack before running any audio apps.
The program qjackctl is good for controlling jack, so install qjackctl. Then start qjackctl, and then try different options. Set Frames/Period to 512 or so, softmode, force 16bit, and then see if that starts ok. There may be a couple of error messages when it begins. If it says 'Started' at the top, it is running OK. Some onboard soundcards are fixed at 48000, so you may have to specify 48000 in there too.

**What the heck is Jack?**

Jack is truly remarkable as it allows you to connect audio AND midi internally in Linux, between any audio apps. Unlimited options! Send midi from Rosegarden to a soft synth recording onto a track in Ardour. All internally, with no noise and great sound. When you open jack compatible apps, they will connect automatically for the most part.

Next: To do midi work you can use sound fonts, as they perhaps work best to start out with. Search google for some popular ones, like the cadenza.sf2 or others.

Once you have a good sound font, you can use **qsynth.** Start qsynth, have it load a soundfont, and then Rosegarden will automatically recognize qsynth and you should have sound on tracks where you load qsynth.

OK hope this helps! I am a free lance commercial music composer and use lots of these apps. I will try to write an in depth guide when I get time. My typical setup is:

Rosegarden as MIDI host triggering ->Qsampler: VSL string samples ->recording onto individual tracks in Ardour loaded with tons of plugins.

All audio and midi routed internally via jack. Add in other synths and I've got quite a tangled mess, but qjackctl handles connections with ease, for the most part.

There are good synths in Linux, too. Try installing zynaddsubfx.

---

### Post by arachnegl on 2007-09-30
I have lots of empathy!! I was in the same boat until quite recently. Apart from the good advice given above, these links helped me no end:

[http://rosegarden.sourceforge.net/tutorial/en/chapter-0.html](http://rosegarden.sourceforge.net/tutorial/en/chapter-0.html)

Especially the section on getting Rosegarden to produce sound.

and,

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

With hindsight, the greatest difficulty for me was getting Jack configured. I just tried many different variations blindly and stumbled on one that works.

I also now have a USB keyboard (E-MU) its just plug and play, I recommend it.

best of luck. The final result is worth it though.

(ZynaddsubFX is great so is Qsynth)

---

