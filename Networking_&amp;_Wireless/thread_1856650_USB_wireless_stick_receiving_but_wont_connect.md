---
title: "USB wireless stick receiving but wont connect"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by dopeyal on 2011-10-08
I have Ubuntu v 11-04 installed  and it recognises my Edimax EW-7612 USB stick, showing the local Wireless networks  available.  I select my network and put in the key but it wont connect to the internet.
I have run some terminal commands and post the results below.  Can you please interpret the outputs,  and advise what I need to do to connect.   Thanks.

**lsmod**

Module                  Size  Used by
binfmt_misc            13213  1 
snd_es1968             28326  2 
gameport               15027  1 snd_es1968
snd_ac97_codec        105614  1 snd_es1968
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_es1968,snd_ac97_codec
snd_page_alloc         14073  2 snd_es1968,snd_pcm
snd_mpu401_uart        13865  1 snd_es1968
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  12 snd_es1968,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
soundcore              12600  1 snd
radio_maestro          13205  0 
r8712u                281937  0 
v4l2_common            16757  1 radio_maestro
pcmcia                 39671  0 
yenta_socket           27230  0 
irda                  185091  0 
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
shpchp                 32345  0 
parport_pc             32111  1 
videodev               75143  2 radio_maestro,v4l2_common
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
i2c_piix4              13095  0 
crc_ccitt              12595  1 irda
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
e100                   40108  0 
floppy                 60032  0 

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     unassociated  Nickname:"rtl_wifi"

          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry; off   RTS thr; off   Fragment thr; off

          Power Management; off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



**iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

          Cell 01 - Address: 00:22:3F:8D:19:6C
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key; on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103

                    Signal level=44/100  
          Cell 02 - Address: 7C:03:4C:76:A6:FD
                    ESSID:"SKY6A6FC"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key; on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie

                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=26/100  
          Cell 03 - Address: 00:26:44:C7:C3:03
                    ESSID:"Bebox289280"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key; on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 04 - Address: 94:44:52:4F:10:02
                    ESSID:"kelsey"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key; on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Signal level=7/100  
          Cell 05 - Address: 00:22:3F:5C:2B:0C
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key; on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  



**dmesg | grep 87**

[    0.000000] Kernel command line: root=UUID=f12e73d6-c58b-4d87-8aaf-eadb5649b08c ro quiet splash 
[    0.000000]     vmalloc : 0xd87f0000 - 0xff7fe000   ( 624 MB)
[    0.620687] ACPI: Power Resource [C1A8] (off)
[    0.697341] ACPI: PCI Interrupt Link [C187] (IRQs *11)
[    0.698703] vgaarb: loaded
[    0.699877] usbcore: registered new interface driver hub
[    0.746087] pnp 00:02: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.752876] pnp 00:07: [io  0x00c0-0x00df]
[    0.753649] pnp 00:0c: [io  0x0800-0x087f]
[    0.753834] system 00:0c: [io  0x0800-0x087f] has been reserved
[    0.753872] system 00:0c: [io  0xf000-0xf0cf] has been reserved
[    0.801240] ACPI: PCI Interrupt Link [C187] enabled at IRQ 11
[    0.801263] pci 0000:00:04.0: PCI INT A -> Link[C187] -> GSI 11 (level, low) -> IRQ 11
[    0.801286] pci 0000:00:04.1: PCI INT A -> Link[C187] -> GSI 11 (level, low) -> IRQ 11
[    0.877018] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.919870] ACPI: acpi_idle registered with cpuidle
[    1.144687] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.265873] Cannot allocate resource for EISA slot 5
[    1.365260]   Magic number: 15:765:878
[    2.408734] Freeing initrd memory: 12512k freed
[   37.107805] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   37.576587] NET: Registered protocol family 23
[   37.645087] yenta_cardbus 0000:00:04.0: Using CSCINT to route CSC interrupts to PCI
[   37.876575] yenta_cardbus 0000:00:04.0: ISA IRQ mask 0x0438, PCI irq 11
[   37.876589] yenta_cardbus 0000:00:04.0: Socket status: 30000006
[   38.254510] r8712u: DriverVersion: v7_0.20100831
[   38.254590] r8712u: register rtl8712_netdev_ops to netdev_ops
[   38.254601] r8712u: USB_SPEED_LOW with 4 endpoints
[   38.270298] r8712u: Boot from EFUSE: Autoload OK
[   38.477877] psmouse serio4: ID: 10 00 64
[   39.589037]  excluding 0x820-0x87f
[   39.687613]  0x4d0-0x4d7
[   39.698361] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: excluding 0x820-0x87f
[   39.728775] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xf0000-0xfffff
[   43.635393] r8712u: CustomerID = 0x0000
[   43.635408] r8712u: MAC Address from efuse = 00:1f:1f:d9:0e:c9
[   43.652708] usbcore: registered new interface driver r8712u
[   44.751252] r8712u: 1 RCR=0x153f00e
[   44.754210] r8712u: 2 RCR=0x553f00e

---

### Post by praseodym on 2011-10-08
Hi,

can you show additionally:
```

lsusb
```

---

### Post by dopeyal on 2011-10-09
here is the result from  lsusb:

  	 	 	 	 	 	   **Lsusb**
 

 

 Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
 

 Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 

thank you,

---

### Post by praseodym on 2011-10-09
You can install a newer driver from Realtek:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential unzip 
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/RTL8191SU_usb_linux_v2.6.6.0.20101111.zip
unzip -x RTL8191SU_usb_linux_v2.6.6.0.20101111.zip
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111/driver
tar xvf rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111.tar.gz
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.6.0.20101111
make
sudo make install 
```
If "sudo make install" stops with an error, move the module by hand:
```
sudo cp 8712u.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless/
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Load the right driver:
```
sudo modprobe -rfv r8712u
sudo modprobe -v 8712u
sudo depmod -a
```
Re-plug the stick. Dont delete the driver, the module has to be build again after a kernel upgrade.

---

