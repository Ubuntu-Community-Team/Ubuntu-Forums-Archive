---
title: "DNS Cache and Encryption"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by quequotion on 2013-05-12
Over the past few days I've read a lot of stories about how network-manager, bind9, resolvconf, dnsmasq, and DNSCrypt are *supposed* to work; although relatively few stories about how they could work *together*. Some here in the forums, others in launchpad bug reports, and a whole lot of blogs. Unfortunately, every story is different and most of them are wrong. Not that the information is entirely incorrect, but things aren't working as they should. The primary cause of trouble is network-manager, which has a somewhat obscure configuration in Ubuntu. The other problems are mostly due to uninformed or misinformed assumptions about how resolvconf works and the fact that this setup seriously overcomplicated where it doesn't need to be.

I'm no expert either, but I was abe to piece together how to get cached, encrypted DNS working!

**How to**: Enable DNS Caching and Encryption with dnsmasq and dnscrypt-proxy in 12.04:

1. Install **dnsmasq** (via apt or sofware center  etc) and **dnscrypt-proxy** (only source archives and git availabe)

2. Configure dnsmasq to use something *other than* localhost; I have it listen on **127.0.1.1**. Set it to bind-interfaces, and enable cache-size to your liking, 1000 for me.

3. Configure dnscrypt-proxy to use yet another unique ip, like **127.0.0.2**. Create an init script for it to run at boot and a configuration file.

4. Disable network-manager's dnsmasq plugin. In the future, it could be possible to use this built-in dnsmasq, but at the moment it is hard-coded to be run without caching and cannot be overridden or configured in Ubuntu or its derivatives.

5. Replace the current DNS servers with dnsmasq and dnscrypt-proxy (in that order). This step is a little mysterious because none of the recommended methods consistently work. The only *reliable* way I could find was to add them to resolvconf's **head** config file.

6. Restart network-manager, dnsmasq, and dnscrypt-proxy. In fact, just restart everthing. A reboot is not a bad idea.

7. Run some tests / enjoy your faster and more secure DNS queries. Everything should work; if it does not, carefully retrace your steps and reverse the process.

Detailed guide with code in the following post >>
[B]
::EDIT::[/B]
[s]As jdthood has pointed out, the "new way" of handling DNS is better implemented in 12.10.[/s] [B]
::EDIT::[/B] No it isn't. Still calling dnsmasq with hard-coded overrides there. So now we have a theoretical configuration for a future version of Ubuntu: Using the built-in dnsmasq with dnscrypt-proxy should be simple, but it is going to require the reconfiguration and repackaging of dnsmasq-base *in Debian*.The good news is that these changes *will* get imported into a future version of Ubuntu :) but maybe it takes a while eh? Not too long really.

---

### Post by quequotion on 2013-05-13
**Install dnsmasq**: [**1a**]```
apt-get install dnsmasq
```

**Get dnscrypt-proxy's source, compile, and install**: 
Download an archive from [http://download.dnscrypt.org/dnscrypt-proxy/](http://download.dnscrypt.org/dnscrypt-proxy/) or clone the git repo at [https://github.com/opendns/dnscrypt-proxy](https://github.com/opendns/dnscrypt-proxy)
Extract the source to a folder like ~/Downloads/dnscrypt-proxy/
Install it the old fashioned way:```
./autogen.sh
./configure
make
sudo make install
```Alternatively, use [fpm]("http://www.semicomplete.com/blog/tags/deb") to build a deb package (I haven't tried this yet).
[B]
Configure dnsmasq[/B]:
Edit the configuration file, uncomment and set: "listen-address=127.0.1.1", "bind-interfaces", "cache-size=1000" [**1b**] [**2**]
/etc/dnsmasq:```
# Configuration file for dnsmasq.
#
# Format is one option per line, legal options are the same
# as the long options legal on the command line. See
# "/usr/sbin/dnsmasq --help" or "man 8 dnsmasq" for details.

# The following two options make you a better netizen, since they
# tell dnsmasq to filter out queries which the public DNS cannot
# answer, and which load the servers (especially the root servers)
# unnecessarily. If you have a dial-on-demand link they also stop
# these requests from bringing up the link unnecessarily.

# Never forward plain names (without a dot or domain part)
#domain-needed
# Never forward addresses in the non-routed address spaces.
#bogus-priv


# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
# Note that (amongst other things) this blocks all SRV requests,
# so don't use it if you use eg Kerberos, SIP, XMMP or Google-talk.
# This option only affects forwarding, SRV records originating for
# dnsmasq (via srv-host= lines) are not suppressed by it.
#filterwin2k

# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
#resolv-file=

# By  default,  dnsmasq  will  send queries to any of the upstream
# servers it knows about and tries to favour servers to are  known
# to  be  up.  Uncommenting this forces dnsmasq to try each query
# with  each  server  strictly  in  the  order  they   appear   in
# /etc/resolv.conf
#strict-order

# If you don't want dnsmasq to read /etc/resolv.conf or any other
# file, getting its servers from this file instead (see below), then
# uncomment this.
#no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
#no-poll

# Add other name servers here, with domain specs if they are for
# non-public domains.
#server=/localnet/192.168.0.1

# Example of routing PTR queries to nameservers: this will send all
# address->name queries for 192.168.3/24 to nameserver 10.1.2.3
#server=/3.168.192.in-addr.arpa/10.1.2.3

# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/

# Add domains which you want to force to an IP address here.
# The example below send any host in double-click.net to a local
# web-server.
#address=/double-click.net/127.0.0.1

# --address (and --server) work with IPv6 addresses too.
#address=/www.thekelleys.org.uk/fe80::20d:60ff:fe36:f83

# You can control how dnsmasq talks to a server: this forces
# queries to 10.1.2.3 to be routed via eth1
# server=10.1.2.3@eth1

# and this sets the source (ie local) address used to talk to
# 10.1.2.3 to 192.168.1.1 port 55 (there must be a interface with that
# IP on the machine, obviously).
# server=10.1.2.3@192.168.1.1#55

# If you want dnsmasq to change uid and gid to something other
# than the default, edit the following lines.
#user=
#group=

# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
#interface=
# Or you can specify which interface _not_ to listen on
#except-interface=
# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
listen-address=127.0.1.1
# If you want dnsmasq to provide only DNS service on an interface,
# configure it as shown above, and then use the following line to
# disable DHCP and TFTP on it.
#no-dhcp-interface=

# On systems which support it, dnsmasq binds the wildcard address,
# even when it is listening on only some interfaces. It then discards
# requests that it shouldn't reply to. This has the advantage of
# working even when interfaces come and go and change address. If you
# want dnsmasq to really bind only the interfaces it is listening on,
# uncomment this option. About the only time you may need this is when
# running another nameserver on the same machine.
bind-interfaces

# If you don't want dnsmasq to read /etc/hosts, uncomment the
# following line.
#no-hosts
# or if you want it to read another file, as well as /etc/hosts, use
# this.
#addn-hosts=/etc/banner_add_hosts

# Set this (and domain: see below) if you want to have a domain
# automatically added to simple names in a hosts-file.
#expand-hosts

# Set the domain for dnsmasq. this is optional, but if it is set, it
# does the following things.
# 1) Allows DHCP hosts to have fully qualified domain names, as long
#     as the domain part matches this setting.
# 2) Sets the "domain" DHCP option thereby potentially setting the
#    domain of all systems configured by DHCP
# 3) Provides the domain part for "expand-hosts"
#domain=thekelleys.org.uk

# Set a different domain for a particular subnet
#domain=wireless.thekelleys.org.uk,192.168.2.0/24

# Same idea, but range rather then subnet
#domain=reserved.thekelleys.org.uk,192.68.3.100,192.168.3.200

# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
#dhcp-range=192.168.0.50,192.168.0.150,12h

# This is an example of a DHCP range where the netmask is given. This
# is needed for networks we reach the dnsmasq DHCP server via a relay
# agent. If you don't know what a DHCP relay agent is, you probably
# don't need to worry about this.
#dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h

# This is an example of a DHCP range which sets a tag, so that
# some DHCP options may be set only for this network.
#dhcp-range=set:red,192.168.0.50,192.168.0.150

# Use this DHCP range only when the tag "green" is set.
#dhcp-range=tag:green,192.168.0.50,192.168.0.150,12h

# Specify a subnet which can't be used for dynamic address allocation,
# is available for hosts with matching --dhcp-host lines. Note that
# dhcp-host declarations will be ignored unless there is a dhcp-range
# of some type for the subnet in question.
# In this case the netmask is implied (it comes from the network
# configuration on the machine running dnsmasq) it is possible to give
# an explicit netmask instead.
#dhcp-range=192.168.0.0,static

# Supply parameters for specified hosts using DHCP. There are lots
# of valid alternatives, so we will give examples of each. Note that
# IP addresses DO NOT have to be in the range given above, they just
# need to be on the same network. The order of the parameters in these
# do not matter, it's permissible to give name, address and MAC in any
# order.

# Always allocate the host with Ethernet address 11:22:33:44:55:66
# The IP address 192.168.0.60
#dhcp-host=11:22:33:44:55:66,192.168.0.60

# Always set the name of the host with hardware address
# 11:22:33:44:55:66 to be "fred"
#dhcp-host=11:22:33:44:55:66,fred

# Always give the host with Ethernet address 11:22:33:44:55:66
# the name fred and IP address 192.168.0.60 and lease time 45 minutes
#dhcp-host=11:22:33:44:55:66,fred,192.168.0.60,45m

# Give a host with Ethernet address 11:22:33:44:55:66 or
# 12:34:56:78:90:12 the IP address 192.168.0.60. Dnsmasq will assume
# that these two Ethernet interfaces will never be in use at the same
# time, and give the IP address to the second, even if it is already
# in use by the first. Useful for laptops with wired and wireless
# addresses.
#dhcp-host=11:22:33:44:55:66,12:34:56:78:90:12,192.168.0.60

# Give the machine which says its name is "bert" IP address
# 192.168.0.70 and an infinite lease
#dhcp-host=bert,192.168.0.70,infinite

# Always give the host with client identifier 01:02:02:04
# the IP address 192.168.0.60
#dhcp-host=id:01:02:02:04,192.168.0.60

# Always give the host with client identifier "marjorie"
# the IP address 192.168.0.60
#dhcp-host=id:marjorie,192.168.0.60

# Enable the address given for "judge" in /etc/hosts
# to be given to a machine presenting the name "judge" when
# it asks for a DHCP lease.
#dhcp-host=judge

# Never offer DHCP service to a machine whose Ethernet
# address is 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,ignore

# Ignore any client-id presented by the machine with Ethernet
# address 11:22:33:44:55:66. This is useful to prevent a machine
# being treated differently when running under different OS's or
# between PXE boot and OS boot.
#dhcp-host=11:22:33:44:55:66,id:*

# Send extra options which are tagged as "red" to
# the machine with Ethernet address 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,set:red

# Send extra options which are tagged as "red" to
# any machine with Ethernet address starting 11:22:33:
#dhcp-host=11:22:33:*:*:*,set:red

# Ignore any clients which are specified in dhcp-host lines
# or /etc/ethers. Equivalent to ISC "deny unknown-clients".
# This relies on the special "known" tag which is set when
# a host is matched.
#dhcp-ignore=tag:!known

# Send extra options which are tagged as "red" to any machine whose
# DHCP vendorclass string includes the substring "Linux"
#dhcp-vendorclass=set:red,Linux

# Send extra options which are tagged as "red" to any machine one
# of whose DHCP userclass strings includes the substring "accounts"
#dhcp-userclass=set:red,accounts

# Send extra options which are tagged as "red" to any machine whose
# MAC address matches the pattern.
#dhcp-mac=set:red,00:60:8C:*:*:*

# If this line is uncommented, dnsmasq will read /etc/ethers and act
# on the ethernet-address/IP pairs found there just as if they had
# been given as --dhcp-host options. Useful if you keep
# MAC-address/host mappings there for other purposes.
#read-ethers

# Send options to hosts which ask for a DHCP lease.
# See RFC 2132 for details of available options.
# Common options can be given to dnsmasq by name:
# run "dnsmasq --help dhcp" to get a list.
# Note that all the common settings, such as netmask and
# broadcast address, DNS server and default route, are given
# sane defaults by dnsmasq. You very likely will not need
# any dhcp-options. If you use Windows clients and Samba, there
# are some options which are recommended, they are detailed at the
# end of this section.

# Override the default route supplied by dnsmasq, which assumes the
# router is the same machine as the one running dnsmasq.
#dhcp-option=3,1.2.3.4

# Do the same thing, but using the option name
#dhcp-option=option:router,1.2.3.4

# Override the default route supplied by dnsmasq and send no default
# route at all. Note that this only works for the options sent by
# default (1, 3, 6, 12, 28) the same line will send a zero-length option
# for all other option numbers.
#dhcp-option=3

# Set the NTP time server addresses to 192.168.0.4 and 10.10.0.5
#dhcp-option=option:ntp-server,192.168.0.4,10.10.0.5

# Set the NTP time server address to be the same machine as
# is running dnsmasq
#dhcp-option=42,0.0.0.0

# Set the NIS domain name to "welly"
#dhcp-option=40,welly

# Set the default time-to-live to 50
#dhcp-option=23,50

# Set the "all subnets are local" flag
#dhcp-option=27,1

# Send the etherboot magic flag and then etherboot options (a string).
#dhcp-option=128,e4:45:74:68:00:00
#dhcp-option=129,NIC=eepro100

# Specify an option which will only be sent to the "red" network
# (see dhcp-range for the declaration of the "red" network)
# Note that the tag: part must precede the option: part.
#dhcp-option = tag:red, option:ntp-server, 192.168.1.1

# The following DHCP options set up dnsmasq in the same way as is specified
# for the ISC dhcpcd in
# http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt
# adapted for a typical dnsmasq installation where the host running
# dnsmasq is also the host running samba.
# you may want to uncomment some or all of them if you use
# Windows clients and Samba.
#dhcp-option=19,0           # option ip-forwarding off
#dhcp-option=44,0.0.0.0     # set netbios-over-TCP/IP nameserver(s) aka WINS server(s)
#dhcp-option=45,0.0.0.0     # netbios datagram distribution server
#dhcp-option=46,8           # netbios node type

# Send RFC-3397 DNS domain search DHCP option. WARNING: Your DHCP client
# probably doesn't support this......
#dhcp-option=option:domain-search,eng.apple.com,marketing.apple.com

# Send RFC-3442 classless static routes (note the netmask encoding)
#dhcp-option=121,192.168.1.0/24,1.2.3.4,10.0.0.0/8,5.6.7.8

# Send vendor-class specific options encapsulated in DHCP option 43.
# The meaning of the options is defined by the vendor-class so
# options are sent only when the client supplied vendor class
# matches the class given here. (A substring match is OK, so "MSFT"
# matches "MSFT" and "MSFT 5.0"). This example sets the
# mtftp address to 0.0.0.0 for PXEClients.
#dhcp-option=vendor:PXEClient,1,0.0.0.0

# Send microsoft-specific option to tell windows to release the DHCP lease
# when it shuts down. Note the "i" flag, to tell dnsmasq to send the
# value as a four-byte integer - that's what microsoft wants. See
# http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true
#dhcp-option=vendor:MSFT,2,1i

# Send the Encapsulated-vendor-class ID needed by some configurations of
# Etherboot to allow is to recognise the DHCP server.
#dhcp-option=vendor:Etherboot,60,"Etherboot"

# Send options to PXELinux. Note that we need to send the options even
# though they don't appear in the parameter request list, so we need
# to use dhcp-option-force here.
# See http://syslinux.zytor.com/pxe.php#special for details.
# Magic number - needed before anything else is recognised
#dhcp-option-force=208,f1:00:74:7e
# Configuration file name
#dhcp-option-force=209,configs/common
# Path prefix
#dhcp-option-force=210,/tftpboot/pxelinux/files/
# Reboot time. (Note 'i' to send 32-bit value)
#dhcp-option-force=211,30i

# Set the boot filename for netboot/PXE. You will only need
# this is you want to boot machines over the network and you will need
# a TFTP server; either dnsmasq's built in TFTP server or an
# external one. (See below for how to enable the TFTP server.)
#dhcp-boot=pxelinux.0

# The same as above, but use custom tftp-server instead machine running dnsmasq
#dhcp-boot=pxelinux,server.name,192.168.1.100

# Boot for Etherboot gPXE. The idea is to send two different
# filenames, the first loads gPXE, and the second tells gPXE what to
# load. The dhcp-match sets the gpxe tag for requests from gPXE.
#dhcp-match=set:gpxe,175 # gPXE sends a 175 option.
#dhcp-boot=tag:!gpxe,undionly.kpxe
#dhcp-boot=mybootimage

# Encapsulated options for Etherboot gPXE. All the options are
# encapsulated within option 175
#dhcp-option=encap:175, 1, 5b         # priority code
#dhcp-option=encap:175, 176, 1b       # no-proxydhcp
#dhcp-option=encap:175, 177, string   # bus-id
#dhcp-option=encap:175, 189, 1b       # BIOS drive code
#dhcp-option=encap:175, 190, user     # iSCSI username
#dhcp-option=encap:175, 191, pass     # iSCSI password

# Test for the architecture of a netboot client. PXE clients are
# supposed to send their architecture as option 93. (See RFC 4578)
#dhcp-match=peecees, option:client-arch, 0 #x86-32
#dhcp-match=itanics, option:client-arch, 2 #IA64
#dhcp-match=hammers, option:client-arch, 6 #x86-64
#dhcp-match=mactels, option:client-arch, 7 #EFI x86-64

# Do real PXE, rather than just booting a single file, this is an
# alternative to dhcp-boot.
#pxe-prompt="What system shall I netboot?"
# or with timeout before first available action is taken:
#pxe-prompt="Press F8 for menu.", 60

# Available boot services. for PXE.
#pxe-service=x86PC, "Boot from local disk"

# Loads <tftp-root>/pxelinux.0 from dnsmasq TFTP server.
#pxe-service=x86PC, "Install Linux", pxelinux

# Loads <tftp-root>/pxelinux.0 from TFTP server at 1.2.3.4.
# Beware this fails on old PXE ROMS.
#pxe-service=x86PC, "Install Linux", pxelinux, 1.2.3.4

# Use bootserver on network, found my multicast or broadcast.
#pxe-service=x86PC, "Install windows from RIS server", 1

# Use bootserver at a known IP address.
#pxe-service=x86PC, "Install windows from RIS server", 1, 1.2.3.4

# If you have multicast-FTP available,
# information for that can be passed in a similar way using options 1
# to 5. See page 19 of
# http://download.intel.com/design/archives/wfm/downloads/pxespec.pdf


# Enable dnsmasq's built-in TFTP server
#enable-tftp

# Set the root directory for files available via FTP.
#tftp-root=/var/ftpd

# Make the TFTP server more secure: with this set, only files owned by
# the user dnsmasq is running as will be send over the net.
#tftp-secure

# This option stops dnsmasq from negotiating a larger blocksize for TFTP
# transfers. It will slow things down, but may rescue some broken TFTP
# clients.
#tftp-no-blocksize

# Set the boot file name only when the "red" tag is set.
#dhcp-boot=net:red,pxelinux.red-net

# An example of dhcp-boot with an external TFTP server: the name and IP
# address of the server are given after the filename.
# Can fail with old PXE ROMS. Overridden by --pxe-service.
#dhcp-boot=/var/ftpd/pxelinux.0,boothost,192.168.0.3

# If there are multiple external tftp servers having a same name
# (using /etc/hosts) then that name can be specified as the
# tftp_servername (the third option to dhcp-boot) and in that
# case dnsmasq resolves this name and returns the resultant IP
# addresses in round robin fasion. This facility can be used to
# load balance the tftp load among a set of servers.
#dhcp-boot=/var/ftpd/pxelinux.0,boothost,tftp_server_name

# Set the limit on DHCP leases, the default is 150
#dhcp-lease-max=150

# The DHCP server needs somewhere on disk to keep its lease database.
# This defaults to a sane location, but if you want to change it, use
# the line below.
#dhcp-leasefile=/var/lib/misc/dnsmasq.leases

# Set the DHCP server to authoritative mode. In this mode it will barge in
# and take over the lease for any client which broadcasts on the network,
# whether it has a record of the lease or not. This avoids long timeouts
# when a machine wakes up on a new network. DO NOT enable this if there's
# the slightest chance that you might end up accidentally configuring a DHCP
# server for your campus/company accidentally. The ISC server uses
# the same option, and this URL provides more information:
# http://www.isc.org/files/auth.html
#dhcp-authoritative

# Run an executable when a DHCP lease is created or destroyed.
# The arguments sent to the script are "add" or "del",
# then the MAC address, the IP address and finally the hostname
# if there is one.
#dhcp-script=/bin/echo

# Set the cachesize here.
cache-size=1000

# If you want to disable negative caching, uncomment this.
#no-negcache

# Normally responses which come form /etc/hosts and the DHCP lease
# file have Time-To-Live set as zero, which conventionally means
# do not cache further. If you are happy to trade lower load on the
# server for potentially stale date, you can set a time-to-live (in
# seconds) here.
#local-ttl=

# If you want dnsmasq to detect attempts by Verisign to send queries
# to unregistered .com and .net hosts to its sitefinder service and
# have dnsmasq instead return the correct NXDOMAIN response, uncomment
# this line. You can add similar lines to do the same for other
# registries which have implemented wildcard A records.
#bogus-nxdomain=64.94.110.11

# If you want to fix up DNS results from upstream servers, use the
# alias option. This only works for IPv4.
# This alias makes a result of 1.2.3.4 appear as 5.6.7.8
#alias=1.2.3.4,5.6.7.8
# and this maps 1.2.3.x to 5.6.7.x
#alias=1.2.3.0,5.6.7.0,255.255.255.0
# and this maps 192.168.0.10->192.168.0.40 to 10.0.0.10->10.0.0.40
#alias=192.168.0.10-192.168.0.40,10.0.0.0,255.255.255.0

# Change these lines if you want dnsmasq to serve MX records.

# Return an MX record named "maildomain.com" with target
# servermachine.com and preference 50
#mx-host=maildomain.com,servermachine.com,50

# Set the default target for MX records created using the localmx option.
#mx-target=servermachine.com

# Return an MX record pointing to the mx-target for all local
# machines.
#localmx

# Return an MX record pointing to itself for all local machines.
#selfmx

# Change the following lines if you want dnsmasq to serve SRV
# records.  These are useful if you want to serve ldap requests for
# Active Directory and other windows-originated DNS requests.
# See RFC 2782.
# You may add multiple srv-host lines.
# The fields are <name>,<target>,<port>,<priority>,<weight>
# If the domain part if missing from the name (so that is just has the
# service and protocol sections) then the domain given by the domain=
# config option is used. (Note that expand-hosts does not need to be
# set for this to work.)

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 389
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 389 (using domain=)
#domain=example.com
#srv-host=_ldap._tcp,ldapserver.example.com,389

# Two SRV records for LDAP, each with different priorities
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,1
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,2

# A SRV record indicating that there is no LDAP server for the domain
# example.com
#srv-host=_ldap._tcp.example.com

# The following line shows how to make dnsmasq serve an arbitrary PTR
# record. This is useful for DNS-SD. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for PTR records.)
#ptr-record=_http._tcp.dns-sd-services,"New Employee Page._http._tcp.dns-sd-services"

# Change the following lines to enable dnsmasq to serve TXT records.
# These are used for things like SPF and zeroconf. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for TXT records.)

#Example SPF.
#txt-record=example.com,"v=spf1 a -all"

#Example zeroconf
#txt-record=_http._tcp.example.com,name=value,paper=A4

# Provide an alias for a "local" DNS name. Note that this _only_ works
# for targets which are names from DHCP or /etc/hosts. Give host
# "bert" another name, bertrand
#cname=bertand,bert

# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
#log-queries

# Log lots of extra information about DHCP transactions.
#log-dhcp

# Include a another lot of configuration options.
#conf-file=/etc/dnsmasq.more.conf
#conf-dir=/etc/dnsmasq.d
```There's one line to change in dnsmasq's init script:
/etc/init.d/dnsmasq, line 123~138:```
start_resolvconf()
{
# If interface "lo" is explicitly disabled in /etc/default/dnsmasq
# Then dnsmasq won't be providing local DNS, so don't add it to
# the resolvconf server set.
    for interface in $DNSMASQ_EXCEPT
    do
        [ $interface = lo ] && return
    done

        if [ -x /sbin/resolvconf ] ; then
        echo "nameserver 127.0.1.1" | /sbin/resolvconf -a lo.$NAME #This should be extracted from config or set up by communicating directly with resolvconf: Launchpad Bug 1042275
    fi
    return 0
}
```
[B]
Configure dnscrypt-proxy[/B]:
Create an init-script to run dnscrypt-proxy at boot:
/etc/init.d/dnscrypt-proxy:```
#!/bin/sh
### BEGIN INIT INFO
# Provides:       dnscrypt-proxy
# Required-Start: $network $remote_fs $syslog
# Required-Stop:  $network $remote_fs $syslog
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Description:    OpenDNS Encrypting DNS Proxy
### END INIT INFO

set +e   # Don't exit on error status

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/local/sbin/dnscrypt-proxy
NAME=dnscrypt-proxy
DESC="OpenDNS Encrypting DNS Proxy"

# Let's have a configuration file!
ENABLED=1
if [ -r /etc/default/$NAME ]; then
    . /etc/default/$NAME
fi

# Get the system locale, so that messages are in the correct language, and the 
# charset for IDN is correct
if [ -r /etc/default/locale ]; then
        . /etc/default/locale
        export LANG
fi

test -x $DAEMON || exit 0

# Provide skeleton LSB log functions for backports which don't have LSB functions.
if [ -f /lib/lsb/init-functions ]; then
         . /lib/lsb/init-functions
else
         log_warning_msg () {
            echo "${@}."
         }

         log_success_msg () {
            echo "${@}."
         }

         log_daemon_msg () {
            echo -n "${1}: $2"
         }

     log_end_msg () {
            if [ $1 -eq 0 ]; then
              echo "."
            elif [ $1 -eq 255 ]; then
              /bin/echo -e " (warning)."
            else
              /bin/echo -e " failed!"
            fi
         }
fi

#if [ ! "$DNSCRYPT_USER" ]; then #dnscrypt does not add a user on installation
#   DNSCRYPT_USER="dnscrypt"
#fi

start()
{
        # Return
    #   0 if daemon has been started
    #   1 if daemon was already running
    #   2 if daemon could not be started

        # /var/run may be volatile, so we need to ensure that
        # /var/run/dnscrypt-proxy exists here as well as in postinst
        if [ ! -d /var/run/$NAME ]; then
           mkdir /var/run/$NAME || return 2
           #chown $NAME:nogroup /var/run/$NAME || return 2
        fi

#    start-stop-daemon --start --quiet --pidfile /var/run/$NAME/$NAME.pid --exec $DAEMON --test > /dev/null || return 1
    start-stop-daemon --start --quiet --pidfile /var/run/$NAME/$NAME.pid --exec $DAEMON -- \
        -p /var/run/$NAME/$NAME.pid \
        ${DNSCRYPT_USER:+ -u $DNSCRYPT_USER} \
        ${LOCAL_ADDR:+ -a $LOCAL_ADDR} \
        ${DNSCRYPT_OPTS:+ $DNSCRYPT_OPTS} \
        || return 2
}

stop()
{
    # Return
    #   0 if daemon has been stopped
    #   1 if daemon was already stopped
    #   2 if daemon could not be stopped
    #   other if a failure occurred
    start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile /var/run/$NAME/$NAME.pid --name $NAME
    RETVAL="$?"
    [ "$RETVAL" = 2 ] && return 2
    return "$RETVAL"
}

#status() #dnscrypt-proxy doesn't have a built-in sanity check :(
#{
#    # Return
#    #   0 if daemon is running
#    #   1 if daemon is dead and pid file exists
#    #   3 if daemon is not running
#    #   4 if daemon status is unknown
#    start-stop-daemon --start --quiet --pidfile /var/run/$NAME/$NAME.pid --exec $DAEMON --test > /dev/null
#    case "$?" in
#        0) [ -e "/var/run/$NAME/$NAME.pid" ] && return 1 ; return 3 ;;
#        1) return 0 ;;
#        *) return 4 ;;
#    esac
#}

case "$1" in
  start)
    test "$ENABLED" != "0" || exit 0
    log_daemon_msg "Starting $DESC" "$NAME"
    start
    case "$?" in
        0)
            log_end_msg 0
            exit 0
            ;;
        1)
            log_success_msg "(already running)"
            exit 0
            ;;
        *)
            log_end_msg 1
            exit 1
            ;;
    esac
    ;;
  stop)
    if [ "$ENABLED" != "0" ]; then
             log_daemon_msg "Stopping $DESC" "$NAME"
    fi
    stop
        RETVAL="$?"
    if [ "$ENABLED" = "0" ]; then
        case "$RETVAL" in
           0) log_daemon_msg "Stopping $DESC" "$NAME"; log_end_msg 0 ;;
            esac 
        exit 0
    fi
    case "$RETVAL" in
        0) log_end_msg 0 ; exit 0 ;;
        1) log_warning_msg "(not running)" ; exit 0 ;;
        *) log_end_msg 1; exit 1 ;;
    esac
    ;;
  restart|force-reload)
    test "$ENABLED" != "0" || exit 1
#    $DAEMON --test ${CONFIG_DIR:+ -7 $CONFIG_DIR} ${DNSCRYPT_OPTS:+ $DNSCRYPT_OPTS} >/dev/null 2>&1
#    if [ $? -ne 0 ]; then
#        NAME="configuration syntax check"
#        RETVAL="2"
#    else   
        stop
        RETVAL="$?"
#        fi
    log_daemon_msg "Restarting $DESC" "$NAME"
    case "$RETVAL" in
        0|1)
                sleep 2
            start
            case "$?" in
                0)
                    log_end_msg 0
                    exit 0
                    ;;
                    *)
                    log_end_msg 1
                    exit 1
                    ;;
            esac
            ;;
        *)
            log_end_msg 1
            exit 1
            ;;
    esac
    ;;
  status)
#    log_daemon_msg "Checking $DESC" "$NAME"
#    status
#    case "$?" in
#        0) log_success_msg "(running)" ; exit 0 ;;
#        1) log_success_msg "(dead, pid file exists)" ; exit 1 ;;
#        3) log_success_msg "(not running)" ; exit 3 ;;
#        *) log_success_msg "(unknown)" ; exit 4 ;;
#    esac
    echo "$NAME doesn't have a built-in sanity check :(" >&2
    ;;
  *)
    echo "Usage: /etc/init.d/$NAME {start|stop|restart|force-reload|status}" >&2
    exit 3
    ;;
esac

exit 0
```Make it executable:```
sudo chmod +x /etc/init.d/dnscrypt-proxy
```Install it:```
sudo update-rc.d dnscrypt-proxy defaults
```Create a configuration file for the dnscrypt-proxy daemon:
/etc/default/dnscrypt-proxy:```
# NB. If systemd is installed and starting dnscrypt-proxy, this file is IGNORED.

#Also specified in init script, override here?
#DNSCRYPT_USER="dnscrypt"
#Use an IP that isn't in use by anything else, especially bind9.
#Port 53 is default and need not be specified, but just in case...
LOCAL_ADDR="127.0.0.2:53"
#Specify any other options on this line. See `man dnscrypt-proxy`.
DNSCRYPT_OPTS="--daemonize"
# Whether or not to run the dnscrypt-proxy daemon; set to 0 to disable.
#Also specified in init script, override here?
#ENABLED=1
```

**Configure network-manager**: [**1c**]
Edit the configuration file, comment out "dns=dnsmasq":
/etc/NetworkManager/NetworkManager.conf:```

[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

no-auto-default=BC:5F:F4:22:35:07,02:26:08:88:7F:EE,

[ifupdown]
managed=true
```
[B]
Add dnsmasq and dnscrypt as nameservers to resolv.conf[/B]: [**2**][**3**]
Edit the head configuration file, don't worry about the warning, and add two lines:
/etc/resolvconf/resolv.conf.d/head:```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1 #dnsmasq
nameserver 127.0.0.2 #dnscrypt-proxy
```
[B]
Restart everything[/B]:
```
sudo /etc/init.d/dnscrypt restart
sudo /etc/init.d/dnsmasq restart
sudo /etc/init.d/network-manager restart
```Sometimes nm-applet (the network icon) crashes when restarting network-manager, but the daemon is still working. This is not a bad place for a reboot.


Here's a great place to test DNS settings:
[https://www.grc.com/dns/dns.htm](https://www.grc.com/dns/dns.htm)


I had a lot of trouble getting this working because I had to sort through quite a few misinformed, outdated, and incorrect guides about DNS in Ubuntu. It looks like 12.04 is in transition to a new way of doing things that will be in future versions of Ubuntu, which has caused a lot of confusion. Things aren't working like they used to, nor do they work how they "should" compared to other distributions, nor is Ubuntu's "new way" completely implemented. The situation can be very frustrating.

Here are some ways to specify DNS servers that *don't work* in Ubuntu:


[LIST]
[*]Modify /etc/network/interfaces:
[LIST]
[*]This is for the specification of *static* network interfaces, which is complicated and probably not necessary or practical. Actually this might work, but it's far from the optimal means. 
[/LIST]
  
[*]Modify either /etc/dhcp/dhclient.conf [s]or /etc/dhcp3/dhclient.conf[/s]:
[LIST]
[*][s]First of all, would the real dhclient.conf please stand up? Second,[/s] The settings here *will be ignored* when resolv.conf is auto-magically generated. This is [s]probably[/s] because "dns=dnsmasq" is commented out in NetworkManager's configuration. 
[/LIST]
  
[*]Modify /etc/resolv.conf:
[LIST]
[*]It is a "good" idea to have this file auto-magically overwritten *every time networking restarts* (at boot, etc) and a "bad" idea to let users handle this by themselves. You can make temporary changes for testing purposes. 
[/LIST]
  
[*]Use Network Manager's "Edit Connections" feature (nm-connection-editor):
[LIST]
[*]This is the "right way" that's supposed to be user-friendly and convenient; *also ignored* when resolv.conf is auto-magically generated, [s]possibly[/s] for the same reason as the settings in dhclient.conf are ignored (see above). 
[/LIST]
  
[*]Add /etc/NetworkManager/dnsmasq.d/cache and specify a configuration for the built-in dnsmasq [**1d**]
[LIST]
[*] Found this in the Archlinux wiki; but it doesn't work for 12.04. The configuration will be ignored because network-manager runs dnsmasq with all the options specified on the command line (like --cache-size=0 and --no-hosts) which cannot be overridden. 
[/LIST]
      
[/LIST]

**::EDIT:: ****::AGAIN::**

Theoretical configuration:
[**1a**] Probably not necessary in a future repackaging of dnsmasq-base.
[**1b**] In a repackaged dnsmasq-base it may or may not be necessary to create a new file at /etc/NetworkManager/dnsmasq.d/cache and add these configuration options to it.
[**1c**] Probably not necessary in a furture repackaging of dnsmasq-base.
[**1d**] This may be available in a furture repackging of dnsmasq-base.

[**2**] There is a section of dnsmasq's config file:
/etc/dnsmasq:```
# Add other name servers here, with domain specs if they are for
# non-public domains.
#server=/localnet/192.168.0.1
```It should be possible to add  dnscrypt-proxy here and skip modifying  /etc/resolvconf/resolv.conf.d/head, but it doesn't work for me. Perhaps  it needs a "domain spec"? **#Still don't know abou this. Any ideas?**
[**3**] Maybe it isn't necessary to add dnsmasq to this list?

---

### Post by quequotion on 2013-05-13
The init script and configuration file I use for dnscrypt-proxy are borrowed from dnsmasq and somewhat simplified.

There's room for improvement:
My resolv.conf looks like this:```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1 #dnsmasq
nameserver 127.0.0.2 #dnscrypt-proxy 
nameserver 127.0.1.1
```[s]I don't know where the redundant third line comes from or how to get rid of it. It's not causing any trouble, but it's weird.[/s]
jdthood was able to clear this up: That line should be here and it is the address specified by /etc/init.d/dnsmasq. In fact, if dnsmasq would forward queries to dnscrypt-proxy by itself this would be the only line necessary (no need to edit /etc/resolvconf/resolv.conf.d/head). There is a place to add other name servers in /etc/dnsmasq, but it doesn't work for me. (see [**2**] above)

Also, note the warning, which is the same as in /etc/resolvconf/resolv.conf.d/head: It is in *head* for the purpose of being copied into *resolv.conf*.

---

### Post by jdthood on 2013-05-14
> **quequotion said:**
> 4. Disable network-manager's dnsmasq plugin. In the future, it could be possible to use this built-in dnsmasq, but at the moment it is hard-coded to be run without caching and cannot be overridden or configured in Ubuntu or its derivatives.

In Ubuntu 12.10 or later it can be configured by adding a file to /etc/NetworkManager/dnsmasq.d/.

---

### Post by jdthood on 2013-05-14
> **quequotion said:**
> 
I had a lot of trouble getting this working because I had to sort through quite a few misinformed, outdated, and incorrect guides about DNS in Ubuntu. It looks like 12.04 is in transition to a new way of doing things that will be in future versions of Ubuntu, which has caused a lot of confusion.

You are certainly correct that there is a lot of misinformation out there.

A good introduction is Stéphane Graber's blog post: [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

> **quequotion said:**
> 
Things aren't working like they used to, nor do they work how they "should" compared to other distributions, nor is Ubuntu's "new way" completely implemented.

I am not sure what you mean by "not completely implemented". Can you explain?

> **quequotion said:**
> 
Here are some ways to specify DNS servers that *don't work* in Ubuntu:
[LIST]
[*]Modify /etc/network/interfaces:
[LIST]
[*]This is for the specification of *static* network interfaces, which is complicated and probably not necessary or practical. Actually this might work, but it's far from the optimal means.
[/LIST]
[/LIST]


The file /etc/network/interfaces is the configuration file for ifup. Ubuntu Server uses ifup rather than NetworkManager.

You are right that on Ubuntu Desktop you shouldn't modify /etc/network/interfaces. (Although NetworkManager can be made to emulate ifup and read /etc/network/interfaces, this is not a good idea. NetworkManager and ifup should be treated as mutually exclusive alternatives (with the single exception that even on Ubuntu Desktop, ifup is used to configure the "lo" interface)).

> **quequotion said:**
> 
[LIST]
[*]Modify either /etc/dhcp/dhclient.conf or /etc/dhcp3/dhclient.conf:
[LIST]
[*]First of all, would the real dhclient.conf please stand up? Second, the settings here *will be ignored* when resolv.conf is auto-magically generated. This may be because "dns=dnsmasq" is commented out in the configuration--which is said to stop automagic generation of resolv.conf altogether (it doesn't).
[/LIST]
[/LIST]


Formerly /etc/dhcp3/ was used, now /etc/dhcp/.

The setting "dns=dnsmasq" has absolutely nothing to do with dhclient.

The setting "dns=dnsmasq" or its absence does not start or stop automagic generation of resolv.conf.

(What "dns=dnsmasq" does control is whether or not NetworkManager starts a slave dnsmasq instance to act as a local forwarding nameserver. If this feature is enabled then resolv.conf always contains "nameserver 127.0.0.1" in Ubuntu 12.04, "nameserver 127.0.1.1" in Ubuntu 12.10 or later; if not then resolv.conf contains upstream nameserver addresses.)

> **quequotion said:**
> 
[LIST]
[*]Use Network Manager's "Edit Connections" feature (nm-connection-editor):
[LIST]
[*]This is the "right way" that's supposed to be user-friendly and convenient; *also ignored* when resolv.conf is auto-magically generated, possibly for the same reason as the settings in dhclient.conf are ignored.
[/LIST]
[/LIST]


I think you are confused here. Adding addresses to the "DNS servers" field on either the IPv4 or IPv6 Settings tab _is_ effective.

If "dns=dnsmasq" is active then adding addresses to "DNS servers" will have no effect on resolv.conf because resolv.conf continues to list one and only one nameserver at 127.0.0.1 (or 127.0.1.1 in Ubuntu 12.10 or later). But NetworkManager _does_ give the addresses to its slave dnsmasq instance to use as forwarding addresses.  If "dns=dnsmasq" is inactive then the addresses from the "DNS servers" fields do show up in resolv.conf.

> **quequotion said:**
> 
[LIST]
[*]Add /etc/NetworkManager/dnsmasq.d/cache and specify a configuration for the built-in dnsmasq
[LIST]
[*] Found this in the Archlinux wiki; but it doesn't work for Ubuntu. The configuration will be ignored because network-manager runs dnsmasq with all the options specified on the command line (like --cache-size=0 and --no-hosts) which cannot be overridden.
[/LIST]
[/LIST]

It works in Ubuntu 12.10 or later, not in Ubuntu 12.04.  You _can_ cause the NetworkManager-controlled dnsmasq to have a nonzero cache size by adding a file to /etc/NetworkManager/dnsmasq.d/. I have tested this in the past and it worked.

---

### Post by jdthood on 2013-05-14
> **quequotion said:**
> 
My resolv.conf looks like this:```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1 #dnsmasq
nameserver 127.0.0.2 #dnscrypt-proxy 
nameserver 127.0.1.1
```I don't know where the redundant third line comes from or how to get rid of it.


The third line comes from your command 
```
echo "nameserver 127.0.1.1" | /sbin/resolvconf -a lo.$NAME #In fact, what does this actually do?
```
in /etc/init.d/dnsmasq.

Because the glibc resolver tries one nameserver at a time, with a five-second timeout between attempts, it should suffice to have just the "nameserver 127.0.1.1" line. That is, you could omit the lines that you added to /etc/resolvconf/resolv.conf.d/head.

If you can't omit those lines then I assume it's because dnsmasq is learning from there that it can use 127.0.0.2 as a forwarding address. The correct way of configuring this is for dnscrypt-proxy's initscript to do
```

    echo "nameserver 127.0.0.2" | resolvconf -a lo.dnscrypt-proxy

```
when it starts and
```

    resolvconf -d lo.dnscrypt-proxy

```
when it stops.

If that doesn't work, let me know and we'll start debugging.

---

### Post by quequotion on 2013-05-15
> **jdthood said:**
> In Ubuntu 12.10 or later it can be configured by adding a file to /etc/NetworkManager/dnsmasq.d/. That's good to know, and this is part of what I meant by "not fully implemented yet" (see below). For reasons unrelated to this thread, and mostly LTS, I am sticking with 12.04. Can you re-verify that creating config files in /etc/NetworkManager/dnsmasq.d/ actually works in 12.10? If it does, then it would make it much easier for dnsmasq and dnscrypt to work together by one less software package to install by hand and several less steps of configuration.

> **jdthood said:**
> You are certainly correct that there is a lot of misinformation out there.

A good introduction is Stéphane Graber's blog post: [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

I am not sure what you mean by "not completely implemented". Can you explain?  As said above, the implementation of configuration files for the built-in dnsmasq hasn't been backported to 12.04 where the dnsmasq run by network-manager is not very useful: [it ignores /ect/hosts]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/993298") and [caching is disabled]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/903854"). At some point after I installed Ubuntu (with a fresh install), dhcp has been transitioned from dhcp3-* to icp-dhcp-* leaving obsolete configuration files in /etc/dhcp3/ which frequently appear in equally obsolete guides. Not even knowing it had happened, I found myself very confused at having two complete sets of configuration files for dhcp and different guides telling me to make changes to either or *both* of them.

If the /etc/dhcp3/ config files are needed, they should be symlinks to /etc/dhcp/ and if not, they should be purged. It is important that these files not be there if they aren't necessary, as this will help people to notice that the guide they are following is obsolete when the config files it recommends do not exist. See below for more about that. [B]#note to self: make a bug report
[/B]
> The file /etc/network/interfaces is the configuration file for ifup. Ubuntu Server uses ifup rather than NetworkManager.

You are right that on Ubuntu Desktop you shouldn't modify /etc/network/interfaces. (Although NetworkManager can be made to emulate ifup and read /etc/network/interfaces, this is not a good idea. NetworkManager and ifup should be treated as mutually exclusive alternatives (with the single exception that even on Ubuntu Desktop, ifup is used to configure the "lo" interface)). NetworkManager in 12.04 comes with the ifup plugin enabled by default. The two are not treated as either mutually exclusive or alternatives, but a *hierarchy* of configuration. NetworkManager basically takes over ifup's job using ifup's configuration files and then overriding them with it's own configuration.

> Formerly /etc/dhcp3/ was used, now /etc/dhcp/.This is also nice to know. Could you track down when and why this happened? Knowing this would help to discern which guides out there in the internet are obsolete.

> The setting "dns=dnsmasq" has absolutely nothing to do with dhclient.

The setting "dns=dnsmasq" or its absence does not start or stop automagic generation of resolv.conf.

(What "dns=dnsmasq" does control is whether or not NetworkManager starts a slave dnsmasq instance to act as a local forwarding nameserver. If this feature is enabled then resolv.conf always contains "nameserver 127.0.1.1"; if not then resolv.conf contains upstream nameserver addresses.) Actually it will be 127.0.0.1 in 12.04, since there are no configurable options for the built-in dnsmasq. I'm curious what other options are available for "dns=?????" and if there is a default enabled when this line gets commented out. You're right that it has nothing to do with the auto-magic generation of resolv.conf, although I did read a misinformed guide to the contrary.

This is one of the steps that would not be necessary if configuration files in /etc/NetworkManager/dnsmasq.d/ were implemented. The reason for disabling this is to set up a separate dnsmasq with a user-specified configuration (ie, to enable cache or respect for /etc/hosts). If this were not necessary, users would not have to install a new dnsmasq package, edit the lengthy /etc/dnsmasq, or modify /etc/init.d/dnsmasq; they could simply add the options they want to an empty file (a reduction of 2.5 steps to my guide). 

> I think you are confused here. Adding addresses to the "DNS servers" field on either the IPv4 or IPv6 Settings tab _is_ effective. No it is not, I assure you. Oddly, the commenting of "dns=dnsmasq" has something to do with this; I agree that it should not, but it does.

> If "dns=dnsmasq" is active then adding addresses to "DNS servers" will have no effect on resolv.conf because resolv.conf continues to list one and only one nameserver at 127.0.0.1 (or 127.0.1.1 in Ubuntu 12.10 or later). But NetworkManager _does_ give the addresses to its slave dnsmasq instance to use as forwarding addresses.  If "dns=dnsmasq" is inactive then the addresses from the "DNS servers" fields do show up in resolv.conf.  In 12.04 this is completely upside down. If "dns=dnsmasq" is set, NetworkManager does add 127.0.0.1 (dnsmasq) as the first in the list, plus adds any servers the user added through nm-connection-editor after it. When it is commented out, NetworkManager cannot be used to add or remove servers from the list in /etc/resolv.conf; again I wonder if there is some alternative default for "dns=?????" in use when this line is commented out.

> It works in Ubuntu 12.10 or later, not in Ubuntu 12.04.  You _can_ cause the NetworkManager-controlled dnsmasq to have a nonzero cache size by adding a file to /etc/NetworkManager/dnsmasq.d/. I have tested this in the past and it worked. That's good news, but I wish this would be backported or SRU'd to the LTS version. The NetworkManager implementation of dnsmasq in 12.04 is nigh-pointless.

> **jdthood said:**
> The third line comes from your command 
```
echo "nameserver 127.0.1.1" | /sbin/resolvconf -a lo.$NAME #In fact, what does this actually do?
```
in /etc/init.d/dnsmasq.  I was curious about this line. You are correct: after setting a different number here and restarting dnsmasq & resolvconf the new number appeared in the list. I think this number should be extracted from dnsmasq's configuration however, and not arbitrarily specified in the init script. If this number is not the same as the number in the configuration file, and users do not specify the correct number in /etc/resolvconf/resolv.conf.d/head then DNS queries will be sent to into a black hole.  **#note to self: make a bug report**

> Because the glibc resolver tries one nameserver at a time, with a five-second timeout between attempts, it should suffice to have just the "nameserver 127.0.1.1" line. That is, you could omit the lines that you added to /etc/resolvconf/resolv.conf.d/head.

If you can't omit those lines then I assume it's because dnsmasq is learning from there that it can use 127.0.0.2 as a forwarding address. The correct way of configuring this is for dnscrypt-proxy's initscript to do
```

    echo "nameserver 127.0.0.2" | resolvconf -a lo.dnscrypt-proxy

```
when it starts and
```

    resolvconf -d lo.dnscrypt-proxy

```
when it stops.

If that doesn't work, let me know and we'll start debugging. That sounds like a good idea; I will give it a shot. This could be added to the init script for dnscrypt in just the same way was the init script for dnsmasq. There was another method of forwarding to dnscrypt-proxy I tried that didn't work: dnsmasq's configuration file includes a line for specifying other servers, but then it never seems to make contact with the specified servers.

---

### Post by quequotion on 2013-05-15
> **jdthood said:**
> ```

    echo "nameserver 127.0.0.2" | resolvconf -a lo.dnscrypt-proxy

```
when it starts and
```

    resolvconf -d lo.dnscrypt-proxy

```
when it stops.

If that doesn't work, let me know and we'll start debugging.

This does not work. 127.0.0.2 will not be added to /etc/resolv.conf and DNS will not resolve. I tried this from the command line as well as by init script; dnscrypt-proxy and dnsmasq both run, but DNS requests never get forwarded to dnscrypt-proxy.

---

### Post by jdthood on 2013-05-17
> **quequotion said:**
> 
This is also nice to know. Could you track down when and why this happened? Knowing this would help to discern which guides out there in the internet are obsolete.

Long ago when Debian contained the "dhcp-client" package (version 2), /etc/dhcp/ was used. When "dhcp3-client" was introduced it used /etc/dhcp3/ so that it could be installed alongside dhcp-client. After dhcp-client was dropped from Debian, dhcp3-client was renamed to "isc-dhcp-client" and stuff was moved from /etc/dhcp3/ to /etc/dhcp/.  So either new, or very old, systems use /etc/dhcp/.

---

### Post by jdthood on 2013-05-17
> **quequotion said:**
> 
In 12.04 this is completely upside down. If "dns=dnsmasq" is set, NetworkManager does add 127.0.0.1 (dnsmasq) as the first in the list, plus adds any servers the user added through nm-connection-editor after it.


This indicates that resolvconf is either absent, or is non-standardly configured on your machine. Because resolvconf normally doesn't include any "nameserver" lines after a "nameserver 127.0.0.1" line. See my next post.

> **quequotion said:**
> 
When it is commented out, NetworkManager cannot be used to add or remove servers from the list in /etc/resolv.conf; again I wonder if there is some alternative default for "dns=?????" in use when this line is commented out.


If /etc/resolv.conf contains "nameserver 127.0.1.1" because dnsmasq is running then (in the standard resolvconf configuration) you won't see any changes in /etc/resolv.conf because resolvconf doesn't list nameserver addresses after any loopback address. (This doesn't mean that adding nameserver information via the connection editor is ineffective, though. If things are working properly, then, if the NetworkManager-controlled nameserver is running, nameserver information added via the connection editor is transmitted to the NetworkManager-controlled nameserver that is listening at that loopback address. This goes via /run/nm-dns-dnsmasq.conf in Ubuntu 12.04, or via D-Bus in Ubuntu 12.10 or later.)

---

### Post by jdthood on 2013-05-17
> **quequotion said:**
> 
I think this number should be extracted from dnsmasq's configuration however, and not arbitrarily specified in the init script. If this number is not the same as the number in the configuration file, and users do not specify the correct number in /etc/resolvconf/resolv.conf.d/head then DNS queries will be sent to into a black hole.  **#note to self: make a bug report**


Perhaps add your comment to the existing bug report [https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1042275](https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1042275)

---

### Post by jdthood on 2013-05-17
> **quequotion said:**
> This does not work. 127.0.0.2 will not be added to /etc/resolv.conf and DNS will not resolve. I tried this from the command line as well as by init script; dnscrypt-proxy and dnsmasq both run, but DNS requests never get forwarded to dnscrypt-proxy.

Resolvconf won't normally add 127.0.0.2 to resolv.conf if there is an earlier line "nameserver 127.0.1.1". It isn't needed there because the glibc resolver should contact dnsmasq (at 127.0.1.1) and not dnscrypt-proxy.

However, dnsmasq *should* contact dnscrypt-proxy.

Let's debug. Please comment out "dns=dnsmasq"; reboot; ensure that dnsmasq is listening at 127.0.1.1; ensure that dnscrypt-proxy is listening at 127.0.0.2; run

```

echo "nameserver 127.0.0.2" | resolvconf -a lo.dnscrypt-proxy

```

and then post the output of

```

ls -l /etc/resolv.conf
cat /etc/resolv.conf
ls -l /run/resolvconf
ls -l /run/resolvconf/interface
for F in /run/resolvconf/interface/* ; do echo "=== $F ===" ; cat "$F" ; done
ls -l /etc/resolvconf/resolv.conf.d
for F in /etc/resolvconf/resolv.conf.d/* ; do echo "=== $F ===" ; cat "$F" ; done
cat /etc/default/resolvconf
ls -l /var/run/dnsmasq
cat /var/run/dnsmasq/resolv.conf

```

---

### Post by quequotion on 2013-05-18
> **jdthood said:**
> Long ago when Debian contained the "dhcp-client" package (version 2), /etc/dhcp/ was used. When "dhcp3-client" was introduced it used /etc/dhcp3/ so that it could be installed alongside dhcp-client. After dhcp-client was dropped from Debian, dhcp3-client was renamed to "isc-dhcp-client" and stuff was moved from /etc/dhcp3/ to /etc/dhcp/.  So either new, or very old, systems use /etc/dhcp/. So what we need are for the transitional packages to install symlinks to the config files and then purge them on uninstall. #note to self: still need to make that bug report / feature request.

> **jdthood said:**
> This indicates that resolvconf is either absent, or is non-standardly configured on your machine. Because resolvconf normally doesn't include any "nameserver" lines after a "nameserver 127.0.0.1" line. See my next post.I think you are looking at this discussion from the wrong angle. resolvconf is present and configured as default (except for the head file).> If /etc/resolv.conf contains "nameserver 127.0.1.1" because dnsmasq is running then (in the standard resolvconf configuration) you won't see any changes in /etc/resolv.conf because **resolvconf doesn't list nameserver addresses after any loopback address.**I think this is the key point. There should be a "correct" way to get resolvconf to add a second line to this file, but I can't find any documentation on it.>  (This doesn't mean that adding nameserver information via the connection editor is ineffective, though. If things are working properly, then, if the NetworkManager-controlled nameserver is running, nameserver information added via the connection editor is transmitted to the NetworkManager-controlled nameserver that is listening at that loopback address. This goes via /run/nm-dns-dnsmasq.conf in Ubuntu 12.04, or via D-Bus in Ubuntu 12.10 or later.) As I pointed out, it is necessary to disable to the NetworkManager-controlled dnsmasq and install a separate dnsmasq in order to have a custom configuration *in 12.04*. My initial two posts are a how-to guide for getting dnsmasq and dnscrypt-proxy to work together *in 12.04*; it is not possible to use the NetworkManager-controlled dnsmasq with DNSCrypt *in 12.04*.

> **jdthood said:**
> Perhaps add your comment to the existing bug report [https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1042275](https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1042275) That's not exactly the right bug, although your last comment in it is relevant. It's not just a matter of listening on "lo" or not, but that the IP address assigned in the initscript is not bound to be the same as the address in dnsmasq's config file and that could create a black hole for DNS queries to fall into. Communicating directly with resolvconf would be an efficient way of solving *both* problems.

> **jdthood said:**
> Resolvconf won't normally add 127.0.0.2 to resolv.conf if there is an earlier line "nameserver 127.0.1.1". As I said before, there must be a "correct" way of getting resolvconf to add a second line. It is necessary because:
> It isn't needed there because the glibc resolver should contact dnsmasq (at 127.0.1.1) and not dnscrypt-proxy.

However, dnsmasq *should* contact dnscrypt-proxy.It should, when configured to do so (it cannot auto-magically do so), but it doesn't. There is a place in dnsmasq's config file to add other DNS servers, but then it never actually forwards queries to them. So, it is necessary to have two lines in resolv.conf: one for the DNS cache (dnsmasq) and another for the secure DNS resolver (dnscrypt-proxy). There is no other way for this to work *in 12.04*.

> Let's debug. Please comment out "dns=dnsmasq"; reboot; ensure that dnsmasq is listening at 127.0.1.1; ensure that dnscrypt-proxy is listening at 127.0.0.2; run

```

echo "nameserver 127.0.0.2" | resolvconf -a lo.dnscrypt-proxy

``` Please go over what I've posted again; this is exactly what I recommended. Commenting out "dns=dnsmasq" and installing a separate, *configurable*, dsnmasq is the only way to get dnsmasq and dnscrypt-proxy working together *in 12.04*, which is why I wrote a how-to guide on setting them up as such.

When I ran that command, nothing was added to resolv.conf and DNS queries do not resolve. There should be a "correct" way to get resolvconf to add a second line to /etc/resolv.conf.

> and then post the output of

```

ls -l /etc/resolv.conf
cat /etc/resolv.conf
ls -l /run/resolvconf
ls -l /run/resolvconf/interface
for F in /run/resolvconf/interface/* ; do echo "=== $F ===" ; cat "$F" ; done
ls -l /etc/resolvconf/resolv.conf.d
for F in /etc/resolvconf/resolv.conf.d/* ; do echo "=== $F ===" ; cat "$F" ; done
cat /etc/default/resolvconf

```

I'll get you that output next time I'm at home. I think it's important to note here: I posted my how-to guide after doing considerable testing and diagnostics myself. The things I said don't work, *really don't work in 12.04*; if someone wants to use dnsmasq with dnscrypt in 12.04 they will (most likely) have do it as I posted. From what you've posted, I take it that much more of the "new way" is properly implemented in 12.10, which means users of 12.10 need a different (and much shorter) guide.

There's only really one point that needs debugging for me:

*Why doesn't dnsmasq use DNS servers specified in it's configuration file?*

An answer to that question would resolve everything else you are asking me about, and possibly shorten my how-to *for 12.04*.

---

### Post by quequotion on 2013-05-18
I've edited and annotated the how-to guide to note the discrepancies between 12.04 and 12.10. Hopefully this will clear up any confusion.

---

### Post by quequotion on 2013-05-19
ls -l /etc/resolv.conf```
lrwxrwxrwx 1 root root 29 Apr 14  2012 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
``` Symlinked where it should be.

cat /etc/resolv.conf```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1 #dnsmasq
nameserver 127.0.0.2 #dnscrypt-proxy 
nameserver 127.0.1.1
``` Just like it is in my how-to.

ls -l /run/resolvconf```
total 4
-rw-r--r-- 1 root root   0 May 19 15:26 enable-updates
drwxr-xr-x 2 root root 100 May 19 15:26 interface
-rw-r--r-- 1 root root 240 May 19 15:26 resolv.conf
```Nothing unusual here.

ls -l /run/resolvconf/interface```
total 8
-rw-r--r-- 1 root root 21 May 19 15:26 lo.dnsmasq
-rw-r--r-- 1 root root 42 May 19 15:26 NetworkManager
```Looks ok to me.

for F in /run/resolvconf/interface/* ; do echo "=== $F ===" ; cat "$F" ; done```
=== /run/resolvconf/interface/lo.dnsmasq ===
nameserver 127.0.1.1
=== /run/resolvconf/interface/NetworkManager ===
nameserver 127.0.1.1
nameserver 127.0.0.2

```NetworkManager probably extracts those from resolv.conf, as they are not specified anywhere else.

ls -l /etc/resolvconf/resolv.conf.d```
total 8
-rw-r--r-- 1 root root   0 May 13 12:34 base
-rw-r--r-- 1 root root 219 May 16 05:44 head
-rw-r--r-- 1 root root 221 May 16 05:41 head~
-rw-r--r-- 1 root root   0 Jan  4 06:31 tail
```I modified head with gedit, so there's a backup file.

for F in /etc/resolvconf/resolv.conf.d/* ; do echo "=== $F ===" ; cat "$F" ; done```
=== /etc/resolvconf/resolv.conf.d/base ===
=== /etc/resolvconf/resolv.conf.d/head ===
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1 #dnsmasq
nameserver 127.0.0.2 #dnscrypt-proxy 
=== /etc/resolvconf/resolv.conf.d/head~ ===
=== /etc/resolvconf/resolv.conf.d/tail ===
```Nothing to see here really, except the changes I made to head to get DNS to resolve.

cat /etc/default/resolvconf```
cat: /etc/default/resolvconf: No such file or directory
```Nothing there.

ls -l /var/run/dnsmasq```
total 8
-rw-r--r-- 1 root root  5 May 19 15:26 dnsmasq.pid
-rw-r--r-- 1 root root 42 May 19 15:26 resolv.conf
```As expected.

cat /var/run/dnsmasq/resolv.conf```
nameserver 127.0.0.2
nameserver 127.0.1.1
```The servers are not in the same order as the real resolv.conf they've been extracted from. My understanding is that it doesn't matter unless I specifiy the "strict-order" option for dnsmasq.

---

### Post by jdthood on 2013-05-19
First let me say that I appreciate what you are trying to do. It's good that you were able to get dnsmasq and dnscrypt working together in daisy chain with the former (dnsmasq, first stage) caching and forwarding queries to the latter (dnscrypt, second stage).

I believe, however, that the way you implemented things was less than ideal, regardless of whether the base system is Ubuntu 12.04 or 12.10. What I would like to do is continue to work with you to implement things as well as the base system allows. When we have done this we will know exactly how to package dnscrypt properly for Ubuntu.

When I replied to your original post I just tried to address a few parenthetical remarks you made and to answer the questions that you asked in your post. The discussion that followed was a bit confusing, but now I think I know why. I have just gone back and re-read the whole thread and I now realize that I overlooked the most important problem of all. You are under the impression that the NetworkManager-controlled dnsmasq instance can be used in the "first stage", in the same role as dnsmasq server &#8212; or, rather, *could* be used as the first stage if it were possible to customize its configuration (as it is possible in Ubuntu 12.10). **But this is not supported, even in Ubuntu 12.10.** NetworkManager feeds its slave dnsmasq instance with the nameserver addresses it knows about that are associated with *external* network connections. When you enter addresses into the "DNS servers" field in the connection editor, those addresses are meant to be *external* addresses *accessible over the connection in question*. Entering *loopback* addresses into the "DNS servers" field is not supported.

Note that daisy chaining dnsmasq server instance to the NetworkManager-controlled dnsmasq instance *is* supported. Obtaining this in Ubuntu 12.04 requires some manual configuration of dnsmasq server because in Ubuntu 12.04 the NetworkManager-controlled dnsmasq instance listens at 127.0.0.1 which conflicts with dnsmasq server in its default configuration. Obtaining the dnsmasq-dnsmasq daisy chain in Ubuntu 12.10 requires only the installation of the dnsmasq package; after it's installed, dnsmasq server listens at 127.0.0.1 in bind-interfaces mode and forwards queries to nm-dnsmasq at 127.0.1.1.

Now let's turn to your debugging output. It looks as if you didn't follow my instructions exactly &#8212; you didn't run the line with "resolvconf -a lo.dnscrypt-proxy", otherwise there would be a file named "lo.dnscrypt-proxy" in /run/resolvconf/interface/ &#8212; but this probably doesn't matter because I think we have found the most important problem.

Looking at the debugging output I see that DNS queries will follow paths like the following.
```

glibc resolver -------------> 127.0.1.1 dnsmasq server -------------> 127.0.0.2 dnscrypt ----> OpenDNS
                  \      /                                  \     /
                   \     \-----------------<--------------- /    /
                    ------------------------>-------------------

```

I assume that dnscrypt is somehow configured to know the OpenDNS nameserver addresses. Is that right? (I have no experience with dnscrypt.)  

**Update:** I have started reading the dnscrypt docs and found: > DNSCrypt comes pre-configured for OpenDNS, although the --resolver-address=<ip>:<port>, --provider-name=<certificate provider FQDN> and --provider-key=<provider public key> can be specified in order to change the default settings. So dnscrypt-proxy can forward to servers other than OpenDNS &#8212; but those servers would of course have to support the DNSCrypt protocol.

That dnsmasq server has 127.0.1.1 as both a forwarding address and as its listen address is bad. This tells dnsmasq to loop queries back to itself. This is a consequence of 127.0.1.1 being included in a "DNS servers" field for a connection.

You should have something like the following instead.
```

glibc resolver -------> 127.0.0.1 dnsmasq server --------> 127.0.0.2 dnscrypt ----> OpenDNS

```

(127.0.0.1 is the IPv4 address of the loopback device and one of the addresses that dnsmasq server listens at by default. For dnscrypt you can choose any address in 127/8 but 127.0.1.1 is not a particularly good choice since that the address used by nm-dnsmasq.)

To achieve this:
* Configure the external network connection with the NetworkManager connection editor. Select "Method: Automatic (DHCP) addresses only" and ensure that all the "DNS server" fields are empty.
* Back up any dnsmasq configuration files you changed and don't want to lose. Purge the dnsmasq package (which will delete those configuration files) and reinstall it. This will restore dnsmasq server to the factory configuration wherein it listens at all addresses.
* Enable dnsmasq "bind-interfaces" mode: uncomment the "bind-interfaces" line in /etc/dnsmasq.conf.
* Also set "cache-size=1000" in dnsmasq if desired.
* Back up any resolvconf configuration files you changed and don't want to lose. Purge the resolvconf package (which will delete those configuration files) and reinstall it. This will restore resolvconf to the factory configuration where it contains no non-comment lines in /etc/resolvconf/resolv.conf.d/head.
* Configure dnscrypt to listen at 127.0.0.2.
* Reboot
* Ensure that dnscrypt is listening at 127.0.0.2 and forwards queries to the OpenDNS nameservers.
```
host www.google.com 127.0.0.2
```
* Do
```
echo "nameserver 127.0.0.2" | resolvconf -a lo.dnscrypt-proxy
```
* Check that you can now resolve names via dnsmasq at 127.0.0.1.
```
host www.microsoft.com 127.0.0.1
```
```
host www.ubuntu.com
```

After doing all this, please post the debugging output again.

```

cat /etc/NetworkManager/NetworkManager.conf
ls -l /etc/resolv.conf
cat /etc/resolv.conf
ls -l /run/resolvconf
ls -l /run/resolvconf/interface
for F in /run/resolvconf/interface/* ; do echo "=== $F ===" ; cat "$F" ; done
ls -l /etc/resolvconf/resolv.conf.d
for F in /etc/resolvconf/resolv.conf.d/* ; do echo "=== $F ===" ; cat "$F" ; done
cat /etc/default/resolvconf
ls -l /var/run/dnsmasq
cat /var/run/dnsmasq/resolv.conf

```

Even if this works then we aren't finished quite yet. We need to change the dnscrypt initscript to run "resolvconf -a lo.dnscrypt-proxy" on start and "resolvconf -d lo.dnscrypt-proxy" on stop. And we should probably enhance dnsmasq's resolvconf hook script to be dnscrypt-aware.

P.S. You should probably delete the updates in your original post where you say that in Ubuntu 12.10 you can configure the NetworkManager-controlled dnsmasq instance to play the same role as the dnsmasq server instance.

---

### Post by quequotion on 2013-05-21
Oh, i see. Yeah, we could be discussing a refit for the currently supplied dnsmasq. I hoped it had happened in 12.10, as it has in Arch, but alas no. I will get on straightening out those notes after work. I will re-lable them as "theoretical configuration"

I'll also get that last output; i guess i missed a line!

I don't really understand about dnsmasq looping into itself: shouldn't it do so as a cache? The path is similar to what you said:
DNSQuery->out; ->dnsmasq: in cache?; yes-> return ip; no-> forward to dnscrypt-proxy; ->dnscrypt-proxy->OpenDNS(mutex communication over the proxy;->return ip;

---

### Post by jdthood on 2013-05-21
I have filed a report in the Debian bug tracking system where I wish for automagic integration of dnsmasq with dnscrypt-proxy: [http://bugs.debian.org/709179](http://bugs.debian.org/709179). The Debian maintainer has already agreed to implement this integration. This means that we should have the integration implemented within, say, a month, in Debian unstable. The support will appear in Ubuntu the next time after that that Ubuntu syncs from Debian unstable, which means 13.10 or 14.04.

---

### Post by quequotion on 2013-05-21
Open Source Development Process to the rescue again!

I love it when things work out this well :)

---

### Post by jdthood on 2013-05-21
I just noticed that there's an ITP for dnscrypt-proxy in the Debian BTS ([http://bugs.debian.org/692320](http://bugs.debian.org/692320)). I have submitted a request that this future package support resolvconf. 

Once this is done and resolvconf/dnscrypt-proxy support has been added to dnsmasq ([http://bugs.debian.org/709179](http://bugs.debian.org/709179)) everything should just work. 

Resolvconf itself doesn't need to be changed ([http://bugs.debian.org/709258](http://bugs.debian.org/709258)).

---

### Post by jdthood on 2013-05-27
Here's the patch which should be applied to /etc/resolvconf/update.d/dnsmasq to cause dnsmasq to be dnscrypt-aware on a resolvconf system. Once this patch is applied, on a resolvconf system, dnsmasq server will forward queries to dnscrypt if dnscrypt has registered its listen address with resolvconf.

Update: This patch has since been applied by the maintainer and is included in (Debian) dnsmasq 2.66-3 which was released on 2013-05-28. This package hasn't been synced to Ubuntu yet but there is a chance that it will still make it into 13.10.

Note that none of this has any direct effect on the NetworkManager-controlled dnsmasq instance. However, when (patched) dnsmasq and (suitably configured) dnscrypt-proxy are installed the NetworkManager-controlled dnsmasq instance will not be used: the glibc resolver will route DNS queries to dnsmasq server which will forward them to dnscrypt-proxy which will resolve names using the OpenDNS servers.

Note that this only works if dnscrypt has an initscript that does the equivalent of ```
echo "127.0.2.1" | resolvconf -a lo.dnscrypt
``` on start (where 127.0.2.1 is the arbitrarily chosen loopback address) and ```
resolvconf -d lo.dnscrypt
``` on stop. Note that the record name used here, "lo.dnscrypt", is different from the one I earlier proposed.

```

--- dnsmasq_2.65-1ubuntu1	2013-02-15 21:53:13.000000000 +0100
+++ dnsmasq	2013-05-27 16:03:51.449152504 +0200
@@ -18,6 +16,8 @@
 RUN_DIR="/var/run/dnsmasq"
 RSLVRLIST_FILE="${RUN_DIR}/resolv.conf"
 TMP_FILE="${RSLVRLIST_FILE}_new.$$"
+MY_RECORD_NAME="lo.dnsmasq"
+DNSCRYPT_RECORD_NAME="lo.dnscrypt"
 
 [ -x /usr/sbin/dnsmasq ] || exit 0
 [ -x /lib/resolvconf/list-records ] || exit 1
@@ -45,7 +45,22 @@
 	exit 1
 fi
 
-RSLVCNFFILES="$(/lib/resolvconf/list-records | sed -e '/^lo.dnsmasq$/d')"
+RSLVCNFFILES=""
+for F in $(/lib/resolvconf/list-records) ; do
+	case "$F" in
+	  "$MY_RECORD_NAME")
+		# Omit
+		;;
+	  "$DNSCRYPT_RECORD_NAME")
+		# Dnscrypt, I only have eyes for you
+		RSLVCNFFILES="$DNSCRYPT_RECORD_NAME"
+		break
+		;;
+	  *)
+		RSLVCNFFILES="${RSLVCNFFILES:+$RSLVCNFFILES }$F"
+		;;
+	esac
+done
 
 NMSRVRS=""
 if [ "$RSLVCNFFILES" ] ; then

```

---

