---
title: "Wifi ubuntu 9.04 intel pro wireless 3945 abg dead"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by mrcet007 on 2009-07-18
My wifi in DELL XPS M1530 is now totally dead,It worked fine 2 times just after installing,but after that the wifi was working only occasionally, Now its totaly dead,the wifi driver is not even detected.My friend have the same wifi hardware in DELL inspirion it works fine!!
I searched the forum and did the following to fix it without any result:

I use 
Ubuntu jaunty 9.04 and  intel pro wireless 3945 abg wifi

1)installed linux restricted backport jaunty package
2)blacklisted open source driver and tried with ndiswrapper using an version 11 XP driver
   after this the wifi led started blinking occasionally but cant connect to network
still not working 
Can anybody suggest something??

---

### Post by Kraut~salat on 2009-07-18
it is strange that it degraded over time, so it's more likely a hardware error.  
But to make sure:
If you have Windows try your Wifi there. Should be working there unless it is a hardware problem. Or try some Linux LiveCDs from different distros with different kernel versions. Also if you have a hardware radio kill switch make sure wifi is on BEFORE you boot Linux. Only the latest kernel support hardware kill switches correctly.

---

### Post by mrcet007 on 2009-07-18
Thanks for the reply!! Wifi works fine in windows.What is the "KILL SWITCH " is it the wifi on /off switch.my wifi switch is on always.Can u suggest something else??

---

### Post by Kraut~salat on 2009-07-18
nope. 

I never had problems with my Thinkpad with pro wifi 3945

---

### Post by mrcet007 on 2009-07-19
i uninstalled ndiswrapper because my friend with same laptop and same wifi hardware is getting wifi fine.i think iwl3945 driver is not detected. any fix for this??
Pls check this
OUTPUT:
 sudo lshw -c network
[sudo] password for deepak: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3f:2d:69
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:43:08:8e:11:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mrcet007 on 2009-07-22
Can any ubuntu geeks help me out?? i cant use ubuntu with out wifi.i have have internet connection via wifi only :(

---

### Post by Kraut~salat on 2009-07-22
[http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)

maybe that helps. There are several non-ndiswrapper drivers for your device. Try playing around with the ipw3945 or the iwl3945 modules.

---

### Post by Kraut~salat on 2009-07-22
I just checked it. I am running the iwl3945 module. For that you need a firmware from [http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz](http://www.intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz) . The .ucode files belong into /lib/firmware. Then just load the module: 

modprobe iwl3945

works for me. All of this is probably already integrated into the current kernel tree. So just try the modprobe thing and maybe you are there already

---

### Post by mrcet007 on 2009-07-22
Thanks a lot [Kraut~salat]("http://ubuntuforums.org/member.php?u=750392"), finally it is working,ur iwifi driver did the magic. But the driver works only occasionally- means sometimes only wifi works when i boot ,if it doesnt work i am unable to load driver by "sudo modprobe iwl3945" and i have to reboot to make it work. can u help me fix it [Kraut~salat]("http://ubuntuforums.org/member.php?u=750392") .is there any patches for the driver because in close range also the signal strength is  75 -80 only.

---

### Post by cheiros on 2009-10-10
> **mrcet007 said:**
> Thanks a lot [Kraut~salat]("http://ubuntuforums.org/member.php?u=750392"), finally it is working,ur iwifi driver did the magic. But the driver works only occasionally- means sometimes only wifi works when i boot ,if it doesnt work i am unable to load driver by "sudo modprobe iwl3945" and i have to reboot to make it work. can u help me fix it [Kraut~salat]("http://ubuntuforums.org/member.php?u=750392") .is there any patches for the driver because in close range also the signal strength is  75 -80 only.

Hey mrcet007 i have the same notebook, same ubuntu version (9.04) and the same problem like you :)

I did the steps recomended by Kraut~salat but nothing or maybe i did wrong the steps :(

could you tell me step by step how you solved?

Thanks :)

---

### Post by mrcet007 on 2009-10-10
BEST SOLUTION : Install fedora 11!!!!!!!!
thats what i finally had to do. I think recombiling the kernel is the solution.but its difficult.I searched every where for solution ,but didnt get one.
Hope ubuntu will solve this problem in 9.10.

---

### Post by cheiros on 2009-10-11
> **mrcet007 said:**
> BEST SOLUTION : Install fedora 11!!!!!!!!
thats what i finally had to do. I think recombiling the kernel is the solution.but its difficult.I searched every where for solution ,but didnt get one.
Hope ubuntu will solve this problem in 9.10.

LOL i didnt get a solution too :S

I hate this situation, ubuntu is wonderfull but is incredible that cant use a %#$%&&" wireless card

---

