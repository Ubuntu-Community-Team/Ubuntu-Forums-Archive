---
title: "Setting up networking in qemu (kvm) guest"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by makowka on 2011-12-02
Hi

I have a problem with getting the network connected on a winxp guest. I have a computer with network being assigned by dhcp on eth0. Now, I copied the following script:

```
#!/bin/sh 
# 
# script to bring up the tun device in QEMU in bridged mode
# first parameter is name of tap device (e.g. tap0)
#
# some constants specific to the local host - change to suit your host
#
ETH0IP=xx.xx.xx.xx
GATEWAY=xx.xx.xx.xx
BROADCAST=xx.xx.xx.xx
#
# First take eth0 down, then bring it up with IP 0.0.0.0 
#
/sbin/ifdown eth0
/sbin/ifconfig eth0 0.0.0.0 promisc up
#
# Bring up the tap device (name specified as first argument, by QEMU)
#
/usr/sbin/openvpn --mktun --dev $1 --user `id -un` --lladdr 00:02:44:30:17:17
/sbin/ifconfig $1 0.0.0.0 promisc up
#
# create the bridge between eth0 and the tap device
#
/usr/sbin/brctl addbr br0
/usr/sbin/brctl addif br0 eth0
/usr/sbin/brctl addif br0 $1
# 
# only a single bridge so loops are not possible, turn off spanning tree protoco                                             
l
#
/usr/sbin/brctl stp br0 off 
# 
# Bring up the bridge with ETH0IP and add the default route 
#
/sbin/ifconfig br0 $ETH0IP netmask 255.255.255.224 broadcast $BROADCAST
/sbin/route add default gw $GATEWAY
```The values for ETH0IP, GATEWAY and BROADCAST are obtained from ifconfig and route -n commands. I start the VM guest with the following command:

```
kvm -m 700 -boot c -hda /media/disk/winxp.qcow -net nic -net tap,ifname=tap0,script=no
```As you can see, I assign the same mac address to the guest as it is on the host (that is, because my ISP delivers the connection upon the correct mac address). 
Nevertheless, the guest doesn't make a connection. I am stucked on the windows activation screen, which tries to automatically establish a connection. I tried it with the command:

```
kvm -m 700 -boot c -hda /media/disk/winxp.qcow -net nic,macaddr=00:02:44:30:17:17 -net user
```but it does't help. Can anyone give me an advice? I can't configure the connection on the guest, because I can't login before I haven't activated windows.

---

