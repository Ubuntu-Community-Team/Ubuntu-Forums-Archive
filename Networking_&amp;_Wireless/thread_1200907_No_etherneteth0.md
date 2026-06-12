---
title: "No ethernet/eth0"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by hajduk on 2009-06-30
Hello,

Ever since upgrading to 9.04 a few months ago, I have been having issues with my wired ethernet. When booting up, it fails to connect to my wired internet, and running commands in the terminal showed me that there was no eth0 entry.

```
~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20300 (20.3 KB)  TX bytes:20300 (20.3 KB)

pan0      Link encap:Ethernet  HWaddr fe:9b:bf:2f:15:c6  
          inet6 addr: fe80::fc9b:bfff:fe2f:15c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1620 (1.6 KB)

```

```
~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=56 mingnt=8

```

```
~$ lspci
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

```

Running dmesg, it seems to have showed me that my driver corrupted, and I tried adding an exception to /etc/modules, to no avail.

```
[    5.087605] e100: 0000:03:08.0: e100_eeprom_load: EEPROM corrupted
[    5.087663] e100 0000:03:08.0: PCI INT A disabled
[    5.087672] e100: probe of 0000:03:08.0 failed with error -11

```

Hopefully somebody can help me fix this issue.

---

### Post by pytheas22 on 2009-06-30
This seems to be a recurring issue (see [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/30666") from a long time ago).

If you remove the e100 module by typing:
```

sudo rmmod e100
```

then reinsert with special options appended:
```

sudo modprobe e100 eeprom_bad_csum_allow=1
```

does it work?  Or do you get the same error message in dmesg?

---

### Post by hajduk on 2009-06-30
Now I get this:

```
[ 5635.340710] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[ 5635.340714] e100: Copyright(c) 1999-2006 Intel Corporation
[ 5635.340777] e100 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 5635.341097] e100: 0000:03:08.0: e100_eeprom_load: EEPROM corrupted
[ 5635.341944] e100: 0000:03:08.0: e100_probe: Invalid MAC address from EEPROM, you MUST configure one.
[ 5635.341952] e100 0000:03:08.0: PME# disabled
[ 5635.343275] e100: eth0: e100_probe: addr 0xefbef000, irq 20, MAC addr 00:00:00:00:00:00

```

---

### Post by pytheas22 on 2009-06-30
That's weird.  Is eth0 brought up anyway, or does 'lshw -C Network' still show your device as unclaimed?  If the device is brought up but with an invalid MAC address, it might work just to spoof a legitimate one, e.g.:
```

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:AB:CD:EF:01:23
sudo ifconfig eth0 up
```

Not the cleanest of solutions, but it would probably work if the device is being brought up at all.

It may also help to power down your machine completely, remove the battery if applicable, unplug the power cord for a couple minutes, then reboot into Ubuntu.  If the NIC is in some kind of strange state, which happens sometimes, cutting off power completely will force it to reset.

If none of the above helps, we'll have to google some more.

---

### Post by hajduk on 2009-06-30
Device isn't being brought up, and i tried powering down, but to no avail. The commands you gave only gave errors.

---

### Post by hajduk on 2009-06-30
bump

---

### Post by pytheas22 on 2009-07-01
Sorry for the slow response--I was sleeping then working all day.

My next suggestion would be to try using the e1000 driver instead of e100.  It might support your device.  To try it, run:
```

sudo rmmod e100
sudo rmmod e1000
sudo modprobe e1000
```

Then check 'dmesg' and 'ifconfig' to see if a device has been brought up.

If this doesn't work, I think you should try compiling the e100 driver from source.  Hopefully a custom-compiled driver will work better than the generic one that ships with Ubuntu.  Unfortunately, I tried building the e100 driver using the source code on [Intel's site]("http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=61&DwnldID=2896&agr=Y&lang=eng") and it wouldn't compile on my 32-bit Jaunty machine, but I didn't try that hard to work through the errors; I'm sure we can get it to compile if necessary.

Finally, it would be helpful if you could post the output of:
```

lspci -nn | grep Ethernet
```

so I'll know the PCI ID number for your device (the PCI ID is a hexadecimal numer in the forum XXXX:XXXX, and you need to run 'lspci' with the '-nn' argument to get it).

---

### Post by hajduk on 2009-07-02
Sorry for my late response. Compiling of a custom driver failed, as it gave a CFLAGS error. However, this is what 'lspci -nn | grep Ethernet' gave me:

```
$ lspci -nn | grep Ethernet
03:08.0 Ethernet controller [0200]: Intel Corporation 82801G (ICH7 Family) LAN Controller [8086:27dc] (rev 01)

```

Trying the e1000 driver, no eth0 appeared in ifconfig, nor I did see any message regarding the driver in dmesg.

---

### Post by pytheas22 on 2009-07-03
I'm thinking another possible solution would be to use ndiswrapper to drive the device, in order to work around the bug with the native Linux driver thinking your csum is bad.  ndiswrapper is usually used for wireless cards, but in principle it works with ethernet too; I've done it successfully before a couple of times.

To get the card going with ndiswrapper, run these commands:
```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://www.burnthesorbonne.com/files/pro100_ethernet_win32.tar.gz
tar -xzvf pro100_ethernet_win32.tar.gz 
sudo ndiswrapper -i Win32/e100b325.inf
```

To activate ndiswrapper, you will need to remove the native Linux driver and insert the ndiswrapper module by typing:
```

sudo rmmod e100
sudo rmmod e1000
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

At this point, your ethernet device will hopefully be up and working.  If it's not, please let me know the output of:
```

dmesg | grep -e eth -e ndis
ndiswrapper -l
```

If this does work, we can activate ndiswrapper permanently (for the time being, it will only take control of the card when you insert it manually).

Also note that the instructions above assume you're running 32-bit Ubuntu; if you're on 64-bit, let me know.

---

### Post by hajduk on 2009-07-03
Tried your instructions, but that failed to kick start the ethernet. I'm still getting the corrupt driver error.

---

### Post by pytheas22 on 2009-07-03
The corrupt driver error will still appear in dmesg from the first time the driver loaded.  But it would be good to see the output of:
```

dmesg | grep -e ndis -e eth
ndiswrapper -l
lshw -C Network
```

to see what's going on with ndiswrapper.

---

### Post by Panayotis689 on 2009-07-26
Hi

I have a similar problem with my old Inspiron 8100 laptop with an Intel 82557 Ethernet Card!

I have just install properly 9.04. Everything was fine except i don't have internet,  do not have ETHERNET at all!

Please have a look and tell me what to do! I do not have a wireless card inside, just Ethernet!
> 
stephane@stephane-inspiron8100:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 08
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=56 mingnt=8
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0e:c6:81:bc:14:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
stephane@stephane-inspiron8100:~$  > 815.457598] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[  815.457605] e100: Copyright(c) 1999-2006 Intel Corporation
[  815.457694] e100 0000:08:04.0: PCI INT A -> Link[LNKD] -> GSI 10 (level, low) -> IRQ 10
[  815.458041] e100: 0000:08:04.0: e100_eeprom_load: EEPROM corrupted
[  815.458062] e100 0000:08:04.0: PCI INT A disabled
[  815.458076] e100: probe of 0000:08:04.0 failed with error -11
> stephane@stephane-inspiron8100:~$ lsmod | grep 100
e100                   41740  0 
output                 11008  1 video
parport_pc             40100  1 
mii                    13312  1 e100
stephane@stephane-inspiron8100:~$ Any idea? I have heard about 2 modules for my Ethernet Card: e100 (a new and defective one) and the old one ee100.

What do you think?

Thanks for your help

---

### Post by pytheas22 on 2009-07-26
Panayotis689: it does like you have the same issues as the original poster in this thread.  Please try working through the solutions suggested on the first page of the thread and let me know if any of them help.  If not, we can try some other things.

---

### Post by komodojay on 2009-08-11
I don't have the exact problem but on my 8100 with Intel pro 100 82557 I can ping the internet and websites but can not load any web pages. Any suggestions for that?

---

### Post by pytheas22 on 2009-08-11
komodojay: that problem sounds a bit different.  One possible reason is your DNS server not working; another is a problem with the web browser.  If you could please post the output of these commands, it would help to pinpoint the problem:
```

ifconfig
ping -c 5 google.com
ping -c 5 74.125.127.100
wget google.com
wget 74.125.127.100
cat /etc/resolv.conf
cat /etc/hosts
```

---

### Post by Iowan on 2009-08-12
> **komodojay said:**
> I don't have the exact problem but on my 8100 with Intel pro 100 82557 I can ping the internet and websites but can not load any web pages. Any suggestions for that?A separate thread would probably be in your best interest.

---

### Post by tomicide on 2010-06-18
> **pytheas22 said:**
> This seems to be a recurring issue (see [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/30666") from a long time ago).

If you remove the e100 module by typing:
```

sudo rmmod e100
```

then reinsert with special options appended:
```

sudo modprobe e100 eeprom_bad_csum_allow=1
```

does it work?  Or do you get the same error message in dmesg?
**thanks alot...** this fixed my compaq armada v300

---

