---
title: "Wireless has completely vanished after upgrading to 12.04"
date: 2012-09-28
forum: Networking &amp; Wireless
---

### Post by Mecer on 2012-09-28
Hey everyone, I'm pretty new to linux, so I hope you could help me out  here... You see, I've just recently upgraded from 10.04 to 12.04 on my  laptop and wireless simply, absolutely vanished. It isn't listed on  ifconfig, iwconfig says "No wireless extensions." and  network-manager-gnome says "device not ready (firmware missing)".

I've  tried installing tg3 and b43, but nothing works... Maybe it's some kind  of conflict from the upgrade, as it was working absolutely fine before  it. Thanks in advance for your help! Here's some info to boot, but ask  anything you need!

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux Mecer 2.6.32-40-generic #87-Ubuntu SMP Tue Mar 6 00:56:56 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
        Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
        Kernel driver in use: iwlagn
--
85:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
        Subsystem: Hewlett-Packard Company Device [103c:30dd]
        Kernel driver in use: tg3

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b059 Chicony Electronics Co., Ltd CKF7037 HP webcam
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810

lo        no wireless extensions.

eth0      no wireless extensions.

tun0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

---

### Post by daslinkard on 2012-09-28
Can you physically turn your wi-fi on either through a button on the laptop or through a combination of your FN key + one of your F keys? Or potentially uninstalling NetworkManager may correct the issue as I've seen this as a solution in previous threads.

---

### Post by Mecer on 2012-09-28
> **daslinkard said:**
> Can you physically turn your wi-fi on either through a button on the laptop or through a combination of your FN key + one of your F keys? Or potentially uninstalling NetworkManager may correct the issue as I've seen this as a solution in previous threads.

Yeah, I can... I have installed the gnome NetworkManager on kubuntu 10.04, so maybe something on the upgrade went wrong. How do I uninstall NetworkManager?

---

### Post by daslinkard on 2012-09-28
> **Mecer said:**
> Yeah, I can... I have installed the gnome NetworkManager on kubuntu 10.04, so maybe something on the upgrade went wrong. How do I uninstall NetworkManager?

You should be able to run the following sudo command:

```
 sudo apt-get purge NetworkManager
```

---

### Post by Mecer on 2012-09-28
> **daslinkard said:**
> You should be able to run the following sudo command:

```
 sudo apt-get purge NetworkManager
```

Hmmm, all I got was "Unable to locate package NetworkManager"...

---

### Post by BicyclerBoy on 2012-09-28
In 12.04 I believe the wifi firmware is now in package
linux-firmware

Don't know for sure what driver your/hardware requires but..
For the b43 there are diff/new firmware cutting/loading tools.
The latest kernels (3.5) break the b43 broadcomm driver.

Why is your kernel (report in post #1) so old ? It is older than 10.04.3..
12.04.1 is using 3.2.0-29something..

Do you have your grub set to boot a specific linux image?

uname -r

---

### Post by daslinkard on 2012-09-28
> **BicyclerBoy said:**
> In 12.04 I believe the wifi firmware is now in package
linux-firmware

Don't know for sure what driver your/hardware requires but..
For the b43 there are diff/new firmware cutting/loading tools.
The latest kernels (3.5) break the b43 broadcomm driver.

Why is your kernel (report in post #1) so old ? It is older than 10.04.3..
12.04.1 is using 3.2.0-29something..

Do you have your grub set to boot a specific linux image?

Upon further research I would agree with BicyclerBoy in updating linux-firmware.

---

### Post by Mecer on 2012-09-29
> **daslinkard said:**
> Upon further research I would agree with BicyclerBoy in updating linux-firmware.
Hmmm, that's weird... I tried:
```

pa@Mecer:~/Desktop/pk/Server/Linux/Driver$ sudo apt-get install linux-firmware
[sudo] password for pa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
The following packages were automatically installed and are no longer required:
  liblualib50 libruby libt1-5 libgtkhtml3.14-19 liberb-ruby lesstif2 hddtemp rubygems1.8 libqt3-mt liblua50
  openbsd-inetd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

pa@Mecer:~/Desktop/pk/Server/Linux/Driver$ sudo apt-get install linux-image-3.2.0-31-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-3.2.0-31-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  liblualib50 libruby libt1-5 libgtkhtml3.14-19 liberb-ruby lesstif2 hddtemp rubygems1.8 libqt3-mt liblua50
  openbsd-inetd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Apparently I have both the newest kernel and the newest linux-firmware installed... Maybe it's conflicting to the older versions? How do I remove them? Thanks a lot for the help, guys!!

---

### Post by BicyclerBoy on 2012-09-29
The kernel that is running could be diff, you have muliple kernel images installed..

uname -r

We are chasing the wrong driver..
The wifi is the Intel WiFi Link 5100 AGN [8086:1211]
The driver is iwlagn..there are some bugs against this device, I can't find any solved posts..

You might have to plug in with cable for a while..

rfkill list

---

### Post by Mecer on 2012-09-29
> **BicyclerBoy said:**
> The kernel that is running could be diff, you have muliple kernel images installed..

uname -r

We are chasing the wrong driver..
The wifi is the Intel WiFi Link 5100 AGN [8086:1211]
The driver is iwlagn..there are some bugs against this device, I can't find any solved posts..

You might have to plug in with cable for a while..

rfkill list
Okay, I got these for both uname -r and rfkill list, respectively:

```

2.6.32-40-generic

0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

---

### Post by BicyclerBoy on 2012-09-29
You must have set your grub to boot that linux image version..

That kernel version is the version in lucid 10.04.3 about 2 weeks ago..
12.04 never used it.

sudo update-grub
can you post the output..

---

### Post by Mecer on 2012-09-29
> **BicyclerBoy said:**
> You must have set your grub to boot that linux image version..

That kernel version is the version in lucid 10.04.3 about 2 weeks ago..
12.04 never used it.

sudo update-grub
can you post the output..
```

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.2.0-31-generic
Found kernel: /boot/vmlinuz-2.6.32-40-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```Also, I'm trying everything to boot GRUB, but I simply can't. I've tried holding SHIFT while kubuntu boots, changing timeout to -1 and nothing... I can't even boot that new kernel like that orz
If nothing works, I'm switching to ubuntu... But I really don't want to do that, as this is my work laptop and I'd have to configure vpn, ssh and set a lot of stuff up again...

---

### Post by BicyclerBoy on 2012-09-29
The only diff between ubuntu & kubuntu is one desktop package (& dependencies).

Kubuntu (KWin) has better performance (bling/eye-candy) than unity (compiz).

Just have a look in this config file (warning do not touch /boot/grub/*)
/etc/default/grub
 edit this file stop it pointing to the old kernel by changing this line:
GRUB_SAVEDEFAULT=false

then run
sudo update-grub

Can you run this sanity check:
dpkg-query -l grub*

---

### Post by AndyOpie150 on 2012-09-29
Try installing these packages in the order their listed:

dkms_2.2.0.3-1ubuntu3_all.deb
ndiswrapper-dkms_1.57-1ubuntu1_all.deb


What ever security level the Network Manager recognize's is as high as you can go on your router.

If after installing and then rebooting the computer you still don't see the Icon (or you got dependency error's), and your network isn't listed as an option in the wireless portion. You will need to install these packages in the order listed:

ndiswrapper-common_1.57-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb
libglade2-0_2.6.4-1ubuntu1_i386.deb
python-glade2_2.24.0-3_i386.deb
ndisgtk_0.8.5-1_i386.deb

Note: If you got dependency errors with the dkms and ndiswrapper-dkms then install them after everything else.

Next: You will have to go to the Networking and wireless forum and look at the threads in there to determine the install procedure for installing the wireless driver (you might even have to install a different driver than the one originally designed for your wireless device)

Go to the sticky and make sure you post all the info mentioned so the experts over there can quickly determine what you will need to do.

I'll will let a Moderator know you need your thread moved over there.

---

### Post by BicyclerBoy on 2012-09-29
Are you sure?
Some people have strong opinions about the ndiswrapper method..

Others suggest iwlwifi driver with "n" disabled.

And how about just getting the right/normal kernel version used first...

---

### Post by Mecer on 2012-09-29
> **BicyclerBoy said:**
> The only diff between ubuntu & kubuntu is one desktop package (& dependencies).

Kubuntu (KWin) has better performance (bling/eye-candy) than unity (compiz).

Just have a look in this config file (warning do not touch /boot/grub/*)
/etc/default/grub
 edit this file stop it pointing to the old kernel by changing this line:
GRUB_SAVEDEFAULT=false

then run
sudo update-grub

Can you run this sanity check:
dpkg-query -l grub*

Sure! Here it is:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                    Version                 Description
+++-=======================-=======================-==============================================================
ii  grub                    0.97-29ubuntu66         GRand Unified Bootloader (Legacy version)
ii  grub-common             1.99-21ubuntu3.1        GRand Unified Bootloader (common files)
un  grub-coreboot           <none>                  (no description available)
un  grub-efi                <none>                  (no description available)
un  grub-efi-amd64          <none>                  (no description available)
un  grub-efi-ia32           <none>                  (no description available)
un  grub-emu                <none>                  (no description available)
un  grub-ieee1275           <none>                  (no description available)
un  grub-legacy             <none>                  (no description available)
un  grub-legacy-doc         <none>                  (no description available)
un  grub-linuxbios          <none>                  (no description available)
rc  grub-pc                 1.98-1ubuntu13          GRand Unified Bootloader, version 2 (PC/BIOS version)
un  grub-yeeloong           <none>                  (no description available)
un  grub2                   <none>                  (no description available)

```

Edit: That didn't work... I still couldn't boot GRUB and I'm still stuck with the old kernel :<

---

### Post by BicyclerBoy on 2012-09-29
I would run:
sudo apt-get update
sudo apt-get upgrade

Your list of grub packages does not match mine..but I have old legacy stuff.
The old 0.97 package prob should be buried in the backyard with full moon.

Try hitting <ESC> or <shift> key during boot (to get grub)..

Try with:
GRUB_HIDDEN_TIMEOUT=5

---

### Post by Mecer on 2012-09-29
> **BicyclerBoy said:**
> I would run:
sudo apt-get update
sudo apt-get upgrade

some of those grub packages are not the latest.
The old 0.97 package prob should be buried in the backyard with full moon.

Try hitting <ESC> or <shift> key during boot (to get grub)..

Try with:
GRUB_HIDDEN_TIMEOUT=5
Here it is. I tried setting every timeout to -1 in order to boot it, to no avail:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=-1
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_SAVEDEFAULT=false

```Edit: Yeah, I was able to upgrade grub-common to ubuntu3.4. Rebooted, hit [SHIFT] and [ESC] multiple times, still no GRUB...

Edit 2: Okay, I have GRUB! But, all it lists is a bunch of "2.6.32-xx-generic" kernels, not one of them is the one that I want... Where can I configure that?

---

### Post by BicyclerBoy on 2012-09-29
AFAIK -1 is not a valid value in this context..

My system has grub2-common installed in addition to yours..
AFAIU
The <ESC> key works during grub working
The <shift> key works before grub starts.

Avoiding anything related to grub is good advice..

---

### Post by Mecer on 2012-09-29
Okay!!! I've installed grub2, successfully booted the newest kernel and everything works! Thanks a lot, man!!

---

### Post by BicyclerBoy on 2012-09-29
Thank *** for that (insert non-specific non-denominational honorific character)..

---

### Post by AndyOpie150 on 2012-09-30
> **BicyclerBoy said:**
> Are you sure?
Some people have strong opinions about the ndiswrapper method..

Others suggest iwlwifi driver with "n" disabled.

And how about just getting the right/normal kernel version used first...
The ndiswrapper method worked great for me. I'm fairly new to Ubuntu and didn't even know about the iwlwifi driver with "n" disabled. Maybe you could post a link that describes this method the best? I Like to help others, but I see I need to obtain more info in this area.

Mercer: Glade to see you got everything working (no help from me though, sorry).

---

### Post by Mecer on 2012-09-30
> **AndyOpie150 said:**
> The ndiswrapper method worked great for me. I'm fairly new to Ubuntu and didn't even know about the iwlwifi driver with "n" disabled. Maybe you could post a link that describes this method the best? I Like to help others, but I see I need to obtain more info in this area.

Mercer: Glade to see you got everything working (no help from me though, sorry).

Thanks a lot for you too! If updating the kernel didn't work out, I'd try your method next. Thanks for your interest in the issue!

---

