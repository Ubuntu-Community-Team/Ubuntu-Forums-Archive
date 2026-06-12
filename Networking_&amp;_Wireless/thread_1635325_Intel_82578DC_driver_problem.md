---
title: "Intel 82578DC driver problem"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by tobi11 on 2010-12-01
Hey guys!
I am using Ubuntu 10.10 64-bit and have a strange problem with my Intel 82578DC network card on my mainboard, which should use the e1000e driver as far as I know. When I cold boot into ubuntu, it isn't properly initialized (or something like this) and unusable, but if I reboot from Windows or Ubuntu back to Ubuntu everything works fine.
The card/interface doesn't show when running ifconfig, but turns up in lspci and lshw.
I found the following two lines in the syslog, when the card didn't work: ```
e1000e 0000:00:19.0: PCI INT A disabled
e1000e: probe of 0000:00:19.0 failed with error -3
```Do you know what I can do to resolve this issue?
thanks for your help

---

### Post by paula_ms on 2011-03-21
Try this, [http://ronenagranat.blogspot.com/2011/01/ubuntu-1010-wired-internet-fail-intel.html](http://ronenagranat.blogspot.com/2011/01/ubuntu-1010-wired-internet-fail-intel.html)

---

### Post by tobi11 on 2011-03-21
wow, thanks for the link after such a long time.
I flashed the newest version BIOS available, but they didn't fix the issue. I don't have an Intel board, it is from DFI. I guess I will have to try to convince them to fix this issue ...
At least now I know what's going on.

---

### Post by Nerson on 2011-06-20
and did you do something with it? I have DFI P55 t3eh9 MB and this same issue. I read this blog entry but I'm not sure that's manual is correct for us. Also I have updated BIOS but it doesn't change anything. I found some firmware on Intel site but it's for developer.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=12344&ProdId=3245&lang=eng&OSVersion=%0A&DownloadType=Firmware](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=12344&ProdId=3245&lang=eng&OSVersion=%0A&DownloadType=Firmware)

It's make me sad, I have to dual boot OS ;(

---

### Post by Sylslay on 2011-06-20
If I am not wrong, 
and You did proper Bios update

and Enthernet Card always run good (in any circumstance) in windows,

then 100 procent is not hardware issue, only
bug in linux driver for Yours entherned card.

And more likly if You can't compile driver from source 
then You will not fix problem.

Solution:
1) Wait for new better dirver (but You did already).
2) Load deflaut settingis in BIOS and tune it, Change IRQ and ACPI settings. 
3) Get other distro linux.

For me Ubuntu works best, I started with Ubuntu and always back to this distro.

PS. Do not tray any "deb" based distro,

---

### Post by tobi11 on 2011-06-20
> and did you do something with it? I have DFI P55 t3eh9 MB and this same issue. I read this blog entry but I'm not sure that's manual is correct for us. Also I have updated BIOS but it doesn't change anything. I found some firmware on Intel site but it's for developer.

[http://downloadcenter.intel.com/Deta...dType=Firmware](http://downloadcenter.intel.com/Deta...dType=Firmware)

It's make me sad, I have to dual boot OS ;( I have the same MB. I couldn't fix the issue and am currently using a separate ethernet card .... I did send a message to DFIs [technical support]("http://www.dfi.com.tw/portal/CM/cmsupport"), but never heard anything back. Maybe they will do something if they get a few more support requests ;)

> If I am not wrong, 
and You did proper Bios update

and Enthernet Card always run good (in any circumstance) in windows,

then 100 procent is not hardware issue, only
bug in linux driver for Yours entherned card.

And more likly if You can't compile driver from source 
then You will not fix problem.

Solution:
1) Wait for new better dirver (but You did already).
2) Load deflaut settingis in BIOS and tune it, Change IRQ and ACPI settings. 
3) Get other distro linux.Since there is a BIOS update from Intel directly, it is a BIOS bug, but our boards are from DFI and they did not fix it in their BIOS ... But maybe their is an option in the BIOS to change the IRQ settings like you suggested. I will have a look.

---

### Post by Sylslay on 2011-06-20
Hardwere makers ara making mistake as well

egxample: Old VIA chip for SATA and PATA hdd.

Good luck

---

