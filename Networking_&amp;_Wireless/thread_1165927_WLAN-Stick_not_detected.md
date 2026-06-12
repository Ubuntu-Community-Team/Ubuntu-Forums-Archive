---
title: "WLAN-Stick not detected?"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Horst724 on 2009-05-21
hi,
first of all, i'm new, and i have a problem...
i installed ubuntu 9.04 on my computer, it also runs windows xp...
now everything is installed but, i can't acces my wifi/wlan connection?
it doesn't detect my stick, i'm using a Fritz!Wlan Stick (germans should know it ;) )
i looked through many threads but didn't find any information how to solve my problem...
and i have to say, i'm a complete n00b concerning linux-systems...
hoping to find some help
Horst ):P

---

### Post by superprash2003 on 2009-05-21
go to your ubuntu terminal (Application->accessories) and type **lshw -C network** , and post its output here ( copy paste )

---

### Post by Horst724 on 2009-05-22
```

*-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:7f:74:b5:62:2f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
here it is :)

---

### Post by benson444 on 2009-05-22
Well, really throwing you in at the deep end here but it looks like you can compile a driver from source code.

Found this: 

[http://forums.debian.net/viewtopic.php?p=92373&](http://forums.debian.net/viewtopic.php?p=92373&)

Links to the driver don't work but I found it here:

[http://download.avm.de/cardware/fritzwlanusb.stick/linux/suse.10.2/](http://download.avm.de/cardware/fritzwlanusb.stick/linux/suse.10.2/)

You'll need to get online using the wired ethernet connection to install the dependencies for compiling. build-essential and so on.

Good luck.

---

### Post by flash63 on 2009-05-22
Hi,
you need ndiswrapper. The linux driver don't work with kernel 2.6.25-* or higher.

Three types exist. What type of the stick do you have?
```
lsusb
```
32bit or 64bit System
```
uname -a
```

The older versions:
ID: 057C:5601  
ID: 057C:6201
(somtimes probs with processpriority of wpa_supplicant while connecting)

Draft-N:
ID: 057C:8401
(modified inf-File needed / 64bit systems require a patch for ndiswrapper 1.54)

More info at [http://wiki.ubuntuusers.de/WLAN/Karten/AVM](http://wiki.ubuntuusers.de/WLAN/Karten/AVM) and
[http://wiki.ubuntuusers.de/FRITZ!WLAN_USB_Stick](http://wiki.ubuntuusers.de/FRITZ!WLAN_USB_Stick) (german)
[http://wiki.ubuntuusers.de/Fritz!WLAN_USB_Stick-N](http://wiki.ubuntuusers.de/Fritz!WLAN_USB_Stick-N) (german)


The deb-packages for **ndiswrapper** and the graphical frontent **ndisgtk** comes with the ubuntu installation disk. Folder ~/pool/main/n/

---

### Post by Horst724 on 2009-05-22
okay so i did like you said flash63 and i'm pretty happy cause now it says driver is installed
but still, i can't figure out how to make him join my wifi-net work
but anyway: thanks for that fast and good advices
horst

---

### Post by flash63 on 2009-05-22
Please show us the following informations about your system an the installed driver.
```
ndsiwrapper -l >> Horst724_01.txt
sudo modprobe ndiswrapper >> Horst724_01.txt
dmesg | grep ndis >> Horst724_01.txt
iwconfig >> Horst724_01.txt
sudo iwlist wlan0 scan >> Horst724_01.txt
```The terminal output was redirected to the text file **Horst724_01.txt** in your home folder. Copy it to WinXP and the content of the file with [code]-tags also here. 

Thanks
Rainer

---

### Post by Horst724 on 2009-05-22
here it is, but i didn't work as it should have so i just copied it from the terminal...

```


fwlan : driver installed
    device (057C:6201) present
tusb1150 : driver installed

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Could not open '/lib/modules/2.6.28-11-generic/misc/ndiswrapper.ko': No such file or directory

Aufruf: dmesg [-c] [-n Level] [-s Puffergröße]

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


wlan      Interface doesn't support scanning.


```
bitte schön,

---

### Post by flash63 on 2009-05-22
Do you speak german?

Something wrong with your source list and ndiswrapper installation. The right path to ndiswrapper must be
/lib/modules/2.6.28-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko

Deinstall ndiswrapper and the wrong driver completely:
```
sudo apt-get remove --purge ndiswrapper-utils-1.9 ndiswrapper-common ndisgtk
sudo rm -r /etc/ndiswrapper 
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm -rf /lib/modules/$(uname -r)/kernel/ubuntu/ndiswrapper

```
Reinstall the linux-kernel-image:
[http://ge.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-11-generic_2.6.28-11.42_i386.deb](http://ge.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-11-generic_2.6.28-11.42_i386.deb)
and ndiswrapper:
[http://ge.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb](http://ge.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb)
[http://ge.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb](http://ge.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb)
[http://ge.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb](http://ge.archive.ubuntu.com/ubuntu/pool/main/n/ndisgtk/ndisgtk_0.8.4-1_i386.deb)

(Download the pakages and install by double clicking)

Download the for ndiswrapper optimized 32bit driver
[http://www.elektronenblitz63.de/download/avmmod_32.tar.gz](http://www.elektronenblitz63.de/download/avmmod_32.tar.gz)
an copy it into your home folder. Install:
```
tar xvf avmmod_32.tar.gz
sudo ndiswrapper -i avmmod_32/fwlan.inf
sudo ndiswrapper -ma
ndiswrapper -l
sudo modprobe ndiswrapper
iwconfig
sudo iwlist wlan0 scan

```

---

### Post by Horst724 on 2009-05-23
geht immer noch nicht ... das kenne ich aber auch von meinem windoof und meinem mac, dass sachen genau bei mir nicht gehen...

okay so i'll post the terminal extract here:
```

fritz@Ubuntu:~$ tar xvf avmmod_32.tar.gz
avmmod_32/fwlan.inf~
avmmod_32/fwlanusb.sys
avmmod_32/FwUSB1b.bin
avmmod_32/fwlan.inf
fritz@Ubuntu:~$ sudo apt-get remove --purge ndiswrapper-utils-1.9 ndiswrapper-common ndisgtk
[sudo] password for fritz: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Lese Status-Informationen ein... Fertig
Die folgenden Pakete werden ENTFERNT:
  ndisgtk* ndiswrapper-common* ndiswrapper-utils-1.9*
0 aktualisiert, 0 neu installiert, 3 zu entfernen und 0 nicht aktualisiert.
Nach dieser Operation werden 676kB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 102549 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne ndisgtk ...
Lösche Konfigurationsdateien von ndisgtk ...
Entferne ndiswrapper-utils-1.9 ...
Entferne ndiswrapper-common ...
dpkg - Warnung: Während Entfernens von ndiswrapper-common ist Verzeichnis »/etc/ndiswrapper« nicht leer, wird daher nicht gelöscht.
Verarbeite Trigger für man-db ...
fritz@Ubuntu:~$ sudo rm -r /etc/ndiswrapper
fritz@Ubuntu:~$ sudo rm -r /etc/modprobe.d/ndiswrapper
fritz@Ubuntu:~$ sudo rm -rf /lib/modules/$(uname -r)/kernel/ubuntu/ndiswrapper
fritz@Ubuntu:~$ sudo ndiswrapper -i avmmod_32/fwlan.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing fwlan ...
fritz@Ubuntu:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper
fritz@Ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
fwlan : driver installed
    device (057C:6201) present
fritz@Ubuntu:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Could not open '/lib/modules/2.6.28-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
fritz@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

fritz@Ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


```

---

### Post by flash63 on 2009-05-24
Hallo,
der Treiber ist ok. Allerdings kann ndiswrapper nicht gestartet werden, da das System das Modul immer noch im falschen Verzeichnis abgelegt hat, bzw. sucht.
> /lib/modules/2.6.28-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or directory
Wurde das Kernelimage neu installiert?

Suche ansonsten einfach das Modul ndiswrapper.ko und kopiere es in das geforderte Verzeichnis welches ggf. noch angelegt werden muss. Verwende dazu einfach den Nautilus Dateimanger als root```
locate ndiswrapper.ko
sudo nautilus
```Versuche nun erneut ndiswrapper zu starten. Ansonsten ist bei der Installation oder dem Systemupgrade etwas schief gelaufen, und das System sollte neu installiert werden.

---

### Post by Horst724 on 2009-05-26
okay, fehler gefunden, der ordner ndiswrapper existiert im odner ubunuu nicht

ich hau ubuntu nochmal komplett neu rauf und mach dann nochmal wie vorgegeben :D

danke für die Hilfe

---

### Post by Sven6210 on 2009-12-01
I am also struggling with Ubuntu 9.10 Karmic Koala and the AVM Fritz!WAN USB Stick. I know that the AVM driver for Linux is not working with the latest kernel however I also struggle to install the NDISWRAPPER version. I tried it with the XP driver, the Windows 7 driver an the alternate driver mentioned above but none works properly.

I can see WLAN access points but I can not connect to them. Does anybody have an idea?

---

