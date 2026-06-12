---
title: "Atmt DVB USB Card Help"
date: 2009-11-11
forum: Mythbuntu
---

### Post by porker on 2009-11-11
Ok firstly i a complete linux and MythTV noob :p
 
I am trying to get the above card working under linux, it work fine under XP Pro.
 
I have done a bit of googling and the storry so far is a follows. The card when attached to the USB port requires a firmare according to dmesg. It says it is called dvb-usb-dposh-01.fw. I have downloaded this form the net and put it into /lib/firmware. dmesg then says that it has loaded the firmware but no frontend was attached. I cannot see the card in MythTV backend or kaffeine.
 
If i boot into windows first so the card is initialised then reboot into windows (the usb doesnt loose power) then the card is recognised and a Zarlink frontend is attached but i can not tune any channels.
 
I think i may have the wrong firmware for it but dont know how to get the correct one. I have recorded the transfer with SnoopyPro and the resulting logs are attached as are the reults of lsusb -v and dmesg from both the cold boot (i.e. card not recognised at all) and the post windows boot (card will not tune)
 
I get the feeling i am almost there with this but have completeley run out of skill/ideas etc etc.
 
Hope someone can help!!
 
I also have pictures of the card and its chips i can post but they are basically ULi M9206, MT352CG and a MT2060F
 
Thanks 
 
p.s. had to zip the dmesg files as i am at work on a windows box and they are too big for the forum.
 
The card can be seen here [http://www.scan.co.uk/Product.aspx?WebProductID=468748](http://www.scan.co.uk/Product.aspx?WebProductID=468748)

---

