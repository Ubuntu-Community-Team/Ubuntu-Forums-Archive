---
title: "Only temporary wifi with dell 3721 and ubuntu 13.04"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by honeycup on 2013-05-26
hi. since i upgraded ubuntu 12.10 to 13.04 i can use wifi only temponary. There is a "_Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)_" inside my dell 3721 laptop.
I installed the driver with this command:

> sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
iwconfig

That worked and I was able to use Wifi. But when I reboot my laptop sometimes I can see Wifi networks and connect and sometimes I can't see any network even I'm home and can connect to the network with other devices. Can also connect when I use Windows with the same laptop, so its a ubuntu issue. Which information do you need to find a solution for this?

---

### Post by Hadaka on 2013-05-26
Hi, please do..
```
sudo modprobe wl
```
are connections now visable?
*If yes then do..
```
echo 'wl' | sudo tee -a /etc/modules
```
this will load the wl module at boot.
thanks.

---

### Post by honeycup on 2013-05-27
No, they arent visible. There is still only "Ethernet" in the connections, no Wifi.

---

### Post by Hadaka on 2013-05-27
Is the wireless icon...upper right..next to envelope visable?
is that where you are clicking to see networks?
if yes..
then..uncheck "Enable wireless"
then..re-check"Enable wireless"
can you see networks now?

---

### Post by honeycup on 2013-05-27
I mean that icon but there is no "wireless" now. It was there last week, my laptop was without power for the weekend and after I came back its gone. There is only the point ethernet now, no wifi.

---

### Post by Hadaka on 2013-05-27
ok, so at this point..you have no wireless at all.
please post the output of..
```
uname -a
lsmod
rfkill list
```
also please try with the ethernet cable unplugged
```
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
did the wireless icon return?

---

### Post by honeycup on 2013-05-27
> seb@Dell:~$ uname -a
Linux Dell 3.8.0-22-generic #33-Ubuntu SMP Thu May 16 15:17:14 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


seb@Dell:~$ lsmod
Module                  Size  Used by
usb_storage            57204  1 
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320371  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
binfmt_misc            17500  1 
nls_iso8859_1          12713  1 
joydev                 17377  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
snd_hda_codec_hdmi     36913  1 
i915                  600351  3 
snd_hda_codec_realtek    78399  1 
wl                   2573614  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm_intel             132891  0 
coretemp               13355  0 
lp                     17759  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
btusb                  22474  0 
snd_rawmidi            30180  1 snd_seq_midi
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
parport                46345  3 lp,ppdev,parport_pc
drm_kms_helper         49394  1 i915
bluetooth             228619  22 bnep,btusb,rfcomm
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
drm                   286313  4 i915,drm_kms_helper
rts5139               352481  0 
psmouse                95870  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videodev              129260  2 uvcvideo,videobuf2_core
cryptd                 20373  1 ghash_clmulni_intel
lib80211               14352  1 wl
mac_hid                13205  0 
snd_timer              29425  2 snd_pcm,snd_seq
microcode              22881  0 
mei                    41158  0 
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
dell_wmi               12681  0 
lpc_ich                17061  0 
sparse_keymap          13890  1 dell_wmi
wmi                    19070  1 dell_wmi
dell_laptop            17369  0 
i2c_algo_bit           13413  1 i915
dcdbas                 14397  1 dell_laptop
serio_raw              13215  0 
video                  19390  1 i915
r8169                  67446  0 
ahci                   25731  3 
libahci                31364  1 ahci


seb@Dell:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


seb@Dell:~$ sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for seb: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
0 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 19 nicht aktualisiert.
Es müssen 1.346 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Fehl [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/restricted bcmwl-kernel-source amd64 6.20.155.1+bdcom-0ubuntu6
  Beim Auflösen von »archive.ubuntu.com:http« ist etwas Schlimmes passiert (-11 - Systemfehler).
Fehlschlag beim Holen von [http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb)  Beim Auflösen von »archive.ubuntu.com:http« ist etwas Schlimmes passiert (-11 - Systemfehler).
E: Einige Archive konnten nicht heruntergeladen werden; vielleicht »apt-get update« ausführen oder mit »--fix-missing« probieren?


seb@Dell:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
0 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 19 nicht aktualisiert.
Es müssen 1.346 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 0 B Plattenplatz zusätzlich benutzt.
Holen: 1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/restricted bcmwl-kernel-source amd64 6.20.155.1+bdcom-0ubuntu6 [1.346 kB]
Es wurden 1.346 kB in 1 s geholt (952 kB/s).     
(Lese Datenbank ... 255481 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu6 (durch .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb) ...
Removing all DKMS Modules
rmdir: konnte »“ nicht entfernen: Datei oder Verzeichnis nicht gefunden
Done.
Ersatz für bcmwl-kernel-source wird entpackt ...
bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) wird eingerichtet ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.8.0-22-generic
Building for architecture x86_64
Building initial module for 3.8.0-22-generic
Done.


wl:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.8.0-22-generic/updates/dkms/


depmod....


DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Trigger für initramfs-tools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic


seb@Dell:~$ sudo modprobe wl





Still no Wifi icon, only ethernet. Tried sudo apt-get install --reinstall bcmwl-kernel-source while beeing offline and online but no change.

---

### Post by Hadaka on 2013-05-27
ok, lets remove and then reinstall.
please do..
from a wired connection..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rfv wl
```
then..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe -v wl
```
```
dmesg | grep wl
```
thanks.

---

### Post by honeycup on 2013-05-27
Still no Wifi networks to see.

> seb@Dell:~$ sudo apt-get remove --purge bcmwl-kernel-source[sudo] password for seb: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete werden ENTFERNT:
  bcmwl-kernel-source*
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 19 nicht aktualisiert.
Nach dieser Operation werden 4.279 kB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 255480 Dateien und Verzeichnisse sind derzeit installiert.)
Entfernen von bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Löschen der Konfigurationsdateien von bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Trigger für initramfs-tools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic
seb@Dell:~$ sudo modprobe -rfv wl
FATAL: Module wl not found.
seb@Dell:~$ sudo apt-get install bcmwl-kernel-source
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden NEUEN Pakete werden installiert:
  bcmwl-kernel-source
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 19 nicht aktualisiert.
Es müssen noch 0 B von 1.346 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 4.279 kB Plattenplatz zusätzlich benutzt.
Vormals nicht ausgewähltes Paket bcmwl-kernel-source wird gewählt.
(Lese Datenbank ... 255413 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von bcmwl-kernel-source (aus .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb) ...
bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) wird eingerichtet ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-22-generic
Building for architecture x86_64
Building initial module for 3.8.0-22-generic
Done.


wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.8.0-22-generic/updates/dkms/


depmod....


DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Trigger für initramfs-tools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic
seb@Dell:~$ sudo modprobe -v wl
seb@Dell:~$ dmesg | grep wl
[   17.990249] wl: module license 'unspecified' taints kernel.

---

### Post by praseodym on 2013-05-27
Please uninstall bcmwl-kernel-source again and install the patched driver from here:

[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Version-V5-100-82-112-DKMS)

Check Kernel 3.x and 32 or 64 bit.

---

### Post by honeycup on 2013-05-27
Some errors and not working:

> seb@Dell:~$ sudo apt-get remove bcmwl-kernel-source[sudo] password for seb: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete werden ENTFERNT:
  bcmwl-kernel-source
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 19 nicht aktualisiert.
Nach dieser Operation werden 4.279 kB Plattenplatz freigegeben.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 255480 Dateien und Verzeichnisse sind derzeit installiert.)
Entfernen von bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Trigger für initramfs-tools werden verarbeitet ...
update-initramfs: Generating /boot/initrd.img-3.8.0-22-generic
seb@Dell:~$ sudo mkdir /usr/src/hybrid-portsrc_x86_64-5.100.82.112
mkdir: das Verzeichnis »/usr/src/hybrid-portsrc_x86_64-5.100.82.112“ kann nicht angelegt werden: Die Datei existiert bereits
seb@Dell:~$ wget [http://media.cdn.ubuntu-de.org/forum/attachments/10/06/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/10/06/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz)
--2013-05-27 19:46:53--  [http://media.cdn.ubuntu-de.org/forum/attachments/10/06/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/10/06/2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz)
Auflösen des Hostnamen »media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)«... 213.95.41.13, 2001:780:0:25:206:5bff:fe04:8bcb
Verbindungsaufbau zu media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.13|:80... verbunden.
HTTP-Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 1179909 (1,1M) [application/octet-stream]
In »»2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz«« speichern.


100%[======================================>] 1.179.909   1,36MB/s   in 0,8s   


2013-05-27 19:46:54 (1,36 MB/s) - »»2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz«« gespeichert [1179909/1179909]


seb@Dell:~$ sudo tar xvf 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-5.100.82.112 
src/
src/.tmp_versions/
src/src/
src/lib/
src/src/wl/
src/src/shared/
src/src/include/
src/src/wl/sys/
src/src/include/proto/
src/.built-in.o.cmd
src/.wl.o.cmd
src/.wl.mod.o.cmd
src/.wl.ko.cmd
src/Makefile
src/.tmp_versions/wl.mod
src/lib/LICENSE.txt
src/lib/wlc_hybrid.o_shipped
src/src/shared/linux_osl.c
src/src/include/osl.h
src/src/include/wlioctl.h
src/src/include/linuxver.h
src/src/include/linux_osl.h
src/src/include/bcmcdc.h
src/src/include/bcmwifi.h
src/src/include/epivers.h
src/src/include/bcmdefs.h
src/src/include/bcmendian.h
src/src/include/typedefs.h
src/src/include/packed_section_end.h
src/src/include/pcicfg.h
src/src/include/packed_section_start.h
src/src/include/bcmutils.h
src/src/wl/sys/wl_iw.h
src/src/wl/sys/wlc_types.h
src/src/wl/sys/wlc_key.h
src/src/wl/sys/wlc_pub.h
src/src/wl/sys/wl_cfg80211.h
src/src/wl/sys/wl_cfg80211.c
src/src/wl/sys/wl_dbg.h
src/src/wl/sys/wl_linux.h
src/src/wl/sys/wl_iw.c
src/src/wl/sys/wl_export.h
src/src/wl/sys/wlc_ethereal.h
src/src/include/proto/wpa.h
src/src/include/proto/ieee80211_radiotap.h
src/src/include/proto/ethernet.h
src/src/include/proto/802.1d.h
src/src/include/proto/bcmevent.h
src/src/include/proto/bcmeth.h
src/src/include/proto/802.11.h
dkms.conf
Makefile
src/src/wl/sys/wl_linux.c
seb@Dell:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden NEUEN Pakete werden installiert:
  build-essential
0 aktualisiert, 1 neu installiert, 3 erneut installiert, 0 zu entfernen und 19 nicht aktualisiert.
Es müssen noch 78,5 kB von 1.079 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 37,9 kB Plattenplatz zusätzlich benutzt.
Holen: 1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main build-essential amd64 11.6ubuntu4 [5.672 B]
Holen: 2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main dkms all 2.2.0.3-1.1ubuntu2 [72,8 kB]
Es wurden 78,5 kB in 0 s geholt (323 kB/s).
Vormals nicht ausgewähltes Paket build-essential wird gewählt.
(Lese Datenbank ... 255413 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von build-essential (aus .../build-essential_11.6ubuntu4_amd64.deb) ...
Vorbereitung zum Ersetzen von dkms 2.2.0.3-1.1ubuntu2 (durch .../dkms_2.2.0.3-1.1ubuntu2_all.deb) ...
Ersatz für dkms wird entpackt ...
Vorbereitung zum Ersetzen von linux-headers-3.8.0-22-generic 3.8.0-22.33 (durch .../linux-headers-3.8.0-22-generic_3.8.0-22.33_amd64.deb) ...
Ersatz für linux-headers-3.8.0-22-generic wird entpackt ...
Vorbereitung zum Ersetzen von linux-headers-generic 3.8.0.22.38 (durch .../linux-headers-generic_3.8.0.22.38_amd64.deb) ...
Ersatz für linux-headers-generic wird entpackt ...
Trigger für man-db werden verarbeitet ...
build-essential (11.6ubuntu4) wird eingerichtet ...
dkms (2.2.0.3-1.1ubuntu2) wird eingerichtet ...
linux-headers-3.8.0-22-generic (3.8.0-22.33) wird eingerichtet ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
linux-headers-generic (3.8.0.22.38) wird eingerichtet ...
seb@Dell:~$ sudo dkms add -m hybrid-portsrc_x86_64 -v 5.100.82.112
Error! DKMS tree already contains: hybrid-portsrc_x86_64-5.100.82.112
You cannot add the same module/version combo more than once.
seb@Dell:~$ sudo dkms build -m hybrid-portsrc_x86_64 -v 5.100.82.112
Module hybrid-portsrc_x86_64/5.100.82.112 already built for kernel 3.8.0-22-generic/4
seb@Dell:~$ sudo dkms install -m hybrid-portsrc_x86_64 -v 5.100.82.112 
Module hybrid-portsrc_x86_64/5.100.82.112 already installed on kernel 3.8.0-22-generic/x86_64
seb@Dell:~$ 

---

### Post by praseodym on 2013-05-27
Uninstallation:
```

rm 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gz
sudo dkms remove -m hybrid-portsrc_x86_64 -v 5.100.82.112 --all
sudo rm -r /usr/src/hybrid-portsrc_x86_64-5.100.82.112
```
I found a solution here:

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1107155](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1107155)

On #5:
```

sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```

---

### Post by honeycup on 2013-05-27
Not working...

> seb@Dell:~$ rm 2865859-hybrid-portsrc_x86_64-v5_100_82_112_patched_dkms.tar.gzseb@Dell:~$ sudo dkms remove -m hybrid-portsrc_x86_64 -v 5.100.82.112 --all
[sudo] password for seb: 
Sorry, try again.
[sudo] password for seb: 


-------- Uninstall Beginning --------
Module:  hybrid-portsrc_x86_64
Version: 5.100.82.112
Kernel:  3.5.0-27-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-27-generic/
rmdir: konnte »“ nicht entfernen: Datei oder Verzeichnis nicht gefunden
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod........


DKMS: uninstall completed.


-------- Uninstall Beginning --------
Module:  hybrid-portsrc_x86_64
Version: 5.100.82.112
Kernel:  3.8.0-21-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-21-generic/
rmdir: konnte »“ nicht entfernen: Datei oder Verzeichnis nicht gefunden
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod........


DKMS: uninstall completed.


-------- Uninstall Beginning --------
Module:  hybrid-portsrc_x86_64
Version: 5.100.82.112
Kernel:  3.8.0-22-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.8.0-22-generic/
rmdir: konnte »“ nicht entfernen: Datei oder Verzeichnis nicht gefunden
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod........


DKMS: uninstall completed.


------------------------------
Deleting module version: 5.100.82.112
completely from the DKMS tree.
------------------------------
Done.
seb@Dell:~$ sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden NEUEN Pakete werden installiert:
  b43-fwcutter firmware-b43-lpphy-installer
0 aktualisiert, 2 neu installiert, 0 zu entfernen und 19 nicht aktualisiert.
Es müssen 23,0 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 120 kB Plattenplatz zusätzlich benutzt.
Holen: 1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/main b43-fwcutter amd64 1:015-14 [19,6 kB]
Holen: 2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/multiverse firmware-b43-lpphy-installer all 1:015-14 [3.434 B]
Es wurden 23,0 kB in 0 s geholt (148 kB/s).             
Vormals nicht ausgewähltes Paket b43-fwcutter wird gewählt.
(Lese Datenbank ... 255422 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von b43-fwcutter (aus .../b43-fwcutter_1%3a015-14_amd64.deb) ...
Vormals nicht ausgewähltes Paket firmware-b43-lpphy-installer wird gewählt.
Entpacken von firmware-b43-lpphy-installer (aus .../firmware-b43-lpphy-installer_1%3a015-14_all.deb) ...
Trigger für man-db werden verarbeitet ...
b43-fwcutter (1:015-14) wird eingerichtet ...
firmware-b43-lpphy-installer (1:015-14) wird eingerichtet ...
No chroot environment found. Starting normal installation
No supported card found.
Use proper b43 or b43legacy firmware.
Aborting.
seb@Dell:~$ 




---

### Post by praseodym on 2013-05-27
Try additionally the package "firmware-b43-installer"

---

### Post by honeycup on 2013-05-27
> seb@Dell:~$ sudo apt-get install firmware-b43-installer
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete werden ENTFERNT:
  firmware-b43-lpphy-installer
Die folgenden NEUEN Pakete werden installiert:
  firmware-b43-installer
0 aktualisiert, 1 neu installiert, 1 zu entfernen und 19 nicht aktualisiert.
Es müssen 3.532 B an Archiven heruntergeladen werden.
Nach dieser Operation werden 1.024 B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
Holen: 1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/multiverse firmware-b43-installer all 1:015-14 [3.532 B]
Es wurden 3.532 B in 0 s geholt (33,9 kB/s).      
(Lese Datenbank ... 255433 Dateien und Verzeichnisse sind derzeit installiert.)
Entfernen von firmware-b43-lpphy-installer ...
Vormals nicht ausgewähltes Paket firmware-b43-installer wird gewählt.
(Lese Datenbank ... 255429 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacken von firmware-b43-installer (aus .../firmware-b43-installer_1%3a015-14_all.deb) ...
firmware-b43-installer (1:015-14) wird eingerichtet ...
No chroot environment found. Starting normal installation
seb@Dell:~$ 




 .

---

### Post by praseodym on 2013-05-27
Reboot and check
```

lsmod
iwconfig
sudo iwlist scan
dmesg | egrep 'wl|bcma|brcm|[F]irm'
```

---

### Post by honeycup on 2013-05-27
> seb@Dell:~$ lsmodModule                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320371  3 vboxnetadp,vboxnetflt,vboxpci
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  12 
binfmt_misc            17500  1 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
joydev                 17377  0 
kvm_intel             132891  0 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   443165  1 kvm_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ghash_clmulni_intel    13259  0 
i915                  600351  3 
cryptd                 20373  1 ghash_clmulni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
uvcvideo               80847  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
coretemp               13355  0 
btusb                  22474  0 
lp                     17759  0 
mac_hid                13205  0 
videobuf2_core         40513  1 uvcvideo
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  19 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         49394  1 i915
psmouse                95870  0 
drm                   286313  4 i915,drm_kms_helper
videodev              129260  2 uvcvideo,videobuf2_core
rts5139               352481  0 
microcode              22881  0 
bluetooth             228619  22 bnep,btusb,rfcomm
parport                46345  3 lp,ppdev,parport_pc
mei                    41158  0 
lpc_ich                17061  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
wmi                    19070  1 dell_wmi
i2c_algo_bit           13413  1 i915
dell_laptop            17369  0 
dcdbas                 14397  1 dell_laptop
video                  19390  1 i915
soundcore              12680  1 snd
serio_raw              13215  0 
r8169                  67446  0 
ahci                   25731  3 
libahci                31364  1 ahci
seb@Dell:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


seb@Dell:~$ sudo iwlist scan
[sudo] password for seb: 
Sorry, try again.
[sudo] password for seb: 
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


seb@Dell:~$ 




.

---

### Post by praseodym on 2013-05-27
Check:
```

egrep 'b43|bcma|brcm' /etc/modprobe.d/*
sudo modprobe -v b43
dmesg | grep b43
```

---

### Post by honeycup on 2013-05-27
> seb@Dell:~$ egrep 'b43|bcma|brcm' /etc/modprobe.d/*
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf:blacklist b43
/etc/modprobe.d/blacklist.conf:blacklist brcm80211
/etc/modprobe.d/blacklist.conf:blacklist bcma
/etc/modprobe.d/blacklist.conf:blacklist brcmwl
/etc/modprobe.d/broadcom-sta-dkms.conf:blacklist b43legacy
/etc/modprobe.d/broadcom-sta-dkms.conf:blacklist b43
/etc/modprobe.d/broadcom-sta-dkms.conf:blacklist brcm80211
/etc/modprobe.d/broadcom-sta-dkms.conf:blacklist brcmsmac
/etc/modprobe.d/wireless-bcm43142-dkms.conf:blacklist b43legacy
/etc/modprobe.d/wireless-bcm43142-dkms.conf:blacklist b43
/etc/modprobe.d/wireless-bcm43142-dkms.conf:blacklist brcm80211
/etc/modprobe.d/wireless-bcm43142-dkms.conf:blacklist brcmsmac
seb@Dell:~$ sudo modprobe -v b43
[sudo] password for seb: 
Sorry, try again.
[sudo] password for seb: 
insmod /lib/modules/3.8.0-22-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/drivers/net/wireless/b43/b43.ko 
seb@Dell:~$ 

.

---

### Post by praseodym on 2013-05-27
dmesg output please

---

### Post by honeycup on 2013-05-28
Here it is:

> seb@Dell:~$ dmesg output
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-22-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #33-Ubuntu SMP Thu May 16 15:17:14 UTC 2013 (Ubuntu 3.8.0-22.33-generic 3.8.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=9cce131a-c0dd-4480-a9d6-de0066e279cf ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x000000009ffaffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009ffb0000-0x00000000a13affff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000a13b0000-0x00000000a9dbefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000a9dbf000-0x00000000aaebefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000aaebf000-0x00000000aafbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000aafbf000-0x00000000aaffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000aafff000-0x00000000aaffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ab000000-0x00000000af9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000014f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0xaaffe000  ACPI 2.0=0xaaffe014  SMBIOS=0xaaebef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006f000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000088000) (0MB)
[    0.000000] efi: mem04: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem05: type=2, attr=0xf, range=[0x0000000000100000-0x0000000001446000) (19MB)
[    0.000000] efi: mem06: type=7, attr=0xf, range=[0x0000000001446000-0x0000000002000000) (11MB)
[    0.000000] efi: mem07: type=2, attr=0xf, range=[0x0000000002000000-0x0000000003346000) (19MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x0000000003346000-0x0000000020000000) (460MB)
[    0.000000] efi: mem09: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000020200000-0x0000000036124000) (351MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x0000000036124000-0x000000003708a000) (15MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x000000003708a000-0x0000000040004000) (143MB)
[    0.000000] efi: mem13: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x0000000040005000-0x00000000753c0000) (851MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x00000000753c0000-0x000000009e3c0000) (656MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x000000009e3c0000-0x000000009e3e0000) (0MB)
[    0.000000] efi: mem17: type=7, attr=0xf, range=[0x000000009e3e0000-0x000000009efd4000) (11MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x000000009efd4000-0x000000009ffb0000) (15MB)
[    0.000000] efi: mem19: type=0, attr=0xf, range=[0x000000009ffb0000-0x00000000a13b0000) (20MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x00000000a13b0000-0x00000000a15a1000) (1MB)
[    0.000000] efi: mem21: type=1, attr=0xf, range=[0x00000000a15a1000-0x00000000a15bf000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x00000000a15bf000-0x00000000a62ab000) (76MB)
[    0.000000] efi: mem23: type=4, attr=0xf, range=[0x00000000a62ab000-0x00000000a62e8000) (0MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x00000000a62e8000-0x00000000a62fc000) (0MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x00000000a62fc000-0x00000000a734f000) (16MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x00000000a734f000-0x00000000a7353000) (0MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x00000000a7353000-0x00000000a7485000) (1MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000a7485000-0x00000000a7486000) (0MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x00000000a7486000-0x00000000a74c1000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000a74c1000-0x00000000a74c3000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x00000000a74c3000-0x00000000a74c4000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x00000000a74c4000-0x00000000a74c6000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x00000000a74c6000-0x00000000a74c9000) (0MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x00000000a74c9000-0x00000000a74ca000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x00000000a74ca000-0x00000000a7904000) (4MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x00000000a7904000-0x00000000a7905000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x00000000a7905000-0x00000000a791b000) (0MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x00000000a791b000-0x00000000a791d000) (0MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x00000000a791d000-0x00000000a7e0f000) (4MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x00000000a7e0f000-0x00000000a7e15000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x00000000a7e15000-0x00000000a95bf000) (23MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x00000000a95bf000-0x00000000a9a06000) (4MB)
[    0.000000] efi: mem43: type=2, attr=0xf, range=[0x00000000a9a06000-0x00000000a9a10000) (0MB)
[    0.000000] efi: mem44: type=3, attr=0xf, range=[0x00000000a9a10000-0x00000000a9dbf000) (3MB)
[    0.000000] efi: mem45: type=5, attr=0x800000000000000f, range=[0x00000000a9dbf000-0x00000000a9f2c000) (1MB)
[    0.000000] efi: mem46: type=5, attr=0x800000000000000f, range=[0x00000000a9f2c000-0x00000000a9f2f000) (0MB)
[    0.000000] efi: mem47: type=6, attr=0x800000000000000f, range=[0x00000000a9f2f000-0x00000000aa0b5000) (1MB)
[    0.000000] efi: mem48: type=5, attr=0x800000000000000f, range=[0x00000000aa0b5000-0x00000000aa1bf000) (1MB)
[    0.000000] efi: mem49: type=6, attr=0x800000000000000f, range=[0x00000000aa1bf000-0x00000000aa2ae000) (0MB)
[    0.000000] efi: mem50: type=6, attr=0x800000000000000f, range=[0x00000000aa2ae000-0x00000000aa3bf000) (1MB)
[    0.000000] efi: mem51: type=0, attr=0xf, range=[0x00000000aa3bf000-0x00000000aadf4000) (10MB)
[    0.000000] efi: mem52: type=0, attr=0xf, range=[0x00000000aadf4000-0x00000000aaebf000) (0MB)
[    0.000000] efi: mem53: type=10, attr=0xf, range=[0x00000000aaebf000-0x00000000aafa1000) (0MB)
[    0.000000] efi: mem54: type=10, attr=0xf, range=[0x00000000aafa1000-0x00000000aafbf000) (0MB)
[    0.000000] efi: mem55: type=9, attr=0xf, range=[0x00000000aafbf000-0x00000000aafe0000) (0MB)
[    0.000000] efi: mem56: type=9, attr=0xf, range=[0x00000000aafe0000-0x00000000aafff000) (0MB)
[    0.000000] efi: mem57: type=4, attr=0xf, range=[0x00000000aafff000-0x00000000ab000000) (0MB)
[    0.000000] efi: mem58: type=7, attr=0xf, range=[0x0000000100000000-0x000000014f600000) (1270MB)
[    0.000000] efi: mem59: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem60: type=0, attr=0x0, range=[0x00000000ab000000-0x00000000afa00000) (74MB)
[    0.000000] efi: mem61: type=11, attr=0x8000000000000001, range=[0x00000000e0000000-0x00000000f0000000) (256MB)
[    0.000000] efi: mem62: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb04000) (0MB)
[    0.000000] efi: mem63: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem64: type=11, attr=0x8000000000000001, range=[0x00000000fed10000-0x00000000fed1a000) (0MB)
[    0.000000] efi: mem65: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem66: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem67: type=11, attr=0x8000000000000000, range=[0x00000000ffb80000-0x00000000ffc00000) (0MB)
[    0.000000] efi: mem68: type=11, attr=0x8000000000000001, range=[0x00000000ffc00000-0x00000000fff00000) (3MB)
[    0.000000] efi: mem69: type=11, attr=0x8000000000000001, range=[0x00000000fff00000-0x00000000fff40000) (0MB)
[    0.000000] efi: mem70: type=11, attr=0x8000000000000001, range=[0x00000000fff40000-0x0000000100000000) (0MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Inspiron 3721/07PX56, BIOS A06 02/22/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x14f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 0A0000000 mask FF8000000 write-back
[    0.000000]   3 base 0A8000000 mask FFE000000 write-back
[    0.000000]   4 base 0AA000000 mask FFF000000 write-back
[    0.000000]   5 base 0FFA00000 mask FFFE00000 write-protect
[    0.000000]   6 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   7 base 100000000 mask F80000000 write-back
[    0.000000]   8 base 14F600000 mask FFFE00000 uncachable
[    0.000000]   9 base 14F800000 mask FFF800000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xab000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff88000007e000] 7e000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xaaffffff]
[    0.000000]  [mem 0x00000000-0xaaffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xaaffffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x14f5fffff]
[    0.000000]  [mem 0x100000000-0x14f5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x14f5fffff @ [mem 0xa9a0d000-0xa9a0ffff]
[    0.000000] RAMDISK: [mem 0x36124000-0x37089fff]
[    0.000000] ACPI: RSDP 00000000aaffe014 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000aaffe210 000AC (v01 DELL    CL09    00000001      01000013)
[    0.000000] ACPI: FACP 00000000aaffa000 0010C (v05 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DSDT 00000000aafed000 092F2 (v01 DELL    CL09    00000000 ASL  00040000)
[    0.000000] ACPI: FACS 00000000aafb9000 00040
[    0.000000] ACPI: SLIC 00000000aaffd000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: UEFI 00000000aaffc000 00236 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASF! 00000000aaffb000 000A5 (v32 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: HPET 00000000aaff9000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: APIC 00000000aaff8000 0008C (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MCFG 00000000aaff7000 0003C (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SLIC 00000000aafec000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000aafeb000 006FE (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000aafe9000 00028 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASPT 00000000aafe7000 00034 (v07 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DBGP 00000000aafe6000 00034 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: FPDT 00000000aafe4000 00044 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MSDM 00000000aafe3000 00055 (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000aafe2000 00926 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000aafe1000 00A92 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: BGRT 00000000aafe0000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000014f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x14f5fffff]
[    0.000000]   NODE_DATA [mem 0x14f5fb000-0x14f5fffff]
[    0.000000]  [ffffea0000000000-ffffea00053fffff] PMD -> [ffff88014ac00000-ffff88014ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x14f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0x9ffaffff]
[    0.000000]   node   0: [mem 0xa13b0000-0xa9dbefff]
[    0.000000]   node   0: [mem 0xaafff000-0xaaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x14f5fffff]
[    0.000000] On node 0 totalpages: 1015095
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 8 pages reserved
[    0.000000]   DMA zone: 3888 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10719 pages used for memmap
[    0.000000]   DMA32 zone: 675296 pages, LIFO batch:31
[    0.000000]   Normal zone: 5080 pages used for memmap
[    0.000000]   Normal zone: 320040 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000088000 - 00000000000c0000
[    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 000000009ffb0000 - 00000000a13b0000
[    0.000000] PM: Registered nosave memory: 00000000a9dbf000 - 00000000aaebf000
[    0.000000] PM: Registered nosave memory: 00000000aaebf000 - 00000000aafbf000
[    0.000000] PM: Registered nosave memory: 00000000aafbf000 - 00000000aafff000
[    0.000000] PM: Registered nosave memory: 00000000ab000000 - 00000000afa00000
[    0.000000] PM: Registered nosave memory: 00000000afa00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb80000
[    0.000000] PM: Registered nosave memory: 00000000ffb80000 - 0000000100000000
[    0.000000] e820: [mem 0xafa00000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88014f200000 s85056 r8192 d21440 u262144
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 999224
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=9cce131a-c0dd-4480-a9d6-de0066e279cf ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3823988k/5494784k available (7006k kernel code, 1434404k absent, 236392k reserved, 6237k data, 996k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1895.627 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3791.25 BogoMIPS (lpj=7582508)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.050194] Security Framework initialized
[    0.050204] AppArmor: AppArmor initialized
[    0.050205] Yama: becoming mindful.
[    0.050553] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.051897] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.052512] Mount-cache hash table entries: 256
[    0.052701] Initializing cgroup subsys cpuacct
[    0.052703] Initializing cgroup subsys memory
[    0.052710] Initializing cgroup subsys devices
[    0.052712] Initializing cgroup subsys freezer
[    0.052714] Initializing cgroup subsys blkio
[    0.052715] Initializing cgroup subsys perf_event
[    0.052718] Initializing cgroup subsys hugetlb
[    0.052745] CPU: Physical Processor ID: 0
[    0.052747] CPU: Processor Core ID: 0
[    0.052752] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.052752] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.052757] mce: CPU supports 7 MCE banks
[    0.052770] CPU0: Thermal monitoring enabled (TM1)
[    0.052779] process: using mwait in idle threads
[    0.052783] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.052783] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.052783] tlb_flushall_shift: 1
[    0.052979] Freeing SMP alternatives: 24k freed
[    0.055599] ACPI: Core revision 20121018
[    0.077470] ftrace: allocating 26693 entries in 105 pages
[    0.094171] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.133844] smpboot: CPU0: Intel(R) Core(TM) i3-3227U CPU @ 1.90GHz (fam: 06, model: 3a, stepping: 09)
[    0.133853] TSC deadline timer enabled
[    0.133858] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, Intel PMU driver.
[    0.133865] ... version:                3
[    0.133866] ... bit width:              48
[    0.133867] ... generic registers:      4
[    0.133869] ... value mask:             0000ffffffffffff
[    0.133870] ... max period:             000000007fffffff
[    0.133871] ... fixed-purpose events:   3
[    0.133872] ... event mask:             000000070000000f
[    0.148293] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.135052] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.174755] Brought up 4 CPUs
[    0.174759] smpboot: Total of 4 processors activated (15165.01 BogoMIPS)
[    0.178847] devtmpfs: initialized
[    0.179809] EVM: security.selinux
[    0.179811] EVM: security.SMACK64
[    0.179812] EVM: security.capability
[    0.179868] PM: Registering ACPI NVS region [mem 0xaaebf000-0xaafbefff] (1048576 bytes)
[    0.180730] regulator-dummy: no parameters
[    0.180780] NET: Registered protocol family 16
[    0.180947] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.180949] ACPI: bus type pci registered
[    0.181017] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.181020] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.214786] PCI: Using configuration type 1 for base access
[    0.214918] dmi type 0xB1 record - unknown flag
[    0.215849] bio: create slab <bio-0> at 0
[    0.215937] ACPI: Added _OSI(Module Device)
[    0.215939] ACPI: Added _OSI(Processor Device)
[    0.215941] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.215943] ACPI: Added _OSI(Processor Aggregator Device)
[    0.215945] ACPI: Deleted _OSI(Windows 2012)
[    0.217546] ACPI: EC: Look up EC in DSDT
[    0.219322] ACPI: Executed 1 blocks of module-level executable AML code
[    0.222735] ACPI: SSDT 00000000aae17018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.223153] ACPI: Dynamic OEM Table Load:
[    0.223156] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.234871] ACPI: SSDT 00000000aae18a98 00303 (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.235316] ACPI: Dynamic OEM Table Load:
[    0.235318] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.235464] ACPI: SSDT 00000000aae16d98 00119 (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.235874] ACPI: Dynamic OEM Table Load:
[    0.235876] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.236758] ACPI: Interpreter enabled
[    0.236762] ACPI: (supports S0 S3 S4 S5)
[    0.236784] ACPI: Using IOAPIC for interrupt routing
[    0.361525] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.361659] ACPI: No dock devices found.
[    0.361663] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.361840] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.361842] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.361996] \_SB_.PCI0:_OSC invalid UUID
[    0.361997] _OSC request data:1 8 1f 
[    0.362333] PCI host bridge to bus 0000:00
[    0.362336] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.362339] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.362341] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.362343] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.362345] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.362347] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.362349] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.362351] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.362353] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.362355] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.362357] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.362359] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.362361] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.362363] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.362365] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.362367] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.362369] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.362371] pci_bus 0000:00: root bus resource [mem 0xafa00000-0xfeafffff]
[    0.362381] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.362426] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.362440] pci 0000:00:02.0: reg 10: [mem 0xc0000000-0xc03fffff 64bit]
[    0.362448] pci 0000:00:02.0: reg 18: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.362455] pci 0000:00:02.0: reg 20: [io  0x3000-0x303f]
[    0.362519] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.362545] pci 0000:00:14.0: reg 10: [mem 0xc0600000-0xc060ffff 64bit]
[    0.362626] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.362659] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.362687] pci 0000:00:16.0: reg 10: [mem 0xc0614000-0xc061400f 64bit]
[    0.362771] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.362820] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.362845] pci 0000:00:1a.0: reg 10: [mem 0xc0619000-0xc06193ff]
[    0.362946] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.362976] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.362995] pci 0000:00:1b.0: reg 10: [mem 0xc0610000-0xc0613fff 64bit]
[    0.363073] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.363102] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.363193] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.363222] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.363311] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.363354] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.363380] pci 0000:00:1d.0: reg 10: [mem 0xc0618000-0xc06183ff]
[    0.363481] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.363510] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    0.363649] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.363672] pci 0000:00:1f.2: reg 10: [io  0x3088-0x308f]
[    0.363681] pci 0000:00:1f.2: reg 14: [io  0x3094-0x3097]
[    0.363690] pci 0000:00:1f.2: reg 18: [io  0x3080-0x3087]
[    0.363700] pci 0000:00:1f.2: reg 1c: [io  0x3090-0x3093]
[    0.363710] pci 0000:00:1f.2: reg 20: [io  0x3060-0x307f]
[    0.363720] pci 0000:00:1f.2: reg 24: [mem 0xc0617000-0xc06177ff]
[    0.363773] pci 0000:00:1f.2: PME# supported from D3hot
[    0.363795] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.363814] pci 0000:00:1f.3: reg 10: [mem 0xc0615000-0xc06150ff 64bit]
[    0.363839] pci 0000:00:1f.3: reg 20: [io  0x3040-0x305f]
[    0.364005] pci 0000:01:00.0: [10ec:8136] type 00 class 0x020000
[    0.364077] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
[    0.364203] pci 0000:01:00.0: reg 18: [mem 0xc0404000-0xc0404fff 64bit pref]
[    0.364282] pci 0000:01:00.0: reg 20: [mem 0xc0400000-0xc0403fff 64bit pref]
[    0.364628] pci 0000:01:00.0: supports D1 D2
[    0.364630] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.370897] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.370902] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.370912] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.371028] pci 0000:02:00.0: [14e4:4365] type 00 class 0x028000
[    0.371082] pci 0000:02:00.0: reg 10: [mem 0xc0500000-0xc0507fff 64bit]
[    0.371366] pci 0000:02:00.0: supports D1 D2
[    0.371368] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.378888] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.378895] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
[    0.378939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.378974] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.379072] \_SB_.PCI0:_OSC invalid UUID
[    0.379074] _OSC request data:1 1f 1f 
[    0.379078]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.379079]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.379603] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.379652] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.379699] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.379745] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.379791] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.379836] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.379884] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.379933] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.380040] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.380044] vgaarb: loaded
[    0.380045] vgaarb: bridge control possible 0000:00:02.0
[    0.380210] SCSI subsystem initialized
[    0.380213] ACPI: bus type scsi registered
[    0.380256] libata version 3.00 loaded.
[    0.380272] ACPI: bus type usb registered
[    0.380293] usbcore: registered new interface driver usbfs
[    0.380301] usbcore: registered new interface driver hub
[    0.380323] usbcore: registered new device driver usb
[    0.380409] PCI: Using ACPI for IRQ routing
[    0.387603] PCI: pci_cache_line_size set to 64 bytes
[    0.387690] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    0.387692] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.387694] e820: reserve RAM buffer [mem 0x9ffb0000-0x9fffffff]
[    0.387695] e820: reserve RAM buffer [mem 0xa9dbf000-0xabffffff]
[    0.387697] e820: reserve RAM buffer [mem 0xab000000-0xabffffff]
[    0.387699] e820: reserve RAM buffer [mem 0x14f600000-0x14fffffff]
[    0.387784] NetLabel: Initializing
[    0.387785] NetLabel:  domain hash size = 128
[    0.387786] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.387796] NetLabel:  unlabeled traffic allowed by default
[    0.387861] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.387867] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.389877] Switching to clocksource hpet
[    0.395142] AppArmor: AppArmor Filesystem Enabled
[    0.395165] pnp: PnP ACPI init
[    0.395177] ACPI: bus type pnp registered
[    0.395211] pnp 00:00: [dma 4]
[    0.395234] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.395254] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.395358] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.395389] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.395434] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.395436] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.395439] system 00:04: [io  0xffff] has been reserved
[    0.395441] system 00:04: [io  0xffff] has been reserved
[    0.395443] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.395446] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.395448] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.395450] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.395452] system 00:04: [io  0xfd60-0xfd63] has been reserved
[    0.395456] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.395481] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.395526] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.395529] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.395570] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.395599] pnp 00:08: Plug and Play ACPI device, IDs DLL059c PNP0f13 (active)
[    0.454045] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.454048] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.454051] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.454053] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.454056] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.454058] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.454060] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.454063] system 00:09: [mem 0xff000000-0xff000fff] has been reserved
[    0.454065] system 00:09: [mem 0xff010000-0xffffffff] could not be reserved
[    0.454068] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.454070] system 00:09: [mem 0xafa00000-0xafa00fff] has been reserved
[    0.454073] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.454365] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    0.454367] system 00:0a: [mem 0x40004000-0x40004fff] has been reserved
[    0.454370] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.454390] pnp: PnP ACPI: found 11 devices
[    0.454392] ACPI: ACPI bus type pnp unregistered
[    0.460913] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.460919] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.460928] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.460936] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.460942] pci 0000:00:1c.1:   bridge window [mem 0xc0500000-0xc05fffff]
[    0.460980] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.460982] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.460984] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.460986] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.460988] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.460990] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.460993] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.460995] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.460997] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.460999] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.461001] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.461003] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.461005] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.461007] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.461009] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.461011] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.461013] pci_bus 0000:00: resource 20 [mem 0xafa00000-0xfeafffff]
[    0.461016] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.461018] pci_bus 0000:01: resource 2 [mem 0xc0400000-0xc04fffff 64bit pref]
[    0.461020] pci_bus 0000:02: resource 1 [mem 0xc0500000-0xc05fffff]
[    0.461052] NET: Registered protocol family 2
[    0.461214] TCP established hash table entries: 32768 (order: 7, 524288 bytes)
[    0.461344] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.461433] TCP: Hash tables configured (established 32768 bind 32768)
[    0.461451] TCP: reno registered
[    0.461460] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.461478] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.461540] NET: Registered protocol family 1
[    0.461551] pci 0000:00:02.0: Boot video device
[    0.493940] PCI: CLS 64 bytes, default 64
[    0.493981] Trying to unpack rootfs image as initramfs...
[    0.814709] Freeing initrd memory: 15768k freed
[    0.816986] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.816992] software IO TLB [mem 0xa22ab000-0xa62ab000] (64MB) mapped at [ffff8800a22ab000-ffff8800a62aafff]
[    0.817038] Simple Boot Flag at 0x44 set to 0x1
[    0.817413] Initialise module verification
[    0.817459] audit: initializing netlink socket (disabled)
[    0.817473] type=2000 audit(1369751391.788:1): initialized
[    0.854708] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.856109] VFS: Disk quotas dquot_6.5.2
[    0.856149] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.856604] fuse init (API version 7.20)
[    0.856674] msgmni has been set to 7640
[    0.857107] Key type asymmetric registered
[    0.857111] Asymmetric key parser 'x509' registered
[    0.857142] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.857169] io scheduler noop registered
[    0.857172] io scheduler deadline registered (default)
[    0.857178] io scheduler cfq registered
[    0.857355] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.857369] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.857424] efifb: probing for efifb
[    0.858348] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90020e00000, using 5632k, total 5632k
[    0.858351] efifb: mode is 1600x900x32, linelength=6400, pages=1
[    0.858352] efifb: scrolling: redraw
[    0.858354] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.862011] Console: switching to colour frame buffer device 200x56
[    0.865580] fb0: EFI VGA frame buffer device
[    0.865586] intel_idle: MWAIT substates: 0x21120
[    0.865587] intel_idle: v0.4 model 0x3A
[    0.865589] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.865683] ACPI: AC Adapter [ACAD] (on-line)
[    0.865798] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[    0.865803] ACPI: Power Button [PWRB]
[    0.865845] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.865869] ACPI: Lid Switch [LID0]
[    0.865899] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.865902] ACPI: Power Button [PWRF]
[    0.865978] ACPI: Requesting acpi_cpufreq
[    0.986619] GHES: HEST is not enabled!
[    0.986694] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.045729] ACPI: Battery Slot [BAT1] (battery absent)
[    1.045828] Linux agpgart interface v0.103
[    1.046997] brd: module loaded
[    1.047550] loop: module loaded
[    1.047847] libphy: Fixed MDIO Bus: probed
[    1.047901] tun: Universal TUN/TAP device driver, 1.6
[    1.047903] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.047938] PPP generic driver version 2.4.2
[    1.047976] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.047978] ehci-pci: EHCI PCI platform driver
[    1.048021] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.048025] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.048031] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.048046] ehci-pci 0000:00:1a.0: debug port 2
[    1.051947] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.051963] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc0619000
[    1.061693] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.061733] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.061736] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.061738] usb usb1: Product: EHCI Host Controller
[    1.061740] usb usb1: Manufacturer: Linux 3.8.0-22-generic ehci_hcd
[    1.061742] usb usb1: SerialNumber: 0000:00:1a.0
[    1.061840] hub 1-0:1.0: USB hub found
[    1.061844] hub 1-0:1.0: 2 ports detected
[    1.061940] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.061944] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.061949] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.061962] ehci-pci 0000:00:1d.0: debug port 2
[    1.065860] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.065874] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc0618000
[    1.077699] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.077729] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.077732] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.077734] usb usb2: Product: EHCI Host Controller
[    1.077736] usb usb2: Manufacturer: Linux 3.8.0-22-generic ehci_hcd
[    1.077737] usb usb2: SerialNumber: 0000:00:1d.0
[    1.077822] hub 2-0:1.0: USB hub found
[    1.077826] hub 2-0:1.0: 2 ports detected
[    1.077898] ehci-platform: EHCI generic platform driver
[    1.077905] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.077916] uhci_hcd: USB Universal Host Controller Interface driver
[    1.077962] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.077966] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.077971] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.078062] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.078110] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    1.078158] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.078160] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.078162] usb usb3: Product: xHCI Host Controller
[    1.078164] usb usb3: Manufacturer: Linux 3.8.0-22-generic xhci_hcd
[    1.078166] usb usb3: SerialNumber: 0000:00:14.0
[    1.078229] xHCI xhci_add_endpoint called for root hub
[    1.078231] xHCI xhci_check_bandwidth called for root hub
[    1.078250] hub 3-0:1.0: USB hub found
[    1.078257] hub 3-0:1.0: 4 ports detected
[    1.078573] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.078577] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.078598] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.078600] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.078602] usb usb4: Product: xHCI Host Controller
[    1.078604] usb usb4: Manufacturer: Linux 3.8.0-22-generic xhci_hcd
[    1.078606] usb usb4: SerialNumber: 0000:00:14.0
[    1.078666] xHCI xhci_add_endpoint called for root hub
[    1.078668] xHCI xhci_check_bandwidth called for root hub
[    1.078685] hub 4-0:1.0: USB hub found
[    1.078692] hub 4-0:1.0: 4 ports detected
[    1.079084] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.096145] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.096153] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.096266] mousedev: PS/2 mouse device common for all mice
[    1.097754] rtc_cmos 00:05: RTC can wake from S4
[    1.097894] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.097924] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.098007] device-mapper: uevent: version 1.0.3
[    1.098075] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [email]dm-devel@redhat.com[/email]
[    1.098168] cpuidle: using governor ladder
[    1.098549] cpuidle: using governor menu
[    1.098553] ledtrig-cpu: registered to indicate activity on CPUs
[    1.098555] EFI Variables Facility v0.08 2004-May-17
[    1.113997] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.114943] ashmem: initialized
[    1.115070] TCP: cubic registered
[    1.115153] NET: Registered protocol family 10
[    1.115312] NET: Registered protocol family 17
[    1.115325] Key type dns_resolver registered
[    1.115558] Loading module verification certificates
[    1.116624] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 7fb074b2e4851c3043f2f3c12342cb419e9d7cc5'
[    1.116635] registered taskstats version 1
[    1.119566] Key type trusted registered
[    1.122109] Key type encrypted registered
[    1.124647] rtc_cmos 00:05: setting system clock to 2013-05-28 14:29:52 UTC (1369751392)
[    1.125423] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.125425] EDD information not available.
[    1.127225] Freeing unused kernel memory: 996k freed
[    1.127352] Write protecting the kernel read-only data: 12288k
[    1.131020] Freeing unused kernel memory: 1176k freed
[    1.134380] Freeing unused kernel memory: 1080k freed
[    1.147745] udevd[107]: starting version 175
[    1.180054] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.180292] r8169 0000:01:00.0: irq 41 for MSI/MSI-X
[    1.180518] r8169 0000:01:00.0 eth0: RTL8105e at 0xffffc90010082000, e0:db:55:e7:2e:1a, XID 00c00000 IRQ 41
[    1.182110] Disabling lock debugging due to kernel taint
[    1.183112] ahci 0000:00:1f.2: version 3.0
[    1.183204] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.197700] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.197708] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.197716] ahci 0000:00:1f.2: setting latency timer to 64
[    1.206767] scsi0 : ahci
[    1.207355] scsi1 : ahci
[    1.208792] scsi2 : ahci
[    1.210380] scsi3 : ahci
[    1.210523] scsi4 : ahci
[    1.210626] scsi5 : ahci
[    1.210688] ata1: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617100 irq 42
[    1.210691] ata2: DUMMY
[    1.210696] ata3: SATA max UDMA/133 abar m2048@0xc0617000 port 0xc0617200 irq 42
[    1.210698] ata4: DUMMY
[    1.210700] ata5: DUMMY
[    1.210701] ata6: DUMMY
[    1.373642] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.506058] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.506062] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.506435] hub 1-1:1.0: USB hub found
[    1.506501] hub 1-1:1.0: 6 ports detected
[    1.529596] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.534576] ata3.00: ATAPI: TSSTcorp DVD+/-RW SU-208BB, D300, max UDMA/100
[    1.537594] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.543029] ata3.00: configured for UDMA/100
[    1.547178] ata1.00: ATA-8: ST500LT012-9WS142, 0001SDM1, max UDMA/133
[    1.547182] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.586439] ata1.00: configured for UDMA/133
[    1.586637] scsi 0:0:0:0: Direct-Access     ATA      ST500LT012-9WS14 0001 PQ: 0 ANSI: 5
[    1.586794] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.586798] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.586835] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.586932] sd 0:0:0:0: [sda] Write Protect is off
[    1.586938] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.587058] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.593433] scsi 2:0:0:0: CD-ROM            TSSTcorp DVD+-RW SU-208BB D300 PQ: 0 ANSI: 5
[    1.608138] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.608141] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.608274] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.608360] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.617559] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.641788]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    1.642974] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.749919] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.749943] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.750176] hub 2-1:1.0: USB hub found
[    1.750276] hub 2-1:1.0: 6 ports detected
[    1.813498] tsc: Refined TSC clocksource calibration: 1895.695 MHz
[    1.813503] Switching to clocksource tsc
[    1.821537] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    1.916361] usb 1-1.1: New USB device found, idVendor=0a5c, idProduct=21d7
[    1.916369] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.916387] usb 1-1.1: Product: BCM43142A0
[    1.916389] usb 1-1.1: Manufacturer: Broadcom Corp
[    1.916391] usb 1-1.1: SerialNumber: 9C2A70BBD3A8
[    1.985459] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    2.078308] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    2.078316] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.078336] usb 1-1.3: Product: USB2.0-CRW
[    2.078338] usb 1-1.3: Manufacturer: Generic
[    2.078339] usb 1-1.3: SerialNumber: 20100201396000000
[    2.149596] usb 1-1.4: new high-speed USB device number 5 using ehci-pci
[    2.306546] usb 1-1.4: New USB device found, idVendor=0c45, idProduct=64ad
[    2.306550] usb 1-1.4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    2.306553] usb 1-1.4: Product: Laptop_Integrated_Webcam_HD
[    2.306555] usb 1-1.4: Manufacturer: CN0Y3PX8724872CBAVX3A00
[    3.686273] EXT4-fs (sda8): INFO: recovery required on readonly filesystem
[    3.686277] EXT4-fs (sda8): write access will be enabled during recovery
[    5.984569] EXT4-fs (sda8): recovery complete
[    5.990732] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   17.350341] Adding 194556k swap on /dev/sda7.  Priority:-1 extents:1 across:194556k 
[   17.514265] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.579729] udevd[381]: starting version 175
[   17.824707] type=1400 audit(1369751409.202:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=515 comm="apparmor_parser"
[   17.824718] type=1400 audit(1369751409.202:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=529 comm="apparmor_parser"
[   17.825147] type=1400 audit(1369751409.202:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=515 comm="apparmor_parser"
[   17.825159] type=1400 audit(1369751409.202:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=529 comm="apparmor_parser"
[   17.825387] type=1400 audit(1369751409.202:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=515 comm="apparmor_parser"
[   17.825401] type=1400 audit(1369751409.202:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=529 comm="apparmor_parser"
[   18.369735] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.429942] mei 0000:00:16.0: setting latency timer to 64
[   18.430008] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   18.464306] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[   18.479720] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   18.483397] scsi6 : SCSI emulation for RTS5139 USB card reader
[   18.483519] usbcore: registered new interface driver rts5139
[   18.483575] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   18.484372] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   18.487367] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   18.504095] Linux video capture interface: v2.00
[   18.512109] [drm] Initialized drm 1.1.0 20060810
[   18.541471] Bluetooth: Core ver 2.16
[   18.541495] NET: Registered protocol family 31
[   18.541498] Bluetooth: HCI device and connection manager initialized
[   18.541506] Bluetooth: HCI socket layer initialized
[   18.541509] Bluetooth: L2CAP socket layer initialized
[   18.541517] Bluetooth: SCO socket layer initialized
[   18.573134] usbcore: registered new interface driver btusb
[   18.596129] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[   18.597429] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[   18.598942] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[   18.600390] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   18.607582] lp: driver loaded but no devices found
[   18.630865] Bluetooth: can't load firmware, may not work correctly
[   18.815529] [drm] Memory usable by graphics device = 2048M
[   18.815534] checking generic (b0000000 580000) vs hw (b0000000 10000000)
[   18.815536] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[   18.815570] Console: switching to colour dummy device 80x25
[   18.815639] i915 0000:00:02.0: setting latency timer to 64
[   18.859135] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   18.859146] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.859147] [drm] Driver supports precise vblank timestamp query.
[   18.859234] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   18.896819] wmi: Mapper loaded
[   18.935391] input: Dell WMI hotkeys as /devices/virtual/input/input4
[   19.091992] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[   19.144824] fbcon: inteldrmfb (fb0) is primary device
[   19.174710] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0c45:64ad)
[   19.215849] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input5
[   19.215973] usbcore: registered new interface driver uvcvideo
[   19.215974] USB Video Class driver (1.1.1)
[   19.437061] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00, board id: 2382, fw id: 1238635
[   19.509809] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   19.863845] Console: switching to colour frame buffer device 200x56
[   19.867323] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   19.867325] i915 0000:00:02.0: registered panic notifier
[   19.869455] ACPI Warning: _BQC returned an invalid level (20121018/video-494)
[   19.869592] acpi device:31: registered as cooling_device4
[   19.869833] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.869885] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   19.869967] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   19.870195] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   19.870203] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.870207] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   19.870213] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.870215] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   19.870220] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   19.870223] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   19.870529] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   20.351518] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   20.351723] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.351813] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.839809] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   23.567177] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   25.256070] init: failsafe main process (972) killed by TERM signal
[   25.605955] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.605959] Bluetooth: BNEP filters: protocol multicast
[   25.605966] Bluetooth: BNEP socket layer initialized
[   25.809820] Bluetooth: RFCOMM TTY layer initialized
[   25.809843] Bluetooth: RFCOMM socket layer initialized
[   25.809846] Bluetooth: RFCOMM ver 1.11
[   25.855338] type=1400 audit(1369751417.234:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1077 comm="apparmor_parser"
[   25.855677] type=1400 audit(1369751417.234:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1077 comm="apparmor_parser"
[   25.856277] type=1400 audit(1369751417.234:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1078 comm="apparmor_parser"
[   25.856288] type=1400 audit(1369751417.234:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1079 comm="apparmor_parser"
[   25.856691] type=1400 audit(1369751417.234:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1078 comm="apparmor_parser"
[   25.856700] type=1400 audit(1369751417.234:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1079 comm="apparmor_parser"
[   25.860130] type=1400 audit(1369751417.238:14): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1080 comm="apparmor_parser"
[   25.860686] type=1400 audit(1369751417.238:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1080 comm="apparmor_parser"
[   25.860991] type=1400 audit(1369751417.238:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1080 comm="apparmor_parser"
[   25.861776] type=1400 audit(1369751417.238:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1083 comm="apparmor_parser"
[   26.070951] init: avahi-cups-reload main process (1104) terminated with status 1
[   26.133607] ppdev: user-space parallel port driver
[   26.384859] init: cups-browsed pre-start process (1164) terminated with status 1
[   28.224040] r8169 0000:01:00.0 eth0: link down
[   28.224059] r8169 0000:01:00.0 eth0: link down
[   28.224081] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.224382] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.488730] vboxdrv: Found 4 processor cores.
[   28.488904] vboxdrv: fAsync=0 offMin=0x118 offMax=0x1164
[   28.489000] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   28.489002] vboxdrv: Successfully loaded version 4.2.6 (interface 0x001a0004).
[   29.132846] vboxpci: IOMMU not found (not registered)
[   29.776351] r8169 0000:01:00.0 eth0: link up
[   29.776361] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   29.780912] init: plymouth-stop pre-start process (1462) terminated with status 1


---

### Post by praseodym on 2013-05-28
Try the b43 driver now:
```

sudo modprobe -v b43
dmesg | grep b43
```

---

### Post by honeycup on 2013-05-28
> seb@Dell:~$ sudo modprobe -v b43
[sudo] password for seb: 
Sorry, try again.
[sudo] password for seb: 
insmod /lib/modules/3.8.0-22-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/drivers/net/wireless/b43/b43.ko 
seb@Dell:~$ 




Btw. any idea why I always have to enter the password twice?

---

### Post by praseodym on 2013-05-28
Typos ;)

Please always show the outputs:
```

dmesg | grep b43
```

---

### Post by honeycup on 2013-05-28
There is no output:

> seb@Dell:~$ dmesg | grep b43
seb@Dell:~$ 


---

### Post by praseodym on 2013-05-28
Try the other one:
```

sudo modprobe -rfv b43
sudo modprobe -v b43legacy
dmesg | grep b43
```

---

### Post by honeycup on 2013-05-28
> 
seb@Dell:~$ sudo modprobe -rfv b43
seb@Dell:~$ sudo modprobe -v b43legacy
insmod /lib/modules/3.8.0-22-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-22-generic/kernel/drivers/net/wireless/b43legacy/b43legacy.ko 
seb@Dell:~$ dmesg | grep b43
seb@Dell:~$


And I didn't wrote the password wrong, I always have to enter it twice before its accepted. Its just a 4 digits code, so would be impossible to write it wrong every time.

---

### Post by honeycup on 2013-05-29
Any other thing I should try?

---

### Post by praseodym on 2013-05-29
Please try this:
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms bcmwl-kernel-source
echo -e "blacklist b43\nblacklist ssb\nblacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist-broadcom.conf
```
and reboot.

Check here [http://askubuntu.com/questions/289609/dell-3721-wifi-problem-ubuntu-13-04](http://askubuntu.com/questions/289609/dell-3721-wifi-problem-ubuntu-13-04)

Thanks to Hadaka via PM

---

### Post by honeycup on 2013-05-29
No need to check that link because its my own post there. The solution worked first, but then it stopped without any reason. This one helped me now:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms bcmwl-kernel-source
echo -e "blacklist b43\nblacklist ssb\nblacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist-broadcom.conf
```

Can connect to my home network now. How to get sure that this will not change with the next update/upgrade again?

---

### Post by praseodym on 2013-05-29
Now its permanent. Sorry, didnt read the name ;)

---

### Post by honeycup on 2013-05-29
Hope so, thank you very much!

---

