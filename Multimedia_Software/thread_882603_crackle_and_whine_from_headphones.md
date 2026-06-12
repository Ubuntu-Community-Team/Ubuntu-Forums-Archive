---
title: "crackle and whine from headphones"
date: 2008-08-07
forum: Multimedia Software
---

### Post by leetrefz on 2008-08-07
This is my last problem till I'm totally satisfied with my little system; homebuilders forums have been no use so trying the gurus here.

I get a high pitched whine in my speakers. If I tap the wires to the mic I get crackles and loud buzzes. I'm using audio sockets soldered to wires since I built my own case so no proper front panel. 

I think the mic has one channel and a ground. Yet the mobo manual says:

Pin Signal     
1---MICIN1_L
2---AGND
3---MICIN1_R
4---+5V
5---LINEOUT_R
6---LINEIN_R
7---LINEOUT_L
8---LINEIN_L
9---HPOUT_R
10--HPOUT_L
11--SENSE_A
12--SENSE_B
13--CEN_OUT
14--LFE_OUT
15--SSROUT_R
16--SSROUT_L
17--SPDIF_IN
18--GND

1 & 2 are mic in L & R. Can there be a stereo mic or lines for 2 mics? I have pins 1 & 3 wired to my mic socket. I have pins 2, 5, and 7 wired to the speaker socket. wiggling any of those wires will change the whine. Touching the wire nubs sticking out of the mic socket makes a loud buzz. I can hear the mouse move. I think I must have the wrong pins, but no soldering iron on hand to experiment. 

I had pin 2 wired to the mic & speaker, but took it off the mic hoping the problem was that simple.

Thanks for any help!

---

### Post by sdowney717 on 2008-10-16
Pin Signal

If it meets ac97 intel audio spec, then this is the pinout.
1 = mic in
2 = gnd
3 = mic reference bias
4 = +5 volts
5 = right channel sound output
6 = gnds when headphone plugged in, turns off rear jack, leave disconnected both jacks work
7 = reserved?
8 = key, no pin
9 = left channel sound output
10 = gnds when headphone plugged in, turns off rear jack, leave disconnected both jacks work

And i will get a tiny humming click that varies with volume control and front panel audio for me always poor compared to rear jack.

---

### Post by markbuntu on 2008-10-16
Are you using shielded cables?
You really should be because unshielded cables will pick up noise and there is not much you can do about that.

If you do use shielded cables you should solder the shields to agnd or gnd. If you have wired the mic wrong, it will pick up all sorts of noises from the cable. Use a shielded cable and wire the shield to agnd and the wire to mic. Be sure that the connections at the plug are the wire to tip and shield to ring. 

Same with the line out though it is a little less suseptible to picking up noise. A two sire shielded cable would be best for that. You can use a shielded cable with more wires just be sure to solder all the unused wires to gnd.

---

