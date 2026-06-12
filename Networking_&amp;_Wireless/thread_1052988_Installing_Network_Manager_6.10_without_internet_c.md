---
title: "Installing Network Manager 6.10 without internet connection"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by itgoodson on 2009-01-28
Hiya

Complete newbie when it comes to Linux. Tried installing 8.04 on an old desktop PC, it ran nicely but Network Manager could not connect to wireless internet. I tried installing WICD, which connected, but after two minutes of connection the whole system froze up.

I read somewhere that 6.10 worked ok with my wireless USB card (Linksys WUSB11 ver 2.6). So I have now installed 6.10... but I have found out that Network Manager isn't installed as default!

I know the basic way of getting it installed is to just download it using sudo apt-get install. But I don't have any way of connecting the machine to an internet connection (it's a bit of a botch job PC without an ethernet port).

All I have for internet access is my MacBook (running OSX)

So I need a way to be able to download NetworkManager to the mac, stick it on a thumb drive, then move it across to the Ubuntu machine.

Can anyone give me simple, newbie friendly instructions... please!!!!

CHeers

Ian

---

### Post by steeleyuk on 2009-01-28
6.10 is over two years old and completely unsupported now. The repositories won't be available now.

You could try 8.10, thats your best bet and then trying to solve the problem from there.

Network Manager was introduced in Ubuntu at Feisty (7.04).

You might also be better finding a cheap Ethernet card and connecting the box up, would make things a little easier.

---

### Post by itgoodson on 2009-01-28
Thanks steeleyuk for that info

- when you say it is unsupported now, how much of a problem is that likely to be? Because all I want is a straight forward desktop to use for openoffice and internet - nothing flashy! And if 6.10 works with my wireless USB adaptor (the Linksys WUSB11 ver 2.6) - as people online say it does - then I'd be happy with 6.10...

I've managed to download Network Manager as a .tar.gz file... but I have no idea how I then install that on Ubuntu. I've read somewhere that Ubuntu prefers .deb files. Anyone know how to get .deb file for NetworkManager?

Cheers

ian

---

### Post by itgoodson on 2009-01-28
Right... I have been doing some more reading. I've found and downloaded a .deb file for Network Manager. But I doubt it's going to work (once I get home to the PC - I'm currently at work) because I guess there will be a whole list of dependancies.

But I have figured out that I can just set up wireless networking in Ubuntu 6.10 without NetworkManager... can someone give me simple instructions on how to do this? Will I need to know my SSID and so on...

Cheers

Ian

---

