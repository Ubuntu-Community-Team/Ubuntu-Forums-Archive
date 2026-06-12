---
title: "wlan0 no internet connection when eth0 is up"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by avatardvr@gmail.com on 2009-05-30
Can someone help me please, or point me in the right direction maybe.  I am running Ubuntu 8.10. I have a wlan0 connected to the internet, works fine, and eth0 works locally but when its up I cant access the net anymore.  I am trying to set up a shared internet connection with the wireless being the internet access and eth0 to a router.  Been at it for too many hours.  Thanks for any help!

---

### Post by megerdin on 2009-05-30
you need to do a lots of things, specially route enable IP forwarding..  But i don't know how far u can handle. so theres a scripts for you. and this will do many thing more then your req. Just copy it and paste the script in a text file.

Give it executable permission.
```
chmod +x yourscriptfile
```
Run it as root and check.
```
/path/to/your/scrip/file/yourscriptfile
```

here is the script, you just need to edit 2 line between ** to adapt your network.
*************

************
```
#!/bin/sh
#
# rc.firewall-iptables-stronger
#
FWVER=0.88s

#          An example of a stronger IPTABLES firewall with IP Masquerade 
#          support for 2.4.x kernels.  
#
# Log:
#
#   0.88s - Updated the commands for dynamically addresses machines and
#           to point to an expanded FAQ section for more information
#
#   0.87s - Removed the unused drop-and-logit chain as it was only later
#           being deleted anyway
#   0.86s - Fixed a typo that had a preceeding ; instead of a #
#   0.85s - renamed from rc.firewall-2.4-stronger to rc.firewall-iptables-
#           stronger to reflect this script works for all IPTABLES enabled
#           platforms including 2.6.x kernels
#         - fixed an incorrect /24 netmask for the INTIP variable
#         - removed the unneeded SED variable
#   0.84s - Changed the defaults from 192.168.1.0 to 192.168.0.x to align
#           with the rest of the IPMASQ howto
#   0.83s - Added additional comments to make PORTFW configs more obvious
#   0.82s - Added a special ICMP filter to work around a Netfilter security
#           issue
#         - renamed the drop-and-log-it rule to reject-and-log-it
#   0.81s - Added an additional comment in the INPUT section for NOT 
#           allowing all traffic in, but only select traffic
#   0.80s - Added a DISABLED ip_nat_irc kernel module section, changed the
#           default of the ip_conntrack_irc to NOT load by default, and 
#           added additional kernel module comments
#   0.79s - ruleset now uses modprobe instead of insmod
#   0.78s - REJECT is not a legal policy yet; back to DROP
#   0.77s - Changed the default block behavior to REJECT not DROP
#   0.76s - Added a comment about the OPTIONAL WWW ruleset and a comment
#           where to put optional PORTFW commands
#   0.75s - Added clarification that PPPoE users need to use
#           "ppp0" instead of "eth0" for their external interface
#   0.74s - Changed the EXTIP command to work on NON-English distros
#   0.73s - Added comments in the output section that DHCPd is optional
#           and changed the default settings to disabled
#   0.72s - Changed the filter from the INTNET to the INTIP to be
#           stateful; moved the command VARs to the top and made the
#           rest of the script to use them
#   0.70s - Added a disabled examples for allowing internal DHCP  
#           and external WWW access to the server
#   0.63s - Added support for the IRC module
#   0.62s - Initial version based upon the basic 2.4.x rc.firewall


echo -e "\nLoading rc.firewall-iptables-STRONGER - version $FWVER..\n"


# The location of various iptables and other shell programs
#
#   If your Linux distribution came with a copy of iptables, most
#   likely it is located in /sbin.  If you manually compiled 
#   iptables, the default location is in /usr/local/sbin
#
# ** Please use the "whereis iptables" command to figure out 
# ** where your copy is and change the path below to reflect 
# ** your setup
#
#IPTABLES=/sbin/iptables
IPTABLES=/sbin/iptables
#
LSMOD=/sbin/lsmod
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe
GREP=/bin/grep
AWK=/bin/awk
IFCONFIG=/sbin/ifconfig


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
#  NOTE:  If this doesnt EXACTLY fit your configuration, you must 
#         change the EXTIF or INTIF variables above. For example: 
#
#            If you are a PPPoE or analog modem user:
#
#               EXTIF="ppp0" 
#
EXTIF="wlan0"
INTIF="eth0"
echo "  External Interface:  $EXTIF"
echo "  Internal Interface:  $INTIF"
echo "  ---"

# Specify your Static IP address here or let the script take care of it 
# for you.
#
#   If you prefer to use STATIC addresses in your firewalls, un-# out the
#   static example below and # out the dynamic line.  If you don't care,
#   just leave this section alone.
#
#   If you have a DYNAMIC IP address, the ruleset already takes care of
#   this for you.  Please note that the different single and double quote 
#   characters and the script MATTER.
#
#
#   PPP and DHCP (Cablemodem and DSL ) users:
#   -----------------------------------------
#   PPP: If you get your TCP/IP address via DHCP, **you will need ** to 
#   enable the #   #ed out command below underneath the PPP section AND 
#   replace the word "eth0" with the name of your EXTERNAL Internet 
#   connection (ppp0, ippp0, etc) on the lines for "ppp-ip" and "extip".  
#
#   DHCP and PPP users:  The remote DHCP or PPP server can and will change 
#   IP addresses on you over time.  To deal with this, users should configure 
#   their DHCP or PPP client to re-run the rc.firewall-* ruleset everytime 
#   the IP address is changed.  Please see the "masq-and-dyn-addr" FAQ entry 
#   in the IPMASQ howto for full details on how to do this.
#
#
# Determine the external IP automatically:
# ----------------------------------------
#
#  The following line will determine your external IP address.  This
#  line is somewhat complex and confusing but it will also work for
#  all NON-English Linux distributions:
#

EXTIP="`$IFCONFIG $EXTIF | $AWK \
 /$EXTIF/'{next}//{split($0,a,":");split(a[2],a," ");print a[1];exit}'`"


# For users who wish to use STATIC IP addresses:
#
#  # out the EXTIP line above and un-# out the EXTIP line below
#
#EXTIP="your.static.PPP.address"
echo "  External IP: $EXTIP"
echo "  ---"

#*******************************************************************************
# Assign the internal TCP/IP network and IP address
#Edit this line according to ur configuration

INTNET="192.168.0.0/24" # assign your internel network
INTIP="192.168.0.1/32"  # assign your eth0 IP and network

#**********************************************************************

echo "  Internal Network: $INTNET"
echo "  Internal IP:      $INTIP"
echo "  ---"



# Setting a few other local variables
#
UNIVERSE="0.0.0.0/0"

#======================================================================
#== No editing beyond this line is required for initial MASQ testing ==

# Need to verify that all modules have all required dependencies
#
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a

echo -en "    Loading kernel modules: "

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

#Load the main body of the IPTABLES module - "ip_tables"
#  - Loaded automatically when the "iptables" command is invoked
#
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "ip_tables, "
#
#Verify the module isn't loaded.  If it is, skip it
#
if [ -z "` $LSMOD | $GREP ip_tables | $AWK {'print $1'} `" ]; then
   $MODPROBE ip_tables
fi


#Load the IPTABLES filtering module - "iptable_filter" 
#
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
#
#Verify the module isn't loaded.  If it is, skip it
#
if [ -z "` $LSMOD | $GREP ip_conntrack | $AWK {'print $1'} `" ]; then
   $MODPROBE ip_conntrack
fi


#Load the FTP tracking mechanism for full FTP tracking
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -e "ip_conntrack_ftp, "
#
#Verify the module isn't loaded.  If it is, skip it
#
if [ -z "` $LSMOD | $GREP ip_conntrack_ftp | $AWK {'print $1'} `" ]; then
   $MODPROBE ip_conntrack_ftp
fi


#Load the IRC tracking mechanism for full IRC tracking
#
# Disabled by default -- insert a "#" on the next few lines to activate
#
# echo -en "                             ip_conntrack_irc, "
#
#Verify the module isn't loaded.  If it is, skip it
#
# if [ -z "` $LSMOD | $GREP ip_conntrack_irc | $AWK {'print $1'} `" ]; then
#    $MODPROBE ip_conntrack_irc
# fi


#Load the general IPTABLES NAT code - "iptable_nat"
#  - Loaded automatically when MASQ functionality is turned on
# 
#  - Loaded manually to clean up kernel auto-loading timing issues
#
echo -en "iptable_nat, "
#
#Verify the module isn't loaded.  If it is, skip it
#
if [ -z "` $LSMOD | $GREP iptable_nat | $AWK {'print $1'} `" ]; then
   $MODPROBE iptable_nat
fi


#Loads the FTP NAT functionality into the core IPTABLES code
# Required to support non-PASV FTP.
#
# Enabled by default -- insert a "#" on the next line to deactivate
#
echo -e "ip_nat_ftp"
#
#Verify the module isn't loaded.  If it is, skip it
#
if [ -z "` $LSMOD | $GREP ip_nat_ftp | $AWK {'print $1'} `" ]; then
   $MODPROBE ip_nat_ftp
fi


#Loads the IRC NAT functionality (for DCC) into the core IPTABLES code
#
# DISABLED by default -- delete the "#" on the next few lines to activate
#
# echo -e "ip_nat_irc"
#
#Verify the module isn't loaded.  If it is, skip it
#
# if [ -z "` $LSMOD | $GREP ip_nat_irc | $AWK {'print $1'} `" ]; then
#    $MODPROBE ip_nat_irc
# fi


echo "  ---"

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


#CRITICAL:  Enable IP forwarding since it is disabled by default since
#
#           Redhat Users:  you may try changing the options in
#                          /etc/sysconfig/network from:
#
#                       FORWARD_IPV4=false
#                             to
#                       FORWARD_IPV4=true
#
echo "  Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward


# Dynamic IP users:
#
#   If you get your IP address dynamically from SLIP, PPP, or DHCP, 
#   enable the following option.  This enables dynamic-address hacking
#   which makes the life with Diald and similar programs much easier.
#
echo "  Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr

echo "  ---"

#############################################################################
#
# Enable Stronger IP forwarding and Masquerading
#
#  NOTE:  In IPTABLES speak, IP Masquerading is a form of SourceNAT or SNAT.
#
#  NOTE #2:  The following is an example for an internal LAN address in the
#            192.168.0.x network with a 255.255.255.0 or a "24" bit subnet 
#            mask connecting to the Internet on external interface "eth0".  
#            This example will MASQ internal traffic out to the Internet 
#            but not allow non-initiated traffic into your internal network.
#
#            
#         ** Please change the above network numbers, subnet mask, and your 
#         

#Clearing any previous configuration
#
#  Unless specified, the defaults for INPUT, OUTPUT, and FORWARD to DROP
#
#    You CANNOT change this to REJECT as it isn't a vaild policy setting.
#    If you want REJECT, you must explictly REJECT at the end of a giving 
#    INPUT, OUTPUT, or FORWARD chain
#
echo "  Clearing any existing rules and setting default policy to DROP.."
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -F -t nat

#Not needed and it will only load the unneeded kernel module
#
#$IPTABLES -F -t mangle


# Delete all User-specified chains
$IPTABLES -X


# Reset all IPTABLES counters
$IPTABLES -Z


#Configuring specific CHAINS for later use in the ruleset
#
#  NOTE:  Some users prefer to have their firewall silently
#         "DROP" packets while others prefer to use "REJECT"
#         to send ICMP error messages back to the remote 
#         machine.  The default is "REJECT" but feel free to
#         change this below.
#
# NOTE: Without the --log-level set to "info", every single
#       firewall hit will goto ALL vtys.  This is a very big
#       pain.
#
echo "  Creating a DROP chain.."
$IPTABLES -N reject-and-log-it
$IPTABLES -A reject-and-log-it -j LOG --log-level info 
$IPTABLES -A reject-and-log-it -j REJECT

echo -e "\n   - Loading INPUT rulesets"


#######################################################################
# INPUT: Incoming traffic from various interfaces.  All rulesets are 
#        already flushed and set to a default policy of DROP. 
#

# loopback interfaces are valid.
#
$IPTABLES -A INPUT -i lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# local interface, local machines, going anywhere is valid
#
$IPTABLES -A INPUT -i $INTIF -s $INTNET -d $UNIVERSE -j ACCEPT


# remote interface, claiming to be local machines, IP spoofing, get lost
#
$IPTABLES -A INPUT -i $EXTIF -s $INTNET -d $UNIVERSE -j reject-and-log-it


# external interface, from any source, for ICMP traffic is valid
#
#  If you would like your machine to "ping" from the Internet, 
#  enable this next line
#
#$IPTABLES -A INPUT -i $EXTIF -p ICMP -s $UNIVERSE -d $EXTIP -j ACCEPT


# remote interface, any source, going to the MASQ servers IP address is valid
#
#  ENABLE this line if you want ALL Internet traffic to connect to your
#  the various servers running on the MASQ server.  This includes 
#  web servers, ssh servers, dns servers, etc.  
#
#  I DON'T recommend you enable this rule.  Instead, only enable specific
#  access to select server ports under the "OPTIONAL INPUT Section".
#  An example of enabling HTTP (WWW) has been given below:
#
#
#$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -j ACCEPT

##

# Allow any related traffic coming back to the MASQ server in.
#
#  STATEFULLY TRACKED

$IPTABLES -A INPUT -i $EXTIF -s $UNIVERSE -d $EXTIP -m state --state \
 ESTABLISHED,RELATED -j ACCEPT


# ----- Begin OPTIONAL INPUT Section -----
#

# DHCPd - Enable the following lines if you run an INTERNAL DHCPd server
#
#$IPTABLES -A INPUT -i $INTIF -p tcp --sport 68 --dport 67 -j ACCEPT
#$IPTABLES -A INPUT -i $INTIF -p udp --sport 68 --dport 67 -j ACCEPT

# HTTPd - Enable the following lines if you run an EXTERNAL WWW server
#
#    NOTE:  This is NOT needed for simply enabling PORTFW.  This is ONLY 
#           for users that plan on running Apache on the MASQ server itself
#
#echo -e "      - Allowing EXTERNAL access to the WWW server"
#$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,ESTABLISHED,RELATED \
# -p tcp -s $UNIVERSE -d $EXTIP --dport 80 -j ACCEPT

######################################################################
#
# ----- End OPTIONAL INPUT Section -----


# Catch all rule, all other incoming is denied and logged. 
#
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j reject-and-log-it


# ---------------------------------------------------------------------

echo -e "   - Loading OUTPUT rulesets"

#######################################################################
# OUTPUT: Outgoing traffic from various interfaces.  All rulesets are 
#         already flushed and set to a default policy of DROP. 
#

# Workaround bug in netfilter
# See http://www.netfilter.org/security/2002-04-02-icmp-dnat.html
#
$IPTABLES -A OUTPUT -m state -p icmp --state INVALID -j DROP

# loopback interface is valid.
#
$IPTABLES -A OUTPUT -o lo -s $UNIVERSE -d $UNIVERSE -j ACCEPT


# local interfaces, any source going to local net is valid
#
$IPTABLES -A OUTPUT -o $INTIF -s $EXTIP -d $INTNET -j ACCEPT


# local interface, MASQ server source going to the local net is valid
#
$IPTABLES -A OUTPUT -o $INTIF -s $INTIP -d $INTNET -j ACCEPT


# outgoing to local net on remote interface, stuffed routing, deny
#
$IPTABLES -A OUTPUT -o $EXTIF -s $UNIVERSE -d $INTNET -j reject-and-log-it


# anything else outgoing on remote interface is valid
#
$IPTABLES -A OUTPUT -o $EXTIF -s $EXTIP -d $UNIVERSE -j ACCEPT


# ----- Begin OPTIONAL OUTPUT Section -----
#

# DHCPd - Enable the following lines if you run an INTERNAL DHCPd server
#         - Remove BOTH #s all the #s if you need this functionality.
#
#$IPTABLES -A OUTPUT -o $INTIF -p tcp -s $INTIP --sport 67 \
# -d 255.255.255.255 --dport 68 -j ACCEPT
#$IPTABLES -A OUTPUT -o $INTIF -p udp -s $INTIP --sport 67 \
# -d 255.255.255.255 --dport 68 -j ACCEPT

#
# ----- End OPTIONAL OUTPUT Section -----


# Catch all rule, all other outgoing is denied and logged. 
#
$IPTABLES -A OUTPUT -s $UNIVERSE -d $UNIVERSE -j reject-and-log-it


echo -e "   - Loading FORWARD rulesets"

#######################################################################
# FORWARD: Enable Forwarding and thus IPMASQ
#

# ----- Begin OPTIONAL FORWARD Section -----
#
#  Put PORTFW commands here
#
# ----- End OPTIONAL FORWARD Section -----


echo "     - FWD: Allow all connections OUT and only existing/related IN"
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED \
 -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT

# Catch all rule, all other forwarding is denied and logged. 
#
$IPTABLES -A FORWARD -j reject-and-log-it


echo "     - NAT: Enabling SNAT (MASQUERADE) functionality on $EXTIF"
#
#More liberal form
#$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
$IPTABLES -t nat -A POSTROUTING -o eth0 -j MASQUERADE
#
#Stricter form
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j SNAT --to $EXTIP


#######################################################################
echo -e "\nrc.firewall-iptables-stronger $FWVER done.\n"


#iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to 192.168.0.1:3128
#iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3128 -j REDIRECT --to-port 8080

echo -e "    Loading Squid rule loading complete\n\n"
```

let me know what are you doing? If any problem just post your route comand output here.

```
route -n

```

---

### Post by Iowan on 2009-05-30
Older versions of NM would manage only one interface at a time.  Dunno if this is still the case, but you might try configuring one interface via */etc/network/interfaces*. As I recall, Hardy and Intrepid (which I skipped) had some issues with that, so it may not work - be prepared to edit out the configuration (or copy back from the backup file you made ;) ).

---

### Post by superprash2003 on 2009-05-30
you need to tell ubuntu to use wlan0 for internet even when eth0 is connected [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by avatardvr@gmail.com on 2009-05-31
thanks for all your help.  I'll post with my results.

---

### Post by avatardvr@gmail.com on 2009-05-31
megerdin, I used your script and broke my network.  lost both devices somehow and Im not sure how to get them back.   route -n reveals no information and though ifconfig suggests my devices are there, there is no ip address for either wlan0 or eth0 and they are listed under network manager as unmanaged.  Any adice? I had to borrow a laptop to get online.  Thanks for your help.  

Edit.  i got back to my original problem by removing my changes to /etc/network/interfaces file so I am back online.  route -n now reveals the following

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by avatardvr@gmail.com on 2009-06-01
still havent been able to make any progress on this... any help with a next step?

---

### Post by mgarrana on 2009-11-17
> **superprash2003 said:**
> you need to tell ubuntu to use wlan0 for internet even when eth0 is connected [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

hi ... i had the same problem , and this worked for me
you simply need to manipulate the routing table but the use of route command
 for example
sudo route add default gw 10.0.0.1 wlan0
this adds 10.0.0.1 as your defualt G.W going through wlan0

sudo route add default gw 10.1.1.15  eth0
this removes 10.1.1.15 as being your default G.W going through eth0

you can then manually route add for specific subnets to go through your defualt G.W on eth0

in my case , i only needed to play with the route command ,
route -n shows you the current status of your routing table
you can also install traceroute to see where packets are going , this will help you know what's going on after your changes

---

### Post by megerdin on 2009-11-18
> **avatardvr@gmail.com said:**
> still havent been able to make any progress on this... any help with a next step?


Sorry I got disconnect. whats your status now?

---

