---
title: "Problem with headphones"
date: 2010-11-14
forum: Multimedia Software
---

### Post by fabzzap on 2010-11-14
First, the boring stuff: my PC has a motherboard MSI 800GM-E41 with integrated audio, runs an AMD Athlon2 quad-core CPU, and Ubuntu 10.10 64-bit is installed.

The problem is  that the headphones do not work as expected. Expectation: when the headphones are unplugged, sound should come from the speakers, and, when the headphones are plugged in, no sound should come from the speakers, and sound should come from the headphones.

What really happens: in Preferences->Audio there is a tab "Output", with a "Connector" drop-down menu with 2 entries: Analog Headphones and Analog Output. The existence of this drop-down menu is already a mistake: the PC is able to detect whether the headphones are plugged or not, so it should be able to detect what output to use.

If Analog Audio is selected and the headphones are unplugged, no problem: the speakers work. Then, headphones are plugged in. The output volume slider goes to Mute automatically, no sound comes at all, either from the speakers or the headphones. I manually uncheck Mute, and sound comes from the speakers *and* the headphones.

If Analog Headphones are selected and the headphones are unplugged, no sound at all, also from the speakers. When the headphones are plugged in, sound comes from the headphones and not from the speakers, which is right.

So, Ubuntu seems capable to do the right the right thing, only not automatically... Is this a bug, or is this some misconfiguration?

---

