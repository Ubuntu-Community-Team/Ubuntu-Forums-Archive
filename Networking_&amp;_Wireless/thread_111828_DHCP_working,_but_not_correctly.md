---
title: "DHCP working, but not correctly"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by mikerobinson on 2006-01-03
I have been trying to use my ubuntu box to share the internet connection with my windows box with dhcp. I have a dhcp server set up and the windows box can connect to it fine. I can ping the ubuntu box and even browse a Samba share that I set up, however I can't browse the web from the windows box.

When I try to send a ping from it, the DNS resolves (i.e. if I try to ping yahoo.com it tries to ping 66.94.234.13) but I get no response from the remote server.

On my ubuntu box (well actually kubuntu), I have eth0 connected to the internet via my ISP's dhcp server. eth1 is running dhcp3-server with the following configuration in /etc/dhcp3/dhcpd.conf (all comments omitted)
> ddns-update-style none;

log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  #option domain-name-servers 196.40.31.205, 196.40.31.205;
  option domain-name "amnet.co.cr";
 
  option domain-name-servers 192.168.0.1,192.168.0.2;

  option routers 192.168.0.1;
  option broadcast-address 192.168.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}

and here is my *ifconfig* output:
> eth0      Link encap:Ethernet  HWaddr 00:48:54:1E:0E:84
          inet addr:10.39.1.198  Bcast:10.39.255.255  Mask:255.255.0.0
          inet6 addr: fe80::248:54ff:fe1e:e84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:299352 errors:4 dropped:0 overruns:0 frame:2
          TX packets:23286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31196855 (29.7 MiB)  TX bytes:2048640 (1.9 MiB)
          Interrupt:11 Base address:0xd000

eth1      Link encap:Ethernet  HWaddr 00:40:F4:9C:66:08
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe9c:6608/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:967269 (944.5 KiB)  TX bytes:4299361 (4.1 MiB)
          Interrupt:5 Base address:0xcc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1591 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:134137 (130.9 KiB)  TX bytes:134137 (130.9 KiB)


I have tried everything I can think of, but can't quite seem to get it to work. Any help would be appreciated.

---

### Post by ape on 2006-01-03
Looks like you don't have ip-forwarding and NAT enabled on your Ubuntu box.  Check out this link [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html]("http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html")

for more information.

---

### Post by tokyovigilante on 2006-01-03
Your problem is most likely iptables, but first a couple of questions to clarify:

1. Does your XP box recieve an IP via DHCP (If yes then DHCP is working correctly).

2. Does your Ubuntu box connect to the net? (I'm guessing yes)

3. You specify local DNS servers in your dhcpd.conf, are these explicitly running with bind9 or dnsmasq? If yes thats cool, but if not, or you have no idea what I just said ;) set them to the DNS servers your ISP provides.

4. Did you specify the interface to run DHCP on in your /etc/default/dhcpd3?

As I mentioned above, if everything I've asked about above is already set up or not applicable to you, then you most likely haven't set up iptables (which is the Linux routing system) to forward traffic to your local network. I suggest installing Firestarter (sudo apt-get install firestarter) and enable Internet Sharing. This will set up forwarding for you, and is also a convenient way to set up an iptables firewall.

Let me know if you have any problems with the above.

---

### Post by mikerobinson on 2006-01-03
[QUOTE=ape]Looks like you don't have ip-forwarding and NAT enabled on your Ubuntu box.  Check out this link [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html]("http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/firewall-examples.html")

for more information.[/QUOTE]
wow that is just really confusing to me. I don't have RedHat or Slackware (which is why i'm posting in the ubuntu forums), so i don't have an /etc/rc.d/ directory (only rc0.d - rc6.d which contain files that link to the /etc/init.d directory).


[QUOTE=tokyovigilante]Your problem is most likely iptables, but first a couple of questions to clarify:

1. Does your XP box recieve an IP via DHCP (If yes then DHCP is working correctly).

2. Does your Ubuntu box connect to the net? (I'm guessing yes)

3. You specify local DNS servers in your dhcpd.conf, are these explicitly running with bind9 or dnsmasq? If yes thats cool, but if not, or you have no idea what I just said ;) set them to the DNS servers your ISP provides.

4. Did you specify the interface to run DHCP on in your /etc/default/dhcpd3?

As I mentioned above, if everything I've asked about above is already set up or not applicable to you, then you most likely haven't set up iptables (which is the Linux routing system) to forward traffic to your local network. I suggest installing Firestarter (sudo apt-get install firestarter) and enable Internet Sharing. This will set up forwarding for you, and is also a convenient way to set up an iptables firewall.

Let me know if you have any problems with the above.[/QUOTE]

1) Yes, it receives an IP and I can ping the ubuntu box and connect to the Samba shares I have set up
2) Yes
3) I'm not sure what exactly you mean by the DNS servers running with bind9 or dnsmasq. I tried both with my ISP's DNS servers (which are now commented out) and with just guessing them. However, they seem to be working because I can resolve a name to an IP from the windows box, just nothing responds when I try to reach the IP.
4) I chose the device to use when installing. I don't have /etc/default/dhcpd3 but I do have /etc/default/dhcp3-server (which contains the device I use for the dhcp server, eth1)

I followed the instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=91370") to set up iptables and install dnsmasq. Maybe I have changed other settings in the meantime and I need to do it again. I seem to remember installing Firestarter before on an old Redhat box and I couldn't connect at all after that and I couldn't even figure out how to revert the changes. Wouldn't the command [FONT="Courier New"]iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE[/FONT] set up IP forwarding for me? (eth0 is the device that connects to the internet and eth1 is the one that connects to the windows box)

Thanks again

---

### Post by tokyovigilante on 2006-01-03
[QUOTE=mikerobinson]wow that is just really confusing to me. I don't have RedHat or Slackware (which is why i'm posting in the ubuntu forums), so i don't have an /etc/rc.d/ directory (only rc0.d - rc6.d which contain files that link to the /etc/init.d directory).[/QUOTE]
Don't worry too much, you should be able to get things running with Firestarter without resorting to manual iptables hacking. The info at TLDP is a bit out of date, and not really aimed at Debian-based systems like Ubuntu.




[QUOTE=mikerobinson]1) Yes, it receives an IP and I can ping the ubuntu box and connect to the Samba shares I have set up[/QUOTE] 
OK cool, DHCP is fine. I'm not sure what DNS servers it's passing your network (ie your XP box) though.

[QUOTE=mikerobinson]
2) Yes
[/QUOTE]
OK that's not an issue then

[QUOTE=mikerobinson]
3) I'm not sure what exactly you mean by the DNS servers running with bind9 or dnsmasq. I tried both with my ISP's DNS servers (which are now commented out) and with just guessing them. However, they seem to be working because I can resolve a name to an IP from the windows box, just nothing responds when I try to reach the IP.
[/QUOTE]
bind9 and the more basic dnsmasq are tools which set up a local DNS server on the machine it is running on, which as I'm sure you already know provides IP addresses based on domain names. If you are running dnsmasq the DNS server will be your Ubuntu box, ie 192.168.0.1. If you're not sure what you're doing with it, you're probably better off just using your ISPs DNS server. The performance gain is generally minimal using a local server anyway. You can uninstall it with sudo apt-get remove dnsmasq --purge (assuming you installed it with apt-get).
Since you're able to perform DNS lookups it seems DNS is working fine anyway and you just need to set up forwarding on your Ubuntu box.

[QUOTE=mikerobinson]
4) I chose the device to use when installing. I don't have /etc/default/dhcpd3 but I do have /etc/default/dhcp3-server (which contains the device I use for the dhcp server, eth1)[/QUOTE]
OK that's fine, just covering my bases.

[QUOTE=mikerobinson]
I followed the instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=91370") to set up iptables and install dnsmasq. Maybe I have changed other settings in the meantime and I need to do it again. I seem to remember installing Firestarter before on an old Redhat box and I couldn't connect at all after that and I couldn't even figure out how to revert the changes. Wouldn't the command [FONT="Courier New"]iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE[/FONT] set up IP forwarding for me? (eth0 is the device that connects to the internet and eth1 is the one that connects to the windows box)

Thanks again[/QUOTE]
Yeah that iptables command will probably do it, but I don't know a lot about it so prefer to use Firestarter. Once it's installed you just need to set the internet and locally connected net interfaces and you should be away.

I use Ubuntu at home as a server - I have my net connection on eth0, Firestarter to handle firewall and NAT duties to eth1 (local), and then eth1 with dhcp3-server running plugged into my wireless router.

To sum up, I suggest:

1. Internet connection to Ubuntu on eth0.

2. Local LAN connected to eth1.

3. dhcp3-server running on eth1 as you have above, using your ISPs DNS server.

4. Firestarter running on your Ubuntu box, specifying eth0 as the internet-connected interface, eth1 as the local interface, Connection Sharing enabled, and DHCP (which should be greyed out) blank. (We want to use dhcp3-server not Firestarter's internal one). Firestarter will take care of iptables and you should be on without further ado.

BTW you may want to set the DNS servers on your XP box to your ISPs independently of DHCP.

Once you get more confident you can add dnsmasq and run a local DNS server if you want, but its more complexity most people don't really need.

Let me know how you get on.

---

### Post by mikerobinson on 2006-01-03
[QUOTE=tokyovigilante]Let me know how you get on.[/QUOTE]
Ok, I followed your suggestions and got it working. Thanks so much for all your help! I was also having some problems using my ubuntu box's DNS servers (extremely slow and some of them didn't resolve) so I am using my isp's now and it works great.

Thanks again

---

