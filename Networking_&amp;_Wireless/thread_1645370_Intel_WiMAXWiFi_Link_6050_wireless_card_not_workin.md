---
title: "Intel WiMAX/WiFi Link 6050 wireless card not working"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by Tazdeviloo7 on 2010-12-14
I'm dual booting windows 7 64 bit and Ubuntu 10.1 64 bit on my Dell Inspiron 11z with an embedded WiMAX/WiFi Link 6050 series wireless card made from Intel. I only use it for wifi, not 3g or wimax. I installed the latest driver from intellinuxwireless.org, iwlwifi-6050-ucode-41.28.5.1, but it still doesn't seem to work. 
I ran these terminal commands from another thread:

cd Desktop/wlwifi-6050-ucode-9.201.4.1
sudo cp iwlwifi-6050-4.ucode /lib/firmware
sudo chmod 644 /lib/firmware/iwlwifi*
sudo chown root:root /lib/firmware/iwlwifi*
sudo rmmod -f iwlagn
sudo modprobe iwlagn

After running "sudo rmmod -f iwlagn sudo modprobe iwlagn", I get this read out for my wireless card. 

*-network DISABLED
       description: Wireless interface
       product: WiMAX/WiFi Link 6050 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:15:5c:2c:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:90400000-90401fff

In the ubuntu help section it tells me to flip a manual wifi switch to enable it, but pressing my windows wifi button, F2, doesn't appear to do anything while in ubuntu. The only experience I have working with linux is typing some terminal commands on my android phone to root it so any help would be greatly appreciated.

---

### Post by Tazdeviloo7 on 2010-12-14
After doing the previous steps I got the 3G/4G modem to work, but still no wifi.

---

### Post by Tazdeviloo7 on 2010-12-18
Got it working finally, I just need one more terminal command to get it working: sudo linux-backports-moudules-wireless-lucid-generic

---

### Post by JackC64 on 2011-01-03
ive got the same card as you, can you walk me through iit step by step? ive downloaded that driver you mentioned in the first post, how do i install it?

...or maybe someone else could since you haven't been on since you last post...

---

### Post by PatchesTheCaveman on 2011-01-03
All the drivers from intellinuxwifi.org are now included with the mainline Linux kernel.  The latest version can be installed with this command that Tazdeviloo7 alluded to but can't get correct (at least on LTS 10.04 Lucid Lynx):
```
sudo apt-get install linux-backports-moudules-wireless-lucid-generic
```

The correct command for Ubuntu 10.10 Maverick Meerkat is:
```
sudo apt-get install linux-backports-moudules-wireless-maverick-generic
```

---

### Post by phoenixcor on 2011-01-04
i have followed these directions to a t, and have invested a few hours this evening trying to get it right, i followed the last directive 

sudo apt-get install linux-backports-moudules-wireless-lucid-generic

but get the following error message

Couldn't find package linux-backports-moudules-wireless-lucid-generic

I explicitly followed the firmware download directions and nothing, wireless connection is still disabled.  good thing i had the afternoon off.  I have only been using open source for about 9 months, so I am still a bit of a noob, but its things like this that help me learn more.  I would greatly appreciated some direction here as to what I am doing wrong.  running 10.4 dell inspirion

kind regards,

---

### Post by PatchesTheCaveman on 2011-01-04
```
Couldn't find package linux-backports-moudules-wireless-lucid-generic
```
Then you are not running Ubuntu 10.04 Lucid Lynx.  You're probably running 10.10 Maverick Meerkat.  I also provided instructions for downloading the correct package for that version in my last post.

---

### Post by phoenixcor on 2011-01-04
[LEFT]thanks a bunch for your response.  i really wish that was it, and i easily might miss something as obvious at that.  i actually just upgraded to meerkat and tried to install sudo apt get... meerkat.  and i get the same error message,but i just upgraded and i definitely was running lucid.   

what the heck am i missing.  modinfo shows

 modinfo iwlagn
filename:       /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6000g2a-4.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-1000-3.ucode
srcversion:     A52B190E945B17CC5225130
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.35-24-generic SMP mod_unload modversions 686 
parm:           swcrypto50:using crypto in software (default 0 [hardware]) (deprecated) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num50:number of hw queues in 50xx series (deprecated) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable50:disable 50XX 11n functionality (deprecated) (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (deprecated) (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart50:restart firmware in case of error (deprecated) (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)

i deleted much of the alias info for brevity.  i dunno, i am at a loss, but i gotta be close, god bless ubuntu







[/LEFT]

---

### Post by tippyTdizzle on 2011-01-14
phoenixcor, did you solve this issue yet? 

I saw your original post, and must say that I did the same thing for the 6050-series Intel 6052 card wifi/wimax in my Asus K52. And it works. What I don't think I saw mention of in this thread was a Hardware switch. Does your laptop have one? I had to find a solution for mine in a K52 thread, just a simple shell script. 

Maybe it (or looking for something similar elsewhere) will help: [http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

One thing that may have also helped my case was removing the old versions of the ucode from /lib/firmware so you might also try that. (This was because at one point I noticed iwlwifi liked to grab the obsolete versions rather than the newest one, installed in the same fashion as your first post.)

-T:popcorn:

---

### Post by phoenixcor on 2011-01-17
thanks tippyt. I will give that a try.  i thought i might just re-install windows and run it in virtualbox, but im now a soldier for open source, and just wont get down with another os.

---

### Post by qwyzmo on 2011-01-21
I am having the same problems: my 6050 wifi card doesnt work, even after all the above steps.

I also get "Couldn't find package ... " message like phoenixcor above.

question, and i know very little about ubuntu and apt-get, but doesnt apt-get go out over the internet and download the package?  if so, how can i get the package without a working wireless network, are you assuming i hook up a wired connection?

---

### Post by wmunguiam on 2011-02-05
Thanks for the info!

I finally could have WIFI access 



I simply run>

```
root@server:/sys# apt-get install linux-backports-modules-wireless-lucid-generic-pae 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes extras:
  linux-backports-modules-compat-wireless-2.6.34-2.6.32-28-generic-pae
Se instalarán los siguientes paquetes NUEVOS:
  linux-backports-modules-compat-wireless-2.6.34-2.6.32-28-generic-pae
  linux-backports-modules-wireless-lucid-generic-pae
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 2824kB de archivos.
Se utilizarán 8380kB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
Des:1 http://pe.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-backports-modules-compat-wireless-2.6.34-2.6.32-28-generic-pae 2.6.32-28.27 [2819kB]
Des:2 http://pe.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-backports-modules-wireless-lucid-generic-pae 2.6.32.28.32 [4418B]
Descargados 2824kB en 23s (118kB/s)                                                             
Seleccionando el paquete linux-backports-modules-compat-wireless-2.6.34-2.6.32-28-generic-pae previamente no seleccionado.
(Leyendo la base de datos ...  00%
159581 ficheros y directorios instalados actualmente.)
Desempaquetando linux-backports-modules-compat-wireless-2.6.34-2.6.32-28-generic-pae (de .../linux-backports-modules-compat-wireless-2.6.34-2.6.32-28-generic-pae_2.6.32-28.27_i386.deb) ...
Seleccionando el paquete linux-backports-modules-wireless-lucid-generic-pae previamente no seleccionado.
Desempaquetando linux-backports-modules-wireless-lucid-generic-pae (de .../linux-backports-modules-wireless-lucid-generic-pae_2.6.32.28.32_i386.deb) ...
Configurando linux-backports-modules-compat-wireless-2.6.34-2.6.32-28-generic-pae (2.6.32-28.27) ...
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic-pae

Configurando linux-backports-modules-wireless-lucid-generic-pae (2.6.32.28.32) ...
root@server:/sys# 
```


My Driver is:
06:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 5f)


And I chooseed the "PAE" only for any compatibility with my Ubuntu 32bit PAE kernel (I needed to have more than 4GB RAM)

---

### Post by outskut on 2011-03-07
hey, I'm pretty sure the package title is 

linux-backports-modules-wireless-lucid-generic

not

linux-backports-moudules-wireless-lucid-generic 

typo...

so run:
sudo apt-get install linux-backports-modules-wireless-lucid-generic

---

### Post by jwhite530 on 2011-04-03
> **outskut said:**
> hey, I'm pretty sure the package title is 

linux-backports-modules-wireless-lucid-generic

not

linux-backports-moudules-wireless-lucid-generic 

typo...

so run:
sudo apt-get install linux-backports-modules-wireless-lucid-generic

That is correct, however wireless is still not working for me on the same card.  I instead went for linux-backports-modules-wireless-lucid-server since I'm running the server edition (I like to build with LVM which desktop can't do).  However, I still have no wireless.  I have no wlan0 device at all.  Before installing this I did have the wireless icon in my panel but it said wired was not managed and a similar but different message about wireless.

I went ahead and tried the generic kernel instead.  When I booted into that I did have a wlan0 but I can't bring it up or scan with it.

Doing an "iwlist wlan0 scanning" as a non-privileged user shows "wlan0 Failed to read scan data : Network is down".  When running as root it gives "wlan0 Interface doesn't support scanning : Network is down".

I can't do an "ifup wlan0" or "ifconfig wlan0 up", both fail.  Hitting F2 it toggle wireless does nothing.

I don't care if I use the server or generic kernel, I just want this to work.  Here is the output of some commands when using the generic kernel:

ifconfig -a: [http://pastebin.com/a0J5NiTX](http://pastebin.com/a0J5NiTX)
interfaces: [http://pastebin.com/PBsi9zdv](http://pastebin.com/PBsi9zdv)
lsmod: [http://pastebin.com/DzwLtxF6](http://pastebin.com/DzwLtxF6)
lspci -vv: [http://pastebin.com/Tiuay5xZ](http://pastebin.com/Tiuay5xZ)

Ubuntu 10.04 Server x64 2.6.32-30-generic

---

### Post by jwhite530 on 2011-04-03
Well, I got it working with the generic kernel.  I don't know how since I rebooted multiple times during my initial testing, but after booting into my Windows partition and back into Ubuntu it started working all on its own.  I made no other changes since the first reboot after installing the backported driver package, but it works.

Although I do have to ifdown eth0 since it brings that up and tries to send data out of it even when the cable is unplugged.  Whatever.

---

