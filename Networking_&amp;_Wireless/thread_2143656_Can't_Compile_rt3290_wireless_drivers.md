---
title: "Can't Compile rt3290 wireless drivers"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by theperfectpunk on 2013-05-09
whenever i try to compile my rt3290 wireless drivers using this guide : [http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

I get the following error : 

[http://pastebin.com/ei67W7HD](http://pastebin.com/ei67W7HD)

Edit : Since it has been more than 9 hours, have i posted the question in the wrong section?

---

### Post by theperfectpunk on 2013-05-10
*bump

---

### Post by varunendra on 2013-05-10
> **theperfectpunk said:**
> Edit : Since it has been more than 9 hours, have i posted the question in the wrong section?

This is the perfect section for the problem. For the record, please post the following outputs :

```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
lsmod
dpkg --get-selections | grep -e build-essential -e linux-headers-generic -e linux-headers-`uname -r`
```

Do you have a wired connection available on the laptop? So that we can use it to download above packages if not already installed.

**PS:**
Please use 'Code' tags to post the outputs. Follow the link in my signature to see how.

---

### Post by theperfectpunk on 2013-05-11
> **varunendra said:**
> This is the perfect section for the problem. For the record, please post the following outputs :

```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
lsmod
dpkg --get-selections | grep -e build-essential -e linux-headers-generic -e linux-headers-`uname -r`
```

Do you have a wired connection available on the laptop? So that we can use it to download above packages if not already installed.

**PS:**
Please use 'Code' tags to post the outputs. Follow the link in my signature to see how.

```

mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ lsb_release -d
Description:    Ubuntu 13.04
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ uname -mr
3.8.0-19-generic x86_64
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2800pci
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:184a]
    Kernel driver in use: r8169
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    89374  1 
crc_itu_t              12707  1 udf
fglrx                5294837  84 
amd_iommu_v2           19068  1 fglrx
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
vesafb                 13828  1 
joydev                 17377  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
hp_accel               26012  0 
snd_hda_codec_idt      70256  1 
lis3lv02d              20111  1 hp_accel
input_polldev          13896  1 lis3lv02d
video                  19390  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm                   443165  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
arc4                   12615  2 
ghash_clmulni_intel    13259  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
rt2800pci              18582  0 
aesni_intel            55399  1 
wmi                    19070  1 hp_wmi
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
rt2800lib              66507  1 rt2800pci
rt2x00pci              14519  1 rt2800pci
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               80847  0 
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
mac_hid                13205  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
videodev              129260  2 uvcvideo,videobuf2_core
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
cfg80211              510937  2 mac80211,rt2x00lib
k10temp                13126  0 
i2c_piix4              13266  0 
psmouse                95870  0 
serio_raw              13215  0 
soundcore              12680  1 snd
eeprom_93cx6           13344  1 rt2800pci
microcode              22881  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
crc_ccitt              12707  1 rt2800lib
rtsx_pci_sdmmc         17475  0 
r8169                  67446  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25731  3 
libahci                31364  1 ahci
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ dpkg --get-selections | grep -e build-essential -e linux-headers-generic -e linux-headers-`uname -r`
build-essential                    install
linux-headers-3.8.0-19-generic            install
linux-headers-generic                install

```

Yes i do have a wired connection

---

### Post by varunendra on 2013-05-11
> **theperfectpunk said:**
> ```
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    **Kernel driver in use: [COLOR="#FF0000"]rt2800pci[/COLOR]**
```

Everything looks good to me, even the native driver rt2800pci is loaded as expected. Isn't it working for you?

If not, then my first suggestion is to try installing 3.9xx kernel as suggested in the askubuntu answer you linked to ([http://askubuntu.com/a/253660](http://askubuntu.com/a/253660)) :
> It has been noted that in the 3.9 kernel version, the wireless card is working correctly, so in 13.04 with backports or 13.10 this issue should be resolved.

Or, if that does not work or if you wish to compile the proprietary driver anyway, I found a patch here that seems to work with it : [http://ubuntuforums.org/showthread.php?t=2138302&p=12628115#post12628115](http://ubuntuforums.org/showthread.php?t=2138302&p=12628115#post12628115)

This is what you have to do to compile the driver (tested on a live session of 13.04, 64 bit) :
[LIST=1]
[*]Download the driver from Ralink : [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5033](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5033) *(you have already done it)*
[*]Copy it to your desktop
[*]Rename it to add ".tar" before ".bz2" at the end (2012_0508_RT3290_Linux_STA_v2.6.0.0.tar.bz2)
[*]Right-click on the file > click "Extract here..". This will create a folder "DPO_RT3290_LinuxSTA_V2600_20120508" and extract the files in it.
[*]Download the attached zip file and extract the patch file from it (it is originally meant for rt5592sta, but also works with rt3290sta)
[*]Copy the patch file **into** the folder you just extracted the driver files in.
[*]Open the "config.mk" file (**os/linux/config.mk** in the extracted file)
[*]Edit line no. 31 ("HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR="#FF0000"]n[/COLOR]**"), and change its value from '**n**' to '**y**' ("HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=**[COLOR="#000080"]y[/COLOR]**")
[*]Also make sure that the value of line no. 26 is also '**y**' ("HAS_WPA_SUPPLICANT=**y**")
[*]Proofread, save and close the file.
[*]Now open a terminal (Ctrl+Alt+T), and run the following commands (one at a time > let it finish > run the next command....) :
[/LIST]
*(for long names, type a few initial characters, then press Tab key to auto-complete the rest of the name)*
```
cd ~/Desktop/DPO_RT3290_LinuxSTA_V2600_20120508
patch ./os/linux/pci_main_dev.c rt5592sta_fix_64bit_3.8.patch
```
The 'patch' command will give some errors, as the patch was originally meant for another driver. Just ignore the errors and proceed as follows (in the same terminal, same directory) -
```
make
sudo make install
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt3290sta
sudo update-initramfs -u
```
The 'make' command will return exactly 1 Error in the last regarding 'tftpboot'. That is normal and can be safely ignored. Watch out for any more errors in any of the commands. Post back if there are any.

To make sure there is no conflict between the native and the compiled drivers, blacklist the native rt2800pci driver -
```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```


**PS:**
Got this weird headache since last night, so I didn't take a thorough look at the patch file, although in a quick glance it looks fine. I may try to edit it later so that it doesn't give those errors while patching. Just let me know how well the driver performs, if you try it.

---

### Post by theperfectpunk on 2013-05-11
Ok thanks, the driver got installed and i restarted the computer but whenever i try to use use wifi, Ubuntu hangs.

Could you please provide a solution to this problem?

---

### Post by varunendra on 2013-05-11
> **theperfectpunk said:**
> Ok thanks, the driver got installed and i restarted the computer but whenever i try to use use wifi, Ubuntu hangs.

Could you please provide a solution to this problem?
Too bad! Does it resume after a while or totally hangs requiring you to force shutdown or reboot?

If it resumes, please post (after it resumes) :
```
dmesg | tail -40
cat /var/log/syslog | tail -40
```

On the other hand, if it hangs so badly that you need to force shutdown/reboot, please post (immediately after next reboot) -
```
cat /var/log/dmesg.0 | tail -40
cat /var/log/syslog.1 | tail -40
```


Alternatively, you may try installing kernel version 3.9 and see if the native driver in it works for you. [Instructions to install 3.9 kernel on Ubuntu 13.04]("http://linuxg.net/how-to-install-3-9-kernel-on-ubuntu-13-04-12-10-12-04-and-linux-mint-15-14-13/")
If you try that, you will have to unblacklist the native driver (remove the line "blacklist rt2800pci" from /etc/modprobe.d/blacklist.conf file) and uninstall the proprietary driver ('sudo make uninstall' command from within the extracted driver directory where you installed the driver from).

Let me know if you wish to choose the alternative path and need help with that.

---

### Post by theperfectpunk on 2013-05-11
It hangs completely, i have to restart to resume :-(

Here's the required output

```
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ cat /var/log/dmesg.0 | tail -40
[   11.927200] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   11.927253] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input8
[   11.930272] hp_accel: laptop model unknown, using default axes configuration
[   11.935314] lis3lv02d: 8 bits 3DC sensor found
[   11.948782] input: HP WMI hotkeys as /devices/virtual/input/input9
[   11.964807] type=1400 audit(1368282883.576:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=520 comm="apparmor_parser"
[   11.964816] type=1400 audit(1368282883.576:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=516 comm="apparmor_parser"
[   11.965366] type=1400 audit(1368282883.576:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=520 comm="apparmor_parser"
[   11.965373] type=1400 audit(1368282883.576:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=516 comm="apparmor_parser"
[   11.965674] type=1400 audit(1368282883.576:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=520 comm="apparmor_parser"
[   11.965681] type=1400 audit(1368282883.576:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=516 comm="apparmor_parser"
[   11.975298] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input10
[   12.132728] Linux video capture interface: v2.00
[   12.140099] uvcvideo: Found UVC 1.00 device HP TrueVision HD (064e:e263)
[   12.145733] input: HP TrueVision HD as /devices/pci0000:00/0000:00:12.2/usb1/1-3/1-3:1.0/input/input11
[   12.145865] usbcore: registered new interface driver uvcvideo
[   12.145867] USB Video Class driver (1.1.1)
[   12.677263] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xf00173/0x240000/0xa2400, board id: 2068, fw id: 1028260
[   12.723942] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   13.944618] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.960894] init: udev-fallback-graphics main process (829) terminated with status 1
[   14.171148] init: failsafe main process (894) killed by TERM signal
[   14.473097] type=1400 audit(1368282886.084:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=969 comm="apparmor_parser"
[   14.473625] type=1400 audit(1368282886.084:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=969 comm="apparmor_parser"
[   14.474846] type=1400 audit(1368282886.084:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//pxgsettings" pid=969 comm="apparmor_parser"
[   14.476617] type=1400 audit(1368282886.088:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*//sanitized_helper" pid=969 comm="apparmor_parser"
[   14.509406] Bluetooth: Core ver 2.16
[   14.509515] NET: Registered protocol family 31
[   14.509518] Bluetooth: HCI device and connection manager initialized
[   14.509567] Bluetooth: HCI socket layer initialized
[   14.509571] Bluetooth: L2CAP socket layer initialized
[   14.509578] Bluetooth: SCO socket layer initialized
[   14.514133] Bluetooth: RFCOMM TTY layer initialized
[   14.514148] Bluetooth: RFCOMM socket layer initialized
[   14.514150] Bluetooth: RFCOMM ver 1.11
[   14.515702] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.515707] Bluetooth: BNEP filters: protocol multicast
[   14.515720] Bluetooth: BNEP socket layer initialized
[   14.659218] ppdev: user-space parallel port driver
[   14.711137] init: avahi-cups-reload main process (1010) terminated with status 1
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ cat /var/log/syslog.1 | tail -40
May 10 23:25:22 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May 10 23:25:22 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May 10 23:25:22 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> Policy set 'Auto MTNL' (wlan0) as default for IPv4 routing and DNS.
May 10 23:25:22 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> Writing DNS information to /sbin/resolvconf
May 10 23:25:22 mohit-HP-Pavilion-g6-Notebook-PC dnsmasq[1343]: setting upstream servers from DBus
May 10 23:25:22 mohit-HP-Pavilion-g6-Notebook-PC dnsmasq[1343]: using nameserver 8.8.8.4#53
May 10 23:25:22 mohit-HP-Pavilion-g6-Notebook-PC dnsmasq[1343]: using nameserver 8.8.8.8#53
May 10 23:25:22 mohit-HP-Pavilion-g6-Notebook-PC nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' took too long; killing it.
May 10 23:25:23 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> Activation (wlan0) successful, device activated.
May 10 23:25:23 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <warn> Dispatcher script timed out: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' timed out.
May 10 23:25:23 mohit-HP-Pavilion-g6-Notebook-PC avahi-daemon[953]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::9e2a:70ff:fe5b:9fa1.
May 10 23:25:23 mohit-HP-Pavilion-g6-Notebook-PC avahi-daemon[953]: New relevant interface wlan0.IPv6 for mDNS.
May 10 23:25:23 mohit-HP-Pavilion-g6-Notebook-PC avahi-daemon[953]: Registering new address record for fe80::9e2a:70ff:fe5b:9fa1 on wlan0.*.
May 10 23:25:30 mohit-HP-Pavilion-g6-Notebook-PC ntpdate[6453]: adjust time server 91.189.94.4 offset 0.119606 sec
May 10 23:25:41 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> (wlan0): IP6 addrconf timed out or failed.
May 10 23:25:41 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May 10 23:25:41 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May 10 23:25:41 mohit-HP-Pavilion-g6-Notebook-PC NetworkManager[990]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May 10 23:56:32 mohit-HP-Pavilion-g6-Notebook-PC dbus[922]: [system] Activating service name='org.debian.apt' (using servicehelper)
May 10 23:56:32 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon: INFO: Initializing daemon
May 10 23:56:32 mohit-HP-Pavilion-g6-Notebook-PC dbus[922]: [system] Successfully activated service 'org.debian.apt'
May 10 23:56:32 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May 11 00:01:33 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon: INFO: Quitting due to inactivity
May 11 00:01:33 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon: INFO: Quitting was requested
May 11 00:01:33 mohit-HP-Pavilion-g6-Notebook-PC dbus[922]: [system] Activating service name='org.debian.apt' (using servicehelper)
May 11 00:01:33 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon: INFO: Initializing daemon
May 11 00:01:33 mohit-HP-Pavilion-g6-Notebook-PC dbus[922]: [system] Successfully activated service 'org.debian.apt'
May 11 00:01:33 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May 11 00:02:20 mohit-HP-Pavilion-g6-Notebook-PC anacron[8991]: Anacron 2.3 started on 2013-05-11
May 11 00:02:20 mohit-HP-Pavilion-g6-Notebook-PC anacron[8991]: Will run job `cron.daily' in 5 min.
May 11 00:02:20 mohit-HP-Pavilion-g6-Notebook-PC anacron[8991]: Jobs will be executed sequentially
May 11 00:06:34 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon: INFO: Quitting due to inactivity
May 11 00:06:34 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon: INFO: Quitting was requested
May 11 00:06:34 mohit-HP-Pavilion-g6-Notebook-PC dbus[922]: [system] Activating service name='org.debian.apt' (using servicehelper)
May 11 00:06:34 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon: INFO: Initializing daemon
May 11 00:06:34 mohit-HP-Pavilion-g6-Notebook-PC dbus[922]: [system] Successfully activated service 'org.debian.apt'
May 11 00:06:34 mohit-HP-Pavilion-g6-Notebook-PC AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May 11 00:07:20 mohit-HP-Pavilion-g6-Notebook-PC anacron[8991]: Job `cron.daily' started
May 11 00:07:20 mohit-HP-Pavilion-g6-Notebook-PC anacron[9270]: Updated timestamp for job `cron.daily' to 2013-05-11
May 11 00:07:21 mohit-HP-Pavilion-g6-Notebook-PC cracklib: no dictionary update necessary.


```

---

### Post by varunendra on 2013-05-11
I got no hints there. Neither about wireless nor anything else.

Please try to connect, let it hang, wait for a couple of minutes. If it does not resume, do a hard reboot and immediately after it boots again, open a terminal and do this -
```
cd /var/log
tar cjf ~/Desktop/logs.tar.bz2 dmesg.0 syslog.1
```
This will create a "logs.tar.bz2" archive on your desktop. Attach it here.
(You may wish to extract the two files included in the archive, especially syslog.1, and analyse it yourself to make sure there is no sensitive information in it.)

Additionally, follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the pastebin link to the "netinfo.txt" file contents that the script generates.

---

### Post by theperfectpunk on 2013-05-11
> **varunendra said:**
> I got no hints there. Neither about wireless nor anything else.

Please try to connect, let it hang, wait for a couple of minutes. If it does not resume, do a hard reboot and immediately after it boots again, open a terminal and do this -
```
cd /var/log
tar cjf ~/Desktop/logs.tar.bz2 dmesg.0 syslog.1
```
This will create a "logs.tar.bz2" archive on your desktop. Attach it here.
(You may wish to extract the two files included in the archive, especially syslog.1, and analyse it yourself to make sure there is no sensitive information in it.)

Additionally, follow the "Wireless Script" link in my signature, follow the instructions in the linked post and post back the pastebin link to the "netinfo.txt" file contents that the script generates.

The pastebin link to netinfo.txt is [http://pastebin.com/a3BrsG9q](http://pastebin.com/a3BrsG9q)

I have attached the logs.tar.bz2 with this post.

---

### Post by varunendra on 2013-05-11
Still no hints nowhere. The wireless connection seems super fine to me (from the netinfo.txt, as well as syslog). And no activity, either wireless or anything else, seem to trigger anything that may cause a freeze. At this point, I am totally clueless. Will take another look at the patch (since it is the only thing that I have used rather carelessly) to see if there is any critical setting. But I guess that will be tomorrow as I am too tired now.

Meanwhile, take a look yourself at other logs in the /var/log directory, may be even older versions of syslog.2.gz or even older to see if there are any suspicious records at their ends (assuming the messages we are actually interested in are the last thing recorded, before you reboot).

I'd reboot my own laptop (I do it only once or twice a month ;)) to make sure I am following the correct logs.

Of course, no clues = no solutions, we desperately need any hints about what may be causing the freeze. Can you identify the exact situation when the freeze occurs? Can you repeat that situation at different times after booting (immediately, after some usage, whenever you want)? If so, please explain in detail what exactly triggers the freeze.

One more thing, disable IPv6 completely following this post : [http://ubuntuforums.org/showthread.php?t=2143561&p=12640479#post12640479](http://ubuntuforums.org/showthread.php?t=2143561&p=12640479#post12640479)

---

### Post by theperfectpunk on 2013-05-11
> **varunendra said:**
> Still no hints nowhere. The wireless connection seems super fine to me (from the netinfo.txt, as well as syslog). And no activity, either wireless or anything else, seem to trigger anything that may cause a freeze. At this point, I am totally clueless. Will take another look at the patch (since it is the only thing that I have used rather carelessly) to see if there is any critical setting. But I guess that will be tomorrow as I am too tired now.

Meanwhile, take a look yourself at other logs in the /var/log directory, may be even older versions of syslog.2.gz or even older to see if there are any suspicious records at their ends (assuming the messages we are actually interested in are the last thing recorded, before you reboot).

I'd reboot my own laptop (I do it only once or twice a month ;)) to make sure I am following the correct logs.

Of course, no clues = no solutions, we desperately need any hints about what may be causing the freeze. Can you identify the exact situation when the freeze occurs? Can you repeat that situation at different times after booting (immediately, after some usage, whenever you want)? If so, please explain in detail what exactly triggers the freeze.

One more thing, disable IPv6 completely following this post : [http://ubuntuforums.org/showthread.php?t=2143561&p=12640479#post12640479](http://ubuntuforums.org/showthread.php?t=2143561&p=12640479#post12640479)

The freeze does not occur when i connect to any access points, The freeze occurs when i try to access internet through firefox, pidgin, empathy etc.

---

### Post by varunendra on 2013-05-11
Please disable IPv6 following the link in my previous post, and post back if it makes any difference. I think you can safely keep it disabled even if it doesn't make any.

---

### Post by theperfectpunk on 2013-05-11
> **varunendra said:**
> Please disable IPv6 following the link in my previous post, and post back if it makes any difference. I think you can safely keep it disabled even if it doesn't make any.

Nope didn't work :-(

I'm gonna try upgrading the kernel

---

### Post by taralej on 2013-09-17
Great post and thank you for the patch!

It compiled and installed correctly. The strength of the wifi signal increased to 100% (from 80% using native drivers 13.04 ubuntu).

But bluetooth (on this rt3290 chip) is not available still :(

Do you have some ideas how to enable it?

Thank you!

---

### Post by varunendra on 2013-09-18
Welcome to the forums taralej !

Glad you found the post helpful. :)

As for the bluetooth, even if included on the same card, usually bluetooth troubleshooting approaches are different, and to be honest, I have no idea yet how this card is associated with bluetooth. So I'd suggest you start a new thread with a suitable title asking for help on specifically the bluetooth issue.

Feel free to post a link to this post/thread as a background/reference to the issue (if you think it is related), as well as posting a link to your thread here, so anyone having same issue with both BT/Wifi can follow the thread for a possible fix. If I got enough time, I'd like to take a look as well.

Good luck, and hope you'll get good help with the remaining issue(s).

---

