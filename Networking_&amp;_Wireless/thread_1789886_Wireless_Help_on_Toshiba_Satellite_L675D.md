---
title: "Wireless Help on Toshiba Satellite L675D"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by jskinner1724 on 2011-06-24
Please forgive  if I have mis-posted or failed to follow forum etiquette. I searched  and found no other adequate place for such a post.

Please help! At my wits end (which didn't take long btw) trying to  figure this one out. After the 2.6.32-32 kernel upgrade my wireless  stopped working. No big deal, just boot to the older kernel version,  right? Well, after going through the forums, I tried everything I could  find to upgrade the drivers, etc. to no avail. Now I am left with a  system that will not recognize my wireless card. Here are some of the  results of scans I assume you will ask for;

jskinner1724@jskinner1724-laptop:~$ sudo -i
[sudo] password for jskinner1724: 
root@jskinner1724-laptop:~#**[COLOR=SeaGreen] lshw -C network[/COLOR]**
 _ *-network UNCLAIMED  _   
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:d000(size=256) memory:ff600000-ff603fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:5a:eb:87
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.1.55 latency=0 link=yes  multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:c000(size=256) memory:d0104000-d0104fff(prefetchable) memory:d0100000-d0103fff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
(This is my virtual machine which I expect to be disabled)

root@jskinner1724-laptop:~# **[COLOR=SeaGreen]lspci -n[/COLOR]**
00:00.0 0600: 1022:9601
00:01.0 0604: 1179:9602
00:06.0 0604: 1022:9606
00:07.0 0604: 1022:9607
00:11.0 0106: 1002:4391
00:12.0 0c03: 1002:4397
00:12.2 0c03: 1002:4396
00:13.0 0c03: 1002:4397
00:13.2 0c03: 1002:4396
00:14.0 0c05: 1002:4385 (rev 41)
00:14.2 0403: 1002:4383 (rev 40)
00:14.3 0601: 1002:439d (rev 40)
00:14.4 0604: 1002:4384 (rev 40)
00:18.0 0600: 1022:1200
00:18.1 0600: 1022:1201
00:18.2 0600: 1022:1202
00:18.3 0600: 1022:1203
00:18.4 0600: 1022:1204
01:05.0 0300: 1002:9712
01:05.1 0403: 1002:970f
_02:00.0 0280: 10ec:8176 (rev 01)_
03:00.0 0200: 10ec:8136 (rev 05)

root@jskinner1724-laptop:~#**[COLOR=SeaGreen] lsmod[/COLOR]**
Module                  Size  Used by
binfmt_misc             7960  1 
vboxnetadp              5171  0 
vboxnetflt             14998  0 
vboxdrv              1792504  2 vboxnetadp,vboxnetflt
iptable_filter          1841  0 
ip_tables              18201  1 iptable_filter
x_tables               22361  1 ip_tables
ppdev                   6375  0 
parport_pc             29958  0 
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_realtek   279008  1 
snd_seq_dummy           1782  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hd  a_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_seq_oss            31191  0 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid  i_event
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi  ,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
fglrx                2353486  32 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd_timer              23649  2 snd_pcm,snd_seq
joydev                 11104  0 
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
psmouse                64576  0 
ndiswrapper           244800  0 
serio_raw               4918  0 
snd                    71283  16  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,   snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,sn   d_pcm,snd_rawmidi,snd_seq,snd_seq_device,snd_timer
edac_core              45423  0 
i2c_piix4               9639  0 
shpchp                 33711  0 
edac_mce_amd            9278  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
raid10                 21450  0 
raid456                54784  0 
async_pq                3891  1 raid456
async_xor               3111  2 raid456,async_pq
xor                     4685  1 async_xor
async_memcpy            1537  1 raid456
async_raid6_recov       1816  1 raid456
usb_storage            50377  0 
raid6_pq               80147  2 async_pq,async_raid6_recov
async_tx                2545  5 raid456,async_pq,async_xor,async_memcpy,async_raid  6_recov
raid1                  22610  0 
usbhid                 41116  0 
hid                    83600  1 usbhid
raid0                   6778  0 
multipath               7181  0 
linear                  4158  0 
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38030  2

root@jskinner1724-laptop:~#**[COLOR=SeaGreen] iwconfig[/COLOR]**
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

Normally, my machine had seen my wireless as wlan0, but as you can tell  from above, it seems to have gotten lost somehow after the upgrade. I  tried the rtl8192ce-dkms for Lucid since I am running 10.04, followed  the instructions precisely, rebooted and found myself no further than  before I started. This laptop is critical to my work and the non-working wireless is seriously affecting it's use. Any suggestions?

---

### Post by chili555 on 2011-06-24
> I tried the rtl8192ce-dkms for Lucid since I am running 10.04, followed the instructions precisely, rebooted and found myself no further than before I started. However, rtl8192ce, which is correct for your device, is not loaded in *lsmod* and ndiswrapper is. Let's work with what we know we have before we start surgery. I wonder why ndiswrapper is not doing the job. Please post:```
iwconfig
dmesg | grep ndis
ndiswrapper -l
```The last character is a lower-case L, not a one. Thanks.

---

### Post by jskinner1724 on 2011-06-24
Thanks for the help chili. Here are the results of the commands:

root@jskinner1724-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

root@jskinner1724-laptop:~# dmesg | grep ndis
[   17.633871] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   18.230423] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192ce; check system log for messages from 'loadndisdriver'
[   18.230632] usbcore: registered new interface driver ndiswrapper

root@jskinner1724-laptop:~# ndiswrapper -l
net8192ce : invalid driver!
net8192se : invalid driver!

---

### Post by chili555 on 2011-06-24
I feel a migraine coming on...I just went through this with another poster and the news was not good. Let's endeavor to persevere. Please look at:```
sudo cat /var/log/syslog | grep ndis
```When you read all the lines about unknown symbol, then we can dismiss ndiswrapper as a possibility. Next, let's do:```
sudo rmmod -f ndiswrapper
sudo modprobe rtl8192ce
```Post any errors or warnings; they will be informative.

I am going for a few dozen aspirin.> ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'_aulldvrm'Is that about it??

---

### Post by jskinner1724 on 2011-06-24
root@jskinner1724-laptop:~# cat /var/log/syslog | grep ndis
root@jskinner1724-laptop:~# rmmod -f ndiswrapper
root@jskinner1724-laptop:~# modprobe rtl8192ce
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rtl8192ce not found.

Sorry for your headache, I really do appreciate the help.

---

### Post by jskinner1724 on 2011-06-24
sorry, I typed quicker than my brain moved and then seen there was no return from the first two commands. Here's the full results (brain included this time):

root@jskinner1724-laptop:~# cat /var/log/syslog | grep ndis
Jun 24 13:10:58 jskinner1724-laptop kernel: [33188.460421] usbcore: deregistering interface driver ndiswrapper
root@jskinner1724-laptop:~# rmmod -f ndiswrapper
ERROR: Removing 'ndiswrapper': No such file or directory
root@jskinner1724-laptop:~# modprobe rtl8192ce
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rtl8192ce not found.

---

### Post by chili555 on 2011-06-24
> FATAL: Module rtl8192ce not found.I wonder if the rtl8192ce build process went well:> I tried the rtl8192ce-dkms for Lucid since I am running 10.04, followed the instructions precisely, rebooted and found myself no further than before I started. Do you still have the files on your computer somewhere? What tutorial did you follow? Do you have a link?

---

### Post by jskinner1724 on 2011-06-24
I do. The link is:
[http://ubuntuforums.org/archive/index.php/t-1641786.html](http://ubuntuforums.org/archive/index.php/t-1641786.html)

The post is:
canuckedDecember 9th, 2010, 08:09 PM
I just created a thread about a laptop I configured which used the Realtek RTL8188CE wireless adapter.

[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Most solutions I found involved compiling the Realtek driver, downloaded  from Realtek's website.  However, this would have to be done each time a  new kernel is installed.

Fortunately, someone has created a PPA which automagically installs the  Realtek driver when a new kernel is installed.  (Since you are new to  Ubuntu, I would suggest reading about PPAs, and understand that they are  not officially supported by Canonical.)

To install support for the Realtek RTL8188CE, run the following in Terminal:
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

Note that the RTL8192CE driver is installed.  Reboot, and see if wireless now works!

I hope this works for you!

---

### Post by jskinner1724 on 2011-06-24
I did notice that following the reboot after install, there was still no wireless card recognized in a lshw -C network command.

It almost seems as if the ndiswrapper did not install fully, at least if it did, the kernel would not use it. Do you think it would be possible to reinstall ndiswrapper and then force the rtl8192ce driver since it is the correct driver? I understand that the wrong driver can cause physical damage to the wifi card, but this is the driver Realtek put out.

---

### Post by chili555 on 2011-06-24
> sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkmsWould you please try each of these commands in order and copy and paste the terminal output to a text document so you can post it here? I am wondering what went wrong.> I understand that the wrong driver can cause physical damage to the wifi card, I have never seen this. That doesn't mean it hasn't happened but a gazillion posts and I've never seen it. Now, I think it's possible to install a driver that simply doesn't work or one that causes a freeze or kernel panic, but it is fairly easy to uninstall or blacklist. > Do you think it would be possible to reinstall ndiswrapper and then force the rtl8192ce driver since it is the correct driver?They are two different processes that are mutually exclusive; either use ndiswrapper and the Windows XP driver...

OR...

Use the Linux native driver rtl8192ce.

You can't graft the two together.

---

### Post by jskinner1724 on 2011-06-24
Here is the text file you requested. And I understand your post about the two different applications of the wireless driver now.

---

### Post by chili555 on 2011-06-24
Everything looks solid. Let's try again. If the ndis parts errors out, that's OK:```
sudo rmmod -f ndiswrapper
sudo modprobe rtl8192ce-dkms
dmesg | grep 819
```I am off to nap, see you tomorrow.

---

### Post by jskinner1724 on 2011-06-24
Here is the results:

root@jskinner1724-laptop:~# rmmod -f ndiswrapper
ERROR: Removing 'ndiswrapper': No such file or directory

root@jskinner1724-laptop:~# modprobe rtl8192ce-dkms
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rtl8192ce_dkms not found.

root@jskinner1724-laptop:~# dmesg grep | 819
819: command not found

Am I wrong or should there not have been at least the slightest mention in the kernel buffer about the 8192 driver?

I am very grateful for your help today. I will try to post as frequently as possible tomorrow.

---

### Post by chili555 on 2011-06-25
> # modprobe rtl8192ce-dkms
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module rtl8192ce_dkms not found.It seems that if you installed it and it's the latest version, it must have some name!!! Let's look for it:```
sudo updatedb
locate 819 | grep .ko
```> # dmesg grep | 819
819: command not foundYou have the pipe in the wrong place. It's:```
dmesg | grep 819
```Certainly, unless it's blacklisted, some kind of 8192ce module ought to be loading. Let's check:```
cat /etc/modprobe.d/blacklist.conf | grep 819
```Also, it is a security compromise to be running as root #, you naughty linuxian!

---

### Post by jskinner1724 on 2011-06-25
> **chili555 said:**
> It seems that if you installed it and it's the latest version, it must have some name!!! Let's look for it:

root@jskinner1724-laptop:~# updatedb
locate 819 | grep .ko
root@jskinner1724-laptop:~# locate 819 | grep .ko
/home/jskinner1724/.local/share/Trash/files/rtl8188ce/driver/rtl8188ce/.8192cu.ko.cmd
/home/jskinner1724/.local/share/Trash/files/rtl8188ce/driver/rtl8188ce/8192cu.ko
/home/jskinner1724/.local/share/Trash/files/rtl8192se/HAL/rtl8192/.r8192se_pci.ko.cmd
/home/jskinner1724/.local/share/Trash/files/rtl8192se/HAL/rtl8192/r8192se_pci.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/media/video/bt819.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-25-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-28-generic/kernel/drivers/media/video/bt819.ko
/lib/modules/2.6.32-28-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-28-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-28-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-29-generic/kernel/drivers/media/video/bt819.ko
/lib/modules/2.6.32-29-generic/kernel/drivers/net/wireless/8192cu.ko
/lib/modules/2.6.32-29-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-29-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-29-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-30-generic/kernel/drivers/media/video/bt819.ko
/lib/modules/2.6.32-30-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-30-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-30-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/media/video/bt819.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-31-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-31-generic/kernel/ubuntu/rtl8192se/r8192se_pci.ko
/lib/modules/2.6.32-32-generic/kernel/drivers/media/video/bt819.ko
/lib/modules/2.6.32-32-generic/kernel/drivers/net/wireless/r8192se_pci.ko
/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rtl8192e/r8192_pci.ko
/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
/lib/modules/2.6.32-32-generic/updates/dkms/r8192ce_pci.ko
/var/lib/dkms/rtl8192ce/2.6.0003.0628.2010ubuntu1/2.6.32-32-generic/x86_64/module/r8192ce_pci.ko

> You have the pipe in the wrong place. 
Like I said, my fingers move faster than my brain.

> Certainly, unless it's blacklisted, some kind of 8192ce module ought to be loading. Let's check:```
cat /etc/modprobe.d/blacklist.conf | grep 819
```
There was no return for this command.

> Also, it is a security compromise to be running as root #, you naughty linuxian!
I know, I can;t help myself though. Since this is my personal laptop that I occasionally use at work (more and more frequently), and it is the only linux box in the shop, there isn't much of a risk. Besides, the guys I work with aren't exactly fluent in penguin.

---

### Post by chili555 on 2011-06-25
> /lib/modules/2.6.32-32-generic/updates/dkms/[COLOR="Red"]r8192ce_pci[/COLOR].koThat's it, I expect. Let's try again:```
sudo rmmod -f ndiswrapper
sudo modprobe r8192ce_pci
iwconfig
modinfo r8192ce_pci | grep 8176
```Any errors, warnings, sparks, smoke, etc. will be informative.> it is the only linux box in the shop, there isn't much of a riskI recommend you be careful what you click on line; be very, very cautious about stray USB keys and CDs; then wean yourself off of root. There is probably a 12-step for that. I'm a recovering root myself.

---

### Post by jskinner1724 on 2011-06-25
> I recommend you be careful what you click on line; be very, very cautious about stray USB keys and CDs; then wean yourself off of root. There is probably a 12-step for that. I'm a recovering root myself.I only use it for hard drive forensics and I use the virtual box for web dev stuff. But the heads up is appreciated. I have a Debian box here at home that I use as an internet server. 

root@jskinner1724-laptop:~# logout
jskinner1724@jskinner1724-laptop:~$ sudo rmmod -f ndiswrapper
[sudo] password for jskinner1724: 
ERROR: Removing 'ndiswrapper': No such file or directory
jskinner1724@jskinner1724-laptop:~$ sudo modprobe r8192ce_pci
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
jskinner1724@jskinner1724-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

wlan0     802.11bg  ESSID:"Skinner"  Nickname:"rtl8192CE"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:17:3F:45:E2:86   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=0 dBm  Noise level=-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jskinner1724@jskinner1724-laptop:~$ modinfo r8192ce_pci | grep 8176
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*

My wireless is back up, but upon reboot, it reverted. I had to remove the ndiswrapper and modprobe the r8192ce driver again to get it to work. Again, I could be wrong, but those settings should have stuck but didn't.

---

### Post by chili555 on 2011-06-26
> My wireless is back up,Woo hoo!!!> but upon reboot, it reverted.Let's fix it.```
sudo su
rm -rf /etc/ndiswrapper/*
rm /etc/modprobe.d/ndiswrapper
echo r8192ce_pci >> /etc/modules
exit
```How about now?

---

### Post by jskinner1724 on 2011-06-27
I think that was the ticket! It is back up and running now. Thank you for your help chili.

---

