---
title: "Kismet Setup"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by narcoleptik.ninja on 2009-10-06
I've done lots of research (or tried) but I can't seem to correctly configure kismet for wireless.

here is my lshw -C network readout:

```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:73:a8:a5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.1.103 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:a0:b1:fe
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s

```Here is my configuration file, I know I'm doing this config wrong...

```

# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=your_user_here

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=wl0,eth1,broadcom

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource


# Automatically destroy VAPs on multi-vap interfaces (like madwifi-ng).
# Madwifi-ng doesn't work in rfmon when non-rfmon VAPs are present, however
# this is a fairly invasive change to the system so it CAN be disabled.  Expect
# things not to work in most cases if you do disable it, however.
vapdestroy=true


# Do we channelhop?
channelhop=true

# How many channels per second do we hop?  (1-10)
channelvelocity=5

# By setting the dwell time for channel hopping we override the channelvelocity
# setting above and dwell on each channel for the given number of seconds.
#channeldwell=10

# Do we split channels between cards on the same spectrum?  This means if 
# multiple 802.11b capture sources are defined, they will be offset to cover
# the most possible spectrum at a given time.  This also controls splitting
# fine-tuned sourcechannels lines which cover multiple interfaces (see below)
channelsplit=true

# Basic channel hopping control:
# These define the channels the cards hop through for various frequency ranges
# supported by Kismet.   More finegrain control is available via the 
# "sourcechannels" configuration option.
# 
# Don't change the IEEE80211<x> identifiers or channel hopping won't work.

# Users outside the US might want to use this list:
# defaultchannels=IEEE80211b:1,7,13,2,8,3,14,9,4,10,5,11,6,12
defaultchannels=IEEE80211b:1,6,11,2,7,3,8,4,9,5,10

# 802.11g uses the same channels as 802.11b...
defaultchannels=IEEE80211g:1,6,11,2,7,3,8,4,9,5,10

# 802.11a channels are non-overlapping so sequential is fine.  You may want to
# adjust the list depending on the channels your card actually supports.
# defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64,100,104,108,112,116,120,124,128,132,136,140,149,153,157,161,184,188,192,196,200,204,208,212,216 
defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64

# Combo cards like Atheros use both 'a' and 'b/g' channels.  Of course, you
# can also explicitly override a given source.  You can use the script 
# extras/listchan.pl to extract all the channels your card supports.
defaultchannels=IEEE80211ab:1,6,11,2,7,3,8,4,9,5,10,36,40,44,48,52,56,60,64

# Fine-tuning channel hopping control:
# The sourcechannels option can be used to set the channel hopping for 
# specific interfaces, and to control what interfaces share a list of 
# channels for split hopping.  This can also be used to easily lock
# one card on a single channel while hopping with other cards.
# Any card without a sourcechannel definition will use the standard hopping
# list.
# sourcechannels=sourcename[,sourcename]:ch1,ch2,ch3,...chN

# ie, for us channels on the source 'prism2source' (same as normal channel
# hopping behavior):
# sourcechannels=prism2source:1,6,11,2,7,3,8,4,9,5,10

# Given two capture sources, "prism2a" and "prism2b", we want prism2a to stay
# on channel 6 and prism2b to hop normally.  By not setting a sourcechannels 
# line for prism2b, it will use the standard hopping.
# sourcechannels=prism2a:6

# To assign the same custom hop channel to multiple sources, or to split the 
# same custom hop channel over two sources (if splitchannels is true), list
# them all on the same sourcechannels line:
# sourcechannels=prism2a,prism2b,prism2c:1,6,11

# Port to serve GUI data
tcpport=2501
# People allowed to connect, comma seperated IP addresses or network/mask
# blocks.  Netmasks can be expressed as dotted quad (/255.255.255.0) or as
# numbers (/24)
allowedhosts=127.0.0.1
# Address to bind to.  Should be an address already configured already on
# this host, reverts to INADDR_ANY if specified incorrectly.
bindaddress=127.0.0.1
# Maximum number of concurrent GUI's
maxclients=5

# Do we have a GPS?
gps=false
# Host:port that GPSD is running on.  This can be localhost OR remote!
gpshost=localhost:2947
# Do we lock the mode?  This overrides coordinates of lock "0", which will
# generate some bad information until you get a GPS lock, but it will 
# fix problems with GPS units with broken NMEA that report lock 0
gpsmodelock=false

# Packet filtering options:
# filter_tracker - Packets filtered from the tracker are not processed or
#                  recorded in any way.
# filter_dump    - Packets filtered at the dump level are tracked, displayed,
#                  and written to the csv/xml/network/etc files, but not 
#                  recorded in the packet dump
# filter_export  - Controls what packets influence the exported CSV, network,
#                  xml, gps, etc files.
# All filtering options take arguments containing the type of address and
# addresses to be filtered.  Valid address types are 'ANY', 'BSSID',
# 'SOURCE', and 'DEST'.  Filtering can be inverted by the use of '!' before
# the address.  For example,
# filter_tracker=ANY(!00:00:DE:AD:BE:EF)
# has the same effect as the previous mac_filter config file option.
# filter_tracker=...
# filter_dump=...
# filter_export=...

# Alerts to be reported and the throttling rates.
# alert=name,throttle/unit,burst/unit
# The throttle/unit describes the number of alerts of this type that are
# sent per time unit.  Valid time units are second, minute, hour, and day.
# Burst rates control the number of packets sent at a time
# For example:
# alert=FOO,10/min,5/sec
# Would allow 5 alerts per second, and 10 alerts total per minute.
# A throttle rate of 0 disables throttling of the alert.
# See the README for a list of alert types.
alert=NETSTUMBLER,10/min,1/sec
alert=WELLENREITER,10/min,1/sec
alert=LUCENTTEST,10/min,1/sec
alert=DEAUTHFLOOD,10/min,2/sec
alert=BCASTDISCON,10/min,2/sec
alert=CHANCHANGE,5/min,1/sec
alert=AIRJACKSSID,5/min,1/sec
alert=PROBENOJOIN,10/min,1/sec
alert=DISASSOCTRAFFIC,10/min,1/sec
alert=NULLPROBERESP,10/min,1/sec
alert=BSSTIMESTAMP,10/min,1/sec
alert=MSFBCOMSSID,10/min,1/sec
alert=LONGSSID,10/min,1/sec
alert=MSFDLINKRATE,10/min,1/sec
alert=MSFNETGEARBEACON,10/min,1/sec
alert=DISCONCODEINVALID,10/min,1/sec
alert=DEAUTHCODEINVALID,10/min,1/sec

# Known WEP keys to decrypt, bssid,hexkey.  This is only for networks where
# the keys are already known, and it may impact throughput on slower hardware.
# Multiple wepkey lines may be used for multiple BSSIDs.
# wepkey=00:DE:AD:C0:DE:00,FEEDFACEDEADBEEF01020304050607080900

# Is transmission of the keys to the client allowed?  This may be a security
# risk for some.  If you disable this, you will not be able to query keys from
# a client.
allowkeytransmit=true

# How often (in seconds) do we write all our data files (0 to disable)
writeinterval=300

# How old (and inactive) does a network need to be before we expire it?
# This is really only good for limited ram environments where keeping a
# total log of all networks is problematic.  This is in seconds, and should
# be set to a large value like 12 or 24 hours.  This is intended for use
# on stationary systems like an IDS
# logexpiry=86400

# Do we limit the number of networks we log?  This is for low-ram situations
# when tracking everything could lead to the system falling down.  This
# should be combined with a sane logexpiry value to flush out very old 
# inactive networks.  This is mainly for stationary systems like an IDS.
# limitnets=10000

# Do we track IVs?  this can help identify some attacks, but takes a LOT
# of memory to do so on a busy network.  If you have the RAM, by all
# means turn it on.
trackivs=false

# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=false
# Path to sound player
soundplay=/usr/bin/play
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=//usr/share/kismet/wav/new_network.wav
# Wepped new network
# sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=//usr/share/kismet/wav/traffic.wav
# Network junk traffic found
sound_junktraffic=//usr/share/kismet/wav/junk_traffic.wav
# GPS lock aquired sound
# sound_gpslock=//usr/share/kismet/wav/foo.wav
# GPS lock lost sound
# sound_gpslost=//usr/share/kismet/wav/bar.wav
# Alert sound
sound_alert=//usr/share/kismet/wav/alert.wav

# Does the server have speech? (Again, not to be confused with the GUI's speech)
speech=false
# Server's path to Festival
festival=/usr/bin/festival
# Are we using festival lite?  If so, set the above "festival" path to also
# point to the "flite" binary
flite=false
# Are we using Darwin speech? 
darwinsay=false
# What voice do we use?  (Currently only valid on Darwin)
speech_voice=default
# How do we speak?  Valid options:
# speech    Normal speech
# nato      NATO spellings (alpha, bravo, charlie)
# spell     Spell the letters out (aye, bee, sea)
speech_type=nato
# speech_encrypted and speech_unencrypted - Speech templates
# Similar to the logtemplate option, this lets you customize the speech output.
# speech_encrypted is used for an encrypted network spoken string
# speech_unencrypted is used for an unencrypted network spoken string
#
# %b is replaced by the BSSID (MAC) of the network
# %s is replaced by the SSID (name) of the network
# %c is replaced by the CHANNEL of the network
# %r is replaced by the MAX RATE of the network
speech_encrypted=New network detected, s.s.i.d. %s, channel %c, network encrypted.
speech_unencrypted=New network detected, s.s.i.d. %s, channel %c, network open.

# Where do we get our manufacturer fingerprints from?  Assumed to be in the
# default config directory if an absolute path is not given.
ap_manuf=ap_manuf
client_manuf=client_manuf

# Use metric measurements in the output?
metric=false

# Do we write waypoints for gpsdrive to load?  Note:  This is NOT related to
# recent versions of GPSDrive's native support of Kismet.
waypoints=false
# GPSDrive waypoint file.  This WILL be truncated.
waypointdata=%h/.gpsdrive/way_kismet.txt
# Do we want ESSID or BSSID as the waypoint name ?
waypoint_essid=false

# How many alerts do we backlog for new clients?  Only change this if you have
# a -very- low memory system and need those extra bytes, or if you have a high
# memory system and a huge number of alert conditions.
alertbacklog=50

# File types to log, comma seperated
# dump    - raw packet dump
# network - plaintext detected networks
# csv     - plaintext detected networks in CSV format
# xml     - XML formatted network and cisco log
# weak    - weak packets (in airsnort format)
# cisco   - cisco equipment CDP broadcasts
# gps     - gps coordinates
logtypes=dump,network,csv,xml,weak,cisco,gps

# Do we track probe responses and merge probe networks into their owners?
# This isn't always desireable, depending on the type of monitoring you're
# trying to do.
trackprobenets=true

# Do we log "noise" packets that we can't decipher?  I tend to not, since 
# they don't have anything interesting at all in them.
noiselog=false

# Do we log corrupt packets?  Corrupt packets have enough header information
# to see what they are, but someting is wrong with them that prevents us from
# completely dissecting them.  Logging these is usually not a bad idea.
corruptlog=true

# Do we log beacon packets or do we filter them out of the dumpfile
beaconlog=true

# Do we log PHY layer packets or do we filter them out of the dumpfile
phylog=true

# Do we mangle packets if we can decrypt them or if they're fuzzy-detected
mangledatalog=true

# Do we do "fuzzy" crypt detection?  (byte-based detection instead of 802.11
# frame headers)
# valid option: Comma seperated list of card types to perform fuzzy detection 
#  on, or 'all'
fuzzycrypt=wtapfile,wlanng,wlanng_legacy,wlanng_avs,hostap,wlanng_wext,ipw2200,ipw2915

# Do we do forgiving fuzzy packet decoding?  This lets us handle borked drivers
# which don't indicate they're including FCS, and then do.
fuzzydecode=wtapfile,radiotap_bsd_a,radiotap_bsd_g,radiotap_bsd_bg,radiotap_bsd_b,pcapfile

# Do we use network-classifier fuzzy-crypt detection?  This means we expect 
# packets that are associated with an encrypted network to be encrypted too, 
# and we process them by the same fuzzy compare. 
# This essentially replaces the fuzzycrypt per-source option.
netfuzzycrypt=true

# What type of dump do we generate? 
# valid option: "wiretap" 
dumptype=wiretap
# Do we limit the size of dump logs?  Sometimes ethereal can't handle big ones.
# 0 = No limit
# Anything else = Max number of packets to log to a single file before closing
# and opening a new one.
dumplimit=0

# Do we write data packets to a FIFO for an external data-IDS (such as Snort)?
# See the docs before enabling this.
#fifo=/tmp/kismet_dump

# Default log title
logdefault=Kismet

# logtemplate - Filename logging template.
# This is, at first glance, really nasty and ugly, but you'll hardly ever
# have to touch it so don't complain too much.
#
# %n is replaced by the logging instance name
# %d is replaced by the current date as Mon-DD-YYYY
# %D is replaced by the current date as YYYYMMDD
# %t is replaced by the starting log time
# %i is replaced by the increment log in the case of multiple logs
# %l is replaced by the log type (dump, status, crypt, etc)
# %h is replaced by the home directory
# ie, "netlogs/%n-%d-%i.dump" called with a logging name of "Pok" could expand
# to something like "netlogs/Pok-Dec-20-01-1.dump" for the first instance and 
# "netlogs/Pok-Dec-20-01-2.%l" for the second logfile generated.
# %h/netlots/%n-%d-%i.dump could expand to
# /home/foo/netlogs/Pok-Dec-20-01-2.dump
#
# Other possibilities:  Sorting by directory
# logtemplate=%l/%n-%d-%i
# Would expand to, for example,
# dump/Pok-Dec-20-01-1
# crypt/Pok-Dec-20-01-1
# and so on.  The "dump", "crypt", etc, dirs must exist before kismet is run
# in this case.
logtemplate=/var/log/kismet/%n-%d-%i.%l

# Where do we store the pid file of the server?
piddir=/var/run/

# Where state info, etc, is stored.  You shouldnt ever need to change this.
# This is a directory.
configdir=/var/lib/kismet/

# cloaked SSID file.  You shouldn't ever need to change this.
ssidmap=ssid_map

# Group map file.  You shouldn't ever need to change this.
groupmap=group_map

# IP range map file.  You shouldn't ever need to change this.
ipmap=ip_map



```

---

### Post by chili555 on 2009-10-07
> # YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=wl0,eth1,broadcomI think the name of the module is actually *wl*, notwithstanding what *lshw* says. I also think, based on the README that Kismet is not yet able to use *wl*. See Section 12 here:```
less /usr/share/doc/kismet/README.gz
```A few people here on the forum have had better success with the module *b43*. Please amend your kismet.conf to use wl and let us know.

---

### Post by narcoleptik.ninja on 2009-10-07
This is what I changed 

```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=wl,eth1,broadcom
```

This is what I got

```

mintyninja@mintynetbook ~ $ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'wl' in source 'wl,eth1,broadcom'
Done.

```

---

### Post by narcoleptik.ninja on 2009-10-07
I think i mis-interpreted what you said previously, I tried...

```

# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=b43,eth1,broadcom
```

and got this response:

```
mintyninja@mintynetbook ~ $ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (broadcom): Enabling monitor mode for b43 source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.

```

---

### Post by chili555 on 2009-10-07
> I think i mis-interpreted what you said previouslyIndeed. First, we must change, temporarily, the driver for your Broadcom card and then run kismet. Please try:```
sudo ifdown eth1 
sudo rmmod -f wl
sudo modprobe b43
sudo ifup wlan0
sudo iwconfig
```Do you now see a wireless interface wlan0? If so, please amend your kismet.conf to use wlan0, instead of eth1 and then do:```
sudo iwconfig wlan0 mode monitor
sudo kismet
```

If not, please let us see:```
dmesg | grep b43
```If this solves your kismet issue, we will have to take some steps to make it permanent.

---

### Post by narcoleptik.ninja on 2009-10-09
Here's what I got...

```
mintyninja@mintynetbook ~ $ sudo ifdown eth1
Ignoring unknown interface eth1=eth1.
mintyninja@mintynetbook ~ $ sudo rmmod -f wl
mintyninja@mintynetbook ~ $ sudo modprobe b43
mintyninja@mintynetbook ~ $ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
mintyninja@mintynetbook ~ $ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

mintyninja@mintynetbook ~ $ dmesg | grep b43
```

the grep for b43 didn't return anything either, what's going on D:

---

### Post by chili555 on 2009-10-09
Before you reboot and undo our work, please let us see:```
sudo lshw -C network
```Let's see if b43 attached to your card and if an interface was created.

---

### Post by Ayuthia on 2009-10-10
You might also want to check ```
lspci -nn
``` to see if you have the 14e4:4315 chipset.  This chipset is not compatible with the b43 module until 2.6.32 unless you compile the most current version from linuxwireless.org.

---

### Post by narcoleptik.ninja on 2009-10-14
This is what I got..

```
mintyninja@mintynetbook ~ $ sudo ifdown eth1
[sudo] password for mintyninja: 
Ignoring unknown interface eth1=eth1.
mintyninja@mintynetbook ~ $ sudo rmmod -f wl
mintyninja@mintynetbook ~ $ sudo modprobe b43
mintyninja@mintynetbook ~ $ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
mintyninja@mintynetbook ~ $ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

mintyninja@mintynetbook ~ $ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:a0:b1:fe
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:26:e8:cc:de:a7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
mintyninja@mintynetbook ~ $ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
02:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
02:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)


```

---

### Post by Ayuthia on 2009-10-14
> **narcoleptik.ninja said:**
> 
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

This shows that you have the 14e4:4315 chipset.  This means that the Ubuntu supplied b43 module will not work for your card.  The only option would be to build the b43 module yourself.  I will note that there is someone in the forums that is trying to do this and has not been successful.  The part that has me concerned is that when the DMA fails, the poster had to removed the card and touch the pins. 

I unfortunately do not have this card so I have not had a chance to test this out.  My recommendation is to not try this unless you know what you are doing.

---

### Post by narcoleptik.ninja on 2009-10-16
//So would your recommendation be to just buy a external usb card that is compatible?

---

### Post by Ayuthia on 2009-10-16
It all depends on how long you want to wait for it.  Ubuntu will most likely get this functionality in Lucid Lynx which comes out just a little over six months from now.  From what I am reading in the b43 mailing list, it sounds like the 2.6.32 kernel version of it is working but there might be something missing in bringing it to 2.6.31.  Lynx will most likely have the 2.6.32 kernel or something newer.

---

### Post by valllllll2000 on 2010-01-05
Hello,

Please can anyone tell me where I can get instructions on how to get kismet work with my laptop.
Laptop: dell inspiron 1501, wifi card: broadcom
ubuntu 9.10
I tried to type kismet in the console or sudo kismet but it doesn´t work. I am really new to this so is there a place where i can get instructions step by step of all the commands tu write?
thank you

---

### Post by chili555 on 2010-01-08
> **valllllll2000 said:**
> Hello,

Please can anyone tell me where I can get instructions on how to get kismet work with my laptop.
Laptop: dell inspiron 1501, wifi card: broadcom
ubuntu 9.10
I tried to type kismet in the console or sudo kismet but it doesn´t work. I am really new to this so is there a place where i can get instructions step by step of all the commands tu write?
thank youThe key is to read and follow the README:```
less /usr/share/doc/kismet/README.gz
```Especially read sections 9 and 12. Then amend your */etc/kismet/kismet.conf* file according to what you learned in the README. Start kismet:```
sudo kismet
```Note any error messages and try again.

Kismet requires that your wireless card go into 'monitor' mode. Not every card supports 'monitor' mode. You may make the appropriate changes to *kismet.conf* and still not get it working.

---

### Post by azwar on 2010-01-16
please remove # at this line #suiduser=your_user_here to only suiduser=your_user_here

```
# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
**#suiduser=your_user_here**
```

As far as I know, the source must reflect your network interface in monitor mode. e.g mon0

---

