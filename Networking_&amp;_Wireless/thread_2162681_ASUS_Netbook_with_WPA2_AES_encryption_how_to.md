---
title: "ASUS Netbook with WPA2 AES encryption how to"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by aklimatize on 2013-07-15
Hi folks,

I've used these forums a ton to figure out how to do things, and today I thought I would give back a little bit.  I had to setup an Asus netbook to connect to a WPA2 secured wireless network and used wpa_supplicant and dhcpcd to do it.  The following is what worked for me, and I hope helps someone else out too.

Firstly, you'll need to make sure these are installed: wpa_supplicant, isc-dhcp-server, isc-dhcp-client, dhcpcd5:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]apt-get install wpa_supplicant isc-dhcp-server isc-dhcp-client dhcpcd5[/TD]
[/TR]
[/TABLE]

If it complains it must remove resolvconf in order to install dhcpcd5, go ahead, because it will install openresolv in its place, which is updated is seems.

Also, I've found dhcpcd5 works better than dhcpcd, so I'd suggest uninstalling dhcpcd and using dhcpcd5 instead if there are any incompatibility problems.

Once those are installed, you'll need to setup your wpa_supplicant configuration file.  The fastest way to do this is to copy the sample from /usr/share/doc/wpa_supplicant/examples and copy/paste from it into your own file.

Here is my wpa_supplicant configuration file:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="WIRELESS1"
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        psk=13d103789a5ae2220d8b53e5842d81d4ba6ebdf1aa96fb988c1929266aaa3ba1
        priority=2
}[/TD]
[/TR]
[/TABLE]

I'll break this down:

ssid = the name of your network
proto = the security protocol of your network (view the comments of wpa_supplicant.conf)
key_mgmt = how the passphrase is sent to the router

If you want to use a hex version of your WPA2 PSK, you'll use the wpa-passphrase command in a terminal:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]wpa_passphrase WIRELESS1 1234567890123456
[/TD]
[/TR]
[/TABLE]

replace WIRELESS1 with your ssid and 1234567890123456 with your passkey

This will output something akin to the following:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]network={
    ssid="WIRELESS1"
    #psk="1234567890123456"
    psk=bb1259e166fa7c06c4d3a9a8a875c52ff34bcb50e6293b8a9e9339eae856bf8e
}[/TD]
[/TR]
[/TABLE]
 
Then just copy/paste the psk field to your wpa_supplicant.conf file

Now save your wpa_supplicant.conf file - it is complete.

Next we have to setup your dhcpcd.conf file.  What I did, as a workaround, because the netbook would not communicate with the dhcp server on the router (Cisco Linksys E1200), was to specificy a static ip address via dhcpcd, so that I did not have to disable dhcp on the router and setup all other computers as static as well and turn off the dhcp server on the router.  So, I will show how I did that below.  if you'd rather have a static setup, change the following to suit your needs.

First, I'd copy the current dhcpcd.conf file so that you have a backup:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]cp /etc/dhcpcd.conf /etc/dhcpcd.conf.orig
cp /etc/dhcpcd.conf.orig /etc/dhcpcd.conf[/TD]
[/TR]
[/TABLE]

Now, edit the dhcpcd.conf file to your needs (my setup is below):

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]option interface_mtu
require dhcp_server_identifier
hostname hostname1
ssid WIRELESS1
     interface wlan0 #change to your wireless interface
     noipv4ll
     static ip_address=192.168.1.18
     static routers=192.168.1.1
     static domain_name_servers=192.168.1.1[/TD]
[/TR]
[/TABLE]

interface wlan0 - change this to your wireless interface, which you can find with the command iwconfig

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]iwconfig[/TD]
[/TR]
[/TABLE]

Your interface could be wlan0, eth1, eth2, etc.

static_ip_address means the ip address you want your machine to be connected to on your router (it is important you pick one that is not already being used, and which is within the range specified on your router)

static routers the ip address of your router

static domain_name_servers address of your DNS

If you don't know the ip address of the router or DNS, find a computer that will connect to your router, and run the following command:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]nm-tool[/TD]
[/TR]
[/TABLE]

nm-tool requires network-manager to be installed; if it's not, install it:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]apt-get install network-manager[/TD]
[/TR]
[/TABLE]

copy/paste from the output of nm-tool to fill in the information in the dhcpcd.conf file

Now,  your dhcpcd.conf file is complete.

Now all you have to do is some simple command line commands and arguments, all the hard work is done

First, stop network-manager as it seems to cause a lot of problems (in my experience)

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]service network-manager stop[/TD]
[/TR]
[/TABLE]


Then, envoke wpa_supplicant, in order to authenticate with your router via the WPA2 PSK protocol

The syntax of the wpa_supplicant command is

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]wpa_supplicant -i[interface name (no spaces)] -c[configuration file (no spaces)] -D[driver to use (no spaces)[/TD]
[/TR]
[/TABLE]

Here is my wpa_supplicant command to give you an example:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]wpa_supplicant -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dnl80211[/TD]
[/TR]
[/TABLE]

You can use other drivers besides nl80211, just type wpa_supplicant in a terminal and it will list the drivers above the command-line switches available

The output of wpa_supplicant should be something like the following:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]Trying to authenticate with 48:f8:b3:1b:d2:ca (SSID='WIRELESS1' freq=2412 MHz)
Trying to associate with 48:f8:b3:1b:d2:ca (SSID='WIRELESS1' freq=2412 MHz)
Associated with 48:f8:b3:1b:d2:ca
WPA: Key negotiation completed with 48:f8:b3:1b:d2:ca [PTK=CCMP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 48:f8:b3:1b:d2:ca completed (auth) [id=0 id_str=][/TD]
[/TR]
[/TABLE]

You can background this process the next time, once you know it is working correctly, by adding a -B switch to the command line:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]wpa_supplicant -B -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dnl80211[/TD]
[/TR]
[/TABLE]

Once that is done, envoke dhcpcd to grab an ip address on the router:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]dhcpcd wlan0[/TD]
[/TR]
[/TABLE]

Again, replace wlan0 with your wireless interface (wlan0, eth1, eth2, etc)

The output should look something like this:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]dhcpcd[16291]: version 5.2.12 starting
dhcpcd[16291]: wlan0: using static address 192.168.1.18
dhcpcd[16291]: forked to background, child pid 16379[/TD]
[/TR]
[/TABLE]

If that works, congratulations, you have an internet connection.  Do a quick ping to google to verify:

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]ping [www.google.com]("http://www.google.com")[/TD]
[/TR]
[/TABLE]

If you get replies, you're up and running

Hopefully this helps out someone with a particular situation of trying to connect a netbook (which has a network card that seems to work buggy with linux already) to a WPA2 PSK encrypted wireless network.

On a seperate note, if you're trying to get wireless working on a netbook under ubuntu, you need to install the wl package (just google wl with your version of netbook) - you can find out all your information by doing a lspci command or lshw in a terminal

Good luck!

Comments are most welcome, if there is a simpler way to do anything, please post it, I have only been working with linux for about a year, so I have much to learn yet.

---

### Post by ajgreeny on 2013-07-15
You have a typo in your third code-box.

Should read **wpa[COLOR=#ff0000]_[/COLOR]passphrase SSID password** (underscore, not dash).

I can't test the rest as I do not use or have wireless on this machine.

---

### Post by aklimatize on 2013-07-16
Thanks, fixed

---

