---
title: "Huawei dongle so new Ubuntu doesn't recognise it"
date: 2011-07-09
forum: Networking &amp; Wireless
---

### Post by hamstermoon on 2011-07-09
Hi,

I posted a similar post in the Newbie thread but having not had any response I thought you guys might know more.

I have a Huawei e353 mobile wireless USB from 3 and apparently it is so new there isn't even a driver for it. Any ideas what I should do so I can actually use it with my Ubuntu notebook or am I going to have to hang around until someone patches a fix?

---

### Post by alexfish on 2011-07-10
Hi

try visiting the usb modeswitch forum

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

[ModeSwitchForum]("http://www.draisberghof.de/usb_modeswitch/bb/")

alexfish

---

### Post by hamstermoon on 2011-07-10
Woah. That is well over my head as a newbie :( I think I shall just have to sit this one out until someone makes an easy way round with a patch!

---

### Post by Plumtreed on 2011-07-10
Hang on, what steps have you taken so far?

I am just back from the UK and used 3 and 'a recent dongle' supplied by them which worked out-of-the-box. It worked so well I don't remember much about it and I gave it to a family member before I returned to Oz.

I am running 10.04.....I used the NetworkManager Applet, right click, Edit Connections, Mobile Broadband, Add..........follow the steps.

---

### Post by hamstermoon on 2011-07-11
How long were you over here? I was told by the man in the shop that it was 'new in the last two weeks' and therefore probably not supported.

I did try the network manager thing and didn't get anywhere with it. Perhaps I should have another go and see if I can get it to go.

---

### Post by hamstermoon on 2011-07-11
Nope, tried that and it still isn't even seeing it ...

---

### Post by Plumtreed on 2011-07-11
Just back but there was no talk about the 'dongle' being new and there have been a lot of new developments in this area.

Is the APN set at..... 3internet       or you could try ....3netaccess

other than that I dunno:confused:

---

### Post by hamstermoon on 2011-07-12
Well strangely enough I got Jolinar (my back-up Fujitsu Siemens Amilo laptop) who runs Maverick and guess what? It works. \\:D/

Now to work out why Mint isn't doing what it should, and to try dual booting Xbuntu onto nubin the notebook and see if that works. [-o<

---

### Post by Plumtreed on 2011-07-12
.....make sure you have 'usb-modeswitch' and 'modemmanager' installed.

---

### Post by hamstermoon on 2011-07-12
I have just checked and I have them installed on Xbuntu and Mint. 

Now I have plugged and unplugged a few times  it does seem that nubin the notebook (an MSI Wind U230) maybe the problem. It's recognising usual USB sticks I put in there, just not the 3 Dongle.

---

### Post by hamstermoon on 2011-07-14
Neither of them worked so I followed a hunch and dropped back to 10.10. Now the dongle DOES work. Has anyone any idea why Natty has killed it and Maverick lets it work perfectly?

---

### Post by nirvblakr on 2011-12-14
> **hamstermoon said:**
> Well strangely enough I got Jolinar (my back-up Fujitsu Siemens Amilo laptop) who runs Maverick and guess what? It works. \\:D/

Now to work out why Mint isn't doing what it should, and to try dual booting Xbuntu onto nubin the notebook and see if that works. [-o<

Hi!  How were you able to make the E353 to work in Maverick?  I was presently running Linux Mint 11 when I have read the issues with the E353.  I read in your post that you were successful in running it Maverick.  I have just installed Linux Mint 10 and have updated everything.  Under the network icon when I click it, the name of my ISP is present but greyed out.  I tried to make a new profile with the same provider and afterwards the profile appeared in my network connections but upon clicking it a window on the upper left corner appears "GSM disconnected".  Any workaround/solution to this? TIA :)

---

