---
title: "how to find a device connected via ethernet"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by andru183 on 2010-11-12
Hey guys, I have a device (not a pc) connected to my pc via ethernet, it dose not show up in networks, I was hoping there was a way of scanning to detect for it, is there a way of seeing content of it is basically what I'm asking?

---

### Post by uncaspi on 2010-11-12
netstat -n

Try it if it shows up. Also see man netstat for other options

---

### Post by pricetech on 2010-11-12
Your router should show you a list of connected devices.  Probably listed as "connected computers" but it will show other stuff too.

---

### Post by SeijiSensei on 2010-11-12
Install a copy of **nmap** from the repositories and run the command "nmap -sP 192.168.1.0/24" replacing the last field with your network address and subnet.  This will ping all the hosts in the subnet and lists the ones it finds.

To determine your network subnet address, run "ifconfig" and see what IP address and "netmask" have been assigned to either eth0 (if its wired) or wlan0 (if its wireless).  The address will probably be something like 192.168.1.24 and the netmask something like 255.255.255.0.  If so, just follow the example I gave.  If the third digit is different, say 192.168.0.24, just replace the "1" with a "0" in the example.  

(The 255.255.255.0 netmask is represented by /24 in the example because the 32-bit binary number represented by 255.255.255.0 has 24 ones followed by eight zeros.)

---

### Post by andru183 on 2010-11-12
thanks for the info guys, its still a no show, I'm just give up on trying to find it, thanks for the help :)

---

### Post by pricetech on 2010-11-15
Is there a reset button on the device ??  Resetting to the factory defaults should activate a DHCP client which will pull an IP from your router.

---

