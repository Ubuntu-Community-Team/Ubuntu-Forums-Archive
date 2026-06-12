---
title: "USB port to get internet 2Wire Gateway"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by winterlove on 2009-05-03
Well I have ubuntu 9.04 and ubuntu 8.10 running on this machine... No ethernet port available, so I need to use the USB port to get internet... I have the Windows driver but there is not a driver for linux... 

So. Is there a way (like ndiswrapper) to use this driver on my ubuntu machine?  

If there is... can somebody explain me how to do it...???
Please... 

Thanks.

Edit... I did what is needed to do to use NDISWRAPPER

installed It and 
and installed driver too... 

# ndiswrapper -i 2WirePCP.inf
# ndiswrapper -ma
# modprobe ndiswrapper

here I get the following Message

WARNING: All config files need .conf: /etc/modprobe/ndiswrapper, it will be ignored in a future release.

And After this I haven't got to do anything more... I dont know what it means or how to solve It.


I installed mandriva in my other computer and I just had to do the 

#sudo modprobe ndiswrapper 

and network manager connected automatically connected my usbport to the gateway and grabbed Internet. I didnt got the message Avove in mandriva... so I gess that message is what doesnt let me connect to internet in Ubuntu... how do I solve It.

I want ubuntu and not Mandriva... Is an old PC that runs better with Ubuntu.

If somebody can help me, I would Apreciate It

---

### Post by winterlove on 2009-05-08
Somebody Please... what is the error??? how do I solve it???

---

