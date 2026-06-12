---
title: "Internet sharing with two computers using crossover Ethernet"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by TestDummy! on 2006-01-19
Hello there, I've been wondering how I would do Internet sharing between two computers, using a crossover cable and Ethernet NIC's.

This computer (The one with the direct connection) has a built-in NIC, Ubuntu says it is a 'VIA VT6102 [Rhine II]', and for the other computer a "Accton SMC2-1211TX" (I think it was something nabbed from a HP). From the looks of feedback I'm getting from the computers, and Google, I'm guessing both are supported cards.

But I don't know how to get them to share the Internet. I did notice in Firestarter, there is a "Internet connection sharing" option, but I don't know if I'm supposed to do something on the other end computer to get it to work right. I don't even know if both network cards are configured.

And er, both are running Ubuntu 5.10 last I checked.

Any ideas on how to get this to work?

---

### Post by cwaldbieser on 2006-01-19
[QUOTE=TestDummy!]Hello there, I've been wondering how I would do Internet sharing between two computers, using a crossover cable and Ethernet NIC's.

This computer (The one with the direct connection) has a built-in NIC, Ubuntu says it is a 'VIA VT6102 [Rhine II]', and for the other computer a "Accton SMC2-1211TX" (I think it was something nabbed from a HP). From the looks of feedback I'm getting from the computers, and Google, I'm guessing both are supported cards.

But I don't know how to get them to share the Internet. I did notice in Firestarter, there is a "Internet connection sharing" option, but I don't know if I'm supposed to do something on the other end computer to get it to work right. I don't even know if both network cards are configured.

And er, both are running Ubuntu 5.10 last I checked.

Any ideas on how to get this to work?[/QUOTE]

One PC needs 2 NICs.  One NIC plugs into the other PC via crossover cable.  The second NIC plugs into your broadband modem (or whatever device you use to connect to the Internet).  Then you should be able to check the "Internet Connection Sharing" in firestarter.

---

### Post by TestDummy! on 2006-01-19
[QUOTE=cwaldbieser]One PC needs 2 NICs.  One NIC plugs into the other PC via crossover cable.  The second NIC plugs into your broadband modem (or whatever device you use to connect to the Internet).  Then you should be able to check the "Internet Connection Sharing" in firestarter.[/QUOTE]

Actually, I don't need two. I use USB for my cable modem, mainly because the Ethernet connector on the modem itself is a tad on the quriky side and doesn't connect right.

---

### Post by bobyang on 2006-01-19
on the other way, I think you can set two ip address on one NIC

---

### Post by matthew on 2006-01-19
[This thread]("http://ubuntuforums.org/showthread.php?t=76346") probably goes a bit further than what you want to do, but if you read through it you will discover how to do what you want.

---

### Post by TestDummy! on 2006-02-17
Bit late to reply to this, but I did try that a few weeks ago when this was new and gave up. I've been a bit busy too for any reattempt until now.

Anyways, the how-to seems all backwards to me because it's talking about a wirelessly connected laptop, a desktop second on the chain, and a wireless router, which I don't even have. Both of mine are desktops, one connected to the Internet with a cable modem, with a crossover cable going to the other. I know your how-to talks about setting up sharing, but the hardware setups are completely different, and that's where I got lost.

The way I see it, your how-to assumes this setup

*Desktop -> Wireless Laptop -> Router -> Internet*

The way I basically want to do it is

*Desktop #2 -> Desktop #1 (the one with the modem) -> Internet*

No routers, no laptops. Not to offend you, but that how-to just confuses me. Any other ideas?

---

### Post by bscbrit on 2006-02-18
All the advice that you have received so far seems good - but I found the easiest way was to install smoothwall on the computer with the internet connection (although I'm sure that firestarter will do the job and I'm told has a much easier interface to get it working).  Static IP settings for the two ethernet cards and off you go.

---

### Post by bscbrit on 2006-02-18
I'll try and do this diagramatically for you:

Desktop#2 (192.168.0.1)------(192.168.0.2)Desktop#1------->USB to ISP

I think that's what you wanted?

---

### Post by matthew on 2006-02-18
[quote=TestDummy!]Bit late to reply to this, but I did try that a few weeks ago when this was new and gave up. I've been a bit busy too for any reattempt until now.

Anyways, the how-to seems all backwards to me because it's talking about a wirelessly connected laptop, a desktop second on the chain, and a wireless router, which I don't even have. Both of mine are desktops, one connected to the Internet with a cable modem, with a crossover cable going to the other. I know your how-to talks about setting up sharing, but the hardware setups are completely different, and that's where I got lost.

The way I see it, your how-to assumes this setup

*Desktop -> Wireless Laptop -> Router -> Internet*

The way I basically want to do it is

*Desktop #2 -> Desktop #1 (the one with the modem) -> Internet*

No routers, no laptops. Not to offend you, but that how-to just confuses me. Any other ideas?[/quote]I was about to reply but what bscbrit suggests is exactly what I was going to say. To reiterate, plug one desktop into the internet connection, and use the crossover from it to the other computer. You should be able to leave DHCP set for the middleman desktop to internet connection and use a static IP for the connection between the two computers.

I'm on the road at the moment and my time here will be sporatic at best. If you have more questions, post and if I can't help more hopefully someone like bscbrit can jump in.

---

### Post by TestDummy! on 2006-02-18
[QUOTE=bscbrit]I'll try and do this diagramatically for you:

Desktop#2 (192.168.0.1)------(192.168.0.2)Desktop#1------->USB to ISP

I think that's what you wanted?[/QUOTE]

Hm, I didn't know it went that way, I should have sworn the first computer got 192.168.0.1, and the second *.2. That kinda thing would have thrown me off too. 

What goes in the other box, for gateway? I could probably figure it out from that how-to, but there's all that extra stuff I'd probably mess up again. I recall the gateway to the second computer being the IP of the first, internet-connected one, but I am not sure.

Edit: I mean in this menu
[IMG]http://img.photobucket.com/albums/v176/TestDummy/confusing.png[/IMG]

I really appreciate the assistance, I'm just stumped on a few of these options.

---

### Post by spd106 on 2006-02-18
It doesn't matter which has .1 or .2 as long as they are different. 

You should be ok to use a subnet of 255.255.255.0 on both machines.

Make sure the default gateway of PC 2 is the ip address of PC 1. In the above case it should be 192.168.0.2

---

### Post by TestDummy! on 2006-02-18
[QUOTE=spd106]It doesn't matter which has .1 or .2 as long as they are different. 

You should be ok to use a subnet of 255.255.255.0 on both machines.

Make sure the default gateway of PC 2 is the ip address of PC 1. In the above case it should be 192.168.0.2[/QUOTE]

So basically, I assume from this that since the first computer is the one with the modem, it does not need a gateway address?

---

### Post by spd106 on 2006-02-18
> So basically, I assume from this that since the first computer is the one with the modem, it does not need a gateway address?

Basically, yes

---

### Post by TestDummy! on 2006-02-18
I have gotten both computers to be able to ping eachother, but the second one cannot ping anything on the Internet, like Google. Any ideas?

---

### Post by bscbrit on 2006-02-18
Yes, if you can ping by number but not by name, then we need to sort the DNS out.  The first machine (with the internet connection) will have the DNS already set up which is why it can ping [www.google.com](www.google.com) but the second machine cannot.  You need to find the contents of /etc/resolv.conf on the machine that has the internet connection and copy the 'nameserver xxx.xxx.xxx.xxx' information into the /etc/resolv.conf which is on the machine that hasn't got its own connection.  It will then know how to look up named addresses.

I don't think I explain that very well, so if you do not understand just come back and I will try again.....:-D

---

### Post by TestDummy! on 2006-02-18
Well, I decided to see if the DNS information the first computer had would help me work with names, and it did, just that.

It seems to work fine now. Finally got the network to actually work \\:D/ 

Thanks again everybody!

---

### Post by matthew on 2006-02-18
I just got to my hotel and stopped in to see how things are going. I'm happy to see that things were figured out. Congratulations!

---

