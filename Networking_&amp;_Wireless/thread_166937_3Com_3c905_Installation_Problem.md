---
title: "3Com 3c905 Installation Problem"
date: 2006-04-27
forum: Networking &amp; Wireless
---

### Post by ds_shellback on 2006-04-27
Hi,

Firstly, I'm new to ubuntu and perhaps the hardware I have is just too old.

Ok I've read thru several threads but I still can't get ubuntu to configure my 3Com 3c905 network card either with the live CD or the install CD.

On install all the LED indicators on the rear of the card go OFF at the point detecting network and then the whole install hangs at configuring DHCP.

If I physically remove the network card prior to install then it's fine - but no network of course.

Tried editing files post install and after replacing network card as follows, but then it locks up on reboot at the point loading module networking. At this point the card is listed in the ubuntu device manager! - so the system sees it.

/etc/modules
added:-
3c905

/etc/network/interfaces
added:-
auto eth0
iface eth0 inet dhcp

I've read other threads relating to 3c905 problems but none seemed to relate directly to this problem.

Any suggestions??.

Regards,
David.

---

### Post by az on 2006-04-27
Isn't it 
3c509?

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=3c509.ko&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=3c509.ko&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

versus

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=3c905.ko&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=3c905.ko&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

---

### Post by Iowan on 2006-04-27
[QUOTE=azz]Isn't it 
3c509?
[/QUOTE]
Interesting question - Breezy didn't like my '509 (ISA) cards, but does that mean '905s (PCI?) are unsupported - or should work out-of-the-box?

---

### Post by ds_shellback on 2006-04-27
hi,

The full 3Com part# is 3C905CX-TX-M it's NOT 509 if that's any help. The system was previously running Win 98 (with the useual flakyness) but I know the hardware is basically ok.

---

### Post by ds_shellback on 2006-04-28
Ok, tried the following approach:-

1.	Re-installed ubuntu without the 3C905 NIC fitted.
2.	After install modified the etc/modules file to add 3c59x (Realised this was the correct driver for the 3Com 3c905 – tornado)
3.	Rebooted
4.	In the networking panel the interface is shown but listed as not active – so configured for DHCP and click ok.

Now for the crunch – select the interface and click activate!

The system just freezes at this point even the cursor stops’ doing it’s round and round thing.

Anyone any thoughts on this I should I abondon it in favour of another NIC

---

### Post by ds_shellback on 2006-05-02
Ok,

Finally found the cause of the problem.

Motherboard is pcChips - buried away in one of the bios setup pages is a setting called "Plug and Play aware OS". Setting this to "NO" fixes the problem.

Many thanks to those who replied.

---

