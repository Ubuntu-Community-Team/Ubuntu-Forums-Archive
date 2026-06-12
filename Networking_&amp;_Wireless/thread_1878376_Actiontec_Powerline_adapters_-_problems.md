---
title: "Actiontec Powerline adapters - problems"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by ratcheer on 2011-11-09
For a long time, I had part of my LAN using two Netgear and two Actiontec 85 powerline adapters. A few months ago, one of the Netgears stopped working, so I converted my Ubuntu PC to wireless only. Then, recently, the other Netgear stopped working.

So, I ordered two new Actiontecs of the identical model number (HPE100T) to the two I was already using. However, I cannot get connectivity with the new ones. I consulted Actiontec's web site, where it said they might not work with Auto DHCP. The old ones work just fine with Auto DHCP, but I manually configured the settings on the new Actiontec that is connected to my Ubuntu PC. I used 192.168.1.128, 255.255.255.0, and 192.168.1.1 as the gateway.

Now, I could at least get an apparent link connection. But I still could not ping other hosts on my LAN, including the router at 192.168.1.1, nor can I surf the internet.

I have verified that the two old Actiontecs are still working. I submitted a request to Actiontec support and received the useless reply that they thought I had configured things correctly and they have no idea why the new ones aren't working. I have been wrestling with this since last night and I'm just about at the end of my rope.

Can anyone help?

Thanks,
Tim

---

### Post by ratcheer on 2011-11-09
Ok, I have an idea, but it will be tomorrow before I can test it out.  Even though the adapters were sold to me as new merchandise and the  packaging seemed completely new and fresh, I think encryption may have  already been applied on them. I will have to download the Actiontec  software and install it on my wife's Windows PC. If they are encrypted, I  hope the software will allow me to unencrypt them.

Tim

---

### Post by ratcheer on 2011-11-10
No dice. I installed the Actiontec Configuration Utility from their web  site onto my wife's Windows PC. It does not detect any of the adapters,  even the one that is currently working on her PC.

The  documentation says if it does not detect it at first to unplug the  adapter from the wall receptacle and then plug it back in. I tried this  several times with two different Actiontec adapters, hers and one of the  new ones. The utility never detected either of them.

Bleh. At least my wife's PC still has connectivity with the old adapter.

Tim

---

### Post by jonobr on 2011-11-10
Ive been looking at your post today and yesterday as I had never heard of those devices. (alot passes me by :-) )

However, it sounds as if the device isnt working the way it should.
Maybe Im reading your posts incorrectly.

---

### Post by ratcheer on 2011-11-10
Now, I have plugged in the two new adapters, only. It works!

So,  I am fairly certain that the problem is that the two pairs of adapters  have different encryption keys. What am I supposed to do if the supplied  utility will not detect them so I can change the keys to all match?  [IMG]https://secure.dslreports.com/i/v2/lite/confused.gif[/IMG]

Tim

---

### Post by PapaGary on 2011-11-10
> **jonobr said:**
> Ive been looking at your post today and yesterday as I had never heard of those devices. (alot passes me by :-) )
.
Google is your friend:

[http://www.actiontec.com/products/product.php?pid=203](http://www.actiontec.com/products/product.php?pid=203)

---

### Post by jonobr on 2011-11-10
PapaGary in the words of the dead....

[GOOGLE!!!!!]("http://www.youtube.com/watch?v=XacvydVrhuI")

:-)

---

### Post by ratcheer on 2011-11-10
I have sent another support request to Actiontec. Maybe they will have a better answer for this.

@jonobr - They are great when they are working. I've been using them for several years. No need to run ethernet cables all over the house - keeps the wife happy!

Tim

---

### Post by jonobr on 2011-11-10
You should see the holes in my house from drilling gone askew....

Networking Im ok at, drilling, eh....... ACTIONTEC!!!!:P

---

### Post by ratcheer on 2011-11-10
Oh, boy. The Configuration Utility is not compatible with Windows 7. They said I need to run it on Win XP. For crying out loud!

Tim

---

### Post by ratcheer on 2011-11-10
Problem is solved.

Dug out old Win XP PC, installed the Megaplug  Configuration Utility, set all four homeplug adapters to same encryption  key, they all work together, now.

Tim

---

### Post by jonobr on 2011-11-10
Man what an effort,
You think they would want their stuff working on stuff....

---

### Post by ratcheer on 2011-11-10
Nah, this is circa 2006/2007 hardware, 85 mbps. They are selling 200 mbps and higher stuff, now. I understand why they don't keep upgrading the software anymore. It's really kind of strange how you can still buy this stuff brand new.

The reason I bought it was for compatibility with what I already had. Also for its cheapness.

Tim

---

