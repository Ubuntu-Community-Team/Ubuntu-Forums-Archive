---
title: "Wireless &lt;-&gt; Ethernet issue"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by Lord Byte on 2010-08-02
Hi, I just installed Ubuntu 10.04 64bit edition, and have been working slowly through configuring it. I have minimal Linux experience.

My problem is as follows:
My internet connection is currently wireless stolen from someone else while my ISP gets its act together and fixes my landline.
The router/modem is used as a network hub atm for my other pc and machines until then.
I can use the wireless no problem UNTIL I enable the ethernet card, no more internet. If I disable the ethernet card again, hey presto! Internet.

Under windows I have no problem whatsoever, if I bridge both connections the other pc can even use the wireless internet of my 
main machine.
Now only thing I care about is making sure I can use ethernet, just internally, and use wireless for internet.
I don't care about sharing, bridging or anything like that.

I have tried several guides on bridging, got that working but.. no internet.
I tried manually configuring the ethernet adaptor to use the gateway the wireless was using, localhost, ...

I've lost 8 hours on this already trying everything but apart from disabling it just won't work :(

I want a way to stop Ubuntu from using the ethernet card for internet... I found an old article detailing how network-manager does this automatically, but it was old and had no info on how to disable it.

Any specific info that you might need?

Any info I can provide?

---

### Post by Lord Byte on 2010-08-02
I sorta figured out a workaround in KDE. By creating an extra network interface and making that one auto-connect makes the Wireless adapter the default one ^_^  And hence me able to use the internet AND access my network :)

Doesn't work on Gnome and its networking manager though :(

(And yes I highly prefer gnome to KDE)

---

### Post by Lord Byte on 2010-08-03
Any chance anyone could help me with this? Just need to stop Ubuntu from using the network as it's primary for internet.

---

### Post by Iowan on 2010-08-03
It's that "stolen" word that creates a problem. > Adult Content/Violence/Illegal Activity: Messages containing sexually oriented/violent/illegal dialogue, images, content, or links to these things will be deleted. Messages with links to or [COLOR="Red"]suggesting illegal activity[/COLOR] will also be deleted. Posting or linking to any of these could result in a ban. The Code of Conduct prohibits supporting such activity.

---

