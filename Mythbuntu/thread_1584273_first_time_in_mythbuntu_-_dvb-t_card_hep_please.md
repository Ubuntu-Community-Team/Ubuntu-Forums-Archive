---
title: "first time in mythbuntu - dvb-t card hep please"
date: 2010-09-28
forum: Mythbuntu
---

### Post by cobelloy on 2010-09-28
Hi, I need some help please, I have ubuntu 10.04 with mythbuntu installed via synaptic, and this capture card:

02:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)
	Subsystem: Hauppauge computer works Inc. Device 8980
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f6000000 (64-bit, non-prefetchable) [size=4M]
	Memory at f6400000 (64-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>
	Kernel driver in use: saa7164
	Kernel modules: saa7164
I followed these instructions to the best of my ability:

[http://ubuntuforums.org/showthread.php?p=9638315](http://ubuntuforums.org/showthread.php?p=9638315)

but the card doesnt work, I dont know enough about this stuff to work this out on my own and my windows installation has completely died with viruses hence the mythbuntu

I have some linux experience - but not extensive

thanks!

---

### Post by cobelloy on 2010-09-29
OK, I think I got it!

If I understand correctly, you have to set up some sort of guide and scan for channels first before myth will let you watch TV

for australian IceTV guide users there is a great tutorial supplied by ice here:

[http://www.icetv.com.au/cgi-bin/websupport.cgi?op=show_faq&faq_id=70&faq_cat_id=18]("http://www.icetv.com.au/cgi-bin/websupport.cgi?op=show_faq&faq_id=70&faq_cat_id=18")

so far I have all the 7's, ABC's ONE's and Ten digital, but I did not complete the last step so I think I can add the missing FTA channels manually - will post again

YAY for myth TV

---

### Post by funkydan2 on 2010-09-30
Hey Cobelloy, that's great to hear.

Unless you've already paid up, you might be interested in using Shepherd ([http://svn.whuffy.com/](http://svn.whuffy.com/)) rather than IceTV for your TV guide data. Shepherd works by grabbing the data from a bunch of websites, and then combining the data to get the best EPG it can. Best of all, it's free.

---

