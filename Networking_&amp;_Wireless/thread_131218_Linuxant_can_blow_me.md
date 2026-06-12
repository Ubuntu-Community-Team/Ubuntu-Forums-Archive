---
title: "Linuxant can blow me"
date: 2006-02-16
forum: Networking &amp; Wireless
---

### Post by Mortimer on 2006-02-16
Ok so I was told that any external modem would work out of the box without drivers. So much for that. Lies, or the modem is just broken?

It is a US Robotics modem model USR5686D - it is not new, so perhaps it's just broken? Got it since linuxant are a bunch of a-holes and the old winmodem I had stopped being supported on a newer kernel and just failed (after I updated ubuntu, thank god I didn't pay for that idiotic driver. Bite me suxixant). 

Anyways, the lights come on, so I would think it is in working order. Would anyone have ideas on how to determine if it works at all? 

It's all plugged in, lights on before turning on the PC. It is not detected. The serial port seems to be ok, I haven't tinkered with any of the settings in ubuntu. Modem is not detected, not in Networking settings, not in GnomePPP - same difference I imagine. If it doesnt work I have no choice but to go back to the other OS. Woohoo, silly little anti virus here I come!!

edit: It had the following dipswitches in the back, I have tried all sorts of settings, to no avail

1. data terminal ready 'normal' or 'override'
2. result codes 'verbal' or 'numeric'
3. result codes 'suppress' or 'display'
4. echo offline commands 'on' or 'off'
5. auto answer on first ring or nvram set, or auto answer off
6. carrier detect 'normal' or 'override'
7. load nvram defaults or load factory defaults
8. dumb mode or smart mode

I'd say the whole thing is 'dumb' as hell

---

### Post by handy on 2006-02-16
Test it on a windoze box if you can.

---

### Post by towsonu2003 on 2006-02-16
give vwdial a try (info on configuration etc on bottom of the second link in my signature).

edit: just saw you mention it's serial modem

If a serial old modem isn't working out of the box, after doing usual googling, I would fill out a bug report...

---

### Post by Mortimer on 2006-02-16
Okay. So it looks like the problem is not the modem, but the cable that I got. Appearently this modem does "not work correctly" with a Null Modem cable; hopefully that's a bs-ed way of saying "not at all", hopefully. What does work? It says an "RS-232 serial cable", which seem to have been phased out over the dull modem cables and are nowhere to be found. Keeping in mind that the null modem cable and this mysterious cable look identical, it doesnt help to see all these other RS-232 cables that are totally different, and who knows which is which. This is wonderful stuff.

Still, it's my fault for not getting a $50 modem at the store so I can connect at 26k in this dump of an area with no broadband. But linuxant still sucks abundantly and without dismay. Let's see, we have these common conexant winmodems that are in most crappy PCs by default around the world, let's help linux by charging $20 and then cutting off support from about 3/4 of the models without notice. Jerks in suck sauce. Die. So long.

---

