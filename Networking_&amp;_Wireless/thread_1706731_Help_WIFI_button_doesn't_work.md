---
title: "Help WIFI button doesn't work"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by fipem on 2011-03-14
Hi all, I have an HP lapton Pavilion dv3 (4120-ss) and I just can't enable the WIFI button, 

```

felipe@Ubuntu-Laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 64:31:50:6b:2b:12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:44 ioport:2000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 18:f4:6a:9b:97:fd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c2400000-c240ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: easytether0
       serial: 02:00:54:74:68:72
       capabilities: ethernet physical
       configuration: broadcast=yes driver=tun driverversion=1.6 firmware=N/A ip=192.168.117.2 multicast=yes
felipe@Ubuntu-Laptop:~$ 

felipe@Ubuntu-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
felipe@Ubuntu-Laptop:~$ 


felipe@Ubuntu-Laptop:~$ rfkill list
0: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
felipe@Ubuntu-Laptop:~$ rfkill unblock all
felipe@Ubuntu-Laptop:~$ rfkill unblock wifi
felipe@Ubuntu-Laptop:~$ rfkill list
0: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
felipe@Ubuntu-Laptop:~$ 

felipe@Ubuntu-Laptop:~$ sudo ifconfig wlan0 up
[sudo] password for felipe: 
SIOCSIFFLAGS: Error desconocido 132
felipe@Ubuntu-Laptop:~$ 



```

So I just can't enable it, could someone please help me?

---

### Post by fipem on 2011-03-14
Please any help?

---

### Post by fipem on 2011-03-15
Please, I really need help with this issue...

---

### Post by chili555 on 2011-03-15
First of all, be sure the physical wireless switch is actually in the 'On' position. Next, please try:```
[COLOR="Red"]sudo[/COLOR] rfkill unblock all
rfkill list all
```Next, see if the module *hp-wmi* is loaded:```
lsmod | grep hp
```If not, load it:```
sudo modprobe hp-wmi
sudo rfkill unblock all
rfkill list all
```If it is already loaded, let's temporarily remove it:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement? Whatever works, if anything, we can drop into rc.local so it works on boot.

---

### Post by fipem on 2011-03-15
> **chili555 said:**
> First of all, be sure the physical wireless switch is actually in the 'On' position. Next, please try:```
[COLOR="Red"]sudo[/COLOR] rfkill unblock all
rfkill list all
```Next, see if the module *hp-wmi* is loaded:```
lsmod | grep hp
```If not, load it:```
sudo modprobe hp-wmi
sudo rfkill unblock all
rfkill list all
```If it is already loaded, let's temporarily remove it:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```Any improvement? Whatever works, if anything, we can drop into rc.local so it works on boot.

Thanks for the reply!


```
felipe@Ubuntu-Laptop:~$ sudo rfkill unblock all
[sudo] password for felipe: 
felipe@Ubuntu-Laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
felipe@Ubuntu-Laptop:~$ 

```


```
felipe@Ubuntu-Laptop:~$ lsmod | grep hp
hp_wmi                  6435  0 
hp_accel               13600  0 
lis3lv02d              10352  1 hp_accel
led_class               3393  2 ath9k,hp_accel
felipe@Ubuntu-Laptop:~$ 

```

I don't know if it's loaded or not :/ I guess it's loaded as it appear there...


```
felipe@Ubuntu-Laptop:~$ sudo modprobe hp-wmi
[sudo] password for felipe: 
felipe@Ubuntu-Laptop:~$ sudo rfkill unblock all
felipe@Ubuntu-Laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
felipe@Ubuntu-Laptop:~$ sudo modprobe -f hp-wmi
felipe@Ubuntu-Laptop:~$ sudo rfkill unblock all
felipe@Ubuntu-Laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
felipe@Ubuntu-Laptop:~$ 


```

Nope, no improvement... thanks a lot for ur help... any more ideas? why I can't rfkill unblock all???

---

### Post by chili555 on 2011-03-15
> I guess it's loaded as it appear there...Yes, exactly. 

My next suggestion was to ***remove*** it:> If it is already loaded, let's temporarily remove it:
```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all

```
Please proceed.

---

### Post by fipem on 2011-03-15
> **chili555 said:**
> Yes, exactly. 

My next suggestion was to ***remove*** it:Please proceed.

Thanks again for ur help...

```

felipe@Ubuntu-Laptop:~$ sudo rmmod -f hp-wmi
[sudo] password for felipe: 
felipe@Ubuntu-Laptop:~$ sudo rfkill unblock all
felipe@Ubuntu-Laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
felipe@Ubuntu-Laptop:~$ 

```

Nope, it keeps as hard blocked... pretty anoying

---

### Post by chili555 on 2011-03-15
Is the light in the wireless button on or off? White or amber? Is there any setting in the computer's BIOS related to wireless?

---

### Post by fipem on 2011-03-15
> **chili555 said:**
> Is the light in the wireless button on or off? White or amber? Is there any setting in the computer's BIOS related to wireless?

F11 control mute and when I want the laptop to be mute I press F11 (without fn) and it turns orange and the laptop mute.

F12 control wifi and it's all the time orange... can't do anything with it. With or without fn.

I checked the bios for any setting related to it but I didn't find anything.

---

### Post by chili555 on 2011-03-15
[http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Wireless-just-stopped-working/td-p/108779](http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Wireless-just-stopped-working/td-p/108779)

[http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)

I have no further ideas. I am sorry I could not be of more help.

---

### Post by fipem on 2011-03-15
> **chili555 said:**
> [http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Wireless-just-stopped-working/td-p/108779](http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Wireless-just-stopped-working/td-p/108779)

[http://madwifi-project.org/wiki/UserDocs/MiniPCI](http://madwifi-project.org/wiki/UserDocs/MiniPCI)

I have no further ideas. I am sorry I could not be of more help.

Do you know about madwifi? I tried to isntall it but I don't know if I did it right... could you please help me with it and its options?

PS: the wifi buton used to work in windows 7 before I remove it, so I don't think is a hardware issue.

---

### Post by chili555 on 2011-03-15
> I tried to isntall it but I don't know if I did it right... could you please help me with it and its options?Sure. If it activates your wireless switch, I'll be shocked.

Tell me what you've done so far. What did you download? What went wrong?

---

### Post by fipem on 2011-03-15
> **chili555 said:**
> Sure. If it activates your wireless switch, I'll be shocked.

Tell me what you've done so far. What did you download? What went wrong?

I did this (it's in spanish but the codes are pretty the same)

I download madwifi-0.9.4-current from the webpage and uncompress it, then I did as it follows here:

```
pollo@ubuntu:~$ cd Descargas/ 

y descomprimimos el archivo: 

pollo@ubuntu:~/Descargas$ tar xvzf madwifi-hal-0.10.5.6-r4119-20100201.tar.gz 

ya descomprimido entonces entramos a la carpeta: 

pollo@ubuntu:~/Descargas$ cd madwifi-hal-0.10.5.6-r4119-20100201/ 

ya adentro hacemso un make para compilar el install y poder instalarlo 

pollo@ubuntu:~/Descargas/madwifi-hal-0.10.5.6-r4119-20100201$ make 

cuando termine entramos a modo root (esto lo podian hacer desde el principio pero es recomendable no estar mucho tiempo en modo root). 

pollo@ubuntu:~/Descargas/madwifi-hal-0.10.5.6-r4119-20100201$ sudo su 
password: *************************************** 

y en modo root hacemos un make install. 

pollo@ubuntu:~/Descargas/madwifi-hal-0.10.5.6-r4119-20100201$ make install 

al terminar para probar si estamos en buen camino escribimos la siguente linea: 

pollo@ubuntu:/$ sudo modprobe ath_pci 

si no nos regresa nada esq estamos bien y vamos por el buen camino. 

ok bueno despues de esto vamos a hacer q la inicie desde la carga de archivos. 

pollo@ubuntu:/$ sudo gedit /etc/moduless 

y al final del archivo escribimos. 

#inicia configuracion de wireless 
ath_pci 
#finaliza configuracion de wireless 

despues entramos en blacklist.conf 

pollo@ubuntu:/$ sudo gedit /etc/modprobe.d/blacklist.conf 

y al final del archivo agregamos 

blacklist ath5k 

guardamos y cerramos y despues vamos a blacklist-ath_pci.conf 

pollo@ubuntu:/$ sudo gedit /etc/modprobe.d/blacklist-ath_pci.conf 

y comentamos el ath_pci con un gato de tal forma q nos qda asi 

#ath_pci 

y guardamos. 

regresamos a la terminal y vemos si nos arranca la wifi. 
pollo@ubuntu:/$ sudo ifconfig ath0 up 

```

But it didn't work at all and I'm affraid I might done something wrong or worst...

---

### Post by chili555 on 2011-03-15
It doesn't work because it's not correct for your device. The correct module is ath9k, the one that's actually loaded. ath_pci and ath5k are for the Atheros 5-series devices. Yours is a 9-series:> *-network DISABLED
       description: Wireless interface
       product: [COLOR="Red"]AR9[/COLOR]285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
It does no harm to build drivers for devices you don't have; I have several on my system.

---

### Post by fipem on 2011-03-15
> **chili555 said:**
> It doesn't work because it's not correct for your device. The correct module is ath9k, the one that's actually loaded. ath_pci and ath5k are for the Atheros 5-series devices. Yours is a 9-series:It does no harm to build drivers for devices you don't have; I have several on my system.

Do you have any idea why ```
sudo rfkill unblock all
``` doesn't work?

This mean Ubuntu doesn't support Atheros 9-series?

Can it be of any help to change the keyboard layout so maybe another key can enable wifi?

Thanks again for your kind help.

---

### Post by fipem on 2011-03-15
> **chili555 said:**
> It doesn't work because it's not correct for your device. The correct module is ath9k, the one that's actually loaded. ath_pci and ath5k are for the Atheros 5-series devices. Yours is a 9-series:It does no harm to build drivers for devices you don't have; I have several on my system.

Is this ok?

```
felipe@Ubuntu-Laptop:~$ cd Descargas
felipe@Ubuntu-Laptop:~/Descargas$ cd madwifi-0.9.4-r4136-20110203
felipe@Ubuntu-Laptop:~/Descargas/madwifi-0.9.4-r4136-20110203$ sudo make
[sudo] password for felipe: 
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/tools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/tools'
felipe@Ubuntu-Laptop:~/Descargas/madwifi-0.9.4-r4136-20110203$ sudo make installsh scripts/find-madwifi-modules.sh -r 2.6.35-22-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i install || exit 1; \
	done
make[1]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath'
test -d //lib/modules/2.6.35-22-generic/net || mkdir -p //lib/modules/2.6.35-22-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.35-22-generic/net
make[1]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath'
make[1]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_hal'
test -d //lib/modules/2.6.35-22-generic/net || mkdir -p //lib/modules/2.6.35-22-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.35-22-generic/net
make[1]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_hal'
make[1]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate/amrr'
test -d //lib/modules/2.6.35-22-generic/net || mkdir -p //lib/modules/2.6.35-22-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.35-22-generic/net
make[2]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate/amrr'
make[2]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate/onoe'
test -d //lib/modules/2.6.35-22-generic/net || mkdir -p //lib/modules/2.6.35-22-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.35-22-generic/net
make[2]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate/onoe'
make[2]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate/sample'
test -d //lib/modules/2.6.35-22-generic/net || mkdir -p //lib/modules/2.6.35-22-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.35-22-generic/net
make[2]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate/sample'
make[2]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate/minstrel'
test -d //lib/modules/2.6.35-22-generic/net || mkdir -p //lib/modules/2.6.35-22-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.35-22-generic/net
make[2]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate/minstrel'
make[1]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/ath_rate'
make[1]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/net80211'
test -d //lib/modules/2.6.35-22-generic/net || mkdir -p //lib/modules/2.6.35-22-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install -m 0644 $f.ko //lib/modules/2.6.35-22-generic/net; \
	done
make[1]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/net80211'
(export KMODPATH=/lib/modules/2.6.35-22-generic/net; /sbin/depmod -ae 2.6.35-22-generic)
WARNING: -e needs -E or -Fmake -C ./tools  install || exit 1
make[1]: Entering directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
make[1]: Leaving directory `/home/felipe/Descargas/madwifi-0.9.4-r4136-20110203/tools'
felipe@Ubuntu-Laptop:~/Descargas/madwifi-0.9.4-r4136-20110203$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
easytether0  no wireless extensions.

felipe@Ubuntu-Laptop:~/Descargas/madwifi-0.9.4-r4136-20110203$ 

```

I'm just doing stuff that might help...

---

### Post by chili555 on 2011-03-15
> Do you have any idea why
Code:

sudo rfkill unblock all

doesn't work?
Because a terminal command has no ability to physically slide a switch and make a previously open electrical connection. Even if the switch is actually in the 'On' position, the operating system thinks it's 'Off.' 

Many laptops have little drivers that are supposed to accurately translate all the key presses and Fn+ combinations to the kernel as useful information. Yours uses hp-wmi, there is a dell-laptop. My Thinkpad uses thinkpad_acpi. Some of them work quite well; some are pretty poor. I routinely get Dell's wireless working by *removing* dell-laptop.

I have no idea what the issue is; as you can see from the links I gave you, it's even a problem in Windows.

You might experiment by pressing and holding the wireless button as you boot. Then try:```
sudo rfkill unblock all
rfkill list all
```I doubt this is a driver problem; I feel it is more likely an *hp-wmi* problem.> I'm just doing stuff that might help...I doubt it; I doubt it's a driver problem at all.

---

### Post by fipem on 2011-03-15
> **chili555 said:**
> Because a terminal command has no ability to physically slide a switch and make a previously open electrical connection. Even if the switch is actually in the 'On' position, the operating system thinks it's 'Off.' 

Many laptops have little drivers that are supposed to accurately translate all the key presses and Fn+ combinations to the kernel as useful information. Yours uses hp-wmi, there is a dell-laptop. My Thinkpad uses thinkpad_acpi. Some of them work quite well; some are pretty poor. I routinely get Dell's wireless working by *removing* dell-laptop.

I have no idea what the issue is; as you can see from the links I gave you, it's even a problem in Windows.

You might experiment by pressing and holding the wireless button as you boot. Then try:```
sudo rfkill unblock all
rfkill list all
```I doubt this is a driver problem; I feel it is more likely an *hp-wmi* problem.I doubt it; I doubt it's a driver problem at all.

Can it be of any help to upgrade from 10.04 LTS to 10.10?

---

### Post by chili555 on 2011-03-15
Possibly. You can always run the live CD before you commit.

---

### Post by fipem on 2011-03-16
> **chili555 said:**
> Possibly. You can always run the live CD before you commit.

I've updated to ubuntu 10.10 and nothing... 

Maybe updating the bios?

---

### Post by chili555 on 2011-03-16
> **fipem said:**
> I've updated to ubuntu 10.10 and nothing... 

Maybe updating the bios?Did you repeat the tests we tried earlier?```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```

---

### Post by dewapur on 2011-10-03
Hi there, 
It seems I have a similar problem with my thinkpad edge 120 and Ubuntu 11.10 beta. Actually the problem happen after wake on suspend, the wireless doesn't enabled. After read some threads, it is said due to hardware switch problem. I tried to do 
```

$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```But keyboard switch doesn't work either even at normal state or after suspend. It troublesome that I need to restart my laptop to enable it again. Can you help me?

---

