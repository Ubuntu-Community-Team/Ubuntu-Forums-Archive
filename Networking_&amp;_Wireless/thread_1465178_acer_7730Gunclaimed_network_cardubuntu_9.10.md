---
title: "acer 7730G|unclaimed network card|ubuntu 9.10"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by m.niels on 2010-04-29
hello
 
i have a acer 7730G labtop 
i installed ubuntu for the first time
i have now  dual boot with windows 7
en i dont get a internet wireless connection or even a LAN 
so i googled en i found out that my network card is unclaimed 
i alredy tryed diskwarapper but it didnt work
i have ubuntu 9.10
here are some specs:
 
**network controller**: intel corporation wireless WiFi link 5100
**ethernet controller**:broadcom corporation NetXtreme BCM5764M Gigabit ethernet PCIe (rev 10)
 
**iwconfig**:  lo no wireless extensions
 
 
**sudo lshw -c network** :
 
 *-network UNCLAIMED     
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:07:00.0"]pci@0000:07:00.0[/EMAIL]
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:be200000-be201fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:09:00.0"]pci@0000:09:00.0[/EMAIL]
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress cap_list
       configuration: latency=0
       resources: memory:be300000-be30ffff
 

[B]kernel architecture
[/B]2.6.31-14-generic i686
 
 
i hope somebody could help me 
 
 
thanks!!

---

### Post by chili555 on 2010-04-29
Please open a terminal and do:```
sudo modprobe iwlagn
iwconfig
rfkill list
```Did your wireless interface appear?

---

### Post by m.niels on 2010-04-29
**iwconfig:**
 
no wireless extensions
 
**rfkill list:** 
 
0: acer-wireless: wireless LAN
soft blocked:    NO
Hard Blocked:  NO
 
this is what i get when i use it in terminal

---

### Post by chili555 on 2010-04-29
Let's see what the kernel reports:```
dmesg | grep iwl
uname -r
lsmod | grep acer
```Thanks.

---

### Post by m.niels on 2010-04-29
[   24.070307] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.085451] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.100596] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.115740] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.130885] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.146029] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.161174] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.176318] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.191462] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.206607] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.221751] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.237020] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.252040] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.267185] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.282329] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.297474] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.312618] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.327763] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.342908] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.358052] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.373196] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.388341] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.403485] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD
[   24.418630] iwlagn 0000:07:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x17EFEDFD

its a lot of text 
i hope it could help us

edit here is the rest 



marc@marc-laptop:~$ uname -r
2.6.31-14-generic

marc@marc-laptop:~$ lsmod | grep acer
acer_wmi               15936  0 
led_class               4096  3 iwlcore,acer_wmi,sdhci

---

### Post by chili555 on 2010-04-29
> iwlagn 0000:07:00.0: MAC is in deep sleep!. CSR_GP_CNTRL = 0x17EFEDFDSee posts 5, 6 and 7 here: [http://ubuntuforums.org/showthread.php?t=1448721](http://ubuntuforums.org/showthread.php?t=1448721)

The fix should work for you. Post back and let us know.

---

### Post by m.niels on 2010-04-30
thanks it works!!!! maybe you should make a topic en show it to a admin or mod to make it sticky! damm!!!!
 
THANKS!!:P

---

