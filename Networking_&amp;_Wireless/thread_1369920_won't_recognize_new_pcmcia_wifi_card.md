---
title: "won't recognize new pcmcia wifi card"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by billrosenblatt on 2010-01-01
I got a new EDUP Wireless Lan PCMCIA Adapter to replace a busted SMC wifi card.  I am running Ubuntu 9.10 on a Dell laptop.  The OS will not recognize the new card. Here is some output:
 
billr@GB-Dell:~$ pccardctl status
Socket 0:
  no card
Socket 1:
  3.3V 32-bit PC Card
billr@GB-Dell:~$ pccardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available
billr@GB-Dell:~$ pccardctl info
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

Any ideas what to do?  Would appreciate any help!

---

### Post by apaschou on 2010-03-01
Hi,

I don't know if it is good news, but on my side, with also EDUP wireless PCMCIA card and same ubuntu, I managed to go a bit further... I can now see the available networks. But I am still unable to connect to them. Nevertheless, here are the steps I needed to perform to reach that state:

STEP 1:
Install windows driver using ndiswrapper. To do that, I used the included CD with windows drivers and used the ndiswrapper from ubuntu. So I simply used the command:

```
sudo ndiswrapper -i nds_pilote.inf
```

where nds_pilote.inf is the .inf file I found on the windows install CD.

Then, reboot the machine. I you have luck, you should at least see that you have a wirless card. I had no luck on my side and needed to do an additionnal operation:


 	Code:
 	gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf 
when it opens,  put a # in front of the last line (blacklist ath_pci),  so that it looks like this:

 	Code:
 	#blacklist ath_pci 
then save and close the file. Restart the PC.

At that time, I can see the wirless networks in the user interface on the right part of the top bar. I can see all available networks.

But now, I am stucked at the next step: when I want to connect my network (with WEP key), nothing happen...

Regards.

---

