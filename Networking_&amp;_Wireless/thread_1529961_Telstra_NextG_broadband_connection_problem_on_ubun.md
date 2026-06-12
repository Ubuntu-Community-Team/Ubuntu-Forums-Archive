---
title: "Telstra NextG broadband connection problem on ubuntu 9.10"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by jmf on 2010-07-12
Ubuntu 9.10 ( Kernel 2.6.31-22-generic ) installed on Dell Latitude D505

The Maxon BP3-EXT usb modem connects OK when connected thru Windows Vista

NetworkManager/pppd recognizes the modem as 16d8:6280 CMOTECH CDMA device - completes CHAP authentication OK - but the modem hangs up during the IPCP conversation - see log below

I get the same result with or without configuration of the telstra account user name and password

I have also set ipcp-max-failure to 30 in /etc/ppp/options - but nothing has changed


```

root@cdsa-laptop:~# stop network-manager
network-manager stop/waiting
root@cdsa-laptop:~# export NM_PPP_DEBUG=1
root@cdsa-laptop:~# NetworkManager --no-daemon
NetworkManager: <info>  starting...
NetworkManager: <info>  modem-manager is now available
NetworkManager:    SCPlugin-Ifupdown: init!
NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
NetworkManager:    SCPluginIfupdown: management mode: unmanaged
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0, iface: eth0): no ifupdown configuration found.
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
NetworkManager:    SCPlugin-Ifupdown: end _init.
NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
NetworkManager: <info>  Wireless now enabled by radio killswitch
NetworkManager:    SCPlugin-Ifupdown: (137329952) ... get_connections.
NetworkManager:    SCPlugin-Ifupdown: (137329952) ... get_connections (managed=false): return empty list.
NetworkManager:    Ifupdown: get unmanaged devices count: 0
NetworkManager: <info>  (eth0): carrier is OFF
NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e100')
NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
NetworkManager: <info>  (eth0): now managed
NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (eth0): bringing up device.
NetworkManager: <info>  (eth0): preparing device.
NetworkManager: <info>  (eth0): deactivating device (reason: 2).
NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0/net/eth0
NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
NetworkManager: <info>  (ttyUSB1): new GSM device (driver: 'option1')
NetworkManager: <info>  (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/1
NetworkManager: <info>  (ttyUSB1): now managed
NetworkManager: <info>  (ttyUSB1): device state change: 1 -> 2 (reason 2)
NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 2).
NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
NetworkManager: <info>  (ttyUSB1): device state change: 2 -> 3 (reason 0)
NetworkManager: user_connection_updated_cb: assertion `old_connection != NULL' failed
NetworkManager: Tried to set deprecated property gsm/band
NetworkManager: <info>  Activation (ttyUSB1) starting connection 'Telstra Telstra (Next G)'
NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 4 (reason 0)
NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (ttyUSB1): device state change: 4 -> 5 (reason 0)
NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (ttyUSB1): device state change: 5 -> 7 (reason 0)
NetworkManager: <info>  Starting pppd connection
NetworkManager: <debug> [1278978153.479217] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute debug ttyUSB1 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
NetworkManager: <debug> [1278978153.502948] nm_ppp_manager_start(): ppp started with pid 2269
NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) scheduled...
NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) started...
NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) complete.
Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
** Message: nm-ppp-plugin: (plugin_init): initializing
** Message: nm-ppp-plugin: (nm_phasechange): status 3 / phase 'serial connection'
using channel 1
NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB1
** Message: nm-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x6911b362> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x3af59a3d> <pcomp> <accomp>]
sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x3af59a3d> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x6911b362> <pcomp> <accomp>]
** Message: nm-ppp-plugin: (nm_phasechange): status 6 / phase 'authenticate'
rcvd [LCP DiscReq id=0x1 magic=0x3af59a3d]
rcvd [CHAP Challenge id=0x1 <0aaebb70584c9f31da3e4dd190c55926>, name = "UMTS_CHAP_SRVR"]
** Message: nm-ppp-plugin: (get_credentials): passwd-hook, requesting credentials...
** Message: nm-ppp-plugin: (get_credentials): got credentials from NetworkManager
sent [CHAP Response id=0x1 <7959cc3c2c8514b40a392db2f9199414>, name = ""]
rcvd [CHAP Success id=0x1 ""]
CHAP authentication succeeded
CHAP authentication succeeded
** Message: nm-ppp-plugin: (nm_phasechange): status 8 / phase 'network'
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
rcvd [IPCP ConfNak id=0x3 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
rcvd [IPCP ConfNak id=0x4 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x5 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
rcvd [IPCP ConfNak id=0x5 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
sent [IPCP ConfReq id=0x6 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
Modem hangup
** Message: nm-ppp-plugin: (nm_phasechange): status 5 / phase 'establish'
** Message: nm-ppp-plugin: (nm_phasechange): status 11 / phase 'disconnect'
Connection terminated.
NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
NetworkManager: <info>  (ttyUSB1): device state change: 7 -> 9 (reason 13)
NetworkManager: <info>  Marking connection 'Telstra Telstra (Next G)' invalid.
NetworkManager: <info>  Activation (ttyUSB1) failed.
NetworkManager: <info>  (ttyUSB1): device state change: 9 -> 3 (reason 0)
NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 0).
NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
** Message: nm-ppp-plugin: (nm_phasechange): status 1 / phase 'dead'
** Message: nm-ppp-plugin: (nm_exit_notify): cleaning up
NetworkManager: <debug> [1278978161.330262] ensure_killed(): waiting for ppp pid 2269 to exit
NetworkManager: <debug> [1278978161.330521] ensure_killed(): ppp pid 2269 cleaned up

```

---

### Post by pdc on 2010-07-13
instead of network manager and modemanager;

if I suggest sakis3g

[http://www.sakis3g.org/](http://www.sakis3g.org/)

I have found it very effective;

sakis has now changed the download page so it is easier to pick a 32bit or 64bit version;

it is a small, lightweight script to download and install

[http://www.sakis3g.org/#download](http://www.sakis3g.org/#download)

 I used it in Europe recently for various vodafone networks: worked well

He provides very good support on the forum he oversees

[http://forum.sakis3g.org/smf/index.php](http://forum.sakis3g.org/smf/index.php)

as the programme runs, it will identify your Telstra and ask which of the networks you want to be connected to

---

### Post by jmf on 2010-07-13
Have tried saskia - but no joy

saskia detected the modem and found the Telstra NextG APN

but could not connect after two attempts

---

### Post by pdc on 2010-07-13
> CMOTECH CDMA device

sorry;

I didn't spot this;

sakis is not configured yet for CDMA ........

can you tell us what

> lsusb

and 

> dmesg | grep tty

give you if you **copy and paste **this commands into a terminal 

and 

**copy and paste** the results back 

I sense from this the device is a ZTE MF626

[https://lists.ubuntu.com/archives/ubuntu-au/2009-April/004770.html](https://lists.ubuntu.com/archives/ubuntu-au/2009-April/004770.html)

so I wonder if you get 

> 0x19d2:2000

or 

> 0x19d2:0031

---

### Post by jmf on 2010-07-13
> lsusb output
Bus 003 Device 006: ID 16d8:6280 CMOTECH Co., Ltd. CMOTECH CDMA Technologies modem

dmesg output
[35114.986412] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB0
[35115.002707] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB1
[35115.005816] usb 3-1: GSM modem (1-port) converter now attached to ttyUSB2

Note that even though it identifies as a CMOTECH CDMA device both NetworkManager and sakis recognize it as a GSM broadband modem - it has its own sim card - see here for a picture [http://quozl.linux.org.au/bp3-usb/]("http://quozl.linux.org.au/bp3-usb/")

The pppd session is similar for both NetworkManager (see log in post 1) and sakis (see log below) and only breaks down when trying to establish an IP address using IPCP

```
Jul 13 16:38:02 cdsa-laptop pppd[32550]: pppd options in effect:
Jul 13 16:38:02 cdsa-laptop pppd[32550]: debug#011#011# (from /etc/ppp/options)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: -detach#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: logfd -1#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: maxfail 3#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: ktune#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: dump#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: noauth#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: name cdsa-laptop#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: user user#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: password ??????#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: usehostname#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: /dev/ttyUSB1#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: 460800#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: lock#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: connect /usr/sbin/chat -v -f /tmp/pppd.tmp.29661#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: crtscts#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: modem#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: asyncmap 0#011#011# (from /etc/ppp/options)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: lcp-echo-failure 4#011#011# (from /etc/ppp/options)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: lcp-echo-interval 30#011#011# (from /etc/ppp/options)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: hide-password#011#011# (from /etc/ppp/options)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: noipdefault#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: ipcp-max-failure 30#011#011# (from /etc/ppp/options)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: defaultroute#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: proxyarp#011#011# (from /etc/ppp/options)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: usepeerdns#011#011# (from command line)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: noipx#011#011# (from /etc/ppp/options)
Jul 13 16:38:02 cdsa-laptop pppd[32550]: pppd 2.4.5 started by root, uid 0
Jul 13 16:38:03 cdsa-laptop chat[32572]: abort on (NO CARRIER)
Jul 13 16:38:03 cdsa-laptop chat[32572]: abort on (NO DIALTONE)
Jul 13 16:38:03 cdsa-laptop chat[32572]: abort on (BUSY)
Jul 13 16:38:03 cdsa-laptop chat[32572]: abort on (ERROR)
Jul 13 16:38:03 cdsa-laptop chat[32572]: abort on (NO ANSWER)
Jul 13 16:38:03 cdsa-laptop chat[32572]: send (ATZ^M)
Jul 13 16:38:03 cdsa-laptop chat[32572]: expect (OK)
Jul 13 16:38:03 cdsa-laptop chat[32572]: ATZ^M^M
Jul 13 16:38:03 cdsa-laptop chat[32572]: OK
Jul 13 16:38:03 cdsa-laptop chat[32572]:  -- got it
Jul 13 16:38:03 cdsa-laptop chat[32572]: send (ATD*99#^M)
Jul 13 16:38:03 cdsa-laptop pppd[32550]: Script /usr/sbin/chat -v -f /tmp/pppd.tmp.29661 finished (pid 32571), status = 0x0
Jul 13 16:38:03 cdsa-laptop pppd[32550]: Serial connection established.
Jul 13 16:38:03 cdsa-laptop pppd[32550]: using channel 13
Jul 13 16:38:03 cdsa-laptop pppd[32550]: Using interface ppp0
Jul 13 16:38:03 cdsa-laptop pppd[32550]: Connect: ppp0 <--> /dev/ttyUSB1
Jul 13 16:38:04 cdsa-laptop pppd[32550]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x8143d6de> <pcomp> <accomp>]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: rcvd [LCP ConfReq id=0x9 <asyncmap 0x0> <auth chap MD5> <magic 0x3c720b63> <pcomp> <accomp>]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: sent [LCP ConfAck id=0x9 <asyncmap 0x0> <auth chap MD5> <magic 0x3c720b63> <pcomp> <accomp>]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x8143d6de> <pcomp> <accomp>]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: sent [LCP EchoReq id=0x0 magic=0x8143d6de]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: rcvd [LCP DiscReq id=0xa magic=0x3c720b63]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: rcvd [CHAP Challenge id=0x1 <46a866d294f7b151723ff57a6e94187b>, name = "UMTS_CHAP_SRVR"]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: sent [CHAP Response id=0x1 <9bc8dba5b4b5d9f2521c713933b6a023>, name = "user"]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: rcvd [LCP EchoRep id=0x0 magic=0x3c720b63 81 43 d6 de]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: rcvd [CHAP Success id=0x1 ""]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: CHAP authentication succeeded
Jul 13 16:38:04 cdsa-laptop pppd[32550]: CHAP authentication succeeded
Jul 13 16:38:04 cdsa-laptop pppd[32550]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: rcvd [LCP ProtRej id=0xb 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jul 13 16:38:04 cdsa-laptop pppd[32550]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jul 13 16:38:05 cdsa-laptop pppd[32550]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 13 16:38:05 cdsa-laptop pppd[32550]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
Jul 13 16:38:06 cdsa-laptop pppd[32550]: Hangup (SIGHUP)
Jul 13 16:38:06 cdsa-laptop pppd[32550]: Modem hangup
Jul 13 16:38:06 cdsa-laptop pppd[32550]: Connection terminated.
Jul 13 16:38:07 cdsa-laptop pppd[32550]: Exit.

```

---

### Post by alexfish on 2010-07-13
hi

can you try these settings in the ppp options

Code:
sudo gedit /etc/ppp/options
look at lines 
 

# Disable negotiation of Van Jacobson style IP header compression (use
# default, i.e. no compression).
 -vj


# If this option is given, pppd will send an LCP echo-request frame to the
# peer every n seconds. Normally the peer should respond to the echo-request
# by sending an echo-reply. This option can be used with the
# lcp-echo-failure option to detect that the peer is no longer connected.

lcp-echo-interval 0

# If this option is given, pppd will presume the peer to be dead if n
# LCP echo-requests are sent without receiving a valid LCP echo-reply.
# If this happens, pppd will terminate the connection.  Use of this
# option requires a non-zero value for the lcp-echo-interval parameter.
# This option can be used to enable pppd to terminate after the physical
# connection has been broken (e.g., the modem has hung up) in
# situations where no hardware modem control lines are available.

lcp-echo-failure 0

---

### Post by jmf on 2010-07-13
Thanks Everybody - including Quozl (see private info below)

Problem solved 

I got it working with NetworkManager by editing the Network Connection
- changed the Telstra (Next G) APN from telstra.internet to telstra.bigpond
- made sure that the bigpond user name & password was correct (i.e. [email]user@bigpond.com[/email])

I got it working with sakis3g by selecting the Custom APN function
- set APN to telstra.bigpond
- set the correct bigpond user name & password

It doesn't work every time - so we've probably got the too many phones problem also

> Quozl said

The symptom you have; IPCP not completing and an argument between the
modem and pppd ... has several causes in my experience.

The most likely are:

1.  the modem has not yet attached to the radio network (the Windows
dialler supplied by Telstra checks for this before dialling, but Ubuntu
9.10 does not) ... may be fixed by allowing more time to elapse between
plugging the device in and requesting the connect,

2.  the modem has a default APN (access point name) set in stored
configuration, (the Windows dialler ignores this setting, but Ubuntu
recent versions, can't remember from when, tries to set the APN before
connection) ... may be fixed by changing the stored APN in the modem,

3.  the service you have is actually using a different APN to the
defaults that Ubuntu is using ... may be fixed by trying the alternate
APN using the Ubuntu configuration screens.

So, do you have a BigPond or a Telstra service?  Although they are the
same company, it's important to know the difference.

Do you recall which of these possible APNs is used when Windows dials?

telstra.bigpond
telstra.pcpack
telstra.datapack
telstra.internet

Only the telstra.bigpond one should be used with modems that were
associated with a BigPond service.  The network protocol is fairly
stupid and doesn't tell you *why* they refuse to give you an IP address.

Would you like to try checking the modem's stored APN?  This takes a bit
of skill or learning, but your forum posts suggest to me that you might
be up for it ...

Query the modem with this pppd chatscript:

# ask modem to respond to attention command
'' AT
# identify modem model and serial numbers
OK ATI7
# get APN profiles stored in modem
OK AT+CGDCONT?
# get PDP profiles stored in modem
OK AT$QCPDPP?
# check signal strength
OK AT+CSQ
# check attachment to network
OK AT+CGATT?
# scan for available radio networks (slow)
OK AT+COPS=?

Paste the above into a file bp3.chatscript and then activate it as root
using the chat command:

sudo /usr/sbin/chat -V -t20 -f bp3.chatscript < /dev/ttyUSB1 > /dev/ttyUSB1

The output should be instructive.  If the stored APN is odd, it might
require changing.  If the network is not attached soon after power up,
you have one of the common syndromes; too many mobile phones in the
area.


---

### Post by pdc on 2010-07-14
well done 

> I set the correct bigpond user name & password

and what are they?

---

### Post by alexfish on 2010-07-14
Most of the above can be checked out here

 

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

The Telstra APN's Posted are a big help 

will be making a link back to this thread

regards 

alexfish

---

