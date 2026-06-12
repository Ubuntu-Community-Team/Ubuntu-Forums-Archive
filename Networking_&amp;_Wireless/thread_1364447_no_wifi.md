---
title: "no wifi"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by panicbox on 2009-12-25
hey gang i need some help, i have a hp G60-235DX laptop i want to install ubuntu 9.10 but the wifi is not working even. i'm looking at the display is telling me network and wireless is checked offed, i'm working with the Atheros 802.11 thx. remember gang keep it simple for me.

---

### Post by gordintoronto on 2009-12-26
I have no idea what this means: "i'm looking at the display is telling me network and wireless is checked offed"

Atheros 802.11 is a very large family of wireless adapters.  To get the specific model identification, use the terminal command:
lspci

Then use Goggle to search the model number and the word "Ubuntu," and it will probably point you to a message thread which solves your problem, if it is actually hardware related.

Did you right-click on the Network Manager icon and select "edit connections"?  Do you know the ID of your router, the type of encryption, and the password?

---

### Post by bender1234 on 2009-12-26
Hey.

The kernel that shipped with karmic has severe networking bugs. I sat up 5 different system, and only my old PIII box worked out of the box. You may try the kernel in the link below which is fixed. Note this kernel is for x64.You have to install them in the proper order. Think its the 9mb file, then the 600k one and the big one last. If it fails just try changing the order. 

[http://people.canonical.com/~apw/lp418933-karmic/]("http://people.canonical.com/~apw/lp418933-karmic/")

Some people on this site have stated that the experimental .17 kernel has fixed the issues, but I can't confirm it. I haven't installed it myself yet.

I'm a bit tired, and I've sat up so many systems and I might be confusing the drivers here. But I think the kernel above fixes both intel and atheros. I got atheros lan and intel 5100 on this box, and it fixed my system. 

Try the following commands in a terminal.
lsmod | grep 80211
lspci | grep Atheros
lspci | grep Network
sudo lshw -C network

and paste your output. Note that the case of the letters must be correct, typing atheros will not give any output.

merry x-mas! :)
Stian Bending Rodriguez

---

### Post by fibercode on 2009-12-26
Here is steb by step how to get your Atheros wireless NIC to work with Ubuntu 9.10 using the madwifi drivers:

[http://dimitar.me/?p=616](http://dimitar.me/?p=616)

---

