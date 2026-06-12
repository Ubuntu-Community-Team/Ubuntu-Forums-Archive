---
title: "HOWTO: Get wireless button working on Fujitsu Siemens Amilo Li1718"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by alexlaban on 2009-06-06
Okay so I got a Fujitsu Siemens Amilo Li1718 laptop, only problem is that the wireless wouldn't work since ubuntu doesn't seem to support the button which you must press to activate the wireless card but i found this old thread [http://ubuntuforums.org/showthread.php?t=644899](http://ubuntuforums.org/showthread.php?t=644899)
However it doesn't work exactly like that in 9.04 since stuff have changed but I got it to work with these steps

1. Paste this into the terminal
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

2. Get acerhk files
```
wget http://www.cakey.de/acerhk/archives/acerhk-0.5.35.tgz
```

3. Extract and Patch
```
tar xfvz acerhk-0.5.35.tgz
cd acerhk-0.5.35
wget http://www.edbl.no/tmp/acerhk.Makefile.patch
patch -p0 < acerhk.Makefile.patch
```

4. Install
```
make
sudo make install
```

5. Create a file containing instructions which the system will carry out when the acerhk module is loaded - see comments in the file:
```
sudo gedit /etc/modprobe.d/amilo_special_keys.modprobe
```

and paste the following into the file, save and exit

```

# set up kernel module acerhk to enable Fujitsu Siemens Amilo Li1718 special keys
# and enable wireless when the module is inserted.
# NOTE: to have the wireless hardware disabled until you press the wireless key on the laptop,
# simply replace "echo 1" with "echo 0" in the command below. 

install acerhk /sbin/modprobe --ignore-install acerhk force_series=6805 autowlan=1; echo 1 > /proc/driver/acerhk/wirelessled
```

6. Remove the original acerhk module
```
sudo rm /lib/modules/$(uname -r)/kernel/ubuntu/misc/acerhk.ko
```

7. Rebuild the module dependencies database
```
sudo depmod -a
```

8. Tell the system to load the acerhk module at boot time - it won't otherwise, as it's not actually an Acer laptop!
```
sudo gedit /etc/modules
```

add on a new line at the end of this file, then save and exit:
```
acerhk
```

9. restart your machine and you should have a working wifi card.

---

### Post by z3on on 2009-07-04
I really dont have a clue what is all this code now, but I have wireless thanks to you!!
Thank you so much

Now I will have to find out what all these mean :D
Going to read now :lolflag:

---

### Post by artiee on 2009-09-11
Thank you very much! I already tried b43-fwcutter and ndiswrapper but couldn't turn the wireless button on. Now I got it working with your help.

--artiee

---

### Post by vayira on 2010-03-25
I've been trying this with a live CD (to test before installing on a friends compu) but I get these errors...

```
ubuntu@ubuntu:~/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/ubuntu/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ubuntu/acerhk-0.5.35/acerhk.o
/home/ubuntu/acerhk-0.5.35/acerhk.c: In function ‘acerhk_proc_init’:
/home/ubuntu/acerhk-0.5.35/acerhk.c:2671: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/ubuntu/acerhk-0.5.35/acerhk.c:2680: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/ubuntu/acerhk-0.5.35/acerhk.c:2690: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/ubuntu/acerhk-0.5.35/acerhk.c:2702: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/ubuntu/acerhk-0.5.35/acerhk.c:2715: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/ubuntu/acerhk-0.5.35/acerhk.c:2728: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[2]: *** [/home/ubuntu/acerhk-0.5.35/acerhk.o] Error 1
make[1]: *** [_module_/home/ubuntu/acerhk-0.5.35] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [acerhk.ko] Error 2
ubuntu@ubuntu:~/acerhk-0.5.35$ 

```

Is this just because it is a live CD or am I going to have probs if I go ahead with the install?

Thanks for any help.

---

### Post by Ryatzu on 2010-04-26
I got the same error, it's not working with Ubuntu 10.04 beta en RC.

---

### Post by Michalxo on 2010-04-29
Try to install driver from System ->  (system management?) -> Hardware drivers. There should be a software modem, which worked fine for me on LiveCd 10.04 RC1+2 days. Haven't tried lately. ;-)

---

### Post by Michalxo on 2010-04-29
> **Michalxo said:**
> Try to install driver from System ->  (system management?) -> Hardware drivers. There should be a software modem, which worked fine for me on LiveCd 10.04 RC1+2 days. Haven't tried lately. ;-)

Edit: No, it's still broken, as usual in ubuntu... Time to move onto different distribution like Debian... or Mint.
Suspend/Hibernation 2 years old bug does not work on this laptop. Wireless is problem for kernel 2.6.31-20+. 

I've already migrated from ubuntu to debian on my personal laptop. This laptop (amilo li1718) will go there soon... Insane what ubutnu devs do.. no change unless debian devs do the hard work. ;-(

---

### Post by pvdsar on 2010-09-18
After finding this thread and other articles I managed to get Wireless working on a Fujitsu Siemens Amilo Li2727. I discovered an easier method using the acerhkgui 0.7.2
This latest version includes the acerhk driver, compiles it and installs it in /etc/modules. Note that compile also works on Ubuntu Lucid 10.04.
After that you need to make sure that wireless is turned on during startup by creating a modprobe cfg for the acerhk module.

This is all whats needed:
1) Install acerhkgui 0.7.2 (download it from [http://sourceforge.net/projects/acerhkgui/](http://sourceforge.net/projects/acerhkgui/))
2) Run it (its under Applications, System tools)
3) gksudo gedit /etc/modprobe.d/amilo_special_keys.modprobe
4) Paste the following in that file, save and reboot:

                    # set up kernel module acerhk to enable Fujitsu Siemens Amilo Li1718 special keys[INDENT] # and enable wireless when the module is inserted.
# NOTE: to have the wireless hardware disabled until you press the wireless key on the laptop,
# simply replace &#8220;echo 1&#8243; with &#8220;echo 0&#8243; in the command below.
 install acerhk /sbin/modprobe --ignore-install acerhk force_series=6805 autowlan=1; echo 1 > /proc/driver/acerhk/wirelessled


[/INDENT]

---

### Post by pigimon on 2011-03-19
hey i have a problem with step 4 ?! should it be just "make" and then "make install" ??? i did it and i got a console freeze.... sorry newb question.. i really need it i have an amilo m7440... i hope it works man cause i have big problems with my wireless... thanks.

---

### Post by flash63 on 2011-03-20
> **pigimon said:**
> hey i have a problem with step 4 ?! should it be just "make" and then "make install" ??? i did it and i got a console freeze.... sorry newb question.. i really need it [COLOR="Orange"]i have an amilo m7440[/COLOR]... i hope it works man cause i have big problems with my wireless... thanks.

Hello,
in this case you need to install fsam7440:
[http://linuxforums.org.uk/ubuntu/how-to-install-amilo-fsam7440-rf-kill-switchs-driver-in-ubuntu/](http://linuxforums.org.uk/ubuntu/how-to-install-amilo-fsam7440-rf-kill-switchs-driver-in-ubuntu/)

How-To and patched source code (ready to build) also here (German):
[http://forum.ubuntuusers.de/post/2804876/](http://forum.ubuntuusers.de/post/2804876/)

---

### Post by pop_ianosd on 2011-07-01
I also have a problem with step 4, it also freezes my terminal, but I am actually using an Amilo Li1718.

Obs.: I used some older version of Ubuntu, with wireless working, using acer-wmi.. but now it won't work...even if it seems to be installed. If I right-click the networking icon on the top bar, it says "Wireless is disabled";(I recently installed Ubuntu 10.04... now wireless won't work anymore...);

Here is the output of  sudo lshw -C network:


```
*-network DISABLED      
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:fd:50:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:8f:2b:99
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.159 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:a000(size=256) memory:c0200000-c02000ff

```Waiting..

---

### Post by praseodym on 2011-08-27
You may try [this]("http://ubuntuforums.org/showpost.php?p=11193514&postcount=4")

---

