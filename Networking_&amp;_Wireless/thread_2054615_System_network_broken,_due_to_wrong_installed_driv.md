---
title: "System network broken, due to wrong installed driver (need help fast)"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by Wouser on 2012-09-07
In my search for fixing the issue I posted here, [http://ubuntuforums.org/showthread.php?t=2052425](http://ubuntuforums.org/showthread.php?t=2052425), I thought that it might be a good idea to update the drivers.

I have a "Intel 82567LM Gigabit Network Connection" and "Intel Wifi Link 5100 AGN" I went to search for linux drivers. I then found this driver, [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng&OSVersion=Linux*&DownloadType=Drivers](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng&OSVersion=Linux*&DownloadType=Drivers). I installed it. Now after a reboot I find out my network connection is broken and can not get access to internet anymore. It seems the driver is incompatible :(

Now is it possible to fix this issue? I really need help with this asap! Because I really need internet, and rather do not want to reinstall my complete system.

Relevant images: 
[img]http://i.stack.imgur.com/xLcgY.jpg

[img]http://i.stack.imgur.com/k6qFN.jpg networking drivers connection intel-wireless

---

### Post by chili555 on 2012-09-07
If you installed it with make, sudo make install, etc., you can go back as before and do:```
cd Desktop/e1000edirectory [COLOR="Red"]<--or wherever you extracted the file[/COLOR]
sudo make uninstall
sudo modprobe -r e1000e
sudo modprobe e1000e
```e1000e is a wired ethernet driver. How would it help your wireless stay on 5 Ghz?

I'm confused.

---

### Post by Wouser on 2012-09-08
> **chili555 said:**
> If you installed it with make, sudo make install, etc., you can go back as before and do:```
cd Desktop/e1000edirectory [COLOR="Red"]<--or wherever you extracted the file[/COLOR]
sudo make uninstall
sudo modprobe -r e1000e
sudo modprobe e1000e
```e1000e is a wired ethernet driver. How would it help your wireless stay on 5 Ghz?

I'm confused.

Sorry but that didn't work :'(

---

### Post by chili555 on 2012-09-08
> e1000e is a wired ethernet driver. How would it help your wireless stay on 5 Ghz?

I'm confused.I'm *STILL* confused. What are you trying to get working, wired or wireless? Which is not connecting on boot?

---

### Post by Wouser on 2012-09-08
> **chili555 said:**
> I'm *STILL* confused. What are you trying to get working, wired or wireless? Which is not connecting on boot?

I'm trying to fix wired, as well as wireless...

I installed that driver because I thought it was the corrent one. Apparently I was wrong, probably misread.

---

### Post by chili555 on 2012-09-08
I'm sorry I guess I haven't made myself at all clear. When you boot your computer and the message pops up 'waiting for network configuration' and it waits and waits and fails, is it because the ethernet is hooked up but not working, or is it because the ethernet is *NOT* hooked up and the wireless is not properly working? Which is your priority? Fixing one will greatly help us fix the other if we need to download something.

I wish I was smart enough to fix your wired, wireless, video, card reader and the fuel pump on your VW all at once, but I'm not. I'm old and slow.

So, what's first?

---

### Post by Wouser on 2012-09-08
> **chili555 said:**
> I'm sorry I guess I haven't made myself at all clear. When you boot your computer and the message pops up 'waiting for network configuration' and it waits and waits and fails, is it because the ethernet is hooked up but not working, or is it because the ethernet is *NOT* hooked up and the wireless is not properly working? Which is your priority? Fixing one will greatly help us fix the other if we need to download something.

I wish I was smart enough to fix your wired, wireless, video, card reader and the fuel pump on your VW all at once, but I'm not. I'm old and slow.

So, what's first?

Ah okay well I will go for the wired then of course at first. I did not try yet to hook up the ethernet before startup. I always have connection by wireless. I will try now.

---

### Post by Wouser on 2012-09-08
I just tried to start my system with the Ethernet Cable attached. Unfortunately I did not have any connection. It is still the same with the same messages.

---

### Post by chili555 on 2012-09-08
For the moment, let's concentrate on wired. Let's see what the message logs have to report. Please run and post:```
dmesg | grep -e e100 -e eth0
```Leave the ethernet plugged in while we troubleshoot, please.

---

### Post by Wouser on 2012-09-08
> **chili555 said:**
> For the moment, let's concentrate on wired. Let's see what the message logs have to report. Please run and post:```
dmesg | grep -e e100 -e eth0
```Leave the ethernet plugged in while we troubleshoot, please.

[img]http://www.imgdumper.nl/uploads6/504b420b3f840/504b420a93c09-20120908_150133.jpg[/img]

---

### Post by greatsirkain on 2012-09-08
that photo made my brain hurt, might seem like a daft question but have you checked that after you made changes to the device that it has the correct network information ie password etc?

---

### Post by Wouser on 2012-09-08
No because I could not get to any settings anymore. See the second picture on the forum. And sorry yhe image hurt your eyes but I only have one computer. And switching from usb OS to the OS i have on the pc it takes to much time.

---

### Post by greatsirkain on 2012-09-08
was there an uninstall script that came with the driver? If not you could try looking in additional drivers in the settings menu and see if you can get rid of it from there.
could also try some things found here [http://ubuntuforums.org/showthread.php?t=838345](http://ubuntuforums.org/showthread.php?t=838345)
such as: sudo /etc/init.d/networking restart 
Which is also what I found when looking around for a way to reset network drivers

---

### Post by chili555 on 2012-09-08
First, he needs no password with wired ethernet. Second, he already ran the uninstall script. Third, the original installed e1000e is what is now loading. Note in the brain hurting photo it says version 1.5.1-k. Here is modinfo from my stock machine:```
$ modinfo e1000e
filename:       /lib/modules/3.2.0-30-generic-pae/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        [COLOR="Red"]1.5.1-k[/COLOR]
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
<snip>
```So we know the original is now back in place. It is obviously not connecting for some other reason(s). 

Please click the Network Manager icon, Edit Connections and see if there are any extra settings you added in either or both wired or wireless. I am concerned about the ADDRCONF entry above. If there are any settings you added, remove them. NM ought to find and connect to your network without any human intervention.

I would like to see some additional diagnostics. Rather than a huge photo, I suggest you put the results into a text document and transfer it to a USB key so you can then post it here after you boot into another computer. Please do:```
sudo cat /var/log/syslog | grep -e eth0 -e e100 -e etwork | tail -n25 > wouser.txt
```Now look in your user directory and find the text file wouser.txt, drag it to your USB key and post it here.

---

### Post by Wouser on 2012-09-08
```
Sep  9 00:36:42 wouter-tablet kernel: [    1.403910] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Sep  9 00:36:42 wouter-tablet kernel: [    1.403921] e1000e 0000:00:19.0: setting latency timer to 64
Sep  9 00:36:42 wouter-tablet kernel: [    1.417897] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
Sep  9 00:36:42 wouter-tablet kernel: [    1.610501] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:23:18:b0:b4:80
Sep  9 00:36:42 wouter-tablet kernel: [    1.610505] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Sep  9 00:36:42 wouter-tablet kernel: [    1.610533] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: FFFFFF-0FF
Sep  9 00:36:42 wouter-tablet kernel: [   24.734168] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep  9 00:36:42 wouter-tablet kernel: [   25.049333] type=1400 audit(1347143801.522:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=592 comm="apparmor_parser"
Sep  9 00:36:42 wouter-tablet kernel: [   25.087581] init: network-interface (eth0) pre-start process (598) terminated with status 1
Sep  9 00:36:42 wouter-tablet kernel: [   25.115591] init: network-interface (eth0) post-stop process (615) terminated with status 1
Sep  9 00:36:42 wouter-tablet kernel: [   25.272236] init: network-interface (lo) pre-start process (688) terminated with status 1
Sep  9 00:36:42 wouter-tablet kernel: [   25.280912] init: network-interface (lo) post-stop process (720) terminated with status 1
Sep  9 00:36:42 wouter-tablet kernel: [   25.399005] cdc_ether 1-4:1.7: wwan0: register 'cdc_ether' at usb-0000:00:1a.7-4, Mobile Broadband Network Device, 02:80:37:ec:02:00
Sep  9 00:36:42 wouter-tablet kernel: [   25.623931] init: network-interface (wwan0) pre-start process (790) terminated with status 1
Sep  9 00:36:42 wouter-tablet kernel: [   25.626514] init: network-interface (wwan0) post-stop process (805) terminated with status 1
Sep  9 00:36:42 wouter-tablet kernel: [   25.645335] init: network-interface (wlan0) pre-start process (822) terminated with status 1
Sep  9 00:36:42 wouter-tablet kernel: [   25.702673] init: network-interface (wlan0) post-stop process (835) terminated with status 1
Sep  9 00:36:43 wouter-tablet kernel: [   26.663179] init: networking main process (962) terminated with status 1
Sep  9 00:38:42 wouter-tablet kernel: [  145.797116] type=1400 audit(1347143922.270:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1012 comm="apparmor_parser"
Sep  9 00:38:42 wouter-tablet vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001002
Sep  9 00:38:43 wouter-tablet kernel: [  146.841675] init: network-interface (vmnet1) pre-start process (1200) terminated with status 1
Sep  9 00:38:43 wouter-tablet kernel: [  146.859440] init: network-interface (vmnet1) post-stop process (1202) terminated with status 1
Sep  9 00:38:43 wouter-tablet vmnet-natd: RTM_NEWLINK: name:eth0 index:2 flags:0x00001002
Sep  9 00:38:43 wouter-tablet kernel: [  146.996483] init: network-interface (vmnet8) pre-start process (1210) terminated with status 1
Sep  9 00:38:43 wouter-tablet kernel: [  147.004740] init: network-interface (vmnet8) post-stop process (1214) terminated with status 1
```

---

### Post by chili555 on 2012-09-08
> init: network-interface (eth0) pre-start process (598) terminated with status 1
Sep  9 00:36:42 wouter-tablet kernel: [   25.115591] init: network-interface (eth0) post-stop process (615) terminated with status 1Interesting! May I see:```
cat /etc/network/interfaces
ifconfig
nm-tool
```Good job posting, by the way.

---

### Post by Wouser on 2012-09-08
```
[wouter@wouter-tablet:~]
[03:00|0] $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;kd&#65533;ku&#65533;ku&#65533;ku&#65533;ku&#65533;ku&#65533;ku&#65533;ku&#65533;ku&#65533;ku&#65533;ku&#65533;ku&#65533;k[wouter@wouter-tablet:~]
[03:02|0] $ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49740 (49.7 KB)  TX bytes:49740 (49.7 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.214.1  Bcast:192.168.214.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.153.1  Bcast:192.168.153.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

[wouter@wouter-tablet:~]
[03:02|0] $ nm-tool

** (process:2368): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

NetworkManager Tool

State: unknown


** (process:2368): WARNING **: error: could not connect to NetworkManager
```

---

### Post by chili555 on 2012-09-08
> ** (process:2368): WARNING **: error: could not connect to NetworkManagerWas Network Manager working properly before? I assume this is a virtual machine.

You might try to reinstall it:```
sudo apt-get install --reinstall network-manager
```

---

### Post by Wouser on 2012-09-08
> **chili555 said:**
> Was Network Manager working properly before? I assume this is a virtual machine.

You might try to reinstall it:```
sudo apt-get install --reinstall network-manager
```

No it's not a virtual machine. I run however a virtual machine on my OS sometimes for work. That are proberbly those vmnet1 and vmnet2.

---

### Post by Wouser on 2012-09-09
ps. sudo apt-get install --reinstall network-manager does not work because I dont have internet...

-edit-

Oh yeah! It worked! Downloaded from [http://packages.ubuntu.com/precise/net/network-manager](http://packages.ubuntu.com/precise/net/network-manager) and installed it! Works fine now again!

Woooot. Now again trying to solve the 2.4 GHz 5GHz problem xD

---

