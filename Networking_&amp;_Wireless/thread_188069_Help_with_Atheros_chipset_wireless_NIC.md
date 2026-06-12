---
title: "Help with Atheros chipset wireless NIC"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by kuriharu on 2006-06-03
I just installed Dapper Drake and just like with Breezy, my wireless doesn't work. ](*,) 

The wireless card does show under System->Administration->Network tools, but naturally, even after putting in the WEP key and SSID I can't get DHCP to connect. Argh!](*,)  I have tried removing WEP from the router itself but I get the same results.

Can someone offer some advice? I know there's TONS of help on the forum, but each one I weed through always turns up a solution that doesn't work for me. If someone can offer me some assistance I'd be very grateful. Wireless not working is the one reason why I don't use Linux all that much, since I mostly use a laptop and if wireless doesn't work there's no real point. I don't want to keep using Windows!

If I do lspci | grep Atheros I do see my card show up and it does so after reboots so it's *almost* like Dapper Drake sees the card. :confused:

---

### Post by Lambert on 2006-06-03
The lspci command shows hardware that's recognized as being attached.

The card listed in Network tools is a good sign as it shows a driver loaded and commnicating with the kernel showing the capabilities of the card.

So, here are some commands to run and post output here. Anything personal like public ip or pass codes you can just xxx out.

```
lsmod | grep ath
iwconfig | grep ath
iwlist ath0 scan
ifconfig | grep ath

```

You may need to use sudo in front of some of these commands to get them to run.

What channel and protocol is your router broadcasting on? By protocol I'm looking for 802.11g or 802.11b or is it possible you bought a newer generation router with pre-n rating? There may be more questions but we can start here.

---

### Post by kuriharu on 2006-06-03
Thanks for the reply.

If I do these:

lsmod | grep ath
iwconfig | grep ath
ifconfig | grep ath

I get responses. I'll post them later; right now I'm using Windows to connect.
If I do this:

iwlist ath0 scan

it ends quickly and doesn't return results. I'm currently using channel 10. I ran

iwconfig ath0 channel 10

and it did find my WAP, so I thought I was in the clear. But when I tried dhclient ath0, I didn't get squat.

---

### Post by Lambert on 2006-06-03
So you have a working driver and are on the correct channel. Before you can run dhclient you need to be associated with router. 

You can do this graphically with the networking tools or from the command line like this (if it's set using an open unsecure signal, more input needed if using wep).

```
sudo iwconfig ath0 essid ____ 
```

You will know you're associated when you run the iwconfig command and in the output you see your wap essid name and it's mac address listed. If you just see 00:00:00:00:00:00:00 then you're not associated with the wap yet.

---

### Post by kuriharu on 2006-06-04
Sorry for the delay in getting back to you.

I have done that and it is set. I originally had my wireless router not broadcast the ssid but I turned the broadcast to "on" to make this part easier. What do you recommend I do next?

---

