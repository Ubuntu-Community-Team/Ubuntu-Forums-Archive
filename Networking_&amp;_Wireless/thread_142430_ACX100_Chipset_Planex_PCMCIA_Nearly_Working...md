---
title: "ACX100 Chipset Planex PCMCIA Nearly Working.."
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by fieldyweb on 2006-03-10
Hi.. 

I have a Planex GW-NS54GM PCMCIA Wifi card, (104c:9066)which i have sucessfully used under Fedora C3 and C4, by following the instructions outlined at [www.houseofcraig.net/acx100_howto.php]("www.houseofcraig.net/acx100_howto.php")

I'm running Ubunti 5.10 with Kernel 2.6.12-10-386

Having installed the necessary extras (GCC etc) i was able to install the Wifi card drivers as outlined in this top HOWTO guide.. and indeed if i invoke the ./start_net script My wifi card detects the Dlink AP with 64Bit encryption and all is good.. 

However i would prefer all this to happen without the use of this script.  Basically i can use it once under FC4 and then use NEAT to configure the NIC from there on in..

However if i do this on Unbuntu (run the script once, then try and use the panels Network Monitor) the card is recognised, it just doesn't seem to be able to attach to the ACCess point.. I have opted for NO DHCP and am using static addressing (i't only me on the network) and the AP has been setup to accept this configuration (as i said all is good if i use the ./start_net script)

So i installed network-manager (nm-applet) and wifi-radar and both can see my Access point (and 2 others in the condo block..)

So my question is, with a set of working drivers 

> find /lib/modules/`uname -r` -name "*acx*"

lists the drivers i have installed as being in

> /lib/modules/2.6.12-10-386/net/acx_pci.ko
/lib/modules/2.6.12-10-386/net/acx_usb.ko

I moved the origional supplied drivers using
> 
find /lib/modules/`uname -r` -name "*acx*" -exec mv {} /root \;

and 

> david@david:~$ ls -ltr /root
total 8
-rw-r--r--  1 root root  167 2006-03-07 10:48 dbootstrap_settings
drwxr-xr-x  2 root root 4096 2006-03-07 17:27 acx

so does anyone have any ideas how i could get this all working using GUI stuff? rather than having to invoke the start_net script each boot? As i move between wifi and wired quite a bit..

---

### Post by fieldyweb on 2006-03-11
In true linux fashion, and for the 3rd no reply time, i have fixed my own problem, but this time it was a bit of a bugger...

the fact that i am able to write this entry is being done over WiFi with no ./start_net as supplied with the ACX Sourceforge driver...

And in an effort to save another single person from this WiFi hell.. Here is what i did.. 

my ***[COLOR="Blue"]/etc/network/interfaces[/COLOR]*** is as follows..

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
	map wlan0

# The primary network interface
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1



#WiFi Interface
iface wlan0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid davewifi
wireless_mode managed
wireless_rate auto 
wireless-key xxxxxxxxxx


#wireless_nick david 






 auto wlan0
auto eth0


I honestly don't know if this is the best way to write this, and if its not, and someone can post up here a better way then cool..

I already had network manager installed and nm-applet running, however if you want to know how to install it, read below

> 
[COLOR="Blue"]sudo gedit /etc/apt/sources.list[/COLOR]

There are lines pre-defined. You only have to uncomment them like this.

[COLOR="DarkGreen"]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe
deb-src [ftp://archive.ubuntu.com/ubuntu](ftp://archive.ubuntu.com/ubuntu) warty main restricted universe[/COLOR]


You have to update your apt-sources with the following command:

[COLOR="Blue"] sudo apt-get update[/COLOR]


Then you can install Network Manager with a simple apt-get command. There are some other packages needed and apt-get will install them for you.

[COLOR="Blue"]sudo apt-get install network-manager[/COLOR]




I had installed it however apparently i needed to update the following

> 
First we are going to edit the /etc/dbus-1/system.d/NetworkManager.conf file.

[COLOR="Blue"] sudo gedit /etc/dbus-1/system.d/NetworkManager.conf[/COLOR]


Here we have to change the deny's to allow's. Like this:

[COLOR="DarkGreen"]<policy context="default">
    <allow own="org.freedesktop.NetworkManager"/>
    <allow send_destination="org.freedesktop.NetworkManager"/>
    <allow send_interface="org.freedesktop.NetworkManager"/>
</policy>[/COLOR]


The same we do with the /etc/dbus-1/system.d/nm-applet.conf file.

 [COLOR="Blue"]sudo gedit /etc/dbus-1/system.d/nm-applet.conf[/COLOR]


Here we also have to change the deny's to allow's. Like this:
[COLOR="DarkGreen"]
<policy context="default">
   <allow own="org.freedesktop.NetworkManagerInfo"/>
   <allow send_destination="org.freedesktop.NetworkManagerInfo"/>
   <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
</policy>[/COLOR]


Becouse Network Manager is working with bind9 for it DNS queries, it can be helpfull te edit your bind9 configuration and add the NDS servers from you IPS to them. The file we want to edit is: /etc/bind/named.conf.options.

[COLOR="Blue"]sudo gedit /etc/bind/named.conf.option[/COLOR]s


Over here you can add the nameservers of the ISP that you want to use. You can add the IP addresses of the nameservers to the forwarders section. The file will look like this when you edited it:

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you might need to uncomment the query-source
        // directive below.  Previous versions of BIND always asked
        // questions using port 53, but BIND 8.1 and later use an unprivileged
        // port by default.

        // query-source address * port 53;

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

[COLOR="DarkGreen"]        forwarders {
                111.222.333.123;
                111.222.333.124;
                111.222.333.125;
        };[/COLOR]

        // forwarders {
        //      0.0.0.0;
        // };

        auth-nxdomain no;    # conform to RFC1035

};





Now i have to admit, the last part of updating bind seemed to achive nada for me, (see later) And rebooting the Pc seemed to just end up with the same [COLOR="DarkGreen"]/etc/resolv.conf[/COLOR] which had a [COLOR="Red"]do not edit using local nameserver[/COLOR] message in it..

Anyway, with the above network config and the nm-applet running, i seem to be working ok.. there are however some issues i have noted, and don't know how to resolve...

> **_[COLOR="Indigo"]OUTSTANDING ISSUES[/COLOR]_**
[LIST]
[*]When i use the gnome-panel [COLOR="DarkOrange"]System -> Logout[/COLOR] to reboot the PC, when the PC reboots it will [COLOR="Red"]NOT[/COLOR] find a wireless network... even though it was working fine before the reboot.. and [COLOR="DarkOrange"]Save Settings[/COLOR] is [COLOR="Red"]**not highlighted**[/COLOR].
[*]If i type [COLOR="Blue"]sudo reboot[/COLOR] from the command console, the PC reboots and all works fine after the reboot.
[*]As i mentioned above the [COLOR="Green"]/etc/resolv.conf[/COLOR] seems to get overwrited despite making any changes unless i update the [COLOR="Green"]resolv.conf [/COLOR]and put the routers DNS server in automatically i can obviously surf the lan but not the internet
[/LIST]

---

