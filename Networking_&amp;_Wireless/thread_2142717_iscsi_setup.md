---
title: "iscsi setup"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by leftcranium on 2013-05-06
The issue:
I had iscsi working on my box in the 10.X days. But I can't seem to recreate it on a 12.X or 13.04 release. I'm currently able to connect to iscsi target from my windows system.

The setup:
Here is what I've done and the error I get. 

root@las52823:~# iscsiadm -m node
iscsiadm: No records found
root@las52823:~# /etc/init.d/open-iscsi restart
 * Unmounting iscsi-backed filesystems                                                                                                                   [ OK ]
 * Disconnecting iSCSI targets                                                                                                                                  iscsiadm: No matching sessions found
                                                                                                                                                         [ OK ]
 * Stopping iSCSI initiator service                                                                                                                      [ OK ]
 * Starting iSCSI initiator service iscsid                                                                                                               [ OK ]
 * Setting up iSCSI targets
iscsiadm: No records found
                                                                                                                                                         [ OK ]
 * Mounting network filesystems                                                                                                                          [ OK ]
root@las52823:~# iscsiadm -m discovery -t st -p 172.17.224.24
172.17.224.24:3260,1 iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252
root@las52823:~# iscsiadm -m discovery -t st -p 172.17.224.25
172.17.224.25:3260,1 iqn.1986-03.com.ibm:2145.nvenergy-svc4.node6160644
root@las52823:~#  iscsiadm -m node
172.17.224.24:3260,1 iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252
172.17.224.25:3260,1 iqn.1986-03.com.ibm:2145.nvenergy-svc4.node6160644


root@las52823:~# iscsiadm -m node --targetname iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252 --portal "172.17.224.24:3260" --login
Logging in to [iface: default, target: iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252, portal: 172.17.224.24,3260] (multiple)
iscsiadm: Could not login to [iface: default, target: iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252, portal: 172.17.224.24,3260].
iscsiadm: initiator reported error (8 - connection timed out)
iscsiadm: Could not log into all portals

root@las52823:~# /etc/init.d/open-iscsi restart
 * Unmounting iscsi-backed filesystems                                                                                                                   [ OK ]
 * Disconnecting iSCSI targets                                                                                                                                  iscsiadm: No matching sessions found
                                                                                                                                                         [ OK ]
 * Stopping iSCSI initiator service                                                                                                                      [ OK ]
 * Starting iSCSI initiator service iscsid                                                                                                               [ OK ]
 * Setting up iSCSI targets
Logging in to [iface: default, target: iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252, portal: 172.17.224.24,3260] (multiple)
Logging in to [iface: default, target: iqn.1986-03.com.ibm:2145.nvenergy-svc4.node6160644, portal: 172.17.224.25,3260] (multiple)
iscsiadm: Could not login to [iface: default, target: iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252, portal: 172.17.224.24,3260].
iscsiadm: initiator reported error (8 - connection timed out)
iscsiadm: Could not login to [iface: default, target: iqn.1986-03.com.ibm:2145.nvenergy-svc4.node6160644, portal: 172.17.224.25,3260].
iscsiadm: initiator reported error (8 - connection timed out)
iscsiadm: Could not log into all portals

dmesg:
[837315.380097] Loading iSCSI transport class v2.0-870.
[837315.390461] iscsi: registered transport (tcp)
[837315.422561] iscsi: registered transport (iser)
[837315.692503] scsi25 : iSCSI Initiator over TCP/IP
[837315.697552] scsi26 : iSCSI Initiator over TCP/IP
[837315.697940]  connection1:0: detected conn error (1020)
[837315.702489]  connection2:0: detected conn error (1020)
[837333.699396]  connection2:0: detected conn error (1020)
[837333.699409]  connection1:0: detected conn error (1020)
[837350.946530]  connection2:0: detected conn error (1020)
[837350.946549]  connection1:0: detected conn error (1020)
[837368.193817]  connection2:0: detected conn error (1020)
[837368.193836]  connection1:0: detected conn error (1020)
[837385.441058]  connection1:0: detected conn error (1020)
[837385.441077]  connection2:0: detected conn error (1020)
[837402.688271]  connection2:0: detected conn error (1020)
[837402.688284]  connection1:0: detected conn error (1020)
[837419.935594]  connection2:0: detected conn error (1020)
[837419.935613]  connection1:0: detected conn error (1020)


                                                                                                                                                         [ OK ]
root@las52823:~# cat /etc/os-release
NAME="Ubuntu"
VERSION="13.04, Raring Ringtail"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 13.04"
VERSION_ID="13.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

root@las52823:~# dpkg -l *iscsi*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                               Version                Architecture           Description
+++-==================================-======================-======================-=========================================================================
ii  iscsitarget                        1.4.20.2-10ubuntu2     amd64                  iSCSI Enterprise Target userland tools
ii  iscsitarget-dkms                   1.4.20.2-10ubuntu2     all                    iSCSI Enterprise Target kernel module source - dkms version
un  iscsitarget-module                 <none>                                        (no description available)
in  iscsitarget-source                 <none>                 all                    (no description available)
ii  open-iscsi                         2.0.873-3ubuntu5       amd64                  High performance, transport independent iSCSI implementation
ii  open-iscsi-utils                   2.0.873-3ubuntu5       all                    transitional dummy package




I'm guessing it's something simple but don't know what else to try.
thanks

---

### Post by aromo on 2013-05-06
try this first:
```
iscsiadm -m discovery -t st -p *<iscsi_host>*
```
It should give you the iqn to connect to.

---

### Post by leftcranium on 2013-05-06
> **aromo said:**
> try this first:
```
iscsiadm -m discovery -t st -p *<iscsi_host>*
```
It should give you the iqn to connect to.

Here is the output. It seems the failure is only on login.

root@las52823:~# iscsiadm -m discovery -t st -p 172.17.224.24
172.17.224.24:3260,1 iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252
root@las52823:~# iscsiadm -m discovery -t st -p 172.17.224.25
172.17.224.25:3260,1 iqn.1986-03.com.ibm:2145.nvenergy-svc4.node6160644

---

### Post by aromo on 2013-05-06
Try:
```
iscsiadm -m node -T *<iqn>* -l
```

---

### Post by leftcranium on 2013-05-06
root@las52823:~# iscsiadm -m node -T iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252 -l
Logging in to [iface: default, target: iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252, portal: 172.17.224.24,3260] (multiple)
iscsiadm: Could not login to [iface: default, target: iqn.1986-03.com.ibm:2145.nvenergy-svc4.node5161252, portal: 172.17.224.24,3260].
iscsiadm: initiator reported error (8 - connection timed out)
iscsiadm: Could not log into all portals
root@las52823:~#

thanks

---

### Post by aromo on 2013-05-09
is there a firewall in between?  is iptables disabled on your machine?

---

### Post by leftcranium on 2013-05-09
no firewall, iptables is set to accept.

root@las52823:~# iptables -L -v
Chain INPUT (policy ACCEPT 766 packets, 62521 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 284 packets, 65964 bytes)
 pkts bytes target     prot opt in     out     source               destination

---

