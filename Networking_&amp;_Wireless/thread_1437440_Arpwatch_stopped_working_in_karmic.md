---
title: "Arpwatch stopped working in karmic"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by rlcarr on 2010-03-23
I'm running Karmic.  Sometime in the past month or so (perhaps when I upgraded to karmic!) arpwatch stopped working.  It immediately exits with 
> Link layer type 189 not ethernet or fddi

But running "arp" shows what it should.  And when I run wireshark and see an arp request/reply it says the hardware type is type ethernet (0x01).

???

(I've tried googling on "Link layer type 189" -- with quotes, and there are zero matches)

Any ideas?

---

### Post by rlcarr on 2010-03-23
And just to be clear -- absolutely **nothing** has changed hardware-wise since it was working.  Exact same ethernet card, switches, router, other machines, etc.

---

### Post by capscrew on 2010-03-23
> **rlcarr said:**
> And just to be clear -- absolutely **nothing** has changed hardware-wise since it was working.  Exact same ethernet card, switches, router, other machines, etc.

This may be a PCAP problem.  See [**_here_**]("http://www.sfr-fresh.com/unix/misc/arpwatch-NG1.7.tar.gz:a/arpwatch-NG1.7/arpwatch.c").  A search for the entire phrase reveals:

[FONT="Courier New"][COLOR="RoyalBlue"][I]308 	**/* Must be ethernet or fddi */**
  309 	linktype = pcap_datalink(pd);
  310 	if(linktype != DLT_EN10MB && linktype != DLT_FDDI) {
  311 		fprintf(stderr, "%s: Link layer type %d not ethernet or fddi", prog, linktype);
  312 		exit(1);
  313 	}
[/I][/COLOR][/FONT]

---

### Post by rlcarr on 2010-03-23
I got it to work.  I had to change /etc/defaults/arpwatch to add:
   > -i eth2
to the argument list.  And then the error was no longer logged to syslog and it started picking up all the arps and sending out email.

This is bizarre because my ethernet card has been eth2 for well over a year.  And as I said, until sometime this February arpwatch worked fine.

I guess something changed in karmic with respect to what the kernel reports to programs like arpwatch when they ask for the default interface?

---

