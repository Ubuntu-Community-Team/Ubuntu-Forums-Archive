---
title: "Grub problem"
date: 2012-09-16
forum: Mythbuntu
---

### Post by emedlin18 on 2012-09-16
After I installed mythbuntu 12.0.4.1 to a usb drive I was getting error out of disk and no suitable mode found.  After showing these errors for a few minutes it would finish booting.  I read that if I uncommented GRUB_TERMINAL=console in /etc/default/grub and ran sudo update-grub that should fix the error.  Well now it won't boot to mythtv at all.  It just boots to a grub prompt.  From there I can do:
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro acpi=off noapic
initrd /initrd.img
boot
and it boots up although I cannot select 1080p as a resolution when I believe it was running at that before.  Also those commands seem very slow.  It takes a minute or two before linux and initrd return.

Here is my /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by oldfred on 2012-09-16
You can try to repairs, but post the BootInfo link it creates:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by emedlin18 on 2012-09-17
emedlin@mythtv:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 80, in get_ppa_info_from_lp
    curl.perform()
pycurl.error: (6, "Couldn't resolve host 'launchpad.net'")

I am remoted into the machine through my lan, so I know the nic is working.

emedlin@mythtv:/etc/network$ cat interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.10.100
netmask 255.255.255.0
gateway 192.168.10.1

All though it looks like this machine cannot get out to the net for some reason.
emedlin@mythtv:/etc/network$ telnet time-a.nist.gov 13                          telnet: could not resolve time-a.nist.gov/13: Name or service not known

Pretty sure this was working because it told me updates were available after I installed the OS.

---

### Post by emedlin18 on 2012-09-17
I can ping the router.
emedlin@mythtv:/etc/network$ ping  192.168.10.1
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.
64 bytes from 192.168.10.1: icmp_req=1 ttl=64 time=0.318 ms
64 bytes from 192.168.10.1: icmp_req=2 ttl=64 time=0.302 ms
64 bytes from 192.168.10.1: icmp_req=3 ttl=64 time=0.377 ms
^C
--- 192.168.10.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.302/0.332/0.377/0.035 ms

I can ping my cable modem.
emedlin@mythtv:/etc/network$ ping 192.168.100.1
PING 192.168.100.1 (192.168.100.1) 56(84) bytes of data.
64 bytes from 192.168.100.1: icmp_req=1 ttl=63 time=1.92 ms
64 bytes from 192.168.100.1: icmp_req=2 ttl=63 time=1.90 ms
64 bytes from 192.168.100.1: icmp_req=3 ttl=63 time=1.96 ms
^C
--- 192.168.100.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2009ms
rtt min/avg/max/mdev = 1.908/1.932/1.964/0.023 ms

So, what could be blocking me?

---

### Post by oldfred on 2012-09-17
Your exact command works for me. But it checks my Ubuntu mirror and does updates also. 

Is you mirror working?

---

### Post by emedlin18 on 2012-09-18
Not sure how do I test to see if my mirror is working?

---

### Post by emedlin18 on 2012-09-18
sudo apt-get update produces alot of Failed to fetch... lines.

It seems the machine cannot get to the net, but can get to my cable modem and other machine on my network.  What would cause this?

---

### Post by YannBuntu on 2012-09-18
Hi 
You should create another thread in order to get help for this network problem. Once it is solved, come back here so that we can check your GRUB problem.

---

### Post by emedlin18 on 2012-09-19
[http://paste.ubuntu.com/1215882/](http://paste.ubuntu.com/1215882/)

This is what I got after clicking Recommended Repair.

---

### Post by emedlin18 on 2012-09-19
I rebooted it and it is setting with a black screen with a blinking cursor in the upper left hand corner.

---

### Post by emedlin18 on 2012-09-19
Well after I left it alone for awhile it did finally boot.  I just rebooted it again to see how long it takes.  This time it says error: out of disk with the flashing cursor under it.  This is one of the errors I was originally trying to fix. It sets here for 5 minutes then says press any key to continue.  Shortly after that without pressing a key the text changes to some strange symbol looking font and finally finishes loading the OS.  Oh, and the resolution is correct again. It also has a dialog box telling me System program problem detected.  This is new. When I clicked report the problem, I got another dialog saying add-apt-repository has closed unexpectedly. It says it couldn't resolve launchpad.net.  Maybe boot repair killed my interface file.

---

### Post by emedlin18 on 2012-09-19
interfaces file is still correct.

emedlin@mythtv:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.10.100
netmask 255.255.255.0
gateway 192.168.10.1
dns-nameservers 8.8.8.8 192.168.10.1

And I can ping launchpad.net, so I don't know why I get that error.  Or, how boot repair could have caused it, but it wasn't there before.

---

### Post by uteck on 2012-09-19
> This time it says error: out of disk
There's your problem.
If your disk is full, that would expalin why it is slow to boot and your other problems.

---

### Post by emedlin18 on 2012-09-19
Not full or even close.

emedlin@mythtv:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        15G  2.4G   12G  17% /
udev            368M  4.0K  368M   1% /dev
tmpfs            64M  8.0K   64M   1% /tmp
tmpfs           150M  872K  149M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            375M     0  375M   0% /run/shm
tmpfs            64M  476K   64M   1% /var/log
tmpfs            64M     0   64M   0% /var/tmp

---

### Post by oldfred on 2012-09-19
We seem to be seeing more and more of the out of disk error. Sometimes reinstall of grub2 solves it, sometimes making smaller / (root) solves it. You already have a small root so that is not the issue.

Do you have AHCI on in BIOS? Required for SSDs, but I am not sure that changes the grub issue.

If you hold shift key from BIOS, do you get grub menu?

It seems like your Internet may be intermittent? If it keeps not getting to the net?

Can you look in Log Files with Log File Viewer if you can boot or they are in /var/log. There are many logs, but look at dmesg first as it is a log of booting. Look for errors, long times between activities, or a driver trying to load multiple times.

---

### Post by emedlin18 on 2012-09-20
I think the boot repair reinstalled grub atleast I though it said it was doing that.

I don't think my old 845g MB running a P4 supports AHCI and I am running off a USB thumb drive not an SSD.

It boots to the grub menu everytime without holding shift.  Started doing that after the boot repair also.

Network is fine for other machines.  It actually seems add-apt-repository is trying to get on the net before the network is ready.  Because, as soon as I close that dialog and open a console up I can ping the site.  Also this didn't happen until the boot repair.

Only line with error in dmesg, doesn't look like an error though.
[   13.225350] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

Longest delays in dmesg, only a few seconds though.
[    2.376487] sd 0:0:0:0: [sda] Attached SCSI removable disk
[    2.509538] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   12.992593] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.038464] udevd[327]: starting version 175
.
.
.
[   20.354163] lirc_serial: auto-detected active high receiver
[   20.390811] lirc_serial lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 0
[   24.786960] init: plymouth-stop pre-start process (1369) terminated with status 1
[   25.669006] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   26.920047] eth0: no IPv6 routers present

All errors:
emedlin@mythtv:/var/log$ fgrep -i error *
auth.log:Sep 20 00:02:30 mythtv dbus[640]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.28" (uid=110 pid=1535 comm="/usr/bin/mythbackend --syslog local7 --user mythtv") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=911 comm="NetworkManager ")
auth.log:Sep 20 00:02:30 mythtv dbus[640]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.28" (uid=110 pid=1535 comm="/usr/bin/mythbackend --syslog local7 --user mythtv") interface="org.freedesktop.NetworkManager" member="GetDevices" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=911 comm="NetworkManager ")
dmesg:[   13.225350] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
kern.log:Sep 19 21:20:08 mythtv kernel: [   13.225350] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
fgrep: lightdm: Permission denied
syslog:Sep 19 21:20:08 mythtv kernel: [   13.225350] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
syslog:Sep 19 21:20:10 mythtv NetworkManager[911]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Xorg.0.log:     (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

I didn't see any drivers loading multiple times in dmesg.

---

### Post by oldfred on 2012-09-20
I remember some of those type errors from my old system and I do not think they are critical. My current configuration does have some things like the Ethernet start  up & go down for some reason also. 

Once you add Boot-Repair to the sources list, it should go out and check for updates like all the Ubuntu software, but I thought was once per day or how you set it.

Does just the command line updates work ok.This should just  make sure it is current.

sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade
sudo apt-get -f install

---

### Post by emedlin18 on 2012-09-20
I know I can run  sudo apt-get update as that is one of the ways I tested my internet connection.  But, how does running those commands fix my grub or add-apt-repository has closed unexpectedly problem?  A fresh install of 12.04.1 should not give grub errors that cause boot to take >5 minutes plus tell me  add-apt-repository has closed unexpectedly when the OS gets loaded.

---

### Post by oldfred on 2012-09-20
Did you set static Ethernet to .100? That is usually inside the DHCP range and that then can cause all sorts of conflicts. If setting static, you need to use a port number not  in the DHCP, but have to check router to see what its DHCP range is.

---

### Post by emedlin18 on 2012-09-21
DHCP range starts at .101.  Grub's out of disk error is the real problem I would like to solve as that causes the system to take over 5mins. to boot.

---

### Post by oldfred on 2012-09-21
All I can suggest now is a total uninstall and reinstall of grub2. You do not need chroot from a liveCD if you can boot. But do have to have Internet working as it totally deletes grub-pc and downloads a new copy.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by emedlin18 on 2012-09-21
I have already used boot repair to reinstall grub once which didn't help.  Although looking at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) I see there is a check box for ATA disk support that solves out of disk error.  Sounds like something I should check.  Any clue what it changes?

---

### Post by YannBuntu on 2012-09-21
Yes you can try it. If it doesn't work, run the "Recommended repair" to revert the change.

But i see another possible problem: your /etc/fstab is strange:

> proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=eff32271-3c9a-49c7-b7b1-a3543c824d2a /               ext4    errors=remount-ro,noatime,nodiratime 0       1
tmpfs /var/log tmpfs rw,noexec,size=64M 0 0
tmpfs /tmp tmpfs rw,size=64M 0 0
tmpfs /var/tmp tmpfs rw,size=64M 0 0 

Did you create it manually?
If not, try to comment the 3 last lines (add # at the start of each).

---

### Post by emedlin18 on 2012-09-21
Yes, I created the fstab file like that.  I made the tmp and log directories tmpfs file systems to reduce the amount of writes to the usb drive.

Got it from here.
[http://www.styryx.com/en/computers/operating-systems/unix-linux/linux-installation-to-usb-flash](http://www.styryx.com/en/computers/operating-systems/unix-linux/linux-installation-to-usb-flash)

---

### Post by emedlin18 on 2012-09-22
Well boot repair didn't work it made it worse.  This is getting old.  I checked the box for ATA disk support that solves out of disk error and hit apply.  Now it boots to a grub rescue prompt with the error "error: no such device: eff32271-3c9a-49c7-b7b1-a3543c824d2a"

Here is the link from boot repair.
[http://paste.ubuntu.com/1221072/](http://paste.ubuntu.com/1221072/)

---

### Post by oldfred on 2012-09-22
I still do not see anything wrong.

Have you tried another thumb drive. They do fail.

---

### Post by emedlin18 on 2012-09-22
New thumb drive, also the only one I have that is large enough.  Any test I can run on it?  I ran CrystalDiskMark on it when I got it and it was very fast for a thumb drive.

---

### Post by YannBuntu on 2012-09-22
> **emedlin18 said:**
> Now it boots to a grub rescue prompt with the error "error: no such device: eff32271-3c9a-49c7-b7b1-a3543c824d2a"

Here is the link from boot repair.
[http://paste.ubuntu.com/1221072/](http://paste.ubuntu.com/1221072/)

That means the "ATA support" option doesn't help. You can remove this option by clicking "Recommended repair".
If i were you, i would backup documents, then reinstall.

---

### Post by emedlin18 on 2012-09-22
No documents to backup as it is a fresh install.  It is also the second install that I have done.  Not sure if a third would help much.  Is there an alternative to grub?  Is it easy to switch to something else?  It really seems grub is just not compatible with my system.  Are there other case of grub not being compatible with an older system?  10.04 with grub worked fine, but that was also installed to an HD and not a USB thumb drive.

---

### Post by oldfred on 2012-09-22
The issue with grub2 lately seems to be larger partitions. I boot my 8GB partition on my 16GB flash without issue.

There are a variety of boot loaders, but you probably are on your own as most of use use grub2.

Lilo, syslinux , and others. Lilo has been around for years, I think it was the one I used with Redhat 15 years ago. The started maintaining it again as I understand. Syslinux is the one on the liveUSBs. Both as I understand are like the Windows boot loader in the MBR is just a chainload to a PBR where there is more boot code.

Both lilo & syslinux are in Repository. 

This is the note on lilo-doc
> This package contains very old PDF and README documentations of lilo.> SYSLINUX is a collection of boot loaders which operates off Linux ext2/3/4 or
btrfs filesystems, MS-DOS FAT filesystems, network servers using PXE firmware,
or from CD-ROMs.

---

### Post by emedlin18 on 2012-09-22
Don't really want to be on my own. So, how big should /boot be.  I would like to make it as small as reasonably possible.  The rest of the USB drive will be /.

---

### Post by emedlin18 on 2012-09-23
Looks like you can just create a new /boot.
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

Although everything I read about this error/bug it says that /boot must be in the first 100gigs or 137gigs.  My drive is only 16gig, so is this really the same problem?

---

### Post by YannBuntu on 2012-09-23
> **emedlin18 said:**
> Although everything I read about this error/bug it says that /boot must be in the first 100gigs or 137gigs.  My drive is only 16gig, so is this really the same problem?

16<100, so i don't think so :)

See also [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) for partition sizes.

---

### Post by emedlin18 on 2012-09-23
> **YannBuntu said:**
> 16<100, so i don't think so :)

See also [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) for partition sizes.


Well if you don't think that is the problem, do you know of anything else to try?  Is it worth trying?  Could it be a bios problem?  I have an updated bios that is suppose add large HD support, but once again 16gig thumb drive doesn't really sound like it needs large HD drive support.

---

