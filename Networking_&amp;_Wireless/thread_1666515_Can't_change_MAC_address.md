---
title: "Can't change MAC address"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by vincix on 2011-01-13
As I try to change my if0 MAC address either from /etc/networking/interface, or from GUI application, when I try to reconnect (through GUI) the application automatically creates some sort of alias interface with the default MAC every time, and leaves the one with the changed MAC aside. 
What should I do?

Thanks

---

### Post by vincix on 2011-01-15
There was a time when you used to answer to these kind of questions :)

---

### Post by Iowan on 2011-01-15
Examples might be helpful.  I'm not familiar with the **if0** interface (my machines usually have **eth0**)- or /etc/networking/interface, but could you post your */etc/network/interfaces* and the lines (**ifconfig -a**) showing the alias interface/MAC address?

---

### Post by vincix on 2011-01-15
> **Iowan said:**
> Examples might be helpful.  I'm not familiar with the **if0** interface (my machines usually have **eth0**)- or /etc/networking/interface, but could you post your */etc/network/interfaces* and the lines (**ifconfig -a**) showing the alias interface/MAC address?

I am sorry, that was my bad. By "if" I only meant to say "interface". It's the same eth0. And it's simply using dhcp without any additional options. I've just installed it a few days ago (Ubuntu 10.10).

---

### Post by Bucic on 2011-01-24
Same problem here!

I changed my interfaces file to look like this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
hwaddress ether 00:01:02:03:04:05
```

as per this article [http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/)

After networking restart I get my IP set up correctly from DHCP and the connection works fine. Problems:
- frequent connection loss when trying to install any app!
- reverts to the incorrect (old) MAC and IP
- incorrect (old) MAC and IP at system startup
- the connections applet creates connection aliases in the list (confusing behavior to say the least)

Please help me tackele the problem ASAP. I can't use my fresh install without my connection functioning properly.

---

### Post by dBuster on 2011-01-24
> **vincix said:**
> I am sorry, that was my bad. By "if" I only meant to say "interface". It's the same eth0. And it's simply using dhcp without any additional options. I've just installed it a few days ago (Ubuntu 10.10).

Okay not exactly sure why you are trying to change the MAC address unless you have multiple NIC cards in your computer and you are trying to use one in particular.  MAC addresses are basically like the serial number of the card that you have and are most times burned into a chip.  There are spoofs out there where you can clone a MAC address mainly on routers and such.  If Ubuntu keeps changing it maybe it is reading the actual MAC address from the hardware and changing it to be correct?  Have you pulled the device/card and read the actual MAC address off of it?  That would give you the exact MAC address to be using.

Here is something from wikipedia:

> MAC address
From Wikipedia, the free encyclopedia
A Media Access Control address (MAC address) is a unique identifier assigned to network interfaces for communications on the physical network segment. MAC addresses are used for numerous network technologies and most IEEE 802 network technologies including Ethernet. Logically, MAC addresses are used in the Media Access Control protocol sub-layer of the OSI reference model.
MAC addresses are most often assigned by the manufacturer of a network interface card (NIC) and are stored in its hardware, the card's read-only memory, or some other firmware mechanism. If assigned by the manufacturer, a MAC address usually encodes the manufacturer's registered identification number and may be referred to as the burned-in address. It may also be known as an Ethernet hardware address (EHA), hardware address or physical address.
MAC addresses are formed according to the rules of one of three numbering name spaces managed by the Institute of Electrical and Electronics Engineers (IEEE): MAC-48, EUI-48, and EUI-64. The IEEE claims trademarks on the names EUI-48 and EUI-64, in which EUI is an acronym for Extended Unique Identifier.

---

### Post by Bucic on 2011-01-24
I know what MAC is and I know that I need to change it*. I don't mean to be grumpy but "what Ubuntu wants/thinks" doesn't seem relevant to me. It takes less than 3 minutes to change MAC on Windows via GUI. 

I'm still hoping for some solution...


* only one MAC per user is allowed on my network and I have to connect a different PC (laptop).

---

### Post by vincix on 2011-01-24
Strange as it may seem, I found a solution on Romanian Ubuntu forums :D The idea is to edit the 'clone' section under the 'mac address' and it works. 
What dbuster says is unbelievable. It is indeed irrelevant why I want to change it, given the fact that, as Bucic said, in windows you can change it in a few seconds. There are tens of reasons why you'd want to change your mac address. Any OS should allow the user to change their mac addresses if they wanted to; it would be utterly stupid otherwise. Moreover, I have an integrated card, so I wouldn't be able to 'get it out'. It is obvious that any OS takes the BIA by default, but that's not the point. 
And your other explanations are quite redundant and irrelevant.

---

### Post by Bucic on 2011-01-24
> **vincix said:**
> Strange as it may seem, I found a solution on Romanian Ubuntu forums :D The idea is to edit the 'clone' section under the 'mac address' and it works. 
What dbuster says is unbelievable. It is indeed irrelevant why I want to change it, given the fact that, as Bucic said, in windows you can change it in a few seconds. There are tens of reasons why you'd want to change your mac address. Any OS should allow the user to change their mac addresses if they wanted to; it would be utterly stupid otherwise. Moreover, I have an integrated card, so I wouldn't be able to 'get it out'. It is obvious that any OS takes the BIA by default, but that's not the point. 
And your other explanations are quite redundant and irrelevant.
I'm getting to it. Can you post a step-by-step instructions in the meantime. I recall I already tried your method to no avail :/

---

### Post by vincix on 2011-01-24
There's nothing to it really.
You just right-click on the network icon - edit connections. then select 'auto Ethernet' (if this is what you've got), edit and then, on the new window you've got two sections: device mac address and cloned mac address. You simply introduce your new mac address in the Cloned section. The two-number groups have to be separated by a colon like this: 00:11:22:33:44:55

This should be it.

---

### Post by dBuster on 2011-01-24
> **vincix said:**
> There's nothing to it really.
You just right-click on the network icon - edit connections. then select 'auto Ethernet' (if this is what you've got), edit and then, on the new window you've got two sections: device mac address and cloned mac address. You simply introduce your new mac address in the Cloned section. The two-number groups have to be separated by a colon like this: 00:11:22:33:44:55

This should be it.

Geez talk about getting on a high horse.  

So you are CLONING and not using the devices actual mac address which was not totally clear in the first place hence my post.  You want to jump on someone jump on yourself and look at your etiquette!

What ever in the end, go clone your mac address...  In my 18 years of networking I have only had to clone a mac address once, yes once.  So to me it is utterly worthless and pointless.  Just as you said my comments were.  Think about how you treat someone with your replies.

Also with cloning you are essentially just using the MAC address of another device.......

```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:1B:FC:F7:71:F7

```

There is an example from a 10 second google search on cloning MAC Addresses and UBUNTU.

---

### Post by vincix on 2011-01-24
You can imagine that there are cases which you, in your 18-year experience, don't deal with.

---

### Post by dBuster on 2011-01-24
> **vincix said:**
> You can imagine that there are cases which you, in your 18-year experience, don't deal with.

Oh I am sure there have been some that I did not see.  My point was that in 18 years I only had to CLONE once.  And if you read back to the beginning of this thread oh mighty high and mighty one yourself you will see not one mention of cloning until after I made that post.  

Needless to say some are all about themselves and not really clear with their initial requests so when someone pops in and provides a post they jump off of their high horse and jump down their throat then they mention the word CLONE.  uh huh...  Thought so.

---

### Post by Iowan on 2011-01-24
> **vincix said:**
> Strange as it may seem, I found a solution on Romanian Ubuntu forums :D The idea is to edit the 'clone' section under the 'mac address' and it works. Problem solved - thread closed.

---

