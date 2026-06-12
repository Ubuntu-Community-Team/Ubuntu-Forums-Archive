---
title: "Very slow boot"
date: 2023-05-13
forum: MINT
---

### Post by pintasa on 2023-05-13
Very slow boot. Over 3 minutes

OS: Linux Mint 20.1 Ulyssa -- base: Ubuntu 20.04 focal
CPU: Quad Core model: Intel Core i5-3470 bits
RAM: 8GB
SSD: CT240BX500SSD1 size: 223.57 GiB speed: 3.0 Gb/s
HDD: ST500DM002-1BD142 size: 465.76 GiB speed: 6.0 Gb/s rotation: 7200 rpm

I had Mint 18 on the HDD and two years ago I did a clean, new, install of Mint 20 on the SSD. At the time boot time was normal but it has gotten slower over time. I feel OS has become slower overall, with programs taking longer time to launch but very particularly the boot time has become much longer. 

Searching the forums I see several issues I do not quite understand but here is some information. 

> systemd-analyze time
Startup finished in 14.169s (kernel) + 1min 15.600s (userspace) = 1min 29.770s 
graphical.target reached after 1min 15.593s in userspace 


I see fstab mentioned a lot but no idea how to analyze it or correct it if needed. 

> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=3c511947-bd97-4be0-985d-963a8fb2fdca /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
# UUID=B891-4F4E  /boot/efi       vfat    umask=0077      0       1
# /swapfile                                 none            swap    sw              0       0
# /dev/disk/by-uuid/3b832ec4-fd2d-4824-bb84-6ed19723d3af /mnt/3b832ec4-fd2d-4824-bb84-6ed19723d3af auto nosuid,nodev,nofail,x-gvfs-show 0 0


> 
NAME     SIZE RO TYPE 
sda    465,8G  0 disk 
&#9500;&#9472;sda1   512M  0 part /dev/sda1: UUID="B891-4F4E" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="37bb6b1b-86d3-4a76-af56-157807f60a86"
&#9500;&#9472;sda2 457,4G  0 part /dev/sda2: UUID="3b832ec4-fd2d-4824-bb84-6ed19723d3af" TYPE="ext4" PARTUUID="7cbf4b1f-4a39-469e-865c-4b9d9c69726c"
&#9492;&#9472;sda3   7,9G  0 part /dev/sda3: UUID="5de95303-47d3-4469-8f03-1780f8ae647a" TYPE="swap" PARTUUID="633c4ac8-9852-48fe-9474-04c7cdfbb126"
sdb    223,6G  0 disk 
&#9500;&#9472;sdb1   512M  0 part /dev/sdb1: UUID="2869-2314" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="57699a38-54e7-4aa6-9564-dd85bce41678"
&#9492;&#9472;sdb2 223,1G  0 part /dev/sdb2: UUID="3c511947-bd97-4be0-985d-963a8fb2fdca" TYPE="ext4" PARTUUID="8568611a-4093-4678-a2f5-8629d84e0964"
sr0     11:0    1  1024M  0 rom  



I also have suspicions about SAMBA and maybe some driver for some device. 

What should I do?

---

### Post by coffeecat on 2023-05-13
*Thread moved to **MINT** sub-forum.*

---

### Post by oldfred on 2023-05-13
Some things to review:
Do not know Mint, I think it does not use snaps which should help.

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by pintasa on 2023-05-13
Thanks to both.  I am afraid I am a total beginner and all those pages are much deeper than I can understand.  The most often mentioned cause for slow boot is misconfigured fstab but I have no idea why this would happen or how it could be corrected. I was hoping someone could have a look at my fstab and drives and tell me if it looks ok or not.

Another thing I found which might be useful. 
```

sudo systemd-analyze blame
[sudo] password for a:       
33.094s dev-sdb2.device                                
29.634s systemd-journal-flush.service                  
23.845s systemd-udevd.service                          
14.256s nmbd.service                                   
10.465s networking.service                             
 8.934s networkd-dispatcher.service                    
 8.662s udisks2.service                                
 8.616s accounts-daemon.service                        
 8.294s polkit.service                                 
 8.243s avahi-daemon.service                           
 8.235s NetworkManager.service                         
 8.234s ubuntu-system-adjustments.service              
 8.110s thermald.service                               
 8.042s systemd-logind.service                         
 8.004s wpa_supplicant.service                         
 6.875s smartmontools.service                          
 6.147s apparmor.service                               
 4.150s alsa-restore.service                           
 3.609s systemd-modules-load.service                   
 2.691s systemd-sysusers.service                       
 2.357s systemd-random-seed.service                    
 2.222s NetworkManager-wait-online.service             
 1.337s grub-initrd-fallback.service                   
 1.293s rsyslog.service                                
 1.120s gpu-manager.service                            
 1.100s grub-common.service                            
 1.046s systemd-tmpfiles-setup-dev.service             
  897ms systemd-backlight@backlight:acpi_video0.service
  873ms kerneloops.service                             
  792ms plymouth-start.service                         
  560ms ModemManager.service 
```

---

### Post by oldfred on 2023-05-13
You start with first entry and set what it is.
So what is sdb2?
Does it need e2fsck or other repairs. Not shown in fstab, so not sure why it is an issue.

It looks like you commented out the ESP? Did you convert install from UEFI to old BIOS? UUID in fstab is same as UUID in of partitions.
It does look like you commented out the last line, which has UUID not shown, so would be an issue. Better to mount by label, not UUID so you can tell what it is easily.

---

### Post by TheFu on 2023-05-14
A failing disk can cause slowness.  If you look at the SMART data for the disk (sdb), look at the 'raw' column. If the tool you use for SMART data doesn't show the raw column, you'll need a better tool.  smartctl is what I use.  Anyway, failing disks show they are failing about 78% of the time through SMART.  It can also show cable errors, which you probably have extras laying around, if you ever bought a motherboard or internal HDD.  They all come with SATA cables.

That's where I'd start.  Also, if you don't do backups, at least weekly, start.  There's something about doing backups that prevents 'bit-rot'.  On MS-Windows, bit rot often is seen as a BSOD at boot ... because systematic backups weren't performed to keep the bits active and give the hardware routine chances to correct and move data from sectors before they full fail.

fsck should be performed every 60 days, at least.  It is possible to tune the file system parameters to force this for ext2/3/4 file systems.  Use the **tune2fs** program for that.  I don't remember what the default period is.  Also, it could be different between SSDs and HDDs.

If the system is using a HDD still, these days it is really cheap to replace that HDD with an SSD.  They are drop-in replacements for the most part. Plus SATA SSDs are cheaper than NVMe SSDs.  I have a laptop that came with a 1TB 2.5in HDD.  The first thing I did, before even booting it, was to pull the HDD out and install a $50 500GB 2.5in Samsung SSD.  Then I did a fresh install of a light Ubuntu flavor and setup daily, automatic, backups to another system on the LAN here.

Performance differences:
[LIST]
[*]HDDs (sata) = 20MB/s - 180MB/s  (depends on built-in cache size)
[*]SSDs (sata) = 250MB/s - 580MB/s (depends on built-in cache size)
[*]SSDs (NVMe) = 3000 MB/s+
[/LIST]


But for almost all end users, the SATA SSD performance increase is amazing.

If you don't use PPP to connect to the internet, you don't need the Modem Service enabled.  It is possible an number of other services aren't needed.
```
systemd-analyze critical-chain
```
is another command to help see why booting is slow.  On computers with multiple cores, most things are parallel, so using the "blame" option to see what's taking time doesn't always reflect additive problems.

A slow DHCP server can be an issue for boot times.  If you setup a static IP on the system for your LAN, that could drastically reduce time.  Also, if you don't use wifi, then you don't need any wifi services.  Wifi is hard to tune because so many parts of those connections are outside our control, unlike a wired ethernet connection.

---

