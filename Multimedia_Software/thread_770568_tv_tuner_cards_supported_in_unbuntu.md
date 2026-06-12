---
title: "tv tuner cards supported in unbuntu"
date: 2008-04-27
forum: Multimedia Software
---

### Post by billw11 on 2008-04-27
ok, im going to try ubuntu 1 final time....

im trying another project now.

im going the opposite direction here.
i never  thought id build a downgrade basic computer before.

i need to strip down this computer case , as im buying another system that requires a full size ATX board.
this case will hold it , but its coming apart as theres only a microATX board in it.

so im ordering a cheap small case for the micro.
ill rebuild it with an old 80 gig sata drive & a cd burner/dvd rom drive..
just very basic system...

i need to know which is the easiest/cheapest tv tuner card i can buy that ubuntu will support.
$40 range
a very cheap wireless card would be nice...

or do i put it together with just the HDD & cd burner alone,
install the server package, & let it act as my wireless access point until the whole thing frys ???

i have no problem with either option.
thanks for any input to this

---

### Post by ThinkDave on 2008-04-27
Ive got a dvico HDTV lite works perfectly (apart from HD which is a bit choppy and the AC3 is frustrating but haven't tried that lately might be fixed) dunno what price you can get them for now but i can recommend it as linux compatible basic card.

---

### Post by crossy on 2008-04-27
Hi Billw11,

Okay, first things first, if you going to use this box for a wireless access point, then I'd be tempted to choose something other than Ubuntu. From my experiences (and others at work), Debian (*upon which Ubuntu is based*) works pretty well and do you really need the extras that Ubuntu gives? Probably not. (*and no, I'm not trying to start a flame war about Ubuntu v's Debian - I have, and like, both*)

Okay, TV tuner cards. Hmm, best advice I can give is to head over to [http://www.linuxtv.org/](http://www.linuxtv.org/). The V4L and DVB projects give good compatibility lists. I've had a quick look at Newegg.com (can't use Pricerunner/Google because they spot where I am and give me a "local" version of the search - grrr!), and you've not any real choice for your $40 budget, especially if you want digital tv! You might want to try and scrimp another $10-15 to get something good. :-\"

From what I've seen, if your searching for a safe brand, then Hauppauge is the one to go for. This is especially good because their Windows software is just awful (*still*) - but check with LinuxTV before buying. :-k  In fact, if you've got hardware and are looking for a use - while you're at LinuxTV have a look at the VDR project - might be interesting for you?

If it's any help, here's the results of my own unofficial survey.
Hauppauge PCI Win-TV (analog only) - works, not tested extensively; 
Freecom DVB USB - works very well;
Hauppauge Nova-TD DVB-Diversity USB - works, but the reception sucks;
Pinnacle Dazzle Hybrid - can't get DVB working on this, analog works, but it needs a roof or amplified aerial.

Hope this helps,
 crossy.

---

### Post by Vic Morgan on 2008-05-04
crossy, You say that the Freecom usb stick works well. For the life of me I can't find any instructions on what to install and how! Is there a Howto for installing this stick (one that works anyway). Whick package runs it, and how do you get it running? Thanks

---

