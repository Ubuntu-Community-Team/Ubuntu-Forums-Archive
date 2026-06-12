---
title: "Broadcom BCM4311"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by 4dr14n on 2013-05-17
Hello everyone, 
Recently I've installed Xubuntuon my pc and I don't know why, but when I tried to install the "drivers" of my wifi card, the pc got blocked. The problem is that when this happened, the pc nor recognise my card nor allows me to install the drivers, it's like they were already installed but no working... I don't know if I explain my problem well or not...
The first time it happened I decided to reinstall the OS, but It has happened again, so I decided to ask for some info.
What I would like to be able to do is to uninstall the drivers (I don't know if it's the proper word) and reinstall it because i can't depend on the wired conexion, and I don't like too much the idea of reinstalling everything again and again...
Thank you so much to everyone for the help you can give me.

---

### Post by 4dr14n on 2013-05-18
Hello again, could someone help me? 
When I said drivers, I meant firmware.
Thank you again to everyone.

---

### Post by 4dr14n on 2013-05-18
I've installed ndiswrapper but now I need and inf file to make my wireless card able to work (I understood reading on the net)... Am I wrong? And, more important, how can I find it? Because I don't have windows anymore on this computer...

---

### Post by Ebia on 2013-05-18
See the instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by mörgæs on 2013-05-18
Please don't bump a thread. 
Without a complete description of your card people can't help you. 
Moving to the network forum.

---

### Post by praseodym on 2013-05-18
Please open a terminal and show these outputs:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
What kind of PC is it?

---

### Post by 4dr14n on 2013-05-18
Sorry if don't do things in the correct way, but I'm new, anyway, I say sorry.
Ok, I'm been playing with this and now I downloaded the firmware, but trying to run the ndiswrapper, appears a problem... it says that the controller is not valid, but it's the good one for my computer (I followed the instructions that Ebian gave me to find it on the SourgeForge web), and opened the exe file with Wine.
So, what could I do? Should I try with different drivers?

---

### Post by praseodym on 2013-05-18
Without more details we can not say more...

---

### Post by 4dr14n on 2013-05-18
Ok, i did a report, I don't know what will be useful or not, but however...
[TABLE]
[TR]
[TD="class: sstitle, colspan: 2"]Computer[/TD]
[/TR]
 [TR]
[TD="class: field"]Processor[/TD]
[TD="class: value"]2x AMD Turion(tm) 64 X2 Mobile Technology TL-56[/TD]
[/TR]
 [TR]
[TD="class: field"]Memory[/TD]
[TD="class: value"]894MB (471MB used)[/TD]
[/TR]
 [TR]
[TD="class: field"]Operating System
[/TD]
[TD="class: value"]Ubuntu 12.04.2 LTS
[/TD]
[/TR]
[/TABLE]

Network controllerBroadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
If you think that other thinks will be necessary just tell me, and, one more time, thank you all and sorry for my ignorance.

---

### Post by 4dr14n on 2013-05-18
Praseodym, I don't understand what you ask me, sorry...

---

### Post by praseodym on 2013-05-18
Install the package "linux-firmware-nonfree" via Software-Center and uninstall "ndiswrapper" and "ndisgtk" (Windows wireless drivers). Reboot after that. This Broadcom device is supported directly from the Linux kernel. Only the firmware is missing.

---

### Post by 4dr14n on 2013-05-18
Thank you praseodym, I did what you said, but it's still no working. I can see that drivers are installed but it doesnt find anything (and there is wifi because my phone does)... 
Thank you again for your time

---

### Post by praseodym on 2013-05-18
Check now:
```

lsmod
iwconfig
dmesg | grep b43
sudo iwlist scan
```

---

### Post by 4dr14n on 2013-05-20
I feel that I'd remember that I created the topic in the absolute beginers users' one =).
Anyway, i'll tell what I see with all the commandos:
lsmod: it appears a list of things but I don't know what worths and what no.
iwconfig: lo no wireless extensions
etho no wireless extensions
dmesg / grep b 43: appeared 3 list of commandos (Options, Supported log facilities and Supported log levels (priorities) )
sudo iwlist scan lo and eth0 --> Interface doesn't support scanning.
I hope this will be useful, but I don't know what to do right now..
One more time, thank you for your time.

---

### Post by Hadaka on 2013-05-20
Hi, you needed to copy and paste the outputs of those commands..

In the mean time..please open a terminal  ctrl/alt/t
COPY !  and paste these commands...one at a time
This removes the ndiswrapper.
```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
 
```
then.. Copy and paste these commands...one at a time.
this installs the driver you need.
```
sudo apt-get install --reinstall linux-firmware-nonfree
modprobe b43
```

when you finish the above..enter this command...
```
lsmod
```
COPY and paste the output.
post it here.
thanks.

---

### Post by 4dr14n on 2013-05-20
ok, let's see, it's in Spanish, I hope it won't be a problem:
adrian@adrian-Latitude-D531:~$ sudo modprobe -rfv ndiswrapper
[sudo] password for adrian: 
FATAL: Module ndiswrapper not found.

:~$ sudo apt-get remove --purge ndisgtk ndiswrapper*
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Nota, seleccionando «ndiswrapper-common» para la expresión regular «ndiswrapper*»
Nota, seleccionando «ndiswrapper-utils» para la expresión regular «ndiswrapper*»
Nota, seleccionando «ndiswrapper-source» para la expresión regular «ndiswrapper*»
Nota, seleccionando «ndiswrapper-dkms» para la expresión regular «ndiswrapper*»
Nota, seleccionando «ndiswrapper-modules-1.9» para la expresión regular «ndiswrapper*»
Nota, seleccionando «ndiswrapper-utils-1.9» para la expresión regular «ndiswrapper*»
El paquete ndiswrapper-common no está instalado, no se eliminará
El paquete ndiswrapper-utils-1.9 no está instalado, no se eliminará
El paquete ndiswrapper-dkms no está instalado, no se eliminará
El paquete ndiswrapper-source no está instalado, no se eliminará
Los siguientes paquetes se ELIMINARÁN:
  ndisgtk*
0 actualizados, 0 se instalarán, 1 para eliminar y 1 no actualizados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ... 159082 ficheros o directorios instalados actualmente.)
Desinstalando ndisgtk ...
Purgando ficheros de configuración de ndisgtk ...


adrian@adrian-Latitude-D531:~$ sudo apt-get install --reinstall linux-firmware-nonfree
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 1 reinstalados, 0 para eliminar y 1 no actualizados.
Se necesita descargar 0 B/3.952 kB de archivos.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
(Leyendo la base de datos ... 159083 ficheros o directorios instalados actualmente.)
Preparando para reemplazar linux-firmware-nonfree 1.11ubuntu2 (usando .../linux-firmware-nonfree_1.11ubuntu2_all.deb) ...
Desempaquetando el reemplazo de linux-firmware-nonfree ...
Configurando linux-firmware-nonfree (1.11ubuntu2) ...


adrian@adrian-Latitude-D531:~$ modprobe b43
WARNING: Error inserting bcma (/lib/modules/3.2.0-43-generic/kernel/drivers/bcma/bcma.ko): Operation not permitted
WARNING: Error inserting cfg80211 (/lib/modules/3.2.0-43-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-43-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
FATAL: Error inserting b43 (/lib/modules/3.2.0-43-generic/kernel/drivers/net/wireless/b43/b43.ko): Operation not permitted


drian@adrian-Latitude-D531:~$ lsmod
Module                  Size  Used by
usbhid                 41937  0 
hid                    77428  1 usbhid
joydev                 17393  0 
dell_wmi               12601  0 
snd_hda_codec_idt      60251  1 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32719  4 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
psmouse                96718  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62218  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
soundcore              14635  1 snd
k8temp                 12905  0 
btusb                  17948  2 
i2c_piix4              13093  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
radeon                733914  2 
rfcomm                 38139  16 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  23 btusb,rfcomm,bnep
ppdev                  12849  0 
video                  19115  0 
wmi                    18744  1 dell_wmi
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 radeon
shpchp                 32265  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12999  0 
tg3                   137318  0 


that's all, I know it's long, anyway, thanks a lot again.

---

### Post by Hadaka on 2013-05-20
hi, that was partly my error.i forgot the sudo..

please COPY and paste these commands

```
sudo modprobe -rfv dell_wmi
sudo modprobe b43
lsmod
```

¿Está trabajando ahora?
thanks.

---

### Post by 4dr14n on 2013-05-21
Upps, sorry I forgot to copy you what appeared... but the first one worked, I mean, something happened (some lines have been writen), but the others 2 no, I write them and nothing happens... I can write on a next line, I appears nothing, nor an error message nor any results... but I tried and it's still no working...
I know this is starting to be so long, but I feel happy in some way to continue going on ;).
Thank you all again!

---

### Post by praseodym on 2013-05-21
Please reboot and show the outputs of:
```

lsmod
iwconfig
rfkill list
dmesg | grep b43
```

---

### Post by 4dr14n on 2013-05-21
adrian@adrian-Latitude-D531:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32719  4 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
dell_laptop            17767  0 
snd_rawmidi            25424  1 snd_seq_midi
dcdbas                 14098  1 dell_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96718  0 
pcmcia                 39826  0 
serio_raw              13027  0 
snd                    62218  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12905  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
btusb                  17948  2 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
i2c_piix4              13093  0 
wl                   3032542  1 
mac_hid                13077  0 
radeon                733914  2 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  16 
bluetooth             158479  23 btusb,bnep,rfcomm
wmi                    18744  1 dell_wmi
ttm                    65344  1 radeon
video                  19115  0 
drm_kms_helper         45466  1 radeon
cfg80211              178877  1 wl
drm                   197641  4 radeon,ttm,drm_kms_helper
binfmt_misc            17292  1 
lib80211               14040  1 wl
i2c_algo_bit           13199  1 radeon
shpchp                 32265  0 
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12999  0 
usbhid                 41937  0 
hid                    77428  1 usbhid
tg3                   137318  0 

adrian@adrian-Latitude-D531:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


adrian@adrian-Latitude-D531:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

adrian@adrian-Latitude-D531:~$ dmesg / grep b43

Usage:
 dmesg [opciones]

Opciones:
 -C, --clear                 clear the kernel ring buffer
 -c, --read-clear            read and clear all messages
 -D, --console-off           disable printing messages to console
 -d, --show-delta            show time delta between printed messages
 -E, --console-on            enable printing messages to console
 -f, --facility <list>       restrict output to defined facilities
 -h, --help                  display this help and exit
 -k, --kernel                display kernel messages
 -l, --level <list>          restrict output to defined levels
 -n, --console-level <level> set level of messages printed to console
 -r, --raw                   print the raw message buffer
 -s, --buffer-size <size>    buffer size to query the kernel ring buffer
 -T, --ctime                 show human readable timestamp (could be 
                             inaccurate if you have used SUSPEND/RESUME)
 -t, --notime                don't print messages timestamp
 -u, --userspace             display userspace messages
 -V, --version               output version information and exit
 -x, --decode                decode facility and level to readable string

Supported log facilities:
    kern - kernel messages
    user - random user-level messages
    mail - mail system
  daemon - system daemons
    auth - security/authorization messages
  syslog - messages generated internally by syslogd
     lpr - line printer subsystem
    news - network news subsystem

Supported log levels (priorities):
   emerg - system is unusable
   alert - action must be taken immediately
    crit - critical conditions
     err - error conditions
    warn - warning conditions
  notice - normal but significant condition
    info - informational
   debug - debug-level messages

---

### Post by praseodym on 2013-05-21
"dmesg | grep b43"

| is the "pipe" made from "AltGr + <"

Edit: Broadcom-STA is still installed

---

### Post by 4dr14n on 2013-05-21
adrian@adrian-Latitude-D531:~$ dmesg | grep b43
adrian@adrian-Latitude-D531:~$

When I put what you said (sorry about that noob's mistake) it occurs nothing... and, I don't know what you mean when you said that it's still installed.
Anyway, thank you one more time for your time.

---

### Post by Hadaka on 2013-05-21
Hi, there is part of a driver still loaded that needs to be removed...
please COPY and paste these commands one at a time..

this removes the driver..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
then.install the new driver..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
¿Está trabajando ahora?
thanks.

---

### Post by 4dr14n on 2013-05-22
Thank you again:

adrian@adrian-Latitude-D531:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for adrian: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete indicado a continuación se instaló de forma automática y ya no es necesarios.
  dkms
Utilice «apt-get autoremove» para eliminarlos.
Los siguientes paquetes se ELIMINARÁN:
  bcmwl-kernel-source*
0 actualizados, 0 se instalarán, 1 para eliminar y 0 no actualizados.
Se liberarán 3.656 kB después de esta operación.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ... 159082 ficheros o directorios instalados actualmente.)
Desinstalando bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purgando ficheros de configuración de bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Procesando disparadores para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-43-generic

adrian@adrian-Latitude-D531:~$ sudo apt-get install linux-firmware-nonfree
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
linux-firmware-nonfree ya está en su versión más reciente.
El paquete indicado a continuación se instaló de forma automática y ya no es necesarios.
  dkms
Utilice «apt-get autoremove» para eliminarlos.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
adrian@adrian-Latitude-D531:~$ sudo modprobe b43
 

One more time, when y write modprobe... nothing happens..
Anyway, one more time, thanks a lot!

---

### Post by praseodym on 2013-05-22
Reboot?

---

### Post by 4dr14n on 2013-05-22
Done and works!!! (I copied it before of rebooting and I was going to say it, but you answered me even faster ;))
Thank you guys again for your time and dedication!

---

