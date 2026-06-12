---
title: "Dual tuners changing order."
date: 2013-10-10
forum: Mythbuntu
---

### Post by drifting on 2013-10-10
Hello.
I wonder if someone can help, or even point me in the direction of a possible solution that I might understand? My linux is ok, but Udev blows me away.

I have two tuners a TBS6982 Dual DVB-S2, and a Hauppauge Nova-TD USB. currently on the latest Mythbuntu .27 and fully update OS.

Problem, the tunes keep swapping order! I seem to recall there was an option that I used before where I created a dvb.conf in modprobe.d, but I was lucky enough to have the same cards as someone else, and I just copied their config, without understanding. The part that I would like to know is where you get the name from for the :-
# Hauppauge Nova-T 500 dual tuner
options dvb-usb-dib0700 adapter_nr=2,3 force_lna_activation=1

I can see that, that is for the Hauppauge I had previously, but now with the TD ?  And no idea what to put for the TBS card (Also read somewhere that the TBS card does not support the nr=0,1 parameter?) Sorry if this sounds dumb but I feel a bit lost by so much conflicting information. Lastly I read and article on the TBS site about blacklisting one of the drivers so that they init in a specific order? So what would I put in the blacklist to say delay the Hauppauge?

Any solutions most welcome.

Paul

---

### Post by drifting on 2013-10-27
Actually semi solved this, I set the Hauppauge to 2,3 in the dvb.conf and let the TBS initialise first. Seems to have sorted it.

---

### Post by JasonEde on 2013-11-11
I had similar problem with freesat and freeview tuners changing place. Used a startup script to detect each tuner and make static links and used those links to tune by...

Used slightly hacked variant of [http://www.mythtv.org/wiki/Force_DVB_Card_Order](http://www.mythtv.org/wiki/Force_DVB_Card_Order).

---

