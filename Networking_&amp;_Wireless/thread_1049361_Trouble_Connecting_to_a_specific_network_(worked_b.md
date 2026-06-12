---
title: "Trouble Connecting to a specific network (worked before)"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by Rawgers on 2009-01-24
Yesterday, I was downloading something, than my wireless connection stopped working. I thought it was something due to the router, so I restarted the Internet, but that did not do anything. I could see my wireless network connection (and others) but when it tries to connect, it stays on that first little green light. Now this morning, I tried deleting the network I saw just to see if it would restart (I guess it was dumb) and now I can not even see the specific network I want to connect to (I can see others though). When I boot up to windows XP it works though.

The Hardware info-
Broadcom Corperation BCM4306 802.11 b/g Wireless LAN

Thanks for any help.

EDIT: SOLVED. SEE POST BELOW

---

### Post by Stunts on 2009-01-24
Sorry to hijack this but I'm having a similar issue on my father in law's laptop.
It can detect lots of wireless networks arround it, but not his own WLAN.
The laptop is running Intrepid and Vista. In vista the connection if fine, but not in Ubuntu. I'm currently typing this of my eeePC also running Intrepid from the same problematic WLAN.
The wireless card is an Intel 5100.
I find this to be extremely strange behaviour...

Oh, one more thing, another laptop running Hardy also detects and connects to this WLAN just fine. It has an Intel 3945 wireless card.

Hope someone has an idea about what is going on.
Thanks in advance!

---

### Post by Rawgers on 2009-01-25
Bump~
Help both of us please =[

---

### Post by Guille Damke on 2009-01-25
Hi,

I remember I had a problem with networking, one thing that *may* help is to check your /etc/network/interfaces file, it should look like this:
```

auto lo
iface lo inet loopback

```

You can check it typing in a terminal:
```
cat /etc/network/interfaces
```
If you have more lines besides the ones I posted, add a "#" (without the "") at the beginning of the other lines, you can edit the file using:
```
sudo gedit /etc/network/interfaces
```
probably, you'll have to reboot the machine.
I hope it helps.

EDIT: I have to add that after this always use the network manager located next to the clock.

---

### Post by Rawgers on 2009-01-25
@Guille Damke

On interfaces, I only had ```

auto lo
iface lo inet loopback
```
So I did not do anything. But thanks for the help.

---

### Post by Stunts on 2009-01-25
My father in Law's /etc/network/interfaces was OK too.
Let me add a new clue for this thing:
His computer is an ASUS with splashtop (it's a little embbebed linux that lets you boot into it in 8 seconds instead of booting into your main OS). In here I have the very same problem. I can see lots of Wlans, but not his own.
Too further mess thing up - his neighbour has the same router model (it's standard issue with the ISP) a 2WIRE something (can't remember the exact model), but I cann see his network too.
Both networks are configured for WPA Personal with a TKIP key.
Oh, and one more thing: if I type in a console:```
sudo iwlist wlan0 scanning
```
I can see the same WLANS than I see in network manager, plus one with a very strong signal, that is named "". Yes, just the quotes I didn't forget to type something in there.
I'm assuming this is the network I'm trying to connect to since the signal follows the distance I am standing from the router (it goes to 99/100 if i'm less than 1m away).
I hope it can be solved with this further info...
Thanks in advance once again.

---

### Post by Rawgers on 2009-01-26
I tried something, and it kind of gave me something. I uninstalled network-manager and installed an alternate program that searches for networks. There was one network that was found that said "hidden" that has a lot of green bars, so I'm guessing that is mine since all my neighbors bars are extremely low. The only thing, when I put in the PSK, it still does not connect.
Edit:
Solved it.
Had to set my router up so it broadcasts.

---

### Post by Stunts on 2009-01-26
I'm glad you got it sorted Rawgers!
Unfortunately my problem seems a bit more complicated...
I hope some expert will take a look at this, and maybe be able to hint me in the right direction.

---

### Post by Stunts on 2009-04-10
Hello again.
I know it's been a while, but I have finally found the cause of my problem, and it's solution.
The router was set to broadcast on automatic channel (1-13). 
Apparently, Intel cards (iw5100 and iw4965) are set only to pick up signals form channel 1-11 and 31-3...something (in Linux - in windows picked up the signal).
So when the router would set itself to channel 12 or 13 I could not connect from the Intel wireless PC's, but could do so from my eeePC.
The solution was to set the router to broadcast on a fixed channel (in this case 7).
I'm glad that it's solved now. It got me scratching my head all this time!
Thank you to all that gave me a tip on this. Since all problems are solved, I think the thread should be marked "Solved".

---

