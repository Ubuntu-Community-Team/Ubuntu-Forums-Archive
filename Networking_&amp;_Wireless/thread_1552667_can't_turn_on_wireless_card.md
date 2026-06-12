---
title: "can't turn on wireless card"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by Ready2DropWin on 2010-08-13
I am having issues trying to turn on my wireless card. I have tried to use the ifconfig command to do so, but it gave me an error.
```

@ubuntu-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

```

This is what I get when I type iwconfig
```

@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

vboxnet0  no wireless extensions.

```

Is there another way to go about this? Thanks in advance.

---

### Post by Ready2DropWin on 2010-08-13
Also this is what I get when I type lspci
```

07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Hewlett-Packard Company Device 1381
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

---

### Post by wojox on 2010-08-13
Give this a read. They got it fixed at the end [my wirless is disabled...can I enable it through the terminal?]("http://ubuntuforums.org/showthread.php?t=1552496")

---

### Post by Ready2DropWin on 2010-08-13
Thanks wojox, I am giving all of it a read now.

I have tried these commands so far, and still got the same error as before.

```

rmmod ath9k
rfkill block all
rfkill unblock all
modprobe ath9k
rfkill unblock all
ifconfig wlan0 up

```

---

### Post by wojox on 2010-08-14
Try:

```
sudo ifconfig wlan0 down
```

Reboot and

```
sudo ifconfig wlan0 up
```

---

### Post by Ready2DropWin on 2010-08-14
> **wojox said:**
> Try:

```
sudo ifconfig wlan0 down
```Reboot and

```
sudo ifconfig wlan0 up
```


I just tried it and i am still getting the same error when I type
```
 sudo ifconfig wlan0 up
```

---

### Post by Ready2DropWin on 2010-08-14
I am still having no luck getting my wireless card to turn on.

---

### Post by Ready2DropWin on 2010-08-14
On the other note, I have a wireless card button on my laptop. If i hold the button down it will turn blue for a second, then turns back orange and I get a message that the wireless card has been disabled.

---

### Post by Ready2DropWin on 2010-08-15
> Yesterday, all was fine but this morning my HP TX1000 Laptop wouldn't auto connect to my wireless router (1 metre away). I remembered that on the bootup Wireless Assistant turned on Bluetooth but not Wireless. In the Network and Sharing Centre, "Manage Wireless Networks" isn't showing so I can't turn it on. In what may be a related issue, I can't get into Services - Vista says that either I don't have permission (I'm logged on as Administrator) or it can't find Windows/System32/Services.msc (which I can't see). I've done the obligiatory re-start and I've connected via cat5 but I need to resolve this - can anyone help?
==============
[Incident Management Software]("http://www.livetime.com/itil-service-management/service-manager/incident-management/")
[embedded code coverage]("http://www.vectorcast.com/software-testing-products/embedded-code-coverage.php")

I would try setting your bios setting to default. I think it is all the same on all hp machines, reboot hit F10, then hit F9 (Yes), and then F10 (Yes). And see what that does, I have tried it and so far no good, you are using windows so I guess we will see.

---

### Post by Ready2DropWin on 2010-08-17
How can I tell in ubuntu if my wireless card is an hardware issue and not a driver issue, or both?

---

