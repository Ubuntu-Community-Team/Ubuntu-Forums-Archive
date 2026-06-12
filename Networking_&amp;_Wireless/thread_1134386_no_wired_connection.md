---
title: "no wired connection"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by pow155 on 2009-04-23
Hi, I need some help with wired connection. I could connect to wireless, but i think i mess up somewhere in the terminal when i try to open port,so now my wired connection doesn't work. on NetworkManager Applet 0.7.0. under wired network, it show "device is unmanaged". 
Here's some info on ifconfig:

> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:01:bf:c6  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe01:bfc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1874654 (1.8 MB)  TX bytes:386372 (386.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-01-BF-C6-66-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

notice there is no eth0 on ifconfig.

I think somehow I delete my eth0 when i mess around in the terminal trying to open port. Any one know how to get eth0 back on? Thanks

edit: when I try to restart network with sudo /etc/init.d/networking restart, this is what it show:
>  * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
Don't seem to be have all the variables for eth0/inet.
Failed to bring up eth0.

here's something from interfaces:
> auto lo
iface lo inet loopback

# <static ip>
auto eth0
iface eth0 inet static
	addresss 192.168.1.3
	netmask 255.255.255.0
	broadcast 192.168.1.255

---

### Post by chili555 on 2009-04-23
I suggest amending *interfaces* to read like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
addresss 192.168.1.3
netmask 255.255.255.0
[COLOR="Red"]gateway 192.168.1.1[/COLOR]
```I would also make sure that */etc/resolv.conf* looks like:```
nameserver 192.168.1.1
```Then restart networking and do:```
ping -c3 www.google.com
```Are you connected?

---

### Post by pow155 on 2009-04-23
I'm a total linux noob, can you show me what to type in order to change interfaces? Thanks

---

### Post by pow155 on 2009-04-23
i manage to do all that, but it still show device is unmanaged under wired network.
Here's what interface is showing:
> tom@ubuntu:/etc/network$ cat interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	addresss 192.168.1.3
	netmask 255.255.255.0
	gateway 192.168.1.1


edit:
> aftering restarting network and pinging. I disconnect my wireless in order to check if wired connection work:
tom@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Don't seem to be have all the variables for eth0/inet.
Failed to bring up eth0.
                                                                         [ OK ]
tom@ubuntu:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)


---

### Post by chili555 on 2009-04-23
> it still show device is unmanaged under wired network.As long as there are entries in */etc/network/interfaces* for either wlan0 or eth0, or both, Network Manager will not be able to manage those interfaces. Is this a desktop machine that never leaves the house or office? If so, you probably would do just as well, maybe better, without Network Manager. If it is a laptop that travels to the cyber cafe, university or library and you need to select from several available networks, then I would stay with Network Manager.> Don't seem to be have all the variables for eth0/inet.Ah, ha!!! I see it! Please change address[COLOR="Red"]s[/COLOR] to address. Restart networking. Connect. Rejoice.

---

### Post by jaithehulk on 2009-05-02
whenever i boot up my PC... my network manager always shows
***Wired Network Device not managed***
I hav a different problem.....my eth0 works when i start it from the terminal using 
*sudo ifconfig eth0 up*
but it always shows *device not managed* in network manager applet.
How to fix this applet status?? when in background eth0 is working properly!!!!

---

### Post by H.K.Murmu on 2009-05-02
I have the same problem and always use pppoeconf to connect internet. But now I am able to connect through network manager applet no need to open a terminal.

To connect through[COLOR=Blue] ADSL modem[/COLOR] you have to configure your modem device by self or take it to your service provider. Once configured then follow the steps
1[COLOR=Red]:-system[/COLOR]----[COLOR=Blue]adminstration[/COLOR]------[COLOR=Purple]user and groups[/COLOR]
2:-In user setting select [COLOR=Purple]use[/COLOR]r-----[COLOR=Purple]propertie[/COLOR]s---check the box "[COLOR=Blue]connect to internet using modem[/COLOR]" and "[COLOR=Blue]connect to wireless and ethernet networks[/COLOR]" then close
3:- open [COLOR=Blue]network manager apple[/COLOR]t from panel under DSL --[COLOR=Blue]-ADD[/COLOR]---Edit DSL connection-----in tab[COLOR=Blue] DSL[/COLOR] provide internet [COLOR=Navy]userid and password[/COLOR] and under tab[COLOR=Red] IPv4 setting[/COLOR] select "[COLOR=Red]automatic pppoe[/COLOR]" and then close(perhaps require restart system not sure)
4:-In pannel left click and click the radio button 
5-now you are connected to internet through [COLOR=Red]Network manager Applet[/COLOR]

---

