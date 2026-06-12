---
title: "Intermittent no sound just beep"
date: 2009-09-10
forum: Multimedia Software
---

### Post by thor-on-kveven on 2009-09-10
Hello!

I've been using ubuntu for a year now and getting a bit used to sorting out issues by surfing the forums and guides in the extremely helpful linux universe. Unfortunately I tend to follow tips and how-tos by the numbers, so still no complete understanding. And this latest issue has me completely stumped:

-I'm running Ubuntu Ibex with all updates on Intel Core 2 Duo with an older Soundblaster Live! soundcard. This has been running well for almost a year.
- I recently installed a Realtek Winfast 1000 S digital TV card (PCI) that is usually un-supported in ubuntu, but I got it working using this recipe: [http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/)
- Everything was running well for some hours and several re-boots after this installation. Then I came back to the box and found it frozen with Kaffeine and firefox running (very rare for me to experience complete freeze) so I had to do power-button re-boot
- After this re-boot sound was gone and replaced by monotone hight pitch beep whenever there was supposed to be sound, i.e. on boot-up, with music players, web pages etc.
- tried several re-boots and minor fiddling in Prefrences > Sound with no change.
- Thought my souncard had gone, so removed it inspected and re-inserted with no change
- followed the ubuntu forum "comprehensive sound guide" thread and found drivers etc to be in order, and fiddled with alsamixer with no intent. After this sound was NORMAL!
- I then got one day of normal functioning before the same sound problem came back, but now intermittent and sometimes self limiting, e.g. 5-10 secs and then normal sound. When it wouldn't stop by itself I could always fix it by adjusting alsamixer
- Today the problem is permanent and adjusting alsamixer has no effect. It started with several programs running but no other problems with running the box. 

So, I'm not even sure where to start looking. 
-Does it sound like gradual hardware failure? The new DVB card is in slot next to soundcard, heat etc? 
- Could it be due to driver changes or kernel changes with the DVB installation? But then why so intermittent?

On my lspci -v I notice that the sound card (i only have one) appears twice, as "Multimedia controller" and "input device controller". Normal? I don't think it looked like that when fiddling with the DVB card a couple of days ago.

04:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: LeadTek Research Inc. Device 6655
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at e5100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

04:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
	Subsystem: Creative Labs Device 8065
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at d000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

04:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
	Subsystem: Creative Labs Device 0020
	Flags: bus master, medium devsel, latency 32
	I/O ports at d100 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

I hope someone can give me a pointer. I almost hope it's hardware so I can go and buy something and not spend hours fiddling with software and drivers;-)

Cheers

---

### Post by tkoco on 2009-09-21
Given what you have told us, it sounds like the hardware is conflicting. The easiest fix is to try a different sound card like a cheap PCI bus sound card using a different chip set than Creative Labs.

In general terms, a freeze of a system is either "a hardware lock-up" or "running out of memory _and_ swap space". Hopefully this helps.

> **thor-on-kveven said:**
> Hello!

I've been using ubuntu for a year now and getting a bit used to sorting out issues by surfing the forums and guides in the extremely helpful linux universe. Unfortunately I tend to follow tips and how-tos by the numbers, so still no complete understanding. And this latest issue has me completely stumped:

-I'm running Ubuntu Ibex with all updates on Intel Core 2 Duo with an older Soundblaster Live! soundcard. This has been running well for almost a year.
- I recently installed a Realtek Winfast 1000 S digital TV card (PCI) that is usually un-supported in ubuntu, but I got it working using this recipe: [http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/)
- Everything was running well for some hours and several re-boots after this installation. Then I came back to the box and found it frozen with Kaffeine and firefox running (very rare for me to experience complete freeze) so I had to do power-button re-boot
- After this re-boot sound was gone and replaced by monotone hight pitch beep whenever there was supposed to be sound, i.e. on boot-up, with music players, web pages etc.
- tried several re-boots and minor fiddling in Prefrences > Sound with no change.
- Thought my souncard had gone, so removed it inspected and re-inserted with no change
- followed the ubuntu forum "comprehensive sound guide" thread and found drivers etc to be in order, and fiddled with alsamixer with no intent. After this sound was NORMAL!
- I then got one day of normal functioning before the same sound problem came back, but now intermittent and sometimes self limiting, e.g. 5-10 secs and then normal sound. When it wouldn't stop by itself I could always fix it by adjusting alsamixer
- Today the problem is permanent and adjusting alsamixer has no effect. It started with several programs running but no other problems with running the box. 

So, I'm not even sure where to start looking. 
-Does it sound like gradual hardware failure? The new DVB card is in slot next to soundcard, heat etc? 
- Could it be due to driver changes or kernel changes with the DVB installation? But then why so intermittent?

On my lspci -v I notice that the sound card (i only have one) appears twice, as "Multimedia controller" and "input device controller". Normal? I don't think it looked like that when fiddling with the DVB card a couple of days ago.

04:00.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: LeadTek Research Inc. Device 6655
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at e5100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

04:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
	Subsystem: Creative Labs Device 8065
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at d000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

04:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
	Subsystem: Creative Labs Device 0020
	Flags: bus master, medium devsel, latency 32
	I/O ports at d100 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp

I hope someone can give me a pointer. I almost hope it's hardware so I can go and buy something and not spend hours fiddling with software and drivers;-)

Cheers

---

### Post by thor-on-kveven on 2009-11-27
Just an update: After much fiddling and and no success I reached for the non-discriminatory weapon of distribution upgrade. Sound OK now.

---

