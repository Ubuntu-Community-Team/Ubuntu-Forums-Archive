---
title: "Driver for Broadcom 4312 won't activate"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by stigb on 2009-12-06
I have a Dell laptop and I would very much like to be able to use wireless networks. Running lspci, I find that my network controller is
```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```I go to System -> Administration -> Hardware Drivers, and I find the "Broadcom STA wireless driver", which I would very much like to activate. So I click "Activate" and type in my password, and nothing happens.
I try to reistall the driver directly from the installation CD (/media/cdrom0/pool/restricted/b/bcmwl) and then I can see that I get some error messages in the terminal, which you can see below.
```
(Les database ... 136471 filer og katalogar er installerte.)
Gjer klar til å byta ut bcmwl-kernel-source 5.10.91.9+bdcom-0ubuntu4 (ved bruk av .../bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb) ...
Removing all DKMS Modules
Done.
Pakkar ut erstattinga bcmwl-kernel-source ...
Set opp bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
Adding Module to DKMS build system
Doing initial module build
/usr/sbin/dkms: line 35: patch: command not found

Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/ for more information.
Installing initial module

Error! Could not locate wl.ko for module bcmwl in the DKMS tree.
You must run a dkms build for kernel 2.6.31-16-generic (i686) first.
Done.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic

```This is as far as I get, are there anybody who can help me? (I apologize that some of the language in the terminal is not English, I hope you understand it anyway.)

---

### Post by stigb on 2009-12-06
Additional information: My laptop is a Dell Latitude E5400, my Ubuntu is 9.10 Karmic, and my Linux kernel is 2.6.31.16. I tried following [http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620) this tutorial, but I can't recognize any changes at all.

---

### Post by leorolla on 2009-12-06
Does this help?

[http://ubuntuforums.org/showthread.php?t=1312603](http://ubuntuforums.org/showthread.php?t=1312603)

---

### Post by chenxiaolong on 2009-12-06
You don't have the package "patch" installed. And the Broadcom STA driver is called bcmwl-kernel-source, so I don't know what the bcmwl package is for (maybe a typo). Anyway you need to uninstall the driver, install patch, and reinstall the driver.

```
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install patch
sudo apt-get install bcmwl-kernel-source
```

---

### Post by stigb on 2009-12-15
Hey, sorry for a late answer. Installing patch worked in the sense that bcmwl-kernel-source installed without any error messages. I had to delete the blacklist files I created in your tutorial, and then it kinda seemed to be working. In "Hardware drivers", the driver was activated, or rather: "This driver is activated but not in use." There still does not show up any wireless options on the networking icon. Thanks for the help so far, though.

---

### Post by chenxiaolong on 2009-12-15
That's okay:) So you've removed the blacklist files with "blacklist b43", "blacklist ssb", and "blacklist wl" right? If you did, you need to blacklist ssb and b43 again because those conflict with wl. Also, you will need to add "wl" to the file "/etc/modules" so it loads on bootup. I hope this works for you:D

---

### Post by stigb on 2009-12-15
It still doesn't work! I have checked quite thoroughly that I have followed your instructions and I have even reinstalled the driver twice. What's worse, another guy in my class has the exact same laptop with the same version of Ubuntu and he somehow got the wireless to work... although he has no idea as to how.

Is there any settings I should check? Jockey still tells me that "This driver is activated but not currently in use."

---

### Post by chenxiaolong on 2009-12-15
Are you trying to follow my directions in this forum: [http://ubuntuforums.org/showthread.php?t=1266620?](http://ubuntuforums.org/showthread.php?t=1266620?) In that thread, I was talking about the b43 driver, which is still in a testing state. The driver in Jockey is referring to the wl driver. If you followed the instructions in my other thread, you won't be able to use the wl driver, even though it's installed.

---

### Post by stigb on 2009-12-16
All I can say now is that it still does not work. I even --purge remove'd the packages I installed from your other tutorial, namely linux-backports-karmic and b43-bwcutter (if I spelled them out right)

---

### Post by linux6994 on 2009-12-16
I did have similar troubles and swithed to Linux Mint Helena which is Karmic based. I loaded it and my bcm wireless driver worked great.

---

### Post by redbook4574 on 2009-12-16
> **stigb said:**
> All I can say now is that it still does not work. I even --purge remove'd the packages I installed from your other tutorial, namely linux-backports-karmic and b43-bwcutter (if I spelled them out right)

Try b43-fwcutter

---

### Post by chenxiaolong on 2009-12-16
Here: I'll give you the complete steps to make the Broadcom STA driver work.

1. sudo rmmod b43 ssb wl

2. sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source

3. Open all the files in /etc/modprobe.d/ and make sure that all of these lines AREN'T there:
   blacklist ssb
   blacklist b43
   blacklist wl

4. Open /etc/modules and make sure that these aren't there:
   b43
   ssb
   wl

5. Open /etc/modprobe.d/aliases.conf (if it exists) and make sure "alias wlan0 b43" isn't there.

6. Now remove or rename the b43 folder and the b43-legacy folder (if they exist) in /lib/firmware.

7. Reboot your computer.

8. Install the Broadcom STA driver using Jockey or install the package "bcmwl-kernel-source"

9. Reboot your computer.

---

### Post by lordraz on 2010-01-16
> **chenxiaolong said:**
> Here: I'll give you the complete steps to make the Broadcom STA driver work.

1. sudo rmmod b43 ssb wl

2. sudo apt-get --purge remove linux-backports-modules-karmic b43-fwcutter bcmwl-kernel-source

3. Open all the files in /etc/modprobe.d/ and make sure that all of these lines AREN'T there:
   blacklist ssb
   blacklist b43
   blacklist wl

4. Open /etc/modules and make sure that these aren't there:
   b43
   ssb
   wl

5. Open /etc/modprobe.d/aliases.conf (if it exists) and make sure "alias wlan0 b43" isn't there.

6. Now remove or rename the b43 folder and the b43-legacy folder (if they exist) in /lib/firmware.

7. Reboot your computer.

8. Install the Broadcom STA driver using Jockey or install the package "bcmwl-kernel-source"

9. Reboot your computer.
You sir... are a genius. This worked perfectly! I've spent about an hour (which in linux time is probably not all that long searching for how to get things to work ;) ) trying to figure out how to get my stupid broadcom 4312 to work and have looked at numerous tutorials which require rather intense and convoluted processes. I happen to stumble across this little post and viola! Thank you soooo very much.

---

### Post by chenxiaolong on 2010-01-16
You're welcome :D. I'm glad it worked for you!

---

### Post by leorolla on 2010-01-16
Hi Chen Xiao Long,

I have wireless working after many attempts and a little black magic, and I doubt I could reproduce the sambe behavior on a fresh install.

From what I remember:

I had STA working fine for months, then it was recently broken with a log message just like [http://ubuntuforums.org/showthread.php?t=1369975](http://ubuntuforums.org/showthread.php?t=1369975). It was broken without any action from me. Jockey would simply produce that error.

I tried blacklisting this and that, I purged and reinstalled bcmwl-kernel-source, didn't work.
I tried a chip of the instructions from your famous thread to install the b43 driver and linux-backports, didn't work.
I tried madwifi following [AspireOne/Ubuntu8.04 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/AspireOne/Ubuntu8.04"), didn't work.

Then I had the idea of just using ndiswrapper, which (if worked) would last stable until Lucid release, much more probably than any other solution subject to Ubuntu updates regressions.

It worked (very) well, then I blacklisted everything else and rebooted. It wasn't working.
I thought that, even though it doen't make sense to me, the problem could be with the blacklisting, as it was the only thing I did between working and not-working.
Bingo!
I removed the blacklistings, rebooted and it worked. Again and again.
I blacklisted again, rebooted, not working.
Removed the blacklisting, rebooted, and it was working. Rebooted again and again, and it was working.

Curious conclusion: it was working only when the other drivers were not blacklisted, even though they didn't seem to be loaded from lsmod.

From your above instructions and the capitalized "AREN'T" I see you somehow arrived at a similar conclusion, but maybe you know or suspect what could be the reason.

Edit:
I downloaded the Windows driver from Acer at
[http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/WLAN_Broadcom_4.170.75.0_XPx86.zip?acerid=633701164785992813&Step1=Netbook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=PA_7](http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/WLAN_Broadcom_4.170.75.0_XPx86.zip?acerid=633701164785992813&Step1=Netbook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=PA_7) (not [http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/WLAN_Intel_12.1.0.14_XPx86.zip?acerid=633701164795352753&Step1=Netbook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=PA_6](http://global-download.acer.com/GDFiles/Driver/Wireless%20LAN/WLAN_Intel_12.1.0.14_XPx86.zip?acerid=633701164795352753&Step1=Netbook&Step2=Aspire%20One&Step3=AOD150&OS=X01&LC=en&BC=Acer&SC=PA_6) as I said before) and opened file bcmwl5.inf with ndiswrapper

Sometimes it fails, then I remove the driver from ndiswrapper, reboot, add the driver again, check for new blacklists, remove them, reboot again and it works.

---

### Post by chenxiaolong on 2010-01-16
I've seen another person who had that problem after blacklisting. I have one question though (nonrelated): How did you find a working driver for Ndiswrapper? Before I found out about the STA driver and b43, I tried over 20 different drivers for Vista, XP, 2000, including ones packaged by different manufacturers and none of them worked :( :D.

---

### Post by leorolla on 2010-01-17
I have an Acer Aspire One D150.

I went to the manufacturer's page and looked for the driver.

The W7 driver didn't work but the XP one did.

---

### Post by stigb on 2010-01-25
Thanks for all the help so far. I have now followed your tutorial in #12, and guess what.

"This driver is installed but not currently in use".

I wanted to install Mint Helena, but people in an IRC chat told me "Mint does a lot of evil".

---

### Post by chenxiaolong on 2010-01-25
```
sudo modprobe wl
```

---

### Post by stigb on 2010-01-25
We're finally getting somewhere!
```

$ sudo modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.31-16-generic/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
$
```And output from dmesg:
```
[ 3842.399553] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 3842.399564] wl: Unknown symbol lib80211_get_crypto_ops
```May this be because I installed bcmwl-kernel-source from the installation CD and not from the interwebs?

---

### Post by chenxiaolong on 2010-01-25
No, just remove the package linux-backports-modules-karmic

---

### Post by stigb on 2010-01-25
I have a package named linux-backports-modules-karmic**-generic**, should I purge that?

---

### Post by chenxiaolong on 2010-01-25
Yes, unless you have hardware that needs it.

---

### Post by stigb on 2010-01-25
I am in fact starting to wonder if the laptop hates me.

I removed linux-backports-modules-karmic-generic and reinstalled bcmwl-kernel-source. And restarted the computer, of course.

Jockey provides the same "installed but not in use" message and modprobe yields the same error I described in a previous post.

I also have a package called linux-backports-modules-2.6.31-16-generic, is this the same cake?

---

### Post by chenxiaolong on 2010-01-25
Yes, it is the same thing. The linux-backports-modules-karmic just references that package.

---

### Post by stigb on 2010-01-25
Well at last!
Thank you, the forums, and chenxiaolong in particular for bearing with me for so long.

And have a nice day.

---

### Post by chenxiaolong on 2010-01-25
Well, considering my other threads, this wasn't long at all :D. Have fun with the wireless :D.

---

### Post by leorolla on 2010-01-26
Did it work finally or not?

Otherwise you can try ndiswrapper as I described at post #15 here.
(The biggest advantage is that it will be less likely to be discontinued, so I plan to keep it that way until Ubuntu can handle our wireless natively and flawlessly.)

Anyway, if a solution is working for you, just stick to it.

---

### Post by bademeister on 2010-02-21
chenxiaolong, thanks so much, this also worked for me. Just had to deinstall the linux-backports-modules-2.6.31-* and the broadcom driver started working again!

Thanks!

---

### Post by chenxiaolong on 2010-02-21
You're welcome!! I'm glad you got it working :D.

---

### Post by Kamikafre on 2010-04-10
Hi chenxiaolong,

Could you please take a look on this, and give me a hand? maybe you could give another point of view...

[http://ubuntuforums.org/showthread.php?t=1447461](http://ubuntuforums.org/showthread.php?t=1447461)

thanks in advance!

---

### Post by chenxiaolong on 2010-04-10
Do you have a specific problem that you need help with or would you like a guide for installing the Broadcom STA driver?

---

### Post by Kamikafre on 2010-04-10
The link is a topic posted by me and i'm not able to make my 4312 to work. The colleague "arjuntank" is trying to help but just to have another point of view of the problem as i saw that you solved this but i tried with your step by step and nothing worked...

thanks

---

### Post by chenxiaolong on 2010-04-10
Here, try this:

1. Remove Wicd, any backports modules, STA driver (reinstall later).

```
sudo apt-get purge wicd linux-backports-modules bcmwl-kernel-source
```

2. Make sure network manager is installed and reinstall the STA driver.

```
sudo apt-get install network-manager network-manager-gnome bcmwl-kernel-source
```

3. Open the file /etc/modprobe.d/blacklist-bcmwl.conf (I don't remember exact name) and check to make sure these lines are in it.

> blacklist b43
blacklist b43legacy
blacklist bcm43xx
blacklist ssb

4. Open the file /etc/modules and make sure that:

> b43
b43legacy
bcm43xx
ssb

aren't there and make sure that:

> wl

is. 

5. Reboot and your wireless should be working. 

By the way, the STA driver does not use the wlan# naming scheme, but rather the eth# naming scheme.

Good luck! Please post back if you have any problems.

---

### Post by Kamikafre on 2010-04-10
I'm closer than ever!!!!!:P

But still could not connect.... network manager is asking me for the password everytime without connecting....:(

thanks so much anyway, as i think we're one step closer...

---

### Post by chenxiaolong on 2010-04-10
Could you post

```
iwconfig
ifconfig
lshw -C Network
```

?

---

### Post by Kamikafre on 2010-04-10
> **chenxiaolong said:**
> Could you post

```
iwconfig
ifconfig
lshw -C Network
```

?

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

```



ifconfig:
```
eth0      Link encap:Ethernet  direcciónHW 00:1e:ec:d3:95:cc  
          Direc. inet:192.168.1.130  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::21e:ecff:fed3:95cc/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3773 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4110 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:3477802 (3.4 MB)  TX bytes:836475 (836.4 KB)
          Interrupción:19 Dirección base: 0xdead 

eth2      Link encap:Ethernet  direcciónHW 00:23:08:22:b1:78  
          Dirección inet6: fe80::223:8ff:fe22:b178/64 Alcance:Enlace
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:688
          Paquetes TX:0 errores:6 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:18 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)

```




lshw -C Network:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:d3:95:cc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.3 ip=192.168.1.130 latency=0 multicast=yes
       resources: irq:19 memory:d4407000-d440707f ioport:1080(size=128)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 01
       serial: 00:23:08:22:b1:78
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:d4100000-d4103fff

```


there's something i'm missing?

---

### Post by chenxiaolong on 2010-04-10
Network-manager seems like it's not setting the wireless card to connect to your network:

```
eth2      IEEE 802.11  Nickname:""
         ** Access Point: Not-Associated**  
```

I suggest reinstalling network-manager and network-manager-gnome, but you will need to download those packages first from packages.ubuntu.com because you won't the internet during this process.

So, here are the links:

64 bit:
[http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091014t134532.4033e62-0ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091014t134532.4033e62-0ubuntu1_amd64.deb)

32 bit:
[http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_i386.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091014t134532.4033e62-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091014t134532.4033e62-0ubuntu1_i386.deb)

After you download those packages, remove your current network-manager and network-manager-gnome (to install later).

```
sudo apt-get purge network-manager network-manager-gnome
```

Then, install the packages you downloaded and restart your computer. Hopefully, your wireless will work then.

Good luck :D!

---

### Post by Kamikafre on 2010-04-10
same as before...

it ask me for password, i type it, and after a few seconds it ask again....

[IMG]http://yfrog.com/5mscreenshot002gzp[/IMG]

---

### Post by chenxiaolong on 2010-04-10
Sorry, but I have no idea what to do now :(. I've only had this problem on versions of Ubuntu prior to 9.10.

---

### Post by Kamikafre on 2010-04-11
And for all mysteries of the Ubuntu this night....





WORKED!!!!

i open my laptop to give it another try and et voilá!!!! is working!!! i have wireless!!!

what worked for me is what chenxialong told me, because is the last thing i tried, and after few hours worked...

thanks to chenxialong!

---

### Post by chenxiaolong on 2010-04-11
AWESOME!!!!

I'm happy you got it working!

---

### Post by yolucid on 2010-05-27
thx, now my bcm43xx adapter is working

---

### Post by donwr on 2010-06-12
I also had the same Broadcom 4312 problem in that my wireless card wouldn't connect to the router.  I did the steps in notes #34 and #38 and still had problems: I had the wireless network active 100%, but when left clicking the "network icon" and displaying the Wired and Wireless Networks, my router's wireless network's color was mid-gray (not white), and in fact I couldn't access the internet via the router. I re-did the steps, purging the driver and network manager first. Still not working. Then, I went traveling for a day or two and tried using other routers and had similar non-connection results.  But, without any other changes, when I returned home, the wireless network started working.  Life is mysterious. Thanks chenxiaolong for your helpful guidance.

---

### Post by Cthulhu_Dreams on 2010-06-23
I've been trying to solve this too, no luck.  Some notes:

> 1. sudo rmmod b43 ssb wl

None of those existed.

> 2. sudo apt-get --purge remove linux-backports-modules-karmic
b43-fwcutter bcmwl-kernel-source

The indicated backports did not exist.  While this is expected since I'm
using Lucid, a quick browse of Synaptic's results for "backports" didn't
reveal any installed backports.

> 
3. Open all the files in /etc/modprobe.d/ and make sure that all of
these lines AREN'T there:

There was a .conf called blacklist-b43 - I deleted it.  Additionally the
blacklist-local.conf contained one line that only blacked listed b43, so
I deleted that too.

> 4. Open /etc/modules and make sure that these aren't
there:

There is no directory called modules in /etc/

Output of terminal upon completion of the remaining steps and restart:

```
adrian@Alpha-60:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for adrian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer
required:
  libkworkspace4 diffstat libgnomepanel2.24-cil
  libplasma-geolocation-interface4 libplasmaclock4 libweather-ion4 quilt
  kdebase-workspace-bin mysql-server-core-5.1 libprocessui4
libprocesscore4
  libsolidcontrol4 libsolidcontrolifaces4 akonadi-server libksgrd4
  libtaskmanager4 mysql-client-core-5.1 module-assistant
  kdebase-workspace-data libplasmagenericshell4 python-configobj
  kdebase-workspace-kgreet-plugins libkephal4
plasma-dataengines-workspace
  ksysguardd libkscreensaver5 libkfontinst4
libplasma-applet-system-monitor4
  kdepim-runtime plasma-widgets-workspace
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/896kB of archives.
After this operation, 2,867kB of additional disk space will be used.
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 194116 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36
+bdcom-0ubuntu3_amd64.deb) ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-22-preempt
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-22-preempt
adrian@Alpha-60:~$ 
```

---

### Post by chenxiaolong on 2010-06-23
Cthulhu_Dreams: You don't have the kernel headers and compilers installed. Fortunately, there's an easy fix for your problem:

```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install build-essential
sudo apt-get install bcmwl-kernel-source
```

---

### Post by Cthulhu_Dreams on 2010-06-23
Nothing....

```
adrian@Alpha-60:~$ sudo apt-get install build-essential
[sudo] password for adrian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
The following packages were automatically installed and are no longer required:
  libkworkspace4 diffstat libgnomepanel2.24-cil
  libplasma-geolocation-interface4 libplasmaclock4 libweather-ion4 quilt
  kdebase-workspace-bin mysql-server-core-5.1 libprocessui4 libprocesscore4
  libsolidcontrol4 libsolidcontrolifaces4 akonadi-server libksgrd4
  libtaskmanager4 mysql-client-core-5.1 dkms module-assistant
  kdebase-workspace-data libplasmagenericshell4 python-configobj
  kdebase-workspace-kgreet-plugins libkephal4 plasma-dataengines-workspace
  ksysguardd libkscreensaver5 libkfontinst4 libplasma-applet-system-monitor4
  kdepim-runtime plasma-widgets-workspace
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by chenxiaolong on 2010-06-23
Try installing "linux-headers-generic" and "linux-source". Then, reinstall "bcmwl-kernel-source".

---

### Post by Cthulhu_Dreams on 2010-06-23
Still nothing.  Here is the jockey log

```
2010-06-23 12:22:07,665 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680>
2010-06-23 12:22:07,722 DEBUG: reading modalias file /lib/modules/2.6.32-22-preempt/modules.alias
2010-06-23 12:22:08,191 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-06-23 12:22:08,219 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-06-23 12:22:08,375 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-06-23 12:22:08,409 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-06-23 12:22:08,581 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-06-23 12:22:08,704 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-06-23 12:22:08,819 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-06-23 12:22:09,092 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2010-06-23 12:22:09,304 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2010-06-23 12:22:09,608 DEBUG: Software modem not available
2010-06-23 12:22:09,609 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2010-06-23 12:22:09,828 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2010-06-23 12:22:09,829 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2010-06-23 12:22:09,866 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2010-06-23 12:22:09,866 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2010-06-23 12:22:09,866 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2010-06-23 12:22:10,295 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2010-06-23 12:22:10,296 DEBUG: Firmware for DVB cards not available
2010-06-23 12:22:10,296 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-06-23 12:22:10,596 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2010-06-23 12:22:10,597 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2010-06-23 12:22:10,608 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-23 12:22:10,616 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-06-23 12:22:10,617 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2010-06-23 12:22:10,630 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-23 12:22:10,631 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2010-06-23 12:22:10,844 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2010-06-23 12:22:10,845 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2010-06-23 12:22:10,857 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2010-06-23 12:22:10,857 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2010-06-23 12:22:10,955 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2010-06-23 12:22:10,956 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2010-06-23 12:22:10,969 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2010-06-23 12:22:10,969 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2010-06-23 12:22:11,086 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-23 12:22:11,098 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2010-06-23 12:22:11,099 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2010-06-23 12:22:11,099 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2010-06-23 12:22:11,166 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2010-06-23 12:22:11,168 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2010-06-23 12:22:11,168 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2010-06-23 12:22:11,168 DEBUG: all custom handlers loaded
2010-06-23 12:22:11,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-23 12:22:11,168 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-23 12:22:11,300 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,300 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0103:')
2010-06-23 12:22:11,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-23 12:22:11,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-06-23 12:22:11,528 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'platform:pcspkr')
2010-06-23 12:22:11,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,529 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,529 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-23 12:22:11,551 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-23 12:22:11,552 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:ENE0100:')
2010-06-23 12:22:11,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-23 12:22:11,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'platform:lis3lv02d')
2010-06-23 12:22:11,552 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0003v04F2pB179e8213-e0,1,kD4,ramlsfw')
2010-06-23 12:22:11,553 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-23 12:22:11,553 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-06-23 12:22:11,556 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'intel_agp', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,556 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-06-23 12:22:11,599 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,602 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-23 12:22:11,603 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-23 12:22:11,603 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2010-06-23 12:22:11,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-23 12:22:11,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-06-23 12:22:11,603 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-06-23 12:22:11,607 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i915', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,607 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,607 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-06-23 12:22:11,610 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-23 12:22:11,610 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-23 12:22:11,613 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,615 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-06-23 12:22:11,618 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,618 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc02ip00')
2010-06-23 12:22:11,619 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-23 12:22:11,619 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,620 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-06-23 12:22:11,620 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,620 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-06-23 12:22:11,620 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,620 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,620 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:INT0800:')
2010-06-23 12:22:11,621 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,623 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-23 12:22:11,624 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-06-23 12:22:11,624 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.24:bd06/12/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.37:cvnQuanta:ct10:cvrN/A:')
2010-06-23 12:22:11,637 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-06-23 12:22:11,640 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-23 12:22:11,640 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-23 12:22:11,643 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-23 12:22:11,643 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-06-23 12:22:11,648 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,648 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-06-23 12:22:11,650 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-06-23 12:22:11,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-06-23 12:22:11,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,656 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,656 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-23 12:22:11,657 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-23 12:22:11,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-23 12:22:11,659 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-06-23 12:22:11,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-23 12:22:11,660 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc01ip00')
2010-06-23 12:22:11,660 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-06-23 12:22:11,661 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,661 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-06-23 12:22:11,663 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-06-23 12:22:11,666 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,669 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-23 12:22:11,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-23 12:22:11,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-23 12:22:11,678 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,678 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-06-23 12:22:11,685 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2010-06-23 12:22:11,685 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1f44680> about HardwareID('modalias', 'acpi:device:')
2010-06-23 12:22:11,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0C04:')
2010-06-23 12:22:11,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2010-06-23 12:22:11,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0103:')
2010-06-23 12:22:11,685 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0C02:')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002A43sv0000103Csd00003627bc03sc80i00')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'platform:pcspkr')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:ENE0100:')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0000:')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'platform:lis3lv02d')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0003v04F2pB179e8213-e0,1,kD4,ramlsfw')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-06-23 12:22:11,686 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002A40sv0000103Csd00003627bc06sc00i00')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v000014E4d00004315sv0000103Csd00001507bc02sc80i00')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0200:')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:LNXVIDEO:')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002A42sv0000103Csd00003627bc03sc00i00')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d0000293Esv0000103Csd00003627bc04sc03i00')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0B00:')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002936sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002930sv0000103Csd00003627bc0Csc05i00')
2010-06-23 12:22:11,687 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc02ip00')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0001v111Dp7603e0001-e0,12,kramls1,2,fw')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:INT0800:')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002935sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:SYN1E04:SYN1E00:SYN0002:PNP0F13:')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'dmi:bvnHewlett-Packard:bvrF.24:bd06/12/2009:svnHewlett-Packard:pnHPPaviliondv6NotebookPC:pvrRev1:rvnQuanta:rn3627:rvr18.37:cvnQuanta:ct10:cvrN/A:')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002919sv0000103Csd00003627bc06sc01i00')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2010-06-23 12:22:11,688 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002939sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'usb:v0BDAp0158d5887dc00dsc00dp00ic08isc06ip50')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002932sv0000103Csd00003627bc11sc80i00')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002938sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002929sv0000103Csd00003627bc01sc06i01')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,3,kra0,1,2,mlsfw')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0303:')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002937sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,689 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0100:')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:PNP0C32:')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'usb:v04F2pB179d8213dcEFdsc02dp01ic0Eisc01ip00')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw6,')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d0000293Asv0000103Csd00003627bc0Csc03i20')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d0000293Csv0000103Csd00003627bc0Csc03i20')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v00008086d00002934sv0000103Csd00003627bc0Csc03i00')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-06-23 12:22:11,690 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-06-23 12:22:11,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2010-06-23 12:22:11,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'pci:v000010ECd00008136sv0000103Csd00003627bc02sc00i00')
2010-06-23 12:22:11,691 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x23dc758> about HardwareID('modalias', 'acpi:device:')
2010-06-23 12:22:11,763 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-23 12:22:11,896 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-23 12:22:11,970 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-23 12:22:14,254 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-06-23 12:22:17,422 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-06-23 12:22:17,423 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-06-23 12:22:17,443 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```

---

### Post by Cthulhu_Dreams on 2010-06-25
Bump

---

### Post by chenxiaolong on 2010-06-26
You can run "sudo dkms status" to see whether there were problems compiling the kernel module (driver). 

The last thing I can recommend is to remove the "bcmwl-kernel-source" package and manually removing the source files from the system for a fresh install of the driver.

```
sudo apt-get purge bcmwl-kernel-source bcmwl-modaliases b43-fwcutter linux-backports-modules-lucid
sudo rm -rf /usr/src/bcmwl-*
sudo apt-get install build-essential gcc make bcmwl-kernel-source
```

If there are any error messages, please post them here.

---

### Post by Cthulhu_Dreams on 2010-06-26
```
adrian@Alpha-60:~$ sudo dkms status
[sudo] password for adrian: 
bcmwl, 5.60.48.36+bdcom: added 
```

Error:

```
adrian@Alpha-60:~$ sudo apt-get purge bcmwl-kernel-source bcmwl-modaliases b43-fwcutter linux-backports-modules-lucid
[sudo] password for adrian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package b43-fwcutter is not installed, so not removed
E: Couldn't find package linux-backports-modules-lucid
```

---

### Post by chenxiaolong on 2010-06-27
```
sudo apt-get purge bcmwl-kernel-source bcmwl-modaliases b43-fwcutter
sudo apt-get install --reinstall build-essential linux-headers-2.6.32-22*
sudo rm -rf /usr/src/bcmwl-*
sudo apt-get install gcc make bcmwl-kernel-source
```

---

### Post by Cthulhu_Dreams on 2010-06-30
```
   	 	 	 	 	 	  sudo apt-get purge bcmwl-kernel-source bcmwl-modaliases b43-fwcutter  
 sudo apt-get install --reinstall build-essential linux-headers-2.6.32-22*  
 sudo rm -rf /usr/src/bcmwl-*  
 sudo apt-get install gcc make bcmwl-kernel-sourceadrian@Alpha-60:~$ sudo apt-getwcutterbcmwl-kernel-source bcmwl-modaliases b43-f  
 [sudo] password for adrian:  
 Reading package lists... Done  
 Building dependency tree         
 Reading state information... Done  
 Package b43-fwcutter is not installed, so not removed  
 The following packages were automatically installed and are no longer required:  
   libkworkspace4 diffstat libgnomepanel2.24-cil  
   libplasma-geolocation-interface4 libplasmaclock4 libweather-ion4 quilt  
   kdebase-workspace-bin mysql-server-core-5.1 libprocessui4 libprocesscore4  
   libsolidcontrol4 libsolidcontrolifaces4 akonadi-server libksgrd4  
   libtaskmanager4 mysql-client-core-5.1 dkms module-assistant  
   kdebase-workspace-data libplasmagenericshell4 python-configobj  
   kdebase-workspace-kgreet-plugins libkephal4 plasma-dataengines-workspace  
   ksysguardd libkscreensaver5 libkfontinst4 libplasma-applet-system-monitor4  
   kdepim-runtime plasma-widgets-workspace  
 Use 'apt-get autoremove' to remove them.  
 The following packages will be REMOVED: 
   bcmwl-kernel-source* bcmwl-modaliases*  
 0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.  
 After this operation, 2,933kB disk space will be freed.  
 Do you want to continue [Y/n]? y  
 (Reading database ... 212907 files and directories currently installed.)  
 Removing bcmwl-kernel-source ...  
 Removing all DKMS Modules  
 Done.  
 update-initramfs: deferring update (trigger activated)  
 Purging configuration files for bcmwl-kernel-source ...  
 update-initramfs: deferring update (trigger activated)  
 Removing bcmwl-modaliases ...  
 Processing triggers for initramfs-tools ...  
 update-initramfs: Generating /boot/initrd.img-2.6.32-22-preempt  
 adrian@Alpha-60:~$ ^C  
 adrian@Alpha-60:~$  
 
```

Now the driver doesn't show up in Hardware Drivers

---

### Post by chenxiaolong on 2010-06-30
I've had lots of problems with the Hardware Drivers (Jockey). Please try installing "bcmwl-kernel-source" now. It's the same thing as the Broadcom STA Driver in Hardware Drivers. You can use apt-get or synaptic.

If it generates any errors, please post them here.

---

### Post by leorolla on 2010-07-01
We have the same controller... it wasn't supposed to get that hard.

Why don't we test if there is something really screwed up in your install after so many attempts of installing/removing thins?

I suggest you make a Ubuntu 10.04 LiveUSB with persistent memory, boot it with wired connection, and then install bcmwl-kernel-source with Synaptic.

---

### Post by Cthulhu_Dreams on 2010-07-05
Chenx:  I did what you said, while I did not receive any errors, the Hardware Drivers did not show any drivers to activate nor did I have access to wireless.

Leo:  I have done as you suggested.  Hardware Drivers offers me two options for activating wireless:

Broadcom B43 Wireless Driver and Broadcom STA wireless driver.

I tried to install both and got the following message:

SystemError: installArchives() failed

I've considered going the way of Ndiswrapper.  I found the appropriate driver and installed the appropriate driver through ndiskgtk....but nothing happened.  Do either you have any experience with Ndiswrapper?

---

### Post by leorolla on 2010-07-06
I have some experience, and I wouldn't go for ndiswrapper. Other solutions may fail just because ndiswrapper is bothering them.

What LiveUSB did you try, Lucid or Karmic?

I think the error message you got is that Hardware Drivers tried to install things but failed because it couldn't connect to the internet. Makes sense? Did you have internet when it happened?

Let's try without Hardware Drivers.

Create a new Lucid USB with persistent memory.

Solution 1:
[https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/AcerAspireOneD150](https://wiki.ubuntu.com/Testing/Laptop/Lucid/Reports/AcerAspireOneD150)

If your hardware doesn't give DMA errors we are done.

Otherwise...

Solution 2:
Get wired connection.
Run "sudo apt-get update && sudo apt-get install bcmwl-kernel-source".
Add "blacklist b43" to your blacklists.
Reboot.

If you get error messages please post them.

---

### Post by Cthulhu_Dreams on 2010-07-06
> What LiveUSB did you try, Lucid or Karmic?Lucid.

> I think the error message you got is that Hardware Drivers tried to  install things but failed because it couldn't connect to the internet.  Makes sense? Did you have internet when it happened?No, I was on the internet.  They got about 90 percent done and then gave that message.

This is what I got back:

```
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Get:1 http://security.ubuntu.com lucid-security Release.gpg [189B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Get:2 http://archive.ubuntu.com lucid Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Get:3 http://security.ubuntu.com lucid-security Release [38.5kB]
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Get:4 http://archive.ubuntu.com lucid-updates Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Get:5 http://archive.ubuntu.com lucid Release [57.2kB]
Get:6 http://archive.ubuntu.com lucid-updates Release [44.7kB] 
Get:7 http://security.ubuntu.com lucid-security/main Packages [44.1kB]    
Get:8 http://archive.ubuntu.com lucid/main Packages [1,386kB]  
Get:9 http://security.ubuntu.com lucid-security/restricted Packages [14B]     
Get:10 http://security.ubuntu.com lucid-security/main Sources [14.6kB]
Get:11 http://security.ubuntu.com lucid-security/restricted Sources [14B]      
Get:12 http://archive.ubuntu.com lucid/restricted Packages [6,208B]
Get:13 http://archive.ubuntu.com lucid/main Sources [659kB]
Get:14 http://archive.ubuntu.com lucid/restricted Sources [3,775B]
Get:15 http://archive.ubuntu.com lucid-updates/main Packages [248kB]
Get:16 http://archive.ubuntu.com lucid-updates/restricted Packages [3,252B]
Get:17 http://archive.ubuntu.com lucid-updates/main Sources [90.1kB]
Get:18 http://archive.ubuntu.com lucid-updates/restricted Sources [1,292B]
Fetched 2,597kB in 4s (545kB/s)                           
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 240 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.60.48.36+bdcom
Kernel:  2.6.32-21-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-21-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-21-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-21-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```  **After doing what you said, I _was_ able to detect wireless networks and connect to them.  Where do we go from here?**

---

### Post by leorolla on 2010-07-07
After doing what exacly? Just the commands you posted above?

Do you still have wireless after rebooting with this USB?

If so, could you post
```
sudo lshw -C network
lsmod
```?

Also, if you could right-click on the network manager icon, show connection information and tell us what you see there in the wireless tab, it may be useful.

If you don't get wireless after reboot, you can try repeating the same steps again. So please run the above commands before and after doing it and post them both.

---

### Post by Cthulhu_Dreams on 2010-07-07
I did Solution 2.  Yes, after reboot wireless is still there.  It might be useful to note the Ubuntu live is 32-Bit while I'm using a 64-bit Ubuntu

```
ubuntu@ubuntu:~$ sudo lshw -C network
SCSI                      
  *-network        
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:26:5e:12:69:0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:f7:78:db
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=24.20.238.175 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:5000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               11331  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_idt      51914  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
joydev                  8708  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
hp_accel               11144  0 
snd_timer              19098  2 snd_pcm,snd_seq
lis3lv02d               6007  1 hp_accel
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lirc_ene0100            6536  0 
lib80211_crypt_tkip     7596  0 
input_polldev           2482  1 lis3lv02d
lirc_dev                8884  1 lirc_ene0100
led_class               2864  1 hp_accel
psmouse                63245  0 
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959598  0 
uvcvideo               56990  0 
soundcore               6620  1 snd
videodev               34361  1 uvcvideo
serio_raw               3978  0 
v4l1_compat            13251  2 uvcvideo,videodev
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lib80211                5046  2 lib80211_crypt_tkip,wl
squashfs               20680  1 
aufs                  149050  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  282354  3 
usb_storage            39425  1 
drm_kms_helper         29297  1 i915
drm                   162471  4 i915,drm_kms_helper
intel_agp              24177  2 i915
ahci                   32008  0 
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
r8169                  33884  0 
mii                     4381  1 r8169
video                  17375  1 i915
output                  1871  1 video
ubuntu@ubuntu:~$ 

```

---

### Post by leorolla on 2010-07-08
Great!

Now you can try the same thing but with the a Lucid 64 bit LiveUSB [:)]

If the test goes fine, we will know that your HD install has been screwed up by Hardware Drivers and some other attempts to fix it... so all we'll have to do is undo it.

---

Personally I think it is worth trying Solution #1.
It uses open-source drivers with the proprietary firmware, and it tends to get much more support from the kernel developmers than Solution #2, which is closed-source drivers with proprietary firmware.

All that Solution #1 does is to download files containing the firmware and a program that extracts the firmware from them, and then place the firmware in the appropriate folder.

Notice that it doesn't require internet connection, nor installing any further software, just have two files pre-downloaded on your HD and access them from the USB Live Session.

---

### Post by InItTogether on 2010-07-20
Thanks so much! This worked for me too. Dell Latitude E6400 with Broadcom. Thank you, thank you, thank you!

---

### Post by chenxiaolong on 2010-07-20
Sorry, I couldn't help out earlier. Vbulletin stopped emailing me updates to my subscribed threads :(.

InItTogether: I'm glad you got it working!

---

### Post by mikkyy on 2010-08-10
Hi all.
I am find help for my card 4e4:4315  BCM4312.
I have Ubuntu 10.4  with last kernel (2.6.35)
i am use b43. but no work manged or monitor.
I am used PIO. But no fix.

How to try my card in work.?

Thank all for reply

By

---

### Post by Lev Lafayette on 2010-10-13
> **chenxiaolong said:**
> Here: I'll give you the complete steps to make the Broadcom STA driver work.


Thank you! Also worked for Ubuntu 10.10 with a very archaic Dell Inspiron 1501, Broadcom BCM4311....

---

