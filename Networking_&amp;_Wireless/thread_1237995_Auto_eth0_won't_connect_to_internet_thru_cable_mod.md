---
title: "Auto eth0 won't connect to internet thru cable modem"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by MorcantM on 2009-08-12
[SIZE=4]I have Ubuntu 9.04. I am switching from DSL to Cable. Autoeth0 tries to connect but can't make the connection through the cable modem. The DSL is still on and Ubuntu works fine with the DSL. I have a computer with XP and it connects through the cable modem just fine. I assume there is a simple solution but I just can't find it. 

Also, I am a relative newcomer to Ubuntu.

Thanks.[/SIZE]

---

### Post by fluffman86 on 2009-08-12
Right-click on your network manager (the two little compute monitors in the top-right of your desktop next to the clock) and then click Edit Connections.  Go to the DSL tab and Delete your current DSL connection.  

Now, right-click on the network manager again and uncheck the box next to Enable Networking, then re-check the box a few seconds later.

---

### Post by MorcantM on 2009-08-12
> **fluffman86 said:**
> Right-click on your network manager (the two little compute monitors in the top-right of your desktop next to the clock) and then click Edit Connections.  Go to the DSL tab and Delete your current DSL connection.  

Now, right-click on the network manager again and uncheck the box next to Enable Networking, then re-check the box a few seconds later.
Thanks for your reply. I am still having trouble connecting. I couldn't follow the directions exactly as there wasn't anything under the DSL tab.  There is Auto eth0 under the wired tab. I was afraid to delete Auto eth0 for fear of losing all connection. 

Thanks

---

### Post by MorcantM on 2009-08-12
I should have posted problem here first.  Very new to Ubuntu forums.  Ubuntu has worked out well.  I have Ubuntu 9.04.

At any rate I was switching from DSL to Cable. DSL is still on.  Ubuntu computer would connect thru DSL but not cable.  My windows computer worked through the cable modem without my doing anything.

I put this question in the wrong part of forum and sort of improvised on the advice I got.

Long story short...ish, I deleted Auto eth0 and now my Ubuntu computer doesn't connect at all.  I need to get it connecting through the cable modem.  PLEASE HELP!  I'm bald enough already.

---

### Post by Iowan on 2009-08-13
Other thread wasn't necessarily misplaced (and could probably be moved). My DSL connection uses wired (actually **auto eth0**) rather than the DSL tab. How do you connect to each? Is DSL via card, or is it ethernet to external modem (like mine)? I presume cable connection is via ethernet, but I'm curious how you are connected to both.

---

### Post by MorcantM on 2009-08-13
> **Iowan said:**
> Other thread wasn't necessarily misplaced (and could probably be moved). My DSL connection uses wired (actually **auto eth0**) rather than the DSL tab. How do you connect to each? Is DSL via card, or is it ethernet to external modem (like mine)? I presume cable connection is via ethernet, but I'm curious how you are connected to both.
My DSL was connected through Ethernet to external modem.  The auto eth0 was not under the DSL tab, it was under the first tab.  Nothing was under the DSL tab.  I thought maybe getting rid of auto eth0 would solve problem.  Not that smart in hindsight.  I like Ubuntu better than windows but I need to get Ubuntu connecting to internet and I need it to be through cable modem.  I just don't get why it would work automatically with DSL but  not the cable modem.

---

### Post by Iowan on 2009-08-13
Before I fire up my laptop to see how "Auto eth0" is configured, how do you connect to cable? Is there a switch or router that XP and Ubuntu use, or do you unplug XP and plug in Ubuntu? (worth asking: XP and Ubuntu are on different machines - or dual-boot?) If you unplug one, then plug in the other, you may need to power-cycle the modem. (turn off, leave for a moment, then turn back on) Some modems "lock onto" a specific MAC address.

---

### Post by MorcantM on 2009-08-14
I have two separate computers.  I switch plugs, but I do powercyle the modem.  It hasn't helped.  Ubuntu is way better than windows, but I have to solve the connectivity problem.  

Would a router possible help?  

I was going to get one anyway because its a pain to switch cables.  

My only other thought is to reinstall Ubuntu and hope it is magically fixed.

Auto Eth0 is back an in the same place under the first tab.  There is no Mac address I notice.  The modem is doing something because the Activity light stars flashing.

---

### Post by Iowan on 2009-08-15
> **MorcantM said:**
> Auto Eth0 is back an in the same place under the first tab.  There is no Mac address I notice.  The modem is doing something because the Activity light stars flashing.So **Auto eth0** is back? Probably a good thing... you *should* be able to edit the MAC address back into it. **ifconfig -a** *might* reveal the MAC, otherwise you can dig it out of **lshw -C network**.

I don't have a router connected to my DSL modem - only a switch... my modem doesn't appear to "lock on".

---

### Post by MorcantM on 2009-08-15
I will try that later today.  Funny thing, I decided to make my windows computer a dual boot with Ubuntu and the Ubuntu portion connects just fine.  I have been using Ubuntu for about 6 months with hardly any problems that I couldn't fix--so why not.  

I want to fix the other computer so that I can learn more about how Ubuntu works.  When you talk about **ifconfig -a** and **1shw -C**, are you talking about commands that I type into the terminal?

---

### Post by Iowan on 2009-08-15
> **MorcantM said:**
>  When you talk about **ifconfig -a** and **1shw -C**, are you talking about commands that I type into the terminal?Yes. Sorry, forgot to mention that. BTW, that's not a numeral, but a letter: **lshw** means **l**i**s**t **h**ard**w**are - the  **"-C network**" limits the results to network class (components).

---

### Post by redlightbreaks on 2010-03-03
Hi, just browsing anywhere I can for a solution to this issue, did this problem ever get solved?

I'm having the exact same problem on my HP pavilion dv9000 trying to connect to a cable modem through an ethernet cable.

Currently have 3 windows computers that can connect no problem, I have one ubuntu 9.10 machine that has never been able to connect (ethernet or wireless)

I tried ifconfig but the hardware address for eth0 matches the mac address listed in eth0 in network manager (this seems obvious) is that what you meant for him to check?

Thanks!

---

