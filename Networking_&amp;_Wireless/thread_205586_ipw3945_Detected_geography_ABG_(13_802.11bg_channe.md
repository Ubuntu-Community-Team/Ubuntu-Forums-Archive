---
title: "ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by zipeppe on 2006-06-28
Hi guys,

I'm puzzled about the messages:
```
[4296256.215000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4296263.813000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4296290.207000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4296297.805000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[4296385.960000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

```


After the boot the yellow led of wireless is blinking and still blinking until I do the following commands:


[LIST]
[*]sudo iwconfig eth1 mode ad-hoc
[*]sudo iwconfig eth1 mode managed
[*]sudo dhclient3 eth1
[/LIST]


After that the led still on and the connection with the router is established.

```
eth1      IEEE 802.11g  ESSID:"mynet"
          Mode:Managed  Frequency:2.412 GHz  Access Point: **XX:XX:XX:XX:XX:XX**
          Bit Rate=48 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/100  Signal level=-71 dBm  Noise level=-117 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9689   Missed beacon:0

```

But I don't know why but it happens that so often the led start blinking
ipw3945 generates the "Detected geography ABG" messages, and iwconfig shows the following condition (AP: not-connected):

```
eth1      unassociated  ESSID:"mynet"
          Mode:Managed  Channel=0  Access Point: **Not-Associated**
          Bit Rate=0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8938   Missed beacon:0

```

And it's still in the same status until I open a shell to give those 3 magic commands.

I have also wrote to the ipw3945 developers, but the didn't give to me any answer up to now. Under windows the wireless works fine (never disconnect).

Have you an idea about?
Tnx

---

### Post by GoNe on 2007-09-05
Same problem here on a vaio Fz-11S 

network adapter Intel Pro Wireless 3945

the link lasts for a few minutes,then i have to give the magic commands you suggested.
:confused:

---

### Post by Zorael on 2007-09-05
Same here.

Only my magic commands are:
```
$ sudo modprobe -r ipw3945
$ sudo modprobe ipw3945
```

And I'm not using DHCP so I actually *have* to use wicd to connect. Neither NetworkManager, nor ifconfig + iwconfig can do the trick, for some reason. It ends up in its useless ("blinking") state before it gets around to actually connecting.

I've had the luxury of owning two 3945 cards; one that worked out of the box, and this current one that I've pretty much given up on now. The setup is the same: I'm running Kubuntu 7.04 now, and I've also tried it with Ubuntu 7.10 tribe 4 and 5. It used to work even on the 7.04 Live CD on the old card, now it doesn't - not even in the latest Gutsy (a couple of weeks back). I've reinstalled ~5 times, hasn't worked satisfactorily once, so I've pretty much ruled out some freak accident while installing.

And I'd like to stress that the earlier card worked like a charm, even on the Live CD. This one just won't - or, well, it works after typing the magic commands, but then it disconnects randomly and I have to go type them again. If I'm at the computer at all.


There HAS to be hardware differences, or something similar to the extent that the driver, to put it simple, just doesn't work for us.



I'll keep an eye on this thread, so please reply if you get some response from the ipw3945 team, or something along those lines.

---

### Post by VoodooRider on 2007-09-06
Yes, exactly the same thing with my ASUS A8JR notebook with IPW3945. My wireless connection is also eth1 and sometimes it connects flawlessly on startup, but from time to time I do not get any connection and the OS is responding very slowly...

---

### Post by kaar3l on 2007-09-06
Same ipw3945 here, but i haven't had any that kind of problems. :/

Compal HGL31

---

### Post by Zorael on 2007-09-07
> **kaar3l said:**
> Same ipw3945 here, but i haven't had any that kind of problems. :/

This proves my point; it's very easy for some, and plain impossible for others. As posted above, I've had one of each 3945 card - one working, one not - so I "know" there's two different types. Call them revisions if you wish.



Anyway, I finally broke down and got me a PCMCIA wlan card; Netgear WGT-somethingsomething. Just Worked, out of the box.

ipw3945 is presently a lost fight (for us), until some benevolent developer fixes the driver.

---

### Post by kaar3l on 2007-09-08
lspci shows me this
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
so rev 02, what is your's?

---

### Post by Zorael on 2007-09-08
Mine says rev 02 as well - so far this is based on my deduction, through process of elimination.


What I do know:

- Some ipw3945 cards *Just Work*. This was the case for my first integrated one on this laptop (Acer Aspire 9815), before I sent it in to be serviced. Never any problems, especially not after I found wicd. This is the kind you have, the kind I miss sorely.

- Some ipw3945 cards *Just **Don't** Work*. They *can* be coaxed into connecting, but then the connection randomly breaks and you have to either reboot the machine or input some magic commands to beat it back in line. When it breaks the card is completely unresponsive, can't see any networks, and spams the 'Detected geography ABG (blahblah)' message in dmesg. If you're using the standard NetworkManager and you don't use DHCP, chances are it's already broken even after  rebooting, since it reads the /etc/network/interfaces file and sets the static IP accordingly upon startup (much like as if I typed 'sudo ifconfig eth1 add 192.168.0.2 broadcast 192.168.0.255' myself). I get the feeling it does this and attempts to automatically connect "too soon", putting it in a broken state before it actually become possible/feasible.

When I sent my laptop in to be serviced, they replaced the motherboard, and along with it the integrated ipw3945 chipset. After getting it back, I find I have the second kind, the Just Don't Work kind. I've had one of each, so I know it's not "just" a case of people scattered around the world who just fail at configuring networking.

If we, for the sake of the argument, assume that I'm just **completely clueless**, the fact remains that, with the second kind, I couldn't get it to connect without breaking on the Live CD - which *was* just the case of:

(0. Opening nm-applet-gnome-thingie)
1. Disabling wired connection (to be safe)
2. Setting up a static IP address, gateway, netmask, DNS and ESSID
3. Pressing apply.


Alternatively:

(0. Opening terminal, or CTRL+ALT+F2)
1. sudo ifconfig eth0 down
2. sudo ifconfig eth1 down
3. sudo ifconfig eth1 add 192.168.0.2 broadcast 192.168.0.255 netmask 255.255.255.0
4. sudo iwconfig eth1 essid Lappskole key [1] 1234567890 open channel 6
5. sudo iwlist scan eth1 *(to verify that it can see networks)*
6. sudo ifconfig eth1 up

Even if I'm completely clueless, that's still taking a big leap to say that I would fail with one or more of those three (or 6) steps. Repeatedly. With both Feisty and Gutsy builds, Ubuntu and Kubuntu.

Something I did manage, repeatedly and with considerable ease, earlier.

---

### Post by kaar3l on 2007-09-09
[http://ubuntuforums.org/showthread.php?t=297659](http://ubuntuforums.org/showthread.php?t=297659)
I found something interesting.

---

### Post by VoodooRider on 2007-09-09
Yes that might be the case. I remember when I switched CAM on  (disabled PSP) (windows xp), I had  quite a big  performance boost of my ipw3945 , so probably that could also help on ubuntu, but I have no idea where to find the proper setting.

---

### Post by Zorael on 2007-09-09
Most interesting.

However, would this at all explain why it stops being able to see networks?

[Regardless](http://ipw3945.sourceforge.net/README.ipw3945).

> The Intel PRO/Wireless 3945ABG Network Connection driver for Linux 
supports the configuration of the Power Save Protocol through a private 
wireless extension interface. The driver supports the following 
different modes:

	0       AC - Always ON
	1-5	Different levels of power management.  The higher the 
		Number, the greater the power savings, but with an impact to 
		packet latencies. 
	6	AC - Always ON
	7	BATTERY - Default setting for battery mode
	>7      AC - Always ON

```
zorael@azrael:~$ iwpriv eth1
eth1      Available private ioctls :
          set_power        (8BE0) : set   1 int   & get   0
          get_power        (8BE1) : set   0       & get  80 char
          set_mode         (8BE2) : set   1 int   & get   0
          get_mode         (8BE3) : set   0       & get  80 char
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get  16 char
          reset            (8BE7) : set   0 int   & get   0
          monitor          (8BE6) : set   2 int   & get   0

zorael@azrael:~$ iwpriv eth1 get_power
eth1      get_power:Power save level: 6 (AC) OFF
```

I haven't touched this setting, so it's at OFF by default. Unplugging the AC adapter leaves it at 6.

---

