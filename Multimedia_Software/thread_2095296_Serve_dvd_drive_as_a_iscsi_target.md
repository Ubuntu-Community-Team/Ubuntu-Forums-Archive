---
title: "Serve dvd drive as a iscsi target"
date: 2012-12-16
forum: Multimedia Software
---

### Post by aasgaa on 2012-12-16
I'm running a Ubuntu 12.04 desktop with a local dvd drive. Playing dvd's locally on this pc works fine.
 
I have installed tgt and added a target with the dvd drive as a LUN:
$ apt-get install tgt
$ apt-get install open-iscsi-utils
 
# Add target
$ tgtadm --lld iscsi --op new --mode target --tid 1 -T iqn.2012-12.com.example.iscsi:tgt:4:16:0:0:T
 
# Add dvd as a LUN
$ tgtadm --lld iscsi --op new --mode logicalunit --tid 1 --lun 1 --bstype=sg --device-type=pt -b /dev/sg0
 
# Enable the target to accept any initiators
$ tgtadm --lld iscsi --op bind --mode target --tid 1 -I ALL
 
On another pc with ubuntu 12.04 desktop - without a physical dvd-drive I have installed open-iscsi and connected to the remote dvd:
$ apt-get install open-iscsi
$ apt-get install open-iscsi-utils
$ apt-get install lsscsi
 
$ iscsiadm --mode discovery --type sendtargets --portal iscsi.hds.local
$ iscsiadm --mode node --targetname iqn.2012-12.com.example.iscsi:tgt:4:16:0:0:T --portal 192.168.1.135:3260 --login
 
The remote dvd drive shows up and a some (a few) dvd's play perfectly. 
However, most of the dvd's that play fine on the pc with local dvd, fails when played on the pc with the iscsi connection to the remote dvd drive.
 
In syslog I find a lot of these entries:
Dec 16 18:38:41 xbmc01 kernel: [247404.245683] end_request: I/O error, dev sr2, sector 13025132
Dec 16 18:38:41 xbmc01 kernel: [247404.269439] sr 4:0:0:1: [sr2] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 16 18:38:41 xbmc01 kernel: [247404.269450] sr 4:0:0:1: [sr2] Sense Key : Illegal Request [current]
Dec 16 18:38:41 xbmc01 kernel: [247404.269460] sr 4:0:0:1: [sr2] Add. Sense: Read of scrambled sector without authentication
Dec 16 18:38:41 xbmc01 kernel: [247404.269472] sr 4:0:0:1: [sr2] CDB: Read(10): 28 00 00 31 af db 00 00 02 00
 
I have also tried to set up a dvd as a iscsi target on a third pc and connected to the first one that can play the dvd's locally. Same problem.
 
Any ideas how to proceed from here?

---

### Post by aasgaa on 2012-12-17
Bump...

---

