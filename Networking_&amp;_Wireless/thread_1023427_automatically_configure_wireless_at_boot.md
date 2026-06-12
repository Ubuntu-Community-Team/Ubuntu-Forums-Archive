---
title: "automatically configure wireless at boot"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by rioguia on 2008-12-27
I want to automatically configure my wireless Netgear MA401 (PCMCIA card for my laptop) on boot. I have tried using the GUI to no avail.  Can someone tell me which file I need to edit and the entries I need to make?  Thanks.

Currently to successfully get a connection, I have to open a terminal and type the following:
sudo iwconfig eth0 mode managed key xxxxxxxxxxxxxxxxdxxxxxxxxx
sudo ifconfig eth0 10.0.0.2 netmask 255.255.255.0
sudo route add default gw 10.0.0.1

After that my connection is fine.  Here is some information about my connection:

sudo cat /etc/network/interfaces gives
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.0.0.1
	netmask 255.255.255.0
	network 10.0.0.0
	broadcast 10.0.0.255
	gateway 10.0.0.1
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid my_essid_name
	wireless-key1 xxxxxxxxxxxxxxxxxxxxxxxxx
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 10.0.0.10
	dns-search my_domaine_name

iwlist scan gives

Cell 02 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"my_essid_names"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:39/153  Noise level:7/153
                    Encryption key:on
                    Extra: Last beacon: 4703728ms ago
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s

---

### Post by neu2buntu on 2008-12-27
try this first maybe... reboot, and dont startup your wireless connection, do command ```
lsmod
``` (if wireless is your only connection) copy and paste to a gedit file(so you can copy and post here in forum) ,then do your commands for connecting up .post the output of the 1st lsmod. then next after that do ```
lsmod
``` again and paste it so we can see if there is any difference in the modules loaded after you are connected.....

---

### Post by rioguia on 2008-12-28
My notes on my install (including how I load my modules) are here:[here.]("http://www.substantis.com/blog/?p=47")

Here is the first lsmod:
sudo lsmod > first
Module                  Size  Used by
ipv6                  263972  8 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,sco,rfcomm,l2cap
rfkill                 17176  0 
led_class              12164  0 
nvram                  16524  0 
ppdev                  15620  0 
apm                    26332  2 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
snd_cs4232             21780  2 
snd_opl3_lib           18560  1 snd_cs4232
snd_hwdep              15236  1 snd_opl3_lib
snd_cs4231_lib         32640  1 snd_cs4232
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_cs4231_lib,snd_pcm_oss
snd_page_alloc         16136  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart        15360  1 snd_cs4232
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  1 snd_seq_midi
snd_seq                57776  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29960  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device         15116  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_cs4232,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uart401                17348  0 
ad1848                 36348  0 
sound                  82892  2 uart401,ad1848
soundcore              15328  2 snd,sound
parport_pc             39204  1 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
orinoco_cs             21516  1 
orinoco                48020  1 orinoco_cs
hermes                 14976  2 orinoco_cs,orinoco
pcmcia                 43052  1 orinoco_cs
evdev                  17696  4 
serio_raw              13444  0 
psmouse                45200  0 
yenta_socket           31756  4 
i2c_piix4              16144  0 
rsrc_nonstatic         19072  1 yenta_socket
intel_agp              33724  1 
pcmcia_core            43412  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               31892  1 i2c_piix4
pcspkr                 10624  0 
agpgart                42184  1 intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
uhci_hcd               30736  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
usbcore               148848  2 uhci_hcd
dock                   16656  1 libata
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 

Second:
sudo lsmod > second
Module                  Size  Used by
ipv6                  263972  8 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,sco,rfcomm,l2cap
rfkill                 17176  0 
led_class              12164  0 
nvram                  16524  0 
ppdev                  15620  0 
apm                    26332  2 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
snd_cs4232             21780  2 
snd_opl3_lib           18560  1 snd_cs4232
snd_hwdep              15236  1 snd_opl3_lib
snd_cs4231_lib         32640  1 snd_cs4232
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_cs4231_lib,snd_pcm_oss
snd_page_alloc         16136  2 snd_cs4231_lib,snd_pcm
snd_mpu401_uart        15360  1 snd_cs4232
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  1 snd_seq_midi
snd_seq                57776  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29960  4 snd_opl3_lib,snd_cs4231_lib,snd_pcm,snd_seq
snd_seq_device         15116  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_cs4232,snd_opl3_lib,snd_hwdep,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uart401                17348  0 
ad1848                 36348  0 
sound                  82892  2 uart401,ad1848
soundcore              15328  2 snd,sound
parport_pc             39204  1 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
orinoco_cs             21516  1 
orinoco                48020  1 orinoco_cs
hermes                 14976  2 orinoco_cs,orinoco
pcmcia                 43052  1 orinoco_cs
evdev                  17696  4 
serio_raw              13444  0 
psmouse                45200  0 
yenta_socket           31756  4 
i2c_piix4              16144  0 
rsrc_nonstatic         19072  1 yenta_socket
intel_agp              33724  1 
pcmcia_core            43412  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               31892  1 i2c_piix4
pcspkr                 10624  0 
agpgart                42184  1 intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
uhci_hcd               30736  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
usbcore               148848  2 uhci_hcd
dock                   16656  1 libata
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1

---

### Post by shafi on 2008-12-28
> **rioguia said:**
> I want to automatically configure my wireless Netgear MA401 (PCMCIA card for my laptop) on boot. I have tried using the GUI to no avail.  Can someone tell me which file I need to edit and the entries I need to make?  Thanks.

Currently to successfully get a connection, I have to open a terminal and type the following:
sudo iwconfig eth0 mode managed key xxxxxxxxxxxxxxxxdxxxxxxxxx
sudo ifconfig eth0 10.0.0.2 netmask 255.255.255.0
sudo route add default gw 10.0.0.1


Open a text editor and paste the following:
[HTML]
#!/bin/sh
sudo iwconfig eth0 mode managed key xxxxxxxxxxxxxxxxdxxxxxxxxx
sudo ifconfig eth0 10.0.0.2 netmask 255.255.255.0
sudo route add default gw 10.0.0.1
[/HTML]
save the file  [ file.sh] and then 
[HTML]
sudo chmod +x file.sh
[/HTML]
an executable file will be created then click:
System -> Preferences -> Session
after that brows to the new executable file which you created.
then you have it each time at boot.

---

### Post by rioguia on 2008-12-28
Thanks for the idea but that won't work because there is no way to provide the sudo password that I am aware of.

---

### Post by shafi on 2008-12-28
> **rioguia said:**
> Thanks for the idea but that won't work because there is no way to provide the sudo password that I am aware of.
Uh..
You tried with out sudo?

---

### Post by rioguia on 2008-12-28
iwconfig eth0 mode managed key xxxxxxxxxxxxxxxxxxxxxxxxx
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Operation not permitted.

---

### Post by neu2buntu on 2008-12-28
its not a module load problem,.. one place you could try and add your script is in ```
sudo gedit /etc/rc.local
``` try after line exit0 first of all (without sudo in your script)       and from reading your setup you must need to keep a static ip ,.. im no expert here but maybe try the network-applet >right click>edit-connections>wireless>choose your ap>edit>ip4 settings >uutomatic(DHPC)>routes >add then edit these settings (not sure how these will work but they are worth a try!

---

### Post by rioguia on 2008-12-28
Thanks for your response.  Great minds think alike!  Based on this [thread]("http://ubuntuforums.org/showthread.php?t=684495") here is my script.  Don't forget to sudo chmod +x /etc/rc.local



#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
#
# The essid name must be in "quotes" like this.  Don't forget to sudo chmod +x /etc/rc.d/local

ifconfig eth0 down
ifconfig eth0 10.0.0.10 netmask 255.255.255.0
route add default gw 10.0.0.1
iwconfig eth0 essid "essid_name"
iwconfig eth0 mode managed key xxxxxxxxxxxxxxxxxxxxxxxxx
ifconfig eth0 up

exit 0

---

### Post by neu2buntu on 2008-12-29
looks good ,does it work....?  was just wondering is it neccessary to bring down the wired connection too although you may not be using it, just incase it may be conflicting with the wireless?

---

### Post by rioguia on 2008-12-29
It works great!

---

