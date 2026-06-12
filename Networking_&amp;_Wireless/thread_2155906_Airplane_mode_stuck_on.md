---
title: "Airplane mode stuck on??"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by jonnymopar on 2013-06-19
Hi all, Compaq nc8430 running Ubuntu 12.04/Cinnamon.

This all started when I brought my laptop to someone else's house and tried to connect to their wireless.  My wireless at home has been working for over a month without any problems.

When I went into Network Settings to connect to a different network, I noticed that my wireless connection was "Unmanaged".  After poking around online for a solution, I edited NetworkManager.conf and set managed=true.  The wifi hasn't worked since, even after changing it back to false.  If I go into Network Settings now, Airplane Mode won't turn off and my wifi won't turn on.  Regular ethernet works fine, which is how I'm posting this.

No matter what I try, every time I type in **ifconfig wlan0 up**, I get the RF-kill error, even after typing **rfkill unblock all**.  I know that my physical wifi enable button on my laptop works because "hard blocked" will toggle between yes and no each time I press it.  Here's my network adapter:

*08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express [14e4:16fd] (rev 21)*

I've read all about people having problems with the Broadcom driver, but in all the lists of problematic devices, this one isn't listed.

Anything else I can try?  Driver reinstall maybe? (which I actually don't know how to do)

---

### Post by leg on 2013-06-20
I recently had problems with wifi (Broadcom card) after a reinstall and my problem was the wrong driver. This doesn't appear to be yours because it was working. Airplane mode on my laptop was stuck on when I had the physical wifi button toggled off. Is it possible that while your laptop was on the move you have physically switched it off?

---

### Post by chili555 on 2013-06-20
> 08:00.0 [COLOR="#FF0000"]Ethernet[/COLOR] controller [0200]: Broadcom Corporation NetXtreme BCM5753M Gigabit [COLOR="#FF0000"]Ethernet[/COLOR] PCI Express [14e4:16fd] (rev 21)This is not your wireless device. Please post:```
lspci -nn | grep 0280
rfkill list all
```>  Is it possible that while your laptop was on the move you have physically switched it off? My thought exactly. What does the wireless button do when you press it? Does the LED change? Does it change the result of:```
rfkill list all
```

---

### Post by jonnymopar on 2013-06-20
> **chili555 said:**
> This is not your wireless device. Please post:```
lspci -nn | grep 0280
rfkill list all
```

Nope, it's not!  I posted the wrong line.  I'll try this again when I'm back home tonight.

> **chili555 said:**
> My thought exactly. What does the wireless button do when you press it? Does the LED change? Does it change the result of:```
rfkill list all
```

There is an LED, but it's not illuminating. With the Linux driver, the LED indicates wifi enabled as well as wifi activity (blinks with activity - very cool).  Originally with Windows, it was merely an enable/disable indicator.

 However, in my original post, I noted that I believe the wifi enable button is working, since "hard blocked" under wifi changes with each button press.  I don't have the laptop with me, but it's like this:

run **rfkill list all**
soft blocked = no
hard blocked = no
press wifi button
run **rfkill list all** again
soft blocked = no
hard blocked = yes
press wifi button again
run **rfkill list all** again
soft blocked = no
hard blocked = no

and so on,and so forth.

I'll have more information tonight.  Thanks for the quick responses.

---

### Post by chili555 on 2013-06-20
Let's see what the device is, be sure you have the correct driver and proceed from there.

---

### Post by jonnymopar on 2013-06-20
**lspci -nn | grep 0280** returns:

```
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
```

**rfkill list all** returns:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

If I press the wifi enable button, I get this:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
```

Press it again, and it goes back to the first one. 

Now, if I enter **rfkill unblock all**, the LED turns ON, and I get this:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

Press the wifi button, LED goes off and I get this:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
```

At no time am I able to connect to the wifi.  Here's the error I get after I enter **ifconfig wlan0 up**:

```
SIOCSIFFLAGS: Operation not possible due to RF-kill
```

At no point in between any of these instances am I able to connect, not with ifconfig and not from within Network Settings.  Also, I have no clue what hci0 is, but it only shows up immediately after an **unblock all**.

Thank you for your help.

---

### Post by chili555 on 2013-06-21
Notice that at no point, could you change:> 0: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="#FF0000"]Hard blocked: yes[/COLOR]I suspect the little module that transfers key presses into action has a bug. It is called hp-wmi. You can verify with:```
lsmod | grep hp
```Do you see hp-wmi listed as a loaded module? Let's try to remove it and see what we can do from there:```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
rfkill list all
```Any change? Improvement?

---

### Post by jonnymopar on 2013-06-21
Yup, it's there:

```
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
wmi                    18744  1 hp_wmi
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
```

Entered the lines you recommended.  Now **rfkill list all** returns:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

Pressing the wireless enable button doesn't change the above.  Unfortunately, Network Settings is acting exactly the same.  Airplane mode won't turn off, wireless "unavailable" and unable to turn on.  **ifconfig wlan0 up** still returns the same error.

I sincerely appreciate the help you've offered so far.

---

### Post by Hadaka on 2013-06-21
Hi,probably an obvious question, but.. have you tried
clicking the white area next to the on indicator? That 
"may" turn it off..also, have you reset the BIOS to default?
good luck.

---

### Post by jonnymopar on 2013-06-25
I tried clicking in the area as you said, and it didn't work.  I'm thinking that even if I was clicking in the wrong area, I would still be able to get it to work manually via terminal.

BIOS settings were reset, no change.  Nothing in the BIOS was changed originally, but I tried it for the hell of it.

---

### Post by jonnymopar on 2013-06-27
If I wanted to uninstall and reinstall the driver for the wifi, how would I do that?  I tried ```
modprobe -r iwl3945
``` and ```
modprobe -r iwl_legacy
``` but they reappear when I restart the computer.

---

### Post by jonnymopar on 2013-06-28
Ok, so I'm not exactly sure how, but I got rid of the Airplane mode being stuck on.  Here's what's happening now: if I enter ```
sudo ifconfig wlan0 up
``` the wifi activity light come on and starts blinking away.  But I can't connect to anything.  Entering ```
sudo ifconfig wlan0 down
``` turns it back off.

On top of all this, wireless is "unavailable" in Network Settings.  That, I haven't figured out how to change.

Once I enter **ifconfig wlan0 up**, typing **ifconfig** returns this:

```
eth0      Link encap:Ethernet  HWaddr 00:17:a4:d2:7b:08  
          inet addr:192.168.8.107  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::217:a4ff:fed2:7b08/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2596677 (2.5 MB)  TX bytes:548160 (548.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:780 (780.0 B)  TX bytes:780 (780.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:49:50:1b  
          inet6 addr: fe80::219:d2ff:fe49:501b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3307 (3.3 KB)  TX bytes:10704 (10.7 KB)


```

---

