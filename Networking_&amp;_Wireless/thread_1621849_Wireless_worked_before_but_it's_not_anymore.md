---
title: "Wireless worked before but it's not anymore"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by ace14_007 on 2010-11-14
Hello, 

I have Windows 7 professional installed. Then I I installed ubuntu 10.10. So now I have both in different partitions. 

My computer used to connect to wifi fine. But since last 4 days, it's not.


So i read somewhere to type the following commands. I am posting the returns here. 



faraz@faraz-laptop:~$ rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no


faraz@faraz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power= off   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off

Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Hewlett-Packard Company Device 137a
        Physical Slot: 1
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at d2600000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k



Can somebody help me with this.

Thanks in advance.

Additional Information (if it's helpful)
My computer used to connect to wifi fine.  Then I heard about Kubuntu. So I installed kubuntu-Desktop through shell. So I would logout from ubuntu and get into kubuntu. It asks for the wifi password. I put it again and again but it just gets stuck somewhere. But still after 2, 3 days of installation of Kubuntu 10.10, and after several shutdowns/restarts, the wireless internet was working on ubuntu (not in kubuntu, and i didn't care). But now it's not working. I have to connect the ethernet cable to get it to work.

---

### Post by uncaspi on 2010-11-14
Your device is blocked. try rfkill unblock

---

### Post by ace14_007 on 2010-11-15
Hurray!!! It's working now. 

You should have told me the proper and full command. 

I used rfkill unblock 1
and rfkill unblock 2

Also, When I point my mouse over the wireless network connection icon, the speed is fluctuating. (between 85 to 95 %) Why is that
What's wrong?

---

