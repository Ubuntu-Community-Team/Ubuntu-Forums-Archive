---
title: "wireless trouble on Fujitsu laptop"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by Edoardo_P on 2011-01-27
Hello everybody,

I've just installed Ubuntu desktop 10.10 on a Fujitsu Amilo laptop but it does not see any wireless network. It recognizes the wireless card but I don't know how to activate it or whether the drivers are already installed... what can I do? 
thank you very much

---

### Post by grahammechanical on 2011-01-27
How do you know that the wireless card is recognized if it does not see any wireless networks? Do you see a network icon? Is there a red exclamation mark set against it?

1) Some laptops require the wireless adapter/card to be switched on through an Fn + function key combination. Make sure that the card is switched on in hardware.

2) Right click the Network Manger icon. Is there a tick mark against the line Enable Networking and the line Enable wireless? By clicking on these lines you can activate or deactivate all networking (wired and wireless) or just wireless.

3) When networking is enabled the wireless card will scan for nearby wireless networks. Left click the icon and select your network. Authenticate with your wireless key.

If this works mark this thread as solved. If it does not work post information that will help identify what is happening or not happening. Remember, a re-boot is often required for changes to configuration to take affect.

Regards.

---

### Post by Edoardo_P on 2011-01-27
> **grahammechanical said:**
> How do you know that the wireless card is recognized if it does not see any wireless networks? Do you see a network icon? Is there a red exclamation mark set against it?

1) Some laptops require the wireless adapter/card to be switched on through an Fn + function key combination. Make sure that the card is switched on in hardware.

2) Right click the Network Manger icon. Is there a tick mark against the line Enable Networking and the line Enable wireless? By clicking on these lines you can activate or deactivate all networking (wired and wireless) or just wireless.

3) When networking is enabled the wireless card will scan for nearby wireless networks. Left click the icon and select your network. Authenticate with your wireless key.

If this works mark this thread as solved. If it does not work post information that will help identify what is happening or not happening. Remember, a re-boot is often required for changes to configuration to take affect.

Regards.

Thank you for the fast reply

I say that the wireless card is recognized just because... well, see below what the terminal says...


Here there is no network manager icon ... not in sight, at least

```


AMILO-Li-1718:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:e0:a2:eb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k  driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes  wireless=IEEE 802.11bg
       resources: irq:16 memory:c0000000-c000ffff

AMILO-Li-1718:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

```

---

### Post by Edoardo_P on 2011-01-27
P.S. yes, the laptop has a physical wifi switch, and it's "ON". at least it looks so, since its led light is switched on...

---

### Post by Edoardo_P on 2011-01-27
Problem solved... Just restarting the system... an idea of my girlfriend actually...  :roll:

---

