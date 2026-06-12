---
title: "Dell Wireless 1370 MiniPCI Card problem"
date: 2006-01-21
forum: Networking &amp; Wireless
---

### Post by VictorCain on 2006-01-21
I could sure use some help on this. Here's what I've 
done up to this point.  It's a Dell Wireless 1370 MiniPCI 
card in an Dell InspironB120 Laptop running Kubuntu 5.10.

The executable /usr/sbin/ndiswrapper is from the
Ubuntu package ndiswrapper-utils, and the module
is what was provided in the kernel 2.6.12-9.

I have two drivers from Dell for the card (although
I haven't tried the older one) R102320.EXE and the
later R115321.EXE which was updated 1-17-2006.  I also
have not tried any of the Wiki drivers.

R115321.EXE was unzipped in /usr/local/wlan_1370 and
the contents of /usr/local/wlan_1370/DRIVER are:
  bcm43xx.cat
  bcmwl5.inf
  bcmwl5.sys

As root,
  /usr/sbin/ndiswrapper -i {full path}bcmwl5.inf
which resulted in 22 messages stating that:
  forcing parameter |BSSGMode|0 to |BSSGMode|2

As root,
  /usr/sbin/ndiswrapper -l
   installed ndisdrivers:
   bcmwl5  driver present, hardware present

As root,
  /usr/sbin/ndiswrapper -m
  Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper

As root,
  /sbin/depmod -a
and,
  modprobe ndiswrapper
both appear to work.

Then,
  iwconfig
 lo        no wireless extensions.
 eth0      no wireless extensions.
 sit0      no wireless extensions.

And,
  dmesg | grep ndiswrapper
[4294706.940000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294707.026000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:strrchr
[4294707.026000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmFreeContiguousMemorySpecifyCache
[4294707.026000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmAllocateContiguousMemorySpecifyCache
[4294707.026000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmGetPhysicalAddress
[4294707.026000] ndiswrapper (load_sys_files:456): unable to prepare driver 'bcmwl5'
[4294707.026000] ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'
[4294718.202000] Modules linked in: i82365 rsrc_nonstatic pcmcia_core tc1100_wmi video battery container i2c_acpi_ec i2c_core button pcc_acpi sony_acpi ac dev_acpi hotkey ipv6 ndiswrapper pcspkr rtc tpm_nsc tpm pci_hotplug snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc intel_agp agpgart nls_iso8859_1 nls_cp437 vfat fat dm_mod tsdev joydev evdev psmouse mousedev parport_pc lp parport md reiserfs thermal processor fan b44 mii ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk ide_generic piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit

I found no messages from "loadndisdriver" in the system log.

And,
  ifconfig
 eth0 Link encap:Ethernet  HWaddr 00:14:22:8E:21:07
      inet addr:192.168.1.29  Bcast:192.168.1.255  Mask:255.255.255.0
      inet6 addr: fe80::214:22ff:fe8e:2107/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
      RX packets:236224 errors:0 dropped:0 overruns:0 frame:0
      TX packets:11029 errors:0 dropped:0 overruns:0 carrier:0
      collisions:11 txqueuelen:1000
      RX bytes:108855096 (103.8 MiB)  TX bytes:1033486 (1009.2 KiB)
      Interrupt:18
 lo   Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:16436  Metric:1
      RX packets:47516 errors:0 dropped:0 overruns:0 frame:0
      TX packets:47516 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:5066184 (4.8 MiB)  TX bytes:5066184 (4.8 MiB)

/etc/network/interfaces (without bland lines and comments):
auto lo eth0 wlan0
iface lo inet loopback
mapping hotplug
        script grep
        map eth0
iface eth0 inet static
        address 192.168.1.29
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 68.87.68.162 68.87.74.162 68.87.64.196 68.87.66.196
iface wlan0 inet static
        address 192.168.1.28
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 68.87.68.162 68.87.74.162 68.87.64.196 68.87.66.196
        pre-up modprobe ndiswrapper
        post-down rmmod ndiswrapper

Any help would be greatly appreciated.

---

### Post by mohapi on 2006-01-23
Hi. I'm using the same card in an Inspiron 600m, and I got it installed without too much stress. I can explain how I put it together, although I'm still very new at this and I don't have a clear understanding of why some things work.

I also cheated a little, since I could run a cable from the laptop to the router, which gave me Internet access. 

First I installed ndiswrapper with 

```
sudo apt-get install ndiswrapper-utils
```
Then I decompressed the drivers I downloaded from Dell support into a folder in my home directory. I called it '1370', just because it's quicker to type, and put *everything *in there. I've seen posts where people say there are other (.sys) files that ndiswrapper needs, but again, I don't know if that's true. I'm definitely not a Linux expert.

Then 

```
cd ~/1370
sudo ndiswrapper -i bcmwl5.inf
```
After the acknowledgements spun past, I checked the driver installation with

```
ndiswrapper -l
```
and got the lovely "hardware present, driver present" message.

At this point I unplugged my cable to the router. I don't know if it matters when you do that. Then

```
sudo modprobe ndiswrapper
```
to start the module, and

```
sudo ndiswrapper -m
```
to set the module to restart on reboot.

Now I had to tinker with the networking menu (under System > Administration > Networking) to tell Ubuntu to stop using (deactivate) the hard line and configure and activate the wireless. I also supplied the SSID and the key I use. That will be something you have to tweak on your own, since your connections will be different from mine. 

I did notice that it was set to static and not DHCP, and that it took a lo-o-o-o-o-ong time for it to finally configure and acknowledge the changes. If Windows had taken that long, I would have assumed it had crashed. :)

I rebooted after it was all said and done with, just to be safe. It came up again on the first try, and as I type, it's running the Automatix script. :KS 

I think that's about it. Hope this helps.

---

### Post by scottporad on 2006-03-02
I have a Dell Inspiron 600m with the Dell 1370 Wireless Network Card, and am having a similar problem to, VictorCain, the original poster. The machine was new out of the box from Dell two days ago. Here's what I've one:

1.  Installed Ubuntu 5.10 from CD
2.  Followed the instructions of Mohapi, (2nd poster who was successful)
3. Here is my terminal session:
```

scott@scottlaptop:~$ mkdir 1370
scott@scottlaptop:~$ unzip R115321.EXE -d 1370
Archive:  R115321.EXE
  inflating: 1370/DellInfo.exe
  inflating: 1370/dellinst.exe
  inflating: 1370/ikernel.ex_
  inflating: 1370/is.exe
 extracting: 1370/launcher.ini
  inflating: 1370/layout.bin
  inflating: 1370/MFC71.DLL
  inflating: 1370/msvcp71.DLL
  inflating: 1370/msvcr71.DLL
  inflating: 1370/preflib.dll
  inflating: 1370/README.rtf
  inflating: 1370/setup.exe
  inflating: 1370/Setup.ini
  inflating: 1370/setup.inx
  inflating: 1370/setup.iss
  inflating: 1370/WLBCGCBPRO731.DLL
  inflating: 1370/wltray.exe
  inflating: 1370/wltrynt.dll
  inflating: 1370/wltrysvc.exe
  inflating: 1370/DRIVER/bcm43xx.cat
  inflating: 1370/DRIVER/bcmwl5.inf
  inflating: 1370/DRIVER/bcmwl5.sys
  inflating: 1370/ATL71.DLL
  inflating: 1370/bcm1xsup.dll
  inflating: 1370/BCMLogon.dll
  inflating: 1370/bcmwlcpl.cpl
  inflating: 1370/bcmwlhlp.cab
  inflating: 1370/bcmwlhlp.chm
  inflating: 1370/bcmwliss.dll
  inflating: 1370/bcmwlnpf.sys
  inflating: 1370/bcmwlpkt.dll
  inflating: 1370/bcmwls32.exe
  inflating: 1370/bcmwls.ini
  inflating: 1370/bcmwltry.exe
  inflating: 1370/bcmwlu00.exe
  inflating: 1370/data1.cab
  inflating: 1370/data1.hdr
  inflating: 1370/data2.cab
  inflating: 1370/Version.txt
scott@scottlaptop:~$ cd 1370/DRIVER/
scott@scottlaptop:~/1370/DRIVER$ ls
bcm43xx.cat  bcmwl5.inf  bcmwl5.sys
scott@scottlaptop:~/1370/DRIVER$ sudo ndiswrapper -i bcmwl5.inf
Password:
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
scott@scottlaptop:~/1370/DRIVER$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
scott@scottlaptop:~/1370/DRIVER$ sudo modprobe ndiswrapper
scott@scottlaptop:~/1370/DRIVER$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
``` 
Now, at this point I visit **System > Administration > Networking** and wlan0 does not appear.  So, I do the following:
```

scott@scottlaptop:~/1370/DRIVER$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
scott@scottlaptop:~/1370/DRIVER$ dmesg | grep ndiswrapper
[4296070.152000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4296070.191000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:strrchr
[4296070.191000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmFreeCo ntiguousMemorySpecifyCache
[4296070.191000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmAlloca teContiguousMemorySpecifyCache
[4296070.191000] ndiswrapper (import:238): unknown symbol: ntoskrnl.exe:MmGetPhy sicalAddress
[4296070.192000] ndiswrapper (load_sys_files:456): unable to prepare driver 'bcm wl5'
[4296070.201000] ndiswrapper (ndiswrapper_load_driver:92): loadndiswrapper faile d (11); check system log for messages from 'loadndisdriver'
``` 
I'm lost at this point.  Can anyone offer any ideas?

---

### Post by Jagot on 2006-03-02
Hi, sorry this post isn't to offer any soultion, but I'm using the very same card in an Inspiron 1300 and am in pretty much the same situation.

> 
jagot@ubuntu:~$ sudo ndiswrapper -i ~/Desktop/DRIVER/bcmwl5.inf
Installing bcmwl5
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
Forcing parameter IBSSGMode|0 to IBSSGMode|2
jagot@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present
jagot@ubuntu:~$ sudo modprobe ndiswrapper
jagot@ubuntu:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

jagot@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

jagot@ubuntu:~$


As far as I can see, the only difference between VictorCain, scottporad and myself is that mine never does the **Adding "alias wlan0 ndiswrapper" to/etc.modprobe.d/ndiswrapper** after I enter **sudo ndiswrapper -m**.  Still end up with the same result, however, that the card does not show up in **System > Administration > Networking.**

I have tried using the version of this driver that came installed on my system as well as an updated version I downloaded from Dell's website.  I have also heard mentioned that some people have got similar cards working by using the  bcmwl5a.inf driver, the only version of which I could find was preinstalled on the system, but this has not worked for me either - still said that the driver and hardware were present, but it came to nothing.

Many thanks if anyone's able to solve this.

Jagot

---

### Post by scottporad on 2006-03-03
This post may be helpful: [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

I followed these instructions exactly.  I am now able to see wlan0 in the System > Administration > Networking dialog.  

However, I don't have it working quite yet because even though the interface is there and active, I cannot find my network.

```
scott@scottlaptop:~$ ping 192.168.14.23
connect: Network is unreachable
```

---

### Post by scottporad on 2006-03-04
Okay...I finally got this working.  Here's how I did it:

1.  The Dell 1370 uses the Broadcom 4318 Chip (BCM4318).  Apparently, Acer has a wireless card that uses the same chip.  So, I used the Acer driver instead of the Dell driver, and ndiswrapper was able to install that driver properly.

2.  I followed the instructions here: [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

3.  On my machine, the default setting in the BIOS is to have the wireless antenna "off".  Apparently, Dell has a utility called Dell Quick Set that is installed as a Windows service on Dell machines that turns the wireless antenna on at startup.  This error:

```
scott@scottlaptop:~$ ping 192.168.14.23
connect: Network is unreachable
```

is a result of the fact that the wireless antenna was off.  So, I turned it "on" in the BIOS, and now everything is working.

---

### Post by Jagot on 2006-03-04
Hi.

Many thanks scottporad - I did the same as you suggested with Acer drivers and now mine's working too.  This was one of the things that was really annoying me - I'm a newbie and I had everything else set up ok, but this was still puzzling me!

Nothing stopping me wiping Windows from my hard drive now :D 

Thanks again,

Jagot

---

### Post by NotJayKay on 2006-03-09
I just wanted to post that I had the exact same problem as all of you did and that the Acer drivers fixed it.

[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

What was odd about mine, was that I was originally using the drivers that came with my laptop and those worked.  But I had a MBR failure and had to reinstall everthing and the new drivers I got from Dell last night weren't working in Ubuntu....weird.

---

### Post by scottporad on 2006-03-09
I've noticed that the Acer drivers only support 802.11g.  Typically,this isn't a problem...except when you go somewhere that only has 802.11b like I did last night.  :)

So, if anybody figures out how to get 802.11b/g working, please post here to let us know. 

Scott

---

### Post by d3dtn01 on 2006-03-11
I just bought a Dell Inspiron B120 and installed ubuntu. Like most people, my wireless card (a Dell 1370) wasn't recognized. I've followed all the directions above and still can't get it to work. The wireless card appears in my network settings window, but it won't recognize my access point. I checked my BIOS and indeed it was set to off, but even after setting it to enable it still doesn't connect to my access point.

Initially I used the Dell drivers, but took the suggestion and downloaded the Acer drivers. I followed the HOW TO ([http://ubuntuforums.org/showthread.php?t=25683&pp=10](http://ubuntuforums.org/showthread.php?t=25683&pp=10)) exactly. Where am I going wrong?

(You can probably tell that I'm a complete newbie to Linux.)

I'm wondering if I've got the wrong version of ndiswrapper (I'm using 1.1-4ubuntu2).

UPDATE: Actually, I got it working by following the directions above. I'm not sure why it didn't work the first time I tested it, but now everything is OK.

Any help would be greatly appreciated.

---

### Post by katarot on 2006-03-19
im having the same problem with a dell inspiron 1300 and the 1370 mini-pci card
no matter what i do it wont work i tried ndiswrapper did not work 
even tried a native driver 

i have been trying the method here on this thread 
ndiswrapper seems to install the drivers i got from acer correctly 
i type this in 
sudo ndiswrapper -l 
hardware present device present 
i go to iwconfig and there is no wlan0 listed 
ifconig is the same im really confused please help

---

### Post by DavidFourer on 2006-03-21
This is a great thread, but I've had enough for one night and maybe I'll have some advice in the morning:

I've followed:  [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

I found /etc/ndiswrapper/bcmwl5/*.conf and all looked well
then:
david@davidf:/$ sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
Password:bash: $conffile: ambiguous redirect

What is "ambiguous redirect"?  

I know some of the symbols, like re-direct and pipe but I don't remember or never knew what $ or ' means

Also this is troubling: 
david@davidf:/$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present

It should say "driver present, hardware present"

lspci
0000:03Network controller: Broadcom Corp: Unknown Device 4318 (rev 02)
lspci -n
0000:03:03.0  0280:  14e4:4318 (rev 02)

david@davidf:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
                                                nothing about Wlan0

I have Dell Inspiron 6000, Dell Wireless 1370 WLAN MiniPCI card
Broadcom BCM4318[Airforce One 54g] 802.11

Thanks for the help I've already gotten.

---

### Post by snikkerz on 2006-03-28
i notice that a lot of others are having the same problem particularly on a dell inspiron 1300.
i'm trying to run a dell 1370 wireless card on a dell inspiron 1300 in kubuntu 5.10.

what i've tried so far:

- using ndiswrapper with bcmwl5 as jonny and everyone else has done.
- changing the BIOS settings to automatically turn on the wireless card when OS starts
- changing RadioState|1 to RadioState|0 as suggested by johnny

problems:
- ifconfig doesn't show wlan0
- iwconfig shows lo, eth0, sit0, all with "no wireless extensions"
- during kubuntu startup, i get "Starting PCMCIA services [failed]" (IS THIS A SEPARATE PROBLEM ALTOGETHER?)

couldn't download acer driver -- the ftp link didn't respond
couldn't find the broadcom driver on their site -- the closest driver was called BCM4318E, which from the description didn't seem to be wha

if any of you have given up (as i'm about to) and purchased another wireless card (USB or PCI), i'd like to know which cards are working

thanks,
-gene

---

