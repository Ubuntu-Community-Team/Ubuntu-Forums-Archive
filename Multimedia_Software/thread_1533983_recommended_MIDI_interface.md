---
title: "recommended MIDI interface"
date: 2010-07-18
forum: Multimedia Software
---

### Post by raymondvillain on 2010-07-18
What is the best way to hook up a MIDI keyboard to the back of my desktop?  I'm using Rosegarden and Jackd, and I have a very old Korg keyboard with MIDI out and MIDI in jacks.

The motherboard on my computer has HDMI, USB ports, firewire, and 6 jacks for 7.1 home theatre (I guess that's what they're for).

Is there a way to use a software program and have its MIDI output connected to Rosegarden with Jackd?  That way I could do away with the Korg.

---

### Post by theraje on 2010-07-19
> **raymondvillain said:**
> What is the best way to hook up a MIDI keyboard to the back of my desktop?  I'm using Rosegarden and Jackd, and I have a very old Korg keyboard with MIDI out and MIDI in jacks.

The motherboard on my computer has HDMI, USB ports, firewire, and 6 jacks for 7.1 home theatre (I guess that's what they're for).

You can get a USB-MIDI interface for pretty cheap ($30-$50 USD). I have an Alesis LineLink brand interface that works well. It comes with MIDI-IN and MIDI-OUT jacks on one end, and a USB plug on the other. Just plug it in and you're ready to go pretty much. :)

---

### Post by cchhrriiss121212 on 2010-07-19
> Is there a way to use a software program and have its MIDI output connected to Rosegarden with Jackd? That way I could do away with the Korg.
There is a virtual midi keyboard in the repos if that is what you mean?

---

### Post by raymondvillain on 2010-07-19
Thanks, cchhrriiss1212, in Synaptic I can see vkeybd and vmpk.

My question is, if I install one or the other of these, can I connect (in software, such as the connection window in jack) a MIDI "out" with Rosegarden "in"?

---

### Post by theraje on 2010-07-22
@raymondvillain:

Sorry, I gave you some incorrect info. I was thinking about this thread when I was looking through my (millions and millions of) cables and stuff, and I came across the Alesis device I mentioned - it is an AUDIO interface, with 1/4" TS plugs... NOT MIDI plugs.

I got my wires crossed (sorry for the horrendous pun). I actually use an E-MU XTab 1x1 MIDI interface. It is what I use to send MIDI data back and forth from my old Korg Triton to my computer.

Please forgive any confusion I may have caused!

As for a virtual keyboard sending MIDI data to other software, I have been poking around, but I can't seem to get anything to work. I was thinking you could do it using the input device dropdown in the MIDI sequencer application, but I haven't had any luck. So I guess your MIDI board is possibly stuck with you for a while longer.

---

### Post by cchhrriiss121212 on 2010-07-22
> **raymondvillain said:**
> Thanks, cchhrriiss1212, in Synaptic I can see vkeybd and vmpk.

My question is, if I install one or the other of these, can I connect (in software, such as the connection window in jack) a MIDI "out" with Rosegarden "in"?
Yes thats right, it will show up just like an actual midi keyboard. I'd also recommend using patchage over the jack connection window, as it is a bit easier to connect things up and see what is going on.

---

