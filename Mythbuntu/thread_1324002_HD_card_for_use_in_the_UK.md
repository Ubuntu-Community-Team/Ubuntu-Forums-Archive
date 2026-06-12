---
title: "HD card for use in the UK"
date: 2009-11-12
forum: Mythbuntu
---

### Post by gwagchunks on 2009-11-12
Hi

Just wondering what capture cards (if any) are available that support HD (for the UK market) and work in mythbuntu.

Thanks

---

### Post by SiHa on 2009-11-12
If you're talking Freesat, then the Hauppauge Nova-S works. It's quite old now, and only DVB-S (as opposed to DVB-S2, which is supposedly coming soon). 

I bought mine off eBay, it is identical to this one, and from the same seller:
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=260464659015](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=260464659015)

It was quite easy to setup, if you get one, give me a shout if you like. Getting the frequency right for the initial scan was a bit tricky.

And I've found it likes to swap ID's with my Nova-T 500. Will be experimenting with a fix this weekend.

At the moment, I've only got BBC-HD. 0.22 supposedly works for ITV-HD as well, but I had to abort the channel scan early, and missed it. There's next to naff-all on it anyway, so I'm not bothered. 

The picture quality on BBC-HD though is excellent.

For a first 'toe-dip' into HD, it's a cheap option, that's why I did it. The whole lot, card + dish came to less than £45.

Edit: Note that HD recordings use 6GB/hr!

---

### Post by byronmyth on 2009-11-12
I've got the NOVA-HD-S2 working (BBC HD), be aware that you will need a pretty quick video card, Nvidia Geforce, preferably 8600 or 9600 to get the best results, although I've used the 8300 which was 95% good too. I can confirm that MythTV 9.10 does display ITV HD, you just have to scan for it using "ALL" rather than TV, then edit channel name, it finds it as 10510 is seem to remember. Not that ITV-HD show much, barely one thing a day, good for the odd football match though.
 
I've the same issue as SiHa with the id's of the two Hauppauge cards swapping, so be aware of that.

---

### Post by Neon Dusk on 2009-11-12
> **byronmyth said:**
> 
..
 
I've the same issue as SiHa with the id's of the two Hauppauge cards swapping, so be aware of that.

To fix DVB cards swapping adapter numbers see :-
[thread=1311795]Force order of allocation of DVB frontends[/thread]

---

### Post by SiHa on 2009-11-12
> **byronmyth said:**
> ...you will need a pretty quick video card, Nvidia Geforce, preferably 8600 or 9600 to get the best results, although I've used the 8300 which was 95% good too.

I've got an 8200 IGP, and the CPU (Dual-Core Athlon II 3GHz) bearly breaks into a trot @18%. That's using the VDPAU slim profile, and TBH, I don't notice any improvements with either of the other two.

---

### Post by gwagchunks on 2009-11-12
Thanks everyone. I've not got a HD Tv yet, but maybe next year, and now I know what will work in Myth. Also that PCI swapping patch will come in useful. Thanks again.

---

