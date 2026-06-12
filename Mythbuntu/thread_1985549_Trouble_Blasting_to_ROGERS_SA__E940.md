---
title: "Trouble Blasting to ROGERS SA  E940"
date: 2012-05-23
forum: Mythbuntu
---

### Post by stevecartermo on 2012-05-23
Our analog cable was finnaly cut off so I am now trying to get Mythbuntu 12.04 working with the ROGERS Scientific Atlanta E940 STB and a MCE Transciever. I have the machine trying to blast when a channel change is requested (RED BLASTER LIGHT FLASHES !) but the cable box does not actually change channels, it just times out on the channel change and says no lock. I tried IRSEND from the command line and that generates flashes from the blaster, but again no actual channel change. The SA box is identified as a SAE8000 perhaps I require another LIRC definition ?

Any Ideas ?

Thanks

---

### Post by jobcol on 2012-05-25
Make sure that the Blaster is directly over the IR receiver eye on your STB,as blasters have a very short range.
Best way to test is issue

```
irsend SEND_START SAE8000 Power 
```

as this will make the Blaster pulse/flash continuously, enabling you to move the Blaster across the IR receiving window, to try and find the sweet spot, and see if it will power off the STB .

---

### Post by stevecartermo on 2012-05-27
Thanks for the suggestion ... it does flash continuously when I issue the command 


irsend SEND_START SAE8000 Power

but unfortunately there is no SWEETSPOT so the STB never shuts off.

Any other ideas ??

---

### Post by jobcol on 2012-05-28
Ok,if it doesnt work you may not have the right lircd.conf for your STB remote.
Before you go down that road though I would suggest making absolutely sure you have the IR Blaster over the right spot on the front of the STB. From Googling your STB model it looks like its IR sensor is about a half inch to the right of the Green power led on front window.So start over the Green led and slowly move to the right, also try blasting a different code(s) with irsend SEND_START and with just irsend SEND_ONCE. Try some numbers and see if the STB responds.

---

### Post by stevecartermo on 2012-05-29
Thanks for the suggestion ... but no joy ... send start causes the light to flash many times whereas sendonce just flashes it once. but niether command will get the STB to do anything. 

I passed the blaster slowly over the front face of the STB.


Any other suggestions ?

---

### Post by nickrout on 2012-05-30
> **stevecartermo said:**
> Thanks for the suggestion ... but no joy ... send start causes the light to flash many times whereas sendonce just flashes it once. but niether command will get the STB to do anything. 

I passed the blaster slowly over the front face of the STB.


Any other suggestions ?

yeah perhaps you are using the wrong remote configuration. The documentation for doing that is here:

[http://lirc.org/html/irrecord.html](http://lirc.org/html/irrecord.html)

or google finds this [http://lirc.sourceforge.net/remotes/scientific_atlanta/E940](http://lirc.sourceforge.net/remotes/scientific_atlanta/E940)

(It also finds other threads if you google sa e940 lirc)

---

### Post by stevecartermo on 2012-05-31
I tried the defintion file described for the 940... It exhibited the same symptoms the irblaster would flash but the STB would not change channels.

Luckily I had another older receiver/blaster. I swapped the older one in place of the newer one ..and voila it worked.

This one didn't work

ID 1934:5168 Feature Integration Technology Inc. (Fintek) F71610A or F71612A Consumer Infrared Receiver/Transceiver


This one did


ID 0471:0815 Philips (or NXP) eHome Infrared Receiver

Thanks to all who helped..

---

### Post by spiregrain on 2012-07-20
I have one of those Fintek 1934:5168s.  Do you still have the config files for it that made the LED flash?

I can get mine to receive OK, but although irsend doesn't complain, the blaster LED doesn't flash.

---

### Post by nickrout on 2012-07-20
> **spiregrain said:**
> the blaster LED doesn't flash.

How are you testing that? Your eye won't see it, quick and easy way is to look through a digital camera viewfinder.

---

### Post by spiregrain on 2012-07-20
> **nickrout said:**
> How are you testing that? Your eye won't see it, quick and easy way is to look through a digital camera viewfinder.

I'm testing it by looking through a digital camera viewfinder.

---

