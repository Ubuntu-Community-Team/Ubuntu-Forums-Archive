---
title: "Ubuntu Studio 9.10 MIDI input from sound card not working"
date: 2010-03-21
forum: Multimedia Software
---

### Post by lenson on 2010-03-21
I am using ubuntu 9.10 (kernel 2.6.31-9-rt) and an M-Audio Delta 1010 PCI sound card, and trying to get MIDI inputs and outputs to work on this sound card.

I have Jack installed and working. MIDI signals from virtual keyboard or a MIDI player can be routed to fluidsynth, and fluidsynth's audio can be played back through the outputs of the delta 1010.

I can use a MIDI sequencer (e.g. rosegarden or qtractor) to record MIDI from virtual keyboard, with jack handling the routing.

But, no matter how I configure the connections in jack, I can't get any signals from the "MIDI In" port on the sound card.

I start qjackctl, then I start qtractor.
Under the qjackctl "connections" window, under the 'ALSA' tab, I see...

Readable Clients / Output Ports:
> 20:M Audio Delta 1010
    > > 0:M audio Delta 1010 MIDI
> 129:Qtractor
    > > 0:Master

In Writable Clients / Input Ports...
> 20: M Audio Delta 1010
    > > 0:M Audio Delta 1010 MIDI
> 129:Qtractor
    > > 0:Master

I connect the output port 0:M Audio Delta 1010 MIDI (under 20:M Audio Delta 1010) to the input port 0:Master (under 129:Qtractor)

I also start up Virtual Keyboard, and connect it to 129:Qtractor/0:Master, just to make sure 0:Master is listening.

Now, I go into Qtractor and hit record. I click keys on the virtual keyboard, and MIDI data shows up in the master track in Qtractor, so it is listening. Now, I push keys on my keyboard, with MIDI out cable from the keyboard going to MIDI in on the delta 1010, and nothing shows up.

Does anybody have some thoughts on how to fix this? Where is the disconnect between the delta 1010 and qtractor? I am concerned also that the "MIDI In" LED on the front panel of the Delta 1010 never blinks. There must be some basic ALSA configuration that needs to be done to activate and use these MIDI ports, or something. I've been trying to figure it out for days.

Thanks for reading,
lenson

---

### Post by cchhrriiss121212 on 2010-03-22
I would try to use patchage to connect midi up. For some reason jack connections refuses to refresh sometimes and ends up freezing on me. I assume you disconnect the virtual keyboard before connecting the real one?
I don't own one but I'm fairly certain that the 1010 is plug and play with alsa. Check your physical connections and cables with something else or try the delta on a windows machine/partition.

---

### Post by lenson on 2010-03-24
it seems to me like there should be no need to disconnect the virtual keyboard- if jack were working properly, both keyboards should be able to send midi simultaneously to the virtual synth. Is this not so?

I haven't heard of 'patchage' - something I'll look in to.

You're right about the 1010- audio plays fine. Just the MIDI is hanging up on me still...

---

### Post by lenson on 2010-03-24
update: tried disconnecting virtual keyboard before using real keyboard- no deal...
also, tried patchage- this looks like a GUI that uses the jack API, right? I don't really see how this should help, but I tried it anyway- no good.
open to any suggestions. Thanks for trying...

---

