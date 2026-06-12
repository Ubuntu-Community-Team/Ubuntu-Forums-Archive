---
title: "Signal strength / noise monitoring utility"
date: 2008-05-14
forum: Mythbuntu
---

### Post by GordonEndersby on 2008-05-14
Is there a graphical Signal strength/noise monitoring utility I could use to look at the signal being received by my DVB cards(Nova T 500).
Im having a few issues getting the splitter/amplifier adjusted just right on my mythbuntu 8.04 system.

Ive got 2 Nova T 500's and they dont have a pass through.
Ive tried a simple splitter and the signal wasnt good enough.
Just 25% on screen in live TV for BBC1 and im only just down the road from the crystal palace transmitters.
The internal amplifier was turned on.
The amplifier ive tried is fiddly to adjust and hit and miss balancing the noise against amplification.

Each channel across the 2 cards seems to get a slightly different signal strength. so Im trying to get an acceptable level across all channels and receivers.
If I turn up or down the amplifier I either get no lock or some breakup.
At the moment its ok but Im not sure Im getting it a s good as it could be.

If I could get something on screen representing the signal strength and noise. I could work out the best settings for the amplifier.
I have tried switching through watching live TV using the "Y" key but its very time consuming.

Might be something nice to roll into the mythbuntu distribution if there is something to use.

Thanks

Gordon

---

### Post by mymythtv on 2008-05-14
Got the same problem - not with a T-500 ( which does  show different signal strength on each input btw ), but a DVB-S card when I try to align the dish - missing a graphical indicator

Have tried "femon", but it only shows signal/snr line-based.
Works ok on DBV-S and DVB-T, so give it a try

The VDR project have the femon as a gui, and thats looks good :-)
( [http://www.saunalahti.fi/~rahrenbe/vdr/femon/](http://www.saunalahti.fi/~rahrenbe/vdr/femon/) )

---

### Post by GordonEndersby on 2008-05-15
Yes I can see the signal strength. 
But you need the signal to noise ratio as well.
I can get the signal strength up to 80% but too noisy for a lock.

Femon looks like what I need.

Thanks

Gordon

---

### Post by copycat on 2010-04-29
Thanks guys... now I don't need to post my question :-)

---

### Post by ian dobson on 2010-04-29
Hi,

Do you have munin running on your backend? If yes I've got a plugin that monitoring the signal strength/ber/ubr. See [http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-dvb_signal.html](http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-dvb_signal.html)

I have several mythtv plugins:-
[http://mail.planet-ian.com/munin/planet-ian.com/index.html](http://mail.planet-ian.com/munin/planet-ian.com/index.html)

Regards
Ian Dobson

---

### Post by williammanda on 2010-04-29
> **ian dobson said:**
> Hi,

Do you have munin running on your backend? If yes I've got a plugin that monitoring the signal strength/ber/ubr. See [http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-dvb_signal.html](http://mail.planet-ian.com/munin/planet-ian.com/alpha2.planet-ian.com-dvb_signal.html)

I have several mythtv plugins:-
[http://mail.planet-ian.com/munin/planet-ian.com/index.html](http://mail.planet-ian.com/munin/planet-ian.com/index.html)

Regards
Ian Dobson

How do you use munin once it is installed? I looked over the wiki but didn't see a way to get started for someone new.

---

### Post by ian dobson on 2010-04-29
Hi,

Munin generates web pages that you can access fromy browser.

Have a look at [http://www.debuntu.org/how-to-monitoring-a-server-with-munin](http://www.debuntu.org/how-to-monitoring-a-server-with-munin) on how to install munin.

Regards
Ian Dobson

---

