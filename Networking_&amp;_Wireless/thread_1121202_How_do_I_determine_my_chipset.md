---
title: "How do I determine my chipset?"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by CynicalPsycho on 2009-04-09
i'm running an intel(r) wifi link 5100 agn.
and I can't for the life of me figure out what chipset i'm running...
could anyone help me out here?

---

### Post by bertolo on 2009-04-09
that's kind of a stupid question. we can only help you googling. and googling it's what you should have done before asking.

apologise:when i said your question was stupid, i didn't mean it and i do not have intention to hurt noone.
i am sorry for the miss understood.

---

### Post by chili555 on 2009-04-09
> **CynicalPsycho said:**
> i'm running an intel(r) wifi link 5100 agn.
and I can't for the life of me figure out what chipset i'm running...
could anyone help me out here?Open up a terminal and type:```
sudo lshw -C network
```Your ethernet and wireless devices will be shown. Opposite *product*, you will find the information you need. Search this forum and you will see a few people that have made it work. Post back if you get stuck.

---

### Post by bertolo on 2009-04-09
googling it's much more obvious

---

### Post by calvinps on 2009-04-09
> **bertolo said:**
> googling it's much more obvious

Googling is unreliable, though. And if he tried a command from a fake site, his computer would crash.

:|

---

### Post by bertolo on 2009-04-10
> **calvinps said:**
> Googling is unreliable, though. And if he tried a command from a fake site, his computer would crash.

:|

AHAHAHHAHHAHAAH
are out of your mind ?
i use google 200 times a day everyday and never get that computer crash. ROTFL

just go to manufacturer's website

---

### Post by tturrisi on 2009-04-10
Um...all Intel devices have Intel chipsets.
Yours has the Intel 5100 chipset!

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

---

### Post by CynicalPsycho on 2009-04-10
> **chili555 said:**
> Open up a terminal and type:```
sudo lshw -C network
```Your ethernet and wireless devices will be shown. Opposite *product*, you will find the information you need. Search this forum and you will see a few people that have made it work. Post back if you get stuck.thanks chili here's what i got from it for my wifi... 

> description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: xxxxxxx
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=xxxxxxxxx latency=0 module=iwlagn multicast=yes wireless=IE
good info there (and glad i learned that command) but unless i'm mistaken (am i mistaken?), not the info i'm lookin for.

---

### Post by lisati on 2009-04-10
lspci and dmidecode are also useful for figuring out what's "under the hood"

---

### Post by CynicalPsycho on 2009-04-10
> **tturrisi said:**
> Um...all Intel devices have Intel chipsets.
Yours has the Intel 5100 chipset!

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)
Hmmm that seems almost too easy... heh, thanks. Curious though, where did you determine this?


also... I checked out the site, but wasn't sure why it was pertinent. Could you explain?

---

### Post by CynicalPsycho on 2009-04-10
> **bertolo said:**
> that's kind of a stupid question. we can only help you googling. and googling it's what you should have done before asking.
> googling it's much more obvious
Obviously this is the first thing I did... I wouldn't just come to a forum blindly asking a question without putting in at least a little effort myself. Infact I'd much rather discover the answer myself than have someone else give it to me. But in this case after about an hour of looking, google couldn't come through for me. which is why I came here. OBVIOUSLY...

You know you seem like a real smart guy with all your pompous arrogance, so why don't you put those smarts to use by actually helping people instead of being a demeaning ******* who ignorantly makes baseless assumptions so as to make himself look 'cool' on the internet.

Yes dumdum, everyone knows to use google... but even google doesn't have all the answers all the time. If it did, people wouldn't need forums like this...

---

### Post by CynicalPsycho on 2009-04-10
> **lisati said:**
> lspci and dmidecode are also useful for figuring out what's "under the hood"

thanks man... I always love learnin this new stuff.

---

### Post by chili555 on 2009-04-10
> **CynicalPsycho said:**
> thanks chili here's what i got from it for my wifi... 


good info there (and glad i learned that command) but unless i'm mistaken (am i mistaken?), not the info i'm lookin for.All there is to know about your chipset is:> product: Wireless WiFi Link 5100
vendor: Intel CorporationI suggest both an advanced search here for 'Intel 5100 packet injection' as well as an advanced search for the same terms on Google. I don't know for sure, but my guess is packet injection does not work with your chipset. If I am right or wrong, please post back and tell us so the searchers can find it.

---

### Post by DirtDawg on 2009-04-10
FYI, check out Sysinfo if you haven't already. It's in the repositories and is a simple but well designed little GUI app that displays your system information (including hardware).
```
sudo apt-get install sysinfo
```

---

### Post by CynicalPsycho on 2009-04-10
> **chili555 said:**
> All there is to know about your chipset is:I suggest both an advanced search here for 'Intel 5100 packet injection' as well as an advanced search for the same terms on Google. I don't know for sure, but my guess is packet injection does not work with your chipset. If I am right or wrong, please post back and tell us so the searchers can find it.

Injection does not work with that card. I just bought a Linksys wireless n usb network adapter wusb6000n. it's got a RT2870 chipset which is so maybe it'll give me better luck than the previous... and if not... i'll take advantage of bestbuys return policy :P.

I'll post if I have any luck.

---

### Post by lensman3 on 2009-04-11
It is easy!

Do a lspci and find the card/device you need to identify.  The report will start with a number like 00:1f.3.  Remember this number. Then run "lspci -n"
and using the remembered number you will find another number with the format of xxxx:yyyy.  Take this number and enter it into google along with the card manufacture (if you know it).  This number is the "assigned" pci device number from "whomever assigns pci numbers".  

For instance on my machine the lspci -nn
4:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
has this for the result of my Ethernet card.  The number 10ec:8168 is unique for this card

"lspci -nn" will also tell you more about the device/card.

See if somebody on google has already had the same problem and has fixed it.

Hope this helps.

---

### Post by CynicalPsycho on 2009-04-11
PERFECT!
thanks!

> **lensman3 said:**
> It is easy!

Do a lspci and find the card/device you need to identify.  The report will start with a number like 00:1f.3.  Remember this number. Then run "lspci -n"
and using the remembered number you will find another number with the format of xxxx:yyyy.  Take this number and enter it into google along with the card manufacture (if you know it).  This number is the "assigned" pci device number from "whomever assigns pci numbers".  

For instance on my machine the lspci -nn
4:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
has this for the result of my Ethernet card.  The number 10ec:8168 is unique for this card

"lspci -nn" will also tell you more about the device/card.

See if somebody on google has already had the same problem and has fixed it.

Hope this helps.

---

