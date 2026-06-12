---
title: "Wireless Not Working"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by Torstol on 2013-05-14
I am new to Linux and have Ubuntu 12.10 on my laptop. For some reason the wireless is not picking up a single signal. I am not a computer guru so any direction is greatly appreciated. 

Thanks, :)

---

### Post by Hadaka on 2013-05-14
Hi, and welcome !
lets take a look at few things.
please open a terminal  ctrl/alt/t
then COPY and paste the following one line at a time.
```
lspci -nn | egrep '0200|0280'
lsmod
iwconfig
ifconfig
rfkill list all
```
Please copy each output and post.
thanks.

---

### Post by Torstol on 2013-05-14
Is there a notepad for Ubuntu that comes with the vanilla download? I need to paste the results from the terminal and use a flash drive to put them on this laptop to post here.

---

### Post by Torstol on 2013-05-14
I apologize for how this might not come out neatly. 

heprodigy@ubuntu:~$ lspci - nn  egrep'0200|0280' 
Usage: lspci [<switches>] 


Basic display modes: 
-mm		Produce machine-readable output(single -m for an obsolete format) 
-t		Show bus tree 


Display options: 
-v		Be verbose (-vv for very verbose) 
-k		Show kernel drivers handling eachdevice 
-x		Show hex-dump of the standard partof the config space 
-xxx		Show hex-dump of the whole configspace (dangerous; root only) 
-xxxx		Show hex-dump of the 4096-byteextended config space (root only) 
-b		Bus-centric view (addresses andIRQ's as seen by the bus) 
-D		Always show domain numbers 


Resolving of device ID's to names: 
-n		Show numeric ID's 
-nn		Show both textual and numeric ID's(names & numbers) 
-q		Query the PCI ID database forunknown ID's via DNS 
-qq		As above, but re-query locallycached entries 
-Q		Query the PCI ID database for allID's via DNS 


Selection of devices: 
-s[[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Showonly devices in selected slots 
-d [<vendor>]:[<device>]			Showonly devices with specified ID's 


Other options: 
-i <file>	Use specified IDdatabase instead of /usr/share/misc/pci.ids.gz 
-p <file>	Look up kernel modulesin a given file instead of default modules.pcimap 
-M		Enable `bus mapping' mode(dangerous; root only) 


PCI access options: 
-A <method>	Use the specified PCIaccess method (see `-A help' for a list) 
-O <par>=<val>	Set PCIaccess parameter (see `-O help' for a list) 
-G		Enable PCI access debugging 
-H <mode>	Use direct hardwareaccess (<mode> = 1 or 2) 
-F <file>	Read PCI configurationdump from a given file 


theprodigy@ubuntu:~$ lsmod 
Module                  Size  Used by 
snd_hda_codec_idt      70209  1 
snd_hda_codec_hdmi     32007  1 
coretemp               13400  0 
joydev                 17457  0 
dell_wmi               12681  0 
sparse_keymap          13890  1dell_wmi 
gpio_ich               13383  0 
dell_laptop            17369  0 
dcdbas                 14438  1dell_laptop 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel 
snd_hwdep              13602  1snd_hda_codec 
snd_pcm                96580  3snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
microcode              22803  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1snd_seq_midi 
psmouse                95552  0 
serio_raw              13215  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
lp                     17759  0 
parport                46345  3parport_pc,ppdev,lp 
bluetooth             209199  7 bnep 
snd_seq_midi_event     14899  1snd_seq_midi 
mac_hid                13205  0 
b43                   369753  0 
snd_seq                61521  2snd_seq_midi,snd_seq_midi_event 
mac80211              539908  1 b43 
r852                   18281  0 
sm_common              16817  1 r852 
nand                   54706  2r852,sm_common 
nand_ids               12723  1 nand 
mtd                    44905  2sm_common,nand 
nand_bch               13147  1 nand 
bch                    17399  1nand_bch 
nand_ecc               13230  1 nand 
cfg80211              206566  2b43,mac80211 
r592                   18019  0 
bcma                   35656  1 b43 
memstick               16554  1 r592 
wmi                    19070  1dell_wmi 
snd_timer              29425  2snd_pcm,snd_seq 
snd_seq_device         14497  3snd_seq_midi,snd_rawmidi,snd_seq 
i915                  520519  3 
drm_kms_helper         46784  1 i915 
snd                    78734  16snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
drm                   275528  4i915,drm_kms_helper 
soundcore              15047  1 snd 
i2c_algo_bit           13413  1 i915 
snd_page_alloc         18484  2snd_hda_intel,snd_pcm 
video                  19335  1 i915 
sdhci_pci              18616  0 
sdhci                  32645  1sdhci_pci 
firewire_ohci          40401  0 
firewire_core          64368  1firewire_ohci 
crc_itu_t              12707  1firewire_core 
ssb                    52036  1 b43 
sky2                   58111  0 


theprodigy@ubuntu:~$ iwconfig 
eth0      no wireless extensions. 


lo        no wireless extensions. 


theprodigy@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr00:23:ae:17:9d:53  
          UP BROADCAST MULTICAST MTU:1500  Metric:1 
          RX packets:0 errors:0dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TXbytes:0 (0.0 B) 
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1 Mask:255.0.0.0 
          inet6 addr: ::1/128Scope:Host 
          UP LOOPBACK RUNNING MTU:16436  Metric:1 
          RX packets:456 errors:0dropped:0 overruns:0 frame:0 
          TX packets:456 errors:0dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:28432 (28.4 KB)  TXbytes:28432 (28.4 KB) 


theprodigy@ubuntu:~$ rfkill list all

---

### Post by Hadaka on 2013-05-14
Hi, please repost the output of..
```

lspci -nn | egrep '0200|0280'
```
you missed one of the pipe symbols...there are 2  " | "
we need this info to determine the correct driver
all you need to post back is the
0280 [14e4:XXXX]

thanks.

---

### Post by Torstol on 2013-05-14
theprodigy@ubuntu:~$ lspci -nn | egrep'0200|0280' 
09:00.0 Ethernet controller [0200]:Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller[11ab:4354] (rev 12) 
0b:00.0 Network controller [0280]:Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by Hadaka on 2013-05-14
ok, lets give this a go and see what happens

```
sudo modprobe -rfv dell_wmi
sudo modprobe b43
```
any changes?

---

### Post by Torstol on 2013-05-14
No changes by doing that for making my wireless function.

---

### Post by Hadaka on 2013-05-14
ok, are you able to connect to your router with a different computer or device?
do you have a triangle symbol in the upper right corner..next to the envelope?
have you clicked it...if you do...and made sure  "Enable wireless" is checked?
and lastly do you have the ability to connect to the router wired?
thanks.

---

### Post by Torstol on 2013-05-15
Right now I am using my newer laptop to connect to my router.

I have a triangular symbol near the upper right corner of my screen. When clicked it has the options: wired network, disconnected, VPN connections, enable networking, connection information, edit connections. The enable networking has a checkmark beside it.

I cannot connect my older PC with ubuntu to a router with a wired connection currently.

---

### Post by Hadaka on 2013-05-15
ok, i noticed in you rlsmod output you have the b43 driver loaded
and that should work for your card. The following is a way to load
the b43 driver with no internet connection...
be sure to extract the b43 zip file first before you do the commands
the file will be on the bottom of this post.

```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
 
```
Drag the zip file to your Desktop ...right click it....and choose  EXTRACT HERE

---

### Post by Torstol on 2013-05-15
But how do I extract that file first before I enter those commands?

---

### Post by Hadaka on 2013-05-15
Hi, put it on a usb stick,take it to your
buntu machine and drop it on the Desktop

---

### Post by Torstol on 2013-05-15
Still no luck finding my wireless connection after that. Results after extracting and typing commands below.

theprodigy@ubuntu:~$ sudo mkdir/lib/firmware/b43 
[sudo] password for theprodigy: 
mkdir: cannot create directory`/lib/firmware/b43': File exists 
theprodigy@ubuntu:~$ sudo cpDesktop/b43/ * /lib/firmware/b43 
cp: omitting directory `Desktop/b43/' 
cp: omitting directory `Desktop' 
cp: omitting directory `Documents' 
cp: omitting directory `Downloads' 
cp: omitting directory `Music' 
cp: omitting directory `Pictures' 
cp: omitting directory `Public' 
cp: omitting directory `Templates' 
cp: omitting directory `Videos' 
theprodigy@ubuntu:~$ sudo rmmod -f b43 
ERROR: Removing 'b43': No such file ordirectory 
theprodigy@ubuntu:~$ sudo rmmod -f ssb 
theprodigy@ubuntu:~$ sudo modprobe b43

---

### Post by Hadaka on 2013-05-15
Hi,please show me....
```
ls Desktop
```

thats lower case L
thanks

---

### Post by Torstol on 2013-05-15
ls: cannot access desktop: No such file or directory

---

### Post by Hadaka on 2013-05-15
Hi, thats upper case "D"

```
ls Desktop
```
or try..
```
cd Desktop
```
```
ls
```
thanks

---

### Post by Torstol on 2013-05-15
b43 b43.zip

---

### Post by Hadaka on 2013-05-15
ok..please COPY and paste these commands one at
a time onto the usb stick.

```

sudo cp Desktop/b43/* /lib/firmware/b43
 sudo rmmod -f b43
 sudo rmmod -f ssb
 sudo modprobe b43
```
note the spacing between sudo cp Desktop/b43/* <space> /lib/firmware/b43
thanks.

---

### Post by Torstol on 2013-05-15
Worked. You sir are a genius. Thank you so much for your help.

---

### Post by Hadaka on 2013-05-15
Thanks, but dont run off yet we arnt done.

---

### Post by Hadaka on 2013-05-15
you need to mark this solved...
How to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

*AFTER you do this...
```
echo "b43" | sudo tee -a /etc/modules
```
thanks.

---

### Post by Torstol on 2013-05-15
Done.

---

