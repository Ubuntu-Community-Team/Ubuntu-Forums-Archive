---
title: "Dell inspiron 1525 wireless problem"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by mahanare on 2009-06-23
Hi, 

I am facing this problem after some update (I guess so).

My wireless is not working. I see the wireless indicator not at all glowing after ubuntu comes up. 

I tried removing network-manager and installing wicd  or something, here is the iwconfig result.


harinath@harinath-laptop:~$ iwconfig eth1
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


Please suggest me some fix. Its difficult to get a wired connecton all the time.

---

### Post by Metaljaz on 2009-06-23
What version of Ubuntu are you using? Did your wireless work before this update. Try going into System>Administration>Hardware Drivers and assuming you have the broadcom, making sure you have the drivers enabled.

---

### Post by mahanare on 2009-06-23
Ubuntu version 9.04
yes it was working without any problem before.

hardware driver is enabled (Broadcom STA wireless driver). (as i see it from system->admin->hardware drivers).


When I right click on  the network manager control, "Enable wireless" option is disabled. 

Wireless indicator blinks for few seconds before ubuntu is loading, but goes off. Driver looks to be 
present.

When I manually tried to restart the network, using "sudo /etc/init.d/networking restart"

[B]SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
[/B]

Well, on a side note, my 15 month old son was having fun playing with keyboard,   it might be that he pressed some key combination which disabled the wireless, but as i understand it is "fn +F2". I tried pressing this combination and restarting network and system. But with no luck.

btw, here is my present /etc/network/interfaces content. please suggest me if there is anything can be done here. 

[B]auto lo
iface lo inet loopback

auto wlan0 
iface wlan0 inet dhcp
iface eth0 inet dhcp
iface pan0 inet dhcp
auto eth0

#wireless-essid harivillu 
#wireless-key i am on wirel 
[/B]

---

### Post by mahanare on 2009-06-23
I changed my interfaces file "wlan0" to "eth1"

now when i restart network, response is different.

[B]Listening on LPF/eth1/00:23:4d:20:46:51
Sending on   LPF/eth1/00:23:4d:20:46:51
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]

But then i am still having problem

---

### Post by enli on 2009-06-23
I had the same problem after fresh installation of 9.04 on Inspiron 1525. Revert back to original settings and then try

sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl

It worked right away after this.

---

### Post by mahanare on 2009-06-24
Tried these commands but no luck. 

btw it was working fine with 9.04 itself. but could be because of some regular updates, something got changed.

help please.

---

### Post by alks_dp on 2009-06-24
Stay away from DELL at all costs. Boycott DELL.

---

### Post by drrdf2 on 2009-06-24
I had the same problem with Ubuntu 8.10 and the current release, using a wireless card.  After wasting an inordinate amount of time I put together a clear detailed procedure which should work with most if not all wireless cards. I have posted it on this forum under **Ubuntu 8.10 stated menu options missing. **Strangely I have now discovered that some of these menu options only appear after you have installed ndisgtk! Weird that.

---

### Post by Ayuthia on 2009-06-24
Can you post the results of:
```
lshw -C network
lsmod|grep -e b43 -e ssb -e wl -e ndis
ls /lib/modules/`uname -r`/volatile
```
This will help us see what your system has loaded, the driver your wireless card is trying to use, and verify that the Broadcom STA module is there.  There was a recent update that has caused the wireless module to disappear, but there are some commands that can bring it back.

---

### Post by mahanare on 2009-07-06
Sorry guys, It was plain mistake of me. By mistake I have switched off the wireless switch that is available on the right side of my lapotp (just below the PCI slot).

Actually I re=installed ubuntu and then found the same problem(wirless disabled). But when I turned on the wireless switch, wireless worked fine.

Thanks for the support of the forum. Inspiron 1525 and Ubuntu combination, there is no problem.

---

### Post by superprash2003 on 2009-07-07
have you tried system->admin->hardware drivers?

---

