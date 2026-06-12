---
title: "Slow! ! ! !"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by jazf on 2010-04-29
Hello

Okay, i have a serious problem

My internet overall is very very very very slow

I'm a linux newb so what can I do ?

I have Windows XP on 2nd boot option (same computer, same hardware configuration)
And i have no problem there, internet is as fast as it should

I connect via wireless with a Linksys WUSB54g Ver4 usb adapter, to my SBG900 broadband connection.

Connecting via cable is not posible.


What can I do? this is very very slow :(

All other linux programs and stuff work normal.

Using Ubuntu 9,04 (i think?)

Computer specs: Athlon XP 2400 with 768ram, 64mb gfx card, etc..



I am using Firefox 3.5.3 Mozilla Firefox for Ubuntu canonical - 1.0

I downloaded and installed Goggle Chrome, speed is the same, very very slow to load pages etc,, even the most simple pages take forever to load, if it even loads.

---

### Post by davec64 on 2010-04-29
I'm guessing you're using Firefox as your browser?
By default IPV6 is enabled in Firefox so when it connects it tries to resolve the address via IPV6 first then IPV4.

Try disabling IPV6:

Open Firefox and in the address bar type:

```
about:config
```

Click the "I'll be careful" button

In the filter bar type "IPV6"

Double click the row:
network.dns.disableIPv6

This will then change the value to TRUE

Restart Firefox and see if its made a difference!

---

### Post by P4man on 2010-04-29
It might help if you can quantify the "slow" a bit. Is it slow dowload speed if your are downloading a large file (or page); is it slow scrolling on webpages even after they fully loaded, does it take a long time to resolve an address (click a link, and have to wait before it starts loading) or something else?

---

### Post by P4man on 2010-04-29
ok saw your edit now, and I googled on your wifi stick and it seems to be Atheros 5001 based. From what I can tell, it should actually work rather well on ubuntu 9.04, but a fresh 9.10 install seems to have big problems with it.

Lets first confirm your ubuntu version. click System > about and let us know.

Also, since your wifi is so slow, I assume you have not installed any updates, correct?

---

### Post by Elaztic on 2010-04-29
Hi,

It's probably the IPV6 issue.

Try however to look at your wireless settings in a terminal:

[FONT="Courier New"]iwconfig[/FONT]

In the second or third line there should be a 'rate' which is the transfer speed. If your wifi card/stick is 54 Mbps then it should state that number.
For my own wifi card I had to use the ndiswrapper and for some reason it sets the speed to 1 Mbps which you can remedy in several ways.
Please report back.

---

