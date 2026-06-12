---
title: "No Microphone Input from Bluetooth Headset"
date: 2020-03-18
forum: Multimedia Software
---

### Post by kmand on 2020-03-18
I'm replacing my original posting with an update based on a further experiment and one success.

I was first motivated by an earpod that worked well with my android phone but I couldn't get mic input on Ubuntu 18.04. This is one of the many nearly identical Chinese earpods from small companies that probably use the same chipset.

pacmd showed 

profiles:
		a2dp_source: High Fidelity Capture (A2DP Source) (priority 20, available: no)
		a2dp_sink: High Fidelity Playback (A2DP Sink) (priority 40, available: yes)
		headset_head_unit: Headset Head Unit (HSP/HFP) (priority 30, available: no)
headset-input: Headset (priority 0, latency offset 0 usec, available: no)

So no surprise that I couldn't get mic input. Then I tried a "Motorola Sliver II" which is a headset a bit larger than an earpod, but still hangs on the ear. This one shows with pacmd

profiles:
		input:analog-stereo: Analog Stereo Input (priority 60, available: no)
		output:analog-stereo: Analog Stereo Output (priority 6000, available: unknown)
		output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 6060, available: unknown)
                headset-input: Headset (priority 0, latency offset 0 usec, available: unknown)


Despite the Unknown, this mic input actually works on Ubuntu 18.04

so its hit and miss. So while I would hope that since all of these support HSP/HFP to work on a phone, getting input on Linux is very device specific.

---

