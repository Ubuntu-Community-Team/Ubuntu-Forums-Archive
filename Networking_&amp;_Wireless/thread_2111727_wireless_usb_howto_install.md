---
title: "wireless usb: howto install?"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by icegood on 2013-02-02
Have
WIRELESS 300N USB ADAPTER MODEL 525206

In system present as:
```

wlan1     Link encap:Ethernet  HWaddr 80:1f:02:64:e5:a0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Tried to connect via wpa_supplicant:

```
wpa_supplicant -B -dd -f/var/log/wifi_log -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -N -iwlan1 -c/etc/wpa_supplicant.conf -Dwext

```

where in my /etc/wpa_supplicant.conf - configuration for my router. 
After that did
```

dhclient -v wlan0 wlan1 2>>$log_file

```

However it doesn't work.  internal wlan0 is OK, but wlan1 fails.
Full configuration start-file is /etc/init.d/wireless_connect.sh:
```

#!/bin/bash
#!/bin/bash
### BEGIN INIT INFO
# Provides:          
# Required-Start:    
# Required-Stop:     
# Should-Start:      
# Should-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: wifi
# Description: Wireless network in home
### END INIT INFO

log_file=/var/log/wifi_log
> $log_file
NAME=wireless_connect

. /lib/lsb/init-functions

function wpa_suppl_running()
{
  ps aux | grep wpa_supplicant | grep -v grep | awk '{print($2)}'
}

function dhclient_running()
{
  ps aux | grep dhclient | grep -v grep | awk '{print($2)}'
}

case "$1" in
        start)
                log_daemon_msg "Starting the daemon " "$NAME"
                v_pid=$(wpa_suppl_running)
                if [ -z $v_pid ]; then
                  wpa_supplicant -B -dd -f$log_file -iwlan0 -c/etc/wpa_supplicant.conf -Dwext -N -iwlan1 -c/etc/wpa_supplicant.conf -Dwext
                  sleep 2
                fi;
                dhclient -v wlan0 wlan1 2>>$log_file
                ;;
        stop)
                log_daemon_msg "Stopping the daemon " "$NAME"
                v_pid=$(dhclient_running)
                if [ -n "$v_pid" ]; then
                  dhclient -r -v wlan0 wlan1 2>>$log_file
                fi;
                v_pid=$(wpa_suppl_running)
                killall wpa_supplicant 
                ;;
        restart|force-reload)
                $0 stop && sleep 2 && $0 start
                ;;
        status)
                echo $0
                ;;
        *)
                echo "Usage: /etc/init.d/winbind {start|stop|restart|force-reload|status}"
                exit 1
                ;;
esac
exit 0


```

log /var/log/wifi_log is in attach (too big for there for even one connection)

What to do? In windows 7 works everything.

---

### Post by icegood on 2013-02-02
found wonderful workaround:
[there]("http://www.youtube.com/watch?v=gk8g1vr2kpA")
but cannot get where kde menus of ndiswrapper are located.

---

### Post by icegood on 2013-02-03
no, it wasn't workaround. ndiswrapper doesn't help me

---

### Post by ahallubuntu on 2013-02-03
If you have this one:

[http://www.intellinet-network.com/en-US/products/9568-wireless-300n-high-gain-usb-adapter](http://www.intellinet-network.com/en-US/products/9568-wireless-300n-high-gain-usb-adapter)

then you seem to have one of the Realtek 8192 chipsets.  Try typing

```
sudo lshw -C network
```

and

```
lsusb
```

to see exactly which one.  Realtek has Linux drivers for many of their chipsets on their website; building/installing one of those would be preferable to using ndiswrapper, which tries to use a Windows driver in Linux and is often problematic.

---

### Post by Bucky Ball on 2013-02-03
Avoid ndiswrapper. You might try a basic fix and update with a cable while the USB dongle is plugged in. Then check Additional Drivers unless it starts working. You may need to restart if you enable any new driver.

If it's an 8192 that should work out of the box or you can download the correct driver from the Realtek site, install, plug in dongle and restart if it doesn't start working automagically.

---

### Post by icegood on 2013-02-03
> **Bucky Ball said:**
> Avoid ndiswrapper. You might try a basic fix and update with a cable while the USB dongle is plugged in. Then check Additional Drivers unless it starts working. You may need to restart if you enable any new driver.

What you mean by "might try a basic fix and update with a cable"?

> **Bucky Ball said:**
> 
If it's an 8192 that should work out of the box or you can download the correct driver from the Realtek site, install, plug in dongle and restart if it doesn't start working automagically.
I had by default linux rtl8192cu driver. And saw my adapter as wlan1 via "ifconfig -a". With ndiswrapper i don't see even that. So i rolled back to linux rtl8192cu. And now wonder what it might happen with DHCP, why DHCPDISCOVER doesn't return DHCPOFFER.

---

### Post by arnarg on 2013-02-07
Any luck? I'm thinking about buying it.

---

### Post by chili555 on 2013-02-07
Is Network Manager installed and running? It is very doubtful that manual methods will work if so.

---

### Post by icegood on 2013-02-10
i've removed network manager for a long time ago. For now no luck. But one guy from my work was lucky to run  it under debian. For this moment i don't know where reason is.

---

### Post by kurt18947 on 2013-02-10
> **arnarg said:**
> Any luck? I'm thinking about buying it.

IMO there are better choices.  Devices that use RealTek's 8192SU chipset are generally plug 'n' play.  2 that I know to work are Dlink's DWA-131 and TrendNet's TEW-649UB, they're twins. The only thing that *may* mess with their functioning would be a different adapter version # using a different chip set.  These are N150 adapters.  I don't have any suggestions for N300/dual band adapters.

---

### Post by chili555 on 2013-02-10
> **icegood said:**
> i've removed network manager for a long time ago. For now no luck. But one guy from my work was lucky to run  it under debian. For this moment i don't know where reason is.May we see:```
cat /etc/network/interfaces
```Please obscure any passwords, etc.

---

### Post by arnarg on 2013-02-11
> **kurt18947 said:**
> IMO there are better choices.  Devices that use RealTek's 8192SU chipset are generally plug 'n' play.  2 that I know to work are Dlink's DWA-131 and TrendNet's TEW-649UB, they're twins. The only thing that *may* mess with their functioning would be a different adapter version # using a different chip set.  These are N150 adapters.  I don't have any suggestions for N300/dual band adapters.

Thanks for the suggestion. How are the range on these adapters without antennas? Do you know of any with antennas and maybe PCI or PCI-Express as this is for a desktop computer?

Edit: [This one]("http://www.ebay.com/itm/802-11bgn-Wireless-1W-High-Power-USB-Adapter-2x5dBi-Antenna-25dBm-2T2R-300Mbps-/400408612968?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item5d3a369068") looks pretty nice and it has the RTL8192SU chipset, what do you think?

---

### Post by kurt18947 on 2013-02-11
> **arnarg said:**
> Thanks for the suggestion. How are the range on these adapters without antennas? Do you know of any with antennas and maybe PCI or PCI-Express as this is for a desktop computer?

Edit: [This one]("http://www.ebay.com/itm/802-11bgn-Wireless-1W-High-Power-USB-Adapter-2x5dBi-Antenna-25dBm-2T2R-300Mbps-/400408612968?pt=US_USB_Wi_Fi_Adapters_Dongles&hash=item5d3a369068") looks pretty nice and it has the RTL8192SU chipset, what do you think?

If it really is an RTL8192SU, it should work.  My concern is that my devices mentioned above are rated at 150 Mb./sec, not 300.  What's different?  As far as range, that's a function of wireless router/access point,  materials between the wireless access point and device ('conventional framing', drywall and 2X are not a problem, brick, stone and plaster with metal lath are), interference etc. etc.  N speed devices are supposed to be quite a bit better than G speed devices.  I live in a townhome and no issues at all, even with transmit power turned down so as to be neighbor friendly.

---

### Post by ahallubuntu on 2013-02-11
All of my issues with my RTL8192CU-based cards went away after building the latest driver from Realtek; without doing that, the card was almost unusable in 12.04 with the built-in driver.

Yes, my cheap USB wireless dongles are only 150Mbps.  For what I use them for, this is not a big concern.

---

### Post by arnarg on 2013-02-11
> **ahallubuntu said:**
> All of my issues with my RTL8192CU-based cards went away after building the latest driver from Realtek; without doing that, the card was almost unusable in 12.04 with the built-in driver.

Yes, my cheap USB wireless dongles are only 150Mbps.  For what I use them for, this is not a big concern.

I found one place locally that sells TEW-649UB and I'm planning on buying it, if I need faster one at least I can use it with my Raspberry Pi :P

Thanks.

---

### Post by icegood on 2013-02-26
> **chili555 said:**
> May we see:```
cat /etc/network/interfaces
```Please obscure any passwords, etc.

Yeah, sure
```

auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
#provider dsl-provider

#auto eth0
#iface eth0 inet manual
#
#auto wlan0
#iface wlan0 inet static
#address 192.168.73.177
#netmask 255.255.255.0
#
#auto wlan1
#iface wlan1 inet static
#address 192.168.73.149
#netmask 255.255.255.0


```

---

### Post by chili555 on 2013-02-27
Since you have removed Network manager, you must populate /etc/network/interfaces unless you wish to start the wireless with a series of complicated terminal commands every time you boot. I suggest:```
auto lo
iface lo inet loopback

auto wlan1
iface wlan1 inet static
address 192.168.73.149
netmask 255.255.255.0
gateway 192.168.73.1
dns-nameservrs 192.168.73.1 8.8.8.8
wpa-essid your_router
wpa-psk yoursecretkey
```Then get the system to re-read the details:```
sudo ifdown wlan1 && sudo ifup wlan1
```Did you connect?```
ping -c3 www.google.com
```

All of this assumes your wireless is working properly. Does it scan and see networks?```
sudo iwlist wlan1 scan
```

---

