---
title: "Ubuntu 13.10 Installation nvidia driver on card NVIDIA  geoforce GT740M"
date: 2013-12-27
forum: Multimedia Software
---

### Post by valnew62 on 2013-12-27
Hi folks,
I installed Ubuntu 13.10 (dual boot windows 8) on my PC/Toshiba satellite i5 with a card video geoforce GT740M  and everyting was perfectly working.

After I tried to install manualy the nvidia-331 driver  (last driver)  driver as follows: 

[COLOR=#008080]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331.

[/COLOR]But after reboot  I had the screen user&password and after the black screen.

So then I Tried to install another driver "nvidia-current" from a terminal (sudo apt-get install nvidia-current) and rebbot but I had the same result as above, i.e. the black screen.


Please can you help me to correct the error if possible  or restore the original video settings ??.

thank you in advance.
Sandro

---

### Post by Yellow Pasque on 2013-12-27
You cannot install nvidia driver directly on an Optimus (Intel/nvidia hybrid) GPU setup. See: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by sgxnew54 on 2013-12-27
Hi folks 

I'm blocked here,  as can I go back to original video config  please ??   

thanks

---

### Post by valnew62 on 2013-12-28
[SIZE=2]Hi everybody,
I tried to install bamblebee following the ubuntu wiki, an now the pc workes, does login normaly.[/SIZE]
 [SIZE=2]After on the terminal I tried to use NVIDIA card with cmd [/SIZE]**[SIZE=2]<[/SIZE]****[SIZE=2]$: [/SIZE]****[SIZE=2]optirun firefox[/SIZE]**[SIZE=2]> [/SIZE][SIZE=2]and [/SIZE][SIZE=2]I had this error :[/SIZE]

[COLOR=#ff0000][SIZE=2][ 5470.593692] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
[ 5470.593718] [ERROR]Aborting because fallback start is disabled.[/SIZE][/COLOR]


 [SIZE=2]I report the configuration of the  files **/etc/bumblebee/xorg.conf.nouveau**[/SIZE]
 

 [SIZE=2]Section "ServerLayout"[/SIZE]

     [SIZE=2]Identifier  "Layout0"[/SIZE]
     [SIZE=2]Option      "AutoAddDevices" "false"[/SIZE]
     [SIZE=2]Option      "AutoAddGPU" "false"[/SIZE]
 [SIZE=2]EndSection[/SIZE]
 

 [SIZE=2]Section "Device"[/SIZE]
     [SIZE=2]Identifier  "DiscreteNvidia"[/SIZE]
     [SIZE=2]Driver      "nouveau"[/SIZE]
 [SIZE=2]#   If the X server does not automatically detect your VGA device,[/SIZE]
 [SIZE=2]#   you can manually set it here.[/SIZE]
 [SIZE=2]#   To get the BusID prop, run `lspci | egrep 'VGA|3D'` and input the data[/SIZE]
 [SIZE=2]#   as you see in the commented example.[/SIZE]
 [SIZE=2]#   This Setting is needed on Ubuntu 13.04.[/SIZE]
     [SIZE=2]BusID "PCI:01:00:0"[/SIZE]
 

 [SIZE=2]EndSection[/SIZE]
 

 

 and** /etc/bumblebee/xorg.conf.nvidia**

 [SIZE=2]Section "ServerLayout"[/SIZE]
     [SIZE=2]Identifier  "Layout0"[/SIZE]
     [SIZE=2]Option      "AutoAddDevices" "false"[/SIZE]
     [SIZE=2]Option      "AutoAddGPU" "false"[/SIZE]
 [SIZE=2]EndSection[/SIZE]
 [SIZE=2]Section "Device"[/SIZE]
     [SIZE=2]Identifier  "DiscreteNvidia"[/SIZE]
     [SIZE=2]Driver      "nvidia"[/SIZE]
     [SIZE=2]VendorName  "NVIDIA Corporation"[/SIZE]
 [SIZE=2]#   If the X server does not automatically detect your VGA device,[/SIZE]
 [SIZE=2]#   you can manually set it here.[/SIZE]
 [SIZE=2]#   To get the BusID prop, run `lspci | egrep 'VGA|3D'` and input the data[/SIZE]
 [SIZE=2]#   as you see in the commented example.[/SIZE]
 [SIZE=2]#   This Setting may be needed in some platforms with more than one[/SIZE]
 [SIZE=2]#   nvidia card, which may confuse the proprietary driver (e.g.,[/SIZE]
 [SIZE=2]#   trying to take ownership of the wrong device). Also needed on Ubuntu 13.04.[/SIZE]
     [SIZE=2]BusID "PCI:01:00:0"[/SIZE]
 [SIZE=2]#   Setting ProbeAllGpus to false prevents the new proprietary driver[/SIZE]
 [SIZE=2]#   instance spawned to try to control the integrated graphics card,[/SIZE]
 [SIZE=2]#   which is already being managed outside bumblebee.[/SIZE]
 [SIZE=2]#   This option doesn't hurt and it is required on platforms running[/SIZE]
 [SIZE=2]#   more than one nvidia graphics card with the proprietary driver.[/SIZE]
 [SIZE=2]#   (E.g. Macbook Pro pre-2010 with nVidia 9400M + 9600M GT).[/SIZE]
 [SIZE=2]#   If this option is not set, the new Xorg may blacken the screen and[/SIZE]
 [SIZE=2]#   render it unusable (unless you have some way to run killall Xorg).[/SIZE]
     [SIZE=2]Option "ProbeAllGpus" "false"[/SIZE]
     [SIZE=2]Option "NoLogo" "true"[/SIZE]
     [SIZE=2]Option "UseEDID" "false"[/SIZE]
     [SIZE=2]Option "UseDisplayDevice" "none"[/SIZE]
 [SIZE=2]EndSection[/SIZE]
 

 [SIZE=2]So I execute  cmd** <l lspci | egrep 'VGA|3D'> **and I had:[/SIZE]

 

 [SIZE=2]00:02.0 **VGA **compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)[/SIZE]
 [SIZE=2]01:00.0 **3D **controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)[/SIZE]
 

 [SIZE=2]So, I think to replace the  BusID "PCI:01:00:0"above, in nouveau and nvidia, as follows[/SIZE]
  [SIZE=2]**BusID "PCI:0****0****:0****2****:0"     **[/SIZE] 
 

 [SIZE=2]please could you tell me if this update is correct, before doing  it   ??[/SIZE]

 

 [SIZE=2]thanks in advance[/SIZE]
 [SIZE=2]Sandro[/SIZE]

---

### Post by sgxnew54 on 2013-12-30
[SIZE=2]Hi everybody,
I finally resolved with the istallation of the driver nvidia-331, the nvidia-304, already installed on my PC   is unable to manage the NVIDIA Geoforce GT 740M

thanks anyway
[/SIZE]

---

### Post by Gustavo_Scaloni_Ve on 2014-01-29
> **sgxnew54 said:**
> [SIZE=2]Hi everybody,
I finally resolved with the istallation of the driver nvidia-331, the nvidia-304, already installed on my PC   is unable to manage the NVIDIA Geoforce GT 740M

thanks anyway
[/SIZE]

Thanks, same problem, same solution!

---

### Post by Dani_Carbonell on 2014-02-25
I worked for me as well. I removed nvidia-304 in synaptic, added nvidia-331 and installed bumblebee
My laptop is a MSI GE60 - i7 4700mq - GT 740m
Thanks

---

