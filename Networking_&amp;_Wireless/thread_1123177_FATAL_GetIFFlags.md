---
title: "FATAL: GetIFFlags"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by reltx on 2009-04-11
How do I fix this error when I try to run kismet?

linuxwireless drivers are installed.

FATAL: GetIFFlags: interface eth1: No such device

---

### Post by chili555 on 2009-04-11
Does *iwconfig* agree that your wireless interface is eth1? Does */etc/kismet/kismet.conf* agree?

---

### Post by reltx on 2009-04-12
It's giving me the weirdest results.  Before it was eth1 now its wlan0.  When it was at eth1 it supported injection but couldn't find it, now it wont do either.

**Iwconfig:**
m@m-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

**Kismet Command:**
m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (eth1): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: GetIFFlags: interface eth1: No such device
Done.


**Kismet Config File:**
# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=m

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
source=bcm43xx,wlan0,wlan0

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource
source=bcm43xx,wlan0,wlan0

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

---

### Post by chili555 on 2009-04-12
> # YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
[COLOR="Red"]source=bcm43xx,wlan0,wlan0
[/COLOR]
# Comma-separated list of sources to enable. This is only needed if you defined
# multiple sources and only want to enable some of them. By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource
[COLOR="Red"]source=bcm43xx,wlan0,wlan0[/COLOR]You don't need this declaration twice. I suggest you comment out one of them. Also, may we please see:```
cat /etc/udev/rules.d/70-persistent-net.rules
```Thanks.

---

### Post by reltx on 2009-04-12
m@m-laptop:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:11", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4311 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:11", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4311 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:11", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"



m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for bcm43xx source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.

---

### Post by chili555 on 2009-04-12
I suggest you comment out this part, like this:```
# PCI device 0x14e4:0x4311 (wl)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:11", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
[COLOR="Red"]#Commented out 12April2009 experimentally[/COLOR]
```In order to be doubly safe, I'd suggest a reboot.> FATAL: Failed to set monitor mode: Invalid argument.Please try, before you start kismet:```
sudo ifconfig wlan0 down
sudo iwconfig wlano mode monitor
```Now start kismet and tell us what happens. When you are ready to go back to Managed mode, please do:```
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```

---

### Post by reltx on 2009-04-12
**m@m-laptop:~$** sudo ifconfig wlan0 down
[sudo] password for m: 
**m@m-laptop:~$** sudo iwconfig wlano mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlano ; No such device.
**m@m-laptop:~$** sudo iwconfig wlan0 mode managed
**m@m-laptop:~$** sudo ifconfig wlan0 up
**m@m-laptop:~$** kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
Done.
**m@m-laptop:~$** sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for bcm43xx source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
**m@m-laptop:~$ **



arrrrrggggg....

---

### Post by chili555 on 2009-04-12
> sudo iwconfig wlan[COLOR="Red"]o[/COLOR] mode monitorIt's not wlano. it's wlan[COLOR="Red"]0[/COLOR]. Please try again.

---

### Post by reltx on 2009-04-12
m@m-laptop:~$ sudo ifconfig wlan0 down
m@m-laptop:~$ sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
m@m-laptop:~$ sudo iwconfig wlan0 mode managed
m@m-laptop:~$ sudo ifconfig wlan0 up
m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for bcm43xx source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
m@m-laptop:~$ 


still no dice...

---

### Post by chili555 on 2009-04-12
Upon further research, I really wonder if your capture source is supposed to be *bcm43xx*. Please do:```
lsmod | grep 43
```If you are using b43, as I suspect, please amend your */etc/kismet/kismet.conf* to change your capture source from bcm43xx to b43. Then try kismet again. If you still have no luck, we ought to troubleshoot your linuxwireless installation.

---

### Post by reltx on 2009-04-12
m@m-laptop:~$ lsmod | grep 43
snd_seq_midi           14336  0 
battery                18436  0 
nvidia               6909268  43 
cdrom                  43168  1 sr_mod
ehci_hcd               43788  0 
m@m-laptop:~$

changed this:
```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=bcm43xx,wlan0,wlan0
```

to:
```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=b43,wlan0,wlan0
```



m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for b43 source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
m@m-laptop:~$ 


If I'm using the wrong drivers, what is the best driver for my BCM4311 that is compatible with kismet and aircrack-ng.  I have used kismet in backtrack so I know that it works.  Although, the interface on BT3 is eth1.

---

### Post by chili555 on 2009-04-12
So, you do not have bcm43xx or b43 loaded! What in the world is driving your wireless??? This gets more amazing by the second!!! Please do:```
sudo lshw -C network
```By the way, that's a capital C there.

Please post only the wireless interface parts. Thanks.

---

### Post by reltx on 2009-04-12
m@m-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:f6:8f:c7
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes promiscuous=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3e:8c:74:f1:95:2a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
m@m-laptop:~$

---

### Post by chili555 on 2009-04-12
> driver=ndiswrapper+bcmwl5This is from */usr/share/doc/kismet/README.gz*:> ndiswrapper - Anything using ndiswrapper is using WINDOWS drivers AND CAN NOT BE USED WITH KISMET.Mystery solved!

You said you were using linuxwireless drivers, but this is from their site:> With Ubuntu you have the option of either installing compat-wireless yourself or of installing the package that provides it built by the Ubuntu kernel team. The Ubuntu package that carries compat-wireless is called linux-backport-modules and it has more backported modules than just your wireless subsystem. Its updated whenever major updates are pushed out into the wireless-testing git tree.I'd suggest you open up synaptic, install linux-backports-modules-intrepid-generic (if you are using Intrepid, of course). Then do:```
sudo apt-get install b43-fwcutter
```Remove b43 and  ssb from /etc/modprobe.d/blacklist if they are there. You can just comment them out.

Then I would do:```
sudo ifconfig wlan0 down
sudo rmmod -f ndiswrapper
sudo modprobe b43
sudo iwconfig
```Do you have a wireless interface? If it all works, we can make the removal of ndiswrapper permanent.

---

### Post by reltx on 2009-04-12
m@m-laptop:~$ sudo apt-get install b43-fwcutter
[sudo] password for m: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
m@m-laptop:~$ 

```
/etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

[COLOR="Red"]# replaced by b43 and ssb.
blacklist bcm43xx
[/COLOR]
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
blacklist bcm43xx
blacklist wl

[COLOR="Red"]deleted in red[/COLOR]
```


m@m-laptop:~$ sudo ifconfig wlan0 down
m@m-laptop:~$ sudo rmmod -f ndiswrapper
m@m-laptop:~$ sudo modprobe b43
FATAL: Error inserting b43 (/lib/modules/2.6.27-11-generic/updates/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)
m@m-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for b43 source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
m@m-laptop:~$

---

### Post by reltx on 2009-04-12
its still not working, bump

---

### Post by chili555 on 2009-04-12
Did you do this part?> I'd suggest you open up synaptic, install linux-backports-modules-intrepid-generic (if you are using Intrepid, of course)That should overwrite the module b43, hopefully one without unknown symbols.

---

### Post by reltx on 2009-04-12
yea i did all that.  im totally lost though

---

### Post by chili555 on 2009-04-12
What we are trying to do here is get rid of ndiswrapper, even temporarily, which does not work with kismet, and to load up b43, which does work with kismet. This part:> m@m-laptop:~$ sudo rmmod -f ndiswrappertells us that the ndiswrapper module was removed successfully. To confirm, please do:```
lsmod | grep ndis
```If ndiswrapper was removed, the command prompt should just pop back. That means lsmod found no loaded modules with 'ndis' in their name.

Now, after you installed *install linux-backports-modules-intrepid-generic *it should have overwritten the module b43, giving you a fresh, new copy. Just in case something went wrong, please open up Synaptic and search for 'linux-backports-modules-intrepid' and mark every one that is installed, signified by a green box, and right click them individually and 'Mark for Reinstallation'. Press Apply and let it whirl. Then do:```
sudo modprobe b43
```Now did it insert cleanly?

If so, we should be able to connect to the internet, go into monitor mode and, finally, run kismet!

---

### Post by reltx on 2009-04-12
After reinstalation and restart.

m@m-laptop:~$ lsmod | grep ndis
ndiswrapper           196380  0 
usbcore               149488  6 usbhid,ndiswrapper,isp1760,ehci_hcd,ohci_hcd
m@m-laptop:~$ sudo modprobe b43
[sudo] password for m: 
m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for b43 source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
m@m-laptop:~$ 



damn....

---

### Post by chili555 on 2009-04-12
Upon restart, ndiswrapper loaded again, since we have not yet put in a permanent fix. We are still at the trial stages. So let's do:```
sudo rmmod -f ndiswrapper
sudo rmmod  -f b43
sudo modprobe b43
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode Monitor
sudo ifup wlan0
kismet
```Thanks.

---

### Post by reltx on 2009-04-12
m@m-laptop:~$ sudo rmmod -f ndiswrapper
[sudo] password for m: 
m@m-laptop:~$ sudo rmmod  -f b43
m@m-laptop:~$ sudo modprobe b43
m@m-laptop:~$ sudo ifconfig wlan0 down
m@m-laptop:~$ sudo iwconfig wlan0 mode Monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
m@m-laptop:~$ sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
m@m-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
m@m-laptop:~$ kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
FATAL:  Unable to set up pidfile /var/run//kismet_server.pid, unlink() failed: Permission denied
Done.
m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for b43 source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not suppm@m-laptop:~$ sudo rmmod -f ndiswrapper
[sudo] password for m: 
m@m-laptop:~$ sudo rmmod  -f b43
m@m-laptop:~$ sudo modprobe b43
m@m-laptop:~$ sudo ifconfig wlan0 down
m@m-laptop:~$ sudo iwconfig wlan0 mode Monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
m@m-laptop:~$ sudo iwconfig wlan0 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
m@m-laptop:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
m@m-laptop:~$ kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
FATAL:  Unable to set up pidfile /var/run//kismet_server.pid, unlink() failed: Permission denied
Done.
m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for b43 source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done
bort monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.


im so sorry about all the trouble, but it still gives me errors.

---

### Post by chili555 on 2009-04-12
Without rebooting, please let me see:```
iwconfig
lsmod | grep ndis
lsmod | grep b43
```Thanks.

---

### Post by reltx on 2009-04-12
m@m-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

m@m-laptop:~$ lsmod | grep ndis
ndiswrapper           196380  0 
usbcore               149488  8 ndiswrapper,usblp,usbhid,isp1760,ehci_hcd,ohci_hcd
m@m-laptop:~$ lsmod | grep b43
b43                   138012  0 
rfkill                 17176  1 b43
lbm_cw_mac80211       215856  1 b43
lbm_cw_cfg80211        46744  2 b43,lbm_cw_mac80211
led_class              12164  1 b43
input_polldev          11912  1 b43
ssb                    49028  2 b43,b44
pcmcia                 43052  2 b43,ssb
pcmcia_core            43412  3 b43,ssb,pcmcia
m@m-laptop:~$

---

### Post by chili555 on 2009-04-13
Wonderful! b43 and ndiswrapper battling together for domination of your wireless card!

Let's see if we can stop ndiswrapper permanently so that b43 can take over without conflict and we can kismet! Please do:```
sudo ndiswrapper -e bcmwl5
```Then edit */etc/modules* and, if it's present, comment out ndiswrapper and add, on it's own line, b43. Next, edit */etc/modprobe.d/blacklist* and add a new line, ndiswrapper. Also make sure that b43 and ssb are not in there. If they are, comment them out.

Reboot and run:```
iwconfig
```Do you have a wireless interface? Will kismet run?

---

### Post by reltx on 2009-04-13
I can get onto wifi and ethernet, but kismet will not run...

m@m-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

m@m-laptop:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wlan0): Enabling monitor mode for b43 source interface wlan0 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
m@m-laptop:~$ 



m@m-laptop:~$ sudo gedit /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
b43
```


m@m-laptop:~$ sudo gedit /etc/modprobe.d/blacklist
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
blacklist bcm43xx
blacklist wl
blacklist ndiswrapper
```

---

### Post by chili555 on 2009-04-13
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up
kismet
```Please let me know.

---

### Post by reltx on 2009-04-14
Ok... So I reinstalled Ubuntu 8.10 and installed some drivers with a tut from joker.  Monitor mode works, but I still get this....

root@m-lap:~# ifconfig wlan0 down
root@m-lap:~# iwconfig wlan0 mode monitor
root@m-lap:~# ifconfig wlan0 up
root@m-lap:~# kismet
Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to m (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'b43' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
Done.
root@m-lap:~#

---

### Post by chili555 on 2009-04-14
> FATAL: Support for capture source type 'b43' was not built. Check the output from 'configure' for more information about why it might not have been compiled in. Done.Did you build kismet from a .tar.gz or install it with Synaptic? I recommend the latter.

We are getting closer!

---

### Post by reltx on 2009-04-14
I got it from a tar, so then ill just install it again from synaptic!

---

