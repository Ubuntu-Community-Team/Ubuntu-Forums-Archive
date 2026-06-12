---
title: "Cannot connect wirelessly with BCM4312 WLAN card!!"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-06-12
Hi all.

I having a bit of trouble correctly setting up my Broadcom BCM4312 WLAN card to connect Wirelessly.

It seems to connect for about 30 seconds but then looses connection.

I have read numerous posts but all I have tried has failed.

I'm also still pretty new to the whole Ubuntu game. 
So I would appreciate it if anybody could try and help me to fix this issue??

Cheers for now...

---

### Post by scrypt on 2009-06-12
I seemed to have completely turned the power to my WLAN Card off.
There are no WIFI light on.

an anyone shed any light on this for me??

---

### Post by scrypt on 2009-06-12
This is the output to 'lshw -c network'

scrypt-laptop:~$ sudo lshw -c network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

As you can see it says it is unclaimed,

---

### Post by uberlube on 2009-06-12
use the guide in my sig. it should be a good start.

---

### Post by scrypt on 2009-06-12
Hey uberlube thanks for the reply.

Ill take a look.

everyhting i have tried has made things worse,

It's been one of thise days for me..

---

### Post by scrypt on 2009-06-12
I have NO light on my laptop indicating that my WIFI is enabled on my laptop.

It usually is ON.

Do you have any recomendations about this?

also bellow is what my terminal produced when I ran you suggested commands:
does it look okay to you??

I'm running through your suggested commands now and in downloading::

mark@mark-laptop:~$ echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
mark@mark-laptop:~$ echo "blacklist ssb" >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
mark@mark-laptop:~$ echo "blacklist b43" >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied
mark@mark-laptop:~$ echo "alias wlan0 ndiswrapper" >> /etc/modprobe.d/ndiswrapper
bash: /etc/modprobe.d/ndiswrapper: Permission denied
mark@mark-laptop:~$ echo "alias wlan0 ndiswrapper" >> /etc/modprobe.conf
bash: /etc/modprobe.conf: Permission denied
mark@mark-laptop:~$ echo "ndiswrapper" >> /etc/modules
bash: /etc/modules: Permission denied
mark@mark-laptop:~$ mkdir /root/wireless_driver
mkdir: cannot create directory `/root/wireless_driver': Permission denied
mark@mark-laptop:~$ cd /root/wireless_driver/
bash: cd: /root/wireless_driver/: No such file or directory
mark@mark-laptop:~$ wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
--2009-06-12 23:52:07--  [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
Resolving ftp.us.dell.com... 143.166.170.10
Connecting to ftp.us.dell.com|143.166.170.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 54750848 (52M) [application/octet-stream]
Saving to: `R151517.EXE'

---

### Post by scrypt on 2009-06-12
No joy yet mate. it didn't work for me...

---

### Post by gradinaruvasile on 2009-06-12
You should give those commands with sudo before them.
like 
[COLOR="Red"]sudo[/COLOR] echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
and so on for evry one of them

---

### Post by scrypt on 2009-06-12
I went into synaptics and reinstalled b43-fcutter firmware for my card, and it has turned my card back on and at the moment I am connected wirelessly :)

Strange thing is I have done this a couple of times already....

I am going to reboot and see if I can still connect wirelessly.

If I can then I think the commands you recomended did go some way in helping me fix my issue. 

One more thing though: is when I look in system-Administration-Hardware drivers

And I try to activate the wireless STA propriety driver for my card I imediately loose connection.

Can you shed any light on why this might be happening??

---

### Post by scrypt on 2009-06-12
okkay thanks for the sudo tip. i tried them and rebooted and once again I have No Wireless connection and NO WIF light is on to indicate that my WLAN card is on.

Whwn I just shutdown I seen a few error messages flash by, they said something along the lines of:

modprobe and ndsiwrapper or something like that (sorry i can't be clearer)

I still have no wireless can anybody help???

---

### Post by scrypt on 2009-06-12
here is my iwconfig output:-

mark@mark-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

---

### Post by scrypt on 2009-06-12
This is an error message that shows a few times when I shutdown:-

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.


I do NOT know what I should do??

---

### Post by scrypt on 2009-06-12
Any help would be appreciated...

I cannot activate the Broadcom STA wireless driver in system-adminstration-Hardware drivers.

I click on the activate button, BUT nothing happens...

can anyone help??

---

### Post by scrypt on 2009-06-12
Hi I managed to get my WIFI light back ON and Wireless connection (Intermitent)

By using these commands by:   albinootje

Here are the commands i folowed from his post i found here:

([http://ubuntuforums.org/archive/index.php/t-1154403.html](http://ubuntuforums.org/archive/index.php/t-1154403.html))

gksu gedit /etc/rc.local


Then make it look like this :

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

modprobe wl
modprobe ieee80211_crypt


These commands got my WLAN card back on and the wifi light on to.

BUT I still only have intermitent wireless conectivity. it comes and goes on phases.

Can someon help me sort this out??

---

### Post by scrypt on 2009-06-12
Right fingers crossed i think i have it working thanks to: albinootje post @


([http://ubuntuforums.org/archive/inde...t-1154403.html](http://ubuntuforums.org/archive/inde...t-1154403.html))

This got it working. but as for the intermittent connection.

I just deleted my Wireless conection profile from Network Manager applet and re entered all my wireles connection details and WPA Key etc.

and it seemd to have done the trick...

Thank's for the help

scrypt

---

### Post by scrypt on 2009-06-13
I still have intermittent wireless connectivity.

When I Boot-Up I can connect for about 30 seconds, then I loose connection for about the same time. This happens for roughly three times. Then I completely loose wireless connectivity.

Can anyone help with this??

---

### Post by scrypt on 2009-06-13
I could really use some hwlp with this.

Can anyone offer any help??

---

### Post by kevdog on 2009-06-13
Well if you could post a few things for starts it would help

lspci -nnm
lshw -C network
lsmod

---

### Post by scrypt on 2009-06-13
Hey Kavdog Good to speak to you again!!

Here are my outputs from the suggested commands.

thank's for the help

mark@mark-laptop:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 4 Series Chipset Memory Controller Hub [2a40]" -r07 "Dell [1028]" "Device [02a0]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "Mobile 4 Series Chipset PCI Express Graphics Port [2a41]" -r07 "" ""
00:1a.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #4 [2937]" -r03 "Dell [1028]" "Device [02a0]"
00:1a.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #5 [2938]" -r03 "Dell [1028]" "Device [02a0]"
00:1a.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #6 [2939]" -r03 "Dell [1028]" "Device [02a0]"
00:1a.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB2 EHCI Controller #2 [293c]" -r03 -p20 "Dell [1028]" "Device [02a0]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801I (ICH9 Family) HD Audio Controller [293e]" -r03 "Dell [1028]" "Device [02a0]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801I (ICH9 Family) PCI Express Port 1 [2940]" -r03 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801I (ICH9 Family) PCI Express Port 2 [2942]" -r03 "" ""
00:1c.3 "PCI bridge [0604]" "Intel Corporation [8086]" "82801I (ICH9 Family) PCI Express Port 4 [2946]" -r03 "" ""
00:1c.5 "PCI bridge [0604]" "Intel Corporation [8086]" "82801I (ICH9 Family) PCI Express Port 6 [294a]" -r03 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #1 [2934]" -r03 "Dell [1028]" "Device [02a0]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #2 [2935]" -r03 "Dell [1028]" "Device [02a0]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #3 [2936]" -r03 "Dell [1028]" "Device [02a0]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB2 EHCI Controller #1 [293a]" -r03 -p20 "Dell [1028]" "Device [02a0]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -r93 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "ICH9M LPC Interface Controller [2919]" -r03 "Dell [1028]" "Device [02a0]"
00:1f.2 "SATA controller [0106]" "Intel Corporation [8086]" "ICH9M/M-E SATA AHCI Controller [2929]" -r03 -p01 "Dell [1028]" "Device [02a0]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801I (ICH9 Family) SMBus Controller [2930]" -r03 "Dell [1028]" "Device [02a0]"
01:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Mobility Radeon HD 3650 [9591]" "Dell [1028]" "Device [02a0]"
01:00.1 "Audio device [0403]" "ATI Technologies Inc [1002]" "RV635 Audio device [Radeon HD 3600 Series] [aa20]" "Dell [1028]" "Device [02a0]"
04:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11b/g [4315]" -r01 "Dell [1028]" "Device [000c]"
08:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "NetLink BCM5784M Gigabit Ethernet PCIe [1698]" -r10 "Dell [1028]" "Device [02a0]"
09:01.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -r05 -p10 "Dell [1028]" "Device [02a0]"
09:01.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r22 -p01 "Dell [1028]" "Device [02a0]"
09:01.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r12 "Dell [1028]" "Device [02a0]"
09:01.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -r12 "Dell [1028]" "Device [02a0]"
mark@mark-laptop:~$ 


mark@mark-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:de:c3:e0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.0.3 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:32:91:69:a7:a0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
mark@mark-laptop:~$ 

mark@mark-laptop:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         10752  0 
xt_DSCP                11264  0 
binfmt_misc            16904  1 
af_packet              25856  4 
ppdev                  15748  0 
rfcomm                 44304  4 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20352  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
vboxnetflt             92296  0 
vboxdrv               119080  1 vboxnetflt
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
ipt_REJECT             11136  1 
ipt_LOG                13700  8 
xt_limit               10372  8 
xt_tcpudp              11008  7 
xt_state               10112  6 
ipt_addrtype           10496  0 
ip6table_filter        10624  1 
ip6_tables             21008  1 ip6table_filter
ipv6                  264228  24 
nf_nat_irc             10240  0 
nf_conntrack_irc       13348  1 nf_nat_irc
nf_nat_ftp             10880  0 
nf_conntrack_ftp       15652  1 nf_nat_ftp
sbp2                   29324  0 
lp                     17156  0 
parport                42604  2 ppdev,lp
snd_hda_intel         385072  3 
snd_pcm_oss            46848  0 
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
iptable_nat            13448  0 
nf_nat                 25368  4 ipt_MASQUERADE,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      21900  9 iptable_nat,nf_nat
nf_conntrack           72032  9 ipt_MASQUERADE,xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
b44                    35984  0 
iptable_mangle         10880  0 
snd_seq                57776  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mii                    13440  1 b44
uvcvideo               63624  0 
iptable_filter         10752  1 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
compat_ioctl32          9344  1 uvcvideo
ip_tables              19600  3 iptable_nat,iptable_mangle,iptable_filter
ssb                    40580  1 b44
joydev                 18368  0 
sdhci_pci              15360  0 
snd                    63268  16 snd_hda_intel,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
x_tables               22916  11 ipt_MASQUERADE,xt_DSCP,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_state,ipt_addrtype,ip6_tables,iptable_nat,ip_tables
sdhci                  23940  1 sdhci_pci
videodev               41344  1 uvcvideo
intel_agp              33980  0 
fglrx                2083204  31 
serio_raw              13444  0 
video                  25488  0 
soundcore              15328  1 snd
ndiswrapper           196380  0 
mmc_core               58268  1 sdhci
agpgart                42184  2 intel_agp,fglrx
v4l1_compat            22404  2 uvcvideo,videodev
dcdbas                 15008  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
output                 11008  1 video
psmouse                45200  0 
pcspkr                 10624  0 
ac                     12292  0 
wmi                    14504  0 
battery                18436  0 
button                 14224  0 
evdev                  17696  14 
ext3                  133512  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sg                     39732  0 
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
usbhid                 35712  0 
hid                    50560  1 usbhid
ahci                   37132  2 
ohci1394               37936  0 
libata                177952  1 ahci
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  5 sbp2,sg,sd_mod,sr_mod,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
tg3                   129924  0 
libphy                 27520  1 tg3
uhci_hcd               30864  0 
usbcore               149488  6 uvcvideo,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  3 thermal
fan                    12548  0 
fuse                   60956  3 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
mark@mark-laptop:~$

---

### Post by kevdog on 2009-06-13
Ok, a couple of possible conflicting things

I noticed you have a Broadcom wireless and wired card.  The wired card is the b44 driver.  I assume you want to run the wireless with the STA/wl driver?  I see ndiswrapper listed under the loaded modules.  Is this what you want?

Can you tell me your kernel version
uname -r

---

### Post by scrypt on 2009-06-13
Hi Kev..

that is correct Imjust want to use the default wireless driver I had when i first updated ubuntu-distribution

uname -r: 2.6.27-14-generic

---

### Post by scrypt on 2009-06-13
What do you suggest I do next.

---

### Post by scrypt on 2009-06-13
What' happened to helping begginers out??.

---

### Post by scrypt on 2009-06-13
bump

---

### Post by scrypt on 2009-06-13
If Nobaody can help me with this.

Can someone at least point me to where I might be able to fix it myself.

I think I have exhausted all my directions

---

### Post by synapsys on 2009-06-13
I think the first thing you should do is remove ndiswrapper. It's a really bad idea to have two wireless drivers running on one system at a time. You should be able to get your card working with the bw43-fwcutter. When you installed fwcutter did you choose to download drivers? 

Sorry if this was in an earlier post..... reading them made my brain hurt.

---

### Post by scrypt on 2009-06-13
Hey synapsys.

Okay I'll remove ndiswrapper.

and yes if I remember correctly I did choose to download driver when I installed bw43-fwcutter.

Was that the right decision??

Also, you know how you said reaading the earlier posts made you brain hurt (Ha Ha) Do you suggest I try and explain myself a little better??

Thank's for taking the time to help a begginer!!

---

### Post by Ayuthia on 2009-06-13
Can you try the following from the Terminal and see if you can connect:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```
This hopefully will bring up your wireless card.  If it does produce wireless sites, then the Broadcom STA module is working.  

Kevdog was close about the Broadcom wired card.  Your card is a 5xxx series instead of the 44xx series so your wired card uses the tg3 module instead of the b44.  

If this does work, we will need to blacklist the b43, ssb, and ndiswrapper modules:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ndiswrapper | sudo tee -a /etc/modprobe.d/blacklist.conf
```
This will help prevent the conflicting wireless modules from loading.

You can then reboot and see if it connects.  If it does not, try:
```
echo wl | sudo tee -a /etc/modules
```
That will have the wl module load up when the system starts up.

---

### Post by synapsys on 2009-06-13
Yes... correct to download driver

No..... you're doing fine.... it's just that my brain hurts.....

I've been fixing computers all day (job) no brain power left for reading.....

---

### Post by scrypt on 2009-06-13
you are spot on with these commands bringing up my WLAN card::

sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan

But it seems as though the original problem I was having has re-accured!

the problem is :
 I can connect wirelessly for about 30, seconds 
then I loose wireless connection for a short time. 

and then completely loose wireless connectivity altogether!!

This was the original problem I had that got me into a right mess with my card!!!

---

### Post by Ayuthia on 2009-06-13
I have a 4328 card that does something similar using wicd, but it works fine if I use the manual way to connect.  How far away are you from the router?  I find that it seems to work fine if I have a Quality of 4/5 or 5/5 when checking with sudo iwlist scan.

It has been a while since I have tried out the Gnome version of NetworkManager in Ubuntu (I usually use Kubuntu).  The Kubuntu version seems to work well with my card.

If you want to try ndiswrapper, you can try the following and see if it works:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
sudo iwlist scan
```
Ndiswrapper is a little more tricky.  It sometimes uses eth1 or wlan0.  Also the Windows driver has to be correct or else it will not work.  If this does not produce any wireless sites, can you post the results of:
```
dmesg|grep ndis
```

---

### Post by Ayuthia on 2009-06-13
By the way, if you want to try the manual method, you can try kevdog's guide on how to connect manually:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by scrypt on 2009-06-13
Hi Ayuthia.

To be honest I am not really sure what to do.

I have just had some posts by synapsys and his commands managed to get my wireless card back up.

But I still have the original issue, where I get wireless for about 30 seconds and then loose it all together.

I just want to have the original default driver etc. that seemed to work fine.

here is my output from your 'dmesg|grep ndis' command

ark@mark-laptop:~$ dmesg|grep ndis
[   14.965469] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.966303] usbcore: registered new interface driver ndiswrapper


ALSO if I go to system-Administration-Hardware Drivers. if I click on the activate the wireless STA Driver NOTHING happens.

I am not sure what to do next.
can you help??

---

### Post by synapsys on 2009-06-13
> **scrypt said:**
> Hi Ayuthia.
I just want to have the original default driver etc. that seemed to work fine.


Do you know what the original driver was that worked? Also can you post the contents of your /etc/modprobe.d/ folder?

```
ls /etc/modprobe.d/
```

Also what wireless encryption are you using if any?

---

### Post by scrypt on 2009-06-13
I am pretty sure it was the 'wl' driver, as default wireless driver!!

Here is the 'ls /etc/modprobe.d/' Output:-   

mark@mark-laptop:~$ ls /etc/modprobe.d/
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  dkms.conf
blacklist-bcm43.conf    blacklist-modem.conf        libpisock9.conf
blacklist.conf          blacklist-oss.conf          ndiswrapper.conf

---

### Post by scrypt on 2009-06-13
mark@mark-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:70:48:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11

---

### Post by synapsys on 2009-06-13
How hard would it be for you to re-install? Do you have your data backed up?

---

### Post by Ayuthia on 2009-06-13
The original driver is the Broadcom STA module which you seem to be able to use again based on the info in [post #28]("http://ubuntuforums.org/showpost.php?p=7452621&postcount=28").  If that is what you want, you can use the info in post #28 to make it use it again.  You will need to blacklist the b43, ssb, and ndiswrapper module.  It might also need to have the wl module added to /etc/modules so that the module will load when you start up.

My guess is that NetworkManager had an update that is causing the issues with disconnecting and reconnecting.  I have not had an opportunity to see what is causing that issue.  You might try using the manual process to see if it will connect.  You might need to turn off NetworkManager.  I am not for sure about how to turn off NetworkManager anymore.   The easiest way is to kill the process.  If you are not using any encryption on your router, please post the results of:
```
ps -ef|grep Network
```and I might be able to guide you on how to connect manually.

---

### Post by synapsys on 2009-06-13
I see you've tried loading only wl and ndiswrapper.... but have you tried only loading b43?

```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by scrypt on 2009-06-13
Hi Ayuthia here is the output.

I do use encryption, cuz I live in A big block of flats. so I need it. alot of wireless routers in close proximity.

mark@mark-laptop:~$ ps -ef|grep Network
root      6115     1  0 02:08 ?        00:00:01 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      6130     1  0 02:08 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      9165  6115  0 02:21 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
mark     10264  9492  0 02:31 pts/0    00:00:00 grep Network

---

### Post by scrypt on 2009-06-13
It's 2:40am and i starting to loose the will. :)

Synapsys: I reckon A reinstallation is sounding Good.

If I don't get this fixed by tommorow that is just what I will do.

I just Do not want to let it beat me

---

### Post by scrypt on 2009-06-13
I used the commands in post ~28 and it did get my wlan card back up.

but it still only lets me connect for about 30 seconds and then I loose w/connectivity.

plz keep in mind im newish

---

### Post by Ayuthia on 2009-06-13
> **scrypt said:**
> Hi Ayuthia here is the output.

I do use encryption, cuz I live in A big block of flats. so I need it. alot of wireless routers in close proximity.

mark@mark-laptop:~$ ps -ef|grep Network
root      6115     1  0 02:08 ?        00:00:01 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      6130     1  0 02:08 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      9165  6115  0 02:21 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
mark     10264  9492  0 02:31 pts/0    00:00:00 grep Network

To kill the process in this example you can kill the process id of 6115 (see the first line of your ps -ef results).  That should stop Network Manager.  However, if you are using WPA, I am not for sure if I can help you too much because I don't use WPA enough to remember how to use it (however, kevdog's guide does provide some good examples on how to do it).

---

### Post by Ayuthia on 2009-06-13
> **synapsys said:**
> I see you've tried loading only wl and ndiswrapper.... but have you tried only loading b43?

```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

The b43 module does not support the 4312 card (the 14e4:4315 version) at this time.

---

### Post by synapsys on 2009-06-13
Well then I guess b43 is a terrible name for it then....lol 

So maybe bcm43xxx?

---

### Post by scrypt on 2009-06-13
Well that just says it all doesn't it....

---

### Post by scrypt on 2009-06-13
what is the best procedure for me to undertake then to correct this if trying to install the b43 is not possible???

---

### Post by keplerspeed on 2009-06-13
Scrypt, if you boot from live cd does it work fine??

I have installed 9.04 on a machine with a BCM4312 and it worked fine out of the box with the restricted Broadcom driver.

---

### Post by synapsys on 2009-06-13
I sense a re-install in your future

---

### Post by keplerspeed on 2009-06-13
Well, before doing a reinstall, try from a livecd. May be able to salvage your current install.

---

### Post by kevdog on 2009-06-13
Jumping to a full reinstall is utterly pointless.  When you lose connectivity, have you checked the system logs?  Does dmesg give you any hint?  Have you tried to make a manual connection so at least you get some debugging output in the terminal that might give you a clue what is going on?  Have you at this point turned off all encryption at the router to simplify the process and not add insult to injury?  Everytime you tell us that wl is not working after 30 seconds or whatever interval, give us something to work with other than the proverbial "its not working!".  We can not see your computer or play with your hardware.  Its your job to describe your situation as best as you can since I'm really "blind" to your exact problem.  You've done a good job up to now, but we need more information.

---

### Post by scrypt on 2009-06-13
ill post back tommorow

---

### Post by scrypt on 2009-06-13
I really do not want to let this beat me...

---

### Post by scrypt on 2009-06-13
Hopefully you can give me a hand later on. and ill try to post more concise error reports.

I get your point about being a bit vague with my problem...

I'll fully review this thread later on and try to post more definitive output..

Thank's for now

scrypt

---

### Post by keplerspeed on 2009-06-14
Scrypt, your OP outlines that you can connect using wireless but it drops out after 30 seconds. I have set up 9.04 with a BCM4312, with the restricted driver, and had no trouble with this card.

Therefore, can you do 2 things:

1)boot with a live cd (no need to reinstall!), install the restricted driver and try to connect to the same network. Report back with the results.

2)try to connect to a different wireless network. Be that a friends or something, to eliminate that fact that it could be a network issue.

I an skeptical that your wireless card itself is not setup right, as it is supported well by the restricted driver. I assume for now that you have an issue with your router.

---

### Post by keplerspeed on 2009-06-14
And to further what kevdog has said, we need more information.

System log files are located in /var/log/

For example, it would help to try to connect (then drops out after 30 secs) and then view the file /var/log/dmesg and see if anything pokes out, letting us know WHY it dropped out.

Kevdog, I think some people are lost when debugging. I have only just begun to understand some good methods to debug an issue. I know, that maybe a year ago, I wouldnt have even though to check a logfile. I woudnt have even know what dmesg is.

(NOTE: dmesg is just a kernel message displayer. Display MESsaGe.)

---

### Post by scrypt on 2009-06-14
Hi Mate.

would /var/log be the same as going to system/administration/system log files??

if it is not how do I open /var/log??

---

### Post by scrypt on 2009-06-14
Does this mean anything from systm logfiles - Debug - last two lines of Debug say :-

Jun 14 22:56:00 mark-laptop kernel: [   38.452050] eth1: no IPv6 routers present
Jun 14 22:56:03 mark-laptop kernel: [   41.372132] eth0: no IPv6 routers present

---

### Post by scrypt on 2009-06-14
Kaplerspeed. I think you are right about my wlan card. it wasworking fine up untill i tried to install the b43 driver which I know find is not supported for my card.

Can you tell me how to install the default driver from the live cd.

I am intrested in learnin how!!

---

### Post by scrypt on 2009-06-14
Okay I will boot into live cd and post back if I can connect successfully wirelessly.

I'll post back from the live cd conection!!

---

### Post by scrypt on 2009-06-14
I am connected wirelessly right now using the live-cd with NO problems whatsoever.

It seems there is some thing wrong with my wireless configurations or the driver because you are right about the problem not being wth my wlan card

---

### Post by keplerspeed on 2009-06-14
OK so it appears that it is a configuration issue.

While in the live cd, did you install the driver via system>administration>hardware drivers? Was this the STA or b43 broadcom driver?

Atleast we know that it is a configuration issue. So going back to you normal installation, remove all ndiswrapper etc. Put all files (such as blacklist.conf or whatever else was edited) back to default (hope you backed them up!! make your life easier!) and then install driver from system>admin>hardware drivers.

If your desparate, and cant get everything back, a reinstall should work, as it will be the same as the livecd. However, this wont teach you anything, so try to fix this first.

---

### Post by scrypt on 2009-06-14
Hi keplerspeed.

I think i might now know what the problem might be.

I ran lshw -c network whilst in the live cd and the wireless driver that worked good was: wl

I just booted back into my normal ubuntu environment and ran lshw -c network and the driver in use now is:- wl0

How can i cjange it from wl0  to wl ??

---

### Post by scrypt on 2009-06-14
I did try the system-administration-hardware drivers

and ran lshw -c network and it stated that the driver was still:- wl

I would rather try and fix it than reinstall

---

### Post by scrypt on 2009-06-14
I have removed all ndiswrapper and NO i did not back up the blacklist.conf files (lesson duelly learn't)

---

### Post by keplerspeed on 2009-06-14
Ok so you have the correct driver. IF you installed it via hardware-drivers then thats ok.

Go to your normal install:

Now delete the network that is saved in network manager. So right click on network icon, edit connections. Go to wireless and delete your network saved there.

Reconnect the same way as you did in the live cd.

---

### Post by scrypt on 2009-06-14
I cannot install the driver through system-administartor-hardware drivers

i click activate and NOTHINg happens!!!

I also just used 'sudo nautilus /etc/modprobe.d/' is this the right command i should use to change all blacklist.conf to blacklist??

there are about 9 files in there and not all of them are just named blacklist.conf.

should I just delete .conf from all files or just the blacklist.conf??

---

### Post by keplerspeed on 2009-06-14
heehe.. ok

This is getting messy. My suggestion:

Write down what files you edited. Such as blackist.conf etc.

Then boot live cd, and copy those files to usb. Then replace the ones in your install with the ones copied from live cd.

REMEMBER to backup any changes on your install. So befoe replacing blackist.conf, copy it to blacklist.conf.bak or something.

---

### Post by scrypt on 2009-06-14
Sorry Keplerspeed Im lost. Im not sue what you mean or what to do next concerning the .conf files

---

### Post by keplerspeed on 2009-06-14
In hardware-drivers, when selecting the wl driver, is there a note down the botton:

Grey dot:"this driver is not activated"

and also:

Green dot: "Activate"

Is this what you see??

---

### Post by scrypt on 2009-06-14
what is the command to get into the blacklist.conf file??

---

### Post by scrypt on 2009-06-14
Yes there is a grey dot that says driver NOT activated

---

### Post by scrypt on 2009-06-14
keplerspeed

Im going to admit defeat  and just reinstall.

---

### Post by keplerspeed on 2009-06-14
Pretty much, a default system works: ie the live cd.

However, you have edited config files, changed/removed drivers etc.

So we need to get you back to the standard configuration: hence copying files from live cd.

To edit blacklist.conf:

```

sudo gedit /etc/modprobe.d/blacklist.conf

```

I am unsure as to how to install the wl driver now. Possibly cant install if it is blacklisted. Please paste your blacklist.conf file here.

Lesson learnt: backup files.

---

### Post by scrypt on 2009-06-14
here is the output:=

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist wl
blacklist b43
blacklist bcm43xx
blacklist wl
blacklist wl
blacklist bcm43xx
blacklist bcm43xx
blacklist wl
blacklist b43
blacklist b43
blacklist b43
blacklist b43
blacklist b43

---

### Post by scrypt on 2009-06-14
can you clarify what modprobe.d and blacklist actually mean, I think I know but can you define it for me??

---

### Post by keplerspeed on 2009-06-14
That would be your problem. edit the end of the file to look like this:

```

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by scrypt on 2009-06-14
So let me get this right. I use 'sudo gedit /etc/modprobe.d/blacklist.conf'

in live cd and just copy all in that page to sudo gedit /etc/modprobe.d/blacklist.conf in my normal ubuntu instalation is this correct??


Also how do you get the box around a command when you post??

---

### Post by keplerspeed on 2009-06-14
Then reboot and try to install the driver in hardware-drivers.

blacklist: list of modules + drivers NOT to be loaded at boot.
Modprobe: utility to remove or add modules (or drivers) to the kernel

---

### Post by scrypt on 2009-06-14
So just delete all the junk at the bottom of sudo gedit /etc/modprobe.d/blacklist.conf???

---

### Post by keplerspeed on 2009-06-14
EITHER:
1)edit the file in your install as I have shown
2)copy bllacklist.conf from livecd and replace the one in install

Do 1 though, it will be faster. So:

```

sudo gedit /etc/modprobe.d/blacklist.conf

```

And remove the stuff at the bottom as I have explained.

NOTE:
use the [ CODE ] tags
[ / CODE ] for commands or code.

---

### Post by keplerspeed on 2009-06-14
Yes exactly. delete the junk, then reboot. Then try hardware-drivers.

---

### Post by keplerspeed on 2009-06-14
For more info on modprobe or blacklist see here [http://en.wikipedia.org/wiki/Modprobe](http://en.wikipedia.org/wiki/Modprobe)

Blacklist section is halfway down the page.

---

### Post by scrypt on 2009-06-14
okay i did as you said a rebooted tried to activate that STA driver again and nothing happened.

i also ran [lshw -c network] to see what wireless driver had loaded at bootup
and it states it is still loadin the wl0 driver??

mark@mark-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:70:48:b4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11

---

### Post by scrypt on 2009-06-14
[/lshw -c network]

---

### Post by keplerspeed on 2009-06-14
In that case, I am unsure as to why we cant enable the STA driver.

What other files did you edit?

---

### Post by scrypt on 2009-06-14
I just tried something on the off chance.

i just wen to synaptics and oaded the b43-fcutter and extracted the firmware and rebooted and my wireless connetivity seems stable and I have stayed connected.

it seems to have worked this time around after we cleaned all the junk out of the blacklist.conf files.

I still cannot activate the driver through hardware drivers though. but at least I have a stable wirless connection now

---

### Post by scrypt on 2009-06-14
Forget my last post wireless just disconnected again.

Do you think I should reinstall ubuntu and amit defeat??

---

### Post by kevdog on 2009-06-14
Lets see what drivers you have loaded

Please list
lsmod

Also lets see a few things:
sudo updatedb
locate wl
locate wl0
modinfo wl
modinfo wl0

According to the b43 website 4312 is supported by b43
Also the STA driver seems to support 4312 as well.

This is also a good reference although it doesnt address jaunty specifically:
[http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61](http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=46:broadcom-guide-for-ubuntu-hardy-and-newer&catid=34:guides&Itemid=61)

---

### Post by Ayuthia on 2009-06-14
The 14e4:4315 chipset is still not supported by b43 yet.  They finished up the reverse-engineering for it but have not started coding it yet.

Can you post the results of:
```
dmesg | grep wl
```
It might help us see why it is disconnecting.  Also, how far away are you from the router when it gets disconnected?  Which encryption are you currently using (WEP/WPA/WPA2)?

I don't think that it really is going to help if you reinstall Ubuntu.  My thoughts is that NetworkManager is thinking that it lost the signal and is trying to reconnect.  The results of dmesg could help us confirm this.

---

### Post by scrypt on 2009-10-08
hi guys

its been a while but im having trouble again with this issue can anyone help me out

---

### Post by hantechbl on 2009-10-08
All of my wifi cards 3 of them see networks but drop the connection.  I think the chips get overused and causes something to happen in the card.  (my cards were 2 2wire cards and a linksys card)  This has happened to me in all OSes.  My recommendation to you check your  bios and make sure the card is enabled if that doesn't work buy a new card (check compatibility and reviews).

---

