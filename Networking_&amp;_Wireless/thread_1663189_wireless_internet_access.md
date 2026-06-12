---
title: "wireless internet access"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by grahambrookbanks on 2011-01-09
I'm really new to Ubuntu and not very technical.  I bought 'LINUX The Complete Manual' and was convinced of the advantages over Windows.

I installed a new hard drive in my old Dell Dimension 3100 computer and loaded Linux. I've upgradaded to v10.10, The Maverick Meerkat (whatever that means!)

The wireless internet card didn't seem to work, so following advice in the LINUX Manual I bought a cheap Wireless LAN USB dongle. It's a Cisco RangerPlus Wireless Network USB adaptor.

As soon as I plugged it in I got a connection to my 2WIRE891 router, but web pages seem slow to load and the connection keeps dropping.
There was a bewildering choice of USB adaptors.  Should I have chosen a more expensive one? Would that improve speed and connection stability? Would an internal card be better?  Can you recommend a particular device?
Please help!
Thanks

---

### Post by PatchesTheCaveman on 2011-01-09
Go to Applications > Accessories > Terminal and type each of the following commands, pressing Enter after each one:
```
sudo lshw -C network
sudo iwconfig
```
You'll be asked for your password after you run the first command.  Type it in and press Enter.  It won't show dots or stars or anything, but it will work.

Once you've done that, copy and paste the output to a reply to this thread.  That will give us information about both your wireless card and USB dongle that we can use to either get the former working or make the latter work better.

---

### Post by grahambrookbanks on 2011-01-10
Thanks for your assistance, Patches.
Since I posted my question, Ubuntu failed (I just got a load of text which I didn't understand on startup)  I hadn't got round to creating a back-up disk, so I had to re-install Ubuntu from scratch.  Since then my internet connection seems stable and quick, so I don't need to try any fixes at the moment. I've saved your instructions in case I get any more problems.
Thanks again for your prompt help.
Graham

---

