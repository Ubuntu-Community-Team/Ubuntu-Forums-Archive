---
title: "How I fixed Asus USB-N13 compile errors in Ubuntu 10.10"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by modal_realism on 2010-10-21
It seems with the newer linux headers, two functions changed their names slightly and caused a crash when attempting to build the Asus-provided USB-N13 drivers.

I'm still in the middle of getting the device to work, but actually compiling the driver was a major problem for me and others I've seen that complained of the breakage in 10.10.

Here's the fix:
Within the include/os/rt_linux.h and os/linux/rt_usb_util.c files, the usb_buffer_alloc and usb_buffer_free functions are part of an internal macro.  These functions do not exist anymore and are replaced by the usb_alloc_coherent and usb_free_coherent respectively.  Input parameters did not change, just the names.

The macro is defined in rt_linux.h and the functions are used in a symbol export within rt_usb_util.c.  Simply renaming the functions should allow it to build.

As I said, I'm still in the process of getting the wireless to work, just wanted to let everyone know of the quick fix.

This issue will probably be addressed with a macro fix somewhere eventually.


#define usb_alloc_coherent(a, b, c, d) usb_buffer_alloc(a, b, c, d)
#define usb_free_coherent(a, b, c, d) usb_buffer_free(a, b, c, d)

---

### Post by nickcloy on 2010-10-24
when i changed the names of the functions make works fine, but make install fails.
however a file called rt3070sta.ko is created in the os/linux folder. 
when i insmod rt3070sta.ko from that folder the driver works fine, how do i get ubuntu to load rt3070sta.ko when the computer boots?

---

### Post by modal_realism on 2010-10-27
It is added to some probe list I think.  I got it working but had a motherboard fail on me due to overheating.  I used the step by step of another thread here, involved 10.04 instructions.  Looking for it now.

I followed this one to get the basics setup.  
[http://ubuntuforums.org/showthread.php?t=1419504&highlight=asus+usb-n13](http://ubuntuforums.org/showthread.php?t=1419504&highlight=asus+usb-n13)

1) Copied RT2870STA.dat and RT2870STACard.dat to their respective RT3070* names.
2) Edited the RT3070STA.dat file as mentioned here in post #5: [http://ubuntuforums.org/showthread.php?t=1467291&highlight=usb-n13](http://ubuntuforums.org/showthread.php?t=1467291&highlight=usb-n13)
2) Made mods to files mentioned in post #1 in this thread
3) Ran sudo su, make, make install
4) Not sure if it helped, followed step #6 in post #35 here: [http://ubuntuforums.org/showthread.php?t=1419504&highlight=asus+usb-n13&page=4](http://ubuntuforums.org/showthread.php?t=1419504&highlight=asus+usb-n13&page=4)
4) ran 'ifconfig eth0 down', 'ifconfig ra0 up', 'iwlist ra0 scan'

After a few seconds, it connected to my local AP.  I rebooted and it worked fine!

Running 10.10 with the Asus USB-N13

---

### Post by Cauda_Draconis on 2010-11-10
I tried those steps, but something is still not working.
Make and make install worked.
I didn't change much in the driver's make files or anything, because I'm a non-programmer, and wasn't sure about most of it. I also changed the folder name in /etc/Wireless from RT3070STA to RT2870STA, since someone elsewhere said it worked for him/her. 
Originally, it saw the device in lsusb and nothing else - no loaded modules, and when I tried, it wouldn't let me (later discovered it was due to lack of sudo). It also didn't see the ra0 device.
I rebooted, and now it recognizes ra0 in iwconfig, but not ifconfig. The rt3070sta module shows up in lsmod, and I can create/edit a connection in Network Manager (wouldn't let me before), but it won't actually connect.

Results for lsusb after reboot:
```
name@desktop:~$ lsusb
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1c4f:0003 SiGma Micro HID controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 056a:0018 Wacom Co., Ltd Bamboo Fun 6x8
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Results for ifconfig after reboot:
```
name@computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:e7:4a:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:49 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14384 (14.3 KB)  TX bytes:14384 (14.3 KB)
```

Results for iwconfig after reboot:
```
name@computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I'm using the DPO_RT3070_LinuxSTA_V2.3.0.2_20100422 version, copied from the driver CD that came with the product.
Ubuntu 10.10, kernel 2.6.35-22-generic.

Please help!

---

