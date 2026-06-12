---
title: "Broadcom 43225 - No wireless"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by favri on 2010-10-11
[FONT=&quot]I'm new to ubuntu.
I've installed ubuntu 10.10 on my netbook, and i can't manage to conect via wireless.

This are all the results:[/FONT]

[FONT=&quot][/FONT]
[FONT=&quot]Thanks for your help.-
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]**sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:2d:ac:a5:29
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
  *-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 90:4c:e5:62:39:fa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0300000-d0303fff




**ifconfig**
eth0      Link encap:Ethernet  direcciónHW 00:26:2d:ac:a5:29  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:43 

eth1      Link encap:Ethernet  direcciónHW 90:4c:e5:62:39:fa  
          Dirección inet6: fe80::924c:e5ff:fe62:39fa/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)


**dmesg | grep -e wl -e eth**
[   12.519978] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.856823] wl 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.856832] wl 0000:06:00.0: setting latency timer to 64
[   13.084335] eth1: Broadcom BCM4357 802.11 Hybrid Wireless Controller 5.60.48.36 
[   14.865858] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  107.392102] eth1: no IPv6 routers present


**rfkill list all**
0: acer-wireless: Wireless LAN
      Soft blocked: yes
      Hard blocked: no
3: hci0: Bluetooth
      Soft blocked: no
      Hard blocked: no

**lsmod**
Module                  Size  Used by
nls_iso8859_1           3261  0 
nls_cp437               4931  0 
vfat                    9201  0 
fat                    48240  1 vfat
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
btusb                  10969  2 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
radeon                825934  4 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ttm                    56633  1 radeon
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
lib80211_crypt_tkip     7736  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
uvcvideo               55847  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               13929  0 
drm                   168054  6 radeon,ttm,drm_kms_helper
led_class               2633  1 acer_wmi
wl                   1959533  0 
videodev               43098  1 uvcvideo
psmouse                59033  0 
video                  18712  0 
v4l1_compat            13359  2 uvcvideo,videodev
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1883  1 video
serio_raw               4022  0 
soundcore                880  1 snd
agpgart                32011  2 ttm,drm
i2c_algo_bit            5168  1 radeon
lib80211                5058  2 lib80211_crypt_tkip,wl
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
k10temp                 2607  0 
shpchp                 29886  0 
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
usb_storage            40172  0 
libahci                21667  3 ahci
pata_atiixp             3288  0 
atl1c                  29949  0 

[/FONT]

---

### Post by favri on 2010-10-11
Can someone help me?

Any idea?

Thanks!

---

### Post by Ayuthia on 2010-10-11
You might try this [thread]("http://ubuntuforums.org/showthread.php?t=1592044").  If I remember correctly, your card is supported by this new driver.

EDIT:
I am not for sure about how much Linux experience you have, so if you need more information, please let us know.

---

### Post by Baga255 on 2010-10-11
I had the same problem, but with the Broadcom 43224 chipset and I managed to solve it.
I believe this thread can help you: [http://ubuntuforums.org/showthread.php?t=1592044](http://ubuntuforums.org/showthread.php?t=1592044)
Good luck :)

EDIT: Ayuthia was quicker :)

---

### Post by favri on 2010-10-11
I'm trying to follow the opensuse forum guide.

Wish me luck, i'm not an expert at all ;)

---

### Post by favri on 2010-10-11
Hi guys. 
I'm following this thread instructions: [http://forums.opensuse.org/english/get-help-here/hardware/447485-bcm43224-bcm43225-bcm4313-installation-guide.html](http://forums.opensuse.org/english/get-help-here/hardware/447485-bcm43224-bcm43225-bcm4313-installation-guide.html)

I encounter a problem in point 2, to create the .ko file.

favri@favri-ntb:~$ ~/linux-next/drivers/staging/brcm80211/> make

bash: /home/favri/linux-next/drivers/staging/brcm80211/: is a directory


Sorry if it's a newbie mistake, this whole issue is being a big school for me!

---

### Post by karlitosbrigante on 2010-10-11
Few words follow this...
System -> Administration -> Additional Drivers -> Activate Broadcom STA wireless driver
tell me if it works but i'm sure that will work fine

---

### Post by Ayuthia on 2010-10-12
> **favri said:**
> Hi guys. 
I'm following this thread instructions: [http://forums.opensuse.org/english/get-help-here/hardware/447485-bcm43224-bcm43225-bcm4313-installation-guide.html](http://forums.opensuse.org/english/get-help-here/hardware/447485-bcm43224-bcm43225-bcm4313-installation-guide.html)

I encounter a problem in point 2, to create the .ko file.

favri@favri-ntb:~$ ~/linux-next/drivers/staging/brcm80211/> make

bash: /home/favri/linux-next/drivers/staging/brcm80211/: is a directory


Sorry if it's a newbie mistake, this whole issue is being a big school for me!

I see what happened.  The person who posted the instructions has an '>' in front of their prompt instead of the '$'.  Instead of typing the full thing, you just need:
```

make

```
What happened was that the '>' is a redirection command so it tried to take the information to the left of the arrow and put it into the command at the right of the arrow.  It was telling you that you cannot copy a directory into a file.

By the way, there is a good chance that you do not have build-essential installed.  You will most likely need it in order to compile the source.  You should be able to install it via the package manager or you can do it from the Terminal:
```

sudo apt-get install build-essential

```

---

### Post by Ayuthia on 2010-10-12
> **karlitosbrigante said:**
> Few words follow this...
System -> Administration -> Additional Drivers -> Activate Broadcom STA wireless driver
tell me if it works but i'm sure that will work fine

In the other thread, it looks like the Broadcom STA driver does not work with the 43xxx series.  I have not had a chance to verify that yet, but it looked like a couple of people so far have had problems with that driver.  The one that is being used here is the new version that Broadcom has supplied for this series.

---

### Post by favri on 2010-10-12
> **karlitosbrigante said:**
> Few words follow this...
System -> Administration -> Additional Drivers -> Activate Broadcom STA wireless driver
tell me if it works but i'm sure that will work fine

The STA drivers doesn't work. 


@[Ayuthia]("http://ubuntuforums.org/member.php?u=286983")

I'll try your instructions today, and let you know ;)

Thanks!

---

### Post by favri on 2010-10-12
In the final step. where it says:

```

linux-next/drivers/staging/brcm80211 # insmod /lib/modules/`uname -r`/brcm80211.ko 

```

i guet this error: 
```

favri@favri-ntb:~/linux-next/drivers/staging/brcm80211$ sudo insmod /lib/modules/2.6.35-22-generic/brcm80211.ko
insmod: error inserting '/lib/modules/2.6.35-22-generic/brcm80211.ko': -1 Unknown symbol in module


```

---

### Post by Ayuthia on 2010-10-12
Yes.  We found out that the mac80211 module was not loaded.  Try:
```

sudo modprobe mac80211
sudo insmod /lib/modules/`uname -r`/brcm80211.ko

```
That should fix that problem.

---

### Post by favri on 2010-10-12
I've donde what you told me and guess it worked for the previous step.
In the last one. i guet this


```

favri@favri-ntb:~/linux-next/drivers/staging/brcm80211$ modprobe brcm80211

```

```
FATAL: Module brcm80211 not found.
```

---

### Post by favri on 2010-10-12
I run

lsmod
```


Module                  Size  Used by
brcm80211             677213  0 
mac80211              231541  1 brcm80211
cfg80211              144470  2 brcm80211,mac80211
rfcomm                 33811  0 
sco                     7998  0 
bnep                    9542  0 
l2cap                  37008  4 rfcomm,bnep
btusb                  10969  0 
bluetooth              50500  5 rfcomm,sco,bnep,l2cap,btusb
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
radeon                825934  4 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
lib80211_crypt_tkip     7736  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168054  6 radeon,ttm,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               13929  0 
uvcvideo               55847  0 
wl                   1959533  0 
led_class               2633  1 acer_wmi
videodev               43098  1 uvcvideo
agpgart                32011  2 ttm,drm
video                  18712  0 
joydev                  8735  0 
i2c_algo_bit            5168  1 radeon
v4l1_compat            13359  2 uvcvideo,videodev
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1883  1 video
psmouse                59033  0 
shpchp                 29886  0 
soundcore                880  1 snd
lib80211                5058  2 lib80211_crypt_tkip,wl
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
k10temp                 2607  0 
lp                      7342  0 
i2c_piix4               8635  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
ahci                   19013  0 
usb_storage            40172  0 
libahci                21667  3 ahci
pata_atiixp             3288  0 
atl1c                  29949  0 

```

Guess the problem is here?

rfkill list all
```
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```

---

### Post by Ayuthia on 2010-10-12
```

Module                  Size  Used by
wl                   1959533  0 
lib80211                5058  2 lib80211_crypt_tkip,wl

```

This could be the problem.  It is the conflicting wireless driver.  Let's try the following:
```

sudo modprobe -r wl
sudo modprobe -r lib80211_crypt_tkip lib80211
sudo rmmod brcm80211
sudo modprobe -r mac80211
sudo modprobe mac80211
sudo insmod brcm80211.ko

```
The first few commands will remove the Broadcom STA driver along with the current driver that we are trying to use.  Next, we are going to load the drivers that we need and try it again.  If this works, we can then check and remove the Broadcom STA driver from Additional Drivers (if it is there).  If it is not there, let us know and then we can blacklist the driver that is not working.

---

### Post by favri on 2010-10-12
When i arrive to the last line of the code


sudo insmod brcm80211.ko
Get this:

```

insmod: can't read 'brcm80211.ko': No such file or directory

```

---

### Post by Ayuthia on 2010-10-12
> **favri said:**
> When i arrive to the last line of the code


sudo insmod brcm80211.ko
Get this:

```

insmod: can't read 'brcm80211.ko': No such file or directory

```

Sorry about that.  That should have been:
```

sudo insmod /lib/modules/`uname -r`/brcm80211.ko

```
insmod needs to know the location of the .ko file or else it cannot load it.

---

### Post by favri on 2010-10-12
Everything donde, but, no conection.

The problem might be here

```

rfkill list all
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```
i tried 
```

rfkill unblock 1
```but still the soft blocked is "yes"

---

### Post by Ayuthia on 2010-10-12
> **favri said:**
> Everything donde, but, no conection.

The problem might be here

```

rfkill list all
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```
i tried 
```

rfkill unblock 1
```but still the soft blocked is "yes"

Can you post the results of 
```

lshw -C network
dmesg|tail

```
It might help us see what is happening.  Also, if your wireless has a switch, have you tried turning it off/on?

EDIT:  I am not familiar with the rfkill command so I am not for sure about what is happening.

---

### Post by favri on 2010-10-12
```

lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:2d:ac:a5:29
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.28.104 latency=0 multicast=yes
       resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:d0300000-d0303fff


```

```

[ 1566.418480] btusb_bulk_complete: hci0 urb f1872480 failed to resubmit (19)
[ 1566.418496] btusb_intr_complete: hci0 urb f1872f00 failed to resubmit (19)
[ 1566.419505] btusb_bulk_complete: hci0 urb f1872280 failed to resubmit (19)
[ 1566.420034] btusb_send_frame: hci0 urb f289e580 submission failed
[ 1568.184278] usb 5-3: new full speed USB device using ohci_hcd and address 16
[ 1568.720050] usb 5-3: USB disconnect, address 16
[ 1568.720375] btusb_bulk_complete: hci0 urb f180d580 failed to resubmit (19)
[ 1568.720391] btusb_intr_complete: hci0 urb f180d980 failed to resubmit (19)
[ 1568.721458] btusb_bulk_complete: hci0 urb f180dd00 failed to resubmit (19)
[ 1568.722020] btusb_send_frame: hci0 urb f2ab2480 submission failed


```

If i go to aditional contollers/drivers i see the broadcom driver (not the default one) but the 80211 as active.

And yes, i've tried the wifi  on/off switch, but it only turns on the bluetooth.



thanks for all your helo so far.

---

### Post by Ayuthia on 2010-10-12
> **favri said:**
> ```

lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:2d:ac:a5:29
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.28.104 latency=0 multicast=yes
       resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:d0300000-d0303fff


```

```

[ 1566.418480] btusb_bulk_complete: hci0 urb f1872480 failed to resubmit (19)
[ 1566.418496] btusb_intr_complete: hci0 urb f1872f00 failed to resubmit (19)
[ 1566.419505] btusb_bulk_complete: hci0 urb f1872280 failed to resubmit (19)
[ 1566.420034] btusb_send_frame: hci0 urb f289e580 submission failed
[ 1568.184278] usb 5-3: new full speed USB device using ohci_hcd and address 16
[ 1568.720050] usb 5-3: USB disconnect, address 16
[ 1568.720375] btusb_bulk_complete: hci0 urb f180d580 failed to resubmit (19)
[ 1568.720391] btusb_intr_complete: hci0 urb f180d980 failed to resubmit (19)
[ 1568.721458] btusb_bulk_complete: hci0 urb f180dd00 failed to resubmit (19)
[ 1568.722020] btusb_send_frame: hci0 urb f2ab2480 submission failed


```

If i go to aditional contollers/drivers i see the broadcom driver (not the default one) but the 80211 as active.

And yes, i've tried the wifi  on/off switch, but it only turns on the bluetooth.



thanks for all your helo so far.

I think that we might need to see more of the dmesg.  Can you attach it as a file:
```

dmesg > ~/dmesg.txt

```
You should be able to find the dmesg.txt file in your home directory.  Please attach it.  I just want to see what is happening at the end of the dmesg.  It is most likely the message that was logged after we loaded the brcm80211 module.

---

### Post by favri on 2010-10-12
Here it is.

---

### Post by Ayuthia on 2010-10-12
```

[   13.938268] brcm80211 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.938276] brcm80211 0000:06:00.0: setting latency timer to 64
[   13.963989] brcm80211: fail to load firmware brcm/bcm43xx-0.fw
[   13.963993] brcm80211: Failed to find firmware usually in /lib/firmware/brcm
[   13.964046] brcm80211 0000:06:00.0: PCI INT A disabled
[   13.964060] brcm80211: wl_pci_probe: wl_attach failed!

```
Here is the key piece.  The firmware is not there yet.  To get and install the firmware:
```

cd
git clone git://git.kernel.org/pub/scm/linux/kernel/git/dwmw2/linux-firmware.git
cd linux-firmware
sudo cp -a brcm /lib/firmware
cd /lib/firmware/brcm
sudo ln -s bcm43xx-0-610-809-0.fw bcm43xx-0.fw
sudo ln -s bcm43xx_hdr-0-610-809-0.fw bcm43xx_hdr-0.fw

```
Then we will remove the module and reload it:
```

sudo rmmod brcm80211
sudo insmod /lib/modules/`uname -r`/brcm80211.ko

```
Hopefully that will get it this time.

---

### Post by favri on 2010-10-12
I think we are almost done ;)

iwconfig
```


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

lshw -C network
```


*-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:2d:ac:a5:29
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.28.104 latency=0 multicast=yes
       resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
  *-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:62:39:fa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0300000-d0303fff


```
rfkill list

```

1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
14: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no
24: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
I guess that: soft blocked is our last barrier?

---

### Post by favri on 2010-10-12
Yesssssssssssssssssssssssssssssssssssssssssss :popcorn:

I did it!!!!

Thx, i really appreciate your effort and pacience for helping me.
This encourages me to use linux.

1 little thng:

2 times the system crashed wile searching for the wirelss connection. Any Idea?

Thx!

---

### Post by Ayuthia on 2010-10-12
> **favri said:**
> I think we are almost done ;)

iwconfig
```


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

lshw -C network
```


*-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:2d:ac:a5:29
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.28.104 latency=0 multicast=yes
       resources: irq:43 memory:d0200000-d023ffff ioport:a000(size=128)
  *-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 90:4c:e5:62:39:fa
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d0300000-d0303fff


```
rfkill list

```

1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
14: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no
24: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
I guess that: soft blocked is our last barrier?

It looks like it.  Can you try the following:
```

sudo ifconfig wlan0 up
sudo iwlist scan

```
Please let us know the results.  Hopefully that will bring up the device and allow it to scan.

---

### Post by favri on 2010-10-12
[SIZE=4]**@Ayuthia **[/SIZE]

thanks for everything, it's up and working now!!!!

---

### Post by Ayuthia on 2010-10-12
Congratulations!  I am glad that it is up and running.

Here is some information about the driver:
[http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)

It does mention that the driver can cause a crash and they are working on resolving it.  Hopefully it does not happen often.

---

### Post by pinkee on 2010-10-17
> **karlitosbrigante said:**
> Few words follow this...
System -> Administration -> Additional Drivers -> Activate Broadcom STA wireless driver
tell me if it works but i'm sure that will work fine

I, or my friend rather, was able to find the issue on my Aspire 1551 and it may apply to other systems.

asus_wmi breaks rfkill! remove and blacklist it and the STA driver works fine. Hope this helps other people.

---

### Post by Pablo Alonso on 2010-11-24
Hi Ayuthia and Pinkee.

I have bought today an acer 5551-2452 with wifi broadcom 43225 rev01
and I'm trying to make ubuntu maverick work with wifi to no avail........

please can you write a clean process to achive it?
my little undertanding is not letting me grasp the solution of the thread and I need the wifi in order to start using ubuntu.......

if anyone else can help, i really appreciate this.

just in case, my email is [email]pablo.alonso@itsas.com.ar[/email]

thanks guys!
regards,
Pablo

---

### Post by Pablo Alonso on 2010-11-26
> **pinkee said:**
> I, or my friend rather, was able to find the issue on my Aspire 1551 and it may apply to other systems.

asus_wmi breaks rfkill! remove and blacklist it and the STA driver works fine. Hope this helps other people.

Hey Pinkee, please.
how can I blacklist asus_wmi ???

can someone else help??...

thanks!

---

### Post by Pablo Alonso on 2010-11-26
Oh God it is working now!

I share with you the solution I found: [http://ubuntuforums.org/archive/index.php/t-1341538.html](http://ubuntuforums.org/archive/index.php/t-1341538.html) (just first post)

Besides I have to leave the laptop wifi light on (orange led) as it it were turned off to get it connected to the networks.....

Hope it helps someone else.

byebye

---

