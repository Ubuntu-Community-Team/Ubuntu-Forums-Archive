---
title: "wireless and wired connections don't work at the same time"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2009-08-10
I have seen others post this problem with no solution.  If I am connected to a wireless signal to get internet connectivity and then connect to a local wired connection with a static I.P. address, I lose my internet connectivity.  How do I get both connections to stay active?

--shaun

---

### Post by Macchi on 2009-08-10
The Network Manager will try to keep ONE connection as your Gateway to the internet and will disconnect others with lower priority.
The highest priority is for faster connections, for instance a wired (ethernet cable) supersedes the wireless (WiFi) that supersedes the Mobile Broadband.

One way to keep the network manager away from an interface is to configure it manually in /etc/network/interfaces. Tell us more about your application and we may provide more specific solutions and hints.

---

### Post by senor_smile on 2009-08-12
> **Macchi said:**
> The Network Manager will try to keep ONE connection as your Gateway to the internet and will disconnect others with lower priority.
The highest priority is for faster connections, for instance a wired (ethernet cable) supersedes the wireless (WiFi) that supersedes the Mobile Broadband.

One way to keep the network manager away from an interface is to configure it manually in /etc/network/interfaces. Tell us more about your application and we may provide more specific solutions and hints.

Specifically, I need to be able to stay connected to the wifi connection(or verizon mobile internet connection) while connected via a crossover cable on the wired connection to to be able to transfer things from the internet to the device I am connected to over the wired connection, which itself does not have internet.   

I will try to configure my eth0 through /etc/network/interfaces to see if I'm able to keep both connections alive.  Thanks!

--shaun

---

### Post by superprash2003 on 2009-08-12
yea, that should work ideally..you could even perform ICS to share the internet with the other machine

---

### Post by senor_smile on 2009-08-12
I tried it and it doesn't work.  I can get either connection working independently just fine.  When both are connected, the wired connection takes precedence and kills the internet connection of the wireless.  

The device that I'm talking to over the wired connection does not have a monitor/keyboard on which to do anything, which is why I have to connect up to it via the wired connection to transfer files in the first place. 

I must add that I only configured eth0 through /etc/networking/interfaces.  The wireless is still managed by the network-manager.  I have connected to wireless connections in the past using nothing but the command line, but that is not ideal as this is a laptop that moves from place to place, and I need the wireless connection to work automatically.

---

### Post by superprash2003 on 2009-08-13
post the contents of your interfaces file , what static ip have you assigned to the 2interfaces?

---

### Post by Macchi on 2009-08-13
> senor_smile; 
Specifically, I need to be able to stay connected to the wifi connection(or verizon mobile internet connection) while connected via a crossover cable on the wired connection to to be able to transfer things from the internet to the device I am connected to over the wired connection, which itself does not have internet.

Señor Smile, do you mean you intent to keep both interfaces active because you want Internet Connection Sharing (from the wireless to the cable)?

Yes it is possible to share the connection easily with Firestarter, a firewall with ICS that is on the repositories and will not require messing around with IPtables.
Configure your eth0 in /etc/network/interfaces and it will not be touched by the network manager. Then you will be able to keep both network interfaces active and set ICS on firestarter.

---

### Post by Iowan on 2009-08-13
Probably self-evident, but you'll need to restart networking - or reboot - to see effects of changes. I usually opt for reboot to insure NM and interfaces file both get reset.

---

### Post by Macchi on 2009-08-14
> **Iowan said:**
> Probably self-evident, but you'll need to restart networking - or reboot - to see effects of changes. I usually opt for reboot to insure NM and interfaces file both get reset.

One way to do that is to disable networking by right-clicking on the NM icon on the upper panel and then re-enable it. I also believe that you can also issue the following command to restart networking: 
```
sudo /etc/init.d/networking restart
```
But I know that the NM may not be affected by that. Another way to restart the network manager and control it from the command line is a tool called cnetworkmanager.

---

### Post by xbyte1024 on 2011-05-30
I had the same problem.
If I plugged the Ethernet cable, the wireless was disabled.
Finally I found a bios setting (LAN/WLAN switch) I thing. I disabled that setting and problem solved.
I am working in a compaq laptop.

---

### Post by Iowan on 2011-05-30
Thread is over a year old.
R.I.P

---

