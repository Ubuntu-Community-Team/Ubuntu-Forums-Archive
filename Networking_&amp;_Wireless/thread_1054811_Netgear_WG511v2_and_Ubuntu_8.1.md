---
title: "Netgear WG511v2 and Ubuntu 8.1"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by iansmith87 on 2009-01-30
Hi all

Laptop - Compaq EVO n1015v with 768RAM attempting to use a Netgear WG511V2 PCI card for wirless networking.

I am a new user to Ubuntu.  I have previously (relunctantly used Windows) and previously (within the last year) started migrating to Mac OS X).  Having an old laptop lying around I decided to give Ubuntu a try.  My experience has generally been execellent - I like the interface and feel semi-comfortable navigating around the interface.

However, one thing is destroying my experience - the lack of working Wireless connectivity.

I have downloaded (via synaptics and the terminal for assurance) the latest wireless-tools.  I attempted to do the same with ndiswrapper but through both methods am told it doesn't exist, so I manually grabbed it using [http://packages.ubuntu.com/dapper/i386/ndiswrapper-utils/download](http://packages.ubuntu.com/dapper/i386/ndiswrapper-utils/download).

If I run the ```
lspci
``` command I am advised I have : Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03).

So having run ```
ndsiwrapper -l
``` before the driver is installed I get that the hardware is present (which matches with what the hardware testing suggests).  I then inserted the cdrom for my WG511v2 and navigated to the Drivers/Windows 2000 directory.  From here I ran ```
sudo ndiswrapper -i WG511v2.INF
``` with no errors reported. After this running ```
ndiswrapper -l
``` tells me that both hardware and driver are present (and if I remove the card only that the driver is present - excellent).  From what I have read I should now be able to run ```
sudo modprobe ndiswrapper
``` (although to be honest I don't understand what it does) and the lights should come on and I have connectivity - nada - no errors absolutely nowt...  I know this isn't windows and so as such no reboot should be necessary folloiwing these kinds of changes but I tried it just in case - still nada...

Also, from what I have read I should be able to run ```
ndiswrapper -m
``` to makethe change permanent and therefore no need to keep repeating these steps upon a reboot - however if I do run this command I advised something along the lines of this can't be done as the change has already been made.

I have tried downloading the driver, I have tried m8335 driver (having removed the Netgear driver first) but nothing.

I have checked /etc/modprobe.d/blacklist for the line ```
blacklist prism54
``` and it is there.  I have also added an additional line that is similar but for mv8335 (from memory) with no effect.

Can anyone help?  I am at the absolute limit of my Linux experience but would dearly like to keep on using it instead of Windows.


Ian

---

### Post by Crafty Kisses on 2009-01-30
Hey there, let's see if I can't help you a bit further! OK, so try running these commands, and installing this package:
```
sudo apt-get update
sudo apt-get install ndisgtk
```
So once you have that "ndisgtk" package, download your driver, you can get them from here: [http://kb.netgear.com/app/answers/detail/a_id/753](http://kb.netgear.com/app/answers/detail/a_id/753). Once you have the driver, save it to wherever you want, then open the folder where the driver is, and look for the ".inf" file, once you see the .inf file, open up a Terminal and run:
```
sudo ndisgtk
```
Then where it says "Install new driver" find the location of the .inf file, and then where it says "Install" click it, and see if that makes a difference, or gets your card up and running.

---

### Post by iansmith87 on 2009-01-30
Codename...

Many thanks for your swift response - I am at work now but will try later when I have access to the laptop in question and will update one way or the other.


Regards

Ian

UPDATE - WOW !!! All done and so easy - I really appreciate this.  If you don't mind me asking (and obviously you spending the time) what did ndisgtk do differently - what I read was that it was just a GUI for ndiswrapper - it seems like it must be more.  There are literally hundreds of postings on this topic and none of them worked except this one- which was a walk in the park.

It even has kept the config (something I had read that didn't happen).

Thanks again

Ian

---

### Post by Crafty Kisses on 2009-01-30
I'm glad that worked for you my friend. What you were doing would have still worked, but it's fairly complicated, I remember using Dapper and I had to ndiswrap my wireless card, it was a pain, but I was successful. Basically ndisgtk does it for you, I don't want to go as far as saying it automates the process, but it  definitely helps you. Ndisgtk is a GTK+ based frontend for ndiswrapper, allowing an easy way to install Windows wireless drivers.

So I'm really glad I could help you on this issue, and remember anymore problems please post back here on the forums.

---

### Post by Vasilis Primos on 2009-05-04
Dear Codename,
Your answer has helped both the originator and myself, possibly others too. Thanks a lot. Today I installed 9.04 and the wireless card can see my router but cannot connect. It worked fine with 8.10. In fact I repeated the same process just in case something got overwritten or deleted.
Looking forward to a suggestion. Thank you.

---

