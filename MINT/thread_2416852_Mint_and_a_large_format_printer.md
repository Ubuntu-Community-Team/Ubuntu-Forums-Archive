---
title: "Mint and a large format printer"
date: 2019-04-16
forum: MINT
---

### Post by dave6 on 2019-04-16
As I may be getting a large format printer "HP Z2100"  I have been thinking it over what is the best solution as it will have to be kept else where.

I have an old P4 Intel 2.66 ghz Celeron with an 80gb drive and about 2gb of RAM running Ubuntu some thing maybe K or Light. So it should run Mint 19, 32 bit OK.
I am thinking of using this computer as the gateway to the printer, ie, put all the photographs for printing onto a mem stick and put them onto the P4 computer and then using the network cable to the printer 

Is there any reason that will not work ?

Dave

---

### Post by DuckHook on 2019-04-16
Why bother with Mint, or any GUI for that matter? The HP Z2100 is supported by HPLIP, which, if memory serves me, is part of a default server install these days. If not, it is child's play to install it yourself (it's in the repos). So just do a server install (which should run quite nicely on that machine BTW), connect the printer, share it, and anyone can now access it from anywhere on your LAN.

Instructions [here]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") and [here]("https://help.ubuntu.com/lts/serverguide/samba-printserver.html").

[This]("https://ubuntuforums.org/showthread.php?t=310450") instruction thread is ancient, but it still works. \\:D/

---

### Post by DuckHook on 2019-04-16
I did not read your original post carefully enough. The printer is network capable? If so, why do you need an intervening machine at all? HPLIP will detect the printer (you must detect for it) and you can print from any Ubuntu machine on the LAN. In other words, you can put that memory stick full of pictures on any machine at all and printing will be a transparent procedure. Or is there some other quirk or difficulty about your layout?

---

### Post by dave6 on 2019-04-17
Hi DuckHook
Thanks for the reply, but when I said, "it will have to be kept else where."  Think of a cabin in the woods with only electric.

So it should work ? computer to printer..

Dave

---

### Post by dave6 on 2019-04-26
Oh dear, after searching the repos for the HP Designjet Z2100 drivers, there is none..  I am now at a lost of what to do with the printer, only got it home today and will be in house for 1 night before it has to be moved into it's working area

Dave

---

### Post by Autodave on 2019-04-26
Hook it up to what ever machine is available and see if Ubuntu recognizes it and can print to it.  Then, check to see if you can print on the larger paper: see if it has that option.

---

### Post by DuckHook on 2019-04-26
Ubuntu does not have independent drivers for each printer. In HP's case, it's done through HPLIP, a management utility that assigns the proper ppa description to the printer. [Here]("https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index") is the HPLIP [supported printer page]("https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index").

The z2100 does not show up, but the z1700 and z2600 are supported. Sometimes, choosing a close ppa is enough.

---

### Post by DuckHook on 2019-04-26
I note only now that you are using MINT. Can't help you there, as I don't know if the MINT devs have included HPLIP.

Also: *Thread moved to **MINT** as the more appropriate forum.*

---

