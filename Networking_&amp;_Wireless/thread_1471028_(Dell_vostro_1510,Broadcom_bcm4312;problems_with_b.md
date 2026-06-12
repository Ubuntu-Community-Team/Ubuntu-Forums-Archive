---
title: ":(Dell vostro 1510,Broadcom bcm4312;problems with b43"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by nbulchandani on 2010-05-03
Hello,
I am unable to use wireless on Lynx;
The specs are as
1.i have a broadcom bcm4312 as there is a line in lspci as:
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
2.iwconfig says:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.
3.sudo lshw -C network says:
 *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:24:2b:60:a5:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
4.scanning for networks via iwlist scan gives
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.
5.dmesg says
b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   10.138880] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   10.145674] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   10.145747] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

6.Finally,lsmod says:
b43                   157218  0 
this about wireless..
Thanks

---

### Post by snowpine on 2010-05-03
Are you sure b43 is the correct driver for your BCM4312 card? Give this how-to a thorough read: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Also, the process will be much easier if you can connect to the internet with a wired connection. :)

---

### Post by SFCampbell on 2010-05-03
> **nbulchandani said:**
> 
1.i have a broadcom bcm4312 as there is a line in lspci as:
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


Try this - Open your modules list for editing:

**sudo gedit /etc/modules**

Add "**wl**" to the end of the file without quotations.  Just the letters WL.  This will call a Broadcom software module at every start-up.  Save, close, reboot.  You will likely see your wireless network list populate with scanned networks.

---

### Post by wojox on 2010-05-03
Have you gone into Hardware Drivers and activated **Broadcom STA wireless driver**

Then reboot and click on Network Manager applet to configure. 

I have a Dell Studio with the same specs and that worked for me.

---

### Post by nbulchandani on 2010-05-03
Well,
I dont have a wired connection.Just now downloaded the bcm4312 driver ..going to extract firmware from it..NOte:I have installed b43 without extracting firmware(i dont have a wired connection:()..What should i do first edit modules or fetch the firmware?and @wojox;it does not detect the hardware driver after install however it did this while using the livecd for installation
Thanks

---

### Post by nbulchandani on 2010-05-03
Well,adding wl to /etc/modules did not work.Can i extract the firmware if i have downloaded the driver from windows and use b43cutter in linux without a net connection there?
Thanks

---

### Post by nbulchandani on 2010-05-03
can anyone help me extracting firmware manually with b43cutter?i dont stand a chance of getting a wired connection
Thanks

---

### Post by snowpine on 2010-05-03
> **nbulchandani said:**
> can anyone help me extracting firmware manually with b43cutter?i dont stand a chance of getting a wired connection
Thanks

Did you read the official Ubuntu documentation that I linked to in post #2? It has directions for what to do if you don't have an internet connection. It also recommends against b43fwcutter for Dell computers with BCM4312... you are free to do as you like :) but why not start with what Ubuntu recommends?

---

### Post by nbulchandani on 2010-05-03
Hello,
i used bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu.deb
it gave the following errors
get_source3_i386
     if self._apt_pkg(package).installed:
    File "usr/lib/python 2.6/dist-packages----
ValueError:package does not exist
dpkg:error processing bcm-wl-kernel-source (--install):
subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
bcm-wl-kernel-source
Now what to to?

---

### Post by snowpine on 2010-05-03
Cool, we are getting somewhere. :) Is i386 the correct architecture? (I think your computer is 64 bit maybe?)

---

### Post by nbulchandani on 2010-05-03
Ofcourse dude:)

---

### Post by nbulchandani on 2010-05-03
Well,..it has been a lot.I have internet acces in my cell phone;when i connect it using bluetooth it gives me a option to use internet from that.do i stand a chance to install firmware from my cell phone'net? Thanks

---

### Post by snowpine on 2010-05-03
Hmmm I don't know what to tell you. :( The only thing I can think of is that the Ubuntu instructions haven't been updated yet for 10.04? I personally have never had to do it without a wired connection.

---

### Post by nbulchandani on 2010-05-03
Never mind.atleast you tried.Thanks.Maybe someone else may help me out.Can any one help me please?

---

### Post by nbulchandani on 2010-05-03
Any one any ideas?

---

### Post by pdc on 2010-05-04
if you read this 

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

it recommends the broadcom sta 

the title of your post 

> Broadcom bcm4312;problems with b43

may be because you persist with b43 (instead of sta)

---

### Post by nbulchandani on 2010-05-04
By broadcom ;is bcmwl  meant?if it is it gives errors as i have written in an earlier post in this thread.

---

### Post by nbulchandani on 2010-05-04
Does no one have any idea.please help me folks...3 days since i have installed ubuntu.no wifi:(

---

### Post by zaphod777 on 2010-05-04
I would try the cell phone trick just make sure you won't get charged for too much data.

Or goto Fry's and find a cheap open box wireless adapter that works in Linux update your other driver and then return it to Fry's and say it didn't work for you.

---

### Post by nbulchandani on 2010-05-04
so how do i use my mobile's net to download the firmware?

---

### Post by zaphod777 on 2010-05-04
depends on the phone what kind do you have? google your phone model and "tethering"

---

### Post by nbulchandani on 2010-05-04
can't you folks suggest a way to fix the driver??

---

### Post by snowpine on 2010-05-04
> **nbulchandani said:**
> can't you folks suggest a way to fix the driver??

If the Ubuntu method isn't working for you for whatever reason (I've always been able to do it one-click with a working ethernet connection, no problem) you can get it direct from Broadcom: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I have not personally tried this method with Ubuntu, but I have used it several times in the past with other distros that do not provide it in their repositories.

Start by thoroughly reading README.txt if you decide this is something you want to try. I personally think the Ubuntu method is much easier, but the nice thing about Linux is that there is always more than one option. :)

---

### Post by nbulchandani on 2010-05-05
Well,
i followed the readme.and i did all the steps succesfully it seems.but still wifi networks not detected:(.and no hardware drivers detected...
A particualar thing i noticed is that the command: 
# lsmod  | grep "b43\|ssb\|wl"
gives ssb when i boot every time.is that a problem.can you help  me checking where do i stand now..and what should i do?
Thanks

---

### Post by nbulchandani on 2010-05-05
Well,
i followed the readme.and i did all the steps succesfully it seems.but still wifi networks not detected:(.and no hardware drivers detected...
A particualar thing i noticed is that the command: 
# lsmod  | grep "b43\|ssb\|wl"
gives ssb when i boot every time.is that a problem.can you help  me checking where do i stand now..and what should i do?Anyways i am attatching the readme i followed..
Thanks

---

### Post by bkratz on 2010-05-05
> **nbulchandani said:**
> Well,
i followed the readme.and i did all the steps succesfully it seems.but still wifi networks not detected:(.and no hardware drivers detected...
A particualar thing i noticed is that the command: 
# lsmod  | grep "b43\|ssb\|wl"
gives ssb when i boot every time.is that a problem.can you help  me checking where do i stand now..and what should i do?Anyways i am attatching the readme i followed..
Thanks

Did you do this part of the steps--

 Check to see if ssb, wl or b43 is loaded:
  # lsmod  | grep "b43\|ssb\|wl"

  If any of these are installed, remove them:
  # rmmod b43
  # rmmod ssb
  # rmmod wl

[B]  Back up the current boot ramfs and generate a new one.
  # cp /boot/initrd.img-`uname -r`  somewheresafe
  # update-initramfs -u
  # reboot[/B]


The update......is supposed to update the boot information, hopefully stopping ssb--However I did not see anywhere in the above whether your system uses a broadcom ethernet connection, typically using b44 driver and also requiring ssb.
lspci should give you that information.

---

### Post by nbulchandani on 2010-05-05
Well,
i did lsmod | grep "b43\|ssb\|wl"
and i got
ssb 
so i did 
rmmod ssb
and updated initrd as given...
now on booting wifi networks not detected yet:(.
but the terminal says
noks@noks-laptop:~$ lsmod | grep "b43\|ssb\|wl"
noks@noks-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

Now what?

---

### Post by nbulchandani on 2010-05-05
well,figured it out.had to first install the patch thing and then bcmwl
Thanks all

---

### Post by ublintu on 2010-05-05
Hi,
Maybe this way working as well.
[http://ubuntuforums.org/showthread.php?t=1474008&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=1474008&highlight=broadcom)

---

