---
title: "High-Speed Home Wireless Suggestions"
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by tom purl on 2006-01-17
Hi.  I currently have the following wireless setup in my home:

```
router - wireless G
main (desktop) computer - wireless B nic
backup (desktop) server - no wireless card
```

This works pretty well for browsing the web, but I would like to setup my network so I can start making backups on my backup server and possibly use it as an NFS/Samba server.  

It's my understanding that I'll probably want to install wireless G cards on all of the computers in my network if I'm going to start doing a lot of file io between them.  So here are my questions:

1. Is anyone doing anything like this with wireless B?  I do incremental backups, so on average I'm only moving a couple of megs a day.  However, if I need to regenerate my backups, I would need to move 40+ GB, and some days I have to move a couple of gigs.  I do my backups early in the morning, so it's ok if the backup takes multiple hours if necessary.

2. What are some recommendations for good, mid-priced wireless g cards?  I'm having a lot of problems finding a current list of cards like this.  Are you using a wireless G card that you particularly like?

3. Is anyone doing anything like this with a usb nic?  I've always been partial to PCI cards due to past issues. However, if usb nics are working well for any other Ubuntu user, then I might look into them since they're so cheap and easy to work with.

Whew!  I guess that's it.  Any help at all on any of my questions would be greatly appreciated!

Tom Purl

---

### Post by tktreload on 2006-01-17
The linksys WRT-54G is an eccelent piece of hardware. It just works. and its not the most pricy on the marked.

---

### Post by healychan on 2006-01-17
Haven't you check this list from wiki. They list all the cards supported by Ubuntu.

I had a bad experience with PCMCIA card on Ubuntu. I am now using USB adapter. However, to be fair, Ubuntu supports many PCMCIA cards very well but I am just the unlucky one.:( 

I had the problem because ndiswrapper dosen't fully support my PCMCIA card, I hope the newer version will have an improvement.

---

### Post by Azion on 2006-01-17
I'm using Netgears WPN range, nice speed.
Using MadWifis drivers.

There's a newer n format on the horizon for the last few months.
So you might be better off waiting for that

---

