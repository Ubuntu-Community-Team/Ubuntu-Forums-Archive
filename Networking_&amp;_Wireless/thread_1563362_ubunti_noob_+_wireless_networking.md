---
title: "ubunti noob + wireless networking"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by ozzynotwood on 2010-08-29
[SIZE=4]Hi everyone, before I start, I'm going to be pain the *** and post a question for a PC and wireless setup that I haven't got, its all 'in transit' to me from a couple of suppliers.

The plan was to have my new PC running Ubuntu 10.4 with a wireless lan USB/PCI card to connect to my modem. It seems that every wireless product that touches ubuntu:
1. Doesnt work
2. Works after 100+ hours of tweaking
3. Works for 30mins then drops out

I've been using microsoft forever, and have just started usuing ubuntu within the last 30 days, so im a complete linux noob, and I really dont need the problems with the points above as I'll have no idea how to fix anything.

So here's what I was thinking: On my current PC, Ubuntu gives me an internet connection with no configuring needed as long as I'm using a hardwired connection: PC -> Ethernet cable -> Router -> [/SIZE][SIZE=4]Ethernet cable-> Modem -> Phoneline. 

As far as I know, a router is configured from the router, not the PC. So would I have less problems with an internet connection going: PC -> Ethernet cable -> Wireless router -> Wireless signal -> Wireless Modem -> Phone line. Its basically the same setup as I have now (which works every time) except I'm swapping 1 Ethernet cable for a wireless signal. 

Will the work better than a wireless Lan card + wireless modem setup?
[/SIZE]

---

### Post by carl4926 on 2010-08-29
Open a terminal and post the result of

```
lspci -nnk
```

---

### Post by ozzynotwood on 2010-08-29
> **carl4926 said:**
> Open a terminal and post the result of

```
lspci -nnk
```

Sorry, my current PC is running windows XP, and my copies of ubuntu live CD are at the house I'm moving to, I'm just trying to do all the prep work now LOL

---

### Post by carl4926 on 2010-08-29
> **ozzynotwood said:**
> Sorry, my current PC is running windows XP, and my copies of ubuntu live CD are at the house I'm moving to, I'm just trying to do all the prep work now LOL
We need that code from the install of ubuntu 10.04 not from the live cd

---

### Post by ozzynotwood on 2010-08-29
> **carl4926 said:**
> We need that code from the install of ubuntu 10.04 not from the live cd

ok, unfortunatly im not able to do that, do you think my my wireless idea could work considering its very similar to the working setup I had with ubuntu?

---

### Post by carl4926 on 2010-08-29
Wired is always better (and safer) than wireless.

You will get many more problems where wireless is involved.

---

### Post by ozzynotwood on 2010-08-29
> **carl4926 said:**
> Wired is always better (and safer) than wireless.

You will get many more problems where wireless is involved.

Wired will not be practical in my house

---

### Post by carl4926 on 2010-08-29
Then this:

PC with pci express wireless device > Wireless access point in a wireless router > Phone

---

### Post by ozzynotwood on 2010-08-29
> **carl4926 said:**
> Then this:

PC with pci express wireless device > Wireless access point in a wireless router > Phone
  Does hat just describe the many problem setups I've been reading about?

---

### Post by carl4926 on 2010-08-29
> **ozzynotwood said:**
> Does hat just describe the many problem setups I've been reading about?
I do not understand this comment

---

### Post by bouncingwilf on 2010-08-29
I think you are maybe being a little pessimistic. In my experience, every PC I've ever  loaded Ubuntu on, has automatically found and configured the network  straight "out of the box" - be it Ethernet or wireless. Unless you've got something very "bleeding edge" or obscure, I'd be surprised if it didn't work from the word go

Bouncingwilf

---

