---
title: "Help with drivers!"
date: 2013-08-05
forum: Networking &amp; Wireless
---

### Post by tyler4 on 2013-08-05
I just reformatted my computer and installed Ubuntu on an Acer M5-583P. I now can't use the recovery partition, so I am stuck without a laptop until I can figure out how to find a driver for it. I already had to have the nomodeset installation, so I know that there exists no graphics drivers. The wireless adapter inside is a 7260 N. Does anybody have any idea how to at least get my wireless working?
I also tried everything here to no avail: [http://askubuntu.com/questions/322511/no-wireless-with-intel-centrino-advanced-n-7260](http://askubuntu.com/questions/322511/no-wireless-with-intel-centrino-advanced-n-7260)

---

### Post by carl4926 on 2013-08-05
Read this
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Isn't it Intel Graphics? Should be OK

Acer wifi sometimes needs some blacklisting
But we need to see the result of
```
lspci -nnk
```

---

### Post by tyler4 on 2013-08-05
I can't boot with UEFI mode into linux because I needed to have the nomodeset property applied in order to actually be able to install. This isn't possible with UEFI because there are no options that would allow me to do that,

The command you wanted me to enter yields the following:
 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 09)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:0830]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
04:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 63)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4060]
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: rtsx_pci
05:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 14)
    Subsystem: Acer Incorporated [ALI] Device [1025:079b]
    Kernel driver in use: r8169


I've read on the intel forums that they probably don't have a driver for it yet. I read that you might even have to compile your own kernel to use it. I might try updating to 3.11 and see what happens.

---

### Post by carl4926 on 2013-08-05
I don't know, I'm not an EFI guru

---

### Post by tyler4 on 2013-08-05
Assuming it's a wireless issue and not one regarding the BIOS, would you have any advice on finding the drivers?

---

### Post by carl4926 on 2013-08-05
I guess this give some clues
[https://bbs.archlinux.org/viewtopic.php?id=167305](https://bbs.archlinux.org/viewtopic.php?id=167305)

Have you tested 13.10 live ?
Just to see if the kernel there is better for your HW

---

### Post by tyler4 on 2013-08-05
Actually it was 13.10 that I tried it on. I was talking about updating the kernel to 3.11 RC3.

---

### Post by carl4926 on 2013-08-05
> **tyler4 said:**
> Actually it was 13.10 that I tried it on. I was talking about updating the kernel to 3.11 RC3.
Right sorry
Worth a try updating the kernel

---

### Post by chili555 on 2013-08-05
>     I also tried everything here to no avail: [http://askubuntu.com/questions/32251...dvanced-n-7260](http://askubuntu.com/questions/32251...dvanced-n-7260) 

What about my answer here didn't work?

---

### Post by tyler4 on 2013-08-05
I still don't have wifi.

---

### Post by tyler4 on 2013-08-05
I updated the kernel with no luck still. Do you guys think a driver will come out for it? I got the laptop a month ago, but I am starting to think it will only truly function with windows on it.

---

### Post by chili555 on 2013-08-05
> **tyler4 said:**
> I still don't have wifi.Very informative.

Did you compile the backports package successfully? Were there errors or warnings? Did you make the needed changes to iwl-7000.c? Did you install the firmware? Was there any error or warning when you loaded the driver?```
sudo modprobe iwlwifi
```Is the backports version the one that is being used?```
modinfo iwlwifi | grep -e 08B1 -e version
```Was a wireless interface created?```
iwconfig
```Are there any errors or warnings here?```
dmesg | grep iwl
```Finally, do you have the exact same device?```
lspci -nn | grep 0280
```

---

### Post by tyler4 on 2013-08-05
tyler@tyler-Aspire-M5-583P:~$ sudo modprobe iwlwifi
[sudo] password for tyler: 
tyler@tyler-Aspire-M5-583P:~$ modinfo iwlwifi| grep -e 08B1
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
tyler@tyler-Aspire-M5-583P:~$ modinfo iwlwifi| grep -e 08B1 version
grep: version: No such file or directory
tyler@tyler-Aspire-M5-583P:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

tyler@tyler-Aspire-M5-583P:~$ dmesg | grep iwl
tyler@tyler-Aspire-M5-583P:~$ lspci -nn |grep 0280
04:00.0 Network controller [0280]: Intel Corporation Device [8086:08b1] (rev 63
Everything compiled just fine. I didn't notice any warnings or errors.

---

### Post by chili555 on 2013-08-05
> tyler@tyler-Aspire-M5-583P:~$ modinfo iwlwifi| grep -e 08B1 versionPlease try again:```
modinfo iwlwifi| grep -e 08B1 [COLOR="#FF0000"]-e[/COLOR] version
```And did you install the firmware? Did you recompile after you upgraded the kernel? If not, please do so and then:```
sudo modprobe iwlwifi
dmesg | grep iwl
```> I am starting to think it will only truly function with windows on it. To be a little too blunt, it ain't over until Dr. Chili says it's over. So far, it ain't over by a long way.

EDIT: If you compiled correctly, you should see:> [COLOR="#FF0000"]version:        backported from Linux (v3.10-0-g8bb495e) using backports v3.10-2-0-ga29c78e[/COLOR]
version:        in-tree:d
srcversion:     E5DDF167634A4AC31A4D778
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
vermagic:       3.8.0-27-generic SMP mod_unload modversions 

---

### Post by tyler4 on 2013-08-05
Haha okay! Thank you! 
Where would I obtain the firmware at?

---

### Post by tyler4 on 2013-08-05
tyler@tyler-Aspire-M5-583P:~$ modinfo iwlwifi| grep -e 08B1 -e version
version:        backported from Linux (v3.10-0-g8bb495e) using backports v3.10-2-0-ga29c78e
version:        in-tree:d
srcversion:     BC89119CDF49183FFC6F3C6
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
vermagic:       3.11.0-031100rc4-generic SMP mod_unload modversions 
tyler@tyler-Aspire-M5-583P:~$ sudo modprobe iwlwifi
[sudo] password for tyler: 
tyler@tyler-Aspire-M5-583P:~$ dmesg | grep iwl
tyler@tyler-Aspire-M5-583P:~$

---

### Post by chili555 on 2013-08-05
> **tyler4 said:**
> Haha okay! Thank you! 
Where would I obtain the firmware at?Right back at the askubuntu link you gave in post #1.

Let's also see, after a reboot:```
dmesg | grep 04:00
```

---

### Post by tyler4 on 2013-08-05
Yeah. I just installed the firmware and nothing changed. I also have to stop the boot up every time I start and set it into nomodeset. 
tyler@tyler-Aspire-M5-583P:~$ dmesg | grep 04:00
[    0.212416] pci 0000:04:00.0: [8086:08b1] type 00 class 0x028000
[    0.212462] pci 0000:04:00.0: reg 0x10: [mem 0xb0500000-0xb0501fff 64bit]
[    0.212653] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.212706] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.706417] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt

---

### Post by chili555 on 2013-08-05
> Yeah. I just installed the firmware and nothing changed.You would need to either reboot or unload and reload the driver; depending on what version of Ubuntu you are running:```
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
sudo modprobe iwldvm
sudo modprobe iwlwifi
```> [ 0.212416] pci 0000:04:00.0: [[COLOR="#FF0000"]8086:08b1[/COLOR]] type 00 class 0x[COLOR="#FF0000"]0280[/COLOR]00
[ 0.212462] pci 0000:04:00.0: reg 0x10: [mem 0xb0500000-0xb0501fff 64bit]
[ 0.212653] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[ 0.212706] pci 0000:04:00.0: System wakeup disabled by ACPI
[ 0.706417] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt Here we see your device and nothing that I know of that's alarming. Please run and post:```
rfkill list all
```I'd love to see your entire dmesg:```
dmesg > tyler4.txt
```Find the file tyler4.txt in your user directory and paste it here and give us the link: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by tyler4 on 2013-08-05
tyler@tyler-Aspire-M5-583P:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
[http://paste.ubuntu.com/5952668/](http://paste.ubuntu.com/5952668/)

---

### Post by tyler4 on 2013-08-05
Reboot and reload did nada for the wifi.

---

### Post by chili555 on 2013-08-05
Very interesting. I am concerned about several things:> [    0.000000] WARNING: CPU: 0 PID: 0 at /home/apw/COD/linux/drivers/iommu/dmar.c:488 warn_invalid_dmar+0x8f/0xa0()
[    0.000000] Your BIOS is broken; DMAR reported at address 0!
[    0.000000] BIOS vendor: Insyde Corp.; Ver: V2.13; Product Version: TBD by OEMI don't know if that is trivial or a show-stopper. I'm not a BIOS person. I think I'd research it and see if it something that needs to be fixed or ignored. I suggest you search and then post here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)> [   13.838334] r8169 0000:05:00.1 eth0: unable to load firmware patch rtl_nic/rtl8411-2.fw (-2)Is your ethernet working as expected? If so, I suggest you ignore this.> [   15.762318] Bluetooth: hci0 failed to open Intel firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq(-2)
[   15.763999] Bluetooth: hci0 failed to open default Intel fw file: intel/ibt-hw-37.7.bseqThe same for bluetooth; if it's working as expected, ignore it; if not, let's try to fix it.

We do see signs of the driver loading or at least trying:> [  901.308408] compat: module verification failed: signature and/or required key missing - tainting kernel
[  901.310134] Loading modules backported from Linux version v3.10-0-g8bb495e
[  901.310136] Backport generated by backports.git v3.10-2-0-ga29c78e
[  901.332338] cfg80211: Calling CRDA to update world regulatory domain
[  901.338828] cfg80211: World regulatory domain updated:
[  901.338832] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  901.338835] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  901.338837] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  901.338839] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  901.338841] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  901.338843] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  901.354133] Intel(R) Wireless WiFi driver for Linux, in-tree:d
[  901.354138] Copyright(c) 2003-2013 Intel CorporationI wonder if Network Manager is defaulting to ethernet and not taking control of wireless. I suggest you reboot with the ethernet cable detached and check:```
iwconfig
lsmod | grep iwl
dmesg | grep iwl
```Is your BIOS set to defaults? In most cases, default is fine for Ubuntu.

---

### Post by tyler4 on 2013-08-05
I had to set my bios to legacy because UFI starts up with a completely black screen and doesn't allow me to add nomodeset.

---

### Post by Valene_Reynolds on 2013-08-05
Check over this link here on setting up your wifi drivers. Its called a NDIS wrapper. It could help you get that ubuntu build up and going on your ubuntu build. Here is the link for that wrapper. You can use this wrapper for you wifi driver. 


~~~~~~~~~~~~~~~~~~~~~~~~
Cyanogenmod nook color"""""""""""""""XDA nook color. Android kernel developer, youngest femme to develop an android kernel.

---

### Post by tyler4 on 2013-08-05
I don't see a link

---

### Post by Valene_Reynolds on 2013-08-05
Hold on. Don't spam here. I will get you up. Here is the link on that wrapper. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

That is what I used. The wrapper is all over the net , just google for it if that guide is too complicated. 



~~~~~~~~~~~~~~~~~~~`
cyanogenmod nook color""""""""""""XDA nook color

---

### Post by tyler4 on 2013-08-05
I am getting an error that I believe relates to me having updated the kernel. 
FATAL: Module ndiswrapper not found.

I give up. This computer isn't going to work.

---

### Post by chili555 on 2013-08-06
First, I doubt that ndiswrapper is the answer. By definition, it requires Windows XP drivers to work. I highly doubt that XP drivers are written for this very new, bleeding edge device. I am even a little skeptical that Vista drivers exist!

Second, I am very interested in new devices and figuring out the way to get them going. I was looking forward to getting this working for you and thereby having a guide for all those that follow. The forum works that way. Solve it once and dozens read it and solve it, too.

However, I understand that you need your computer to be working to enjoy it and not as a seemingly endless research project.

---

### Post by tyler4 on 2013-08-07
Yeah, Ndiswrapper didn't seem promising at all. I do have debian on my machine right now, which I know Ubuntu is based off of. If you want to keep throwing ideas at me, I can try them out while I wait for my recovery discs to arrive. I look forward to being able to run linux on this machine though, so as long as I don't have windows to use I will try any ideas you have.

---

### Post by chili555 on 2013-08-07
> **tyler4 said:**
> Yeah, Ndiswrapper didn't seem promising at all. I do have debian on my machine right now, which I know Ubuntu is based off of. If you want to keep throwing ideas at me, I can try them out while I wait for my recovery discs to arrive. I look forward to being able to run linux on this machine though, so as long as I don't have windows to use I will try any ideas you have.I suggest you try all the steps carefully from my askubuntu answer. Please don't forget the firmware. Reboot and paste your dmesg. We'll go from there.

---

### Post by tyler4 on 2013-08-08
Actually, the make command got messed up. Let me reinstall Ubuntu and see what happens when I follow your answer again.

---

### Post by chili555 on 2013-08-08
> **tyler4 said:**
> Actually, the make command got messed up. Let me reinstall Ubuntu and see what happens when I follow your answer again.A problem at 'make' is usually easily fixable. Nothing has yet been installed in your system. What happened?

---

### Post by tyler4 on 2013-08-08
Something to do with missing essential header files. I reinstalled some parts of make and made sure everything was installed, and it still wasn't working. For some reason I couldn't use my USB wireless adapter with that version of Debian (beta), although it worked fine with the stable release. All in all, it's too complicated for me to try and address all of these issues at once. I think moving back to Ubuntu would be best for trying to get the internal wireless card up and running.

---

### Post by chili555 on 2013-08-12
Hey, tyler4! I helped a guy running 13.10 get his 7260 *confirmed working*!!! I suggest you do the same process: [http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63/331696#331696](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63/331696#331696) I am pretty sure it will work for 13.04 also.

You will also need the build tools:```
sudo apt-get install build-essential linux-headers-generic
```Let us know if it works for you.

---

### Post by carlexpc on 2013-08-12
Try booting your Acer M5-583P using an Ubuntu LiveCD, and see if your wireless network device works. You could start your driver troubleshooting from there.

---

### Post by chili555 on 2013-08-12
> **carlexpc said:**
> Try booting your Acer M5-583P using an Ubuntu LiveCD, and see if your wireless network device works. You could start your driver troubleshooting from there.Did you not read the whole thread? We absolutely know that no driver exists in Ubuntu even in the developmental release 13.10. Trying the live CD is not just specious but a waste of time.

---

### Post by tem4 on 2013-08-18
I am in the same miserable boat.  Bought an m5-583p, installed Ubuntu and ran into these same issues.  Any more progress on this or do I have to go buy a usb wifi adapter for now?

---

### Post by carl4926 on 2013-08-18
> **tem4 said:**
> I am in the same miserable boat.  Bought an m5-583p, installed Ubuntu and ran into these same issues.  Any more progress on this or do I have to go buy a usb wifi adapter for now?

More progress since 5 days ago...unlikely
Go shopping and buy carefully

---

### Post by chili555 on 2013-08-18
More progress since this post?> Hey, tyler4! I helped a guy running 13.10 get his 7260 confirmed working!!! I suggest you do the same process: [http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63/331696#331696](http://askubuntu.com/questions/331667/no-wireless-for-intel-corporation-7260-version-63/331696#331696) I am pretty sure it will work for 13.04 also.No, none. However, I doubt you need anything more than_* confirmed working*_.

---

