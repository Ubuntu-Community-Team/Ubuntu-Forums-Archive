---
title: "T-Mobile Web n Walk USB dongle"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by jdb91 on 2009-07-16
Just wondering if this is working on anyone's laptop? T-Mobile assured me it would work (ofcourse, no actual support).

Just wondering if anyone has any tips?

Ta

---

### Post by solitaire on 2009-07-16
The dongles should work...

I've a "3" 3g dongle (uk) all i needed to do was plug it in and it was recognized as a "Mobile Broadband" connection. Had to to a bit of tweaking to get it to connect (the wizard had a different APN address). But a few seconds later i was surfing away.

---

### Post by ibutho on 2009-07-16
> **jdb91 said:**
> Just wondering if this is working on anyone's laptop? T-Mobile assured me it would work (ofcourse, no actual support).

Just wondering if anyone has any tips?

Ta

I have used the Huawei E160 from T-Mobile UK with Ubuntu and other Linux distros. It just worked out of the box and all I needed to do was select the network provider in NetworkManager. The Huawei E156 and E169 also work with Linux.

---

### Post by jdb91 on 2009-07-16
i was hoping mine would work like that, but it doesn't seem to be

---

### Post by ibutho on 2009-07-16
> **jdb91 said:**
> i was hoping mine would work like that, but it doesn't seem to be
What make of modem is it and which T-Mobile network (UK, US etc).

---

### Post by jdb91 on 2009-07-17
It's on T-Mobile UK and it's the Web'n'Walk 150. I think it is recognising it, I can see device pan0, which i can't think what else that could be?

---

### Post by ibutho on 2009-07-17
> **jdb91 said:**
> It's on T-Mobile UK and it's the Web'n'Walk 150. I think it is recognising it, I can see device pan0, which i can't think what else that could be?

What version of Ubuntu are you using? In 8.10 and 9.04, just plugin the modem, run NetworkManager, go to the Mobile Broadband section and choose T-Mobile UK.

---

### Post by jdb91 on 2009-07-21
> **ibutho said:**
> What version of Ubuntu are you using? In 8.10 and 9.04, just plugin the modem, run NetworkManager, go to the Mobile Broadband section and choose T-Mobile UK.


i'm using 9.04, im doing that with network manager, but that's as far as i get

---

### Post by jdb91 on 2009-08-04
This is what I see but i can't get further. I think i need some drivers, what is the real model of the T-Mobile USB 120

[IMG]http://img195.imageshack.us/img195/2774/donglek.png[/IMG]

---

### Post by statham on 2009-10-01
Hi, I'm running the Netbook Remix 9.04 on a Dell Mini 9. Trying to use a T-Mobile 530 USB stick, but it only recognises it as a CD. How do you get it to recognise the stick as a modem?

---

### Post by theozzlives on 2009-10-01
If you left click on Netwoork Manager the option should be there.

---

### Post by statham on 2009-10-01
No sign of dongle when I left click the network manager. I can right click and manually install t-mobile broadband connection but you don't need the dongle to do that. The problem seems to be that the dongle comes with zeroCD web n walk software installed on an in built memory stick so ubuntu sees the device as a CD and fails to recognize the modem part. This has happened with other makes but I don't know how to make ubuntu see the modem and not the disk files. Any ideas gratefully received. Thanks

---

### Post by terry_gardener on 2009-10-03
to get the t-mobile 530 working follow the instructions i have placed in the following thread. 

[http://ubuntuforums.org/showthread.php?t=1202391&highlight=t-mobile+530]("http://ubuntuforums.org/showthread.php?t=1202391&highlight=t-mobile+530")

---

