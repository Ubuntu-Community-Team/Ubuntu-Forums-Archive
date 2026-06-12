---
title: "Ubuntu Router Guide"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by Ellias on 2006-01-20
HOWTO-Ubuntu internet router, Firewall,DHCP,DNS,NAT
By: Ellias, special thanks to Mips 


This tutorial will go over all the steps one must take in order to set-up routing on a Linux box. There are some minimum requirements you must have in order to follow this tutorial to its completion. First you need a PC with Linux on it, the examples I will be giving are based off the Ubuntu distribution, but my examples should work on most other Debian based distributions and only slight modifications are needed to get it to work with Red Hat, etc... Second, you need two NICs. In my examples I will be showing how to do this with three NICs, 1 external and 2 internal. You probably need two cross-over cables to connect from PC to PC and one straight-through to connect from PC to modem, router, or switch (that will be on your external NIC). I say probably because some more advanced NICs support automatic conversion between the two. Thirdly, you need a somewhat working knowledge of Linux and networking in general, I will be covering a wide range of networking topics that are nec
essary to gain router functionality. Now before we get our feet wet, disclaimer time...

I am not responsible for any damage done to your computers and/or network. By following the instructions in this document you agree to these terms and recognize that you are solely responsible for what you do while following the instructions. Furthermore, the scripts provided here should NOT be used for a production and/or business environment. They are not secure and further modification would be needed in order to make them so. These instructions are for home use, educational purposes only.

There, now here is the setup I will be referring to in this document.

Internet
|
L Router (192.168.0.1) ----- PC's connected to router
|
|
Switch (typical 4 port) ----- PC's connect to switch 
|
|
Our Linux Box with Ubuntu Linux (connected to switch as well)
(3 NICs)
L eth2 (192.168.0.103) via DHCP from Router above.
L eth1 (192.168.1.1 ) Statically assigned --------- Connecting PC
L eth2 (192.168.2.1) Statically assigned --------- Connecting PC

Ok, so you've got things setup and ready to go. Now you need a way for the PCs connecting to the Linux box to get an IP address. For this we can use the DHCP server that comes with Linux. If you don't already have this a simple 'sudo apt-get install dhcp3-server' should get it for you just fine.

Once this is done you're going to have to configure it. The base of this configuration file was taken from Sean O'Donnell [http://code.seanodonnell.com](http://code.seanodonnell.com), but modified to fit our configuration here.

So type.... 'vim /etc/dhcp3/dhcpd.conf'
and put the following in there (numbers may need to be tweaked for your setup)

```

# Configuration file for ISC dhcpd (see 'man dhcpd.conf')
#
# For more information regarding the ISC DHCP Daemon,
# please visit: http://www.isc.org/sw/dhcp/
#
##########################################################
#
# Configuration Notes:
#
# This configuration file assumes that you
# have a total of 4 NIC cards installed on your system,
# with eth2 connecting (as a client) to a remote dhcp server. 
#
# This will assign a dhcp subnet to each additional NIC card
# (eth1, eth0), which can be used to create a
# multi-subnet DHCP Server.
#
# Example by: Sean O'Donnell http://code.seanodonnell.com
#
##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc; 

# this may be required for some network configurations,
# but seems to work fine without it on my LAN.
option domain-name "my-dhcp-server.com";

#assign the remote dhcp server hostname/ip addresses 
option domain-name-servers 192.168.1.1, 192.168.2.1;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth0 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
}

# eth1 subnet configuration
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.99;
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;
}

##########################################################
# end config

```

Now to modify the /etc/default/dhcp3-server file to include eth1 at the bottom...

```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests? 
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0 eth1"

```

Now restart the DHCP server by typing ' sudo /etc/init.d/dhcp3-server restart '
After that try resolving an IP with the connecting PC's (remember to use crossover cables when connecting). If you got IP's on both of the sub netted PC's great, thats a big step. If not, go back and check your configs match your current set-up. Use the 'ifconfig' command to check if you are using the right IP addresses.

Once you've got it working your ready to now setup DNS. DNS is a snap, all you should need to do is type, 'sudo apt-get install bind9'. Boom you have a small DNS server on you box! This is so computers connecting to your router will be able to resolve web addresses based on their URL instead of their IP. For example...

instead of typing traceroute 216.239.37.147 you can type traceroute [www.google.com](www.google.com) and still gain the same functionality!

Now there is just one more thing needed, and thats a script enabling IP Masquerade. I was able to figure this out by consulting.... (by the way I highly recommended reading over their site, it's very comprehensive and was a key part in me figuring out how to get this to work).

[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

by slightly modifying their example scripts I came up with this...

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
EXTIF="eth2"
INTIF="eth1"
INTIF2="eth0"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo "   Internal Interface:  $INTIF2" 

EXTIP="your external IP address"
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

Notice the top, you will have to set the external IP address to whatever it is for this to work. In this example it's eth2's IP. I realize that this is quite a long script but I left the comments in there because they explain what's going on in the script (remember the point of this is to learn).
Now run the shell script, 'sh scriptname' and your connecting PCs should have Internet access! If not, check out the script and see if everything is configured appropriately. Consult

[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

for further troubleshooting techniques.

Now assuming that everything is in order and working properly, we want to make our new script bootable so we don't have to run the script every time we restart.

Type: cp 'scriptname' /etc/init.d/'scriptname'

This copies the script to the init.d directory where other scripts are run at bootup. Now that, that is out of the way, we need to make a symbolic link in the rc2.d directory pointing to the script we stored in the init.d directory.

Type: ln -s /etc/init.d/'scriptname' /etc/rc2.d/S95masquradescript

Presto, restart your computer and test to see if you still have the same functionality. If so then congratulations! If not then make sure you followed the above correctly so the script is bootable.

Additional thanks to the webmasters of the URLs mentioned in this tutorial. Each site was a great aid.

---

### Post by unlotto on 2007-03-02
[COLOR="Silver"]This guide worked well for me. I have one problem though. I can't access certain sites like [www.ati.com](www.ati.com) and other sites like [www.quicktime.com](www.quicktime.com) - trailer section, seems only to respond halfways. I.e only some of the page gets loaded.

Proxy'ing the connection through a local proxy server will give me access, but is not ideal in my situation.

Do I need a special rule for port 443 https SSL or something like that?

Thanks![/COLOR]

update: It turns out one of the gateway's of my ISP is at fault.

---

### Post by Tr1p on 2007-06-23
doesent work here :(

---

### Post by __Preved on 2007-09-17
IP can be evaluated automatically. Just one less setting.

```

EXTIP=`ifconfig $EXTIF | grep 'inet addr:' | sed 's#.*inet addr\:\([0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\).*#\1#g'`

```

---

### Post by themoebius on 2007-12-12
Firestarter is a really easy way to manage your firewall. I find that the iptables scripts are really hard to understand. Firestarter does seem to spontaneously crash on my quite often though, which means the internet connection goes down.

---

