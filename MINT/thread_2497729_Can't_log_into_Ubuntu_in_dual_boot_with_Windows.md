---
title: "Can't log into Ubuntu in dual boot with Windows"
date: 2024-05-15
forum: MINT
---

### Post by tacolandia on 2024-05-15
I had installed an SSD drive that I put Ubuntu 20.04 on in a partition. It was also partitioned as D: drive in Windows. It worked fine for awhile. Then I started experiencing issues before when it didn't give the option to choose Windows on boot, unless I chose in bios, and it went to a grub terminal, which I would have to exit from. But I upgraded to 22.04 and I think around then it started giving the option to log into Windows again, though it still went to grub on boot. Now I can't access Ubuntu at all, and D: drive on Windows can't be read. It may be an issue with the extra SSD drive, but in Windows it shows no issues in disk management, just the D: drive shows up as RAW, but the partition for Ubuntu is still there. I ran boot repair and got the boot info. I uploaded it and can share the info here if someone may have ideas on how to fix. If it may just be an issue with the SSD drive, I'm not sure if I should trust it and install Ubuntu again, or get another.

There's no recommended repair, the boot repair info just says

```
Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  win-legacy-basic-fix
```

 Thanks.

---

### Post by oldfred on 2024-05-16
Is this also you?
I prefer a forum like this for issues requiring back & forth or more  complex issues. AskUbuntu is one question & one answer.
[https://askubuntu.com/questions/1514201/installed-extra-ssd-d-drive-was-working-but-now-no-ubuntu-in-dual-boot-boot](https://askubuntu.com/questions/1514201/installed-extra-ssd-d-drive-was-working-but-now-no-ubuntu-in-dual-boot-boot)

Please post link to full Boot-Repair Boot-info report with external drive attached.
Do not use the same site as that is not allowed here, use the recommended pastebin site.

---

### Post by tacolandia on 2024-05-16
Yes I can delete that one, if that's preferable. I generated this. It  said a report was uploaded to pastebin. It says I can reboot, I haven't  done that yet. There were advanced options I didn't check the box of.  
[http://*******.us/BCEPaR](http://*******.us/BCEPaR)

I'm not sure what you mean by this

Do not use the same site as that is not allowed here, use the recommended pastebin site.

same site as what and what?

---

### Post by tacolandia on 2024-05-16
checking if quick reply works, it wasn't before

---

### Post by tacolandia on 2024-05-16
[LIST]
[*][                         ]("https://askubuntu.com/questions/1514201/installed-extra-ssd-d-drive-was-working-but-now-no-ubuntu-in-dual-boot-boot?noredirect=1#")                 
                                                                                                     
                                               RAW is what Windows sees as a  Windows partition that has lost the essential boot info that is in the  PBR - partition boot sector. Or it may just the the ext4 partition as it  has no info in PBR. Do not use Windows tools on Linux partiitions as it  may erase or corrupt them. post link to full summary report from  Boot-Repair. If UEFI installs be sure to boot live installer in UEFI  mode when running Boot-Repair.                                   &#8211; [oldfred]("https://askubuntu.com/users/126395/oldfred")                 
                 [22 hours ago]("https://askubuntu.com/questions/1514201/installed-extra-ssd-d-drive-was-working-but-now-no-ubuntu-in-dual-boot-boot?noredirect=1#comment2657976_1514201")                                                      

[*]                                      
         
          
[*]                                           1             
                                                                                                
                 

                                                                                    
                                               You are not showing external  drive and have no Linux install on internal drive. And you have grub  installed to Windows drive in both BIOS boot mode and UEFI boot mode.  Only one will probably work, Best to have Ubuntu in UEFI boot mode since  Windows is UEFI boot. Older installs defaulted to installing grub on  first drive unless you specified otherwise and UEFI installer even made  that difficult.  [bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379") Add ESP to external drive with gparted and reinstall grub in UEFI mode using that ESP with Boot-Repair. 


[/LIST]

---

### Post by oldfred on 2024-05-16
The site you are posting to is a banned word on this site.
Normally with Ubuntu, Boot-Repair posts to pastebin, but since Mint I guess it uses something else?

Moved to Mint sub-forum since not Ubuntu or one of Ubuntu's official flavors.

It looks like sda2 is not used. Remove boot,esp flags with gparted from sda2.
You can see UEFI boot entries as shown in report with:
sudo efibootmgr -v
And partitions:
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

---

### Post by tacolandia on 2024-05-16
The boot repair usb runs on mint, but I've only ever installed Ubuntu. I couldn't install boot repair in Ubuntu itself since I can't get to it. It said it was uploaded to pastebin but I'm not sure how to get results from there. But I guess it's the same that is shown locally, which I copied to pastebin here

[https://pastebin.ubuntu.com/p/DDQk5PhJCP/](https://pastebin.ubuntu.com/p/DDQk5PhJCP/)

---

### Post by tacolandia on 2024-05-16
Here are results of those commands

`
mint@mint:~$ sudo efibootmgr -v
BootCurrent: 0009
Timeout: 2 seconds
BootOrder: 0008,0000,0005,000A,0009,0007
Boot0000* Windows Boot Manager    HD(1,GPT,d764402b-115d-4e11-b06d-28f43361dbd7,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...h................
Boot0005* INTEL SSDPEKNW010T8    BBS(HD,,0x0)..BO
Boot0007* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0008* ubuntu    HD(1,GPT,d764402b-115d-4e11-b06d-28f43361dbd7,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0009* UEFI: SanDisk Cruzer Glide 1.26, Partition 1    PciRoot(0x0)/Pci(0x8,0x1)/Pci(0x0,0x3)/USB(1,0)/HD(1,MBR,0xaeba4e92,0x20,0x1dd17e0)..BO
Boot000A* SanDisk Cruzer Glide 1.26    BBS(HD,,0x0)..BO
mint@mint:~$ lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint ,uuid,partuuid
lsblk: ,uuid,partuuid: not a block device
`

---

### Post by tea for one on 2024-05-17
From the boot-repair report in post 7:-
[COLOR="#0000FF"]Line 80[/COLOR] - One OS detected Windows 10 or 11 on nvme0n1p3
[COLOR="#0000FF"]Line 151[/COLOR] - nvme0n1p5 2000406528 2000408575       2048     1M Linux filesystem

There is no sign of Ubuntu on your nvme0n1 disk
Your Linux file system size is miniscule.

Is Ubuntu on a separate unattached disk?

---

### Post by oldfred on 2024-05-17
This has an extra space which is not obvious 
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint ,uuid,partuuid
remove space before ,uuid

Make sure all drives are connected and in UEFI settings are seen by UEFI.
Better to use same version of Ubuntu, if current or a current version of Ubuntu as live installer for repairs.

---

### Post by tacolandia on 2024-05-17
The SSD is attached that had Ubuntu, it is seen in windows, but files can't be read there. I can't access Ubuntu anymore. I was wondering if I should trust the SSD still or replace it and reinstall Ubuntu.

---

### Post by tacolandia on 2024-05-17
mint@mint:~$ lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
NAME        FSTYPE   SIZE FSUSED LABEL PARTLABEL                    MOUNTPOINT                   UUID                                 PARTUUID
sda                    0B                                                                                                             
sdb                 14.9G                                                                                                             
&#9492;&#9472;sdb1      vfat    14.9G   2.6G                                    /cdrom                       C270-0D97                            aeba4e92-01
nvme0n1            953.9G                                                                                                             
&#9500;&#9472;nvme0n1p1 vfat     100M              EFI system partition                                      5478-1FD7                            d764402b-115d-4e11-b06d-28f43361dbd7
&#9500;&#9472;nvme0n1p2           16M              Microsoft reserved partition                                                                   9b45626c-8371-48d0-b40b-e368350c5606
&#9500;&#9472;nvme0n1p3 ntfs   953.2G 640.2G       Basic data partition         /media/mint/6C587B7E587B463C 6C587B7E587B463C                     3a663434-a8c3-4450-9773-9e5b214eb791
&#9500;&#9472;nvme0n1p4 ntfs     569M                                                                        1CFA7CDDFA7CB51C                     c61ac5e4-71ec-4752-b8a2-bb92f2ade510
&#9492;&#9472;nvme0n1p5            1M                                                                                                             e21a4ce4-ba59-47af-be57-727a5f8682bd

---

### Post by oldfred on 2024-05-17
It sees an empty drive.
sda                    0B

You can see if smartstatus says anything about drive.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)
Smart Data 
[https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854)

---

### Post by tacolandia on 2024-05-17
Ok I'll check that out thanks. When I initially installed dual boot I did it twice so there may be leftover partitions or something

---

### Post by tacolandia on 2024-05-17
does this mean there is likely an issue with the drive hardware?

mint@mint:~$ sudo smartctl -s on /dev/sda 
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-76-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
mint@mint:~$ sudo smartctl -s on -T permissive /dev/sda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-76-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Short INQUIRY response, skip product id
=== START OF ENABLE/DISABLE COMMANDS SECTION ===
unable to fetch IEC (SMART) mode page [scsi response fails sanity test]
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

---

### Post by oldfred on 2024-05-18
> sudo smartctl -s on /dev/sda

I do not think command includes "on" as key word?

I have seen & used:
sudo smartctl -t short /dev/sda

Or this which I just ran and shows passed.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo smartctl -H /dev/sda [/COLOR]
[sudo] password for fred:  
smartctl 7.4 2023-08-01 r5530 [x86_64-linux-6.8.0-31-generic] (local build) 
Copyright (C) 2002-23, Bruce Allen, Christian Franke, www.smartmontools.org 

=== START OF READ SMART DATA SECTION === 
SMART overall-health self-assessment test result: PASSED


[/FONT]
```

---

### Post by tacolandia on 2024-05-18
I get this 

```
mint@mint:~$ sudo smartctl -t short /dev/sda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-76-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

or this

```
mint@mint:~$ sudo smartctl -T permissive -t short /dev/sda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-76-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Short INQUIRY response, skip product id
Short Background Self Test has begun
Use smartctl -X to abort test
mint@mint:~$ 
```

---

### Post by tacolandia on 2024-05-18
or this

> 
mint@mint:~$ sudo smartctl -H /dev/sda 
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-76-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.



---

### Post by tacolandia on 2024-05-18
I don't see the 2 TB drive here, maybe I should just replace it

> 

mint@mint:~$ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0   2.3G  1 loop /rofs
sda           8:0    0     0B  0 disk 
sdb           8:16   1  14.9G  0 disk 
&#9492;&#9472;sdb1        8:17   1  14.9G  0 part /cdrom
nvme0n1     259:0    0 953.9G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   100M  0 part 
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 953.2G  0 part /media/mint/6C587B7E587B463C
&#9500;&#9472;nvme0n1p4 259:4    0   569M  0 part 
&#9492;&#9472;nvme0n1p5 259:5    0     1M  0 part 





> 

mint@mint:~$ sudo fdisk -l
Disk /dev/loop0: 2.3 GiB, 2473005056 bytes, 4830088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: INTEL SSDPEKNW010T8                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5BB98305-EBEC-4329-BDA9-FA7657CA7E65

Device              Start        End    Sectors   Size Type
/dev/nvme0n1p1       2048     206847     204800   100M EFI System
/dev/nvme0n1p2     206848     239615      32768    16M Microsoft reserved
/dev/nvme0n1p3     239616 1999239109 1998999494 953.2G Microsoft basic data
/dev/nvme0n1p4 1999239168 2000404479    1165312   569M Windows recovery environment
/dev/nvme0n1p5 2000406528 2000408575       2048     1M Linux filesystem


Disk /dev/sdb: 14.91 GiB, 16008609792 bytes, 31266816 sectors
Disk model: Cruzer Glide    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xaeba4e92

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *       32 31266815 31266784 14.9G  c W95 FAT32 (LBA)




---

### Post by tacolandia on 2024-05-18
But then I'm not sure why Windows detects it, though it can't read from it.

---

### Post by #&amp;thj^% on 2024-05-18
> **tacolandia said:**
> But then I'm not sure why Windows detects it, though it can't read from it.

make sure you haven't enabled Microsoft proprietary features in Windows like dynamic disks or whatever as they may prevent the drive form being used for other OSes. 

Was it seen during the install?

---

### Post by tacolandia on 2024-05-18
Ubuntu was run on this hard drive before, for some years, it just stopped working. I didn't explicitly change anything in Windows.

---

### Post by #&amp;thj^% on 2024-05-18
Just checking we covered all base's first....Sounds like it going/gone bad.

---

### Post by tacolandia on 2024-05-19
Here is latest pastebin, I tried rebooting, 

[https://paste.ubuntu.com/p/CdhhjcQHWv/](https://paste.ubuntu.com/p/CdhhjcQHWv/)

---

### Post by tacolandia on 2024-05-19
It still sees the drive in windows. On startup, it says 

> 

Scanning and repairing drive (//?/Volume{46a173d9-2fba-4e20-bb66-ea940223e454}):0


---

### Post by tacolandia on 2024-05-19
Here is windows

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA/AAAAHiCAYAAABP3ie3AAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAK02SURBVHhe7f0NYBvZeR76P7STbJK9zm6T7H b3LSNtYTWYWE3UWKlgZovp9IWpJNQScTcNjeh4sak5I8lbIfZKmHam4SNbsM2Jt06EuHUIfv3dmtqfcX6hkRXcpImWcKOXMtrGwtbBKSNvy1rd02t90P7yXveM2cGB8DMYEAAJAZ8fvaswMEAmDlzZua8c96Z6fv617  CSIiIiIiIiLqai8z/xIRERERERFRF2MAT0RERERERBQDDOCJiIiIiIiIYiD0GviXXnoJjz7 hP73pU01yL8vbWJT/ u8dsfv d7vwTd wzeYTxIRERERERFRO4X2wD/x1DPqv9Hucfelr1wzr4iIiIiIiIio3QID GduPIcXnn/B/NXY00/fwPUnvm7 IiIiIiIiItp v/7rv45bbrkFr3jFK3wHeU m6Tav Uffj7/66782f9WT9wJT6C9//ku4VPy0kyqv0 Q3san 3dyUFHp5rQb5n/60 o/6/6sGvg v b69 vO1XvOa1 CRRx4xfwGvfOUr8clPftL8BRw fBjf 73fi3e 851mTLW3ve1tOHDgAH7hF37BjKn34Q9/GIcOHcK5c fwIz/yI2as42//9m/x6le/Gn/yJ38S h1EREREREQUXxKgf QjH8F3f/d3mzHVHnvsMfzAD/wArl /bsZ0BwnQ3/CGN C9730vfuxHf9SMdbjvBQbwf3Pxk/iT7B/h2WefxXPPPecNzz//PF544QU9vPjii3jqB57CN134Jh3QZ379X EXf/5nzTdUkwD gx/8oA7SxezsLH77t38bn/rUp7xxYZoJ4P/pP/2nOHv2rBnrcH9vtwTwUcqLiIiIiIio10gv xe 8AUdyAeRaVQsbP7qHn5BvD2upbvQv wHX4bX/vFr8dRrnzJjostkMvi93/s9zM3NmTHtIcH75cuXdY 7TRb2137t18xfRERERERERN1FgnaJXSVgl8C9NqAPv4ndE0/g05/ tA6IP//5z Pq1au6F9710sdewsVfu4ibP3qzGdOcH/7hH/YCbekxvv/  /Vr de9PkFS62vJtPJeEFnA5eVl85fzfT/1Uz9l/nLYvyGD9N4L6amXQTIGZLz865Lx9mfskwTu9DLIdDKPLlkG z0hvyfj3WWR1/J9tdMJe7wMtWXmjnfLSsb/8R//MX71V39VjyciIiIiIqJ4sIN4O3gXdQH8b//2/4U/ /O/xpMb1/Evf 04fv/3Z9Tw773hN3/z/8K/ lf/GsffNIEf/MH9 P2f 0P83skZPfzga19rviWa7/qu79InB2pJ4CnpDDL4pcJLABuW7jA8PKwX0nXvvfdiYmLC/OWQ1HL3N Sa T/4gz8w70gZ/LZO95f37rjjDu/EgmQNuJ RVHw3e0ACZjlB4L5n/7a890u/9Evee3/5l3/pBeAf tCHdJq7jJdy Jmf Rn9Wi4rkHlwybX77uflPflO169aZSXfIScG5D4Ckm0g8yjjiYiIiIiItsLtLGw00PaoC B/7Md Aq95zT8yw/c7wz96jRrccWpQr3/yJ1 H9ODr8VM/dgA/9eMH8E9/4p g/ /73yQgyJe//GUdINeSNHi759slgbgEwLVBfS25pl4Cagm83Z51v vs3V5zuW7eJqn97vQ//uM/rq fcLkVVAJn15/92Z9VnSD41//6X5tXznsyrfs5Cdr/1//6X/o9WU73GnWZX/dz8ttykz8J9N35dz8vwbx8h0uCdJd8xxe/ EXzFxERERERUWvczsJGA7WPnTbv9sTLOFEXwH/Lt36L u8m3vjGUTX8inPnebnr/EtyB/qX8Gu/9iv4tX/5K3jppRfxLd/8zc6HtmhpaUkHyLUkQJcecAlY7RR66WG2g9cwIyMjOuCX35Ae8FoSvM/Pz vKJj3wUcj8SA 4fMYOnEXYjfjcz7hDszeWk0Df/rwMRERERERE1Ftqr3mvvSa LoB/4fnn8W2v FY8/dRTevi2b/vWquHpp9V4NdzybTfj Rcq18M3S9LApXda0tL9SEAsgaodsEsPtQTOfr3zteQxchLwy28EBcySwi8kyI/KDdTl5IBLsgjsa9Z/93d/17xyesVbuVGfLIeUgdsTH9U/ Af/oCpzgIiIiIiIaDd42cteph8VF RLX/qSnqbb1AbvLjuIr5vrF198AV/96jXzF3BVvbYHl7x 6cUXzV/RSPq3mwou7OfA29xpZKjt6ZZgXGZc3msU1ErAL9P6kfHu/EQl15W782X3uEvGgFyz7r5n/6Zcjy4nEdz3ZGiWZAhImr/7efsa CByg0B3noiIiIiIiHaLN77xjfo57278VDt83/d9n56mm8hj2d/61rvrgneXG8TXPQf /If AolEwvwVwHyiVFrHwYOvc/4gj9sbH5RdQERERERERGSTIL6vr8/85a uB37zpRfx0ksv1Q8vqvHuoKdRw ZL5lPkkhvPSc 39IATERERERERRdEoeBd1PfD/ T//Cf737/ke54 qd p98YtfwL/8l5W7se9W0uNuP/ZN0v6bvVEdERERERERUZi6AJ6IiIiIiIiIuk/33XqPiIiIiIiIiOowgCciIiIiIiKKAQbwRERERERERDHAAJ6IiIiIiIgoBhjAExEREREREcUAA3giIiIiIiKiGGAAT0RERERERBQDfZuKeU1EREREREREXYo98EREREREREQxwACeiIiIiIiIKAYYwBMRERERERHFAAN4IiIiIiIiohhgAE9EREREREQUAyEBfA7jfX3os4YDc2WgPIcDfQcgL51p3NedlxtX8zGeM381qWq d4bMvy5DW27cWaYumD9H0DqNsq63tz4QERERERHtJg164FOYLW1CnjQnw9pEP9A/gbXNNcjLbaUC3OnCGMYK0xEDxJpgcqfm25IeHkO WDJ/OXLLWYwNp7ti/oiIiIiIiKh7xSaFvryyBIxMYnIEWFqJaRdvYgCp7DIqOQQ5LGfHIPE7ERERERERUZgtBPAhadI6DdxNuR 3AtVWlaHj96F 9A/pCF6NsZUxd6CS6j ek3kcRBZ5ZBJu2n3NfFfNq3zGjHenmxv33qtLe9 q/iGMpLJYdn8rt4zs2DCc D1s/pyylBT8uvm0p9/q5QVb0XBdm/nLVaZrWzkSERERERHtQg0CeBMAmwAsPD5UAVtiCSNuyv0qMN2ugK28AvXNUPG7EwSrvyqd8BK8J7A0UvJS/efTacyrGRhzLwGYr 3ilnnNILlq5rU0i8KgFQzLcheHzXKMIZ Z8QlQt6IfQyMpFNadH/LS5 v4l6Wk4Gfd6F8F/4VUJRtBZygMJPTr1lWvd2eQEyKuqOtafc80sGjKGJlR/xM/RERERERE1FBT18DXxcG28joKduA3mK273nurnPT5IRX CgmCVSw4YwJZCe7zY5hq5uJxPa9W6nr/BKbG8qjMrlruSfNmelhNWYCJuVtWySAoY11F4L4xd1BZSgp YV1nH SWCxiZqnyXm6HQHtXr3RnkhIgReV2r71mccNZbXRkTERERERFRM9p8DfwYVu2gLzTijyqHmUwe UzC9AT3IaH RtW15DHiZhDkrKwCXz5l6WUf5LBcUJ9Ny99FlOwMhW3T7LqWExbmJRERERERETWtfQF8/14kkW1f2rxLrhNPzaJkB4ubJcymzLXk5rrypn7XzKt3LXp5DtPbdjM5k0EwmLGyCmoElqXz2aXRaRT0Z XvApZnisHf1QmR13W csNBkynBG/YRERERERFtTRt74NOY19c5V3rKt/zMdotcJ56qC06da8md68H7MbG2iqT1u87PpjE8ZtK86 bDmdfCoJlPfT33vLmZXOdJGn1K/S845T24LHUKfr6SLi9/F7KFNqbPRxF1XaeQLI6aMpZ7DmxfGRMREREREfWavk3p0iZqO7kL/TQGSny2PRERERERUTu0 Rp4IiIiIiIiIuoEBvBEREREREREMcAUeiIiIiIiIqIYYA88ERERERERUQwwgCciIiIiIiKKAQbwRERERERERDHQ96d/ qe8Bp6IiIiIiIioy/U9 cwLDOCJiIiIiIiIuhzvQk9EREREREQUA7wGnoiIiIiIiCgGYhvA/4f/8B/Mq 23k7/dSb26XERERERERL0gtin0Emy 4x3vMH9tr6i//QOH/9y8iualb/o2fOL9P2T 2n47WaZEREREREQULrQH/q// q RzWbNX50h3y /04te jvf6Q1DB5P42fSr8fNDr8bIT78G//xnvx//5 Hvx6/8/A/gl39 n3q9T62M580niYiIiIiIiKoF9sCfO3cO//W//ld8 7d/O/7wD//QjG2/o0eP4ju/8zvxsz/7s/jRH/1RM7axOPTAv aXP2FeAT/3T74L3/ANfTjwj27GT/7Qt pxn1x/Fg tP4erj72I51/ow/0rF3Hx//lJ/d5O2Oke N//g9ZS H/zN5g9QEREREREvcs3gP8f/ N/4L/9t/ GX/zFX0Qul8O73vUu8077SQD/z//5P8f58 ebCuKjBJuz//G0ebU1mbceM6 qRQ10f AXP2xeAb9wVwJ7/vdvwj /69tw4aEv4 knr En/slr8PQzz Od/ WLeO6lv4P/99xHcPHsXeYTwXZ6uUTp8mf1vy97WR9eemlTDS85g6pO3ms9OH /dt r9fRhmg3gf/RACn 9ljd/MYAnIiIiIqLeVpdC/8ADD jg/ciRI/jyl79sxnaW/M7rX/96/Pf//t/bnk7/T 9KRxouffm5qn/boe/FG97wsr4 XHv8Rcy//wr KPtf8d8/9Hmc/6vL NZv Ua87NlP4OkbarrNZ80nG7PnPWzoxHJ10uTb7q4a tNjeqgdL8M/3v9D3msiIiIiIqJeV9UDL73g9957L37hF34BV69exTd90zfhox/9qP43yKFDh/QQxE3FDyOf/4Zv Ab83b/7d/HBD34wUk981B74R778jPmrOa/8rm9puad63 GceQX84s/ MKSkX3zxeTz39Nfx8m/5TvxS n/DHd/zDXjrv/rPeOHm/bjwyS/iY2f mflEsJ1eLrf3XUTtgd/cfAn7f/AfmU/5kx54Nxg/8aEN/Gz/y/FvP/w87vv5v4P/7Zv69PggM 98F3vgiYiIiIiop3kBvJs2//M///O4du0avvEbv1EH1S972ctU8OUEYS   CKeffZZPPPMM3jqqacwMDCAj3zkI/j93/99/WV JEX n/2zf4YvfvGL kSAfO83f/M346abbtLf/8ILL C5557T3y/f/d3f/d34q7/6q4ZBfNQAPj300 Yvfy  6ASatT50LtdyoPuDh//UvAKO/HQKfX19ePZF4IXngJ/ 8Zvx2n/4Tfh/zz MhftyuK3/MC5 5K9w4YO/aj4RbKeX62Of gyeefppXS82nngC1597ETc2vxFPPvU0vuOmTXzvd91upqz2o//4B80rf3YAf/rCdfz/H34Rf/BjL8eBO27R4z796U/rf23f933fp/9lAE9ERERERL1Op9Dbwbv0vEtg7QbvEnQKCa43NjZ0cP Vr3xFp71LEB/F17/ df15CdRlkM997Wtf098l/8rfMsg06 vreO1rX9u2dPq/ejAfOqx9 CP48N9cqBvaYlMF0GZ4cbMPN54HnnuhDz/y/d sg/f/ ZHP4k/uXcW3/J0BvNj3rXjZZrTyFH7LYg dXC45 TL/n96Je//Le7Ghlqnvlu/BV595GS5/9WmsffpLWPkfDyDz5jGMPPR6vGX8DXjTG4 aT0b3S9/3Mvynn3o5kt9hRigSrNcOREREREREu4UO4CV4/7mf zkdvEsPuQwvf/nLdQ/r008/jccffxyPPvqo/vf69es62L5x44bukY9CAj45GSDBu/Tey/D8884j09wTBPJbbm/8ww8/jJ/5mZ/RQXyrfuUXf8YbfvLHD6DwmS9UjQsa2uHlfTe84Vm1uM88BxXEb LH930zPvqpr2Lu9BK 6dv6cdPf X48r8qyr8/3gQC /ObZHoKWtZ2 9dZvx0vf8h145ItX8aUvfwXXH7 Gxx57FC9987fh2vg1DB0bwtVjV83UzXnFK16BH/j7t DPv3ITzn7mhhlLRERERES0e kA/ld 5VfwP//n/8Q//If/UKe5S1AtAbr0uMsgPegSdEsPuQzynvwrAXcUMq0E/RK0SyAvv H jpATAfKeBO8y7U/8xE9geXlZZwS0Sk4MvPXUGn7 3/ NGeOMc4fHn7mKX/6LH6kaJ0M79L34hDfcUMH7cy  hOefewHf s19 MLnP4dvvPnv4 a/ 8N4Vo179hlVNi9 zXyyMXtef WBH8HHHnuwapxLXrvLb49vj0189suP6oyMJ1Tw/uyTG3heDc88/SRum78ND55 ELef9k nb0Sugf/I334d7/340zi45yYzloiIiIiIaPfSAfzrXvc6/PRP/zTOnDmDV77ylXjiiSd00P6qV70Kr371q/H93//92Ldvn05t/5Ef RH82I/9GH7yJ3/S9xprP7feeqv rAzyXclkEnfeeaceEomE7qF30 sleP/TP/1TfRd8 a1WyTzOjv1jLL3th8wYZ5wMX33qC5j4yHDVOHdoh5e9dN0bbjwnJyg28dwLL EP73sMf/Xhh4Fv FY88 wLeE4F1i 8fFNPF5U9ry9 w4v4g0  DR/ 6ofq5l9eu8tvj2/VPb/9u/jRH/0J/P  /dvw2h/6QRz8qZ/Ez75 EP/HLx5B8lV7sXjf/bj/dTnce2YZ933gg7j55pvNJ6P5B9/Wh1//i fxr/a/3LuBnVwDXzsQERERERHtFt5j5CQgP3z4sL4LvATV0isuAfWf/dmf4S//8i Rz f1HekfeughFAoFXLp0CeVyGT/1Uz9lvsHfL//yL PjH/ 4vtmdXNP F3/xF/jQhz7kDX/ 53 O7/me79E97z/ 4z u74QvN69rR/AupNc5k/0IRt75v8yYSu/1r390BHckfrhqnDu0Q9 mPBrOGV54cRPPv/CsTpW/6ZuA16ZeB9z03Xh 8yU8/ zzuPFUtMsRXPa8vuxlL8f3JQ7gPZ/ t3XzL6/d5bfHtyK595V6uO07vwNPfOnT MYXnsbLX3Iuibj lc9i/F/8nDeNO x79av0 1HJNfD/kdfAExERERERebwAXkjgLI90kyBagiM3RV7uMh80NArg5X2/z7mDkPR56dWXR85JJoCcSGgXCVr/8Nf2479N7DNjKsHvv3/t 3G55KTWu PcoR368KI3SOD /At9eOH5F/Hmn/8O/Iv038Odf 95vHDjBbzw0iZe2JTpnjOfbMye129S//vclU/i1171W3XzL6/d5bfHt rBj34cf/Jf7kXqNUl8/Utlb5DgvR3ca BvudW5Az0REREREdFuVxXAC0lhP3jwoO4pj3qNe6skxV5OGkjw3q6ed9vb//gC/o 5i avim /6bvwh/s/YP7qrOdffAnPPf8CbqgA/g/vu4o/vvfP8eG/ hCefeZLeO6lF/GSev9lTQTwVVRcfuxV/wb7v MnzIhqQcu/Vf/rEw/j/8n9GX71V34J/ S1P6CDdndolTwObisDERERERFRr/OeA19L0t1zuZx 7faUd8Jv/uZv6n bDd6jPgf 1371/zR/AV957An8x/n349/ 5hvNmGB//Cfva/l56amhf2teAf9g37/ACy/2YbPvRTx/YxPPP/M5vPDcE i7eS9eVKvgpZf68NLld J/5t5jPhGsdrn8BC1rq8v10YufwH1/eh4/l/4pHbwTERERERHR9ggM4MWHP/xhfa370aPNP8c7qoWFBX0zu2Z73qMG8K1oNYD/ifQ4sOlcGx5J38sjB/CtaGW5fud3fgf/bOin8cM/VLkkgYiIiIiIiDovNIDvZlGD6E7Yyd/upF5dLiIiIiIiol4Q2wCeiIiIiIiIaDfpK5fLDOCJiIiIiIiIulzfxsYGA3giIiIiIiKiLlf3GDkiIiIiIiIi6j4M4ImIiIiIiIhigAE8ERERERERUQwwgCciIiIiIiKKAQbwRERERERERDHQt7CwwLvQExEREREREXW5vuPHjzOAJyIiIiIiIupyfZuKeU27yJve9Cb80R/9kfmLGmF5VWN5dAbLtXkss53F8newHLYPy5qIdru z3/ 8wzgd5k/ 7M/w9/8zd/oA AXvvAFM5aCsLyqsTw6g XaPJbZzmL5O1gO24dlTUSkAviNjQ0G8LvM8vJy1QHwFa94hXmH/LC8qrE8OoPl2jyW2c5i TtYDtuHZU1ExLvQExEREREREcUCA3giIiIiIiKiGKgL4M9nbsWhU1fMX8b5DG7NnDd/BDmPzK2HUPtRiiOuy2bINnPrrfVD3Xa0a0j98SmLK6dwyKtXW6hjsh/yvjOjvmEXYhls0RWcOuSWmxoOnVJjtklVvd9tAvYF7RaD7eLKqUPePNrNKTl  DevtqnsiIgoduoC INDR3Hh0mXzl P8ygKODh00fxF1WrxOIByc3cDGhgxncBT7cfKi8/e543vMFLtRpRy8sthzHOc2zmFLxSJB0BHgjPm jYt3otx0Kz1e9apOYBlEXa6YL/9W6QB6Hy5NmnKT4TTwwHZFeVX1fjeuA599QTu1Zd/QaefxrrOHcVHP4xlgxpxAUvM gzOYDWxedbjsiIgolupT6O 4E/sXVtThxnUeKwtHwfidiHbM5Uu4sP9O3GH lKDo G7bJ7EMtuAKTh07gYEzG9VBEsuud8R2u5C6eQmTwdE7ERGRr/oAfs9dOLx/AStuBH9 BQtHh AdYnRvRiWlKzj1y 5lsP82r89Xvke w04vq0oTq/o9pozutKp0cb3yndTUqnog6YxuimpgfQmqI/LvESzgAk7sc38jjsLKpX4b2B11vnadWxot88EhHL1wAseqPhxWxs57lXoXUK98f7d /cjkgfuo7eJbBv7LVb d k1Xuz7sv2vLT08QP1cewNkL4Seg68tKj62rA/Y69/ M8Cs3t1xr18GpkPrb65wyyWRkmzLbXdA YEv7BrHVddgJB3H34bPYp3/vCDB5HCp6x6XJ2UrbKrI2lh0REcWSz03s9uCuw/tRLDsHuur0eXXg2Of0ZjipaidRPGI3AKNSDZgZ4LR8x5mjWDhyK47htPOd6u8LJ95lDjTye2dx2E0h05lnvd 06WZV6eILM2rd78HxSbUOvTM ps6oBsqeLdWXg5i1U9Fj2zsRVi7C2gZUueDEMVMuvVLnTZBiGo/h7eMoyyz14iIOn91nfV9IGZ9/F04MnDF1VXpf/epV2O9G3UdtJ78y8N9e6rfTJreruvIz4 PI7p31UV9W5o3AbTToMxK878PZwxfNe7XlVrsOjjfYR/SKoH3BBRTvlG1KgtigbXGr wZXs uwc/YcP2d T qFk1J/d8PtqtNlR0REceQTwEsn/GHg7AOqOXIF5eJ 3Om2fq6UUVTNDy e33Mck0cvoOaS QhUA a0aaTI2XP19 G7TJNF/12EPn gf886gB1ZqLs n7aZd7Mg6UkyZJ15l12cx0rxpNMwaVt9iamgctGsbcAul56p8yZI8RqsZrSfyMusAvZz6vv0iSDTmA0qY30p0JHwnvLQ3424j9p2PmXgx287bUaU8ouLC5cQugUFllXANir8PmN6 yebuU45dB/RK4L2BdY2FbQttrJv0Jpch9vkfGYGd6r5QsCN7Sq2o yIiChufAN4nUaPs3jgvGqQqFfucWJnHK3cnEaGWHcFxZyk43k3C7qIk/vNeBzE3SeL uz lVMzKB6 y2kw7XpRy0VOlJmX2m6s800ss2qIn1aVz m5DChjNc059T2ncSykcSxiWtZVZVAjcDttQuTy63K1l4TVilxW1jbajvL1cN9ZEbQtbnXfUKtT67BJ6rdnMInjewJubLclbSg7IiKKDf8AXjUhpBP xJETgN2g2NOPAViNITkQ d7g7g7cud8 072ytTPc5veY9tUl7JsF6d4mPVZzsjbepRokUmVMjQmtL22qI13Ot1y0Czj7gKnX9nW6u7HOR1nm86esFNcreEBVvv0mNSi4jNV7x8/homqdu5cEVYlbWYeUQZWQ7bRa420wtPxiwVxmUZutoPZFp Tv0LIK2EaDPmNOFjRbn8Lq764RtC22uG9oeh3ivLlfQdjrVlxp/43rWik7IiKKpYAA3mlU7LfTtLSDmDUpajolS19f5XcTlkqjSU 3IueBt8L5PZxwrm3TQ2y7guLGSr1Tg06lPXg3TuKEcyMe1QgZsHst9hzH5MACFgakZ8GMC60vYXXkIIaOmt P /r2LRexHwOXnN7NW/V9Atxy2Y11PsIyH zHJa8 7tPXZ3uPVPIrYy899lbsOzFg0ppr61XMyjqwDGqWK3A7rV3 kG3Qt/xi6uCsl1rtLtOtx4C7ZIML26cFbaOBn5E07jMYsOpTfXXy2bcF7iN2k6BtscV9Q9PrsLOunDqGs4fvduZB/bf2xnZbW/0tlB0REcVS38bGxqZ5TbvE8vIy/uZv/gZ/9Ed/hC984Qt4xSteYd5pjdzVd2WowfXOMdRqedWXi/TmzODOi1t8JvoO61T9aUUv1L1uLNdu17ky295tNK71t7vr7PatQ26724dlTUQU0gNP1BRJj /JGzC1iOXSeSxjijPWXyIiImoCA3hqkXnusaTHu3f7JYXl0nksY4oz1l8iIiJqXt/CwgJT6HchNwVtcXHRjKEwLK9qLI/OYLk2j2W2s1j DpbD9mFZE9Fu13f8 HEG8ERERERERERdrm9TMa JiIiIiIiIqEvxGngiIiIiIiKiGGAAT0RERERERBQDDOCJiIiIiIiIYsAL4EuXP6uHy498Tv97qfQIPn3pMh7 TBmfKq7jE4XP4OOfLOJjDz2Mj178lPlUuPLcAfSN58xfooy5A33o6zPDgTk1plpuvA8H5mrH0rbLjVfWU9849Fosz FA3wG0d/XkMN7279xusgxWvVZDVbWPqiPluxNMedQVQmVdy3Zul5c7HJibqytLb3/gVyd3laBtpZVtKOyzrXxvReU4IN9XvW63tJ00y6o39rFFz5c3L259qj5GBc2fXX rjlcBv1VHb uV76gcC3eojDompDyDyqphGW7hO2tte/kHz3NgXbLYdbX2s 2ZPyIiipPO9cCrA To0ghK82nv7wN9CRSnNiH3zdPDIrBSc/BJz5cwsjTacqORWiDrahBYdddTaQDrsp76J7C2uYaJfmcysqUwW3LLaxaFwS0EmD1VvimkCoOBjcv0vCmrzVWMWWW3NrFXvWuVpR6nCiSoTlIbtSdgr1J7HGjHdtKMqnqzimSmcmwpFfMYWzXzsjkPZw5L2Oseo4LmT33n rD7Ofs7VfkF/FYVmafEEkasOr6aLKpfdm1zGXVUUHkGlFXI qoI 86CKbtuK/ AeQ6sS7YcZmQbMtNg2pxsUJ dxiq8TYuIiHYNHcBLj3uzLnzsE aVv/LKEjAyBCcWKWNuNIOkaixVHWxUwDJRd/Dpx8RUEpmZ DZZYq9URD41gIT50389UaD vUiigHW/xuMuMjKlGqpuY7NVrJOxVH0cqLEN24n /dlJE5ynMTkLLK24P5jCgFehXGmk3Xql589HVd1LYCBlXuaWkR0bDvgtl3ssrD5Rl553TyDUiP2 JKA8A8oqfH25Ar6zvI5CagRDulzTGB7Lo1iJyo2dKv AeQ6qSw3JchQxxeidiGhX0gH8E08/g6uPPoavXHsUX7p6Tf/71ccex6Nf28DjG9ex8cTX8cSTT FJNd3TN27gxnPP4dnnX9Bf4K8Mp91mjpDlFSzlxzAcdKyRtDc7nT4xgFRhvfI3ba/0MMbyGYzWdQXYPXTmdW7OS0WU3lY71a SDlg/bWB6o/SOmGlimyatG6dTXgOxKl3c65L2S6m0y1f4TRMjiQlMJf3q0RYE1kmqE7AN ddDl9S9QWSRRyZR836pdrt16mXVV9Tuw7Wa40Ctmu1ke5WxXjDL6i1XjaogM0gJxXwSe9UylNcLSFlnBPr3JpGvjSAbHQtr7WgZtZlVnpHKKgp7HfUPYQRLcOL9HJazPuXcDeUfWK8qdalaGpMjS0jobXAQmJqAit5RnAo46UBERD1PB/A33XQTfus33oape95eN9zz9rfiHXcfR bNYxh56PV4y/gb8KY3HtUfDuZzILJ7zxqRM9R5O6WNtlca85tyKUNCN26DA0fVAJ4GFiW1b3UM2cE jGLRSQdUf czM1YAbk1bmgUCUgXH7dRGnS3o07DuSpVgQNpYq1bPSFW6eHbaWe7cDDLJVTO JjNFkyApgaWRUsg03S89H5LKGsgqS6/ Ra2Tva66bJxBAm9X8DbkWw89Ur7W5QxeZavexp1tWrKk1Pa XFkJueUsxlRgUR17 AUkwdtJJ jA0NsPyQmFvH6l3sHEWqU87DrqnYRcHrbKwV9ufBAFr8c4IutYWDnhaZ 4294y6rRmyjN4fVXz/061ThdVCK/LThec/3rZofJvVA5hdal/Ys3UVTkOOCn1k 2ZLSIiiqHI18BfG7 GoWNDuHrsqhnTpLCAPD2PzTW78SepZExB3lmmgauv1wsKmFRjf9GsN khVX97vW36b3sdWtP2T2DKL71RUiCrGk/ZrfXK7Aj7uskBTNsNQu/GSlagJVkm2cGQTASnp2gq9l1vKjBcbfaSGKssdYPVjI5UJ3tdddk4gwTeRtg25FcPG6rdxs02La zyybQymG5MBsxoAjZTjpBHVtKswUM6uUeRTHpl6PspFu7qdpesDS8rD4TNH9OFsL0QMm5R0MzrGOh81vW tO2uYw6LFp5GpHWV8B3SubJqDnZpIbh5YB9xA6Vf3A5NFeXcuPTGFDbpPqQ h5nO9 9JzSJiHanyAH8bfO34cHTD L207ebMU2Q1LZUFlaHTQNBqWS07VSwvTibqupta52kr5qXdcYqNyqToU29H9tK13dzgkIaldKLo5enBFWUDlWua2rcIkZ7vwGWnsRsyA3tmtaROtlLfLahoHq4ZXJ9ckH37pfnplEIus49jL2ddJAXOG2uYRh5JAMOLHXjVTC5GnQdtRMpVgVctWngtWniWrPXVG9TGW0LqzzDyirq tKs76y930J6uDpLROuG8q qV/51KZDajqchKf0BN7YjIqJdwQvg3/2eBd8hu3Av3vu 92Pxvvtx/ tyuPfMMu77wAdx8803m0/6qe1BNymXtb1m6mA0J3/XXj pb0bTRMo9tVdOrZfKytBpjHUN0aZVergCr0PUjatsjNLmA jlMzfIsm  psfLiwpprJZUNFWobVGak16xLwtNUlul17yZnt8aHamTPShoG2pQD7eif2gEWJpRgUTQde4NMqns7QT2/R CXrdIHWcG/TIFJCjKmvnI5UxWgZDrqH3mT1/ 4nNdtM6qqWQlzGT8ysW5MVsmEfH HlVlFENB5RmlrKrWl13 /t pTwosrXjtCLmso34fsUPlH1QOQXXJlwr2eeM6IiJSdACf3PvKpod9r36V/gJ//dBtO/vusel5L/XVTfvqGwWG/I5F0thM7m2 R4faI70XRTcFty hr9VuOk20TgrJotPb3JeQuwD7XZ Yxry Pt65zlkPsemattKW9TXI5i7H0vuMjHMDItX48jJCvXTmPiQySZ9UeUkXl2tzK2UR615602u ZR2pk70oYBsKqodVnFRyXY jVDa5FCaZRTYwAPE5DgRtJx0jgZ/5PclA8C7Vssbr/ZGZj8Q6pt3xzgfq5k96i5EdNNM4g74URrJqVmHSv/0/K3QPszedM21hdtGadrvLqIOCyjOwrILWlyXoO1Ubo Td7K0Pg/DfR xI QfMc2Bd8lGeG8XSiHWH/pob27U6i0REFB99m5Kr1gmSsimZYX4H4FBuSlkbDprUJaRRNo2BODdEiaiO3Nl eTjkBotbPg4QERERkZ/I18A3TXrc5Axxk92GuXHpXWvzY1uIiKi9JPW80c3rtngcICIiIiJ/neuBJ/KwB56od0iWVAKZvNytm9s0ERER0XZiAE9EREREREQUA51LoSciIiIiIiKitmEAT0RERERERBQDDOCJiIiIiIiIYoABPBEREREREVEMeAF86fJn9XD5kc/pfy VHsGnL13Gw58p41PFdXyi8Bl8/JNFfOyhh/HRi58ynwpXnjuAPv34ILkLeR/6rOHAXNmZqIY8VzjoPdpGuXFrfY2rNajIM537DqC9q0fqRru/c7vV1 8tPTWrI W7E6KVh2zrzv6hQsZVj/KpH1I3t1TAcRe0rbSyDYV9tpXvrQg7DmzLarT2ZZVji9xJP2A fKf3p5ftwJz6NiPqZ/W2Xvn9ynfsUBl1Esu/Qs fOZ66guY5wrLo5TfT2PNZvx8lIqJe0rkeeHWAHF0aQWnefUiwPHJoE3LT 83NVSQzCd9GeHq hJGl0ZYbjdQCadwMAqt6XamhNIB1WVX9E1jb5GOj/Fn1uzSLwmBNIy2KnipfqzxWx5CtLQ9Vx6YLYxgrTFdt6 lhNe2yNWV5HQXksbRSmai8XkBqIGH ovZpT8BeJew4sNXtpBlV zI57rjHlhL2TvnNhyoD3 n95DCTyZvXQj5bMMsX8lmZp8QSRrzj4SZWk0U1R65tLqNOYvkb5oTFMjBmxjiCljdKOajll23LTINpcxJCLd80VuFtckRE1HN0AC897s268LFPmFf yitLwMgQ/GORNObVgTGVXfY5MPZjYiqJzExsmyzxVyoinxqAFyKpwHKCjYHo vciqcLO9cCG5y6THlaN1urycPYPk5gcQVVwjsQAUoV1r0dNpkvOzgJFt3ldhrNr4VmkOAg9DmzDdqJ/f3ZSHXFEGpOqKjn1LY20u0/T82HklpEdG/aZvl55blp9tzqOmb/1yabUCJyqmcbwWL5SbT0qkBvNILlafaIuPT9vfrNGzPclLH XatesqUB7ftj8bQQtbxPlUE2Wr4gpRu9ERD1NB/BPPP0Mrj76GL5y7VF86eo1/e9XH3scj35tA49vXMfGE1/HE08 hSfVdE/fuIEbzz2HZ59/QX BvwiN7P4hjKSy0J1tkipmp8HVNOJpm0nAlc9gtO6Uf87qoTOvc3NeKqIkVNgpfZW0v/ppA9MbpXfETFOXahgXuvE15TUQdaq4u0xe1olfCqldvsJvmhiS8vAa1qKyf gf0hF8ZVuX/QKW4LRVnekGhlQj2jvZV0Ixn8TekF3LrhewDfnXQ5fUvUFkkUcmUfN qXa7depl1VfU7sO1BseBmu1kx1jBUm12R//eJPL1UaAu49HiFOaHzN iqu7msJwdw3BtHFVewVLeZ3yQbimjTtrF5R 0vNHKQQX2I0tI6G1zEJiagIreUZwKOBlBREQ9QwfwN910E37rN96GqXveXjfc8/a34h13H0fmzWMYeej1eMv4G/CmNx7VHw7WYiNbznrn7ZQ22l5pzG/KpQwJ3WgPDhxVY38aWJQUPp0m3YdRLDqph rvfGbGCx6qpi3NAgEpgeN2aqPOCqybqEuZwEcaU5L6aPWApOfN8qgFGsualPHcDDLJVTN 0yfdUYKkBJZGSiHTdDOrPJaHsbk2UemFlUa0amrruK6q0S36sTfp9pyp/YieTnrTTC Y1djfnaxy9QYJvF3B25BvPfTINq/Gu nDXmWr3sadbVqypKovdcgtZzGmAojqXb7fcSB4O kEHfh4 yE5oVBJufZONkr9bGo pJdTlfFk7WdUuSyq2qyXTy cfz21spsqJzztE3fbW0adxPLvrP6JNev44KTU1xULERH1nMjXwF8bv4ahY0O4euyqGdMOKeiTzOn56ga OrwOpOKbNtgbTMqfvgYwKIhXjf1Fs950mnSq0ttWlzZtTds/gSm/9EZzvXOl8ZT1733pSvZ1kwOYthuE3s2IrEBLskyygyGZCE5P0VRsu95MefhcKlOdVt0P6YS3L5nxroOXYD25V0 nikunkPL6d6ueeYME3kbYNuRXDxuq3cbNNi2vvfWaw3JhNmLgELKddII6tpRmCxjUyz2KYtJLuK4EP8PL6r3o81GeG8XSyGJ9r6xkPoyakx1qGF4O2G9aJ6edebDWn7bNZdRJLP9tkxufxoDaVmFlwQWffCciojiLHMDfNn8bHjz9IG4/fbsZ0yIdoAT10jNNtmuoYHtxNlV9Y7GWlaHisABj5sY9Zohj75O PMScoJBGpfTi6OUpQRWlQ9 wbhOLGO3thpauPwUrk8K58VRebmJpGpkJuRGVHeSbS2hyqpKMmVxXnWpfXAlPySbDZxsKqodbJtflOutVrkUuBN7vJIS9nXRQpZdyDcPII1l7YFFB5qo5oVibqlx/wqim/iYyyOczSByYQ67qxJSc46i5IaNo9prqbSqjTmL5Bwta3sblUENt39OQVP AG9sREVFP8QL4d79nwXfILtyL977v/Vi8737c/7oc7j2zjPs 8EHcfPPN5pN GvWgS5qn3EjGpLjVXj pb0Zj3USNtlduzupxcNIeW /1tO4kHnQdom5cZWOUNh9AL5/JLrFvCKjHy4sKadyWVDRVqN1YdMOxB8pC6Z YqtxFWXrVU7OmgekOElCa 2EIWXZkMJiBU4Z6nFwHn0GGJ/bCBW1DDerhVjj3L5hRAUPQSZUGxwF7O5FjgtfTGfS6Reo4M hmCuRy6ptdcr20mQ dGVPJLJhRddBZNnc 5FIDq 5KhonU57UJpCXosu7nIJcV1O83nRuSZRIR7 9RVUYxx/KvF7S8geXgRy4p4I3riIh2Ex3AJ/e sulh36tfpb/An5MWW33XVCuts28aA6WQa3qlsWlSZ2kHpPei6K2rhL5We63lVO4UkkWnt1l6TbyTN1WcpxOoimJ Ww2x6Zq26re Btnc5Tg9iVkVjOobDalGlpdB6qUzSw900idVXi5hkMcHVcoivr30ptE8Ooc5aVTX9dbK/sLO8nD VhNaN76T6 DVP7v6 vcoArahoHpYxblzt67HUSqbXAqTzCKbDLrJV4PjgL2ddIwEfub3JAPBvVQrsY5pd7zzhjMfkhmzCpPybY2PQtLFvZuK9WEQ/vtN3SPt/YbzO4VZOyV8u8uok1j oYKWt4lycC4psO70X3Nju07NOhER7Zy TTmN3Qnu9WhV17ZHITfv0h/s3EGTtpk04uSkDdcpUS RO9svD4ecjN3ycYCIiIiI/ES Br5p/RNYlDPBTXYb5salx7fHH5tDRBR3ct1to5vXbfE4QERERET OtcDT RhDzxR73AecZjJy926uU0TERERbScG8EREREREREQx0LkUeiIiIiIiIiJqGwbwRERERERERDHAAJ6IiIiIiIgoBhjAExEREREREcWAF8CXLn9WD5cf Zz 91LpEXz60mU8/JkyPlVcxycKn8HHP1nExx56GB 9 CnzqXDluQPo048PkruQ96HPGmqfKiTPEz4wVzZ/0Y7LjVvra1ytQUWe6dx3AO1dTVI32v2d261x/Y6kI W7E rLo3bblu3d2TdU6HE1n3M m8Pcgcrf9sfsz/T /iNoW2llGwr7bCvfW9HMcaAT9O97v2n2ZS69n6se17hOmeUImHnn99xy25ll7iYsf4vP8jrjfJY3aLzFLlt7uaQMd1s9IyLaTTrXA6 CkdGlEZTm3YcEyyOHNiE3vZfBG22k50sYWRptubFIbSCB5CCwatbVZmkA69IY6J/A2iYfG XPqt lWRQGaxppUfRU VZv72v2Qunnh49hrDBdtb2n593pVzFmfX5tAtg7Zd6zy1Z9z/pw5TPJDPcfrZFgp/WAvUrYcWCr20mTSsU8xlbdejIPZ07kUXgq8FmGqmuWyHUqhVRN/XXkMJPJm9eu7V/mbsLyFwHLq Zk3DvW2ssbNN6mllW2LTMNpufUryiyf8VqXRuLiIh6hw7gpce9WRc 9gnzyl95ZQkYGUL0WKQfE1NJZGZ2U9OmS5WKyKcGkDB/SmA5wcZAdP17kUQB674NT3L2DZOYHAGWVqIUUhppt/7psjWq6mUCAynzkrpG6HFg27aTFAa8nZlLHW/WVOAzP2z NpqoU0lVEevqb24Z2bGxmiDNsiv3DSz/wOXV8ztsTmqkMTlrlilofENlzI0WMcXonYiop kA/omnn8HVRx/DV649ii9dvab//epjj PRr23g8Y3r2Hji63jiyafwpJru6Rs3cOO55/Ds8y/oL/BXhtNuaxC S4rYAXPWWCQGkCqsV/6mnZEexlg g9G6U/52D515nZO070oKn53SV0n7q582KCVQeg/caepSDeNCN76mvJ70qtRwL6/R9MiY8c5ou3yF3zRxV9k39A/pCL657b2qYWsroZhPYm/0M4a9K2Ab8q HLql7g8gij0yi5v1S7Xbr1Muqr6jdl2sNjgM120lnlLFeMMvkzX9U4XVqYHIKycyMtY9S5TJdwOxkTZBm25Zl7iYs/zDl9QJS1tmN/r1J5IulwPHVVGA/soSE3jYHgakJqOgdxSk3y4GIiHqVDuBvuukm/NZvvA1T97y9brjn7W/FO 4 jsybxzDy0OvxlvE34E1vPKo/HMzvwFs5iAcGZnJ2PF9Un6adlcb8plzSkNDrKzhwVOt0GliUFL7VMWQH zCKRSdVUf2dr2pcWdOWZoGAlMDxxBJG3HRHnRXYTINvJ1n1W1IfrR6QqtTwrEn7zM0gk1w14 svKdGN0QMJLI2UQqbpZvb2btWh8grUGoaO6fqH1KslROlY8k4MLQ9j06cgcuODKMxO7oKGa3W5OoME3q7gbci3Hnpkm7cuXfDKuHobd7ZpyZZS2/tyZevOLWcxpgKI6riowXGgZjvpDNPzaZa7mcssGtepNIbHsvCKwa7bVbZ7mbsJy7 T ifWTNnK8cFJqZ/cTdWLiGiXinwN/LXxaxg6NoSrx66aMc2yrkNzr4NLz2NzzW70ScocU4 7g2l46WsGg4J4tU4XzfqTXnv1t9fbpv 216U1bf8EpsbyqOtQKK rT9iNraxPr0O3sq zHMC03ZPu3YzICrQk2yQ7GJKJoBqj TFMxbarzt7eKycfqlOq yGd8FEum/EaqsPLqhzrsxSmB0rV19n3rOpydQYJvI2wbcivHjZUu42bbVpeZ5fNCboclguzEQOHkO2k4yTgy0dIRY5ep9KTav9orj3OzWSQrDuJIXZymbsJy7 TcuPTGFDbqio8s533StYWERHVihzA3zZ/Gx48/SBuP327GdMJTIPtOirYXpxNVfW2tU7SKs3LOmOVm fJEMfeEulZTpkTFJLOLL0 enlKUEXpUOW6psYtYnQXNbScG0zlM05mhwwJueGUFwhGkJ7HqnfyRxr6o9I9vEuC96h8tqGgerhlcl1uQfful emUWjqfieGvZ1so2ToAabJOuVmkeTkxowRTmLs0DJ3E5Z/RW1qvJs6HzQ kL5xnVwaEHBjOyIi6ileAP/u9yz4DtmFe/He970fi/fdj/tfl8O9Z5Zx3wc iJtvvtl80k/EnvTa6yal98i eRrtDNUYsns4V5by4Y2HSKyeF9O7PFzb2NI3GMrGKG0 gF4 c Mm 4aAery8qJCe5ZKKpgq1G4tuaPZAWdjk tPUrGlcuoMEk1YarJ9czgrwc1jOmrLVlyHspuuJIwjahhrUw61w7mEwowKGoOvcGxwH7O1Erde6 2vUvW6RBDlu3QnSdJ2SywmSyAxmrMySEFXLvMuw/OvpTKxKJsuMXgy1FEHjfZV54zoiol1GB/DJva9setj36lfpL/DnpMZWp8pZaZ1q8E0dlkZmcm/jgzB1Vnovit66SuhrtVvv4UwhWXR6m/sSGSRX/W60k8a8vj6 0kMb9Kzf7mPVb30NsnkcXHoSs8g4NxpSjayk2/PppTNLL3TSJ1VeLmGQa0YrZRH3Xnq5TjpV18iWfUWDDI/EOqZNGeibNa06ZSu9UsgOeuUjQ3M3yepFAdtQUD2s4qQ463ocpbLJpTDJLLKBAVeD44C9nXSMnABwf0/2O G/t6U6JWWbCrvcZbuXuZuw/ENJJtYqMKiXtbJvCxzvozw3iqUR914B9Te265ZFJSKi9unblG6wTpCUTcmEq7rGPYybOrebGje7hTTipjGwqxquRL1P7my/PBxyg8WmjwNEREREFCbyNfBNk2un5UxwxG7D3Lj09DIdlogoFiQlutF1x00eB4iIiIgoXOd64Ik87IEn6h2SLZVAJi939 Y2TURERLSdGMATERERERERxUDnUuiJiIiIiIiIqG0YwBMRERERERHFAAN4IiIiIiIiohhgAE9EREREREQUA14AX7r8WT1cfuRz t9LpUfw6UuX8fBnyvhUcR2fKHwGH/9kER976GF89OKnzKfqlecOoE8/MkjuPN6HPms4MFd2JhLyfOC A7BHVZPPh71v5Mb9v7 Twua94XI1S 74XClD92lM8vzlji6vVa59feNqbShtXzYRcT13tfq6vqWnZnWkfKl3BG0rrWxDYZ9tz7YZdkzYjqfL6d/3ftPsy1x6P2eP89/fVjPLETDzzu 55bYzy9xNWP6WuuVVgtowQeMtdtnayyXtg91Wz4iIdpP29sCrAGR0aQSleffBwPKYoU3Ije43N1eRzCQqB93 CaxttvoIInVwHgRWve8fbbmx6U8aAVZDtmrew95rhxL2TpkyLM2iMOgc/NPzJYwsdWh5JZD0ylV dwDr8qNtX7ZeYtV1az01heVLO6pmX9YOoceETXijO6hUzGNs1f3NeTg/aQLFZWBM/ 3y39/WSyFVmPYpqxxmMnnz2tWGfUOMsfxF0PIGtWGitG3Ussq2ZabB9Jz6FUVtc9NY3ZZti4iIdoYO4KXHvVkXPvYJ86qivLIEjAzBP/5IY14dPFPZ5fYdPHPLyI4NmwZBGpOzwNJK3VEu5tJIuwfi/r1ImpfqD0xMJZGZ6UBTpFREPjWAhPlTAssJNgai0 upgPVeq4pETQo/JmyXFAa8nZlL7T/XVOAzP2z dgXtb sl1Zt1xxt9TBqrCdIsu3LfwPIPXN6gNsyW2zZlzI0WMcXonYiop kA/omnn8HVRx/DV649ii9dvab//epjj PRr23g8Y3r2Hji63jiyafwpJru6Rs3cOO55/Ds8y/oL6gow2mrhTTV ocwkspiWcecdm9Po7Q5mVa9V/NGeb2AlNUy6N bRL5YMn 5zO/kJD3Z X47HU1SzdzfrXy/85nxcTc9bRBZ5JFJuNO48y7/Br2nv0jNZOV3ZagsgplurnGanKfqoK4kBpAqrDtn3dspPYyxfAajdfNjL5t5bZWrLJud0ldZnvppA5e1qrxi2lOl19OU15PuX8f86nxN3Wm4XRD5CNiG/OuhS pe7b7MKNVut069rPoKSfc9YHoAPRGOCR1XxnrBLJM3/xHV7m9rDExOIZmZsfZRqlymC5idrA1KLTX7ht7H8g8T1IaJ1rZRgf3IEhJ62xwEpiagoncUp9wsByIi6lU6gL/pppvwW7/xNkzd8/a64Z63vxXvuPs4Mm8ew8hDr8dbxt AN73xqP5wtRKK ST2buXAmJtBJrnqpLipofrksTQWdS4ZNrd8Vlk1IKaBRfn 0ixgpaOl553flBS0saydkpdHYWCx8p6bhlc1D2nMB74nVKM4kUHSTR/U6Xt2gKbmqzjsvLc6hnxVY6TCC4qX1bT2b0hvQr6oSr7dZLkkRT hfzc4cLTKVc1/drAPozBlVrc8weugQsprCSNuuqPOCmyiwbejKo1UaUutWuvJt46F1nkh9T6BpZFSyDS0 1j1zBsk8HYFb0PB zoRtC r3sadbVqyf9T27pyJ1XLLWYypAKJ69 93TLDnfztO0JmeT7PcUS6zCtzf1kljeMw9Ia2UV6BKHvXnK4L3Db2P5d9J/RNrpmzl OCk1E/upupFRLRLRb4G/tr4NQwdG8LVY1fNmK3ySaeTnuTsoO/Z aVRJ4hp7ZirGqWLpnHZP4GpsTy8k9nejWLsRrBItd5zVF5HQTWJh915r/1tmS/3aCu93gGpfd5BenhZzad9AiCBgVSn0gFNw0ufdAgK4q1y1fNvlVnd8oSsA5cuL7uxlfXpdehWJvCR9VQawLS9nvzqWEid16Qxmh/DFC IpypWPfMGCbyNsG0ocF8XpnYbN9u0vPYuh8phuTAbMXCw53 7ewol4Ms3TEUO3t/WS0 q/aO59jg3k0Gy7iSGCNk37Cos/07KjU9jQG2rCLixHRER9Y7IAfxt87fhwdMP4vbTt5sxW6CDEp9een3zrk0sYrTmoCM3o0kFBnG1aWW1aWf JKXPfTln3aythNmUGd t0vNYrQp8W8h6iEqtm0VVMHZvW usdVBnrHLzPBni2FuiLxUx6ymojgXWeaJW WxDbd/XyXW5Bd27X56bRmHHr3OPLhl1h1m3v/Uh2zqWsJKbw3SUkxj2vmGXYvlXBLVhmm7bqO17GnJpQMCN7YiIqKd4Afy737PgO2QX7sV73/d LN53P 5/XQ73nlnGfR/4IG6  WbzSVej3mA3nTy410XOvJdUy7LgfUkKI4trWEVAT6Xuxaz0As1kgq63tM76m55N3Stu36xNj5cXbaRvmGOn KmDbNbqkY8ilzPLJ3JYzloZDNLbZt9srl1UY6hS3HIdaz7CiZFGAtaBzZRXfNLmA jlM upQR2rr/OGbmj2QFnQ9grahjqwr sfGgGWZlTAELTfjZohJNffu72iQa/bQO9//W6oZgnb3/qSywmSyAzqg0/jkxj2vmG3YfnXC2rDRG7biDJvXEdEtMvoAD6595VND/te/Sr9BRX90O25qvQ4 3rHaQyUAq7jtZ53msgk69KGnUemJepvkiS9mKvAoP6sdC8FPYIrhWTR6enss08ipCcxi4xzExh1AEwG9ko5qX96Weq6SsPfkzvvSwq689tybWqTaaOJdUzr5ZOhZhmlUZ7c27jR0qz0XhS99ZbQ12qvtZzKHbAOqjjlpQrT/LYaYtM1bdV1vZ7NegqqYw3qvG6YqsqtH71opmMvPTUWsA1F2teF7ct8yKUwySyyyaCbgjU6JjR5U7MtkZMA5vf0fqfBYxrD9rdBpGxTYZe7BOwbdgWWf6igNkzkto2cFxnF0sikOZ7W39iuWxaViIjap29TcizbRdI0R4HFtW46aEgDQk4edNFBuy3kJme6sGOwXL26Doh2N7mz/fJwyA0Wu/KYQERERBRfka Bj6R/Aoty9pddhR2XG5ee8d30OCIi6iqSEt3oumMeE4iIiIjaqr0BvKLvIMtrsTpOPxKK5UxE206yf0w6snuH hA8JhARERG1T3tT6ImIiIiIiIioI9reA09ERERERERE7ccAnoiIiIiIiCgGGMATERERERERxQADeCIiIiIiIqIY8AL40uXP6uHyI5/T/14qPYJPX7qMhz9TxqeK6/hE4TP4 CeL NhDD OjFz9lPlWvPHcAffqRQfLs7z70WcOBubIzkZDnA/cdgD2qmnw 7H0jN 7//Z0UNu8Nl2vrdNkemIN8tTx/uaPLa5VrX9 4WhtKR5Yt4nruavV1fUtPzepg3aFeELSttLINhX22Pdtm8DFhG u63p Z/VgdM18BG62ef29ea5dhi9v6bsPyd/iVQ1AbJmi8xSmb nKQ9gHrJRFR72pvD7wKQEaXRlDyHhmUwmxpE3Kj 83NVSQzicpBun8Ca5trLT7HXB3MB4FV7/tHO9QglEaD1dismvew99oph5lM3ryWx8iVMLLUoeWVQNIrVzWUBrAuq61jy9YLrLpemkVhMKixGoLlSzuqZl/WDiHHBLWZIDPqnJDsHPPIu2VgzIzxl0KqMO2z7NX7XUcbtvVdg XvCCqHoDZMlLaNKhvZtsw0mDbbktrmprEKPrmRiKh36QBeetybdeFjnzCvKsorS8DIUMBzgdOYVwfbVHa5fQfb3DKyY8Pqm0Uak6pBuLRSd5TrCeW5aWBWlZ/5W0V7mJhKIjPTgaZLqYh8agAJ86cElhNsDETXvxdJFLDem1WRKLKwY0L/xBTG8kvo7C5b7SfXVIAzP2z DpZM hw/9DFmLDj45LbeAMvfEVAOQW2YLbdtypgbLWKK0TsRUU/TAfwTTz Dq48 hq9cexRfunpN//vVxx7Ho1/bwOMb17HxxNfxxJNP4Uk13dM3buDGc8/h2edf0F9QUYbTVgvpPuwfwkgqi2Udc9q9PebstE8qmEOmVe/VvFFeLyA14IWZ6lieRL5YMn 5zO/kJD3Z X47HU1SzdzfrXy/85nxcTc9bRBZ5JFJuNO48y7/Br2nv0jNZOV3ZagsgplurnGanO7FKk5hfsj87UoMIFVYd866t1N6WDWsMxitmx972cxrq1xl2eyUvsry1E8btqyV8oppz5ZufE15Pen dcyvztfUnYbbBZGPgG3Ivx66pO7V7suMUu1269TLqq QdF9zeU9FhGNCFxmYnEIyM2Ptc9RyThcwOxkSfNZs67R1u7H8g9ow0do2KrAfWUJCb5uDwNQEVPSO4tS8CfyJiKhX6QD pptuwm/9xtswdc/b64Z73v5WvOPu48i8eQwjD70ebxl/A970xqP6w9VKKOaT2LuVA2luBpnkqpMSp4bqk8fSWNS5ZNjc8lll1SidBhbl 528TS9ISs87vykpaGNZO4Uvj8LAYuU9N22vah7SmA98T6hGcSKDpMy7 e3CoB2gqfkqDjvvrY4hX9V4canlH13CyKTPskvvQ76oSr7dZLkkRT hG 3BgaNVrmr s4N9GIUps7rlCV4HFVJealnd9EidFVg3UZcygY80pqS6WnXBt46F1nkh9T6BpZFSyDS0 1j1zBsk8HYFb0PB zoRtC r3sadbVqyf9T27pyJ1XLLWYypAKJ69x9 TJCsomxqBN0T36cxPOaeYFbKK1Al6TN/wds6tYLl36z iTXr OCk1Ps1FYiIqLdEvgb 2vg1DB0bwtVjV82YrUrBOrHskJ7k7KBvr zSqBPEtHaMVo3SRdO47J/A1Fge3sls70YxdiNYpFrvOSqvo6CaxMPuvNf tsyXe7SVXm fVMDy3Kha/sWAHoYEBlKdSh80KX/6pENQEG Vq55/q8zqlidkHbh0edmNs6xPr0O3MoGPNKZKA5i2e9L96lhIndek8ZofwxS79qiKVc 8QQJvI2wbCtzXhandxs02La 9y6FyWC7MRgwcKvOWyCSxulYb9O s9KTa35lriXMzGSTrTkqIkG2dWsLy37rc DQG1LaKgBvbERFR74gcwN82fxsePP0gbj99uxmzBToo8emR0Tfv2sQiRmsOOnLzmlRgEFebVlabduavDDWZeTln3aythNnKBeZdwrmBT15u/icH5EQG XwGCS9VtYWsh6jUullUBWP3trXOWgd1xio3z5Mhjr0r lIRc4IiqI4F1nmiVvlsQ23f18l1uQXduy896YXAe5/Usk9AdGGqr2y7WMJKbg7TUU5K2Ns6tW6XlX9QG6bpto3avqchlxIE3NiOiIh6ihfAv/s9C75DduFevPd978fifffj/tflcO ZZdz3gQ/i5ptvNp90NeoNdtPJgxttkg5WUi3LgvclKYwsrmEVAT2Vuhez0gs0kwm63jJfuQGM6dnUveL2zdr0eHnRRvoGO3ZKoDrIZq0e YYkrdVt7KpBbgKYmkXJ7bWS3jb7ZnPtohpPleKW61jzEU6MNBKwDmymvOKTNh9AL5/JNGlQx rrvKEbpj1QFrS9grahDuzr odGgKUZFTAE7XebyRCSa/DdntSg19tBLg9IIjOoDyaNT0rY2zq1wS4r/6A2TOS2jZDL7HjjOiKi3UQH8Mm9r2x62PfqV kvqOiHbs9V3SnVSuXsm8ZAKeA6Xut5p5JWWZs27DwyLVF/kyTpxVwFBvVnpXsp6BFcKSSLTk n9GJ7JxHSk5hFxrkJjDoAJgN7peTaPLMsdV2l4e/JnfclBd35bbk2tY29TtIoT 5t3MhpVnovit56S hrtddaTuUOWAdVnPJShWl Ww2x6Zq26rpez6YuBtWxBnVeN2RV5daPXjTTsZeeGgvYhiLt68L2ZT7kUphkFtlk0E3E/I4JMSBllQq7fCVgW6f22E3lH9SGidy2UeG7vsxu0hxP629sx6pJRNR7 jala7ddJE1zFFjsqusapQdHTh70WiNLbnKmCzsGy9Wr64Bod5M72y8Ph9xgsSuPCURERETxFfka Ej6J7AoZ3/ZVdhxuXHpGefji4hoh8glQY2uU YxgYiIiKit2hvAK/qxJrwWq P0I6FYzkS07ST7x6Qvu3eoD8FjAhEREVH7tDeFnoiIiIiIiIg6ou098ERERERERETUfgzgiYiIiIiIiGKAATwRERERERFRDDCAJyIiIiIiIooBL4AvXf6sHi4/8jn976XSI/j0pct4 DNlfKq4jk8UPoOPf7KIjz30MD568VPmU/XKcwfQpx8ZJM/ 7kOfNRyYKzsTCXk cN8B2KOqyefD3jdy4/7f30lh895wubZGnrfsLKfz3fJ3R5fXKte vnG1NpSOLFvE9dzV6uv6lp6a1aG6Q70iaFtpZRsK 2x7ts3gY8I21XXfY4S5k74ZX7e96s Y/Z4PvUzms/Z0lf10g/2z3tYr0/YdmFNzJGrLaIv7km7C8q/wWy7f8lGCxlvscrDnU8oh9vWGiIgCtbcHXh0UR5dGUPIeGZTCbGkTcqP7zc1VJDMJ05BT iewtrnW4nPM1cF2EFj1vn 0Qw3CmoZs1byHvdcecjCeHiiZcnS Oz1fwshSh5ZXGjdeuaqhNIB1WW0dWLbeYdX10iwKg8GNz0AsX9pRNfuydgg5JqjNBJlRN3DqkKp9mX2MKGHvlN/2agLLZWBM/ 2vVMxjbNV8fnMeeunUb60Pu NCjkcyT/IIPu/YuInVZFHNkasN 5JuwfI3gpYrqA0TpW2Tw4xsW2YaTJttSS3fNFbBJzcSEfUuHcBLj3uzLnzsE ZVRXllCRgZCngucBrz6mCYyi634WBo5JaRHRt2Dt7qv5OqQbi04nfEjrMclguzWKyL6voxMZVEZqYDTbtSEfnUABLmTwksJ9gYiK5/L5IoYL3XqiJRk8KOCf0TUxjLL6GTu2z9 7OTPseINNLuPk1vry61X11TAdH8sPk7SAoD3g7SqNpPJjCQMi rqEBuNIPkavWJuvS8CUJrxXxfwvJ3BSxXUBtmy20bWb4iphi9ExH1NB3AP/H0M7j66GP4yrVH8aWr1/S/X33scTz6tQ08vnEdG098HU88 RSeVNM9feMGbjz3HJ59/gX9BRVlOG01//Bd6x/CSCqLZR1z2r095uy0TyqYQ6ZV79W8UV4vIGUdxfv3JpEvVs6jO8zv5Oa8lDk7Hc1Ouat8v/OZ8XE3PW0QWeSRSbjTuPMu/wa9p79IzWTld2WoLIKZbq5BmpwcyJNFzLjf4aX6KYkBpArrlb/bJT2sGtYZjNbNj71s5rVVrrJsdkpfZXnqpw1KCawur5j2POnG15TXQPSvY351vqbuNNwuiHwEbEP 9dAlda92X2aUardbp15WfYWk 9r7Ji3CMaEbVAVLUZSxXjDl5JVJrRKK ST21i56eQVL TEMR/2xmn1JT9rF5R/UhonWtlGB/cgSEnrbHASmJqCidxSnAk5GEBFRz9AB/E033YTf o23Yeqet9cN97z9rXjH3ceRefMYRh56Pd4y/ga86Y1H9YerBRwwo8jNIJNcdVLW1FB98lgaizqXDJtbPqusDvbTwKJ8f2lW8ja9ICk97/ympKCNZaet4CmPwsBi5T03ra5qHtKYD3xPqEZxQs72m9/Q6Xh2gKbmqzjsvLc6hnxmxj9gzRYwYFL6VpNWYC29A3k79a9dZLkkRT hG0jBgaNVrmr s4N9GIUps7rlCV4HFVJeVmqjzgqsm6hLVRqU0pZateqCbx0LrfNC6n0CSyPupRN 09DuY9Uzb5DA2xW8DQXv60TQvqx6G3e2acn Udu7cyZWyy1nMaYCiOrdf/gxoTw3jWxqBJ2M73Xg4 2H5IRCXr8S3snGZbUPbmrjMr2ppiz90ptz44MoeD3PNazspsoJz5rjQsC JG5Y/p3VP7FmykGOD05K/WR8qwsREUUU Rr4a PXMHRsCFePXTVjtson9U16krODvmfSl0adIKa1Y6hqlC6axmX/BKbG8vBOZns3irEbwSLVes9ReR0F1ST2zvbX/rbMl3u0lV7voFQ9qwcgPawa0d4XSJpgp9IrTSNJn3QICuKtctXzb5VZ3fKErAOXLi 78ZT16XXoVibwkcZUaQDTdoPQr46F1HnN9BRN9XTXGzXPqmfeIIG3EbYNBe7rwtRu42abltfe5VDOZT7RAofKvCUySayu1Qb9bZaeR2m2gEG93KMoJit51V7wM7ys3rMDuGakMaz2ZZX0Zic7Qe5Zsha07VonXZ15sNafFrIviRuW/7bJjU9jQG2rqgD09iVD8Ml3IiKKs8gB/G3zt HB0w/i9tO3mzFboIMSnx4ZFdCtqYPlIkZrDjpytj4VGMTVppXVpp35k/Q79 WcdYOdEmZ9r5nrZi1kPUSl1s2iKhi7t6111jqoM2bWhxni2PukLxUxJyiC6lhgnSdqlc821PZ9nVyXW9C9 9KTXgi890kt wTE9qT6Vnop1zCsjinJ2h2mCjJX/U4oNsH5TgkeRyVdITh4bPaaantfElMs/2BBbZim2zZq 56GnOgPuLEdERH1FC Af/d7FnyH7MK9eO/73o/F  7H/a/L4d4zy7jvAx/EzTffbD7patQb7KaTBzfa5EBfUi3LgvclKYwsrmEVAT2Vuhez0gs0kwm63tI6Q29fA2ffrE2PlxdtpBsL7jX/ihxks01cfyd0T5eb7qoaKNNZjLlfIL1t9s3m2iU3Z/U4OGmPjU MNBKwDmymvOKTNh9AL5/JNGlQx rrvGHuFxH7sqDtFbQNdWBf1z80AizNqIAhaL/bTIaQXIPv9nQGvW5RbhyDbqZALmeOGyKH5axPZliVgPnQ 3TzWX1ZTKPrpZ0bkmUSEe/vYe9L4o7lXy oDRO5bSNUu4A3riMi2lV0AJ/c 8qmh32vfpX gop 6PZc1Z1SrVTOvml9HbfvMcZL7XTSKmvThp1HpiXqb5IkvZirMOl50r0U9AiuFJJFp6ezzz6JkJ7ELDLOTWDUAdDK7qvhpOnpZanrKg1/T 68Lynozm/LtanN9jrJd4xgSZdjQl837ZWhNMqTe9ufgprei6K33pzfDOzRiCxgHVRxyksVpvltNcSma9qq63o9m7oYVMca1HnZniZU5daPXjTTsZeeGgvYhiLt68L2ZT7kUphkFtnAoMnvmLDdJPAz5aAPESZlP7GOaXd86LHDj/Wdel/mfFZ6SZEdNN/pDH4nnnWPtHfckkGu1160fj9gXxJLLP9QQW2YyG0bOYcxiqUR607/NTe269SsExHRzunblNy2dpE0Tclg6/R1jU2Rg72cPOjgQXhHuOmCcViuXl0HRLub3Nl eTjkBotdeUwgIiIiiq/I18BH0j BRTn7y67CjsuNS894o3RBIqIOkfTlRjev4zGBiIiIqK3aG8ArOj2N12J1nH4kFMuZiLadZP Y9GL3DvUheEwgIiIiap/2ptATERERERERUUe0vQeeiIiIiIiIiNqPATwRERERERFRDDCAJyIiIiIiIooBBvBEREREREREMeAF8KXLn9XD5Uc p/ 9VHoEn750GQ9/poxPFdfxicJn8PFPFvGxhx7GRy9 ynyqXnnuAPr0I4Pk2d996LOGA3NlZyIhzwfuOwB7VDX5fNj7lty4 v5x9YltEjbvDZdri2qWUZ6/XFWe7aZ/z1135nc7smxNrOeuVV/Xt/TUrE7VHeoRQdtKK9tQ2Gfbs22GHRO27elyfscIax9XtS8NGu8xyxEw83p5vXLbwWXuJix/R1vLwV3W uWS9sGurGdERLtEe3vgVQAyujSCkvfIoBRmS5uQG91vbq4imUlUDrr9E1jbXGvxOebmcUbLwJgZ0xnSCLAaslXzHvZeO/gvY3q hJGl0ZYb174kkBwEVvV6U0NpAOuy2tq bL3EquulWRQGaxppUbB8aUfV7MvaIfSYsInOP10u6BihltXbx8mxyd2XBo2vlUKqMO3zXg4zmbx57WrDviG2WP6OTpSDWlbZtsw0mJ5Tv6KobW4aq9uwbRER0U7RAbz0uDfrwsc YV5VlFeWgJGhgOcCpzGvDp6p7HIbD579mFhTB6/5YfN3LwpaRjV KonMTAeaIqUi8qkBJMyfElhOsDEQXf9eJFHAum/Dk2j3CD8mbIeA/WduGdmxYXVUEmlMzgJLK2qDDRrvI5n0eU9/fiz4hPKu2zew/B2dK4dqZcyNFjHF6J2IqKfpAP6Jp5/B1Ucfw1euPYovXb2m//3qY4/j0a9t4PGN69h44ut44smn8KSa7ukbN3Djuefw7PMv6C oKMNpq4U01fqHMJLKYlnHnDmrt8ecnfZJBXPItOq9LeWEmd/JSXqy8/12Opqkmrm/W/l 5zPj42562iCyyCOTcKdx513 DXpPf5FatMrvylBZBDPdXOM0uUCJAaQK685Z93ZKD2Msn8Fo3fzYy2ZeW Uqy2an9FWWp37awGWtKq Y9lTpxteU15PuX8f86nxN3Wm4XRD5CNiG/OuhS pe7b7MKNVut069rPoKSfc9YHoAPRGOCTukvF5AasA7RaniuiTyxVLgeD8Dk1NIZmasfZQql kCZidDTijX7Bt2K5a/o7VyUIH9yBISetscBKYmoKJ3FKfmTeBPRES9SgfwN910E37rN96GqXveXjfc8/a34h13H0fmzWMYeej1eMv4G/CmNx7VH65WQjGfxN6tHBhzM8gkV50UNzVUnzyWxqLOJcPmls8qq0bpNLAo31 aBax0tPS885uSgjaWtVPy8igMLFbec9PwquYhjfnA94RqFCcySMq8m98uDNoBmpqv4rDz3uoY8lWNkQikNyFfVCXfbrJckqKf0I324MDRKlc1/9nBPozClFnd8gSvgwopryWMuOmOOiuwbqIuZQIfaUxJdbXqgm8dC63zQup9AksjpZBpaPex6pk3SODtCt6Ggvd1ImhfVr2NO9u0ZP o7d05E6vllrMYUwFE9e7f75hgz3/cU8nTGB5zT0gr5RWokkf9 YrgfQO1guXfP7FmHR clPpJVi8iop4X Rr4a PXMHRsCFePXTVjtioF68SyQ3qSs4O vbJLo04Q09oxVzVKF03jsn8CU2N5eCezvRvF2I1gkWq956i8joJqEg 781772zJf7tFWer2bTu1LYCDVqXRAk/KnTzoEBfFWuer5t8qsbnlC1oFLl5fd2MoG9r50HxP4SGOqNIBpuyfdr46F1HlNGqP5MUzxgniqYtUzb5DA2wjbhgL3dWFqt3GzTctr73KoHJYLsxEDB3v 499TmJ5U 0dz7XFuJoNk3UkMEbJvoJaw/Cty49MYUNsqAm5sR0REvSNyAH/b/G148PSDuP307WbMFuigxKeXXt 8axOLGK056MjNaFJtDuLKWC 4L esm7WVMJsy42OjhayHqNS6WVQFY/e2tc5aB3XGzPowQxx7S/SlIuYERVAdC6zzRK3y2Ybavq T63ILune/PDeNwo5e59682pRkN2U5aHwg2daxhJXcHKajnMSw9w27GMvf0bZyUNv3NOTSgIAb2xERUU/xAvh3v2fBd8gu3Iv3vu/9WLzvftz/uhzuPbOM z7wQdx8883mk65GvcFuOnlwr4ukg5VUy7LgfUkKI4trWEVIT2Uk coNYEzPpu4Vt2/WpsfLizbSN8yxU/zUQTZr9ci3Snrb7JvNtYtqDFWKW65jzYc3HiIJWAc2U17xSZsPoJfPZJo0qGP1dd7QDc0eKAvaXkHbUAf2df1DI8DSjAoYgq5zj5ohJNffu72iQa/bTGfAVDIIZjJmGYLGB5LLCZLIDOoJG5/EsPcNuxnL39GWcijzxnVERLuMDuCTe1/Z9LDv1a/SX1DRD92eq7pTqn294zQGSgHX8VrPO01kknVpw84j0xI N0mKKoVk0enp7LNPIqQnMYuMcxMYdQBMBvZKybV2ZlnqukrD35M770sKuvPbcm1qG9NGpVGe3Nu40dKs9F4UvfWW0Ndqr7Wcyh2wDqo45aUK0/y2GmLTNW3Vdb2ezePggupYgzqvG6Zr8vigSlmwl54aC9iGIu3rwvZlPuRSmGQW2WTQTcEaHRO2cOPOdpEMmFVgUM HpCaY7TVofBgp21TY5S4B 4bdjOXvaEM5lOdGsTQyaY6n9Te265ZFJSKi9unblBzLdpE0zVFgca2bDhrSiyMnD7rooN0WcpMzXdgxWK5eXQdEu5vc2X55OOQGi115TCAiIiKKr8jXwEfSP4FFOfvLrsKOy41LzzgfR0REO0QuCWp03TGPCURERERt1d4AXtGPNeG1WB2nHwnFciaibSfZPyYd2b1DfQgeE4iIiIjap70p9ERERERERETUEW3vgSciIiIiIiKi9mMAT0RERERERBQDDOCJiIiIiIiIYoABPBEREREREVEMeAF86fJn9XD5kc/pfy VHsGnL13Gw58p41PFdXyi8Bl8/JNFfOyhh/HRi58yn6pXnjuAPv3IIHn2dx/6rOHAXNmZSMjzgfsOwB5VTT4f9r4lN66 f1x9YpuEzXvD5do6XbYH5iBfLc9frirPdtNl6q47U7YdWbYm1nPXqq/rW3pqVgfrDvWCoG2llW0o7LPt2TbDjgnb8XQ5/fveb1YfJ2Q/6oy3ltPa9/nvY81yBMy883vu9 3MMncTlr/Fr60StLwNy6G6bO3lknLdbfWMiGg3aW8PvApARpdGUPIeGZTCbGkTcqP7zc1VJDOJykG3fwJrm2stPsfcPM5oGRgzYzpDGgFWA6Nq3sPea6ccZjJ581oeI1fCyNJo5XfbSQLJQWBVrzc1lAawLqutY8vWC6y6XppFYXALJ5RYvrSjavZl7RB2TFgdQ3Yr20mTSsU8xlbNb27Ow50TCXKmB0pmvNnuqvZ9cswK2semkCpM 7xXvZ92tGHfEGMsfxHUVlHbnO/yBo23qWWVbctMg2nn5L6U4TRWwSc3EhH1Lh3AS497sy587BPmVUV5ZQkYGQp4LnAa8 rgmcout/Hg2Y JNXXwmh82f/eu8tw0MKvKz/ytl30qicxMB5oipSLyqQEkzJ8SWE6wMRBd/14kUcC6b8OTaPcIPSakh1Uwsx3bSQoD3s7MlcNyYRaLNWfL9PzOTpogM43JWWBpxX8Gk0mf93LLyI6NBZ9Q3pX7Bpa/Pl77tVX0/A7XL2/Q IbKmBstYorROxFRT9MB/BNPP4Orjz6Gr1x7FF 6ek3/ 9XHHsejX9vA4xvXsfHE1/HEk0/hSTXd0zdu4MZzz HZ51/QX1BRhtNW8w/ftf4hjKSyWNYxp93bY85O 6SCOWRa9d6WcsLM7 QkPdn5fjsdrZLCZ3 /85nxcTc9bRBZ5JFJuNO48y7/Br2nv0gtWuV3ZagsgplurnGanHzHaHEK80Pmb1diAKnCunPWvZ2kYZ3PYLRufuxlM6 tcpVls1P6KstTP23YslbKK6Y9VbrxNeX1pPvXMb86X1N3Gm4XRD4CtiH/euiSule7LzNKtdutUy rvkLSfc3lPRUNjgmynaRGEHbIaF0Z6wWzTN78K/LbySJm3PKom/fGBiankMzMWPsoVS7TBRV/hpxQrtk39D6Wf5jyegEp6 xG/94k8sVS4PhqKrAfWUJCl EgMDUBFb2jOFXJciAiot6kA/ibbroJv/Ubb8PUPW vG 55 1vxjruPI/PmMYw89Hq8ZfwNeNMbj oPVyuhmE9i71YOjLkZZJKrToqbGqpPHktjUeeSYXPLZ5VVA2IaWJTvL80CVjpaet75TUlBG8vaKXl5FAYWK  5aXhV85DGfOB7QjWKExkk3fRBnb5nB2hqvorDznurY8hXNUZcavlHlzAy6bPs0puQL6qSbzdZLknRT jGVXDgaJWrToftwyhMmdUtT/A6qJDyUsvqpdhKVmCzzbqdUmmkSltq1aoLvnUstM4LqfcJLI24KaZ 09DuY9Uzb5DA2xW8DQXv60TQvqx6G3e2acn Udu7cyZWyy1nMaYCiOrdv98xwZr/ZbXvW6v9TLuZnk z3FWpyNkCBkw5rSadE5Y6UPL2W3ICojYd25bG8Jh7Qlopr0CVvM8JieB9Q 9j XdS/8SaKVs5Pjgp9X5NBSIi6i2Rr4G/Nn4NQ8eGcPXYVTNmq3zS6aQnOTvo2yu7NOoEMa0dc1WjdNE0FPsnMDWWh3cy27tRjN0IFqnwbIIoyusoqCbxsDvvtb8t8 UebQPSSctzo2r5FwN6DBIYSHUqHdA0vPRJh6Ag3ipXPf9WmdUtT8g6cOnyshtbWZ9eh25lAh9pTJUGMG33pPvVsZA6r0ljND Gqd3TVUeRWPXMGyTwNsK2ocB9XZjabdxs0/LauxzKSYeOFjiY W/75VRRSMCXr6QiWz2x6eExp5zS8yjNFjCoy2kUxWTloiU/6Um1fzTXHudmMkjWncQQIfuGXYXl30m58WkMqG0VATe2IyKi3hE5gL9t/jY8ePpB3H76djNmC3RQ4tNLr2/etYlFjNYcdOTse6rNQZyk9Lkv56wb5pQwG95W2AHODXnycvM/OSAnMsjnM0h46YYtZD1EpdbNoioYu7etddY6qDNm1ocZ4thboi8VMScogupYYJ0napXPNtT2fZ1cl1vQvftyf45C4L1PAuj9ivP57ZZssMOs9GquYVgdg0Knl20dS1jJzWE6ykkMe9 wS7H8K2pT493U aDxgdT2PQ05IRJwYzsiIuopXgD/7vcs A7ZhXvx3ve9H4v33Y/7X5fDvWeWcd8HPoibb77ZfNLVqDfYTScPvj5LDtwl1bIseF SwsjiGlYR0lMZiXXW3/Rs6l5x 2Ztery8aCN9wxw7xU8dZLNWj3xDktYqB2IzSK9VahYlN 1Uetvsm821i2oMVYrbSWMMbTxEErAObKa84pM2H0Avn8k0aVDH6uu8oRuaPVAWtL2CtqEO7Ov6h0aApRkVMARd5x5 TOifkGuY3ZRquQbf7RkNet0ivf8126XOIHAvI5Brp7MYq90h5cYx2DAolMsJksgMZkJu4Gqx9w27Dcu/ns7EqmSyzOjFUEsRNN6XXGbHG9cREe0mOoBP7n1l08O V79Kf0FFP3R7rupOqVYqZ9 0vt7N9xjjpXb2IZFJ1qUNO49MS2zpRjeOFJJFp6dTerG9kwjpScwi49wERh0Ag7P1nNQ/vSx1XaXh78md9yUF3fltuTa1jTeYkUZ5cm/jRkuz0ntR9NZbQl rvdZyKnfAOqjilJcqTPPbaohN17RV1/V6No9FCqpjDeq8bpiuyTWjlbJgLz01FrANRdrXhe3LfMilMMksssmgm4L5HRNszt21M6Od7CWUEwCmHPR x31Mo5TTCJb0Nuvs45xjkzW9ZCxEuUZfyjYVdrlLwL5hV2D5h5JMrFWYSwb0AjvzFjTeh3OZnXXn/pob23XLohIRUfv0bUrXbrtImuYosNjxGxM1QxoEcvKg1xpNcpMzXdgxWK5eXQdEu5vc2X55OOQGi115TCAiIiKKr8jXwEci1zXK2V92FXZcblx6LbrncThEtMtISnSjFGceE4iIiIjaqr0BvKJvQMNrsTpOPxKK5UxE206yf0w6snuH hA8JhARERG1T3tT6ImIiIiIiIioI9reA09ERERERERE7ccAnoiIiIiIiCgGGMATERERERERxQADeCIiIiIiIqIY8AL40uXP6uHyI5/T/14qPYJPX7qMhz9TxqeK6/hE4TP4 CeL NhDD OjFz9lPlWvPHcAffqRQfLs7z70WcOBubIzkZDnA/cdgD2qmnw 7H1Lblx9/7j6xDYJm/eGy9U8XaZeOTrLKc9frirPdtNlWv2bnVi2ptZz16qv61t6alZHypd6R9C20so2FPbZ9mybwceEbazroccIM18BG62z/3XntXYZtrit7zYsf4dfOVjH2qpjetB4i902sMtB2gesl0REvau9PfAqABldGkHJe2RQCrOlTciN7jc3V5HMJCoH6f4JrG2utfgcc/M4o2VgzIzpDGk0WI3NqnkPe689SsU8xlbdcpyHlG56voSRpdHONIAlkBwEVvXvqaE0gHVZbR1Ytt5h1fXSLAqDQY3VECxf2lE1 7J2CDkmqM0EmdE5tRfvpKjHiBRShWmfZc9hJpM3r11t2NZ3DZa/I6gc1DbnHWuljeQe04PG21TZyLZlpsG02ZbUNjeNVfDJjUREvUsH8NLj3qwLH/uEeVVRXlkCRoYCngucxrw62Kayy2082PZjYk0dvOaHzd 9KoWBhHnpUcs lURmpgNNl1IR dQAvJ9UgeUEGwPR9e9FEgWs1zW4iHaXsGNC/8QUxvJLWOnodhL9GJFMAku1M5NbRnZsLDj45LbeAMvfEVAOevmG9Ul5aSNNzpoyCBrfUBlzo0VMMXonIuppOoB/4ulncPXRx/CVa4/iS1ev6X / tjjePRrG3h84zo2nvg6nnjyKTyppnv6xg3ceO45PPv8C/oLKspw2moh3Yf9QxhJZbGsY067t8ecnfZJBXPItOq9LeWEmd/JSXqy8/12Opqkmrm/W/l 5zPj42562iCyyCOTcKdx513 DXpPf5FatMrvylBZBDPdXKM0uTLWC b7a6dJDCBVWHfOurdTelg1rDMYrZsfe9nMa6tcZdnslL7KvNZPG5QSWF1eMe3Z0o2vKa8n3b O dX5mrrTcLsg8hGwDfnXQ5fUvdp9mVGq3W6deln1FZLue6C2Nz3CMaGLDExOIZmZsfY5ajmnC5idDAk a7Z12rrdWP7l9QJS1tn5/r1J5IulwPHVVGA/soSE3jYHgakJqOgdxSknS4 IiHqXDuBvuukm/NZvvA1T97y9brjn7W/FO 4 jsybxzDy0OvxlvE34E1vPKo/XK2EYj6JvVs5kOZmkEmuOilxaqg eSyNRZ1Lhs0tn1VWjdJpYFG 38nb9IKk9Lzzm5KCNpa1U/jyKAwsVt5z0/aq5iGN cD3hGoUJzJIuunvOt3PDtDUfBWHnfdWx5Cvary4zJl7Mx9VqXTS 5AvqpJvN1kuSdFP6EZ7cOBolaua/ xgH0ZhyqxueYLXQYWU1xJG3PRInRVYN1GXMoGPNKakulp1wbeOhdZ5IfU gaWRUsg0tPtY9cwbJPB2BW9Dwfs6EbQvq97GnW1asn/U9u6cidVyy1mMqQCievcffkwoz00jmxpB98T3aQyPuSeYlfIKVEn6zF/wtk6tYPk3q39izTo OCn1k6yOREQ9L/I18NfGr2Ho2BCuHrtqxmyVTzq49CRnB317ZZdGnSCmtWO0apQumsZl/wSmxvLwTmZ7N4qxG8Ei1XrPUXkdBdUkHnbnvfa3Zb7co630ejdMBZQGTt5KpUtgINWp9EFz4kCfdAgK4q1y1fNvlVnd8oSsA5cuL7txlvXpdehWJvCRxlRpANN2T7pfHQup85o0XvNjmGLXHlWx6pk3SOBthG1Dgfu6MLXbuNmm5bV3OVQOy4XZiIFDZd4SmSRW12qD/p2VnlT7O3MtcW4mg2TdSQkRsq1TS1j W5cbn8aA2lYRcGM7IiLqHZED Nvmb8ODpx/E7advN2O2QAclPj0y uZdm1jEaM1BR25ek2pzECcp6e7LOetmbSXMpsz4Lpf0CrCFrIeo1LpZVAVj97a1zloHdcYqN8 TIY69K/pSEXOCIqiOBdZ5olb5bENt39fJdbkF3bsvPemFwHuf1LJPQHRhqq9su1jCSm4O01FOStjbOrVul5V/bWq8mzofND6Q2r6nIZcSBNzYjoiIeooXwL/7PQu Q3bhXrz3fe/H4n334/7X5XDvmWXc94EP4uabbzafdDXqDXbTyYMbbZIOVlIty4L3JSmMLK5hFSE9lZFYvdamZ1P3its3a9Pj5UUb6Rvs2CmB6iCbtXrkm6U/b2UwSG bfbO5dlGNp0pxy3Ws fDGQyQB68Bmyis afMB9PKZ9dSgjtXXeUM3THugLGh7BW1DHdjX9Q NAEszKmAIus69mQwhuQbf7UkNer0d5PKAJDKDmZAbslrsbZ3aYJeVv87EqmSyzOjFVksdNN5XmTeuIyLaZXQAn9z7yqaHfa9 lf6Cin7o9lzVnVKtVM6 aQyUAq7jtZ53KmmVtWnDziPTEj43SYoqhWTR6enss08ipCcxi4xzExh1AEwG9ko5qet6Weq6SsPfkzvvSwq689tybWqzvU7SgHU/L/NuPWZMGuXJvY0bOc1K70XRW28Jfa32Wsup3AHroIpTXqowzW rITZd01Zd1 vZrKegOtagzuuG7Jp59KKZjr301FjANhRpXxe2L/Mhl8Iks8gmg24i5ndMiAEpq1TY5SsB2zq1x24qf8nEWgUG9bYqKTJmWYLG yjPjWJpZNIcT tvbMeqSUTUe/o2JZexXSRNcxRY7KrrGiUAlpMHvdbIkpuc6cKOwXL16jog2t3kzvbLwyE3WOzKYwIRERFRfEW Bj4SuV5azv6yq7DjcuPSM87HFxHRDpFLehpdp8xjAhEREVFbtTeAV/RjTXgtVsfpR0KxnIlo20n2j0lfdu9QH4LHBCIiIqL2aW8KPRERERERERF1RNt74ImIiIiIiIio/RjAExEREREREcUAA3giIiIiIiKiGGAAT0RERERERBQDDOCJiIiIiIiIYqBvY2ODd6EnIiIiIiIi6nLsgSciIiIiIiKKAT4HnoiIiIiIiCgG j7/ c8zgCciIiIiIiLqcrwGnoiIiIiIiCgGeA08ERERERERUQz0LSwssAeeiIiIiIiIqMv1HT9 nAE8ERERERERUZfjNfBEREREREREMcBr4ImIiIiIiIhigAE8ERERERERUQwwgCciIiIiIiKKAQbwRERERERERDHQt6mY19QlFhcXMTw8bP4iIiIiIiIi4l3ou8Ytt9xiXhERERERERHVYwDfJSSAv379un69vLzMHngiIiIiIiKqwmvgiYiIiIiIiGKAATwRERERERFRDDCFvkvUptCPjo7q10REcSI34RTch1GYVuoJ6xhFwXpCRL3C3Z 5l1gzgO8SfgF8X9/v6L JiOJiYeF79b/ch1GYVuoJ6xhFwXpCRL3C3Z 5ATxT6ImIiIiIiIhigAE8ERERERERUQxEDuC/ uiGHh59/Lr 9ytffRxf sqj MKXr FzX7yKv/38l3Hls19E ZEvYP3y58yniIiIiIiIiKgd2ANPREREREREFAORAnjpcW/WpfLfmlfiPDK33opba4ZDp66Y95XzmfpxtiuncEg d gUAqawVP9e5rwZTURERERERBRTkQL4J55 BlcffQxfufYovnT1mv73q489jke/toHHN65j44mv44knn8KTarqnb9zAjeeew7PPv2A bdl/Ehc3NrChhosn9 PCiX24te3RtQTvR7Cgf si1M9g4UhGjSUiIiIiIiKKr0gB/E033YT5//RO/Mc//Hf4D//37 Hk7/42fmfqHkzd83bc8/a34h13H0fmzWMYeej1eMv4G/CmNx41nwy25/hpHVxjYQa60/3grA7szx3fo9/fsvMrWFD/7D98F/ao/911WP8IVhjBExERERERUYy17Rr4a PXMHRsCFePXTVjGnGD6wu4dFn9U5VCX5Ny79NLfz5j3qtJqb9SLup/B/qdEwF7 gf0v8Vy48R7IiIiIiIiom7VtgD tvnb8ODpB3H76dvNmOhqg vzmSNYwH6cvOik22/MHjTvGCrYPyLd7EfPYOPccbTYZ09ERERERETU9SIH8Pf89u/iX0//O0z/wTvxB7PvxuwfvQfvfs8Csgv34r3vez8W77sf978uh3vPLOO D3wQN998s/lkY25vueuOO52e RP7/G5qdxbHJHqXa9xrA3siIiIiIiKiHhUpgP97t39708Mdf/ 7zKeDXMEDZy of49iqCYO33P8HDbOONfR6xvd2Wny8hEd35/FAz5Z8bUp87Up9URERERERERx1LYU madz zDCRWM7z95N3z70fVN7c6o8L7G/sM4ffqkiuGlh97n7vIHh/RnLpx9QAX9wScJiIiIiIiIiOKkb2NjY9O87iDzaDfzl0OucT8H76bzchO7IwsqoL IyUv7nGvcNTMdTuHQvhO4IKnz544Dpw5hn5wBUMH5mY3Z6pMA8sx4mVb/UfM7XeqWW27B9evX9evl5WX9LxEREREREdHw8LD d5sCeGqkNoAfHR31/iYiihPuwyiKVuoJ6xhFwXpCRL1C9mduAL9jKfREREREREREFB174LtEox54GUdE1I389lfch1GtVuoJ6xhFwXpCRL3Cb9/FFPouEyWAl3FERN0oSqOZ zBqpZ6wjlEUrCdE1Ctq911MoSciIiIiIiKKEQbwRERERERERDHQIICXx7/dilutIVP34PUI5LFutx7CqSvmbyIiIiIiIiJqSoQeeHmO gY2NtRw8SSKRzIqrG/SnuM4t9H9z2InIiIiIiIi6lbNpdDv6ccAiiizJ73L5TDe14e 8Vzldc1wYK7sTFojNy7vj6tPERER9SrrOFmew4EGx0geG4mIqFs0F8CfX8HC0UmvJ/18xkqv93Lrr DUodqUe0nFt1Po/aahdinPTSOLMazOp80YJTWL0uYmNtVQmk0hn0mYAL9aen5VfTKLQZ/3iIiIekGj4 TaRL8Z6eCxkYiIukWEAP4CTuwzwfYR4MzsQTMeODhrUus3zuDowowToJ9/F04MnDHjN2BNbkjwvg9nD18MmYa2royVpTwwNgyrWVKlf2IRKoYHstOo74hPY3hM/ZNdZk8DERH1oMbHyXo8NhIRUXdo8hr4OzFj96Sfz5he9CNYMKNwx53Yv3AEh4LuWHflAZy9cBSTvCC M8orkHZJaiBhRvjpx9CIRPB5FEvqn9x4Vcpg2mmlYJmtFCIi6jWRjpMKj41ERNSFmrwG/i4c3n8Bly6r13JneemR173oF3FyvzOJc8O6DZzGMabH76Dk3ur0vyCFdf9r4YmIiHpZ3XEyn0HCXAPPTHkiIupWzQXwuvd8P 68Q72 fAkX9t8JeemMlxcVe46fw0UV1Rdr73inTwIsYIbPlOsKugGTnq  5i8xAOmfJyIi2jWsa D1pfE8NhIRURdq7hr4fWdx KJ5HNzBu3ESJ7BPxh 7hAG3B95Lq78V 04M KTK78Hxc2cwcGKfNx176dsvvGfdXP HMQz7XQBYKkLeJSIi6lVNZ6Dx2EhERF2gQQB/ELPmRnPOYD/LXQJxM/7cLGbPuYH9rDX9rPoGId9jf7b6e3kTuzbqH4Jc3p7XF7f7y40nkJHr/2YnnRv41Fznl1vOqv8GBPdERERxFuE4qfHYSEREXai5FHqKAXODuto75VrX9g1mU5gt1T8mx5GD00Zp5u68REREcdH4OFn/mFUeG4mIqDswgO9B/RNT1vNq05g31/RVhjVUxe7WdX658cH6Z MSERH1kKrjZP8E1mqPk3IM5LGRiIi6EAP4nmSC9i00NNLz0niZZw8DERH1sOaOkzw2EhFRt2AAT0RERERERBQDDOCJiIiIiIiIYiBaAK8fDZdB1dPerMfFHap5pvv5jDP 1lsPwXnrCk4dcseFPDYu6DtDfqvKlVM4ZKbTw6FT6pfFeWTs8Wrgo uIiIiIiIgoThoE8CbwXgGOmjEOFRAfKeLkRXkMnDzT/ZgJ1J3gfebOi YRce6j4y6jf9I8Nu7iSRSP1JwM0OQ7gTP6c/Z3Bo2vIcG7fk69 R01nBm4pH7Ztd/MrxoC54GIiIiIiIioOzUI4M2z3meHzN/GlTKK w/jLh2cH8TQ0Qu4pCPl81gpnsTpygPfjYM46D7rfU8/BszLKudXsHB0yHtu/N0ngbMPqEg9aHyVKzh17AQGztjPmldTz7rPoa h56GIst JgDgxz6iVwX1OLVDG3AHzGBw1VD0Jx3d6f W5A g7MKe zYj62fIcDpjp9OB9Rw7j9ng11D2lR4s2XW5cvVfzhoyrHiXfdQBVsyvL4f/DRLTN9H7G29bHqx/ppfc59riQfZvH7D8CtnHn99x9QtR9EsVZPOpY/XS1x9mgY579mcpnc4HLYX mUTtgV/Ft4zSoD3X1p1pQ3Yu8DlpuTxFRr9raNfB77sJhnIUTR6ugfeEohiRSlmB74BLe5aaqeynslqqAvOJKuYj9d95h/pIYewAXLl0OHF/lygM4e8HMQxR6Hiargv3YkR37ILCqH3mzimRm1DQYStg7JePUUJpFYdA9aKgdvu/0fnKYyeTNayGfLehnx4d VuYpsYQRPZ0zrCaLao5czvPn6 etljXd6hiytdOp35kujGGsMF01H lhNe2yNWV5HQXksbRSmai8XkBqIGH IqKdVCrmMbZqtnXvDt m0bwMjOm/XUH7tloppGr2DY7a/ZqIuk iuIpPHbOmU4M8us4TdMzTd8aXYVUtR XzaxPwXw71PevDlc EtwN2kabbU0H1p5pv3Yu6DmSe2tKeIqJetMWb2O3B8dMqhN8ngbrkt1s93QtF3GlS1c8MnMAxk 9 5dQhJ6hfGcLGbNRIuwn774Qb5nu/5V2DLy7ghJ5fNehZ7sA8bKPyyhIwO2kaI2lMzsIEqmmk3efc9O9F0rxEbhnZsWGf6euV56bVd8 qw4MhgXBqBEO6PZHG8FgexcpRxFAHtNEMkqvVz5hPzwc8dkfPWwHrjRoP6WF1gKyeTi/7yCQmR2qWITGgGlXr5gy1M11SLUdlZsvQH3UWhIh2XAr159P6MbGmGqXzw ZvV8C zUdSvVm3f9P7QBUEmT/rRN0nUczEv44FHvMCBSxH/wQmvANyAgPeQX53a7o9FVh/avnUvUjroEPtKSLqGVsL4OV682PAaXOt dCKdVM4q2f74NBRr7d8z/FzzvXnQys1gXWbXKhc7 781pma6/bta DvxEwn5qHbWEF7bc9z/94k8vVRuJpwDqPFKczbV030D2EES3DaDTksZ8cwXHsUKa9gKe8zPoiet6mqg5Mvmc47eSAqQXj/kG7NeAF79Xw60w0MqQNbdtmcmS6hmE9iL N3oi5Qxnohj0zCSQFtKp3X2rf5GZicQjIzY/VIqQbxdEG10UMa3FH3SRQjvVDHQo55UQQuB4 HTWlQH pFqXsB66BT7Ski6hlbCuCvPHAWOHwX3Ax0CdQXViLeEu7gLM5418xX7KlJjXdT54PGV2n2mna5BGB//TzEiQ7AvcaDHOAraXvedVfLw9icj364ke ZG13CyGTtZ/oxsahCY30gkjyzgLPAqQG4pwgq137Z16BXDmbO1wTNmzWdLMPahJoDQw5sKkzXAX1VwC76sTfpZgeoA6OeTjIGzJnppg/ARNQ5pherUSqpJfq Tbb7LLwrauz9RpWo ySKpzjVMWs6NXjXNIce84I1Wo7c CAKXq/z7taZ9lTjuhe6DtrWniKiXrSlAF4H1Wcf8K5vP7 y4ATVB4dwdGHG9GxfwamZBRyVC9PPn7fu C7XzO HE4PL491MT/gdd2L/woqZ7jzedULOEewJHl/FubndiX0R7yyvr5l35yGm0vMozRYwqHfqoygmK3lY/RNrzkFjeLlmhx uPDeKpZHF rO4ci3WKLCoD0SbGF4OuGFKvnJ9ljMPcl2ezb5mawDTgfNmpivNIuX1njucVMIhE9D3QzokMjOVKbzr4CVYT 7V0yUGnHQ4Xv9O1K2cS3MapQc3s29LT86iMO3c9Ck3k0FyyjoR6Im6T6L46/Y6Zk2nBjcea3TMCxK8HGV9/fb0QKn6OvvdrAPtqWq1dS/COmhbe4qIetHWUugPzuLi4bPYZ25WdwRncE7nzR/E7EX32vh9ODFwBvpS8zvKmDHTOtfMV98tXttzHOfOAEdqpwkaX0OnzXvTOdMWT562prWugdePm/P/njjxDiybaxhGHsnaPCx1UFo116vXpszXB7POzXfymYQ6SKmDWCKDfD6DxIE55KoaEOpra28WJ5q9Bkt6ElJ 19Jb iewqA6q095RqWYe1ZCQGwbZQb65Dj6nlm/M5J/ptMPiipeGSETdqW4fFsTatwVyeytzcgOwWdQlFtWKsk i2ItXHYtwzGukajkkcNRn4xm812imPbVVzndGWAedaE8RUU JGMCrwHyj pFs3jXtMtg3hJOAu3a8PU4Nlcnle61A uCszzRK0Pha1nQyOCcV9BvqdyrjK8 n7xG5cQy6jYdczjqwy/Xq5iYqEth6B31pFLjBrDyORM7cpjGvD17uGd1ZpFKzKK1NIC3Bv3XdXW4569OT7dz4JZOIeCdUfY2X382FqvVPyHWGJvVMetVlnuz53CxhNmWlMeoGVQaDavm875aDYTaDDK/3I pOZRUAufuqIEH7tkD9mJhKIiM7A sEZKCI ySKqTjWsSjHPD9By5GbQSbJa6VDRWlPBXLbU ZPl133Iq2DzrSniKh3bK0HnrqA9RxQuf7JvU48sY5pd7zzhnOg6J/A2ipMipg1Por0PEojS0iY7x3Equ ZY30G2/sN53cKs3ZKvnXNln48SpR5MAey0TnMyYmDukaSpBSmrIwA5281oXUtoqSvqX94/TtRF7H2YYn6Oy7XCdq3hUlPqmBnDFOBE25ln0TxEe86pk WNzzm QhYDsm8Q3bQjHeGpm7s17OabE9F4l/3oq6DzrSniKhX9G1sbGya17SDbrnlFly/fl2/Xl5exujoqPe3cMcREXUjv/0V92FUq5V6wjpGUbCeEFGvqN13DQ87TzphDzwRERERERFRDDCAJyIiIiIiIooBBvBEREREREREMRAtgD fMY9mc4ZDzoPeI7Ce837lFA65r4mIiIiIiIioKY0DeAnejxRx8qL7CLaLOHx2XxNBvKEfJddjj28jIiIiIiIi2iYNAvgrODWzgKNn7MB7D46fPgmceBfOmzG0E QRJT7PGw0cH0XYZ1v53ory3AH0jcvjb6xHrJhBj25WeQ4Hmpqv t/t3GN0an r9fILXd6my6JebpyPFaLtErRPaWVfE/bZVr63ovE rH68s03J IDnOufGrekjPvt5W9UuU vluD2C1nnQ CjCPtvK91bwOGne2jZB662V9Rn22Va tyK4noR8dxvaCa1rYn6jYtuIdpnwAP7KAzh74SiGDpq/XXvuwuH9RZR1J7xJkz9VSbP375230ukbfUan27sp xmeKNgR7TnAVFE70dGlEZTm3aexpzBb2sTmphpKsygMbqHhKs 332z2 afW726uIplJmINgmK2WR W31CLq59k39xU1v1u1vGHvbU16voSRpdH2rneiHbHN zA1eKNrxq FbZTSuJRHTJtpN0sDWG96R9iBZa3T6r6sF21zHeNxMqa2t56ElmEb2gnt0eo6rylTto1ol2mcQr//TtxhXla7gEuXzUv1 sSlISfF/sxRXIjUOx/0GRXc7zuLw27K/hlghhfO94TyyhIwMgTffWj/XiRRwPq27xzTmFdHj1R2uflGUZP6J6Ywll/CSlcfAPoxMZVEZqbTpUEUP6H7sK0qFZFPDSBh/pTG5oR3IqA7xWNfFk88TrJuRRFWT JWhmwbETWvcQB/4RK8OL3KftzpRfb7cfJu001/cAhH4fbOhwn4zJWyeqWC 32mB/7IgpoF/zmgCKR3x0tTqpy5l3QgL32p7qy6nL0cRBZ5ZBI175cq3 ekE5Uxd6AmrU/SQQ/Unk0twzneBDR9c8vIjk15Z0j958/5LXe8M7r2zLbfNA30D2EklcWymbb t/3LI7wMG/P/vLM84 MHzHu1v sur9881ZRF1bq3y8JMN1dJ261KDUsMIFVYr1l/RDskLvuwrUoPq8ZrBqP2Nhg6T7X7uIBl9S03s 3nKu/J5DoV1/y9lTTRsH1ZLPA42VgXHye3TSz3RXZZyTzbdcG8jrg/aLwuDuBApPkPF2Wds21Eu114AK9T5RewUtudrlPrB9DfsRvSHcUZfcM8M8zW5vCTw ygrB2Rs1NzqZ1RYgkjbhrcKjBtdkbpeTNOjRzLTlsHdpHGvIx3U5y8FC31e9PAov6uMeQzM oX5KzkGLLuUV3JLWcxNjVRc2a4hGI ib1VI635lxTSSv6p//zlZpBJrprxdrqqSw5 CSyNlEKmaaz t/3LI7wM65XnppFNjcA95gZ/Po/CwGLlvbr1IILWkUvWfQbJVfMbJUm9tA5gUvbFYec9b10a0suTL6o1RtRpPbQPsxr0tctV1aCtI/Mq6ZkJa9qQearbD/ota3C51ZZBdrAPozD7m9p9QYBm9mU7r4fqGI TVXXLPU62R9zrSUVtGVbKal7NTa3q QjbHzReF2tYizT/1dg2Impegx74PTg eRQLR zr0CXF/QRw8m50JKze048BLDBtPhKzg9I7M3eQHZdRXkdBdkbewT LfNHseuSsaN0BqhH1e4tmRyy9Rm4qn7z2UutyWC7MYrL KOHDmv/SAKbtM6R 8ydnP7ODwT1E5RUs5ccwtaULnVIYcHNYo5ZNpOkq5Z/IJLG6Zh3IAj far2XT6/7MQy766F/AlNjebirX5e9u5LsdaklMJDaiTRN2n16aB9W1TiuXq7GAZJquK paXVj0gTxQfPUaD8owsqtrgys/U3dvsC2tX3ZzuuhOsbjpKUNx8kqca8nIWUYWla18xGyP4iyLiLP/w6tc7aNqEc0TqE/OKuvQz/i3VTuCHBmA c69jy4g5i9KHe532d Tw0Z3sZu68YqN0eSQVqSkj7k3TSphNmW21hpTM4W9NloOZNa2Mo1ojo9z xEg ZP34hkE4sY1Tv38F6tJugGjTmbHbVsIpeh3SiwGvhtXwftFH52n2h7xWQf1g5qH7eoFsbpwQqYp8j7QZ9ya0kc92VR8TjZEI TSjfXk4AybJfIyxl1/tk2ImpF4wBeSBBvpbRXZ7SrgLvq e7231Fei5q/9TPjmULfMn3Dm6zekVaxb5qkD8p6bEv6h0aApRnMBF6X1eDMpZ4Pc3a/wfz1T6yhpPbqhdovM9fo1S1vKDedyhxAopZNq2XYgXVQxax7L5NNHRSns9ZZ5zByhtqdN6KdFKd92Fbl5qz0Tbm2NY U6eYMm6fA/aAIKrdO6PS rNN4nIygR4 TzdgN 6IwTSxn4/kP0el1zrYR9YhoATzFVBpy51jI4190OpIa5HR8ehKzyCAhf48WkfQ9w5nG8JhJcYpyCl/SkJJZZJOVG xU64fep1fdZtRKR9PXlpnHfATNn5dW5aRc1acAShqqedyNmc5/1q3f7ZvGQMlKcQ0sm5ryiFSGISJ/Pmw9hL8n617ScfVy6vKNeFZeDqDJvc33DhG1XYz2YWoITWsPkt6LovcdCX39svfYOb958t0P1i5rQLl1Qqv7wh3H46T/rNt1u9uPk9uh2 tJhzWzLhrOf4jIvxNWpuHvsW1EvaBvY2OjXXcAoRbccsstuH79un69vLyM0dFR72/hjutmcufQ5eGQ6z0lNUotwmLVtVnUXeQGR3olNX/gpV3Nb3/FfVjrGs5TzLRST1jHKArWk53Xa/stto1op9Tuu4aHh/Vr9sBTe0gaUqObrfRPYHFkCYkoZ6BpR TGpQdwC2fNieKuG/dhUeaJ4oPHSYoi7vWkB/dbbBtRt2EATy1ynluq05DcO5mGkOvyWr ZEnWKfnwL1w/tKt24D2tunqjb8ThJUcS9nvTufottI o2DOCpRebxR5tMKyKiOOrGfRj3q72F65OiiHs9YT0n2i4M4ImIiIiIiIhigAE8ERERERERUQwwgCciIiIiIiKKAQbwRERERERERDHAAJ6IiIiIiIgoBhjAExEREREREcUAA3giIiIiIiKiGGAAT0RERERERBQDDOCJiIiIiIiIYoABPBEREREREVEMMIAnIiIiIiIiigEG8EREREREREQxwACeiIiIiIiIKAYYwBMRERERERHFAAN4IiIiIiIiohhgAE9EREREREQUAwzgiYiIiIiIiGKAATwRERERERFRDDCAj4nR0VHziogofrgPoyhaqSesYxQF6wkRxV3fxsbGpnlNO iWW27B9evX9evl5WV9gHH/JiKKE 7DKIpW6gnrGEXBekJEvUL2Z8PDw/o1e CJiIiIiIiIYoABPBEREREREVEMMIW S9Sm0BMREREREREJN4WeAXyXqA3g3RVEREREREREJJhCT0RERERERBQDDOCJiIiIiIiIYoAp9F2C170TERERERFRmL6FhQUG8F2I18ATERERERGRrW9TMa pSywuLjKAJyIiIiIioipMoe8Schd6IiIiIiIi2hlx6EhlAN8l Bg5IiIiIiKinROHOIx3oSciIiIiIiKKAQbwRERERERERDHAFPouUZtCPzo6ql8TdZJc5yNY34iIiLaGx1Ki9tuO7cr9DTtlPg4p9Azgu4RfAN/X9zv6b6JOWVj4Xv0v6xsREdHW8FhK1H7bsV25vxG3AJ4p9EREREREREQxwACeiIiIiIiIKAYiB/BffXRDD48 fl3/ 5WvPo4vfeVRfOHL1/C5L17F337 y7jy2S i/MgXsH75c ZTRERERERERNQO7IEnIiIiIiIiioFIAbz0uDfrUvlvzStxHplbb8WtNcOhU1fM 8r5TP0425VTOCSfO3QKAVPUOZ R38moXyciIiIiIiKKt0gB/BNPP4Orjz6Gr1x7FF 6ek3/ 9XHHsejX9vA4xvXsfHE1/HEk0/hSTXd0zdu4MZzz HZ518wn7bsP4mLGxvYUMPFk/tx4cQ 3JrpRHh9BacO3YojC ZPIiIiIiIiopiLFMDfdNNNmP9P78R//MN/h//wf/8eTv7ub N3pu7B1D1vxz1vfyvecfdxZN48hpGHXo 3jL8Bb3rjUfPJYHuOn4aK4YGFGehO94OzOrA/d3yPfr8V5zP7cGLgpPP9RERERERERD2gbdfAXxu/hqFjQ7h67KoZ08ge3HVYIuwLuHRZ/VOVQl Tcu/TS  kx6vBJ6X 4OwGNmbvMn8RERERERERxV/bAvjb5m/Dg6cfxO2nbzdjoiuWq0Pw85kjWMB nLzopNtvzB407xgq2Nfp8UfPYOPccbTeZ09ERERERETU3SIH8Pf89u/iX0//O0z/wTvxB7PvxuwfvQfvfs8Csgv34r3vez8W77sf978uh3vPLOO D3wQN998s/lkYwP91SH4HXc6PfMn9vnd1O4sjkn0LtfT1wb2RERERERERD0qUgD/927/9qaHO/7 d5lPB7mCB85eUP8exVBNHL7n DlsnHGuo9c3urPT5OUjOr4/iwdqY3siIiIiIiKiHtW2FPpm6RvNqWB8/8m74duPrm9qd0aF9zX2H8bp0ydVDC899HxEHBEREREREe0OfRsbG5vmdQfJTenkunabXON Dt5N5 UmdkcWVEB/EZOX9lmPgDPT4RQO7TuBC5I6f 44cOoQ9skZABXin9mY9TkJII Sk5MEQe93l1tuuQXXr1/Xr5eXl/W/RERERERE1DnDw8PmlROH2X93o20K4KmR2gB dHTU 5uok1jfiIiIWsNjKVH7bcd2VRuw1/7djXYshZ6IiIiIiIiIomMPfJdo1AMv44jawa9usb4RERFFx2MpUfttx3bl931MoactiRLAyziidoiyc2R9IyIiCsZjKVH7bcd2Vft9TKEnIiIiIiIiorZjAE9EREREREQUAw0CeHn826241RoyW3nw pVTOHTrIZy6Yv4mIiIiIiIioqZE6IGX57BvYGNDDRdPongko8L6Ju05jnMb1jPfiYiIiIiIiKgpzaXQ7 nHAIoosyediDw5jPf1oW88Z/4GynMH0CfjzHBgrmzeceTGZfy4 iQREREREUXVXAB/fgULRye9nvTzGSu93sutv4JTh2pT7iUV306h95uGiOKoPDeNLMawOp/Wf0twnsjkMba6ic1NGVYxot pSM vqk9kMWgF/UREREREFC5CAH8BJ/aZYPsIcGb2oBkPHJw1qfUbZ3B0YcYJ0M /CycGzpjxG7AmNyR434ezhy GTENE8VDGylIeGBuGDt/Lc5jOqn/HVmHieSWNiYl 89qVxvCY ie7zF54IiIiIqKImrwG/k7M2D3p5zOmF/0IFswo3HEn9i8cwaGgO9ZdeQBnLxzFJC IJ4q/8gokfk8NJMyfS1B/qnjei94rcuNV6fRpJ4LHMiN4IiIiIqJImrwG/i4c3n8Bly6r13JneemR173oF3FyvzOJc8O6DZzGMabHE 0Syb1OD3upKOF7CiaeJyIiIiKiNmougNe95/tx5x3q9eVLuLD/TshLZ7y8qNhz/Bwuqqi WHvHO30SYAEzfKYcUY/Ko1gyL23peX1N/JqbTp8YUKE ERERERFF1dw18PvO4vBF8zi4g3fjJE5gn4w/dgkDbg 8l1Z/K/adGPBJld D4 fOYODEPm869tITxVth3U6Lr/wdqlTU6fZERERERBRNgwD IGbNjeacwX6WuwTiZvy5WcyecwP7WWv6WfUNQr7H/mz19/ImdkQx1T EkRSQd7vc05OYlb8zCVRuMJ/DnFz3XnMNfG5Z3 0OfpfLExERERFRveZS6ImIqvRjSCJ4727y/ZhYK kgPjvoPgd EEv6PVsOTvxu7l5PREREREQNMYAnopb0T0zVPNNdgnj3GfDOoK97t66Bz40PVj07noiIiIiIGmMAT0QtSmNeAvUmgvH0vAT28 x9JyIiIiJqAgN4IiIiIiIiohhgAE9EREREREQUA40DeOuxcIesZ7dfOXXIG3/rrRk4T4K7glOH3HEhj4dr6jt9XDmFQ950ajh0Sv2yOI MPV4NfEQdERERERER9YLwAF4C5SPAGf24N3l2 zG48fblSxdw9Ezt4 Iuo3/SjLt4EsUjfkG4CrKPFHHyYtTvrCHzpJ9H7063gTMDl9Qvu/ab71ZD4DwQERERERERxUtoAH/lgbPAybu9Z7nffRI4 4DbY74fd95hXnoO4qAbde/px4B5WeVKGcX9h3GXfib8QQwdvYBLXvTt9522Kzh17AQGztjPlFffMhsQ7Ot5KKJc6eTvPfrZ2uPmEV6Ged62/cxtLWi8J4dxeb/yAO8q5bkD6rMH4HzUTGsNAR jXhFQf5x64dYDty6WMXegcd3IjVemaa6uGuU5HDDT6eHAnPplEbV BtV5Ge/UdXse7eHA3Fzdb3jzas1/3fZJRES7lv8x01E53rhtLT3Sm55tN6IQelvZHW2uLV4DfwXl4gWc2Oekqdtp8J7zK1g4OlQfWO 5C4dxFs55gPNYWTiKIT1RhO 88gDOXnCnj0DPw2RVsN87TIC0DIyZMQ61cx4EVvXju1aRzIxWdtq 42ulkCpM 7yXw0wmb167UpgtOY8J2yzNojDIQKVnSaAcUH9KxTzGVk098O4sX8LeqQZ1Q33n rD7uS3UVZmnxBJG3DqohtVkUf2yK2r9lDo/GNiIce6YL8Oq2tYq37k2sVe9a/2GHtdfU1ZqKA1gnRsGEREp/sdMiT36MD1QMuPXIIeTsGNvNbbdaDcLiol6V2gAv6d/ABdOvMukoF/BA2cv6FfqHRw/56awV6fBe9exrwxhY9Yv0lafPa1CeB2oS36 23se/J1V9t8Jt5O cs38IWvaykkA5 ujRvtxY561PT9s/jZyy8iODZsDQhqTs8DSitqjB433kUz6vKc/Pxa8YfTvRRIFrPt/JcVceWUJmJ0MqD8pDCTMS08aabdVouuGj/4JTLjTIIGBlHkZqa6qnfVoBslV08gx0vMBj6ZrUD9HplQjZtrtvW9RqYh8akAtkVG1nEREtLv5HTNzWC7MYtE oCnhx95qbLvR7hUQE/Ww8B74g7O4eLKIIzpIPoZLA/vNGzYnDd5Nrd9z/JwThA t1ATWhlzDfgw4rQP1DQyt N1orvo7q1yoXO/u/NYZHDV/O xr4O/EjN889LDyegEp68jQvzeJfLEUON7PwOQUkpkZ64ysCpamC oYErJh6IPEVFUwRbtBGeuFPDIJJxXPN72vKiAPUkIxn8Re6cCOUlfLK1jKj2E4amDcqH4mJjCVzGDUv2ujOelhjOXb9F1ERNRDAo6ZcoxKFjHjprZ7l4NFx7Yb0e7RMIXeC8g3zmEIFzDQ75 PXjdeBf9nqq5vd jr6g/fBXfqg0NHsbDif5u5uu9s9pp2SdffXz8P1Egaw2NZLLtHAQmWMIKhuh185SDUJyle8 xm7FU6iPYaBmWsLLkpeeasp096n3ed3/IwNhvUjdz4IApeL0NEVi935ZpC67rBJutnej4sPTGI9RtqcNLw05jfLGFkKWGNIyIiCj5mIlvAgEltXzUnlIOPvX7YdiPaLaJfA38 gyPFk7i7NiP9yinMLJibz50/b93xXa5vd29KJ493c3rCdVr 2QfMY9/kMvUF7K 9c539nVWcG md2BfxzvL6mvlGN8YjP nJSkpxbiaD5NSEOuzUsq jGsB0VfBEPSU9j9JsAYM6UB1FMenmu9uk8ZD3Uvj6J9acujG8rD4TVDec65bkuj99/Xgz8pXr3Z3fkmvUbc3WTxV4ryaRmWkm4q6 Br7SDjKNNH19IYN4IiKqVX3MhNUTnh4eczLPIh17K9h2I9odGgTw1nPV5Xryc8dNz7k1fp91V/g7yphxxzsfqL BnKTlHz6LfWa6IziDc3qigO soTMCzsCk9Tu/Uzx52prWugZeP27O/3t6VW26sZuOHDQ UP8QRrCEldwcpguzmGx0glamT URkJVPPcALyDfXMIw8kpLv7qNuvGqArKpGSn3dkOB9FFg0N38zItXVZq/bi1o/05OYDbmhXdP6J7A4m0LW6xIhIiKqCDqWuqIeezW23Yh2hQYB/EHMmmvVq5/Lbo/fgHefuD3Hcc5vvJ6 EkhX0vLV4E0U8J1 Ds5WPq8G5wSAfqPqOyTtfzcF71piAKnsskm3kruPAiOSPxU0PlA/JqaSyAzqCX3O4NbQ1yT73ZiFek5uHIN DYOyajBkTR3I5UxdEzksu PVa/fxbMjNIJP0ufYuUl11buaTSUS8e27k qnq/aL0mg8ia8Y0TTWcKr0ZTspj6MkyIiLafexjptw7JeveRV6uXc9irPYmL0HH3ipsuxHtBtFT6Cke iewtgqTbiUXN5m7dAeNDyO9kakxTAVOaF1HpR/nFeE7KaasZ8fq6uOm5VnjE9Zd4RPrmHbHB9Q36VlHdtBM4wz6hj4R66rulfCmc6YtzC5a026xfppe8y1L70XRuy4 gUxytfnLA4iIqAcFHDPlEq7SCJb0scM5bjiXZAUde0Ow7UbU8/o2NjY2zWvaQbfccguuX7 uXy8vL2N0dNT7W7jjiNrBr26xvhEREUXHYylR 23HdlX7fcPDlac11P7djdgDT0RERERERBQDDOCJiIiIiIiIYoABPBEREREREVEMRAvgz2fMI9uc4ZA80D2SyvPf5dnuh9zXRERERERERNSUxgG8BO9Hijh50X0020UcPruviSDe0I Y24WPdSMiIiIiIiJqgwYB/BWcmlnA0TN24L0Hx0 fBE68C fNGNoJ1vO0qwSNjyLss618b0V57gD6xuXJ3dajUcygR/uM148W0 MDnvmdG7emj/hc8G1Vu0ytl6M8P/ZA0PeEvbdlQes/aHwUYZ9t5XsrGte37VD72 1eN37ql1dvR1V1ox1lXMbcAet3DsypMa2KOl8By9gV6udtS/Wt6W15O8uk9rfaUK87vF/LjXdTHaHdKWj/FjQ irDPtvK9Fd1xLG232mVpvZy4D9spQfW8PfW/G4UH8FcewNkLRzF00Pzt2nMXDu8voqw74U2a/KlKmr1/77yVTt/oMzrd3k3Zz/BEwY7oQKVXO6/RpRGUnIebKinMljaxuekM3uia8aHP0JYdojwb1Uy7WRrAetMHk 3YwCvLVJoFMqPNBjo18yjPSt90n90a9l5cbHN9UyuhMNjqyZ5m5rnV9b8VPttRO uGbowkUJyq/MbmIrCyrY05exlXkcwkTCOzG7Shvm1pfW2lTLa6/bVar7d3v5aeL2FkabS9 xmirrLNx9LVMWRbPpbuJO7DKJ4ap9DvvxN3mJfVLuDSZfNSvT5xachJsT9zFBci9c4HfUYF9/vO4rCbsn8GmOGF8z2hvLIEjAyhhX1XvVIR dQAEuZP2UFOeCcCulP/xBTG8ktY4Q64o0LrW/9eJFHA g6sg95Y/2XMjWaQXLVPvCk7uv2lMa9aYKnscvc1Jnesvm1fmcSjXvdjYiqJzEx8ww2i7RZ6LE0PY2yHjqXtxn0YxUnjAP7CJXhxepX9uNOL7Pfj5N2mm/7gEI7C7Z0PE/CZK2X1SgX3 0wP/JEFNQv c0AR6F4yNz2ocpZU0nC8tKG63hk5aziILPLIJGreL1W z0njcVJoq75CUtrrUmnLcI4BbQ3fnYNHPoPRqtORYfNUnfI7ngtYVt9yM2dTc5X3ZHKdWmb 3kpqk/ 6cH5rfNz97tp5dM/s s2/ 57 Ir0s2yYu9S23jOzYVOVMeNV813y/73sh89ykwLKxfvfA3FzdOvUr58Zq6oatme8sr2ApP4bhwGDd R2n/jrf5b ctdujGS3q1n0E/UMYSWWxrL ndlntv83rSNty/bRNb c19S16WdQuQ0h5BakqE7/flt or8vh22xj/p93lqdd 7VKfbXLwkw3V7m0qmp9JQaQKqzX7C IukzA/jh8u/TbboxOHktTI/DeDjyOBOy7fLfjBvPm xvOdu/sWw7gQKRlC8d9GHWz8ABep8ovYKW2O12n1g gv2M3pDuKM/qGeWaYrc3hJ4fZMVg7AGdn4lI7gcQSRrxUJ2Da7ATS82acGjmWnbYaiCKNeRnvphZ5XWzq96aBRZM2lc/MqF Qs4FjyLqtQyW3nMXY1ETN2doSivkk9laNtOff3tFXL1fVTriOzKukFCWsaUPmKTeDTHLVLLv0Hvota3C51ZZBdrAPo1g007llEq48N111wAteF3kUBsx3 64PEbSuXLIsGfO6VT1U3 SyC 93nDKS3mQ9jzrd2T3IBr3XqNyDRVv/1b 7iKVI5Vytme0o6nda7MwXX279nVdrOGA567ZH/UHFb923W/VvhG/L1rROnmVNHfYTVN aLQuXNGoTWBophUzTWP1v 9fl8G223k7s1/y3WaHKvjjsvFe7LiUbIl9UewiinWLtG7whpsfSZbWdrbmfCZrvoH1X0HYcNm9hxyp337KGtUjLVo37sLhrtF31lgY98HtwfPIoFo7Y16FLivsJ4OTd6EhYvacfA1hg2nwkZsegdyLuIDsMo7yOgl2hB7PIF80mL2cjm67c6vcWzQ7QTpuS116KZg7LhVlM1u6rfNnz7zTyHdXLVbffq6N29mtqWr0DNIFK0DzJmcvsYHgPWli51ZVBqnJm2i6TOpXvS2SSWPUOeErgurC e6v0sng1okU9VN9KA5h2z4SbMvJ6k/snMDWWh571sPea0uT6l99NVZZLp/Y5L8PLuUoT21Hk77Q0bEDU1F /5QzcHgPWfSQpDISfWTBqfyNsW7amjVwHAuqbaKosDJP1MLWlCyitMom6LUaabmf3a8HbpSp7d OpW5cJDKSaqU9E7WbtG7whhsdS1eaqujwnaL6D9l1h23HQvIUeq2r24ZGWjfuw3tFgu oxjVPoD87q69CPeDeVOwKc2cC5jj0P7iBmL8pd7veZ31NDhrex27qxyg3eZJBWvKTteDd K2E2ZSbdsjQmZwv6LKicwSy0 zr3qNQOcFEtjHPWNWCe1DRrarkXMap3zMG9kj7l1hJ7x2KdrGj7uthpMalvOq14K4H4VrV7/be7foomvrMmLbuhoOWMvD1GpBuKtb1F7VbGesG8jMqub9tVFi67TKLWt8j1Mo77Nb8eRaJuE4NjqW5zOZ vaNexKWzeovxG1GXjPoziqXEALySIt1LaqzPaVcBd9Xx3  8or0XN3/qZ8Uyhb5m cVK2Zueq2Dd 0407PbYl/UMjwNIMZgKvlerQGcPcnJVyJNdq5ZEyXU1h89Q/sYaS2iMX/GYoqNw6oQProopZlm0Rp/qm58P0Spr59oJRdeCezpoz42HvtUNQ2cjv5jNw71MjDRBvLQaVcyua/k6T4uhmvLhU cz5BZ4N6kDo9hiZm5LoNsKkDlgnaeRaTfOyeXksuXc20vPfZB2w69tWy8KcNGluvdeUSdRtsdVtttXPN9LKdik9X 68EXWjoP1xB7arVo lkh2WdC8pCprvoH1Xg 24Mm/JSu99E8eqxssWgvsw6nLRAniKqTTkDsSQxwjpNCA1SGs7PYlZZJCQv0eLSPqeWUxjeMykFkXpCuqfwFQyi2zSujFYlX7ofWnV7T2tNCg1hKa1B0nvRdH7joS htR77JzfPHkpUU66lHNQqF3WgHLrhEjrQoStj/D39LJsixjVN30Nnfs4F2e 5fKLyntuEBj XtU8S91q8iY5wWWjftdcly2/O4oRVNLAAsq5JQHfGbZM6XnvshXvM6PAkF8DJGg5fbfHZljrtG8aAyX7UoHKSQb9/rL022xVCsmi0zPeZwfEoes8oL5tuSzkUiHzWDgznf9qDymTkPpWVZcjbbMhIn  tf2a/3bZgDTMk3tVaRJ1q4D9caTtajuOpTbp6Vazqh /FnRsCtp3NdiOJfBXQW42OVwZF/gbPhouWwjuw6jL9W1sbGya17SDbrnlFly/fl2/Xl5exujoqPe3cMd1M7lj5/JwyLW25TkcUIuwaF9j1GEN52mX8qtbrG t6Whdk2VJFDFVda IzuP2I3IY14Gwe8KnguUTN3IzLb1TaL5BT SDx9Lu1nv76N2xD9uO7ar2 4aHh81f9X93I/bAU3tI k jG6D0T2BxZAmJoLOl7RZlniieuq6 5bDcztT6GrmZTCWdb9t0dpnij UTN7lxydLaQm8cUa/qxrZbu/RgG5D7MHIxgKcWOc/r1Ok/7l1OQ8j1ne254VaY5uaJ4qQb65tIY76tveNmOU2K4KAKFKvujrst2r1MvYblEzf6sVBMlyBSuvVY2g692wbkPoxcDOCpReYRbpvdlM7TjfNE7bFb1q27nO7AQHHnSKDOfQkR9ZJePpayDUi9jwE8ERERERERUQwwgCciIiIiIiKKAQbwRERERERERDHAAJ6IiIiIiIgoBhjAExEREREREcUAA3giIiIiIiKiGGAAT0RERERERBQDDOCJiIiIiIiIYoABPBEREREREVEMMIAnIiIiIiIiigEG8EREREREREQxwACeiIiIiIiIKAYYwBMRERERERHFAAN4IiIiIiIiohhgAE9EREREREQUAwzgiYiIiIiIiGKAATwRERERERFRDDCAJyIiIiIiIooBBvAxMTo6al4RdR7rGxERUWt4LCVqP25XQN/GxsameU076JZbbsH169f16 XlZV053b JOon1jYiIqDU8lhK133ZsV/Ibw8PD5q/6v7sRe CJiIiIiIiIYoABPBEREREREVEMMIW S9Sm0BMREREREVFnxS2FngF8l6gN4Lu94hAREREREfUSXgNPRERERERERG3Rt6mY10RERERERETUpZhCT0RERERERBQDTKEnIiIiIiIiioGqHvhm7n7e6Yfq9wKWJxEREREREbVLXQB/9OhR81c4uXSeAWc4pzz/1vwVbnPz37A8iYiIiIiIKFCbU jPI3PrIZy6Yv7U/MY1w/58q9/Vbp2eH/n W3GrN4T81pVTONRVZdMmYcvVq8tMRERERETkg9fAa912YsC2HycvbmBjYwMXTwInjp2C72zuOY5zG dwfI/5O7Zq1kXVcoW9R0RERERE1NsYwMfInuOTOHrhLB5gjzMREREREdGus80BvOlBPZXx0sIPWd3e5zNWunjmvBkbQqdQVz5T/ZErOHWo/r3635B5OoIFXMCJfe44peq7M2oqwxp/6FTZjNwJTllmMofM/Nm90 b1 cq8ymJdOSXTuvPeqNzt7z EQ6osvbfEebUOD9VmA9T/bnO/I /Vrgt3ueTfoPf0F4XUBzNdQL0jIiIiIiKKgx3ogVcB2KUhnRK ceYoLpx4lwqvHAdnnVTxjY0zOLowUwnMfKmgbN8JDJwxn7l4EsUjbjAnwfs nD180XzfBmYP6g/5/MZBzMprN1VdTyjffRaHTeq6ehsz ourf/M0zqqAcvtcOTWDhf2HcZeXMn4BxTtPq3mZhVk8iyrnGeC0nv jWDhyK46pOXaWJ2q5u99/Ducm1XeseBExzq8s4OjkcdRnr1u/6 T8e9/X HfMe1XrwuW3nmxh9UEE1zsiIiIiIqI42IEAXgVgd7vR9JAKyIoou0GW9OrqHlLpaW3gSll98iiG3Dhuz3FMHr2AS5fV6ysP4OyFo5j0uzg6ym/o7zY9vTLtkQVckC W8ftPwp19ndLuvOygynzsOzGAM fsoHk/Dlei RqqnE baXU5W9NGLveazyysmKD3PFaKlXKoZv2uvU5ElN/ZqrD6oIXUOyIiIiIiohhocwB/B 7cb166dGA1gP5G8ZmkPx8Bzuhe2Is4Wfs97dDUbxw105mhrsd3u5geZz0ffj3tLYpcJgdx98mizkSQTIDi4bt8et9rXUG56L7chvVLRERERETUw9ocwO9B/8CFqjuln3/XCVw4OtQ48Lx8CRf234k75LXuQddjg 3pxwAW4GV1qwBxZsH0wO65C4f3L5i0d0vU3zDfXfd5GX/hBN5lflOntDsv46uJct9z12Hg7LvwrrMI6TG/gLPuXfZMJoReJ82u32aF1QciIiIiIqIe0PYU oOzF3ESJ7BPp0rfiiPFk7gYpff64N2Vzx27hIGGPbQHMauvc3Z 51Z9zbrbQ70Hx8 dwcCJfSZl29zQLPA3DmLoqElVdybU361GeJ/3xpvryWXcMRxG51PoO6yZcpe09IEFLAxMhjy6bT8GLh1zykxfk27WSeTfqV0XtvD3gusDERERERFR/PVtbGxsmtdYXl7G0aPRQtLNzU1cv37d/EV nPL8W/NXuM3NfxOL8pQ7ya8MVW4KWE3u9j6DOy/y2exERERERETttgM3saPYkrT0wJvXERERERERUecA/x/pX7RaVcAXhwAAAABJRU5ErkJggg==[/IMG]

---

### Post by tacolandia on 2024-05-19
disk management windows

---

### Post by yancek on 2024-05-19
The image in post 27 from Disk Management shows nothing on the 'D' drive which you say is your Linux/Ubuntu.  It shows free space as 100%.  In fact only what windows refers to as the 'C' partition which is the windows primary filesystem shows partially used and all others have 100% free.  Windows default installs will not show anything on a Linux filesystem as far as the ability to read or write to that partition and what you see in Disk Management is about the extent of what you will see in windows.  If you ran the 'repair' option from windows you reference above it might have overwritten anything on what you thought was your Linux partition.

---

### Post by oldfred on 2024-05-19
You can try testdisk to see if it sees old partitions.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

