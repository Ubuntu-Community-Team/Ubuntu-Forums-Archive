---
title: "Intel 3945 &quot;Mac is in deep sleep&quot; lucid"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by wstrinz on 2010-05-09
I've always had issues with my wireless card in various linux releases. I have the intel 3945ABG internal card in my laptop. Wireless works for a little while after installation, but when I suspend or restart, suddenly it can't detect any wireless interfaces. Restarting the network applet, rebooting, and various other solutions I've tried don't seem to do anything, but one rare occasions it starts working again for a session. 

dmesg shows:
```
[   30.640034] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.664032] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.684031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.704030] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.724034] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.748034] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.768192] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.788033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.812033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.832031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.852030] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.876034] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.896031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.916031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.936031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.960030] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   30.980032] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.000036] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.024031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.044029] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.064033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.084034] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.108034] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.128033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.148033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.172032] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.192030] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.212031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.236031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.256033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.276031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.296031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.320031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.340033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.360034] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.384033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.404031] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.424033] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   31.426705] iwl3945 0000:02:00.0: Error: saturation power is -1, less than minimum expected 40
[   31.426709] iwl3945 0000:02:00.0: Invalid power index
[   31.426712] iwl3945 0000:02:00.0: initializing driver failed
[   31.426743] iwl3945 0000:02:00.0: PCI INT A disabled
[   31.426757] iwl3945: probe of 0000:02:00.0 failed with error -5
```

and my network card is listed as unclaimed in lshw:
```
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f8100000-f8100fff

```

I'm using 10.04 by the way

Thanks

edit:
output of lsmod:
> iwl3945                68727  0 
iwlcore               105922  1 iwl3945
mac80211              204922  2 iwl3945,iwlcore
cfg80211              126485  3 iwl3945,iwlcore,mac80211
led_class               2864  3 iwl3945,iwlcore,sdhci


ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:e0:b8:d0:3b:46  
          inet addr:146.151.41.38  Bcast:146.151.47.255  Mask:255.255.248.0
          inet6 addr: fec0::8:2e0:b8ff:fed0:3b46/64 Scope:Site
          inet6 addr: 2002:9297:29a8:8:2e0:b8ff:fed0:3b46/64 Scope:Global
          inet6 addr: fe80::2e0:b8ff:fed0:3b46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:576568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:217062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:491011939 (491.0 MB)  TX bytes:18077165 (18.0 MB)
          Memory:f8500000-f8520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19573958 (19.5 MB)  TX bytes:19573958 (19.5 MB)


---

### Post by wstrinz on 2010-05-10
Bump? I've installed the linux wireless drivers from: [http://www.linuxwireless.org/en/users/Download](http://www.linuxwireless.org/en/users/Download) now, but they haven't made any difference.

---

### Post by wstrinz on 2010-05-14
Bump. Anybody? This has been around for a while, someone must've figured out a workaround.

---

### Post by chili555 on 2010-05-14
Please see posts #5, 6 and 7 here:  [http://ubuntuforums.org/showthread.php?p=9102317](http://ubuntuforums.org/showthread.php?p=9102317)

---

### Post by ceesiebo on 2010-05-16
Hi Chili555, you tried to help me in the past. I've had problems with the iwl3945 and at a certain point returned to windows. But I can't keep away from Linux and since my external wifi usb-adapter suddenly started working out of the box since Ubuntu 9.04 it has become my favourite OS again.
 
Anyway, the problem with the iwl3945 never went away. I saw this thread and this is something new I've never tried. I get the same errors as wstrinz but your suggestion does not do anything. Still the same problem. I adjusted the grubfile and did sudo update-grub, but nothing. Still the iwl3945 mac in deep sleep messages keep rolling over the screen when I boot. Sometimes after a few boots, the card works (when the machine is warm basically).

I still think it has to do with the Dell XPS M1530 I'm using. Collegues of mine also have the same iwl3945 in their laptops (other manufacturers like IBM) and they have it working out of the box with no problems at all.

---

### Post by chili555 on 2010-05-16
I'd like to take a look at your entire kernel boot messages. Please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file called dmesg.zip in your user directory. Attach it to your reply. I will look for problems and maybe we can fix this poor thing.

My laptop with an Intel 3945ABG works perfectly.

---

### Post by ceesiebo on 2010-05-16
Here you go.

By the way, I've updated from 9.04 to 9.10 to 10.04. I'm not able to do a fresh install of 10.04 since I still have a dual boot and the installer of Lucid can't see my partitions.

Yesterday I updated to GRUB2 so I could start using the etc/default/grub file and try your solution. Something went wrong there (boot caused Error 15 in Grub while I'm sure I selected a partition) so I had to install the grubfiles from the livecd. Anyway, everything boots up fine now except for the mac in deep sleep messages.

---

### Post by chili555 on 2010-05-16
> iwl3945 0000:0b:00.0: Error: saturation power is -1, less than minimum expected 40Hmmm...googling...

---

### Post by orouwk on 2010-05-16
Hello, I have the same problem in backtrack, same messages for wireless (Intel 3945).
I have attached the messages from  dmesg.
Thanks for all your help.

---

### Post by chili555 on 2010-05-16
Please see: [http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1651](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1651)

Notice they are almost all Dells?

One of the posts suggests that adding noapic as a kernel option solves it (although others disagree). Can you please replace the pci=use_crs option with noapic and see if it helps? Also, please post the version of iwl3945:```
modinfo iwl3945
```We just need the version; ideally, it's version: 1.2.26ks.

---

### Post by ceesiebo on 2010-05-16
The version is 1.2.26, so no worries there. I rebooted with the noapic option. I did that also when I was still using 8.04. It worked for a while as it does now. The wifi-led is blinking and wireless is working. But I'm not sure whether that is caused by my laptop which is heated up a bit now.

I will post back when it has worked for several reboots with a cold laptop.

Extra remark : I'm not sure what the noapic option does. I have the 32-bits version installed (and therefore not getting full access to my 4gb memory) but when I install the 64-bits version and use the noapic option, one of the cores will drop (that's what happened when I had the problem with 8.04). When I checked the system monitor only 1 of my cores was displayed. This is not the case when I use the 32-bits version.

---

### Post by chili555 on 2010-05-16
Yikes! I sounds like the fix for one thing stops another thing. I saw this: [http://ubuntuforums.org/showthread.php?t=334083](http://ubuntuforums.org/showthread.php?t=334083)

Post #4 and 5 refer to the BIOS. Is there a later BIOS available? I wonder if it would help.

---

### Post by ceesiebo on 2010-05-16
No, BIOS A12 is the latest and I have it installed. It's not a big deal though. Like I said, I still have my old usb-adapter that suddenly started working from 9.04 onwards.

---

### Post by ceesiebo on 2010-05-16
I've rebooted with a 'cold' laptop and it still works. So, as expected, the noapic parameter works. But I'd rather not use it since I have no clue what it exactly does and also what it turns off.

I've read some posts about ndiswrapper though. Maybe I'll give that a go. In the past I had an old Dell Inspiron and that used the broadcom card. I also got that working with ndiswrapper but every kernelupdate messed it up and I had to start all over again.

At a certain point in the future, I'll just buy a laptop that works fine with Ubuntu :P

---

### Post by chili555 on 2010-05-16
> I'll just buy a laptop that works fine with UbuntuNot a Dell, I'd assume. May I see:```
lsmod | grep dell
```We may have one more trick before we try ndiswrapper or bin the Dell.

---

### Post by orouwk on 2010-05-16
I have added &quot;noapic&quot; in the default start option in &quot;/boot/grub/menu.lst&quot;. The network is working fine now. I'm using wicd and I'm very satisfied by the choice. Anyway, it's something that I don't understand, for testing purposes, I replaced the noapic with &quot;pci=use_crs&quot; and finally removed for good, but the network is still working (restart after each change). Why does &quot;noapic&quot; is necessary only once and then you can remove it from the kernel line? What was happened there to be necessary this command only once?

---

### Post by wstrinz on 2010-05-16
Thanks for your help, I tried what you suggested and it seemed to work for a while but... today it stopped. Unfortunately I've recently moved to a place where I can't use an ethernet cable to access the network from ubuntu, so I'm writing this on my vista partition. It's good to see other people have a similar problem though. I will try adding the noapic option (I seem to vaguely remember that helping a long time ago) and get back to you.

I have a gateway c141 by the way, so the dell specific problems may not apply to me.

---

### Post by chili555 on 2010-05-16
> **orouwk said:**
> I have added &quot;noapic&quot; in the default start option in &quot;/boot/grub/menu.lst&quot;. The network is working fine now. I'm using wicd and I'm very satisfied by the choice. Anyway, it's something that I don't understand, for testing purposes, I replaced the noapic with &quot;pci=use_crs&quot; and finally removed for good, but the network is still working (restart after each change). Why does &quot;noapic&quot; is necessary only once and then you can remove it from the kernel line? What was happened there to be necessary this command only once?I have no idea! That's very strange. I will be interested to hear if it stays.

---

### Post by ceesiebo on 2010-05-17
This is the output of lsmod | grep dell :

dell_wmi                1793  0 
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop

By the way, using ndiswrapper might give a clue whether it is a driverproblem or a kernelproblem (or something else). Since other users with an IWL3945 have no problems I suspect ndiswrapper will not be the solution.

---

### Post by chili555 on 2010-05-17
Please try:```
sudo rmmod -f dell-laptop
sudo rmmod -f iwl3945
sudo modprobe iwl3945
dmesg | tail -n 25
```Is 'deep sleep' still present?

---

### Post by ceesiebo on 2010-05-17
Unfortunately yes. The dmesg shows the same errors.

---

### Post by chili555 on 2010-05-17
I am sorry; I am out of ideas. You could blacklist iwl3945 to keep the boot process from chocking on 'deep sleep.'

---

### Post by ceesiebo on 2010-05-18
Thanks for your support. The blacklisting is a good idea. Have to do it anyway if I want to test with ndiswrapper. The ndiswrapper-site refers to an old driver though that Intel and Dell don't have anymore. I'll give it a go with a newer driver.

---

### Post by king mint on 2010-06-04
Hey, any luck with this? I have had the same problem with every version of Ubuntu for two years.

---

### Post by LK_gandalf_ on 2010-06-11
Hi all, I also have a Dell XPS 1530, installed Kubuntu 64bit lucid, everything works perfect, the wireless card too, but during the boot I get 20-30 seconds of messages like:

.........iwl3945 MAC is in deep sleep..........

then it usually freeze on the Kubuntu logo, and I have to manually shutdown and the second boot goes well.

The button to power-on/off the wireless works. Is there any solution for the message at boot?
Thank you in advance
```

lspci
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```


```

............:~$ modinfo iwl3945
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.2.26ks
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     02CBE7C0CB9F55C123EC213
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        mac80211,iwlcore,led-class,cfg80211
vermagic:       2.6.32-22-generic SMP mod_unload modversions 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software])
 (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           fw_restart3945:restart firmware in case of error (int)


```

---

### Post by LK_gandalf_ on 2010-06-21
any idea?

---

### Post by flash63 on 2010-06-21
Hello,
try the boot-Option **noapic**
```
sudo gedit /etc/default/grub
```
Change the following entry to
```
GRUB_CMDLINE_LINUX="noapic"
```
Activate it ...
```
sudo update-grub
```
... and restart.

---

### Post by ceesiebo on 2010-07-08
Hi King Mint, sorry that I didn't respond earlier. I was on holiday. Anyway, I've tried ndiswrapper with a newer Vista driver, but that didn't work. ndiswrapper couldn't make use of it. But I already expected this because ndiswrapper is very sensitive. My past experiences with ndiswrapper were also not very positive. Every kernelupdate resulted in me going through the whole ndiswrapper procedure again.

---

