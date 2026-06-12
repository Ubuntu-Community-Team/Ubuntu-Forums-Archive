---
title: "Realtek 8169 and WOL: pre-down false in interfaces"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by geus on 2009-01-10
Hello,

First post here so please be kind :)
Just wanted to post this "fix" I found.

Running Intrepid 64 bit here on a Gigabyte P35 DS3R mobo which uses the RTL8111b onboard nic and have been trying to get WOL working for days. Tried all kinds of solutions like changing NETDOWN=yes to NETDOWN=no in /etc/init.d/halt and adding all sorts of scripts like mentioned here: [http://sethbc.org/2008/10/12/wake-on-lan-and-the-intrepid-ibex](http://sethbc.org/2008/10/12/wake-on-lan-and-the-intrepid-ibex)

Nothing seemed to work but finally came across this feisty bug ([https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/44170](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/44170)) and since I was really reaching at the time thought; let's try...
And lo and behold: the bugger works!

Note that I still got NETDOWN=no set atm as mentioned above. Will check if this is stil required. And obviously have Network Manager removed.
Just wanted to post this here, because I can't find a single website linking this in relation to Intrepid. Might help someone with a simmilar mobo.

And obviously to ask if I'm missing something very obvious? I just started using ubuntu and am hardly an experienced user, so please, any comments are appreciated.

Edit: Can confirm that NETDOWN=no is required for WOL to function, same goes for pre-down false in /etc/network/interfaces. When one of both is commented out WOL won't work.

---

### Post by rogersce on 2009-01-20
this fixes my problem exactly! thanks for posting this

it wasn't immediately obvious from the bug report what to do, so i'm just going to list here the steps I took to fix the problem for other newbies out there like myself.

1. follow directions [here]("http://ubuntuforums.org/showthread.php?t=234588") to set up WOL.

2. remove Network Manager. you'll need to configure your connection manually, [see here]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html") .

3. set NETDOWN=no in /etc/init.d/halt

4. in /etc/network/interfaces, under the device you use to WOL (most likely eth0), add the line 'pre-down false'

---

### Post by geus on 2009-01-21
Good to hear that the post helped, you're welcome.
And thanks for clarifying the process involved a bit.

Seems accurate except one comment I'd like to make: I think you only need a script when running two OS's in dual boot. If you're running Ubuntu solely you can skip step 1 as the 'Wake-on: g' setting of the NIC will remain flagged. At least; mine did.

One can check with ethtool as mentioned in the [thread]("http://ubuntuforums.org/showthread.php?t=234588") you posted

```
sudo apt-get install ethtool
```

After a reboot the output of ```
sudo ethtool eth0
``` should be 

```
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	**Wake-on: g <----**
	Current message level: 0x00000033 (51)
	Link detected: yes
```


so step 2-4 sufficed for me. No script running whatsoever.

---

