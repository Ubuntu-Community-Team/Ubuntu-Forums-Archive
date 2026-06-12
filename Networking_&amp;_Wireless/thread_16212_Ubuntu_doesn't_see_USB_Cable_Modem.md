---
title: "Ubuntu doesn't see USB Cable Modem"
date: 2005-02-20
forum: Networking &amp; Wireless
---

### Post by TestDummy! on 2005-02-20
Okay, I'm having trouble getting Ubuntu 4.10 (Install version) to notice my cable modem, which is connected by USB, not Ethernet. I could probably make it work off Ethernet, but I don't want to have to go back and switch it around every time I want to load up Windows or Ubuntu. 

Anyway. I have gotten the modem to work before in Linux. On SuSE 9.1 and Damn Small Linux. I just have no clue how to get it to work in Ubuntu. I haven't used Gnome before so I'm not really sure, I found the network configureation, and they had a bunch of options listed, except for the one I have. 

I'd like to get this to work. This seems to have a lot of the applications I've been looking for in a default install. 

The modem is a Terayon TJ-715x, if you are curious

Any help would be great, thanks.

---

### Post by somuchfortheafter on 2005-02-20
why not use ethernet in windows?

---

### Post by TestDummy! on 2005-02-20
Well, let's see. Windows doesn't even have any clue what to do with it when I use Ethernet. It has only worked in Windows with USB. I would use the Ethernet option in Ubuntu but like I said, I don't really want to have to keep on switching it around when I change the OS around. 

But, my question isn't about which interface I should use in Windows, it's if I can get this to work. Can it be done or will I have to use the Ethernet option. 

(Just to let you know, I haven't tried the Ethernet option in Ubuntu yet, I guess I'll see if that works, but I still want to see if USB will work.)

---

### Post by somuchfortheafter on 2005-02-20
check your tcp/ip settings in windows on the usb modem, if you want it to work in ethernet then just change it to match the usb connection(ie dhcp or static ip, gateways and such), also then apply this information in linux. i will assume this is already installed as dhcp as it works without tweaking in knoppix 3.6. anyway to get it to work in linux via usb.
boot up knoppix
enter in a terminal
lsmod
copy and save everything into a txt file in your linux partition in your home directory
boot up ubuntu and repeat and compare results
dl the module that is needed to make your card work
recompile your kernel with the module in it.

---

### Post by TestDummy! on 2005-02-20
You seem to be talking about this like I know how to do everything you are talking about

Well, for one, I don't even have Knoppix, I know how to get it but downloading Ubuntu already took a big enough bite out of my bandwidth limit. I do have a few other LiveCD's but none of them really work (Besides SuSE) at seeing my connection, 

Also, I have no clue what you are talking about with all these modules. I've never recompiled the kernel. Most compiling I've ever done was compiling Irssi. That's it. 

A more thourough explanation would be appriciated, thanks.

---

### Post by somuchfortheafter on 2005-02-20
well i shall go ahead and tell you that compiling a kernel is not that hard and that it is somthing you will probably want to learn to do. honestly i started out not knowing a thing about linux and i found a great book on amazon called linux power tools. if you are serious about learning linux i strongly recomend you buy it as it will tell you how to do some of the most important tasks in linux while keeping it so that anyone can understand it.

---

### Post by wallijonn on 2005-02-20
The first question to ask is, "Did the LiveCD connect to the internet"? Linux usually has problems with USB modems - and that is why most suggest that you switch over to a PCI ethernet card and J45 (instead of USB) modem. 

[http://www.short-media.com/forum/archive/index.php/t-5426.html](http://www.short-media.com/forum/archive/index.php/t-5426.html) (typical problem).

---

### Post by TestDummy! on 2005-02-21
Well, I do have one other Ethernet card around, but it's in another computer. I could try that. Ubuntu doesn't seem to notice my onboard network card. But I'm kinda tight on space, tiny case, don't have too much more room for cards. 

But, I'll see if that works and if it doesn't, plan B. 

To tell you the truth, I don't get why the USB connection works in SuSE (9.1 Personal) and Damn Small Linux, but fails to work in Ubuntu

---

### Post by TestDummy! on 2005-02-21
Okay, I added the network card to the computer that I had lying around 

The computer think's it a Realtek RTL8139 , but the card itself says it's a D-Link DFE-530TX . I add it, and I go into Ubuntu's device manager, and it seems to notice it, so I go to try and add a Ethernet device for Internet, (using DHCP or whatever it's called) and it calls it eth0, activates it, check stays there for one second, then it deactivates. 

What's up with that? I don't want to go out and have to buy new hardware to get thsi to work, and if I have to do that, then I think I'll just go back to what was working, even if it is missing a lot of the stuff I'm looking for.

---

### Post by TestDummy! on 2005-02-24
(I didn't really want to bump this, but my problem is unresolved) 

Does anybody have any idea on what to do?  I really can't do the Ethernet thing because I figured out my cable modem has a somewhat faulty connector, and it doesn't really work to well. But, I did actually try the Ethernet deal, and all Ubuntu does is activate it then instantly deactives it.

I have tried asking on the #ubuntu channel on IRC (And for those that tried to help, I do appriciate it), and I was suguessted a few things, but nothing really worked at all. 

I have gotten my cable modem to work with USB in SuSE and DSL just fine. Ubuntu is just being stubborn. It seems like 

SuSE: Go to the network devices, add a device, tell it that it's USB. Done
Ubuntu: Add new hardware, watch as it deactivates it over and over, ask questions all over, mess all day with the the console with no results. Tap your feet together three times.... yeah

I don't mean to be bashing Ubuntu, I kinda like it. It seems to run pretty good, has nice apps, etc. It' s just that I feel the download was a waste because of all this trouble I have to go though to get this to work

---

### Post by somuchfortheafter on 2005-02-24
[QUOTE=TestDummy!](I didn't really want to bump this, but my problem is unresolved) 

Does anybody have any idea on what to do?  I really can't do the Ethernet thing because I figured out my cable modem has a somewhat faulty connector, and it doesn't really work to well. But, I did actually try the Ethernet deal, and all Ubuntu does is activate it then instantly deactives it.

I have tried asking on the #ubuntu channel on IRC (And for those that tried to help, I do appriciate it), and I was suguessted a few things, but nothing really worked at all. 

I have gotten my cable modem to work with USB in SuSE and DSL just fine. Ubuntu is just being stubborn. It seems like 

SuSE: Go to the network devices, add a device, tell it that it's USB. Done
Ubuntu: Add new hardware, watch as it deactivates it over and over, ask questions all over, mess all day with the the console with no results. Tap your feet together three times.... yeah

I don't mean to be bashing Ubuntu, I kinda like it. It seems to run pretty good, has nice apps, etc. It' s just that I feel the download was a waste because of all this trouble I have to go though to get this to work[/QUOTE]
 well whenever i had the activate deactivate problem i just did a reinstall to fix it

---

### Post by nocturn on 2005-02-24
Let's take it one thing at a time.

If you plug in your MODEM to USB, what messages get logged?

You can check this with the command 'dmesg'

---

### Post by TestDummy! on 2005-02-25
Well, it does seem to give some output, even mentioning a 'eth2' and USB (Could that be it?) but I'm not sure, because every time I try to plug in my modem and mouse at the same time, the mouse freezes up.

---

### Post by TestDummy! on 2005-02-25
Well, I finally got it to work with USB :) 

I found out it actually knew what the modem was, but I didn't know what eth# it was. Turns out it was eth1. So I go ahead with configureing it and it worked out. 

But one question, is there a firewall? (I don't have a router or whatever, nor do I need one)

---

