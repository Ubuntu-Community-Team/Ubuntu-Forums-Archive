---
title: "another connection problem"
date: 2010-06-30
forum: Networking &amp; Wireless
---

### Post by ksnimi on 2010-06-30
Hi.
Just installed ubuntu 10.04 and there's no internet connection. i typed in sudo pppoeconf and it said that no working ethernet card could be found.
i have a [SIZE=1]Via Rhine II Fast Ethernet Adapter. A cable connection w/o a router.
I have tried this guide so far: [https://help.ubuntu.com/10.04/internet/C/connecting-wired.html](https://help.ubuntu.com/10.04/internet/C/connecting-wired.html) with no success and everything i found on the forum didn't seem to help either.
This is my first day with ubuntu(so i don't really know anything) and i hope it won't be last due to this issue. All suggestions are highly appreciated, thank you.
[/SIZE]

---

### Post by pedro_orange on 2010-06-30
Hello.

Does the system recognise the network card? 

```
lshw -C network
```

```
lspci -v | grep Ethernet
```

If it does recognise that a card is there, can you do:

```
ifconfig eth0
```

---

### Post by dineshs on 2010-06-30
also
```
ping -c3 4.2.2.1
```

---

### Post by ksnimi on 2010-06-30
So I entered the first 
 	Code:
 	lshw -C network 
and all I got was a swift text: PCI (sysfs) which immediately turned back to my terminal user waiting for another code.
Second
 	Code:
 	lspci -v | grep Ethernet 
didn't get any reaction at all.
The two other codes I was supposed to enter after successfully entering the first ones just told that the Network is unreachable or Device not found.
Any further suggestions or am I doomed?

---

### Post by ksnimi on 2010-07-01
I figured that the problem might be in my bios, cause I couldn't find where to enable NIC, so i did a CMOS jumper reset after which it appeared and was enabled. So I already got all excited, but I guess it was too soon. Nothing significant happened. The response from terminal after pushing those codes again resulted as before. No internet connection whatsoever. Any ideas? :-k

---

### Post by pedro_orange on 2010-07-01
Right; you need to figure out if Ubuntu can actually see your card first. Run the commands as an administrator you'll get more info

```
sudo lshw
```

Look for eth0 / ethernet etc. Post what you find in a pastebin or something. 

Same with:

```
sudo lspci -v
```

I imagine the hardware is detected, the drivers are just not loaded.

---

