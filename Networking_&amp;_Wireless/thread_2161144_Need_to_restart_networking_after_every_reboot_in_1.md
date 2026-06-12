---
title: "Need to restart networking after every reboot in 13.04 server"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by smillette on 2013-07-09
Hello,

I am fairly new to Linux and have setup 13.04 on a media server that is to be kept in a closet. I found that every time the box boots I have to restart networking to get connectivity, which makes it unusable.

I have setup br1 with a static IP address and em1 pulls an address from the DHCP. From another post's recommendation I just had networking restart when the box was booting, but this caused em1 to disappear completely. What direction should I be looking to fix this?

thanks,

---

### Post by duanedesign on 2013-07-09
Check /etc/network/interfaces. It should have an "auto" line for your interface.
ex:  auto br1

Could you post your /etc/network/interfaces file.
You can output the file contents in the terminal with the command:

```
cat  /etc/network/interfaces
```

If you have to use the workaround are you restarting networking at boot by editing /etc/rc.local to include the line "/etc/init.d/networking start" (do not use sudo in this file, it is run at startup with root permissions).

---

### Post by smillette on 2013-07-10
From cat /etc/network/interfaces/ I got the following output

auto lo
iface lo inet loopback

#auto em1

auto br0 inet static
address 192.168.3.2
netmask 255.255.255.0
gateway 192.168.3.1
bridge_ports em0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

---

### Post by smillette on 2013-07-11
Just seeing if anyone can help on this issue. I have verified from ifconfig and netstat that em1 has a valid ip address assigned by DHCP. 

I am not able to ping the internet or the gateway without restarting the networking adapters. 

I edited the rc.local file with networking start and this didn't fix the problem.

---

### Post by steeldriver on 2013-07-11
Maybe explain a bit more what you're trying to do? why the bridged interface? why do you only have only em0 in your bridge_ports list when you only have an actual interface definition for em1 (and that is commented out... )

What actual NICs do you have in the box?

---

### Post by smillette on 2013-07-11
Ok I was able to solve the issue I was having. After your questions regarding commenting out the em1, I changed it to

auto em1
iface em1 inet manual

...
bridge_ports em1

I am not sure why this solved the problem and why I was previously able to get the networking to work if I restarted the adapters. Thanks for pointing me in the right direction.

---

