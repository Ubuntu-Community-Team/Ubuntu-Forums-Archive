---
title: "Wireless connection after minimal install of Intrepid"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by johnny2m on 2009-01-12
I've just done a minimal install of Ubuntu and am really pleased with the speed, but now my wireless card is not recognised.

It's an Edimax EW-7108PCg (RT2500 or RT61 I think??).  I've had Xubuntu Hardy and Intrepid on this laptop and with both of those the wireless setup just worked.  So obviously the minimal install is not adding something I need, I just don't know what!  In fact, I've just noticed my USB PCMCIA card is not recognised either, so maybe I'm missing a few things?!

Since the install, the only things I've added were:

sudo apt-get install xorg xterm icewm menu gksu synaptic kazehakase xfe

The setup is very basic but perfect for the hardware (only 650MHz with 192MB RAM).  I really don't want to have to go back to Xubuntu unless I have to!

Any ideas?? :confused:

---

### Post by johnny2m on 2009-01-15
Okay, it's working now.  I installed wicd, but couldn't understand why it wasn't picking up my wireless card.  Then I added wlan0 in manually and everything came alive:guitar:!

---

### Post by jwathome on 2009-01-21
Hi,

I'm also struggling with getting my edimax card operational under Ubuntu. Would much appreciate if you could explain what type of actions you've undertaken to make yours work (i.e. step by step including commands).

Many thanks

---

### Post by johnny2m on 2009-01-21
Hi,

I'm rather a n00b myself but will try to explain as best I can.  Also, not sure exactly where you're having the problem, i.e. whether the card is not recognised at all or whether it is recognised but just doesn't want to connect to your router?

Firstly, I would say getting things to work depends very much on what version of Ubuntu you're running.  I couldn't get my card working with 7.10 at all (there was an option of compiling the driver from source I think but I never got it working), it was only with 8.04 and then 8.10 that it sprang to life.  I think they included the driver for the card in the 8.04 kernel so it basically just worked 'out of the box' (I may be wrong about it being in the kernel, but it was definitely there somewhere!).  Unfortunately I don't have Xubuntu installed any more so I can't give you the specifics, but it recognised the card without need for further configuration and it was just a case of putting in the wep code and it was off and running.  I'm still not sure what chipset my card has, RT2500 or RT61, but google your own model as if it's a different chipset it could be that the driver is not included in the install, which makes things a whole lot more complicated!

My most recent problem was after a minimal install of 8.10.  Basically, I just didn't know how to get to my network settings.  I started by installing wicd, which is a network manager.  You can either search for wicd in Synaptic Package Manager or run:

```
sudo apt-get install wicd
```

Then, to run the client program:

```
wicd-client
```

I'd do a screenshot but I can't quite figure out how to do it at the moment :redface:

Anyway, in Wicd Manager go to Preferences and make sure that the Wireless Interface field has "wlan0" in it.  After that, click on Refresh and you should see your wireless connection appear, then you need to connect and input your WEP/WPA code.

Hope this helps!

---

