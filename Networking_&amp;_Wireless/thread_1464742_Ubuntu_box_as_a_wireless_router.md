---
title: "Ubuntu box as a wireless router"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by gnat man on 2010-04-28
I have followed the information in the guides here:
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

The DHCP stuff from here:
[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

And the IP table stuff from here:
[http://georgia.ubuntuforums.org/showthread.php?p=3937715](http://georgia.ubuntuforums.org/showthread.php?p=3937715)

And I have a system right now where on the wired connections, it is working like a proper router, however, I can't seem to get any devices to connect to the wireless network I set up.

I am able to see the wireless network I create, and using iwconfig confirms that the madwifi drivers are loaded properly, and that the card is in master mode, so it should all just work, but it's not.

When I try to connect with another ubuntu box, it asks for a WPA password, but I am initially trying set it up without any security just to see if I can get it working.  When I try to connect with the iPhone, it looks like it's going to connect but I never get the little check mark.

I tried doing a WEP password, and ubuntu still asks for WPA, and the iPhone asks for a username and password, as if it were WPA.

Any ideas?

---

### Post by randumnumber on 2010-04-28
Did you run into any issues when setting up for wireless? I have never used madwifi but I have set up an AP with airbase-ng i would try the man pages for madwifi. If its asking for WPA then there must be a reason that madwifi thinks it is in WPA mode. In airbase-ng you are required to be in monitor mode, so i'm not sure what master mode is. I found this [http://madwifi-project.org/wiki/UserDocs/SimpleAccessPoint](http://madwifi-project.org/wiki/UserDocs/SimpleAccessPoint) maybe it will help?

Also, In setting up my AP i was almost driven crazy by figuring out what ATH0 is, you probably already know but i will say anyway just in case:
madwifi creates ath0 as a virtual device inside your machine, this is what you should be pointing your DHCP and ip tables to. It might be that you are actually getting a connection but the device is not getting an IP address from your DHCP service though your wireless card. Also if you would give a readout of your IP tables and DHCP config that would probably help people on this forum to help you solve your issue. One more thing, make sure that your Wireless card is compatible with madwifi. here [http://madwifi-project.org/wiki/Compatibility](http://madwifi-project.org/wiki/Compatibility)

---

### Post by gnat man on 2010-04-28
I tried the guide you posted, and I'm still having the same problem.

I will put my conf files here, and maybe someone can spot a stupid mistake I made or something.

/etc/network/interfaces
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
#iface eth1 inet dhcp
auto eth2
#iface eth2 inet dhcp
iface bnep0 inet dhcp
# Set up the internal wireless network
auto ath0
iface ath0 inet manual
    wireless-mode master
    wireless-essid Jimmynet2
    wireless-channel 1
    wireless-key 70dfbc5331432fbeb22c7f28c2

#iface ath0 inet manual
    # ensure ath0 is down (never fails because of "true")
#    pre-up wlanconfig ath0 destroy || true
    # set up the ath0 device in AP mode before bringing up the interface (unless you're using AutoCreate)
#    pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
    # remove the ath0 device when bringing the interface down
#    post-down wlanconfig ath0 destroy
    # set master mode, channel, and the essid
#    wireless-mode master
#    wireless-channel 11
#    wireless-essid Jimmynet2
    # IF you use WEP, put the key here:
    #wireless-key 1234-1234-1234-1234

# Set up the internal wired/wireless network bridge
#
# Don't forget to change wlan0 and eth1 to the proper name of
# the internal wired and wireless interfaces if applicable.
#
auto br0
iface br0 inet static
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    bridge-ports eth1 ath0 eth2

```

/etc/dhcp3/dhcpd.conf
```
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc; 

# this may be required for some network configurations,
# but seems to work fine without it on my LAN.
option domain-name "my-dhcp-server.com";

#assign the remote dhcp server hostname/ip addresses 
option domain-name-servers 4.2.2.1, 4.2.2.2;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600;

# assign the max lease time (seconds)
max-lease-time 7200;

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.150;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

```

/etc/default/dhcp3-server
```
INTERFACES="br0"
```

My IP Masquerade script
```
#!/bin/sh
#
#firewall-iptables
FWVER= 0.76
#
#               Initial SIMPLE IP Masquerade test for 2.6 / 2.4 kernels
#               using IPTABLES.
#
#               Once IP Masquerading has been tested, with this simple
#               ruleset, it is highly recommended to use a stronger
#               IPTABLES ruleset either given later in this HOWTO or
#               from another reputable resource.
#
#
#
# Log:
#       0.76 - Added comments on why the default policy is ACCEPT
#       0.75 - Added more kernel modules to the comments section 
#       0.74 - the ruleset now uses modprobe vs. insmod
#       0.73 - REJECT is not a legal policy yet; back to DROP
#       0.72 - Changed the default block behavior to REJECT not DROP
#       0.71 - Added clarification that PPPoE users need to use 
#              "ppp0" instead of "eth0" for their external interface
#       0.70 - Added commented option for IRC nat module
#            - Added additional use of environment variables
#            - Added additional formatting 
#       0.63 - Added support for the IRC IPTABLES module
#       0.62 - Fixed a typo on the MASQ enable line that used eth0
#              instead of $EXTIF
#       0.61 - Changed the firewall to use variables for the internal 
#              and external interfaces.
#       0.60 - 0.50 had a mistake where the ruleset had a rule to DROP
#              all forwarded packets but it didn't have a rule to ACCEPT
#              any packets to be forwarded either
#            - Load the ip_nat_ftp and ip_conntrack_ftp modules by default
#       0.50 - Initial draft
#

echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"


# The location of the iptables and kernel module programs 
#
#   If your Linux distribution came with a copy of iptables,
#   most likely all the programs will be located in /sbin.  If
#   you manually compiled iptables, the default location will
#   be in /usr/local/sbin 
#
# ** Please use the "whereis iptables" command to figure out
# ** where your copy is and change the path below to reflect
# ** your setup
#
IPTABLES=/sbin/iptables
#IPTABLES=/usr/local/sbin/iptables 
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe


#Setting the EXTERNAL and INTERNAL interfaces for the network
#
#  Each IP Masquerade network needs to have at least one
#  external and one internal network.  The external network 
#  is where the natting will occur and the internal network
#  should preferably be addressed with a RFC1918 private address
#  scheme.
#
#  For this example, "eth0" is external and "eth1" is internal" 
#
#
#  NOTE:  If this doesnt EXACTLY fit your configuration, you must
#         change the EXTIF or INTIF variables above. For example:
#
#            If you are a PPPoE or analog modem user:
#
#               EXTIF="ppp0" 
#
#
EXTIF="eth0"
INTIF="br0"
INTIF2="eth2"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2" 

EXTIP="74.192.39.29"
echo "   External IP:  $EXTIP"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing == 


echo -en "   loading modules: "

# Need to verify that all modules have all required dependencies
#
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a

# With the new IPTABLES code, the core MASQ functionality is now either 
# modular or compiled into the kernel.  This HOWTO shows ALL IPTABLES
# options as MODULES.  If your kernel is compiled correctly, there is
# NO need to load the kernel modules manually.
#
#  NOTE: The following items are listed ONLY for informational reasons. 
#        There is no reason to manual load these modules unless your
#        kernel is either mis-configured or you intentionally disabled
#        the kernel module autoloader.
#

# Upon the commands of starting up IP Masq on the server, the 
# following kernel modules will be automatically loaded:
#
# NOTE:  Only load the IP MASQ modules you need.  All current IP MASQ
#        modules are shown below but are commented out from loading.
# =============================================================== 

echo "----------------------------------------------------------------------"

#Load the main body of the IPTABLES module - "iptable"
#  - Loaded automatically when the "iptables" command is invoked 
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_tables, "
$MODPROBE ip_tables


#Load the IPTABLES filtering module - "iptable_filter"
#  - Loaded automatically when filter policies are activated 


#Load the stateful connection tracking framework - "ip_conntrack"
#
# The conntrack  module in itself does nothing without other specific
# conntrack modules being loaded afterwards such as the "ip_conntrack_ftp" 
# module
#
#  - This module is loaded automatically when MASQ functionality is
#    enabled
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_conntrack, " 
$MODPROBE ip_conntrack


#Load the FTP tracking mechanism for full FTP tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_conntrack_ftp, " 
$MODPROBE ip_conntrack_ftp


#Load the IRC tracking mechanism for full IRC tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -en "ip_conntrack_irc, " 
$MODPROBE ip_conntrack_irc


#Load the general IPTABLES NAT code - "iptable_nat"
#  - Loaded automatically when MASQ functionality is turned on
#
#  - Loaded manually to clean up kernel auto-loading timing issues 
#
echo -en "iptable_nat, "
$MODPROBE iptable_nat


#Loads the FTP NAT functionality into the core IPTABLES code
# Required to support non-PASV FTP.
#
# Enabled by default -- insert a "#" on the next line to deactivate 
#
echo -en "ip_nat_ftp, "
$MODPROBE ip_nat_ftp


#Loads the IRC NAT functionality into the core IPTABLES code
# Required to support NAT of IRC DCC requests
#
# Disabled by default -- remove the "#" on the next line to activate 
#
#echo -e "ip_nat_irc"
#$MODPROBE ip_nat_irc

echo "----------------------------------------------------------------------"

# Just to be complete, here is a partial list of some of the other 
# IPTABLES kernel modules and their function.  Please note that most
# of these modules (the ipt ones) are automatically loaded by the
# master kernel module for proper operation and don't need to be
# manually loaded. 
# --------------------------------------------------------------------
#
#    ip_nat_snmp_basic - this module allows for proper NATing of some
#                        SNMP traffic
#
#    iptable_mangle    - this target allows for packets to be
#                        manipulated for things like the TCPMSS
#                        option, etc.
#
# --
#
#    ipt_mark       - this target marks a given packet for future action.
#                     This automatically loads the ipt_MARK module
#
#    ipt_tcpmss     - this target allows to manipulate the TCP MSS
#                     option for braindead remote firewalls.
#                     This automatically loads the ipt_TCPMSS module
#
#    ipt_limit      - this target allows for packets to be limited to
#                     to many hits per sec/min/hr
#
#    ipt_multiport  - this match allows for targets within a range
#                     of port numbers vs. listing each port individually
#
#    ipt_state      - this match allows to catch packets with various
#                     IP and TCP flags set/unset
#
#    ipt_unclean    - this match allows to catch packets that have invalid
#                     IP/TCP flags set
#
#    iptable_filter - this module allows for packets to be DROPped,
#                     REJECTed, or LOGged.  This module automatically
#                     loads the following modules:
#
#                     ipt_LOG - this target allows for packets to be
#                               logged
#
#                     ipt_REJECT - this target DROPs the packet and returns
#                                  a configurable ICMP packet back to the
#                                  sender.
#

echo -e "   Done loading modules.\n"



#CRITICAL:  Enable IP forwarding since it is disabled by default since 
#
#           Redhat Users:  you may try changing the options in
#                          /etc/sysconfig/network from:
#
#                       FORWARD_IPV4=false
#                             to
#                       FORWARD_IPV4=true
#
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward


# Dynamic IP users:
#
#   If you get your IP address dynamically from SLIP, PPP, or DHCP, 
#   enable this following option.  This enables dynamic-address hacking
#   which makes the life with Diald and similar programs much easier.
#
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr 


# Enable simple IP forwarding and Masquerading
#
#  NOTE:  In IPTABLES speak, IP Masquerading is a form of SourceNAT or SNAT.
#
#  NOTE #2:  The following is an example for an internal LAN address in the 
#            192.168.0.x network with a 255.255.255.0 or a "24" bit subnet mask
#            connecting to the Internet on external interface "eth0".  This
#            example will MASQ internal traffic out to the Internet but not
#            allow non-initiated traffic into your internal network.
#
#
#         ** Please change the above network numbers, subnet mask, and your
#         *** Internet connection interface name to match your setup 
#


#Clearing any previous configuration
#
#  Unless specified, the defaults for INPUT and OUTPUT is ACCEPT
#    The default for FORWARD is DROP (REJECT is not a valid policy)
#
#   Isn't ACCEPT insecure?  To some degree, YES, but this is our testing 
#   phase.  Once we know that IPMASQ is working well, I recommend you run
#   the rc.firewall-*-stronger rulesets which set the defaults to DROP but
#   also include the critical additional rulesets to still let you connect to 
#   the IPMASQ server, etc.
#
echo "   Clearing any existing rules and setting default policy.."
$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD
$IPTABLES -t nat -F

echo "   FWD: Allow all connections OUT and only existing and related ones IN"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT 
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $INTIF2 -m state --state ESTABLISHED,RELATED \-j ACCEPT 
$IPTABLES -A FORWARD -i $INTIF2 -o $INTIF -m state --state ESTABLISHED,RELATED \-j ACCEPT
$IPTABLES -A FORWARD -i $INTIF2 -o $EXTIF -j ACCEPT
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

echo -e "\nrc.firewall-iptables v$FWVER done.\n"

```

And here's the output from some commands.

ifconfig
```

```

iwconfig
```
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"test"  Nickname:""
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:1E:58:3F:AF:95   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:3  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

br0       no wireless extensions.

vboxnet0  no wireless extensions.

```

/etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 1239
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:19:d1:xx:xx:xx
Sending on   LPF/eth0/00:19:d1:xx:xx:xx
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 172.24.xxx.xxx port 67
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface eth1=eth1.
RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:19:d1:xx:xx:xx
Sending on   LPF/eth0/00:19:d1:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 74.192.xxx.xxx from 10.20.xxx.xxx
DHCPREQUEST of 74.192.xxx.xxx on eth0 to 255.255.255.255 port 67
DHCPACK of 74.192.39.29 from 10.20.0.1
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 74.192.xxx.xxx -- renewal in 44471 seconds.
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.

Waiting for br0 to get ready (MAXWAIT is 32 seconds).
                                                                         [ OK ]
```

Parts I changed from /etc/hostapd/hostapd.conf
```
# SSID to be used in IEEE 802.11 management frames
ssid=test

# Country code (ISO/IEC 3166-1). Used to set regulatory domain.
# Set as needed to indicate country in which device is operating.
# This can limit available channels and transmit power.
country_code=US

# Enable IEEE 802.11d. This advertises the country_code and the set of allowed
# channels and transmit power levels based on the regulatory limits. The
# country_code setting must be configured with the correct country for
# IEEE 802.11d functions.
# (default: 0 = disabled)
#ieee80211d=1

# Operation mode (a = IEEE 802.11a, b = IEEE 802.11b, g = IEEE 802.11g,
# Default: IEEE 802.11b
hw_mode=g

# Channel number (IEEE 802.11)
# (default: 0, i.e., not set)
# Please note that some drivers (e.g., madwifi) do not use this value from
# hostapd and the channel will need to be configuration separately with
# iwconfig.
channel=11

```
WEP and WPA are not enabled there.

So yeah, I'm all out of ideas at this point.

---

### Post by gnat man on 2010-05-13
Tried upgrading to 10.04 hoping that would help, but no such luck.

I notice that when I restart the networking, ath0 is trying to get a dhcp address, should that be happening?

---

### Post by inox84 on 2010-05-14
Hi!

Set SSH server up and running on your router PC

sudo apt-get install openssh-server

Set ath0 an IP address manually in /etc/network/interfaces

address 192.168.1.1
netmask 255.255.255.0

Set your wireless client manually to use 192.168.1.2 and the netmask above.

Don't bridge any interfaces!

Try 64bit WEP key, not the 128bit one.

Check your connection with static IPs assigned (we are not checking the Internet access, but the local "network" only):

In gnome-terminal (on client machine) try: ssh 192.168.1.1
On Windows use PuTTY.

If everything is ok. setup your NAT.
You can follow [http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html) (change appropriate ethX-s to ath0-s :D).

Then think of dhcp...

---

### Post by gnat man on 2010-05-15
Thank you for the response.

I tried what you said, and I switched the ath0 to static, and I have tried connecting with a couple of devices (iPhone, android, and ubuntu) and none of them can connect to the network.

On the iPhone for example, I set it all to manual, then I select the network, and it tries to connect, but it never actually associates. 

The only error I see when I restart networking (on the machine to be a router) is this one:

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801

But I see that everywhere when I'm searching, for people where it even works, so I doubt that that's the problem here.

---

