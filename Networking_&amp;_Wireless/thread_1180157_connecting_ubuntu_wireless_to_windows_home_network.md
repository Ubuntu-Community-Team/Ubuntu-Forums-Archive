---
title: "connecting ubuntu wireless to windows home network"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by AlanInVancouverBC on 2009-06-06
We gave a cheap computer with ubuntu 8.04 on it to my daughter's friend as a birthday present. Tomorrow I am going to TRY to get this computer connected to her family's wireless network, which has the wired computer (using windows 98!) and a windows xp laptop connected wirelessly to that wired computer.

After 20 years with Microsoft, I've only been with ubuntu for less than a year, so my knowledge is "newbie" level.

How do I tweak the software to "see" the network?

---

### Post by pastalavista on 2009-06-06
If you can see the router, you should also be able to see the network. Will you be connecting wired or wireless? The Samba client is already installed so the network should be available to you but for you to be available to the network, you'll need to install Samba server.

---

### Post by AlanInVancouverBC on 2009-06-06
Thanks for the quick reply.
When you say "see the router", what do you mean?
Also, I will be connecting this new ubuntu computer wirelessly to the already-present wireless network in her home.
Alan

---

### Post by SIGTERMer on 2009-06-06
sorry for barging in but i couldn't resist..

anyways, as for the network. networking is more or less similar to windows.
first, try to connect to the network using the network-manager from your desktop. if your connecting to a wireless network, it should be visible unless the network hidden. if you're connecting to the network through wire, it should connect automatically if you're connecting to a normal "home" router.

if things didn't go as planed, you could try
```
ifconfig
```  
to determine dermine wither you're connected or not. normally, eth0 is used for a wire connection, and wlan0 for wireless.

---

### Post by pastalavista on 2009-06-06
> **AlanInVancouverBC said:**
> Thanks for the quick reply.
When you say "see the router", what do you mean?
Also, I will be connecting this new ubuntu computer wirelessly to the already-present wireless network in her home.
Alan

By "see" I just mean if it shows up in the network manager.

---

### Post by AlanInVancouverBC on 2009-06-06
Thank you, both.
I have to go volunteer at a computer recycling place (where I got the $20 computer, including monitor, mouse, keyboard, and speakers!), get the wireless card and build some computers (using recycled parts). It's FreeGeek Vancouver.
So I won't be responding til this evening.
Alan

---

### Post by pastalavista on 2009-06-07
good luck.. sounds like a fun project. if you computer isreally old, you may need to find some drivers in the [archive repositories]("http://www.debianadmin.com/adding-ubuntu-repositories.html").

---

### Post by AlanInVancouverBC on 2009-06-07
Thanks again, people.
It turned out to be incredibly easy.
I put the card in, used my wireless network to see if it "saw" it.
It did.
I put in my wep and I was on the net.
Easier than Windows!

---

### Post by 2zeek on 2009-06-29
[LEFT]sorry
[/LEFT]

---

