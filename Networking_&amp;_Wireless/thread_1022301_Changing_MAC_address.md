---
title: "Changing MAC address"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by Gizmo688 on 2008-12-26
Im trying to change my mac address, but apparently im doing something wrong.

my ethernet thing is "eth1"

```

sudo iwconfig

eth1      IEEE 802.11g  ESSID:"my network"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:MY:MA:C0:00:00   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:###
          Power Management:off
          Link Quality=78/100  Signal level=-56 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

sudo ifconfig

eth1      Link encap:Ethernet  HWaddr 00:1f:3c:54:ed:07  
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: ######## Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4285866 (4.0 MB)  TX bytes:686781 (670.6 KB)

```

i then run:
```
sudo ifconfig eth1 down
sudo ifconfig eth1 hw ether 00:1E:C2:22:21:FC
sudo ifconfig eth1 up

```

sudo ifconfig now displays 00:1E:C2:22:21:FC as my mac address, but it is still 00:1f:3c:54:ed:07 up in my connection information.

After all this, i cant make a connection to the network. If i restart, my mac is set back to 00:1f:3c:54:ed:07.

How can i change my MAC for good, and get the connection to work?

edit:lspci yields
```

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

```

---

### Post by gettinoriginal on 2008-12-26
If your ISP wants you to call them everytime when you change your hardware (as my ISP does):

$ sudo gedit /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp
hwaddress ether XX:XX:XX:XX:XX:XX (insert here your old MAC)
name Ethernet LAN card

auto eth0

---

### Post by Gizmo688 on 2008-12-26
```

sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

```


so am i supposed to include ```

iface eth0 inet dhcp
hwaddress ether XX:XX:XX:XX:XX:XX (insert here your old MAC)
name Ethernet LAN card

auto eth0

``` in my interfaces file below whats already there? and i assume i use eth1 instead of eth0?

---

### Post by Gizmo688 on 2008-12-28
bump?

---

### Post by 2hot6ft2 on 2008-12-28
Have you tried macchanger? It's in the repos i.e. synaptic along with a gui for it macchanger-gtk.

utility for manipulating the MAC address of network interfaces
Features:
 .
   * set specific MAC address of a network interface
  * set the MAC randomly
  * set a MAC of another vendor
  * set another MAC of the same vendor
  * set a MAC of the same kind (eg: wireless card)
  * display a vendor MAC list (today, 6200 items) to choose from

Homepage: [http://www.alobbs.com/macchanger](http://www.alobbs.com/macchanger)

---

### Post by Gizmo688 on 2008-12-28
it still appears to be doing the same thing with macchanger

---

### Post by Cracauer on 2008-12-28
> **Gizmo688 said:**
> ```

sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

```


so am i supposed to include ```

iface eth0 inet dhcp
hwaddress ether XX:XX:XX:XX:XX:XX (insert here your old MAC)
name Ethernet LAN card

auto eth0

``` in my interfaces file below whats already there? and i assume i use eth1 instead of eth0?

I don't use the /etc/network config mechanism myself, but I'm pretty sure that the above is your existing mac address and only used to verify that the right interface is being changed. 

%%

As for your original question, make sure that there is no dhclient or similar running on the ethernet.

I used this back in the Commiecast days.  Kinda brutal but got the job done:

```

inet_if=eth0
inet_module=tulip
inet_mac=00:xx:xx:xx:xx:xx

forceethernet ()
{
        local counter=0
        while : ; do
                counter=$(($counter + 1))
                if [ $counter = 100 ] ; then
                        break
                fi
                ifconfig $inet_if hw ether $inet_mac
                sleep 1
                if ! ifconfig $inet_if | grep -q $inet_mac ; then
                        rmmod $inet_module
                        killall dhclient
                        killall -9 dhclient
                        modprobe $inet_module
                        ifconfig $inet_if hw ether $inet_mac
                        killall dhclient
                        killall -9 dhclient
                else
                        break
                fi
        done
}

```

---

