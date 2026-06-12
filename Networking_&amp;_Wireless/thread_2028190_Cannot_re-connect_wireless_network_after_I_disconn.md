---
title: "Cannot re-connect wireless network after I disconnected it"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by zurga on 2012-07-17
I disconnected Wireless network from the network drop down menu to test the wired network. Now I cannot find any way of reconnecting Wireless. Symptoms are:

[LIST]
[*]Network drop down menu says "Wireless is disabled by hardware switch"
[*]SystemSettings/Network/Wireless lists the Wireless MAC address, and says "Wireless Unavailable". It has a virtual on/off switch which shows "OFF". If I try to toggle it to "ON", it drops back to "OFF" as soon as I pull the mouse away from it.
[*]The computer does have a hardware switch for wireless which is in the "ON" position, and the Wireless does comes on normally if I boot into Windows7
[*]The command "sudo lshw -C network" displays lists the wireless network as:
[LIST]
[*] *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc., etc., etc.
[/LIST]
 
[*]The Wireless hardware switch incorporates an indicator light which should glow on, and it does with Windows7, and it did with Ubuntu as well, but not now.
[/LIST]
I did not expect my act of soft disconnection to almost change the hardware! Any help will be greatly appreciated.

---

### Post by Cheesehead on 2012-07-17
> **zurga said:**
> 
[*]Network drop down menu says "Wireless is disabled by hardware switch"

[*]The computer does have a hardware switch for wireless which is in the "ON" position, and the Wireless does comes on normally if I boot into Windows7

[*]The Wireless hardware switch incorporates an indicator light which should glow on, and it does with Windows7, and it did with Ubuntu as well, but not now.



What happens if you turn the hardware switch (not the menu switch) off then on again? 

If the system thinks the hardware switch is in the 'off' position, then it will corectly refuse to turn it back on in software. That is precisely why the hardware switch exists. (And there are ways around it.)

---

### Post by zurga on 2012-07-18
> **Cheesehead said:**
> What happens if you turn the hardware switch (not the menu switch) off then on again? 

If the system thinks the hardware switch is in the 'off' position, then it will corectly refuse to turn it back on in software. That is precisely why the hardware switch exists. (And there are ways around it.)
You have expressed it exactly: The system thinks the hardware switch is "OFF", to the extent that even the indicator light does not glow. I have tried already tried various combinations of turning the h/w switch on & off, with no consequence.

---

### Post by zurga on 2012-07-18
I spent the best part of a day to resolve the problem.  The command

[LIST]
[*]zurga@ubuntu:~$ iwconfig
[/LIST]
displayed many lines including

[LIST]
[*]wlan0     IEEE 802.11bgn  ESSID:"Emmanuelle"
[/LIST]
indicating that wlan0 is the network to be examined. The command

[LIST]
[*]zurga@ubuntu:~$ ip link show | grep wlan0
[/LIST]
displayed the line 

[LIST]
[*]3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state DOWN qlen 1000
[/LIST]
indicating the problem to be 'state DOWN'. So I used the command

[LIST]
[*]zurga@ubuntu:~$ sudo ip link set wlan0 up
[/LIST]
to get the state to go up, but it returned

[LIST]
[*] RTNETLINK answers: Operation not possible due to RF-kill
[/LIST]
which indicated rfkill problem. Used the rfkill command to determine the problem:

[LIST]
[*]zurga@ubuntu:~$ rfkill list
[/LIST]
which returned:

[LIST]
[*]0: sony-wifi: Wireless LAN
[/LIST]

[LIST]
[*]    Soft blocked: yes
[/LIST]

[LIST]
[*]    Hard blocked: no
[/LIST]

[LIST]
[*]1: phy0: Wireless LAN
[/LIST]

[LIST]
[*]    Soft blocked: yes
[*]    Hard blocked: yes
[/LIST]
indicating wireless LAN (wlan0) is blocked. Hence unblocking and listing the state again:

[LIST]
[*]zurga@ubuntu:~$ rfkill unblock 0 wlan
[*]zurga@ubuntu:~$ rfkill list
[*]0: sony-wifi: Wireless LAN
[*]    Soft blocked: no
[*]    Hard blocked: no
[*]1: phy0: Wireless LAN
[*]    Soft blocked: yes
[*]    Hard blocked: no
[/LIST]
Now nothing is hard blocked. So repeating

[LIST]
[*]zurga@ubuntu:~$ sudo ip link set wlan0 up
[/LIST]
this time it worked, and wlan0 burst into life.

---

