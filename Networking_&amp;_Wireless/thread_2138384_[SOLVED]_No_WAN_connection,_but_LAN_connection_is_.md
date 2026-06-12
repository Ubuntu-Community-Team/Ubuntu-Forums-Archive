---
title: "[SOLVED] No WAN connection, but LAN connection is OK"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by dpechiu on 2013-04-23
After the last automatic update internet is down whether I use wifi or  ethernet. I use Ubuntu 12.04 on a Dell XPS laptop.
I can connect to the router, and use the web interface to configure it. I can ping all devices on the LAN side successfully. Pinging any site on the WAN side fails.  All other PCs, tablets, and  phones on the same LAN can connect to the internet no problem.
I have rebooted the laptop and the router many times.  I have reset  router to default settings and no success. Router is at 192.168.1.254  and laptop is at 192.168.1.3 set by DHCP. I am not using any firewall  software.  This is most likely a software issue not a router/hardware issue.
Any tips to fix my connection  before I install new version of Ubuntu from a CD?  Thanks in advance!

[PHP]ifconfig
eth0 Link encap:Ethernet HWaddr 00:21:9b:db:5a:ca
    UP BROADCAST MULTICAST MTU:1500 Metric:1
    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) Interrupt:17

lo Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
wlan0 Link encap:Ethernet HWaddr 00:1d:e0:50:c8:d1
    inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
    inet6 addr: fe80::21d:e0ff:fe50:c8d1/64 Scope:Link
    UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
    RX packets:162 errors:0 dropped:0 overruns:0 frame:0
    TX packets:182 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:30715 (30.7 KB) TX bytes:23103 (23.1 KB)

netstat -nr
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
0.0.0.0 192.168.1.254 0.0.0.0 UG 0 0 0 wlan0
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 wlan0
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 wlan0[/PHP][COLOR=#008000][/COLOR]

---

### Post by Iowan on 2013-04-23
Are you pinging the WAN by name or IP address (or both)?
If via IP works, it may be DNS problem.

---

### Post by dpechiu on 2013-04-23
I've pinged websites by name.  Firefox cannot connect to any site.  Skype cannot connect to its server. That's how I concluded that I can't connect to the WAN.  Keep in mind that all other devices on the LAN have no DNS trouble.

---

### Post by Iowan on 2013-04-23
Try an IP ping... 173.194.46.72 or 8.8.8.8.

You might also check Network Manager connection information to see if it shows a valid DNS Server.

---

### Post by dpechiu on 2013-04-23
Pinging both out those IPs works! I don't have network manager installed, and can't use apt-get cause of the dns issue...

I found edit connections from the top bar and added the opendns IPs. Also I edited /etc/dhcp/dhclient.conf and added the IPs there as well. Still it doesn't work. 

I can browse google if I use it's IP address...

---

### Post by Iowan on 2013-04-24
> **dpechiu said:**
> I found edit connections from the top bar and added the opendns IPs.:confused: That's what I've been calling Network Manager> **dpechiu said:**
>  Also I edited /etc/dhcp/dhclient.conf and added the IPs there as well.Where in */etc/dhcp/dhclient.conf * did you add them?
Did you reboot or restart networking after making the changes?
*/etc/resolv.conf* is another place to look. My machine has **nameserver 127.0.0.1** in */etc/resolv.conf*, but the Connection Information shows the proper DNS server. The DHCP server *should* provide this info.

[Here]("http://ubuntuforums.org/showthread.php?t=2078398&page=2") is a DNS-changing thread that might be helpful.

---

### Post by dpechiu on 2013-04-24
Thanks for you reply! 
Yes I was confused by what you called Network Manager. I couldn't find any tool named as such when looked for it.
Regardless, I've set the ipv4 to Automatic (DHCP) addresses only, and it allowed me to enter a DNS. 
I've added 208.67.222.222, 208.67.220.220 there

On opendns.com I found out how to add the DNS addresses for Ubuntu from : [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

```
sudo gedit /etc/dhcp3/dhclient.conf
```

Added
```
supersede domain-name-servers 208.67.222.222,208.67.220.220;
```

..right before the require subnet-mask line.

I then rebooted the machine, but no cigar.

I did check out the thread you mentioned and I did exactly the steps mentioned for Ubuntu Desktop, as that's what I have.

I did not look at */etc/resolv.conf *as that gets overwritten according to most threads I've read.

---

### Post by Iowan on 2013-04-24
I usually use the **prepend domain-name-servers** line to add my choice servers to the top of whatever list DHCP provides...
As an aside - it is recommended to use **gksudo** with graphical apps like nautilus or gedit.

I presume */etc/network/interfaces* has only setup for **lo** (loopback device). If eth0 is defined there, NM will probably ignore it (although eth0 should not show up in NM, then).

---

### Post by dpechiu on 2013-04-24
/etc/network/interfaces contains:
auto lo
iface lo inet loopback

I've added the IPs as you suggested with prepend, rebooted, and still no go. "Connection Information" does show the DNS IPs correctly.

---

### Post by dpechiu on 2013-04-24
Update:
Skype was able to connect.
Firefox and Update Manager do not work

---

### Post by steeldriver on 2013-04-25
Have you checked that the resolvconf service is running and that /etc/resolvconf is correctly symlinked?

```

service resolvconf status

ls -l /etc/resolvconf

```

If you're using network-manager, then I don't think it's necessary to mess with dhclient in order to set alternative DNS servers, you can do it by editing the connection in the nm-applet GUI - if you're using DHCP you can change 'Automatic (DHCP)' to 'Automatic (DHCP) addresses only' then add your DNS IPs in the boxes below.

---

### Post by jdthood on 2013-04-25
The problem could also be with the local NetworkManager-controlled forwarding nameserver. See if disabling it helps. To disable the local forwarding nameserver, "gksudo gedit /etc/NetworkManager/NetworkManager.conf", comment out the line "dns=dnsmasq" (put a '#' at the beginning of the line), save the file and then reboot. After that you should see the remote nameserver addresses in resolv.conf instead of 127.0.0.1, the address of the local nameserver.

---

### Post by dpechiu on 2013-04-25
The response to > 
service resolvconf status 
is:
>  resolvconf start/running

---

### Post by dpechiu on 2013-04-25
I commented out dns=dnsmasq in NetworkManager.conf and rebooted but still cannot browse or use update manager.
> #dns=dnsmasq

Update:

I found /etc/resolv.conf and there was complete garbage in it.
> search mosys.lan mosys.com
nameserver 192.168.6.128
nameserver 207.5.0.50


I removed all 3 lines and added 
> nameserver 208.67.222.222
nameserver 208.67.220.220


 I'm now writing you from my Ubuntu laptop which can now browse websites and update manager works as well. 

The issue is partially fixed because I restored functionality, but we haven't found the root cause. The next question is why does resolv.conf not update automatically from Network Manager?  NM has the correct info, and had it the whole time, whether I used my ISP's DNS or opendns.com DNS. How the garbage ended up in /etc/resolv.conf is beyond me.

---

### Post by jdthood on 2013-04-26
Something appears to have trashed your /etc/resolv.conf. Run "sudo dpkg-reconfigure resolvconf" to reinstall the symbolic link /etc/resolv.conf -> ../run/resolvconf/resolv.conf.

---

### Post by dpechiu on 2013-04-26
Before running the command /run/resolvconf/resolv.conf did not exist.

After running > sudo dpkg-reconfigure resolvconf and rebooting the machine the symbolic link was created, and /etc/resolv.conf contained 4 lines instead of 2 but I don't care at this point.
> nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 208.67.222.222
nameserver 208.67.220.220

This evening I will change the DNS in my router back to the ISP DNS to see if it gets updated in /etc/resolv.conf, and will report my findings here.  In the mean time thanks for all your help!

---

### Post by dpechiu on 2013-04-27
So I've changed the DNS adresses in the router to the ones provided by  my ISP.  However, the Ubuntu laptop was still using the opendns.com ones.  I had to backtrack and revert all the changes I've made:

In /etc/dhcp/dhclient.conf I've commented out the prepend domain... line
#prepend domain-name-servers 208.67.222.222, 208.67.220.220;

In /etc/NetworkManager/NetworkManager.conf I've removed the comment from the line below:
dns=dnsmasq

I then went to Network Manager and changed ipv4 to Automatic DHCP without providing any DNS addresses.

Now "Connection Information" reports my router's IP as the DNS.

/etc/resolv.com  shows first my router'sIP address then the two from opendns.com.  So I  guess I'm using the ISP one from the router, and as a fallback I have  the opendns.com ones too.  Sweet!

So my /etc/resolf.conf was trashed, and the symbolic link was broken preventing me from having a correct DNS server. The fix for this was 
>                                                          sudo dpkg-reconfigure resolvconf                      

**Thank you all for your help! You have saved me hours of insalling a new distro and coniguring it to my liking!!!**

---

### Post by nachwaal3ab on 2013-04-28
[COLOR=#000000]I've pinged websites by name. Firefox cannot connect to any site. Skype cannot connect to its server. That's how I concluded that I can't connect to the WAN. Keep in mind that all other devices on the LAN have no DNS trouble.[/COLOR]

---

