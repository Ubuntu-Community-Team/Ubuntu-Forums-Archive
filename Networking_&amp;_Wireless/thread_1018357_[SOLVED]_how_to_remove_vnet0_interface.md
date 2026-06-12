---
title: "[SOLVED] how to remove vnet0 interface?"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by vpnm_87 on 2008-12-22
when i type ifconfig i am getting vnet0 interface..i am using only ethernet interface...

can anybody tell me what that vnet0 interface is? and plz tell me a way to remove that interface

---

### Post by jpkotta on 2008-12-22
It's from vmware.  You can get rid of it with ```
sudo /etc/init.d/vmware stop
```, or use sysvconfig to disable it starting at boot.  It shouldn't be hurting anything though.

---

### Post by vpnm_87 on 2008-12-22
1) when i try to install sysvconfig i am getting this msg:

The following extra packages will be installed:
  dialog
The following packages will be REMOVED:
  apparmor apparmor-utils friendly-recovery initscripts startup-tasks
  system-services sysvinit-utils ubuntu-minimal upstart upstart-compat-sysv
  upstart-logd
The following NEW packages will be installed:
  dialog sysvconfig
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  sysvinit-utils
0 upgraded, 2 newly installed, 11 to remove and 0 not upgraded.
Need to get 282kB of archives.
After this operation, 4051kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] 

Is that normal??

2) i tried the command u gave but i got "no command found" error..there s no file called vmware in the directory u specified?


what should i do now??

---

### Post by jpkotta on 2008-12-22
Well, if that command doesn't exist there is no point in installing sysvconfig (and no, those removals don't look normal).  

So apparently you don't have vmware installed?  That is the context that I've seen such an interface in before, but it could be just a generic virtual network interface.  Are you sure you don't have any virtual machines, Xen, fancy networking things, etc., installed?

---

### Post by vpnm_87 on 2008-12-22
i am sure i dint install any VMs..but two days before i tried to create ppp0 interface using two GSM modems(dint succeed)..at that time my mobile phone ISP name was displayed in Network Connections under Mobile Broadband tab...could that be the reason for that vnet0 interface?

i posted about that ppp0 interface prob here but dint get any reply from anyone...

---

### Post by jpkotta on 2008-12-22
> **vpnm_87 said:**
> i am sure i dint install any VMs..but two days before i tried to create ppp0 interface using two GSM modems(dint succeed)..at that time my mobile phone ISP name was displayed in Network Connections under Mobile Broadband tab...could that be the reason for that vnet0 interface?


Maybe.  I don't use Network Manager, so I can't say.  This will give you a pretty good idea:
```
ls -l /sys/class/net/
```

```
total 0
lrwxrwxrwx 1 root root 0 2008-12-22 20:05 eth0 -> ../../devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eth0/
lrwxrwxrwx 1 root root 0 2008-12-22 20:05 lo -> ../../devices/virtual/net/lo/
lrwxrwxrwx 1 root root 0 2008-12-22 20:05 pan0 -> ../../devices/virtual/net/pan0/
lrwxrwxrwx 1 root root 0 2008-12-22 20:05 vmnet1 -> ../../devices/virtual/net/vmnet1/
lrwxrwxrwx 1 root root 0 2008-12-22 20:05 vmnet8 -> ../../devices/virtual/net/vmnet8/
```

My only physical network device is eth0, and you can see it is on the PCI bus.  The rest are virtual, and the links show this.

---

### Post by vpnm_87 on 2008-12-23
i got the same output for the ls -l /sys/class/net(except vnet0 instead of ur vmnet).....

i referred [http://www.sunmanagers.org/archives/2000/1036.html](http://www.sunmanagers.org/archives/2000/1036.html) and found out the solution for my problem..

ifconfig vnet0 down.....thats it...if u think that might cause some prob then plz let me know...coz they gave some unplumb command that dint worked for me..

but now i am not seein that vnet0 in my ifconfig list.....to see that again i gave (ifconfig vnet0 up)

anyway thanks for ur suggestions and guidance...

---

### Post by thyarles on 2009-01-16
Hi,

If it is still useful, just use the command: **sudo apt-get remove libvirt-bin**

[]'s
Charles Henrique

---

