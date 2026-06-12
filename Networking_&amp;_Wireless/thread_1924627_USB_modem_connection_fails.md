---
title: "USB modem connection fails"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by beparas on 2012-02-13
Hi all,

I am having D-Link DWM-156 USB adapter.
I am trying to  connect to internet using this modem by using pppd command but it get  fails. But I can connect the internet using "NetworkManager Applet". :(

The steps are given below.

I did usb_modswitch successfully, then install "option" driver by
> 
$ modprobe -v option


and redirect vid,pid to "/sys/bus/usb-serial/drivers/option1/new_id" file.
> 
$ echo "2001 7d00" > /sys/bus/usb-serial/drivers/option1/new_id


> 
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04b3:3025 IBM Corp.
Bus 002 Device 002: ID 17ef:6019 Lenovo
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 2001:7d00 D-Link Corp. [hex]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> 
$  dmesg  | grep tty
[ 4900.049637] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[ 4900.049978] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[ 4900.050243] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2


> 
$  pppd /dev/ttyUSB0 115200 modem connect "/usr/sbin/chat -v -f  /root/connt" defaultroute nodetach ipcp-accept-remote novj mru 1500 mtu  1500 noipdefault usepeerdns user "" password ""

 when I run this command gets error:
"Connect script failed"

So I add the entry in "NetworkManager Applet" under "Mobile Broadband".
and get connected through this. 

Here is output of syslogd
> 
$ cat /var/log/syslog | grep tty
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Vodafone Default'
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Feb 13 12:57:19 paras-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/3: state changed (registered -> connecting)
Feb 13 12:57:19 paras-desktop modem-manager: Modem /org/freedesktop/ModemManager/Modems/3: state changed (connecting -> connected)
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 (reason 0)
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 7 (reason 0)
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Starting pppd connection
Feb  13 12:57:19 paras-desktop NetworkManager: <debug>  [1329118039.274523] nm_ppp_manager_start(): Command line: /usr/sbin/pppd  nodetach lock nodefaultroute ttyUSB0 noipdefault noauth usepeerdns  lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/4 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Feb 13 12:57:19 paras-desktop NetworkManager: <debug>  [1329118039.276538] nm_ppp_manager_start(): ppp started with pid 3980
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) started...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) complete.
Feb 13 12:57:19 paras-desktop pppd[3980]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Feb 13 12:57:19 paras-desktop pppd[3980]: pppd 2.4.5 started by root, uid 0
Feb  13 12:57:19 paras-desktop NetworkManager:    SCPlugin-Ifupdown: devices  added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb 13  12:57:19 paras-desktop NetworkManager:    SCPlugin-Ifupdown: device  added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown  configuration found.
Feb 13 12:57:19 paras-desktop pppd[3980]: Using interface ppp0
Feb 13 12:57:19 paras-desktop pppd[3980]: Connect: ppp0 <--> /dev/ttyUSB0
Feb 13 12:57:19 paras-desktop pppd[3980]: PAP authentication succeeded
Feb 13 12:57:19 paras-desktop pppd[3980]: Could not determine remote IP address: defaulting to 10.64.64.64
Feb 13 12:57:19 paras-desktop pppd[3980]: Cannot determine ethernet address for proxy ARP
Feb 13 12:57:19 paras-desktop pppd[3980]: local  IP address 42.104.15.166
Feb 13 12:57:19 paras-desktop pppd[3980]: remote IP address 10.64.64.64
Feb 13 12:57:19 paras-desktop pppd[3980]: primary   DNS address 10.11.230.2
Feb 13 12:57:19 paras-desktop pppd[3980]: secondary DNS address 10.11.230.3
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  PPP manager(IP Config Get) reply received.
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled...
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 13 12:57:19 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started...
Feb 13 12:57:20 paras-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Feb 13 12:57:20 paras-desktop NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 8 (reason 0)
Feb 13 12:57:20 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) successful, device activated.
Feb 13 12:57:20 paras-desktop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 13 12:57:26 paras-desktop ntpdate[4035]: no server suitable for synchronization found
Feb 13 12:57:40 paras-desktop NetworkManager: <info>  (ttyUSB0): device state change: 8 -> 3 (reason 39)
Feb 13 12:57:40 paras-desktop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 39).
Feb 13 12:57:40 paras-desktop pppd[3980]: Terminating on signal 15
Feb 13 12:57:40 paras-desktop pppd[3980]: Connect time 0.4 minutes.
Feb 13 12:57:40 paras-desktop pppd[3980]: Sent 0 bytes, received 0 bytes.
Feb 13 12:57:40 paras-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.


and log for pppd is
> 
$ tail /var/log/systemd
Feb 13 13:00:14 paras-desktop pppd[4094]: pppd 2.4.5 started by paras, uid 0
Feb 13 13:00:15 paras-desktop chat[4096]: timeout set to 10 seconds
Feb 13 13:00:15 paras-desktop chat[4096]: abort on (\nBUSY\r)
Feb 13 13:00:15 paras-desktop chat[4096]: abort on (\nERROR\r)
Feb 13 13:00:15 paras-desktop chat[4096]: abort on (\nNO ANSWER\r)
Feb 13 13:00:15 paras-desktop chat[4096]: abort on (\nNO CARRIER\r)
Feb 13 13:00:15 paras-desktop chat[4096]: abort on (\nNO DIALTONE\r)
Feb 13 13:00:15 paras-desktop chat[4096]: abort on (\nRINGING\r\n\r\nRINGING\r)
Feb 13 13:00:15 paras-desktop chat[4096]: send (^MAT^M)
Feb 13 13:00:15 paras-desktop chat[4096]: timeout set to 12 seconds
Feb 13 13:00:15 paras-desktop chat[4096]: expect (OK)
Feb 13 13:00:15 paras-desktop chat[4096]: ^M
Feb 13 13:00:27 paras-desktop chat[4096]: alarm
Feb 13 13:00:27 paras-desktop chat[4096]: Failed
Feb 13 13:00:27 paras-desktop pppd[4094]: Connect script failed
Feb 13 13:00:28 paras-desktop pppd[4094]: Exit.


Connection script is 
> 
cat /root/connt

TIMEOUT         10
ECHO            ON
ABORT           '\nBUSY\r'
ABORT           '\nERROR\r'
ABORT           '\nNO ANSWER\r'
ABORT           '\nNO CARRIER\r'
ABORT           '\nNO DIALTONE\r'
ABORT           '\nRINGING\r\n\r\nRINGING\r'
''              \rAT
TIMEOUT         12
OK              ATE1
OK              'AT+cgdcont=1,"IP","www","",0,0'
OK              ATDT*99#\
CONNECT


I am working on Ubuntu-10.4

Please help me whether I debug this issue. 

Thanks In advance. 

Paras

---

