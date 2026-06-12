---
title: "Netgear WNDAv2 N600 wireless dual and USB adapter"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by Skullxbagel on 2012-02-29
I'm new to Linux and I was tying to set up an Internet connection, but I didn't have the driver for it, so the help section told me to fild the windows driver and find the .inf file then install some randomly named thing, which I couldn't find either. So just please help me find this .inf file, thanks

---

### Post by kurt18947 on 2012-02-29
This is talking about using NDISwrapper.  That is not necessarily the best first choice but it is sometimes the only game in town.  A usual good place to start would be to post the output of the command "lsusb".  To do this, open a terminal.  How to do that depends on which version of Ubuntu you are using.  I think ctrl-alt-t will work on any distro.  The output will look something like this:

```
account_name@xxxx:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
**Bus 002 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]**
Bus 004 Device 002: ID 047d:2048 Kensington 
Bus 004 Device 003: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 001 Device 005: ID 04f9:01f3 Brother Industries, Ltd 
Bus 004 Device 004: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
account_name@xxxx:~$
```This tells us this adapter uses an Atheros AR9271 chipset which is what we really want to know.

---

### Post by chili555 on 2012-02-29
Correct. Moreover, it tells us the usb.id:> Bus 002 Device 002: ID [COLOR="Red"]0846:9030[/COLOR] NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]We can search Google and this forum for the usb.id and get an idea of the correct procedure.

For the benefit of all the driver genies out there, the usb.id is everything!

@Skullxbagel--

Your usb.id is undoubtably different.

---

### Post by Skullxbagel on 2012-02-29
The I'd is 0846:9011

---

### Post by kurt18947 on 2012-03-01
The chipset appears to be a Broadcom BCM4323.  I'm ignorant of Broadcom except to avoid it if I can :wink:

[http://www.wikidevi.com/wiki/Netgear_WNDA3100v2](http://www.wikidevi.com/wiki/Netgear_WNDA3100v2)

---

### Post by chili555 on 2012-03-01
Please see post #29 here: [http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3](http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3)

The same files work for your device.

Post back if you need additional assistance.

---

### Post by Skullxbagel on 2012-03-01
Gahhh, it says 
Package 'ndiswrapper-common' is not installed and no info is available.
I have more routers If this is a problem
1 is 0461:4d16
Another is 050d:6050

---

### Post by chili555 on 2012-03-01
> Gahhh, it says
Package 'ndiswrapper-common' is not installed and no info is available.Please see post #33 here: [http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=4](http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=4)> I have more routers If this is a problem
1 is 0461:4d16
Another is 050d:6050 Let's solve one at a time, 0846:9011 as you stated above.

---

### Post by Skullxbagel on 2012-03-01
I try to download ndiswrapper from my cd it says it isn't in Debian format or something, does it need to be .iso, it's currently ndiswrapper-1.57-tar.gz
What now?

---

### Post by chili555 on 2012-03-02
> I try to download ndiswrapper from my cd it says it isn't in Debian format or something,I hope you are talking about your Ubuntu install CD; yes?? Is that where you tried to install ndiswrapper? You are using Ubuntu, aren't you? Please let us see:```
uname -r
```

Installing ndiswrapper from tar.gz is quite involved; we should reserve it for a last resort.

---

### Post by Skullxbagel on 2012-03-03
I am using Ubuntu and no, not at first atleast, but now I burned Ubuntu 11.10 and 10.04 to a disk but neither have ndiswrapper wrapper on them. Is that wht you mean by install disc?

---

### Post by chili555 on 2012-03-03
> **Skullxbagel said:**
> I am using Ubuntu and no, not at first atleast, but now I burned Ubuntu 11.10 and 10.04 to a disk but neither have ndiswrapper wrapper on them. Is that wht you mean by install disc?Are you quite sure? On my 10.04 disc, I browsed to pool > main > n > ndiswrapper and the .deb files you need are there. Please see attached.

I suggest you copy both to your desktop and then, in a terminal, do:```
sudo dpkg -i Desktop/ndis*.deb
```Then proceed as discussed above.

---

### Post by Skullxbagel on 2012-03-03
Now it says whenever I type in the terminal command


Dpkg:  error processing Desktop/ndis*.deb (--install):
Cannot process archive: no such file or directory
Errors were encountered while processing:
Desktop/ndis*.deb

I copied and pasted the ndiswrapper file and ndisgtk into the desktop, but the error happens, here's what I typed in 

***********-desktop:~$ sudo dpkg -i Desktop/ndis*.deb
Do I need to be su? If I do whenever It asks for my password correctly it says it is wrong.

---

### Post by chili555 on 2012-03-03
> ***********-desktop:~$ sudo dpkg -i Desktop/ndis*.debAre the files really there?```
cd Desktop
ls -al
sudo dpkg -i ndis*.deb
```> I copied and pasted the ndiswrapper file and ndisgtk into the desktop, but the error happens, here's what I typed in I hope you mean file***s***. You need -common *and* -utils; optionally ndisgtk.> Do I need to be su?That's what sudo does; become Super User temporarily; which is the most safe thing. If you try to su, it rejects your password because Mother Canonical doesn't think you should walk around with a lit stick of dynamite. As you gain experience with dynamite, you will discover a way around it. For now, use sudo.

---

### Post by Skullxbagel on 2012-03-03
Yess!!!! It worked I installed common and utils so now what do I do.

What I was doing wrong was that I tried installing the folder, not the files inside of the folder

---

### Post by chili555 on 2012-03-03
Now you proceed as outlined in the thread I linked above in post #6. Post back if you get stuck.

---

### Post by Skullxbagel on 2012-03-03
I did that, how do I use it?  I went to hardware drivers and there were none.

---

### Post by chili555 on 2012-03-03
> **Skullxbagel said:**
> I did that, how do I use it?  I went to hardware drivers and there were none.What???

Post #6 above refers you to post #29 here: [http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3](http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3)> Next, download the attached file to your desktop. Right-click it and select Extract Here. Now back in the terminal, do:
```
cd Desktop/wna3100-drivers
sudo su
ndiswrapper -i bcmwlhigh5.inf
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules
exit

```
Now is it working? If not, post back:
```
ndiswrapper -l
```

That says *nothing* about Hardware Drivers. Did you do that???

---

### Post by Skullxbagel on 2012-03-03
I just meant that I still don't have Internet, by the way on the codes like the one with the >> they did nothing

---

### Post by Skullxbagel on 2012-03-03
It says bcmwlhigh5 : invalid driver!

---

### Post by Skullxbagel on 2012-03-03
Whenever I do the ndiswrapper -l

---

### Post by chili555 on 2012-03-03
> **Skullxbagel said:**
> Whenever I do the ndiswrapper -lPlease run and post:```
dmesg | grep ndis
```

---

### Post by Skullxbagel on 2012-03-03
How do I write that line in between Dmesg and grep?

---

### Post by chili555 on 2012-03-03
> **Skullxbagel said:**
> How do I write that line in between Dmesg and grep?The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by Skullxbagel on 2012-03-03
Ok, it says this

[         14.251639] ndis(ndis is red)wrapper version 1.55 loaded (smp=yes, preempt=no)
[         14.711021] usbcore: registered new interface driver ndis(red)wrapper

---

### Post by chili555 on 2012-03-03
Looks pretty solid to me. How about:```
iwconfig
```

---

### Post by Skullxbagel on 2012-03-03
Lo.          No wireless extensions
Eth0.       No wireless Extensions

---

### Post by chili555 on 2012-03-04
> **Skullxbagel said:**
> The I'd is 0846:9011Here is a snip from the bcmwlhigh5.inf:> ;-----------------------------------------------------------------
; x86 - Win9x, Win2K, WinXP
;
[BROADCOM]
	%BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9011[/COLOR]
        
;-----------------------------------------------------------------I'm not quite sure it could be an invalid driver. As well, there don't seem to be any complaints in dmesg:> Ok, it says this

[ 14.251639] ndis(ndis is red)wrapper version 1.55 loaded (smp=yes, preempt=no)
[ 14.711021] usbcore: registered new interface driver ndis(red)wrapper Is yours a 64-bit system?```
arch
```Are there any clues here?```
ndiswrapper -l
sudo cat /var/log/syslog | grep ndis | tail -n10
```

---

### Post by Skullxbagel on 2012-03-04
X86_64

---

### Post by Skullxbagel on 2012-03-04
chris@chris-desktop:~$ sudo cat /var/log/syslog | grep ndis | tail -n10
[sudo] password for chris: 
Mar  3 09:45:19 chris-desktop kernel: [   11.810787] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar  3 09:45:19 chris-desktop kernel: [   12.372685] usbcore: registered new interface driver ndiswrapper
Mar  3 10:26:40 chris-desktop kernel: [   14.251639] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar  3 10:26:40 chris-desktop kernel: [   14.711021] usbcore: registered new interface driver ndiswrapper
Mar  3 13:39:46 chris-desktop kernel: [   11.471320] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar  3 13:39:46 chris-desktop kernel: [   11.787584] usbcore: registered new interface driver ndiswrapper
Mar  4 00:35:33 chris-desktop kernel: [   11.685219] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar  4 00:35:33 chris-desktop kernel: [   12.112103] usbcore: registered new interface driver ndiswrapper
Mar  4 01:59:39 chris-desktop kernel: [   11.516933] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar  4 01:59:39 chris-desktop kernel: [   11.771727] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2012-03-04
Ahhh! 64-bit!! Let's try again:```
sudo ndiswrapper -e bcmwlhigh5.inf
sudo rm -rf /etc/ndiswrapper/*
```Now download the attached file to your desktop. Right-click it and select *Extract Here*. Back in the terminal, do:```
cd Desktop/ndis_bcmwl
sudo su
ndiswrapper -i bcmwlhigh5.inf
modprobe -rv ndiswrapper
modprobe ndiswrapper
exit
iwconfig
```Any improvements?

---

### Post by Skullxbagel on 2012-03-04
It works, but I don't know how to use it to connect to the Internet. I won't be able to get onto my computer till next Saturday so I can't do anything for now.

---

### Post by chili555 on 2012-03-05
> **Skullxbagel said:**
> It works, but I don't know how to use it to connect to the Internet. I won't be able to get onto my computer till next Saturday so I can't do anything for now.If it's working, you should be able to click the Network Mananger icon, see your network, click it and connect.

See you then.

---

### Post by Skullxbagel on 2012-03-10
Sadly nothing happens, I think wireless connection 1 is the one I added a week ago but whenever I click on it, and press apply nothing happens, I thought maybe since the adapter has a cord to the computer that may work too but auto eth0 doesn't work either.

---

### Post by chili555 on 2012-03-10
Let's see:```
dmesg | grep -e ndis -e wlan
```

---

### Post by Skullxbagel on 2012-03-10
Also, it won't let me delete the 32 bit driver

---

### Post by chili555 on 2012-03-10
> **Skullxbagel said:**
> Also, it won't let me delete the 32 bit driverHow so? If you did these steps from my previous post, it's gone for sure:```
sudo ndiswrapper -e bcmwlhigh5.inf
sudo rm -rf /etc/ndiswrapper/*
```

---

### Post by Skullxbagel on 2012-03-10
chris@chris-desktop:~$ dmesg | grep -e ndis -e wlan
[   11.267134] ndiswrapper version 1.55 loaded (smp=yes,preempt=no)
[   11.719910] usbcore: registered new interface driver ndiswrapper

---

### Post by Skullxbagel on 2012-03-10
chris@chris-desktop:~$ sudo ndiswrapper -e bcmwlhigh5.inf
couldn't delete /etc/ndiswrapper/bcmwlhigh5.inf: No such file or directory
chris@chris-desktop:~$ sudo rm -rf /etc/ndiswrapper/*

---

### Post by chili555 on 2012-03-10
> **Skullxbagel said:**
> chris@chris-desktop:~$ sudo ndiswrapper -e bcmwlhigh5.inf
couldn't delete /etc/ndiswrapper/bcmwlhigh5.inf: No such file or directory
chris@chris-desktop:~$ sudo rm -rf /etc/ndiswrapper/*I think you've done all you need to do to get rid of the old .inf file. Now can you install the newer 64-bit version?

---

### Post by Skullxbagel on 2012-03-10
I did that now what- iwconfig says
Lo.        No wireless connections
Eth0.     No wireless connections

Sorry it's not connections it says extensions

---

### Post by chili555 on 2012-03-10
What does this tell us?```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by Skullxbagel on 2012-03-10
I'm trying a bunch of things but when I do mod probe it just freezes

---

### Post by Skullxbagel on 2012-03-10
Well not freeze, but it doesn't let me use password, I enter it and it just stays there for a while. Am I doing something wrong? This is what I entered.

Chris@chris-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for Chris: ( I entered right password)
( just freezes here)

---

### Post by Skullxbagel on 2012-03-10
No other commands work either, I'll try restarting the system

---

### Post by Skullxbagel on 2012-03-10
There might be. Problem, a few restarts ago it gave me an error saying there was some bad script or something epwasnt working, but now the computer is extremely slow, like it takes a minute for the login screen to even show, should I reinstall Linux?
How do I do that after I've already installed it as an os?

---

### Post by chili555 on 2012-03-10
Let's see if we can isolate what the error is. We are going to copy your message log to a text document and attach it to your reply. I'll look at it and we'll see what's happening.```
dmesg > skull.txt
```Look in your user directory for the file skull.txt and attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by Skullxbagel on 2012-03-10
Just letting you know whenever I type in my pass to login it gives me a window saying power manger is still running, after a few seconds I log in anyway, but just letting you know

---

### Post by Skullxbagel on 2012-03-10
That code does nothing and I don't know where skull.txt is, I'll keep looking

---

### Post by Skullxbagel on 2012-03-10
Yah, I can't find skull.txt, help?

---

### Post by chili555 on 2012-03-10
> **Skullxbagel said:**
> That code does nothing and I don't know where skull.txt is, I'll keep lookingIt simply creates a text file and puts it in your Home directory. It will not put out any text in the terminal. Was the terminal at 'Home' when you ran the command? If not, do this:```
cd
dmesg > skull.txt
```If the terminal was elsewhere, you should get something like this:> chili@LAPTOP60:~/Desktop/Forum$ cd
chili@LAPTOP60:[COLOR="Red"]~$[/COLOR] dmesg > skull.txt
chili@LAPTOP60:~$The part I've highlighted tells you that you are at 'home.'

---

### Post by Skullxbagel on 2012-03-11
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-38-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 (Ubuntu 2.6.32-38.83-generic 2.6.32.52+drm33.21)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=abce0f3a-5ddf-48e3-96aa-8861eeb7d559 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a400 (usable)
[    0.000000]  BIOS-e820: 000000000009a400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001a0000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 00000001b0000000 aka 6912M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcffb0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009a400 (usable)
[    0.000000]  modified: 000000000009a400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  modified: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  modified: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 00000001a0000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cffb0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cffb0000 page 4k
[    0.000000] kernel direct mapping tables up to cffb0000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-00000001a0000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0180000000 page 1G
[    0.000000]  0180000000 - 01a0000000 page 2M
[    0.000000] kernel direct mapping tables up to 1a0000000 @ 12000-14000
[    0.000000] RAMDISK: 377f3000 - 37fef09a
[    0.000000] ACPI: RSDP 00000000000fb050 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000cffb0100 0006C (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cffb0290 000F4 (v03 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20090903/tbfadt-557)
[    0.000000] ACPI: DSDT 00000000cffb05d0 04AB6 (v01 HPQOEM SLIC-CPC 00000504 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cffbe000 00040
[    0.000000] ACPI: APIC 00000000cffb0390 0007C (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cffb0410 0003C (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000cffb0450 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: OEMB 00000000cffbe040 00072 (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cffba6b0 00843 (v01 HPQOEM SLIC-CPC 00000001 INTL 20051117)
[    0.000000] ACPI: SRAT 00000000cffbaf00 000E8 (v03 HPQOEM SLIC-CPC 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 00000000cffbaff0 00038 (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cffbb030 0088C (v01 HPQOEM SLIC-CPC 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 2 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 3 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
[    0.000000] SRAT: Node 0 PXM 0 100000000-1b0000000
[    0.000000] NUMA: Allocated memnodemap from 13000 - 16640
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-00000001a0000000
[    0.000000]   NODE_DATA [0000000000016640 - 000000000001b63f]
[    0.000000]   bootmap [000000000001c000 -  000000000004ffff] pages 34
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 01a0000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a35ac4]    TEXT DATA BSS ==> [0001000000 - 0001a35ac4]
[    0.000000]   #3 [00377f3000 - 0037fef09a]          RAMDISK ==> [00377f3000 - 0037fef09a]
[    0.000000]   #4 [000009a400 - 0000100000]    BIOS reserved ==> [000009a400 - 0000100000]
[    0.000000]   #5 [0001a36000 - 0001a366a4]              BRK ==> [0001a36000 - 0001a366a4]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000]   #8 [0000013000 - 0000016640]       MEMNODEMAP ==> [0000013000 - 0000016640]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0005bfffff] PMD -> [ffff880028600000-ffff88002d7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x001a0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000cffb0
[    0.000000]     0: 0x00100000 -> 0x001a0000
[    0.000000] On node 0 totalpages: 1507130
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 110 pages reserved
[    0.000000]   DMA zone: 3812 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833512 pages, LIFO batch:31
[    0.000000]   Normal zone: 8960 pages used for memmap
[    0.000000]   Normal zone: 646400 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cffb0000 - 00000000cffbe000
[    0.000000] PM: Registered nosave memory: 00000000cffbe000 - 00000000cffe0000
[    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91608 r8192 d23080 u262144
[    0.000000] pcpu-alloc: s91608 r8192 d23080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1483724
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=abce0f3a-5ddf-48e3-96aa-8861eeb7d559 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 6518000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 5859324k/6815744k available (5436k kernel code, 787224k absent, 169196k reserved, 2982k data, 884k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:456
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 60293120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3100.307 MHz processor.
[    0.020004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6200.60 BogoMIPS (lpj=31003030)
[    0.020022] Security Framework initialized
[    0.020035] AppArmor: AppArmor initialized
[    0.020498] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.023226] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.024491] Mount-cache hash table entries: 256
[    0.024590] Initializing cgroup subsys ns
[    0.024594] Initializing cgroup subsys cpuacct
[    0.024596] Initializing cgroup subsys memory
[    0.024603] Initializing cgroup subsys devices
[    0.024605] Initializing cgroup subsys freezer
[    0.024606] Initializing cgroup subsys net_cls
[    0.024621] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.024623] CPU: L2 Cache: 512K (64 bytes/line)
[    0.024625] CPU 0/0x0 -> Node 0
[    0.024628] tseg: 0000000000
[    0.024639] CPU: Physical Processor ID: 0
[    0.024641] CPU: Processor Core ID: 0
[    0.024642] mce: CPU supports 6 MCE banks
[    0.024651] Performance Events: AMD PMU driver.
[    0.024655] ... version:                0
[    0.024656] ... bit width:              48
[    0.024657] ... generic registers:      4
[    0.024658] ... value mask:             0000ffffffffffff
[    0.024659] ... max period:             00007fffffffffff
[    0.024661] ... fixed-purpose events:   0
[    0.024662] ... event mask:             000000000000000f
[    0.025826] ACPI: Core revision 20090903
[    0.040005] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040009] ftrace: allocating 22567 entries in 89 pages
[    0.044765] Setting APIC routing to flat
[    0.045063] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.146250] CPU0: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.030000] Initializing CPU#1
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.030000] CPU 1/0x1 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 1
[    0.300066] CPU1: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.300079] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.310056] Booting processor 2 APIC 0x2 ip 0x6000
[    0.030000] Initializing CPU#2
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.030000] CPU 2/0x2 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 2
[    0.470068] CPU2: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.470077] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.480053] Booting processor 3 APIC 0x3 ip 0x6000
[    0.030000] Initializing CPU#3
[    0.030000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.030000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.030000] CPU 3/0x3 -> Node 0
[    0.030000] CPU: Physical Processor ID: 0
[    0.030000] CPU: Processor Core ID: 3
[    0.640071] CPU3: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.640080] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.650018] Brought up 4 CPUs
[    0.650020] Total of 4 processors activated (24800.68 BogoMIPS).
[    0.650394] CPU0 attaching sched-domain:
[    0.650398]  domain 0: span 0-3 level MC
[    0.650399]   groups: 0 1 2 3
[    0.650404] CPU1 attaching sched-domain:
[    0.650406]  domain 0: span 0-3 level MC
[    0.650407]   groups: 1 2 3 0
[    0.650410] CPU2 attaching sched-domain:
[    0.650411]  domain 0: span 0-3 level MC
[    0.650412]   groups: 2 3 0 1
[    0.650415] CPU3 attaching sched-domain:
[    0.650416]  domain 0: span 0-3 level MC
[    0.650417]   groups: 3 0 1 2
[    0.650493] devtmpfs: initialized
[    0.650493] regulator: core version 0.5
[    0.650493] Time: 23:51:33  Date: 03/10/12
[    0.650493] NET: Registered protocol family 16
[    0.650493] node 0 link 0: io port [1000, ffffff]
[    0.650493] TOM: 00000000d0000000 aka 3328M
[    0.650493] Fam 10h mmconf [e0000000, efffffff]
[    0.650493] node 0 link 0: mmio [a0000, bffff]
[    0.650493] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.650493] node 0 link 0: mmio [f0000000, fe7fffff]
[    0.650493] node 0 link 0: mmio [fe800000, fe9fffff]
[    0.650493] node 0 link 0: mmio [fea00000, ffefffff]
[    0.650493] TOM2: 00000001b0000000 aka 6912M
[    0.650493] bus: [00,07] on node 0 link 0
[    0.650493] bus: 00 index 0 io port: [0, ffff]
[    0.650493] bus: 00 index 1 mmio: [a0000, bffff]
[    0.650493] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.650493] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.650493] bus: 00 index 4 mmio: [1b0000000, fcffffffff]
[    0.650493] ACPI: bus type pci registered
[    0.650493] Trying to unpack rootfs image as initramfs...
[    0.650493] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.650493] PCI: Not using MMCONFIG.
[    0.650493] PCI: Using configuration type 1 for base access
[    0.650493] PCI: Using configuration type 1 for extended access
[    0.650654] bio: create slab <bio-0> at 0
[    0.650654] ACPI: EC: Look up EC in DSDT
[    0.650827] ACPI Error (psargs-0359): [ECEN] Namespace lookup failure, AE_NOT_FOUND
[    0.650831] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node ffffffff81a14080), AE_NOT_FOUND
[    0.650934] ACPI: Executed 3 blocks of module-level executable AML code
[    0.654623] ACPI: Interpreter enabled
[    0.654625] ACPI: (supports S0 S1 S3 S4 S5)
[    0.654639] ACPI: Using IOAPIC for interrupt routing
[    0.654675] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.656011] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.663514] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.666744] ACPI: No dock devices found.
[    0.666858] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.666965] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.666968] pci 0000:00:05.0: PME# disabled
[    0.667002] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.667004] pci 0000:00:0a.0: PME# disabled
[    0.667049] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.667055] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.667061] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.667067] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.667073] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.667079] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe7ffc00-0xfe7fffff]
[    0.667127] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe7fe000-0xfe7fefff]
[    0.667176] pci 0000:00:12.1: reg 10 32bit mmio: [0xfe7fd000-0xfe7fdfff]
[    0.667241] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe7ff800-0xfe7ff8ff]
[    0.667288] pci 0000:00:12.2: supports D1 D2
[    0.667289] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.667293] pci 0000:00:12.2: PME# disabled
[    0.667321] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe7fc000-0xfe7fcfff]
[    0.667370] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe7f7000-0xfe7f7fff]
[    0.667437] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe7ff400-0xfe7ff4ff]
[    0.667483] pci 0000:00:13.2: supports D1 D2
[    0.667485] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.667488] pci 0000:00:13.2: PME# disabled
[    0.667599] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe7f0000-0xfe7f3fff]
[    0.667637] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.667641] pci 0000:00:14.2: PME# disabled
[    0.667808] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.667811] pci 0000:01:05.0: reg 14 io port: [0xd000-0xd0ff]
[    0.667814] pci 0000:01:05.0: reg 18 32bit mmio: [0xfe8f0000-0xfe8fffff]
[    0.667819] pci 0000:01:05.0: reg 24 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.667829] pci 0000:01:05.0: supports D1 D2
[    0.667843] pci 0000:01:05.1: reg 10 32bit mmio: [0xfe8e8000-0xfe8ebfff]
[    0.667858] pci 0000:01:05.1: supports D1 D2
[    0.667897] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.667899] pci 0000:00:01.0: bridge 32bit mmio: [0xfe800000-0xfe9fffff]
[    0.667902] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.667932] pci 0000:02:00.0: reg 10 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.668027] pci 0000:00:05.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.668058] pci 0000:03:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.668071] pci 0000:03:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.668081] pci 0000:03:00.0: reg 20 64bit mmio pref: [0xfdffc000-0xfdffffff]
[    0.668111] pci 0000:03:00.0: supports D1 D2
[    0.668112] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.668116] pci 0000:03:00.0: PME# disabled
[    0.668168] pci 0000:00:0a.0: bridge io port: [0xe000-0xefff]
[    0.668170] pci 0000:00:0a.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.668174] pci 0000:00:0a.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.668226] pci 0000:00:14.4: transparent bridge
[    0.668245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.668360] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.668399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.668437] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.671157] ACPI: PCI Interrupt Link [LNKA] (IRQs *4 7 10 11 12 14 15)
[    0.671222] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.671285] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 12 14 15)
[    0.671346] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.671408] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.671471] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.671535] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *7 10 11 12 14 15)
[    0.671598] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.671671] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.671673] vgaarb: loaded
[    0.671749] SCSI subsystem initialized
[    0.671770] libata version 3.00 loaded.
[    0.671770] usbcore: registered new interface driver usbfs
[    0.671770] usbcore: registered new interface driver hub
[    0.671770] usbcore: registered new device driver usb
[    0.671770] ACPI: WMI: Mapper loaded
[    0.671770] PCI: Using ACPI for IRQ routing
[    0.671770] NetLabel: Initializing
[    0.671770] NetLabel:  domain hash size = 128
[    0.671770] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.671770] NetLabel:  unlabeled traffic allowed by default
[    0.671770] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.671770] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.672305] Switching to clocksource tsc
[    0.675144] AppArmor: AppArmor Filesystem Enabled
[    0.675144] pnp: PnP ACPI init
[    0.675144] ACPI: bus type pnp registered
[    0.675144] pnp: PnP ACPI: found 12 devices
[    0.675144] ACPI: ACPI bus type pnp unregistered
[    0.675144] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.675144] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.675144] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.675144] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.675144] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.675144] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.675144] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.675144] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.675144] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.675144] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.675144] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.675144] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.675144] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.675144] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.675144] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.675144] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.675144] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.675144] system 00:08: ioport range 0xb00-0xb0f has been reserved
[    0.675144] system 00:08: ioport range 0xb20-0xb3f has been reserved
[    0.675144] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.675144] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.675144] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.675144] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.675144] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.675144] system 00:09: ioport range 0xe00-0xe0f has been reserved
[    0.675144] system 00:09: ioport range 0xe80-0xe8f has been reserved
[    0.675144] system 00:09: ioport range 0xf40-0xf4f has been reserved
[    0.675144] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.675144] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.675144] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.675144] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.675144] system 00:0b: iomem range 0x100000-0xcfffffff could not be reserved
[    0.675144] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.677446] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.677448] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.677450] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe9fffff
[    0.677453] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.677456] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
[    0.677458] pci 0000:00:05.0:   IO window: disabled
[    0.677460] pci 0000:00:05.0:   MEM window: 0xfea00000-0xfeafffff
[    0.677462] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.677465] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:03
[    0.677467] pci 0000:00:0a.0:   IO window: 0xe000-0xefff
[    0.677469] pci 0000:00:0a.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.677472] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.677475] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.677476] pci 0000:00:14.4:   IO window: disabled
[    0.677481] pci 0000:00:14.4:   MEM window: disabled
[    0.677484] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.677498]   alloc irq_desc for 17 on node 0
[    0.677499]   alloc kstat_irqs on node 0
[    0.677503] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.677506] pci 0000:00:05.0: setting latency timer to 64
[    0.677510]   alloc irq_desc for 18 on node 0
[    0.677511]   alloc kstat_irqs on node 0
[    0.677513] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.677516] pci 0000:00:0a.0: setting latency timer to 64
[    0.677522] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.677524] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.677526] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.677528] pci_bus 0000:01: resource 1 mem: [0xfe800000-0xfe9fffff]
[    0.677530] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.677532] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.677534] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.677536] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.677537] pci_bus 0000:03: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.677539] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.677541] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.677568] NET: Registered protocol family 2
[    0.677731] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.678924] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.681738] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.682104] TCP: Hash tables configured (established 524288 bind 65536)
[    0.682107] TCP reno registered
[    0.682189] NET: Registered protocol family 1
[    1.445004] pci 0000:01:05.0: Boot video device
[    1.445786] PCI-DMA: Disabling AGP.
[    1.445863] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    1.445864] PCI-DMA: using GART IOMMU.
[    1.445868] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.447080] Scanning for low memory corruption every 60 seconds
[    1.447167] audit: initializing netlink socket (disabled)
[    1.447174] type=2000 audit(1331423493.444:1): initialized
[    1.453194] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.454164] VFS: Disk quotas dquot_6.5.2
[    1.454215] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.454693] fuse init (API version 7.13)
[    1.454759] msgmni has been set to 11443
[    1.455088] alg: No test for stdrng (krng)
[    1.455181] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.455184] io scheduler noop registered
[    1.455185] io scheduler anticipatory registered
[    1.455186] io scheduler deadline registered
[    1.455224] io scheduler cfq registered (default)
[    1.455443]   alloc irq_desc for 24 on node 0
[    1.455445]   alloc kstat_irqs on node 0
[    1.455452] pcieport 0000:00:05.0: irq 24 for MSI/MSI-X
[    1.455456] pcieport 0000:00:05.0: setting latency timer to 64
[    1.455595]   alloc irq_desc for 25 on node 0
[    1.455596]   alloc kstat_irqs on node 0
[    1.455600] pcieport 0000:00:0a.0: irq 25 for MSI/MSI-X
[    1.455603] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.455682] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.455700] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.455770] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.455779] ACPI: Power Button [PWRB]
[    1.455806] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.455807] ACPI: Power Button [PWRF]
[    1.456061] processor LNXCPU:00: registered as cooling_device0
[    1.456103] processor LNXCPU:01: registered as cooling_device1
[    1.456127] processor LNXCPU:02: registered as cooling_device2
[    1.456148] processor LNXCPU:03: registered as cooling_device3
[    1.457574] Linux agpgart interface v0.103
[    1.457602] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.458325] brd: module loaded
[    1.458586] loop: module loaded
[    1.458649] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.458907] Fixed MDIO Bus: probed
[    1.458929] PPP generic driver version 2.4.2
[    1.458956] tun: Universal TUN/TAP device driver, 1.6
[    1.458957] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.458999] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.459118] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.459147] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.459184] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.459226] ehci_hcd 0000:00:12.2: debug port 1
[    1.459244] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe7ff800
[    1.460378] Freeing initrd memory: 8176k freed
[    1.474936] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.475038] usb usb1: configuration #1 chosen from 1 choice
[    1.475057] hub 1-0:1.0: USB hub found
[    1.475063] hub 1-0:1.0: 6 ports detected
[    1.475182]   alloc irq_desc for 19 on node 0
[    1.475184]   alloc kstat_irqs on node 0
[    1.475189] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.475205] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.475229] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.475255] ehci_hcd 0000:00:13.2: debug port 1
[    1.475272] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe7ff400
[    1.494961] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.495065] usb usb2: configuration #1 chosen from 1 choice
[    1.495083] hub 2-0:1.0: USB hub found
[    1.495089] hub 2-0:1.0: 6 ports detected
[    1.495168] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.495219]   alloc irq_desc for 16 on node 0
[    1.495221]   alloc kstat_irqs on node 0
[    1.495225] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.495244] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.495271] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.495295] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe7fe000
[    1.559019] usb usb3: configuration #1 chosen from 1 choice
[    1.559037] hub 3-0:1.0: USB hub found
[    1.559049] hub 3-0:1.0: 3 ports detected
[    1.559150] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.559167] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.559193] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.559210] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe7fd000
[    1.619014] usb usb4: configuration #1 chosen from 1 choice
[    1.619032] hub 4-0:1.0: USB hub found
[    1.619043] hub 4-0:1.0: 3 ports detected
[    1.619145] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.619163] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.619189] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.619213] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fc000
[    1.679027] usb usb5: configuration #1 chosen from 1 choice
[    1.679046] hub 5-0:1.0: USB hub found
[    1.679058] hub 5-0:1.0: 3 ports detected
[    1.679163] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.679181] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.679210] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.679228] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe7f7000
[    1.730045] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.734133] usb usb6: configuration #1 chosen from 1 choice
[    1.734151] hub 6-0:1.0: USB hub found
[    1.734162] hub 6-0:1.0: 3 ports detected
[    1.734236] uhci_hcd: USB Universal Host Controller Interface driver
[    1.734295] PNP: No PS/2 controller found. Probing ports directly.
[    1.734683] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.734694] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.734787] mice: PS/2 mouse device common for all mice
[    1.734856] rtc_cmos 00:03: RTC can wake from S4
[    1.734886] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.734907] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.734997] device-mapper: uevent: version 1.0.3
[    1.735125] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.735279] device-mapper: multipath: version 1.1.0 loaded
[    1.735282] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.735468] cpuidle: using governor ladder
[    1.735469] cpuidle: using governor menu
[    1.735704] TCP cubic registered
[    1.735791] NET: Registered protocol family 10
[    1.736263] NET: Registered protocol family 17
[    1.736321] powernow-k8: Found 1 AMD Athlon(tm) II X4 645 Processor processors (4 cpu cores) (version 2.20.00)
[    1.736353] powernow-k8:    0 : pstate 0 (3100 MHz)
[    1.736354] powernow-k8:    1 : pstate 1 (2400 MHz)
[    1.736356] powernow-k8:    2 : pstate 2 (1900 MHz)
[    1.736357] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.737056] PM: Resume from disk failed.
[    1.737064] registered taskstats version 1
[    1.737308]   Magic number: 4:512:908
[    1.737333] mem port: hash matches
[    1.737396] rtc_cmos 00:03: setting system clock to 2012-03-10 23:51:34 UTC (1331423494)
[    1.737398] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.737398] EDD information not available.
[    1.737444] Freeing unused kernel memory: 884k freed
[    1.737629] Write protecting the kernel read-only data: 7716k
[    1.752877] udev: starting version 151
[    1.783688] ahci 0000:00:11.0: version 3.0
[    1.783712]   alloc irq_desc for 22 on node 0
[    1.783714]   alloc kstat_irqs on node 0
[    1.783721] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.783858] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.783861] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.785079] scsi0 : ahci
[    1.785364] scsi1 : ahci
[    1.785598] scsi2 : ahci
[    1.787112] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.787133] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.787174] r8169 0000:03:00.0: setting latency timer to 64
[    1.787178] r8169 0000:03:00.0: unknown MAC, using family default
[    1.787206]   alloc irq_desc for 26 on node 0
[    1.787207]   alloc kstat_irqs on node 0
[    1.787217] r8169 0000:03:00.0: irq 26 for MSI/MSI-X
[    1.787658] eth0: RTL8101e at 0xffffc90000c6a000, 2c:27:d7:21:64:37, XID 0c200000 IRQ 26
[    1.793045] scsi3 : ahci
[    1.793115] ata1: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 22
[    1.793118] ata2: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd80 irq 22
[    1.793121] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe00 irq 22
[    1.793124] ata4: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe80 irq 22
[    1.886129] usb 1-2: configuration #1 chosen from 1 choice
[    2.120069] usb 2-6: new high speed USB device using ehci_hcd and address 3
[    2.140086] ata2: SATA link down (SStatus 0 SControl 300)
[    2.140106] ata4: SATA link down (SStatus 0 SControl 300)
[    2.275180] usb 2-6: configuration #1 chosen from 1 choice
[    2.280048] Initializing USB Mass Storage driver...
[    2.280174] scsi4 : SCSI emulation for USB Mass Storage devices
[    2.280250] usb-storage: device found at 3
[    2.280253] usb-storage: waiting for device to settle before scanning
[    2.280257] usbcore: registered new interface driver usb-storage
[    2.280260] USB Mass Storage support registered.
[    2.320053] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.322552] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.324688] ata3.00: ATAPI: hp       CDDVDW TS-H653T, H6D1, max UDMA/100
[    2.324944] ata1.00: ATA-8: ST31000528AS, HP40, max UDMA/100
[    2.324947] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.326158] ata1.00: configured for UDMA/100
[    2.327056] ata3.00: configured for UDMA/100
[    2.342691] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     HP40 PQ: 0 ANSI: 5
[    2.342839] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.342920] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.342946] sd 0:0:0:0: [sda] Write Protect is off
[    2.342948] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.342959] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.343062]  sda:
[    2.343513] scsi 2:0:0:0: CD-ROM            hp       CDDVDW TS-H653T  H6D1 PQ: 0 ANSI: 5
[    2.348048] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.348051] Uniform CD-ROM driver Revision: 3.20
[    2.348145] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.348191] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.359937]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.403251] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.602540] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    2.791889] usb 4-1: configuration #1 chosen from 1 choice
[    2.800277] usbcore: registered new interface driver hiddev
[    2.803952] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input3
[    2.804020] generic-usb 0003:0461:4D16.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.1-1/input0
[    2.804040] usbcore: registered new interface driver usbhid
[    2.804042] usbhid: v2.6:USB HID core driver
[    2.911148] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    3.122537] usb 5-2: new low speed USB device using ohci_hcd and address 2
[    3.319828] usb 5-2: configuration #1 chosen from 1 choice
[    3.327914] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input4
[    3.327968] generic-usb 0003:04CA:003A.0002: input,hidraw1: USB HID v1.10 Keyboard [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:13.0-2/input0
[    3.338978] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.1/input/input5
[    3.339058] generic-usb 0003:04CA:003A.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:13.0-2/input1
[    7.280223] usb-storage: device scan complete
[    7.280800] scsi 4:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    7.281424] scsi 4:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    7.282049] scsi 4:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    7.282795] scsi 4:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    7.283133] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    7.283205] sd 4:0:0:1: Attached scsi generic sg3 type 0
[    7.283268] sd 4:0:0:2: Attached scsi generic sg4 type 0
[    7.283340] sd 4:0:0:3: Attached scsi generic sg5 type 0
[    7.287538] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.288287] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[    7.289038] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[    7.289664] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   11.478819] udev: starting version 151
[   11.506191] Adding 17190904k swap on /dev/sda6.  Priority:-1 extents:1 across:17190904k 
[   11.516747] lp: driver loaded but no devices found
[   11.528708] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.529127] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.558479] EDAC MC: Ver: 2.1.0 Jan  4 2012
[   11.602974] [drm] Initialized drm 1.1.0 20060810
[   11.603899] EDAC amd64_edac:  Ver: 3.2.0 Jan  4 2012
[   11.604325] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   11.604333] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   11.604334]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   11.604335]  (Note that use of the override may cause unknown side effects.)
[   11.604346] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   11.631176] type=1505 audit(1331445104.385:2):  operation="profile_load" pid=687 name="/sbin/dhclient3"
[   11.631367] type=1505 audit(1331445104.385:3):  operation="profile_load" pid=687 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.631475] type=1505 audit(1331445104.385:4):  operation="profile_load" pid=687 name="/usr/lib/connman/scripts/dhclient-script"
[   11.631705] [drm] radeon defaulting to kernel modesetting.
[   11.631708] [drm] radeon kernel modesetting enabled.
[   11.632534] type=1505 audit(1331445104.395:5):  operation="profile_replace" pid=732 name="/sbin/dhclient3"
[   11.632732] type=1505 audit(1331445104.395:6):  operation="profile_replace" pid=732 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.632844] type=1505 audit(1331445104.395:7):  operation="profile_replace" pid=732 name="/usr/lib/connman/scripts/dhclient-script"
[   11.634584] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.634589] radeon 0000:01:05.0: setting latency timer to 64
[   11.636899] [drm] radeon: Initializing kernel modesetting.
[   11.648981] [drm] register mmio base: 0xFE8F0000
[   11.648984] [drm] register mmio size: 65536
[   11.649652] ATOM BIOS: BR34448.005
[   11.649668] [drm] Clocks initialized !
[   11.649896] [drm] Detected VRAM RAM=256M, BAR=256M
[   11.649899] [drm] RAM width 32bits DDR
[   11.650982] [TTM] Zone  kernel: Available graphics memory: 2934194 kiB.
[   11.650984] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[   11.651003] [drm] radeon: 256M of VRAM memory ready
[   11.651004] [drm] radeon: 512M of GTT memory ready.
[   11.651038] [drm] radeon: irq initialized.
[   11.651040] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   11.651984] [drm] Loading RS780 Microcode
[   11.651988] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin
[   11.653388] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin
[   11.655038] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[   11.690326] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.690412] [drm] ring test succeeded in 1 usecs
[   11.690481] [drm] radeon: ib pool ready.
[   11.690528] [drm] ib test succeeded in 0 usecs
[   11.690530] [drm] Enabling audio support
[   11.690635] [drm] Radeon Display Connectors
[   11.690637] [drm] Connector 0:
[   11.690638] [drm]   VGA
[   11.690639] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   11.690641] [drm]   Encoders:
[   11.690642] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   11.690643] [drm] Connector 1:
[   11.690644] [drm]   DVI-D
[   11.690645] [drm]   HPD1
[   11.690646] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   11.690647] [drm]   Encoders:
[   11.690649] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[   11.743826] Disabling lock debugging due to kernel taint
[   11.748160] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.836478] [drm] fb mappable at 0xD0141000
[   11.836480] [drm] vram apper at 0xD0000000
[   11.836481] [drm] size 5760000
[   11.836482] [drm] fb depth is 24
[   11.836483] [drm]    pitch is 6400
[   11.836599] fb0: radeondrmfb frame buffer device
[   11.836600] registered panic notifier
[   11.836604] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   11.837874] vga16fb: initializing
[   11.837878] vga16fb: mapped to 0xffff8800000a0000
[   11.837883] vga16fb: not registering due to another framebuffer present
[   11.866183] hda_codec: ALC888: BIOS auto-probing.
[   11.867686] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   11.876419] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   11.876486] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   11.877019] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.877080] HDA Intel 0000:01:05.1: setting latency timer to 64
[   11.995339] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.000089] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.005147] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.009979] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.012833] Console: switching to colour frame buffer device 200x56
[   12.014773] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.019660] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.024848] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.030295] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.035267] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.040049] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.044973] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.049844] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.065646] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.097022] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.103835] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.111710] usb 1-2: reset high speed USB device using ehci_hcd and address 2
[   12.115563] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.121715] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.126761] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.131387] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.136999] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.141775] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.149220] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.155827] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.161361] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.167596] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.174955] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.181237] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.186388] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.191581] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.193434] type=1505 audit(1331445104.955:8):  operation="profile_load" pid=1170 name="/usr/share/gdm/guest-session/Xsession"
[   12.194949] type=1505 audit(1331445104.955:9):  operation="profile_replace" pid=1171 name="/sbin/dhclient3"
[   12.195157] type=1505 audit(1331445104.955:10):  operation="profile_replace" pid=1171 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.195270] type=1505 audit(1331445104.955:11):  operation="profile_replace" pid=1171 name="/usr/lib/connman/scripts/dhclient-script"
[   12.197824] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.205029] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.216803] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.222738] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.228063] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.233607] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.238627] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.244007] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.248899] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.253917] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.258847] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.263752] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.268478] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.273034] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.449446] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[   12.450563] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[   12.452992] BUG: unable to handle kernel paging request at 00000000ffffffd0
[   12.452997] IP: [<ffffffffa02b4ae9>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[   12.453017] PGD 183d75067 PUD 0 
[   12.453019] Oops: 0000 [#1] SMP 
[   12.453021] last sysfs file: /sys/kernel/uevent_seqnum
[   12.453023] CPU 3 
[   12.453024] Modules linked in: snd_hda_codec_atihdmi snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate ndiswrapper(+) snd_hda_intel snd_pcm_oss snd_hda_codec snd_mixer_oss snd_hwdep snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq radeon snd_timer ttm snd_seq_device drm_kms_helper snd joydev drm i2c_algo_bit psmouse serio_raw edac_core edac_mce_amd soundcore snd_page_alloc i2c_piix4 shpchp lp parport usbhid hid usb_storage r8169 mii ahci
[   12.453047] Pid: 653, comm: modprobe Tainted: P           2.6.32-38-generic #83-Ubuntu p7-1054
[   12.453049] RIP: 0010:[<ffffffffa02b4ae9>]  [<ffffffffa02b4ae9>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[   12.453063] RSP: 0018:ffff880183e6f720  EFLAGS: 00010286
[   12.453064] RAX: ffffffffa02b4ae0 RBX: ffff880182b0b000 RCX: ffff880199699100
[   12.453066] RDX: 0000000000000000 RSI: ffff8801963cb400 RDI: 00000000ffffff38
[   12.453067] RBP: ffff880183e6f720 R08: 0000000000000000 R09: ffff8801963cb400
[   12.453068] R10: ffffffffa02a67a0 R11: ffff8801963cb518 R12: ffff8801840f3800
[   12.453070] R13: 0000000000000000 R14: ffff8801834abe30 R15: 0000000000000000
[   12.453072] FS:  00007f5d1df49700(0000) GS:ffff8800282c0000(0000) knlGS:0000000000000000
[   12.453073] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   12.453074] CR2: 00000000ffffffd0 CR3: 0000000183d6d000 CR4: 00000000000006e0
[   12.453076] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   12.453077] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   12.453079] Process modprobe (pid: 653, threadinfo ffff880183e6e000, task ffff8801969d5bc0)
[   12.453080] Stack:
[   12.453081]  ffff8801963cb4d0 ffffc9001434cda8 ffff880182b0b000 ffff8801963cb4d0
[   12.453084] <0> ffff8801963cb400 ffff880183e6f768 ffffffffa02a22aa ffff8801834abe30
[   12.453086] <0> 0000000000000000 ffff880199699100 ffffffffa02b4c70 ffffffffa02b4c40
[   12.453088] Call Trace:
[   12.453100]  [<ffffffffa02a22aa>] ? NdisAllocateMemoryWithTag+0x1a/0x40 [ndiswrapper]
[   12.453112]  [<ffffffffa02b4c70>] ? USBD_InterfaceReference+0x0/0x30 [ndiswrapper]
[   12.453124]  [<ffffffffa02b4c40>] ? USBD_InterfaceDereference+0x0/0x30 [ndiswrapper]
[   12.453135]  [<ffffffffa02b4aa0>] ? USBD_InterfaceGetUSBDIVersion+0x0/0x40 [ndiswrapper]
[   12.453147]  [<ffffffffa02b51c0>] ? USBD_InterfaceQueryBusTime+0x0/0x30 [ndiswrapper]
[   12.453159]  [<ffffffffa02b4c10>] ? USBD_InterfaceSubmitIsoOutUrb+0x0/0x30 [ndiswrapper]
[   12.453171]  [<ffffffffa02b4be0>] ? USBD_InterfaceQueryBusInformation+0x0/0x30 [ndiswrapper]
[   12.453182]  [<ffffffffa02b4ae0>] ? USBD_InterfaceIsDeviceHighSpeed+0x0/0x20 [ndiswrapper]
[   12.453194]  [<ffffffffa02a752c>] ? ExAllocatePoolWithTag+0x3c/0x80 [ndiswrapper]
[   12.453206]  [<ffffffffa02b672b>] ? win2lin3+0x11/0x14 [ndiswrapper]
[   12.453210]  [<ffffffff8107679c>] ? lock_timer_base+0x3c/0x70
[   12.453222]  [<ffffffffa02b290f>] ? mp_init+0x6f/0x200 [ndiswrapper]
[   12.453234]  [<ffffffffa02accd2>] ? pdoDispatchPnp+0x42/0x100 [ndiswrapper]
[   12.453245]  [<ffffffffa02b3e5c>] ? ndis_start_device+0x2c/0x8b0 [ndiswrapper]
[   12.453257]  [<ffffffffa02a9dfd>] ? IofCallDriver+0x6d/0xd0 [ndiswrapper]
[   12.453260]  [<ffffffff81547b29>] ? _spin_unlock_bh+0x19/0x20
[   12.453271]  [<ffffffffa02a9dd1>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[   12.453283]  [<ffffffffa02aa3b6>] ? IoSyncForwardIrp+0x96/0xd0 [ndiswrapper]
[   12.453295]  [<ffffffffa02b4783>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
[   12.453306]  [<ffffffffa02b6717>] ? win2lin2+0xe/0x11 [ndiswrapper]
[   12.453317]  [<ffffffffa02a9dd1>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[   12.453329]  [<ffffffffa02a9dfd>] ? IofCallDriver+0x6d/0xd0 [ndiswrapper]
[   12.453331]  [<ffffffff81547b29>] ? _spin_unlock_bh+0x19/0x20
[   12.453342]  [<ffffffffa02a9dd1>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[   12.453353]  [<ffffffffa02abdad>] ? IoSendIrpTopDev+0xdd/0x130 [ndiswrapper]
[   12.453355]  [<ffffffff81547b29>] ? _spin_unlock_bh+0x19/0x20
[   12.453367]  [<ffffffffa02a9c18>] ? IoAttachDeviceToDeviceStack+0x68/0x80 [ndiswrapper]
[   12.453379]  [<ffffffffa02ac1ac>] ? pnp_start_device+0x4c/0x90 [ndiswrapper]
[   12.453390]  [<ffffffffa02ac479>] ? wrap_pnp_start_device+0xf9/0x180 [ndiswrapper]
[   12.453402]  [<ffffffffa02ac5f1>] ? wrap_pnp_start_usb_device+0xf1/0x120 [ndiswrapper]
[   12.453404]  [<ffffffff8154634e>] ? mutex_lock+0x1e/0x50
[   12.453407]  [<ffffffff813dcd74>] ? usb_autopm_do_device+0x84/0x130
[   12.453409]  [<ffffffff813dda75>] ? usb_probe_interface+0xe5/0x1d0
[   12.453412]  [<ffffffff8136cf95>] ? really_probe+0x65/0x170
[   12.453414]  [<ffffffff8136d0e5>] ? driver_probe_device+0x45/0x70
[   12.453416]  [<ffffffff8136d1ab>] ? __driver_attach+0x9b/0xa0
[   12.453418]  [<ffffffff8136d110>] ? __driver_attach+0x0/0xa0
[   12.453420]  [<ffffffff8136c3f8>] ? bus_for_each_dev+0x68/0x90
[   12.453422]  [<ffffffff8136ce0e>] ? driver_attach+0x1e/0x20
[   12.453423]  [<ffffffff8136c6ce>] ? bus_add_driver+0xde/0x280
[   12.453425]  [<ffffffff8136d4e0>] ? driver_register+0x80/0x150
[   12.453428]  [<ffffffff811af541>] ? sysfs_add_file+0x11/0x20
[   12.453431]  [<ffffffff813dd7a8>] ? usb_register_driver+0xb8/0x130
[   12.453439]  [<ffffffffa02d7000>] ? wrapper_init+0x0/0xb0 [ndiswrapper]
[   12.453449]  [<ffffffffa029de4f>] ? loader_init+0xcf/0x160 [ndiswrapper]
[   12.453457]  [<ffffffffa02d707b>] ? wrapper_init+0x7b/0xb0 [ndiswrapper]
[   12.453460]  [<ffffffff8100a04c>] ? do_one_initcall+0x3c/0x1a0
[   12.453464]  [<ffffffff810a159f>] ? sys_init_module+0xdf/0x260
[   12.453467]  [<ffffffff810121b2>] ? system_call_fastpath+0x16/0x1b
[   12.453468] Code: 00 00 83 79 1c 03 b9 10 01 00 00 0f 45 c1 89 46 04 c7 02 01 00 00 00 c9 c3 66 0f 1f 84 00 00 00 00 00 55 48 89 e5 0f 1f 44 00 00 <48> 8b 87 98 00 00 00 83 78 1c 03 c9 0f 94 c0 c3 0f 1f 80 00 00 
[   12.453485] RIP  [<ffffffffa02b4ae9>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[   12.453497]  RSP <ffff880183e6f720>
[   12.453498] CR2: 00000000ffffffd0
[   12.453500] ---[ end trace 2f8432e1ec286acd ]---
[   12.517189] r8169: eth0: link down
[   12.517932] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.646150] ppdev: user-space parallel port driver
[   12.925170] CPU0 attaching NULL sched-domain.
[   12.925177] CPU1 attaching NULL sched-domain.
[   12.925179] CPU2 attaching NULL sched-domain.
[   12.925180] CPU3 attaching NULL sched-domain.
[   13.001749] CPU0 attaching sched-domain:
[   13.001753]  domain 0: span 0-3 level MC
[   13.001754]   groups: 0 1 2 3
[   13.001760] CPU1 attaching sched-domain:
[   13.001761]  domain 0: span 0-3 level MC
[   13.001762]   groups: 1 2 3 0
[   13.001765] CPU2 attaching sched-domain:
[   13.001767]  domain 0: span 0-3 level MC
[   13.001768]   groups: 2 3 0 1
[   13.001770] CPU3 attaching sched-domain:
[   13.001771]  domain 0: span 0-3 level MC
[   13.001773]   groups: 3 0 1 2
[   14.906196] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   15.481102] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   15.540296] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  120.001440] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[  120.070589] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)

---

### Post by chili555 on 2012-03-11
This is not at all good:> [ 12.450563] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[ 12.452992] BUG: [COLOR="Red"]unable to handle kernel paging request[/COLOR] at 00000000ffffffd0
[ 12.452997] IP: [<ffffffffa02b4ae9>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[ 12.453017] PGD 183d75067 PUD 0
[ 12.453019] [COLOR="Red"]Oops[/COLOR]: 0000 [#1] SMP Here is what I suggest you do:```
sudo su
modprobe -rv ndiswrapper
ndiswrapper -e bcmwlhigh5.inf
rm -rf /etc/ndiswrapper/*
rm -rf Desktop/ndis_bcmwl
```Now download the attached file to your desktop. Right-click it and select *Extract Here*. Now, back to the terminal and do:```
cd Desktop/Broadcom_bcm43xx_USB_32_64bit_v2
ndiswrapper -i bcmn43xx64.inf
modprobe ndiswrapper
ndiswrapper -l
exit
```Any improvements? If not, please post:```
dmesg | grep ndis
```Thanks.

---

### Post by Skullxbagel on 2012-03-11
There's no response whenever I type in modprobe -rv ndiswrapper

---

### Post by Skullxbagel on 2012-03-11
chris@chris-desktop:~$ cd Desktop/Broadcom_bcm43xx_USB_32_64bit_v2
chris@chris-desktop:~/Desktop/Broadcom_bcm43xx_USB_32_64bit_v2$ ndiswrapper -l





it just stops, and doesn't do anything

---

### Post by Skullxbagel on 2012-03-11
chris@chris-desktop:~$ sudo su
root@chris-desktop:/home/chris# modprobe -rv ndiswrapper




just stops here too, i think modprobe is the thing messing everything up

---

### Post by Skullxbagel on 2012-03-11
the file installed but as you saw, it doesn't list it, it just freezes.

---

### Post by chili555 on 2012-03-11
Arrrgh!! Let's see if there are any messages:```
sudo cat /var/log/syslog | grep ndis | tail -n20
```

---

### Post by Skullxbagel on 2012-03-11
chris@chris-desktop:~$ sudo cat /var/log/syslog | grep ndis | tail -n20
[sudo] password for chris: 
Mar 11 06:55:40 chris-desktop kernel: [   11.628575] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar 11 06:55:40 chris-desktop kernel: [   12.159235] usbcore: registered new interface driver ndiswrapper
Mar 11 17:52:14 chris-desktop kernel: [   11.629609] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar 11 17:52:14 chris-desktop kernel: [   12.049169] usbcore: registered new interface driver ndiswrapper
chris@chris-desktop:~$ ^C
chris@chris-desktop:~$

---

### Post by chili555 on 2012-03-12
There is nothing significant there. Let's try the text file again. Please do:```
cd
dmesg > skull.txt
```Open your home directory. Click the column header at the top to sort the sort order by name. Scroll down among the S's to find 'skull.txt.' 

Then reply to this post and attach the file skull.txt as an attachment using the paperclip tool at the top of the reply box. Please see attached.

---

### Post by Skullxbagel on 2012-03-12
it says it exceeds the file size for .txt files so i'll just copy and paste.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-38-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 (Ubuntu 2.6.32-38.83-generic 2.6.32.52+drm33.21)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=abce0f3a-5ddf-48e3-96aa-8861eeb7d559 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a400 (usable)
[    0.000000]  BIOS-e820: 000000000009a400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001a0000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 00000001b0000000 aka 6912M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcffb0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009a400 (usable)
[    0.000000]  modified: 000000000009a400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  modified: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  modified: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000cffe0000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 00000001a0000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cffb0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cffb0000 page 4k
[    0.000000] kernel direct mapping tables up to cffb0000 @ 10000-13000
[    0.000000] init_memory_mapping: 0000000100000000-00000001a0000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0180000000 page 1G
[    0.000000]  0180000000 - 01a0000000 page 2M
[    0.000000] kernel direct mapping tables up to 1a0000000 @ 12000-14000
[    0.000000] RAMDISK: 377f3000 - 37fef09a
[    0.000000] ACPI: RSDP 00000000000fb050 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000cffb0100 0006C (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cffb0290 000F4 (v03 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20090903/tbfadt-557)
[    0.000000] ACPI: DSDT 00000000cffb05d0 04AB6 (v01 HPQOEM SLIC-CPC 00000504 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cffbe000 00040
[    0.000000] ACPI: APIC 00000000cffb0390 0007C (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cffb0410 0003C (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000cffb0450 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: OEMB 00000000cffbe040 00072 (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cffba6b0 00843 (v01 HPQOEM SLIC-CPC 00000001 INTL 20051117)
[    0.000000] ACPI: SRAT 00000000cffbaf00 000E8 (v03 HPQOEM SLIC-CPC 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 00000000cffbaff0 00038 (v01 HPQOEM SLIC-CPC 20110504 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cffbb030 0088C (v01 HPQOEM SLIC-CPC 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 1 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 2 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 3 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
[    0.000000] SRAT: Node 0 PXM 0 100000000-1b0000000
[    0.000000] NUMA: Allocated memnodemap from 13000 - 16640
[    0.000000] NUMA: Using 20 for the hash shift.
[    0.000000] Bootmem setup node 0 0000000000000000-00000001a0000000
[    0.000000]   NODE_DATA [0000000000016640 - 000000000001b63f]
[    0.000000]   bootmap [000000000001c000 -  000000000004ffff] pages 34
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 01a0000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a35ac4]    TEXT DATA BSS ==> [0001000000 - 0001a35ac4]
[    0.000000]   #3 [00377f3000 - 0037fef09a]          RAMDISK ==> [00377f3000 - 0037fef09a]
[    0.000000]   #4 [000009a400 - 0000100000]    BIOS reserved ==> [000009a400 - 0000100000]
[    0.000000]   #5 [0001a36000 - 0001a366a4]              BRK ==> [0001a36000 - 0001a366a4]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
[    0.000000]   #8 [0000013000 - 0000016640]       MEMNODEMAP ==> [0000013000 - 0000016640]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0005bfffff] PMD -> [ffff880028600000-ffff88002d7fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x001a0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000cffb0
[    0.000000]     0: 0x00100000 -> 0x001a0000
[    0.000000] On node 0 totalpages: 1507130
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 110 pages reserved
[    0.000000]   DMA zone: 3812 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833512 pages, LIFO batch:31
[    0.000000]   Normal zone: 8960 pages used for memmap
[    0.000000]   Normal zone: 646400 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cffb0000 - 00000000cffbe000
[    0.000000] PM: Registered nosave memory: 00000000cffbe000 - 00000000cffe0000
[    0.000000] PM: Registered nosave memory: 00000000cffe0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:2ff00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91608 r8192 d23080 u262144
[    0.000000] pcpu-alloc: s91608 r8192 d23080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1483724
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-38-generic root=UUID=abce0f3a-5ddf-48e3-96aa-8861eeb7d559 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ fd1c000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] Memory: 5859324k/6815744k available (5436k kernel code, 787224k absent, 169196k reserved, 2982k data, 884k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:456
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 60293120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3099.551 MHz processor.
[    0.030004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6199.09 BogoMIPS (lpj=30995470)
[    0.030022] Security Framework initialized
[    0.030035] AppArmor: AppArmor initialized
[    0.030499] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.033225] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.034490] Mount-cache hash table entries: 256
[    0.034589] Initializing cgroup subsys ns
[    0.034592] Initializing cgroup subsys cpuacct
[    0.034595] Initializing cgroup subsys memory
[    0.034601] Initializing cgroup subsys devices
[    0.034603] Initializing cgroup subsys freezer
[    0.034605] Initializing cgroup subsys net_cls
[    0.034620] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.034622] CPU: L2 Cache: 512K (64 bytes/line)
[    0.034624] CPU 0/0x0 -> Node 0
[    0.034627] tseg: 0000000000
[    0.034638] CPU: Physical Processor ID: 0
[    0.034639] CPU: Processor Core ID: 0
[    0.034641] mce: CPU supports 6 MCE banks
[    0.034649] Performance Events: AMD PMU driver.
[    0.034653] ... version:                0
[    0.034654] ... bit width:              48
[    0.034655] ... generic registers:      4
[    0.034656] ... value mask:             0000ffffffffffff
[    0.034658] ... max period:             00007fffffffffff
[    0.034659] ... fixed-purpose events:   0
[    0.034660] ... event mask:             000000000000000f
[    0.035830] ACPI: Core revision 20090903
[    0.050005] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.050009] ftrace: allocating 22567 entries in 89 pages
[    0.054762] Setting APIC routing to flat
[    0.055057] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.156250] CPU0: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.040000] Initializing CPU#1
[    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.040000] CPU 1/0x1 -> Node 0
[    0.040000] CPU: Physical Processor ID: 0
[    0.040000] CPU: Processor Core ID: 1
[    0.310025] CPU1: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.310031] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320056] Booting processor 2 APIC 0x2 ip 0x6000
[    0.040000] Initializing CPU#2
[    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.040000] CPU 2/0x2 -> Node 0
[    0.040000] CPU: Physical Processor ID: 0
[    0.040000] CPU: Processor Core ID: 2
[    0.480081] CPU2: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.480086] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.490049] Booting processor 3 APIC 0x3 ip 0x6000
[    0.040000] Initializing CPU#3
[    0.040000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.040000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.040000] CPU 3/0x3 -> Node 0
[    0.040000] CPU: Physical Processor ID: 0
[    0.040000] CPU: Processor Core ID: 3
[    0.650029] CPU3: AMD Athlon(tm) II X4 645 Processor stepping 03
[    0.650037] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.660013] Brought up 4 CPUs
[    0.660015] Total of 4 processors activated (24799.17 BogoMIPS).
[    0.660396] CPU0 attaching sched-domain:
[    0.660400]  domain 0: span 0-3 level MC
[    0.660402]   groups: 0 1 2 3
[    0.660406] CPU1 attaching sched-domain:
[    0.660408]  domain 0: span 0-3 level MC
[    0.660409]   groups: 1 2 3 0
[    0.660412] CPU2 attaching sched-domain:
[    0.660413]  domain 0: span 0-3 level MC
[    0.660414]   groups: 2 3 0 1
[    0.660417] CPU3 attaching sched-domain:
[    0.660418]  domain 0: span 0-3 level MC
[    0.660419]   groups: 3 0 1 2
[    0.660496] devtmpfs: initialized
[    0.660496] regulator: core version 0.5
[    0.660496] Time:  3:38:20  Date: 03/12/12
[    0.660496] NET: Registered protocol family 16
[    0.660496] node 0 link 0: io port [1000, ffffff]
[    0.660496] TOM: 00000000d0000000 aka 3328M
[    0.660496] Fam 10h mmconf [e0000000, efffffff]
[    0.660496] node 0 link 0: mmio [a0000, bffff]
[    0.660496] node 0 link 0: mmio [d0000000, efffffff] ==> [d0000000, dfffffff]
[    0.660496] node 0 link 0: mmio [f0000000, fe7fffff]
[    0.660496] node 0 link 0: mmio [fe800000, fe9fffff]
[    0.660496] node 0 link 0: mmio [fea00000, ffefffff]
[    0.660496] TOM2: 00000001b0000000 aka 6912M
[    0.660496] bus: [00,07] on node 0 link 0
[    0.660496] bus: 00 index 0 io port: [0, ffff]
[    0.660496] bus: 00 index 1 mmio: [a0000, bffff]
[    0.660496] bus: 00 index 2 mmio: [d0000000, dfffffff]
[    0.660496] bus: 00 index 3 mmio: [f0000000, ffffffff]
[    0.660496] bus: 00 index 4 mmio: [1b0000000, fcffffffff]
[    0.660496] ACPI: bus type pci registered
[    0.660496] Trying to unpack rootfs image as initramfs...
[    0.660496] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.660496] PCI: Not using MMCONFIG.
[    0.660496] PCI: Using configuration type 1 for base access
[    0.660496] PCI: Using configuration type 1 for extended access
[    0.660653] bio: create slab <bio-0> at 0
[    0.660653] ACPI: EC: Look up EC in DSDT
[    0.660827] ACPI Error (psargs-0359): [ECEN] Namespace lookup failure, AE_NOT_FOUND
[    0.660831] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node ffffffff81a14080), AE_NOT_FOUND
[    0.660936] ACPI: Executed 3 blocks of module-level executable AML code
[    0.664609] ACPI: Interpreter enabled
[    0.664612] ACPI: (supports S0 S1 S3 S4 S5)
[    0.664627] ACPI: Using IOAPIC for interrupt routing
[    0.664661] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.665992] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.673504] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.676714] ACPI: No dock devices found.
[    0.676825] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.676931] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.676934] pci 0000:00:05.0: PME# disabled
[    0.676967] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.676969] pci 0000:00:0a.0: PME# disabled
[    0.677014] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.677020] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.677026] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.677032] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.677038] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.677044] pci 0000:00:11.0: reg 24 32bit mmio: [0xfe7ffc00-0xfe7fffff]
[    0.677091] pci 0000:00:12.0: reg 10 32bit mmio: [0xfe7fe000-0xfe7fefff]
[    0.677141] pci 0000:00:12.1: reg 10 32bit mmio: [0xfe7fd000-0xfe7fdfff]
[    0.677207] pci 0000:00:12.2: reg 10 32bit mmio: [0xfe7ff800-0xfe7ff8ff]
[    0.677253] pci 0000:00:12.2: supports D1 D2
[    0.677255] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.677258] pci 0000:00:12.2: PME# disabled
[    0.677287] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe7fc000-0xfe7fcfff]
[    0.677336] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe7f7000-0xfe7f7fff]
[    0.677403] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe7ff400-0xfe7ff4ff]
[    0.677449] pci 0000:00:13.2: supports D1 D2
[    0.677451] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.677454] pci 0000:00:13.2: PME# disabled
[    0.677565] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe7f0000-0xfe7f3fff]
[    0.677604] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.677607] pci 0000:00:14.2: PME# disabled
[    0.677774] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.677777] pci 0000:01:05.0: reg 14 io port: [0xd000-0xd0ff]
[    0.677780] pci 0000:01:05.0: reg 18 32bit mmio: [0xfe8f0000-0xfe8fffff]
[    0.677786] pci 0000:01:05.0: reg 24 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.677795] pci 0000:01:05.0: supports D1 D2
[    0.677810] pci 0000:01:05.1: reg 10 32bit mmio: [0xfe8e8000-0xfe8ebfff]
[    0.677825] pci 0000:01:05.1: supports D1 D2
[    0.677861] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.677863] pci 0000:00:01.0: bridge 32bit mmio: [0xfe800000-0xfe9fffff]
[    0.677866] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.677896] pci 0000:02:00.0: reg 10 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.677986] pci 0000:00:05.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.678018] pci 0000:03:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.678031] pci 0000:03:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.678040] pci 0000:03:00.0: reg 20 64bit mmio pref: [0xfdffc000-0xfdffffff]
[    0.678070] pci 0000:03:00.0: supports D1 D2
[    0.678072] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.678075] pci 0000:03:00.0: PME# disabled
[    0.678131] pci 0000:00:0a.0: bridge io port: [0xe000-0xefff]
[    0.678134] pci 0000:00:0a.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.678137] pci 0000:00:0a.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.678189] pci 0000:00:14.4: transparent bridge
[    0.678208] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.678322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.678362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.678400] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.681102] ACPI: PCI Interrupt Link [LNKA] (IRQs *4 7 10 11 12 14 15)
[    0.681168] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.681230] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 *11 12 14 15)
[    0.681291] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.681353] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.681415] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.681480] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *7 10 11 12 14 15)
[    0.681542] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.681615] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.681618] vgaarb: loaded
[    0.681693] SCSI subsystem initialized
[    0.681714] libata version 3.00 loaded.
[    0.681714] usbcore: registered new interface driver usbfs
[    0.681714] usbcore: registered new interface driver hub
[    0.681714] usbcore: registered new device driver usb
[    0.681714] ACPI: WMI: Mapper loaded
[    0.681714] PCI: Using ACPI for IRQ routing
[    0.681714] NetLabel: Initializing
[    0.681714] NetLabel:  domain hash size = 128
[    0.681714] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.681714] NetLabel:  unlabeled traffic allowed by default
[    0.681714] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.681714] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.682298] Switching to clocksource tsc
[    0.684846] AppArmor: AppArmor Filesystem Enabled
[    0.684846] pnp: PnP ACPI init
[    0.684846] ACPI: bus type pnp registered
[    0.684846] pnp: PnP ACPI: found 12 devices
[    0.684846] ACPI: ACPI bus type pnp unregistered
[    0.684846] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.684846] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.684846] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.684846] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.684846] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.684846] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.684846] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.684846] system 00:08: ioport range 0xc50-0xc51 has been reserved
[    0.684846] system 00:08: ioport range 0xc52-0xc52 has been reserved
[    0.684846] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.684846] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.684846] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[    0.684846] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[    0.684846] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.684846] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.684846] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.684846] system 00:08: ioport range 0x800-0x89f has been reserved
[    0.684846] system 00:08: ioport range 0xb00-0xb0f has been reserved
[    0.684846] system 00:08: ioport range 0xb20-0xb3f has been reserved
[    0.684846] system 00:08: ioport range 0x900-0x90f has been reserved
[    0.684846] system 00:08: ioport range 0x910-0x91f has been reserved
[    0.684846] system 00:08: ioport range 0xfe00-0xfefe has been reserved
[    0.684846] system 00:08: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.684846] system 00:08: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.684846] system 00:09: ioport range 0xe00-0xe0f has been reserved
[    0.684846] system 00:09: ioport range 0xe80-0xe8f has been reserved
[    0.684846] system 00:09: ioport range 0xf40-0xf4f has been reserved
[    0.684846] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.684846] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.684846] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.684846] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.684846] system 00:0b: iomem range 0x100000-0xcfffffff could not be reserved
[    0.684846] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.687407] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.687409] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.687412] pci 0000:00:01.0:   MEM window: 0xfe800000-0xfe9fffff
[    0.687414] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.687417] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
[    0.687419] pci 0000:00:05.0:   IO window: disabled
[    0.687421] pci 0000:00:05.0:   MEM window: 0xfea00000-0xfeafffff
[    0.687423] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.687426] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:03
[    0.687428] pci 0000:00:0a.0:   IO window: 0xe000-0xefff
[    0.687430] pci 0000:00:0a.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.687432] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.687435] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04
[    0.687437] pci 0000:00:14.4:   IO window: disabled
[    0.687441] pci 0000:00:14.4:   MEM window: disabled
[    0.687444] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.687457]   alloc irq_desc for 17 on node 0
[    0.687458]   alloc kstat_irqs on node 0
[    0.687462] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.687464] pci 0000:00:05.0: setting latency timer to 64
[    0.687469]   alloc irq_desc for 18 on node 0
[    0.687470]   alloc kstat_irqs on node 0
[    0.687472] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.687474] pci 0000:00:0a.0: setting latency timer to 64
[    0.687481] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.687483] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.687485] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.687486] pci_bus 0000:01: resource 1 mem: [0xfe800000-0xfe9fffff]
[    0.687488] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.687490] pci_bus 0000:02: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.687492] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.687494] pci_bus 0000:03: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.687495] pci_bus 0000:03: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.687497] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.687499] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.687527] NET: Registered protocol family 2
[    0.687694] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.688887] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.691693] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.692048] TCP: Hash tables configured (established 524288 bind 65536)
[    0.692051] TCP reno registered
[    0.692139] NET: Registered protocol family 1
[    1.455438] pci 0000:01:05.0: Boot video device
[    1.456138] PCI-DMA: Disabling AGP.
[    1.456220] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    1.456222] PCI-DMA: using GART IOMMU.
[    1.456224] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.457454] Scanning for low memory corruption every 60 seconds
[    1.457544] audit: initializing netlink socket (disabled)
[    1.457559] type=2000 audit(1331523500.455:1): initialized
[    1.463555] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.464507] VFS: Disk quotas dquot_6.5.2
[    1.464549] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.465021] fuse init (API version 7.13)
[    1.465081] msgmni has been set to 11443
[    1.465509] alg: No test for stdrng (krng)
[    1.465586] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.465592] io scheduler noop registered
[    1.465594] io scheduler anticipatory registered
[    1.465596] io scheduler deadline registered
[    1.465638] io scheduler cfq registered (default)
[    1.465866]   alloc irq_desc for 24 on node 0
[    1.465869]   alloc kstat_irqs on node 0
[    1.465876] pcieport 0000:00:05.0: irq 24 for MSI/MSI-X
[    1.465880] pcieport 0000:00:05.0: setting latency timer to 64
[    1.466064]   alloc irq_desc for 25 on node 0
[    1.466067]   alloc kstat_irqs on node 0
[    1.466078] pcieport 0000:00:0a.0: irq 25 for MSI/MSI-X
[    1.466082] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.466179] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.466196] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.466269] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.466279] ACPI: Power Button [PWRB]
[    1.466308] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.466310] ACPI: Power Button [PWRF]
[    1.466579] processor LNXCPU:00: registered as cooling_device0
[    1.466617] processor LNXCPU:01: registered as cooling_device1
[    1.466639] processor LNXCPU:02: registered as cooling_device2
[    1.466658] processor LNXCPU:03: registered as cooling_device3
[    1.468067] Linux agpgart interface v0.103
[    1.468095] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.468813] brd: module loaded
[    1.469086] loop: module loaded
[    1.469152] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.469405] Fixed MDIO Bus: probed
[    1.469425] PPP generic driver version 2.4.2
[    1.469444] tun: Universal TUN/TAP device driver, 1.6
[    1.469445] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.469491] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.469592] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.469621] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.469640] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.469673] ehci_hcd 0000:00:12.2: debug port 1
[    1.469693] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe7ff800
[    1.470514] Freeing initrd memory: 8176k freed
[    1.485385] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.485487] usb usb1: configuration #1 chosen from 1 choice
[    1.485506] hub 1-0:1.0: USB hub found
[    1.485511] hub 1-0:1.0: 6 ports detected
[    1.485649]   alloc irq_desc for 19 on node 0
[    1.485651]   alloc kstat_irqs on node 0
[    1.485656] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.485675] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.485711] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.485737] ehci_hcd 0000:00:13.2: debug port 1
[    1.485754] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe7ff400
[    1.505391] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.505492] usb usb2: configuration #1 chosen from 1 choice
[    1.505510] hub 2-0:1.0: USB hub found
[    1.505515] hub 2-0:1.0: 6 ports detected
[    1.505592] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.505696]   alloc irq_desc for 16 on node 0
[    1.505699]   alloc kstat_irqs on node 0
[    1.505705] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.505725] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.505782] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.505806] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe7fe000
[    1.569486] usb usb3: configuration #1 chosen from 1 choice
[    1.569508] hub 3-0:1.0: USB hub found
[    1.569520] hub 3-0:1.0: 3 ports detected
[    1.569650] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.569669] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.569707] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.569724] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe7fd000
[    1.629507] usb usb4: configuration #1 chosen from 1 choice
[    1.629528] hub 4-0:1.0: USB hub found
[    1.629540] hub 4-0:1.0: 3 ports detected
[    1.629670] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.629691] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.629724] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.629751] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe7fc000
[    1.689545] usb usb5: configuration #1 chosen from 1 choice
[    1.689562] hub 5-0:1.0: USB hub found
[    1.689573] hub 5-0:1.0: 3 ports detected
[    1.689709] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.689728] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.689763] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.689784] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe7f7000
[    1.744130] usb usb6: configuration #1 chosen from 1 choice
[    1.744148] hub 6-0:1.0: USB hub found
[    1.744159] hub 6-0:1.0: 3 ports detected
[    1.744236] uhci_hcd: USB Universal Host Controller Interface driver
[    1.744299] PNP: No PS/2 controller found. Probing ports directly.
[    1.744685] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.744697] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.744789] mice: PS/2 mouse device common for all mice
[    1.744859] rtc_cmos 00:03: RTC can wake from S4
[    1.744886] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.744908] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.744994] device-mapper: uevent: version 1.0.3
[    1.745125] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.745314] device-mapper: multipath: version 1.1.0 loaded
[    1.745317] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.745510] cpuidle: using governor ladder
[    1.745511] cpuidle: using governor menu
[    1.745746] TCP cubic registered
[    1.745836] NET: Registered protocol family 10
[    1.746298] NET: Registered protocol family 17
[    1.746356] powernow-k8: Found 1 AMD Athlon(tm) II X4 645 Processor processors (4 cpu cores) (version 2.20.00)
[    1.746389] powernow-k8:    0 : pstate 0 (3100 MHz)
[    1.746390] powernow-k8:    1 : pstate 1 (2400 MHz)
[    1.746391] powernow-k8:    2 : pstate 2 (1900 MHz)
[    1.746392] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.747095] PM: Resume from disk failed.
[    1.747104] registered taskstats version 1
[    1.747347]   Magic number: 4:777:613
[    1.747377] pcieport 0000:00:0a.0: hash matches
[    1.747435] rtc_cmos 00:03: setting system clock to 2012-03-12 03:38:21 UTC (1331523501)
[    1.747437] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.747438] EDD information not available.
[    1.747481] Freeing unused kernel memory: 884k freed
[    1.747667] Write protecting the kernel read-only data: 7716k
[    1.762908] udev: starting version 151
[    1.790665] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.790688] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.790738] r8169 0000:03:00.0: setting latency timer to 64
[    1.790742] r8169 0000:03:00.0: unknown MAC, using family default
[    1.790771]   alloc irq_desc for 26 on node 0
[    1.790773]   alloc kstat_irqs on node 0
[    1.790783] r8169 0000:03:00.0: irq 26 for MSI/MSI-X
[    1.791186] eth0: RTL8101e at 0xffffc90000c6e000, 2c:27:d7:21:64:37, XID 0c200000 IRQ 26
[    1.800477] ahci 0000:00:11.0: version 3.0
[    1.800500]   alloc irq_desc for 22 on node 0
[    1.800502]   alloc kstat_irqs on node 0
[    1.800508] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.800623] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.800625] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.801080] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.806256] scsi0 : ahci
[    1.806444] scsi1 : ahci
[    1.806573] scsi2 : ahci
[    1.806706] scsi3 : ahci
[    1.806771] ata1: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd00 irq 22
[    1.806774] ata2: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffd80 irq 22
[    1.806778] ata3: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe00 irq 22
[    1.806780] ata4: SATA max UDMA/133 abar m1024@0xfe7ffc00 port 0xfe7ffe80 irq 22
[    1.953803] usb 1-1: configuration #1 chosen from 1 choice
[    1.958709] Initializing USB Mass Storage driver...
[    1.958862] scsi4 : SCSI emulation for USB Mass Storage devices
[    1.959010] usb-storage: device found at 2
[    1.959012] usb-storage: waiting for device to settle before scanning
[    1.959030] usbcore: registered new interface driver usb-storage
[    1.959033] USB Mass Storage support registered.
[    2.072547] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    2.150069] ata2: SATA link down (SStatus 0 SControl 300)
[    2.150074] ata4: SATA link down (SStatus 0 SControl 300)
[    2.226293] usb 1-2: configuration #1 chosen from 1 choice
[    2.332550] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.332575] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.333576] ata1.00: ATA-8: ST31000528AS, HP40, max UDMA/100
[    2.333579] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.334729] ata3.00: ATAPI: hp       CDDVDW TS-H653T, H6D1, max UDMA/100
[    2.334777] ata1.00: configured for UDMA/100
[    2.337090] ata3.00: configured for UDMA/100
[    2.352709] scsi 0:0:0:0: Direct-Access     ATA      ST31000528AS     HP40 PQ: 0 ANSI: 5
[    2.352855] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.352921] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.352945] sd 0:0:0:0: [sda] Write Protect is off
[    2.352947] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.352961] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.353071]  sda:
[    2.353538] scsi 2:0:0:0: CD-ROM            hp       CDDVDW TS-H653T  H6D1 PQ: 0 ANSI: 5
[    2.358070] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.358073] Uniform CD-ROM driver Revision: 3.20
[    2.358166] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.358218] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.370125]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.413449] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.462544] usb 2-6: new high speed USB device using ehci_hcd and address 3
[    2.615347] usb 2-6: configuration #1 chosen from 1 choice
[    2.615677] scsi5 : SCSI emulation for USB Mass Storage devices
[    2.615766] usb-storage: device found at 3
[    2.615767] usb-storage: waiting for device to settle before scanning
[    2.888196] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.950037] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    3.131803] usb 4-1: configuration #1 chosen from 1 choice
[    3.450046] usb 5-2: new low speed USB device using ohci_hcd and address 2
[    3.670800] usb 5-2: configuration #1 chosen from 1 choice
[    6.950315] usb-storage: device scan complete
[    6.950762] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer Slice     1.02 PQ: 0 ANSI: 2
[    6.951180] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    6.952516] sd 4:0:0:0: [sdb] 7813120 512-byte logical blocks: (4.00 GB/3.72 GiB)
[    6.954012] sd 4:0:0:0: [sdb] Write Protect is off
[    6.954016] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    6.954018] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.956390] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.956394]  sdb: sdb1
[    6.958760] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    6.958764] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    7.610360] usb-storage: device scan complete
[    7.610940] scsi 5:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    7.611564] scsi 5:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    7.612191] scsi 5:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    7.612939] scsi 5:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    7.613273] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    7.613343] sd 5:0:0:1: Attached scsi generic sg4 type 0
[    7.613415] sd 5:0:0:2: Attached scsi generic sg5 type 0
[    7.613482] sd 5:0:0:3: Attached scsi generic sg6 type 0
[    7.617804] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    7.618554] sd 5:0:0:1: [sdd] Attached SCSI removable disk
[    7.619313] sd 5:0:0:2: [sde] Attached SCSI removable disk
[    7.619929] sd 5:0:0:3: [sdf] Attached SCSI removable disk
[   11.499456] udev: starting version 151
[   11.514996] lp: driver loaded but no devices found
[   11.516103] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.525495] Adding 17190904k swap on /dev/sda6.  Priority:-1 extents:1 across:17190904k 
[   11.562940] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.611155] EDAC MC: Ver: 2.1.0 Jan  4 2012
[   11.612243] [drm] Initialized drm 1.1.0 20060810
[   11.618799] type=1505 audit(1331541511.365:2):  operation="profile_load" pid=663 name="/sbin/dhclient3"
[   11.618988] type=1505 audit(1331541511.365:3):  operation="profile_load" pid=663 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.619096] type=1505 audit(1331541511.365:4):  operation="profile_load" pid=663 name="/usr/lib/connman/scripts/dhclient-script"
[   11.620259] type=1505 audit(1331541511.365:5):  operation="profile_replace" pid=688 name="/sbin/dhclient3"
[   11.620532] type=1505 audit(1331541511.365:6):  operation="profile_replace" pid=688 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   11.620660] type=1505 audit(1331541511.365:7):  operation="profile_replace" pid=688 name="/usr/lib/connman/scripts/dhclient-script"
[   11.630658] usbcore: registered new interface driver hiddev
[   11.634821] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input3
[   11.634908] generic-usb 0003:0461:4D16.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.1-1/input0
[   11.637293] EDAC amd64_edac:  Ver: 3.2.0 Jan  4 2012
[   11.639834] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input4
[   11.639957] generic-usb 0003:04CA:003A.0002: input,hidraw1: USB HID v1.10 Keyboard [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:13.0-2/input0
[   11.650434] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   11.650452] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   11.650453]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   11.650454]  (Note that use of the override may cause unknown side effects.)
[   11.650483] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   11.650824] input: Lite-On Technology Corp. USB Multimedia Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.1/input/input5
[   11.650939] generic-usb 0003:04CA:003A.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [Lite-On Technology Corp. USB Multimedia Keyboard] on usb-0000:00:13.0-2/input1
[   11.650968] usbcore: registered new interface driver usbhid
[   11.650970] usbhid: v2.6:USB HID core driver
[   11.651019] [drm] radeon defaulting to kernel modesetting.
[   11.651020] [drm] radeon kernel modesetting enabled.
[   11.651102] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.651106] radeon 0000:01:05.0: setting latency timer to 64
[   11.653145] [drm] radeon: Initializing kernel modesetting.
[   11.667683] [drm] register mmio base: 0xFE8F0000
[   11.667686] [drm] register mmio size: 65536
[   11.668287] ATOM BIOS: BR34448.005
[   11.668300] [drm] Clocks initialized !
[   11.668531] [drm] Detected VRAM RAM=256M, BAR=256M
[   11.668535] [drm] RAM width 32bits DDR
[   11.669573] [TTM] Zone  kernel: Available graphics memory: 2934194 kiB.
[   11.669575] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[   11.669592] [drm] radeon: 256M of VRAM memory ready
[   11.669594] [drm] radeon: 512M of GTT memory ready.
[   11.669621] [drm] radeon: irq initialized.
[   11.669623] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   11.670489] [drm] Loading RS780 Microcode
[   11.670493] platform radeon_cp.0: firmware: requesting radeon/RS780_pfp.bin
[   11.672231] platform radeon_cp.0: firmware: requesting radeon/RS780_me.bin
[   11.674063] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[   11.708824] [drm] ring test succeeded in 1 usecs
[   11.708915] [drm] radeon: ib pool ready.
[   11.708964] [drm] ib test succeeded in 0 usecs
[   11.708966] [drm] Enabling audio support
[   11.709065] [drm] Radeon Display Connectors
[   11.709067] [drm] Connector 0:
[   11.709068] [drm]   VGA
[   11.709069] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   11.709071] [drm]   Encoders:
[   11.709072] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   11.709073] [drm] Connector 1:
[   11.709074] [drm]   DVI-D
[   11.709074] [drm]   HPD1
[   11.709076] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   11.709077] [drm]   Encoders:
[   11.709078] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[   11.773645] Disabling lock debugging due to kernel taint
[   11.778007] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   11.853836] [drm] fb mappable at 0xD0141000
[   11.853838] [drm] vram apper at 0xD0000000
[   11.853839] [drm] size 5760000
[   11.853840] [drm] fb depth is 24
[   11.853841] [drm]    pitch is 6400
[   11.853925] fb0: radeondrmfb frame buffer device
[   11.853926] registered panic notifier
[   11.853930] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0
[   11.855135] vga16fb: initializing
[   11.855139] vga16fb: mapped to 0xffff8800000a0000
[   11.855144] vga16fb: not registering due to another framebuffer present
[   11.945319] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.023989] Console: switching to colour frame buffer device 200x56
[   12.220457] hda_codec: ALC888: BIOS auto-probing.
[   12.221937] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[   12.233123] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.233180] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.233498] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.233536] HDA Intel 0000:01:05.1: setting latency timer to 64
[   12.329974] type=1505 audit(1331541512.072:8):  operation="profile_replace" pid=986 name="/sbin/dhclient3"
[   12.330175] type=1505 audit(1331541512.082:9):  operation="profile_replace" pid=986 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.330290] type=1505 audit(1331541512.082:10):  operation="profile_replace" pid=986 name="/usr/lib/connman/scripts/dhclient-script"
[   12.331691] type=1505 audit(1331541512.082:11):  operation="profile_load" pid=991 name="/usr/lib/cups/backend/cups-pdf"
[   12.343443] usbcore: registered new interface driver ndiswrapper
[   12.349476] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.354441] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.359200] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.363899] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.368316] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.372877] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.377266] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.381898] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.386352] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.390835] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.397246] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.402046] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.406795] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.411633] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.416318] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.421264] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.425950] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.430931] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.438616] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.446936] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.452263] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.457094] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.462074] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.466844] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.471713] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.476404] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.479997] r8169: eth0: link down
[   12.480907] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.481365] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.486238] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.491062] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.495864] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.500653] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.506263] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.511148] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.516384] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.522661] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.529523] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.534914] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.540799] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.550245] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.555846] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.560992] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.566829] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.573275] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   12.634131] ppdev: user-space parallel port driver
[   12.923016] CPU0 attaching NULL sched-domain.
[   12.923022] CPU1 attaching NULL sched-domain.
[   12.923024] CPU2 attaching NULL sched-domain.
[   12.923025] CPU3 attaching NULL sched-domain.
[   13.002576] CPU0 attaching sched-domain:
[   13.002579]  domain 0: span 0-3 level MC
[   13.002581]   groups: 0 1 2 3
[   13.002585] CPU1 attaching sched-domain:
[   13.002586]  domain 0: span 0-3 level MC
[   13.002588]   groups: 1 2 3 0
[   13.002591] CPU2 attaching sched-domain:
[   13.002592]  domain 0: span 0-3 level MC
[   13.002593]   groups: 2 3 0 1
[   13.002596] CPU3 attaching sched-domain:
[   13.002597]  domain 0: span 0-3 level MC
[   13.002598]   groups: 3 0 1 2
[   14.075506] CPU0 attaching NULL sched-domain.
[   14.075515] CPU1 attaching NULL sched-domain.
[   14.075517] CPU2 attaching NULL sched-domain.
[   14.075519] CPU3 attaching NULL sched-domain.
[   14.150109] CPU0 attaching sched-domain:
[   14.150112]  domain 0: span 0-3 level MC
[   14.150114]   groups: 0 1 2 3
[   14.150118] CPU1 attaching sched-domain:
[   14.150120]  domain 0: span 0-3 level MC
[   14.150121]   groups: 1 2 3 0
[   14.150124] CPU2 attaching sched-domain:
[   14.150125]  domain 0: span 0-3 level MC
[   14.150126]   groups: 2 3 0 1
[   14.150129] CPU3 attaching sched-domain:
[   14.150130]  domain 0: span 0-3 level MC
[   14.150131]   groups: 3 0 1 2
[   14.947759] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   15.580311] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   15.621138] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   25.030300] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)
[   25.081957] hda_codec: num_steps = 0 for NID=0xc (ctl = Front Playback Volume)

```

---

### Post by Skullxbagel on 2012-03-12
Also, logging in seems to be faster now, and terminal doesn't take a hour. Just letting you know.

---

### Post by chili555 on 2012-03-12
I don't see one thing wrong. Was the device inserted at the time you booted? If not, we're not going to get much information about the device, the driver, ndiswrapper and your computer.

---

### Post by Skullxbagel on 2012-03-12
Yes, it's always plugged in, I use in windows as well

---

### Post by Skullxbagel on 2012-03-12
The lag and slowness seems to have stopped maybe it fixed itself

---

### Post by Skullxbagel on 2012-03-12
Just to let you know whenever I do ndiswrapper -l it says bcmn43xx64 : driver installed

---

### Post by Skullxbagel on 2012-03-12
So now thA it works now what?

---

### Post by flash63 on 2012-03-13
Hello,
some limitations with this driver / Stick
* 5GHz band does not work
* N-mode in the 2.4 GHz band at 40MHz bandwidth does not work in most cases

Switch your Router settings to
 * b/g or g-Mode ...
 * witch 20MHz bandwith
 * use a fixed radio channel between 1-11
 * use pure WPA2-AES encryption, no mixed mode WPA1/2

check the function:
```
sudo modprobe ndiswrapper
dmesg | egrep 'ndis|wlan'
iwconfig
iwlist chan
sudo iwlist scan      # mark your own Cell
```
try to connect if the interface is displayed and your own network was found

---

### Post by Skullxbagel on 2012-03-13
Some of these might be stupid questions but ill ask anyway. Do I have to change these things in windows, because I have no control of its settings in Linux. Also I can't find just a wpa2 aes security setting option in the network connections. And also, would I have to access my router through windows as well? Would change the MHz or GHz affect my other computers?

---

### Post by Skullxbagel on 2012-03-13
Also, in windows this adapter has an interface to connect to the Internet, is that supposed to show up in Linux as well?

---

### Post by flash63 on 2012-03-13
> **Skullxbagel said:**
> Some of these might be stupid questions but ill ask anyway. Do I have to change these things in windows, because I have no control of its settings in Linux. Also I can't find just a wpa2 aes security setting option in the network connections. And also, would I have to access my router through windows as well? Would change the MHz or GHz affect my other computers?

These are standard settings of your router to work with any current wireless cards. You have to call up the settings menu (WEB-Interface) of the router to change these settings!

It is recommended (better) to use a cable connection for this.

---

### Post by Skullxbagel on 2012-03-13
Yes, i would if i could, but i am on the second floor of my house whereas the router is on the first floor.

---

### Post by flash63 on 2012-03-13
Ok, is there no chance to connect via Laptop and cable  to the router?

If you change the settings of the router over WLAN, you lost the connection as well under Windows for a short time.

If all goes well, the connection automatically renewed, but if not &#8222;Houston we have a problem&#8220;.

First show us the output of
```
sudo modprobe ndiswrapper
dmesg | egrep 'ndis|wlan' > wlan_info1.txt
iwconfig >> wlan_info1.txt
iwlist chan >> wlan_info1.txt
sudo iwlist scan >> wlan_info1.txt     # mark your own Cell
```

The output will be redirected to a text file wlan_info1.txt in your home-folder and can be copied and attached here by using Windows.

---

### Post by Skullxbagel on 2012-03-13
Sorry, but i don't own a laptop, here was the output.

> chris@chris-desktop:~$ dmesg | grep -e ndis -e wlan
[   13.638614] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.480424] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[   14.481550] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[   14.484273] IP: [<ffffffffa02acae9>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[   14.484306] Modules linked in: snd_hda_codec_atihdmi snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate ndiswrapper(+) snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_hwdep snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq joydev snd_timer snd_seq_device radeon ttm drm_kms_helper psmouse snd serio_raw drm i2c_piix4 soundcore snd_page_alloc i2c_algo_bit edac_core edac_mce_amd shpchp lp parport usbhid hid usb_storage r8169 mii ahci
[   14.484332] RIP: 0010:[<ffffffffa02acae9>]  [<ffffffffa02acae9>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[   14.484386]  [<ffffffffa029a2aa>] ? NdisAllocateMemoryWithTag+0x1a/0x40 [ndiswrapper]
[   14.484398]  [<ffffffffa02acc70>] ? USBD_InterfaceReference+0x0/0x30 [ndiswrapper]
[   14.484410]  [<ffffffffa02acc40>] ? USBD_InterfaceDereference+0x0/0x30 [ndiswrapper]
[   14.484422]  [<ffffffffa02acaa0>] ? USBD_InterfaceGetUSBDIVersion+0x0/0x40 [ndiswrapper]
[   14.484434]  [<ffffffffa02ad1c0>] ? USBD_InterfaceQueryBusTime+0x0/0x30 [ndiswrapper]
[   14.484446]  [<ffffffffa02acc10>] ? USBD_InterfaceSubmitIsoOutUrb+0x0/0x30 [ndiswrapper]
[   14.484457]  [<ffffffffa02acbe0>] ? USBD_InterfaceQueryBusInformation+0x0/0x30 [ndiswrapper]
[   14.484469]  [<ffffffffa02acae0>] ? USBD_InterfaceIsDeviceHighSpeed+0x0/0x20 [ndiswrapper]
[   14.484481]  [<ffffffffa029f52c>] ? ExAllocatePoolWithTag+0x3c/0x80 [ndiswrapper]
[   14.484493]  [<ffffffffa02ae72b>] ? win2lin3+0x11/0x14 [ndiswrapper]
[   14.484510]  [<ffffffffa02aa90f>] ? mp_init+0x6f/0x200 [ndiswrapper]
[   14.484522]  [<ffffffffa02a4cd2>] ? pdoDispatchPnp+0x42/0x100 [ndiswrapper]
[   14.484533]  [<ffffffffa02abe5c>] ? ndis_start_device+0x2c/0x8b0 [ndiswrapper]
[   14.484545]  [<ffffffffa02a1dfd>] ? IofCallDriver+0x6d/0xd0 [ndiswrapper]
[   14.484561]  [<ffffffffa02a1dd1>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[   14.484572]  [<ffffffffa02a23b6>] ? IoSyncForwardIrp+0x96/0xd0 [ndiswrapper]
[   14.484584]  [<ffffffffa02ac783>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
[   14.484596]  [<ffffffffa02ae717>] ? win2lin2+0xe/0x11 [ndiswrapper]
[   14.484607]  [<ffffffffa02a1dd1>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[   14.484618]  [<ffffffffa02a1dfd>] ? IofCallDriver+0x6d/0xd0 [ndiswrapper]
[   14.484632]  [<ffffffffa02a1dd1>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[   14.484643]  [<ffffffffa02a3dad>] ? IoSendIrpTopDev+0xdd/0x130 [ndiswrapper]
[   14.484657]  [<ffffffffa02a1c18>] ? IoAttachDeviceToDeviceStack+0x68/0x80 [ndiswrapper]
[   14.484669]  [<ffffffffa02a41ac>] ? pnp_start_device+0x4c/0x90 [ndiswrapper]
[   14.484681]  [<ffffffffa02a4479>] ? wrap_pnp_start_device+0xf9/0x180 [ndiswrapper]
[   14.484692]  [<ffffffffa02a45f1>] ? wrap_pnp_start_usb_device+0xf1/0x120 [ndiswrapper]
[   14.484731]  [<ffffffffa02cf000>] ? wrapper_init+0x0/0xb0 [ndiswrapper]
[   14.484740]  [<ffffffffa0295e4f>] ? loader_init+0xcf/0x160 [ndiswrapper]
[   14.484749]  [<ffffffffa02cf07b>] ? wrapper_init+0x7b/0xb0 [ndiswrapper]
[   14.484778] RIP  [<ffffffffa02acae9>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]



---

### Post by flash63 on 2012-03-13
And the rest of the queries?

---

### Post by Skullxbagel on 2012-03-13
That was it, I took to edesg or whatever it was called and pasted it in

---

### Post by chili555 on 2012-03-13
> [ 14.481550] ndiswrapper: driver [COLOR="Red"]bcmwlhigh5[/COLOR] (Netgear,05/05/2009, 5.10.79.30) loaded
[ 14.484273] IP: [<ffffffffa02acae9>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]See post #53. I thought we replaced this with bcmn43xx64.inf. No?

---

### Post by Skullxbagel on 2012-03-13
> **chili555 said:**
> See post #53. I thought we replaced this with bcmn43xx64.inf. No?

Yah, but it keeps saying it can't delete, so you said that's basically all we can do.

---

### Post by chili555 on 2012-03-13
Let's try again:```
sudo su
modprobe -rv ndisrwapper
rm -rf /etc/ndiswrapper/*
cd Desktop/Broadcom_bcm43xx_USB_32_64bit_v2
ndiswrapper -i bcmn43xx64.inf
modprobe ndiswrapper
ndiswrapper -l
exit
```We are especially interested in any errors, warnings, etc.

---

### Post by flash63 on 2012-03-14
> **Skullxbagel said:**
> That was it, I took to edesg or whatever it was called and pasted it in

Ok, the used Driver bcmwlhigh5 don't work. 

Follow the instructions of chili555 and install the mentioned driver (bcmn43xx64.inf). It may only be installed one module driver!

---

### Post by Skullxbagel on 2012-03-14
It is installed I don't know why it even listed it because when I do ndiswrapper -l it lists only the bcmn43xx64

---

### Post by Skullxbagel on 2012-03-14
i guess i couldn't find the file you wanted me to put all the stuff in so i just deleted the last part of some of the commands and i'll just show you what it said in terminal.

```
chris@chris-desktop:~$ sudo modprobe ndiswrapper
[sudo] password for chris: 
chris@chris-desktop:~$ dmesg | egrep 'ndis|wlan'
[   11.846101] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.871104] usbcore: registered new interface driver ndiswrapper
chris@chris-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

chris@chris-desktop:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

chris@chris-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by Skullxbagel on 2012-03-14
I don't know if this makes a difference, but in windows this adapter has a pretty complicated interface, with this thing where you press a button and press a button on another thing within 30 seconds, and lots of pages. Basically i'm wondering if this will do this in Ubuntu.
Also what does modprobe do?

---

### Post by flash63 on 2012-03-15
modprobe loads ndiswrapper and also the Windows driver into the kernel.

Hmm, no obvious errors but no interface!?

what shows
```

lsusb
ndiswrapper -l
find /etc/ndiswrapper/*
```

---

### Post by Skullxbagel on 2012-03-15
```

chris@chris-desktop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04ca:003a Lite-On Technology Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0781:5566 SanDisk Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0846:9011 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@chris-desktop:~$ ndiswrapper -l
bcmn43xx64 : driver installed
chris@chris-desktop:~$ find /etc/ndiswrapper/*
/etc/ndiswrapper/bcmn43xx64
/etc/ndiswrapper/bcmn43xx64/0846:9020.F.conf
/etc/ndiswrapper/bcmn43xx64/050D:6050.F.conf
/etc/ndiswrapper/bcmn43xx64/bcmn43xx64.inf
/etc/ndiswrapper/bcmn43xx64/050D:615A.F.conf
/etc/ndiswrapper/bcmn43xx64/050D:825C.F.conf
/etc/ndiswrapper/bcmn43xx64/bcmn43xx64.sys
chris@chris-desktop:~$ 

```

---

### Post by chili555 on 2012-03-15
> 0846:[COLOR="Red"]9011[/COLOR] NetGear, Inc. However, 9011 is *not* mentioned in /etc/ndiswrapper. BUT, 9011 is mentioned in the .inf file:> Manufacturer]
%Broadcom% = Broadcom

[Broadcom]
%BCM4xx01_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_825C
%BCM4xx02_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_6050
%BCM4xx04_DeviceDesc% = BCM43XXN64, USB\VID_050D&PID_615A
%BCM4xx03_DeviceDesc% = BCM43XXN[COLOR="Red"]**32**[/COLOR], USB\VID_[COLOR="Red"]0846[/COLOR]&PID_[COLOR="Red"]9011[/COLOR]
%BCM4xx03_DeviceDesc% = BCM43XXN64, USB\VID_0846&PID_9020

[BCM43XXN64]
Characteristics	= 0x84	
BusType		= 15	
AddReg		= Parameter
CopyFiles	= Driver

[Driver]
bcmn43xx64.sysIt is evidently for 32-bit only...??? However, the .inf file seems to be written for 64-bit. I am wondering if this is actually a typo.

What do you think, flash63, about amending the .inf and unloading/reloading ndiswrapper?

This is a bit wierd.

---

### Post by Skullxbagel on 2012-03-15
So do i try and uninstall then reinstall? I mean it's only one of the lines, maybe it is a typo.

---

### Post by flash63 on 2012-03-15
You use a older Driver-Package. Uninstall and delete it.

The current package contains the required device ID without syntax errors (32bit and 64bit).

[http://forum.ubuntuusers.de/post/2955302/](http://forum.ubuntuusers.de/post/2955302/)

---

### Post by Skullxbagel on 2012-03-15
Uninstall what? And what do I do on that other page?

---

### Post by flash63 on 2012-03-15
> **Skullxbagel said:**
> Uninstall what?
The installed driver, of course.

Delete it
```
sudo rm -r /etc/ndiswrapper/*
```

> **Skullxbagel said:**
> And what do I do on that other page?
Download the new driver-pakage (Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz ), unpack it and install the included 64bit version (bcmn43xx64.inf).

---

### Post by Skullxbagel on 2012-03-15
Gahhh! Now my computer is slow again, it says it couldn't find source disk files... Continuing anyway while I was installing.

---

### Post by Skullxbagel on 2012-03-15
It freezes also when I do ndiswrapper -l
Also, when I tried to delete it, it didn't do anything, I'll just try again I guess.

---

### Post by flash63 on 2012-03-16
> **Skullxbagel said:**
> It freezes also when I do ndiswrapper -l
Also, when I tried to delete it, it didn't do anything, I'll just try again I guess.

No response? Then the command was executed without errors. The directory **/etc/ndiswrapper/** must be empty now.
```
find /etc/ndiswrapper/*
```

Remove the stick and unload ndiswrapper ...
```
sudo modprobe -rfv ndiswrapper
```
... and install the new driver shown on the upper post. Then connect the WLAN-Stick to the USB port and check the function.

```

sudo modprobe ndiswrapper
dmesg | egrep 'ndis|wlan'
iwconfig
iwlist chan
sudo iwlist scan

```

---

### Post by Skullxbagel on 2012-03-16
Upper post of what? I went to the German posts but there was no link to a driver.

---

### Post by flash63 on 2012-03-16
> **Skullxbagel said:**
> Upper post of what? I went to the German posts but there was no link to a driver.

Thats's not right.

[http://forum.ubuntuusers.de/post/2955302/](http://forum.ubuntuusers.de/post/2955302/)

The driver package is located in the atachment and can be downloaded very simple by clicking on it (Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz (0.8 KiB)).

Here the direct link for you
[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

---

### Post by Skullxbagel on 2012-03-17
It installs, but Now the system starts slowly again and before it does it checks my system for errors!! What now? I guess this isn't working

---

### Post by Skullxbagel on 2012-03-17
Ok well I thought maybe we were getting a bit unlucky with the netgeAr one so I tried out the Belmont, found the driver and it works. 
Ndiswrapper -l says
Bcmwlhigh6 : driver installed
             Device (050d:6050)  present

---

### Post by Skullxbagel on 2012-03-17
So how do i use it, because I still don't have any connections.

---

### Post by Skullxbagel on 2012-03-19
Well since that didn't work, just can I have an idea on whatim supposed to do here? I mean is 64-bit not going to work? Because all of these drivers just don't work for some reason!! So I guess if deleting and reinstalling Ubuntu is the best way to go, please tell me.

---

### Post by chili555 on 2012-03-19
I think we have thrown all the skill and .inf files we have at the project and come up with nothing. If I were you, I'd try the live CD in 32-bit and the 32-bit .inf. If it works, then install 32-bit.

Unfortunately,there are a few projects that we, even the most experienced of us, have to admit we have no way to get working.

---

### Post by Skullxbagel on 2012-03-20
There is a cd that comes with the adapter, should we try that? I have my other adapter from my friend that actually uses Ubuntu, and then I have the adapter already installed in the computer.

---

### Post by chili555 on 2012-03-20
> There is a cd that comes with the adapter, should we try that? The problem is that the 64-bit Windows XP has some conflict with ndiswrapper and doesn't work. Some kind soul communicated with Broadcom and got a revised .inf especially for ndiswrapper, bcm43xx32.inf and bcm43xx64.inf. The trouble is, while it doesn't conflict with ndiswrapper, but it doesn't work on your system either!

I am quite troubled by the freezing behavior on your computer. I wonder if there is some underlying issue that prevents the driver, ndiswrapper, Network Manager, et al from working together harmoniously. Do you still have your install CD? Can you run a live session, install ndiswrapper and the bcm43xx64.inf from a USB key, perhaps, and see if the freezing is cured? Does the live session run as 64-bit?

---

### Post by Skullxbagel on 2012-03-21
What's a live session, also can you give me a link to it, I couldn't see anything about a live session on their website

---

### Post by chili555 on 2012-03-21
A live session is when you let the CD boot, instead of the harddrive and run from the live CD. You can try out different Linux versions, 32-bit vs. 64-bit, etc. before you install. Obviously, you can decide that Mint or Suse or Fedora is or is not for you, shut down, remove the CD and go back to what you have. 

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by Skullxbagel on 2012-03-22
I think it's the device, I ran a live session, did all of that stuff and still it didn't work, shall we try with another device?

---

### Post by chili555 on 2012-03-23
Does the device work in Windows? On another computer?

What other device do you have that we can try?```
lsusb
```

---

### Post by Skullxbagel on 2012-03-23
Post 7:::

> 
Re: Netgear WNDAv2 N600 wireless dual and USB adapter
Gahhh, it says 
Package 'ndiswrapper-common' is not installed and no info is available.
I have more routers If this is a problem
1 is 0461:4d16
Another is 050d:6050


---

### Post by chili555 on 2012-03-23
> 0461:4d16 Google says this is manufactured by Primax Electronics, Ltd. According to their website, they don't make a wireless networking card: [http://www.primax.com.tw/products.htm](http://www.primax.com.tw/products.htm)

> 050d:6050 This is described here: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Belkin_F6D6050nt](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Belkin_F6D6050nt)

That's another ndiswrapper bcmwlhigh5.inf nightmare. What happens when you stick it in the slot and run:```
ndiswrapper -l
iwconfig
```

---

### Post by Skullxbagel on 2012-03-23
In live session or does it not matter?

---

### Post by chili555 on 2012-03-24
Either. Why not try both?

---

### Post by Skullxbagel on 2012-03-24
```


nchris@chris-desktop:~$ ndiswrapper -l
bcmwlhigh6 : driver installed
chris@chris-desktop:~$ sudo rm -rf /etc/ndiswrapper/*
[sudo] password for chris: 
chris@chris-desktop:~$ ndiswrapper -l
chris@chris-desktop:~$ 
chris@chris-desktop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04ca:003a Lite-On Technology Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I still have the netgear in because i use it in Windows.

---

### Post by chili555 on 2012-03-24
> chris@chris-desktop:~$ sudo [COLOR="Red"]rm[/COLOR] -rf /etc/ndiswrapper/*Why did you do that? I thought we were trying to install ndiswrapper drivers, not remove them!

Are you now running 32- or 64-bit?```
arch
```We now start from scratch.

---

### Post by Skullxbagel on 2012-03-24
well because that was a netgear driver. Oops im sorry i did lsusb without my adapter in... ok well I'll just do it again, the adapter inside the computer should be showing though.

---

### Post by Skullxbagel on 2012-03-24
```

chris@chris-desktop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 04ca:003a Lite-On Technology Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0846:9011 NetGear, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 050d:6050 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@chris-desktop:~$ ndiswrapper -l
chris@chris-desktop:~$ arch
x86_64
chris@chris-desktop:~$ 

```

---

### Post by chili555 on 2012-03-25
It ought to work with bcmwlhigh6.inf. Don't you have it somewhere in your many downloads?```
cd Desktop/??file??
sudo ndiswrapper -i bcmwlhigh6.inf
sudo modprobe ndiswrapper
ndiswrapper -l
iwconfig
```If it doesn't work, please show me:```
dmesg | grep ndis
```Thanks.

---

### Post by Skullxbagel on 2012-03-25
```


chris@chris-desktop:~$ sudo su
root@chris-desktop:/home/chris# cd Desktop/vista
root@chris-desktop:/home/chris/Desktop/vista# ndiswrapper -i bcmwlhigh6.inf
installing bcmwlhigh6 ...
root@chris-desktop:/home/chris/Desktop/vista# modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
root@chris-desktop:/home/chris/Desktop/vista# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwlhigh6 : driver installed
	device (050D:6050) present
root@chris-desktop:/home/chris/Desktop/vista# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@chris-desktop:/home/chris/Desktop/vista# 
root@chris-desktop:/home/chris/Desktop/vista# 
root@chris-desktop:/home/chris/Desktop/vista# dmesg | grep ndis
[   11.766768] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.335108] usbcore: registered new interface driver ndiswrapper
[  141.707530] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  141.707551] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  141.707567] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  141.707594] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  141.707609] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  141.707624] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  141.707639] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  141.707653] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  141.707681] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  141.707696] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  141.707711] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  141.707725] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  141.707746] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  141.707764] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  141.707778] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  141.707806] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  141.707820] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  141.707882] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  141.707901] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  141.707916] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  141.707930] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  141.707942] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  141.707954] ndiswrapper (import:242): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  141.707959] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[  141.708791] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
root@chris-desktop:/home/chris/Desktop/vista# 

```
Are the errors because of 32-bit versions and what not?

---

### Post by chili555 on 2012-03-25
> cd Desktop/[COLOR="Red"]vista[/COLOR]ndiswrapper wants XP files, not Vista. Do you have an XP version?

---

### Post by Skullxbagel on 2012-03-25
I tried the xp version but it comes up with the same error with the 

[warning] and stuff, this is all that happened.

```


chris@chris-desktop:~$ sudo su
[sudo] password for chris: 
root@chris-desktop:/home/chris# rm -rf /etc/ndiswrapper/*
root@chris-desktop:/home/chris# cd Desktop/xp
root@chris-desktop:/home/chris/Desktop/xp# ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
root@chris-desktop:/home/chris/Desktop/xp# modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
ndiswrapper -l

```
it froze, i think it's a 64-bit problem.

---

### Post by chili555 on 2012-03-26
> it froze, i think it's a 64-bit problem.Normally, trying to load a 32-bit .inf file on a 64-bit system doesn't cause a freeze; it just doesn't work and it puts errors in the messages file. Let's see what it says:```
dmesg | grep ndis
```When you read the inf file you installed, does it include those magic words like this?> ;-----------------------------------------------------------------
; x64 (AMD64, Intel EM64T) - WinXP
;
[Belkin.NT[COLOR="Red"]amd64[/COLOR]]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_050D&PID_825C
        %BCM430NDX_DeviceDesc% = BCM43XNMD, USB\VID_[COLOR="Red"]050D[/COLOR]&PID_[COLOR="Red"]6050[/COLOR]
        %BCM430NDS_DeviceDesc% = BCM43XNMD, USB\VID_050D&PID_615A
;-----------------------------------------------------------------
; x86 - Win9x, Win2K, WinXP
;
[Belkin]
        %BCM430ND_DeviceDesc% = BCM43XNMD, USB\VID_050D&PID_825C
        %BCM430NDX_DeviceDesc% = BCM43XNMD, USB\VID_050D&PID_6050
        %BCM430NDS_DeviceDesc% = BCM43XNMD, USB\VID_050D&PID_615A
If not, I can send you my copies.


-------------
ref: .wine/drive_c/Program Files/Belkin/F7D4101/V1/xp/bcmwlhigh5.inf

---

### Post by Skullxbagel on 2012-03-26
Sadly, no magic words... How do I get to .wine? It's not in my home folder or anything

---

### Post by chili555 on 2012-03-26
> How do I get to .wine? It's not in my home folder or anythingNope, sorry. That was to remind me where on ***my*** computer the file is located. I have several copies of bcmwlhigh5.inf, all of which seem different. The copy I quoted is on my computer and is now zipped and attached here.

Please remove your old not-functioning .inf as before and install this.

---

### Post by Skullxbagel on 2012-03-27
I'm starting to think maybe I am doing something wrong because that doesn't work either!! Same thing with the device is present but nothing shows up under iwconfig.

---

### Post by chili555 on 2012-03-28
Ratzz!

Any informative messages here?```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

---

### Post by Skullxbagel on 2012-03-28
```

chris@chris-desktop:~$ sudo su
[sudo] password for chris: 
root@chris-desktop:/home/chris# rm -rf /etc/ndiswrapper/*
root@chris-desktop:/home/chris# cd Desktop/xp
root@chris-desktop:/home/chris/Desktop/xp# ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
root@chris-desktop:/home/chris/Desktop/xp# modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
root@chris-desktop:/home/chris/Desktop/xp# dmesg | grep ndis
[   11.730549] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   12.248103] usbcore: registered new interface driver ndiswrapper
root@chris-desktop:/home/chris/Desktop/xp# 

```

---

### Post by chili555 on 2012-03-29
Looks fabulous! No problems or errors so far. Let's clean this up:> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.Let's see what it says in there:```
cat /etc/modprobe.d/ndiswrapper
```We will either rename it with .conf or remove it entirely, depending on what's there. Let's also see:```
ndiswrapper-l
iwconfig
```

---

### Post by Skullxbagel on 2012-03-29
```


chris@chris-desktop:~$ sudo su
[sudo] password for chris: 
root@chris-desktop:/home/chris# cat /etc/modprobe.d/ndiswrapper
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
root@chris-desktop:/home/chris# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwlhigh5 : driver installed
	device (050D:6050) present
root@chris-desktop:/home/chris# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by Skullxbagel on 2012-04-01
Should I just get another newer version of Ubuntu? Maybe it would work better.

---

### Post by chili555 on 2012-04-01
You could certainly try the live CD in both 32- and 64-bit versions. *Any* device using bcmwlhigh5.inf will be very tricky.

Please do:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```The warning message will be solved.

---

### Post by Skullxbagel on 2012-04-03
I did it now what

---

### Post by scottrasmussen on 2012-04-05
chili,
i've been reading these forums trying to get my n600 usb to be recognized by new ubuntu computer.

after typing : ndiswrapper -i /path/to/bcmwlhigh5.inf

i get:

driver bcmwlhigh5 is already installed
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# modprobe -rv ndiswrapper
rmmod /lib/modules/3.0.0-12-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# modprobe ndiswrapper
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# ndiswrapper -l
autorun :** invalid driver!**
bcmwlhigh5 : driver installed

is this causing a problem?

computer is running ubuntu 11.10. 

thx!

---

### Post by chili555 on 2012-04-05
> **scottrasmussen said:**
> chili,
i've been reading these forums trying to get my n600 usb to be recognized by new ubuntu computer.

after typing : ndiswrapper -i /path/to/bcmwlhigh5.inf

i get:

driver bcmwlhigh5 is already installed
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# modprobe -rv ndiswrapper
rmmod /lib/modules/3.0.0-12-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# modprobe ndiswrapper
root@skat:/home/massolit/Desktop/ndiswrapper-1.57# ndiswrapper -l
autorun :** invalid driver!**
bcmwlhigh5 : driver installed

is this causing a problem?

computer is running ubuntu 11.10. 

thx!Please see your other thread: [http://ubuntuforums.org/showthread.php?t=1695036&page=5](http://ubuntuforums.org/showthread.php?t=1695036&page=5)

---

### Post by Skullxbagel on 2012-04-07
ok well i don't have a cd big enough to install amd64 Ubuntu X on it, so i guess i can't do the headers or whatever.

I did the ndiswrapper update but something weird happened after i thought i had deleted 1.55. Take a look.
```


chris@chris-desktop:~$ dmesg | grep ndis
***_[   11.662213] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)_***
[   12.398660] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[   12.398854] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh5'
[   12.399313] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh5; check system log for messages from 'loadndisdriver'
[   12.399520] usbcore: registered new interface driver ndiswrapper
[  466.511068] usbcore: deregistering interface driver ndiswrapper
[  466.511435] ndiswrapper (ntoskernel_exit:2677): object ffff880180f32430(2) was not freed, freeing it now
[  476.281161] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  476.587641] ndiswrapper (import:233): unknown symbol: ntoskrnl.exe:'IoUnregisterPlugPlayNotification'
[  476.587920] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[  476.593305] ndiswrapper: driver bcmwlhigh5 (Belkin International, Inc.,12/23/2009, 5.60.180.11) loaded
[  476.596656] IP: [<ffffffffa0362749>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[  476.596730] last sysfs file: /sys/module/ndiswrapper/refcnt
[  476.596741] Modules linked in: ndiswrapper(+) nls_iso8859_1 nls_cp437 vfat fat binfmt_misc ppdev snd_hda_codec_atihdmi snd_hda_codec_realtek fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss joydev snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq radeon ttm drm_kms_helper snd_timer snd_seq_device drm i2c_algo_bit snd usbhid psmouse serio_raw lp edac_core edac_mce_amd soundcore snd_page_alloc i2c_piix4 hid shpchp parport usb_storage ahci r8169 mii [last unloaded: ndiswrapper]
[  476.596834] RIP: 0010:[<ffffffffa0362749>]  [<ffffffffa0362749>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[  476.597024]  [<ffffffffa035021a>] ? NdisAllocateMemoryWithTag+0x1a/0x40 [ndiswrapper]
[  476.597070]  [<ffffffffa03628d0>] ? USBD_InterfaceReference+0x0/0x30 [ndiswrapper]
[  476.597115]  [<ffffffffa03628a0>] ? USBD_InterfaceDereference+0x0/0x30 [ndiswrapper]
[  476.597161]  [<ffffffffa0362700>] ? USBD_InterfaceGetUSBDIVersion+0x0/0x40 [ndiswrapper]
[  476.597206]  [<ffffffffa0362e20>] ? USBD_InterfaceQueryBusTime+0x0/0x30 [ndiswrapper]
[  476.597251]  [<ffffffffa0362870>] ? USBD_InterfaceSubmitIsoOutUrb+0x0/0x30 [ndiswrapper]
[  476.597297]  [<ffffffffa0362840>] ? USBD_InterfaceQueryBusInformation+0x0/0x30 [ndiswrapper]
[  476.597342]  [<ffffffffa0362740>] ? USBD_InterfaceIsDeviceHighSpeed+0x0/0x20 [ndiswrapper]
[  476.597387]  [<ffffffffa035544c>] ? ExAllocatePoolWithTag+0x3c/0x80 [ndiswrapper]
[  476.597432]  [<ffffffffa03641cb>] ? win2lin3+0x11/0x14 [ndiswrapper]
[  476.597477]  [<ffffffffa035a6ba>] ? pdoDispatchPnp+0x5a/0x500 [ndiswrapper]
[  476.597522]  [<ffffffffa035fdff>] ? mp_init+0x6f/0x200 [ndiswrapper]
[  476.597566]  [<ffffffffa03582d6>] ? IoSyncForwardIrp+0x96/0xd0 [ndiswrapper]
[  476.597624]  [<ffffffffa036192b>] ? NdisDispatchPnp+0xab/0xc10 [ndiswrapper]
[  476.597678]  [<ffffffffa0358c49>] ? IoAllocateIrp+0x59/0x80 [ndiswrapper]
[  476.597722]  [<ffffffffa0358377>] ? IoInitializeIrp+0x37/0x70 [ndiswrapper]
[  476.597766]  [<ffffffffa0358c5f>] ? IoAllocateIrp+0x6f/0x80 [ndiswrapper]
[  476.597811]  [<ffffffffa03641b7>] ? win2lin2+0xe/0x11 [ndiswrapper]
[  476.597854]  [<ffffffffa0357cf1>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[  476.597897]  [<ffffffffa0357d1d>] ? IofCallDriver+0x6d/0xd0 [ndiswrapper]
[  476.597950]  [<ffffffffa0357cf1>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[  476.597993]  [<ffffffffa0359bad>] ? IoSendIrpTopDev+0xdd/0x130 [ndiswrapper]
[  476.598046]  [<ffffffffa0357b38>] ? IoAttachDeviceToDeviceStack+0x68/0x80 [ndiswrapper]
[  476.598091]  [<ffffffffa0359e9c>] ? pnp_start_device+0x4c/0x90 [ndiswrapper]
[  476.598135]  [<ffffffffa035a223>] ? wrap_pnp_start_device+0x1b3/0x270 [ndiswrapper]
[  476.598180]  [<ffffffffa035a3d1>] ? wrap_pnp_start_usb_device+0xf1/0x120 [ndiswrapper]
[  476.598316]  [<ffffffffa0385000>] ? wrapper_init+0x0/0xb0 [ndiswrapper]
[  476.598352]  [<ffffffffa034badf>] ? loader_init+0xcf/0x160 [ndiswrapper]
[  476.598385]  [<ffffffffa038507b>] ? wrapper_init+0x7b/0xb0 [ndiswrapper]
[  476.598486] RIP  [<ffffffffa0362749>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
chris@chris-desktop:~$ 

After this I checked version because of the 1.55 at the top::::::::::

chris@chris-desktop:~$ arch
x86_64
chris@chris-desktop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-38-generic/misc/ndiswrapper.ko
version:        1.56
vermagic:       2.6.32-38-generic SMP mod_unload modversions 
chris@chris-desktop:~$

```
So did i completely delete ndiswrapper 1.55? should i just delete 1.56 and get 1.57?
```

chris@chris-desktop:~$ rm -rv /etc/ndiswrapper*
rm: descend into write-protected directory `/etc/ndiswrapper'? 
chris@chris-desktop:~$ sudo su
[sudo] password for chris: 
root@chris-desktop:/home/chris# rm -rv /etc/ndiswrapper*
removed `/etc/ndiswrapper/bcmwlhigh5/bcmwlhigh564.sys'
removed `/etc/ndiswrapper/bcmwlhigh5/050D:6050.F.conf'
removed `/etc/ndiswrapper/bcmwlhigh5/bcmwlhigh5.inf'
removed `/etc/ndiswrapper/bcmwlhigh5/050D:615A.F.conf'
removed `/etc/ndiswrapper/bcmwlhigh5/050D:825C.F.conf'
removed directory: `/etc/ndiswrapper/bcmwlhigh5'
removed directory: `/etc/ndiswrapper'
root@chris-desktop:/home/chris# cd Desktop/ndiswrapper-1.56
root@chris-desktop:/home/chris/Desktop/ndiswrapper-1.56# make
make -C driver
make[1]: Entering directory `/home/chris/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.32-38-generic M=/home/chris/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-38-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-38-generic'
make[1]: Leaving directory `/home/chris/Desktop/ndiswrapper-1.56/driver'
make -C utils
make[1]: Entering directory `/home/chris/Desktop/ndiswrapper-1.56/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/chris/Desktop/ndiswrapper-1.56/utils'
root@chris-desktop:/home/chris/Desktop/ndiswrapper-1.56# make install
make -C driver install
make[1]: Entering directory `/home/chris/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.32-38-generic M=/home/chris/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-38-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-38-generic'
echo /lib/modules/2.6.32-38-generic/misc
/lib/modules/2.6.32-38-generic/misc
mkdir -p /lib/modules/2.6.32-38-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.32-38-generic/misc
/sbin/depmod -a 2.6.32-38-generic -b /
make[1]: Leaving directory `/home/chris/Desktop/ndiswrapper-1.56/driver'
make -C utils install
make[1]: Entering directory `/home/chris/Desktop/ndiswrapper-1.56/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/chris/Desktop/ndiswrapper-1.56/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
root@chris-desktop:/home/chris/Desktop/ndiswrapper-1.56# ndiswrapper -i /path/to/bcmwlhigh5.inf
couldn't open /path/to/bcmwlhigh5.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
root@chris-desktop:/home/chris/Desktop/ndiswrapper-1.56# ndiswrapper -i /Desktop/xp/bcmwlhigh5.inf
couldn't open /Desktop/xp/bcmwlhigh5.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
root@chris-desktop:/home/chris/Desktop/ndiswrapper-1.56# cd Desktop/xp
bash: cd: Desktop/xp: No such file or directory
root@chris-desktop:/home/chris/Desktop/ndiswrapper-1.56# exit
exit
chris@chris-desktop:~$ cd Desktop/xp
chris@chris-desktop:~/Desktop/xp$ sudo su
root@chris-desktop:/home/chris/Desktop/xp# ndiswrapper -i bcmwlhigh5.inf
installing bcmwlhigh5 ...
root@chris-desktop:/home/chris/Desktop/xp# modprobe -rv ndiswrapper
***_It froze here_***

```

That was what happened when i installed it. If i get a newer version of ndiswrapper, should i retry some of the other versions of the driverS?
-Thanks

---

### Post by scottrasmussen on 2012-05-06
hey chili,

back again...wtf!!!  upgraded to 12.04 and now adapter wont work again.  when i run ndiswrapper -l it shows that the adapter is present, but no connection.  am i going crazy?  should i revert to 11.10?

thx

---

### Post by chili555 on 2012-05-07
> **scottrasmussen said:**
> hey chili,

back again...wtf!!!  upgraded to 12.04 and now adapter wont work again.  when i run ndiswrapper -l it shows that the adapter is present, but no connection.  am i going crazy?  should i revert to 11.10?

thxLet's do some diagnostics. Please run and post:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

