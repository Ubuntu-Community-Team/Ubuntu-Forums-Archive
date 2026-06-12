---
title: "Which is more secure: The iPhone or Ubuntu?"
date: 2012-12-28
forum: Mobile Technology Discussions (CLOSED)
---

### Post by aligator12 on 2012-12-28
Hi, which should I feel more secure using (for personal data) the iPhone (over the 3g network), or Ubuntu on a wifi network with possibly compromised systems?

---

### Post by chadk5utc on 2012-12-29
I think that any device that uses wireless is at some risk , some of this directly related to what the user does with or to it. That being said I also believe that 3G service is less likely to have the same risk as wifi strictly because the type of service it is and the fact that hardware for it is not usually user configurable except maybe username/password. Some precautions can be taken for wifi, firewalls, using a VPN when on public wifi and in general some commonsense, Think before you act dont do anything that would outright expose your personal data, banking info, credit cards Etc.

---

### Post by mike acker on 2012-12-29
i think it is going to depend greatly on what you  have installed

[ suggested reading ]("https://www.net-security.org/article.php?id=1734")

what does Firefox read from your computer and where does it send that information ?  that will depend on the scripts and add-ons running under Firefox ... or similar app, e.g. a music player

---

### Post by Hungry Man on 2012-12-29
Ubuntu is easier to secure, and you can likely trust your desktop browser to implement SSL far better than your mobile browser.

---

### Post by Ms. Daisy on 2012-12-29
> **aligator12 said:**
> Hi, which should I feel more secure using (for personal data) the iPhone (over the 3g network), or Ubuntu on a wifi network **with possibly compromised systems**? What does the bit in bold mean?  

Never do anything personal or important over a wifi network you don't trust.  You can do a bit better if you can tunnel out of the public wifi to your own server at home or a VPN and do your browsing through that tunnel.  Barring that, at the very least you should have strong inbound and outbound firewall rules on your PC (and I wouldn't do financial transaction online).

If you think there are compromised systems on the same network as you, then **get them cleaned up** if they're yours.  I can't imagine a scenario where it would be OK to allow compromised systems to co-exist with my system on the same network.  If they're not yours then I personally would stick with 3g.

---

### Post by mike acker on 2012-12-29
it was with some misgiving that i read the following

                          > "Online hackers may create websites that automatically trigger the installation of malicious extensions," Google wrote in a [the Chrome help section]("http://support.google.com/chrome_webstore/bin/answer.py?hl=en&answer=2664769&p=crx_warning"). "Their extensions are often designed to secretly track the information you enter on the Web, which the hackers can then reuse for other, ill-intended purposes."This was regarding Google's recent decision to take control of the installation of plug-ins for Chrome [ REFERENCE Tech news Daily ]("http://www.technewsdaily.com/16115-chrome-25-plug-in-install-changes.html")
there was a similar report on C/Net
[ Reference: C/net ]("http://reviews.cnet.com/8301-3514_7-57560757/chrome-prepares-to-ax-silent-extensions/")

C/Net's report notes
> These changes pull Chrome in line with changes that Mozilla made to [Firefox]("http://www.cnet.com/firefox-3/")'s  add-on management policies. If Chrome's implementation resembles  Firefox's, then the third-parties, such as security suite vendors or  businesses, will still be able to get their extensions installed. It  will just take an extra click from the end user. these notes raise concerns regarding -- what is installed in our browser and -- what can the installed plug-ins and/or web page scripts actually do ?

I have my Firefox running in AppArmor provided by Canonical but I need to learn how to read and edit that profile . i would like to restrict my browser to one sub-directory in my /documents area

it is critical to security to remember that most hacking is accomplished via un-authorized programming (aka "malware") running in either the client or in the server . this would be like 95% of the problem; attacks on traffic in progress on the net are much less common -- although usually related to unsecured wireless .

---

### Post by bodueko on 2012-12-29
If you are going to use ubuntu with compromised systems then i strongly urge you to try this configuration:

Try this config (NOTE: IT IS STILL A WORK IN PROGRESS) BUT IT HELPS

```
# copy and paste this "sudo gedit /etc/ufw/before.rules" without the quotes in terminal
# Then copy from the next line of rules to replace the firewall default rules
#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
# ufw-before-input
# ufw-before-output
# ufw-before-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


################################################## ################################################
# FIREWALL ARRANGEMENT PREVENTS DDoS DROPPING INVALID BEFORE PROCESSING VALID PLUS FULL TRACKING #
################################################## ################################################


################################################## #####################################
# drop INVALID inbound packets (logs these in loglevel medium and higher)
################################################## #####################################
-A ufw-before-input -p all -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -p all -m state --state INVALID -j DROP
################################################## #####################################


################################################## #####################################
# DROP FROM UNSPEC(0.0.0.0) - [Ensure source address verification is on]
################################################## #####################################
-A ufw-before-input -p all -m addrtype --src-type UNSPEC -j DROP
################################################## #####################################


################################################## #####################################
# DROP FROM UNREACHABLE - [Ensure source address verification is on]
# To use this ensure [icmp - destination-unreachable] is accepted
################################################## #####################################
#-A ufw-before-input -p all -m addrtype --src-type UNREACHABLE -j DROP
################################################## #####################################


################################################## #####################################
# DROP FROM MULTICAST [affects IGMP] - [Ensure source address verification is on]
################################################## #####################################
-A ufw-before-input -p all -m addrtype --src-type MULTICAST -j DROP
################################################## #####################################


################################################## #####################################
# DROP FROM LOCAL - [Ensure source address verification is on]
################################################## #####################################
-A ufw-before-input -p all -m addrtype --src-type LOCAL --dst-type ANYCAST -j DROP
-A ufw-before-input -p all -m addrtype --src-type LOCAL --dst-type MULTICAST -j DROP
-A ufw-before-input -p all -m addrtype --src-type LOCAL --dst-type BROADCAST -j DROP
################################################## #####################################


################################################## #####################################
# [Prevent malicious tcp looped/reversed connection initiation]
# [Packets with only 'syn' bit set and 'ACK,RST and FIN bits cleared']
################################################## #####################################
-A ufw-before-input -p tcp --syn -m state --state NEW,ESTABLISHED,RELATED -j DROP
################################################## #####################################


# [allow all on loopback]
# Any traffic that a computer program sends to the loopback interface 
# is immediately received on the same interface.
# This works without any actual network connection&#8211;so it is useful for testing services 
# without exposing them to security risks from remote network access. 
# This is primarily a means of testing the transmission or transportation infrastructure.
# ***** CAUTION - IT IS A TARGET FOR SPOOFING TO LEAK TRAFFIC TO REMOTE NETWORK *****
# ***** [BLOCK ALL TRAFFIC GOING OUT TO 127.0.0.0/8 WITH THE USER FIREWALL] *****
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT


# quickly process packets for which we initiated and already have a connection
-A ufw-before-input -p all -m state --state ESTABLISHED,RELATED -j ACCEPT


# connection loop tracking/processing for initiated outbound connections
-A ufw-before-output -p all -m state --state ESTABLISHED,RELATED -j ACCEPT

################################################## #####################################
# DROP TO UNSPEC(0.0.0.0)
################################################## #####################################
-A ufw-before-output -p all -m addrtype --dst-type UNSPEC -j DROP
################################################## #####################################


################################################## #####################################
# DROP TO PROHIBIT
################################################## #####################################
-A ufw-before-output -p all -m addrtype --dst-type PROHIBIT -j DROP
################################################## #####################################


################################################## #####################################
# DROP CASTING [WE ARE NOT A ROUTER]
# [BROADCAT USED BY DHCP CLIENT FOR DHCP DISCOVERY]
################################################## #####################################
-A ufw-before-output -p all -m addrtype --dst-type ANYCAST -j DROP
-A ufw-before-output -p all -m addrtype --dst-type MULTICAST -j DROP
################################################## #####################################


# connection tracking initiation for outbound
-A ufw-before-output -p all -m state --state NEW -j ACCEPT


################################################## #########################################
# -----[ok icmp codes]
# *****[because the state{NEW,ESTABLISHED,RELATED} of icmp cannot be verified]*****
# *****[firewall rule set arrangement above will DROP icmp as INVALID regardless if it is set to ACCEPT]*****
################################################## #########################################
# ********** DROP all of these packets to prevent DDoS **********
# Use REJECT with caution - possible DDoS generating reject packets
# ********** [source-quench] is used for traffic throttling **********
################################################## #########################################
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP
################################################## ##########################################


################################################## ##########################################
# allow DHCP client to work
# [UDP PERMITS ONLY SOURCE TO DESTINATION PORT VERIFICATION ONLY] - [ENSURE SOURCE ADDRESS VERIFICATION IS ON]
# Initially DHCP Client sends a [broadcast] request and recieves a [UNICAST] DHCP discovery response
-A ufw-before-input -p udp --sport 67 --dport 68 -m addrtype --src-type LOCAL --dst-type UNICAST -j ACCEPT

# Allow L2TP only over IPSEC
-A ufw-before-input -m policy --dir in --pol ipsec -p udp --dport 1701 -j ACCEPT
################################################## ###########################################


################################################## ########
# -----*****traffic of not-local below*****----- #
################################################## ########

-A ufw-before-input -j ufw-not-local

# if [LOCAL] RETURN - [Process internet traffic]
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if [MULTICAST] DROP
# *****[PREVENT DDoS]*****
-A ufw-not-local -m addrtype --dst-type MULTICAST -j DROP

# if [ANYCAST] DROP
# *** PREVENT ROGUE SERVERS FROM CAUSING DDoS ATTACKS ***
-A ufw-not-local -m addrtype --dst-type ANYCAST -j DROP

# if [BROADCAST] DROP
# *****[PREVENT DDoS]*****
# Broadcasting may be abused to perform a DoS-attack. 
# The attacker sends fake ping request with the source IP-address of the victim computer. 
# The victim computer is flooded by the replies from all computers in the domain.
-A ufw-not-local -m addrtype --dst-type BROADCAST -j DROP

# all other non-local packets are dropped
# [If rate is above the specified below then start logging traffic]
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

# Deny MULTICAST mDNS for service discovery 
# If intended for use (be sure the MULTICAST line above is uncommented)
-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j DROP

# Deny MULTICAST UPnP for service discovery 
# If intended for use (be sure the MULTICAST line above is uncommented)
-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j DROP

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT


#
# OPEN TERMINAL AND COPY AND PASTE "sudo gedit /etc/ufw/after.rules"
# REPLACE CONTENTS WITH CONTENTS BELOW THIS LINE
#
# rules.input-after
#
# Rules that should be run after the ufw command line added rules. Custom
# rules should be added to one of these chains:
# ufw-after-input
# ufw-after-output
# ufw-after-forward
#

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-after-input - [0:0]
:ufw-after-output - [0:0]
:ufw-after-forward - [0:0]
# End required lines

# don't log noisy services by default
-A ufw-after-input -p udp --dport 137 -m addrtype --dst-type UNICAST -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 138 -m addrtype --dst-type UNICAST -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp --dport 139 -m addrtype --dst-type UNICAST -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp --dport 445 -m addrtype --dst-type UNICAST -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 67 -m addrtype --dst-type UNICAST -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 67 -m addrtype --dst-type UNICAST -j ufw-skip-to-policy-input
-A ufw-after-input -p udp --dport 68 -m addrtype --dst-type UNICAST -j ufw-skip-to-policy-input

# don't log noisy CASTS - [Handles both 'LAN' and 'WAN' traffic]
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input
-A ufw-after-input -m addrtype --dst-type MULTICAST -j DROP
-A ufw-after-input -m addrtype --dst-type ANYCAST -j DROP

# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT


# Copy and paste "sudo gedit /etc/sysctl.conf" into terminal and hit enter
# Copy and paste the configuration below into opened document and Save the document
# Then copy and paste "sudo sysctl -p" into terminal and hit enter
#
################################################## ########################
## COPY FROM THE LINE JUST ABOVE THIS TEXT
################################################## ########################
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

################################################## ############3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to prevent some spoofing attacks
# FOR SERVER TURN IT OFF BY SETTING VALUE TO 0, FOR DESKTOP LEAVE IT ON WITH VALUE 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
#
#
# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
# Block SYN attacks
# Syn cookies acts as a recovery back up to the backlog/syn retries/syn ackretries
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_synack_retries = 2
net.ipv4.tcp_syn_retries = 2
#
#
# Preferably prevent packet forwarding for IPv4 by setting value to 0
# *****ENABLE PACKET FORWARDING IF YOU INTEND TO USE OPENVPN*****
# *****'MITM' MONITORING BODIES CAN HIJACK TRAFFIC AND DIRECT TO LESS SECURE DESTINATION*****
# To enable it change the value "0" below to value "1"
net.ipv4.ip_forward = 1
#
# Uncomment the next line to enable packet forwarding for IPv6
# Enabling this option disables Stateless Address Autoconfiguration
# based on Router Advertisements for this host
net.ipv6.conf.all.forwarding = 0
#
#
################################################## #################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
#
# Controls the System Request debugging functionality of the kernel
kernel.sysrq = 0
#
#
# Controls whether core dumps will append the PID to the core filename.
# Useful for debugging multi-threaded applications.
kernel.core_uses_pid = 1
#
#
# Do not accept ICMP redirects (prevent MITM attacks)
# ***[Make sure no one can alter the routing tables]***
net.ipv4.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_redirects = 0
net.ipv4.conf.default.accept_redirects = 0 
net.ipv6.conf.default.accept_redirects = 0
#
#
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
net.ipv4.conf.all.secure_redirects = 0
#
#
# Do not send ICMP redirects (we are not a router)
# Ignore send redirects
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.default.send_redirects = 0
#
#
# Do not accept IP source route packets (we are not a router)
# Disable source packet routing
net.ipv4.conf.all.accept_source_route = 0
net.ipv6.conf.all.accept_source_route = 0 
net.ipv4.conf.default.accept_source_route = 0
net.ipv6.conf.default.accept_source_route = 0
#
#
########## IPv6 networking start ##############
# Number of Router Solicitations to send until assuming no routers are present.
# This is host and not router
net.ipv6.conf.default.router_solicitations = 0

# Accept Router Preference in RA?
net.ipv6.conf.default.accept_ra_rtr_pref = 0

# Learn Prefix Information in Router Advertisement
net.ipv6.conf.default.accept_ra_pinfo = 0

# Setting controls whether the system will accept Hop Limit settings from a router advertisement
net.ipv6.conf.default.accept_ra_defrtr = 0

#router advertisements can cause the system to assign a global unicast address to an interface
net.ipv6.conf.default.autoconf = 0

#how many neighbor solicitations to send out per address?
net.ipv6.conf.default.dad_transmits = 0

# How many global unicast IPv6 addresses can be assigned to each interface?
net.ipv6.conf.default.max_addresses = 1

########## IPv6 networking ends ##############
#
#
# Turn on and log spoofed, source routed, and redirect packets
net.ipv4.conf.all.log_martians = 1
net.ipv4.conf.default.log_martians = 1
#
#
# Turn on protection for bad icmp error messages
net.ipv4.icmp_ignore_bogus_error_responses = 1
#
#
# Ignore ICMP broadcast requests
# *****Avoid a smurf attack*****
net.ipv4.icmp_echo_ignore_broadcasts = 1
#
#
# Ignore Directed pings
net.ipv4.icmp_echo_ignore_all = 1
#
#
# increase system file descriptor limit 
fs.file-max = 65536
#
#
# (Default swappiness value is 60 - Proposed to be balanced)
# For speed & Longetivity of HDD/SSD - Decrease swappiness value
# (USB recommended = <5, SSD recommended = 10, HDD recommended = 15)
# For security prevention of RAM exploit - Increase the swappiness value
# *************************CAUTION****************** *********************
# IF INSTALLATION DOES NOT HAVE A SWAP PARTITION
# OPEN TERMINAL AND TYPE "sudo apt-get install zram-config" 
# ONLY AFTER DOING A FULL SYSTEM UPDATE
# ************************************************** *********************
vm.swappiness = 0
vm.vfs_cache_pressure = 50
#
#
## Turn on Stack protection
kernel.randomize_va_space = 1
#
#
################################################## ##########
# Exec-shield no longer supported from ubuntu 11 and above
################################################## ##########
#
#
# Kernel protection and optimization
kernel.kptr_restrict = 1
kernel.yama.ptrace_scope = 1
kernel.sem = 250 32000 100 128
kernel.shmall = 2097152
kernel.shmmax = 134217728
kernel.shmmni = 4096
#
#
# Disable suid binaries from core dumps 
fs.suid_dumpable = 0
#
#
# Decrease the time default value for tcp_fin_timeout connection
# Reduces the FIN2 wait time
net.ipv4.tcp_fin_timeout = 10
#
#
# Decrease the time default value for tcp_keepalive_time connection in seconds
net.ipv4.tcp_keepalive_time = 3600
net.ipv4.tcp_keepalive_intvl = 60
net.ipv4.tcp_keepalive_probes = 3
#
#
# Reduce IP default time to live (ttl) from default 64 in seconds
# Recommended value is [18] - [In seconds] for privacy
# USE *** 24 when in a monitored environment *** and on slow internet
# TTL is a timer value included in packets sent over TCP/IP-based networks 
# that tells the recipients how long to hold or use the packet or any of its included data 
# before expiring and discarding the packet or data.
# *** While in transit the value reduces by 1 at every hop/interchange ***
net.ipv4.ip_default_ttl = 24
#
#
# Enable Forward RTO-Recovery (F-RTO) defined in RFC4138
# F-RTO is an enhanced recovery algorithm for TCP retransmission timeouts.
# It is particularly beneficial in wireless environments
# where packet loss is typically due to random radio interference
# 1 basic version is enabled.
# 2 enables SACK enhanced F-RTO if flow uses SACK.
net.ipv4.tcp_frto = 2
#
#
# Set FRTO response to 0
# 0 = Rate halving based; a smooth and conservative response
# 1 = Very conservative response; it interacts poorly with the rest of Linux TCP
# 2 = Aggressive response; undoes congestion control measures that are now known to be unnecessary
net.ipv4.tcp_frto_response = 2
#
#
# Turn on tcp abort on overflow
# Resets listening services in event on flood DDoS attack
net.ipv4.tcp_abort_on_overflow = 1
#
#
# Turn on the tcp_window_scaling
net.ipv4.tcp_window_scaling = 1
#
#
# Turn on the tcp_sack - Enable select acknowledgments (SACKS)
net.ipv4.tcp_sack = 1
#
#
# Enable tcp_fack - Enable FACK congestion avoidance and fast restransmission
net.ipv4.tcp_fack = 1
#
#
# Enable tcp_dsack - TCP Duplicate SACK support - [Added congestion avoidance measure].
net.ipv4.tcp_dsack = 1
#
#
# Enable thin duplicate ACK
# Enable dynamic triggering of retransmissions after one dupACK for thin streams. 
# If set, a check is performed upon reception of a dupACK to determine if the stream is thin (less than 4 packets in flight).
# This improves retransmission latency for non-aggressive thin streams, often found to be time-dependent.
net.ipv4.tcp_thin_dupack = 1
#
#
# Enable thin linear timeouts
# Enable dynamic triggering of linear timeouts for thin streams. 
# If set, a check is performed upon reception of a dupACK to determine if the stream is thin (less than 4 packets in flight).
# This improves retransmission latency for non-aggressive thin streams, often found to be time-dependent.
net.ipv4.tcp_thin_linear_timeouts = 1
#
#
# Reduce tcp re-odering - Default is 3
net.ipv4.tcp_reordering = 2
#
#
# Reduce tcp_retries1 - Default is 3
# How many times to retry before deciding that something is wrong 
# and it is necessary to report this suspection to network layer.Minimal RFC value is 3
net.ipv4.tcp_retries1 = 2
#
#
# Reduce tcp_retries2 - Default is 15 corresponds to ~13-30min depending on RTO.
# The default value of 15 yields a hypothetical timeout of 924.6 seconds 
# and is a lower bound for the effective timeout.
# How may times to retry before killing alive TCP connection.
# The RFC 1122 specified minimum limit of 100 seconds is typically deemed too short. 
# RFC1122 says that the limit should be longer than 100 sec 
# which corresponds to a value of at least 8.
net.ipv4.tcp_retries2 = 10
#
#
# Enable pmtu - (Path Maximum Transfer Unit) with value 0, disable with value 1
net.ipv4.ip_no_pmtu_disc = 0
#
#
# Turn on the tcp_timestamps
net.ipv4.tcp_timestamps = 1
#
#
# Increase the maximum tcp time wait buckets
# Maximal number of timewait sockets held by system simultaneously.
# If this number is exceeded time-wait socket is immediately destroyed and warning is printed. 
# [This limit exists only to prevent simple DoS attacks], you _must_ not lower the limit artificially,
# but rather increase it (probably, after increasing installed memory) - Max port capacity is [65535]
net.ipv4.tcp_max_tw_buckets = 4096
#
#
# Increase the maximum total TCP buffer-space allocatable
net.ipv4.tcp_mem = 4096 87380 8388608
#
#
# Increase the maximum TCP write-buffer-space allocatable
net.ipv4.tcp_wmem = 4096 87380 8388608
#
#
# Increase the maximum TCP read-buffer space allocatable
net.ipv4.tcp_rmem = 4096 87380 8388608
#
#
# Increase TCP queue length
net.ipv4.neigh.default.proxy_qlen = 96
net.ipv4.neigh.default.unres_qlen = 6
#
#
# Increase the maximum and default receive socket buffer size
net.core.rmem_max = 8388608
net.core.rmem_default = 8388608
#
#
# Increase the maximum and default send socket buffer size
net.core.wmem_max = 8388608
net.core.wmem_default = 8388608
#
#
# Increase the maximum amount of option memory buffers
net.core.optmem_max = 8388608
#
#
# increase Linux auto tuning TCP buffer limits
net.core.netdev_max_backlog = 4096
#
#
# Reduce igmp group membership - [Default = 20]
# Change the maximum number of multicast groups we can subscribe to.
net.ipv4.igmp_max_memberships = 0
#
#
# Optimizing network traffic
# [Vegas congestion avoidance detects congestion] 
# [before packet loss unlike others that detect after loss]
net.ipv4.tcp_congestion_control = vegas
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_orphan_retries = 2
net.ipv4.tcp_max_orphans = 256
net.ipv4.tcp_rfc1337 = 1
net.ipv4.udp_mem = 4096 87380 8388608
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
#
#
# Use/Don't use Explicit Congestion Notification in our packets.
# ECN is only used when both ends of the TCP flow support it. 
# It is useful to avoid packet loss due to congestion.
# Disable for security [If disabled some routers don't like it]
# 0 disable ECN
# 1 ECN enabled
# 2 Only server-side ECN enabled. If the other end does not support ECN, behavior is like with ECN disabled.
net.ipv4.tcp_ecn = 0
#
#
# This option tells the handler how long to keep an IP fragment in memory, 20 seconds in this case. 
# Only fragments that can not yet be assembled are kept here, 
# since fragments that can be assembled have already been moved.
net.ipv4.ipfrag_time = 20
#
#
# ipfrag_max_dist is a non-negative integer value which defines the maximum "disorder" 
# which is allowed among fragments which share a common IP source address. [Default = 64]
# Using a very small value, e.g. 1 or 2, for ipfrag_max_dist can result in unnecessarily dropping fragment queues 
# when normal reordering of packets occurs, which could lead to poor application performance. 
# Using a very large value, e.g. 50000, increases the likelihood of incorrectly reassembling IP fragments 
# that originate from different IP datagrams, which could result in data corruption.
net.ipv4.ipfrag_max_dist = 256
#
#
# We don't really want to proxy ARP for anyone, do we? 
# This option is turned off by default, but just to be safe..
net.ipv4.conf.all.proxy_arp = 0
#
#
#Increase system IP port limits
# Increase range with larger physical RAM (>128mb)
# Reduce range with lesser physical RAM (<128mb)
net.ipv4.ip_local_port_range = 2000 65000
#
#
# Increase the maximum memory used to reassemble IP fragments
net.ipv4.ipfrag_high_thresh = 512000
net.ipv4.ipfrag_low_thresh = 446464
#
#
# Set maximum amount of memory allocated to shm to 128MB
kernel.shmmax = 134217728
#
#
# Reboots system after 20 seconds of kernel panic
kernel.panic = 20
#
#
# Turn on route flush
net.ipv4.route.flush = 1
#
#
```

---

### Post by haqking on 2012-12-29
> **bodueko said:**
> 

copy and paste this "**sudo gedit** /etc/ufw/before.rules" 
#

You should use gksudo with graphical apps such as gedit.

---

### Post by Hungry Man on 2012-12-29
> You should use gksudo with graphical apps such as gedit.

Why?

---

### Post by haqking on 2012-12-29
> **Hungry Man said:**
> Why?

I have never had issues, however I know some have, everyones mileage varies.

it is best practice really

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

Due to files in your /home becoming owned by root

---

### Post by aligator12 on 2012-12-29
> **Ms. Daisy said:**
> What does the bit in bold mean?  

Never do anything personal or important over a wifi network you don't trust.  You can do a bit better if you can tunnel out of the public wifi to your own server at home or a VPN and do your browsing through that tunnel.  Barring that, at the very least you should have strong inbound and outbound firewall rules on your PC (and I wouldn't do financial transaction online).

If you think there are compromised systems on the same network as you, then **get them cleaned up** if they're yours.  I can't imagine a scenario where it would be OK to allow compromised systems to co-exist with my system on the same network.  If they're not yours then I personally would stick with 3g.

Well I am currently using my extended families wireless network, and I am 99% sure their computers are compromised. And they won't let me fix it because they don't trust me for some reason lol.

And since the wifi is compromised I am afraid to connect my iPhone to the wifi so I can't upgrade my iOS 5 to iOS 6, do you think that posses any security risks?

And can you get malware from text messages? I only use my iPhone for calls, texts, facebook, email and banking.

---

### Post by Ms. Daisy on 2012-12-29
> **aligator12 said:**
>  And can you get malware from text messages? I only use my iPhone for calls, texts, facebook, email and banking. Yes if the text message has a link in it that's malicious.  I think we've all gotten the spamtext message that we have won $10,000 and just need to call some number/click here to claim it. Obvious but worth stating: don't call, don't click, you didn't win.

Remember that your bank shouldn't email you links, so if you receive them they're probably spam/malicious.

I would recommend looking carefully at the apps you install in Facebook. A lot of them are spammy and want access to your contacts, and on the phone your Facebook contacts get weirdly merged with your phone contacts.  All of those stupid surveys ("which is the best boy band?") are apps.  I can't come up with a legitimate reason for a survey app to need access to your contacts, but if it wants it then I assume it's going to do something shady with it.

---

### Post by Ms. Daisy on 2012-12-29
> **haqking said:**
> I have never had issues, however I know some have, everyones mileage varies.

it is best practice really

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

Due to files in your /home becoming owned by rootIt has happened to me. It's a real PITA to fix, too.  gksudo is SOOOOOOO much easier.

Edit: not so much a pita to fix as it is to diagnose. You just find yourself locked out of /home.

---

### Post by bodueko on 2012-12-30
thanks.. sure.. would use gksudo instead

---

### Post by mike acker on 2012-12-30
> **Ms. Daisy said:**
> 
{snip}
I would recommend looking carefully at the apps you install in Facebook.{snip}
you might take a [ close look at fb itself]("https://www.net-security.org/article.php?id=1734")
then you take the battery out* of your "smart phone" before you toss it in the Herbie and get you a plain flip phone that has only txt and phone; no "apps" .

Note: I'm a privacy advocate . I think too much "data mining" is going on without our knowledge or permission .
~~
* uh-oh I just remembered the battery is glued into some of these phones :-( oh well, wrap it in tin-foil it'll go dead after a while .

---

### Post by offgridguy on 2012-12-30
> 

Note: I'm a privacy advocate . I think too much "data mining" is going on without our knowledge or permission.
I agree with you, not sure we can do much about it though.

---

### Post by aligator12 on 2013-01-04
> **Ms. Daisy said:**
> Yes if the text message has a link in it that's malicious.  I think we've all gotten the spamtext message that we have won $10,000 and just need to call some number/click here to claim it. Obvious but worth stating: don't call, don't click, you didn't win.
Sorry about the long reply time lol. :) I never ever follow links, but my iphone automatically opens spam text messages, there is no way to infect me that way is there?

---

### Post by aligator12 on 2013-01-05
bump

---

### Post by NCLI on 2013-01-06
> **aligator12 said:**
> bump
No, and you're being paranoid.

---

### Post by aligator12 on 2013-01-06
> **NCLI said:**
> No, and you're being paranoid.
I am glad you think that lol. But none of you guys think using an older obsolete iOS (iOS 5) is a bad security idea?

---

### Post by aligator12 on 2013-01-07
bumpity bump bump bump

---

### Post by Nr90 on 2013-01-14
iOS 5 will probably be just as safe to use on that network as iOS 6. Very little malware will target specific errors in older versions of iOS.
Many older ipads / iphones do not get an update to iOS 6 and I have not heard stories of them being very prone to viruses issues.

That said, fix your network...;)

---

### Post by haqking on 2013-01-14
> **Nr90 said:**
> **This forum is about Ubuntu mobile, not about the security of your iPhone.**
i

no its not.

This sub-forum is about mobile technology. and the thread is about iPhone vs Ubuntu.

The OP can make the thread about any subject they wish as long as it is inline with the forum topic and CoC

from the sub-forum topic:
> **Mobile Technology Discussions** A place to discuss smartphones, tablets, and anything to do with mobile technology.

---

