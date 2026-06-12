---
title: "is it possible to have Mint on a usb drive boot an ubuntu installed system?"
date: 2019-01-26
forum: MINT
---

### Post by sdowney717 on 2019-01-26
I have a 320gb Maxtor drive in a usb case.
I managed to install Mint on it and it boots fine off the usb port with no other drives in an older PC.
It is a 32 bit os install.

I then connect it to a different newer PC with 64 bit ubuntu OS, and it fails to boot every time.
I tried lots of stuff and reinstalls. 

I am showing some errors. 
The first pic is if I hit F11 to show the bios boot selection and select the usb drive
Second pic is after I update-grub in ubuntu with drive connected to the pc.
Third pic is result of selecting Mint after rebooting PC

This same usb drive boots perfectly as either usb or when plugged into the IDE port of the older PC.

Before getting the older PC involved, I tried installing (installs always said it worked) on the new PC, but it always error when selecting the usb drive to boot.
(fourth pic)
So what is going on you think?

---

### Post by yancek on 2019-01-26
Did you boot Ubuntu and mount the drive partition with Mint on it to check to see if you actually had the file mentioned?
The third image pretty much explains the problem, the partition is encrypted.  Do you have a separate boot partition for Mint?  Do you get prompted for the password for encryption?  I don't use encryption so really have no advice.

I see you have windows 10 and 7 as well as Ubuntu/Mint.  Are all of these UEFI installs or all Legacy/MBR?

---

### Post by sdowney717 on 2019-01-26
> **yancek said:**
> Did you boot Ubuntu and mount the drive partition with Mint on it to check to see if you actually had the file mentioned?
The third image pretty much explains the problem, the partition is encrypted.  Do you have a separate boot partition for Mint?  Do you get prompted for the password for encryption?  I don't use encryption so really have no advice.

I see you have windows 10 and 7 as well as Ubuntu/Mint.  Are all of these UEFI installs or all Legacy/MBR?

When did it get encrypted? I just installed it today, I did not select any encryption. All the Mint partition files I can view and open in ubuntu.
IMO, the encryption message is bogus, like fake news.
Nothing is UEFI, both PC are legacy bios.


Which file is mentioned? the I-386?

But see I  had also tried earlier to install Mint 64 bit using the newer PC with 64 bit OS, it installed and also always failed to boot.

yes, that file is on the linux mint drive.
Here they are  viewed in Ubuntu file manager.

They are on the 26gb system partition of the Mint usb drive.

---

### Post by oldfred on 2019-01-26
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Run from newer PC, using live installer if necessary and USB drive plugged in.

---

### Post by sdowney717 on 2019-01-26
> **oldfred said:**
> May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Run from newer PC, using live installer if necessary and USB drive plugged in.

Thanks, got the summary here, run from a workng ubuntu install. It asked me if one of the 1gb sata drives was a portable drive, and I said no.


[http://paste.ubuntu.com/p/4973dMjzzB/](http://paste.ubuntu.com/p/4973dMjzzB/)

sdd is the usb drive, it has the 320gb Maxtor ide drive inside.

---

### Post by oldfred on 2019-01-26
Do not use Boot-Repair auto fix with multiple drives. That will install one grub to all drives. Use advanced mode, if using Boot-Repair to reinstall grub and choose install and MBR of same drive.
You want to keep your Windows boot loader in the Windows drive(s) and may have version issues, with other installs.

Elf error is usually something related to grub versions. Is grub in MBR different than default install it is booting? Or when you reinstalled did you not select same drive for grub install in Something Else. Otherwise grub defaults to first drive.

Normal not found is another version issue. I think I have primarily seen it with newer UEFI systems where trying to boot in other boot mode. BIOS boot with UEFI install or UEFI boot with BIOS install. Note sure why you get that?

Not sure if related to old 32 bit installs or BIOS settings or USB boot.
There are IDE/AHCI settings for internal drives. With old IDE systems, boot files had to be inside the first 137GB of a drive. It could be a separate /boot partition or just have all of / (root) inside first 137GB and rest of drive as /home or data. A few users had system working in larger drive with / over 137GB. But then update installed newer kernel or grub boot files beyond 137 and system stopped working. Files typically are randomly located anywhere inside the partition.
Similar issue is more prevalent with some older installs and USB boot. (maybe back then they were 32 bit?). That would not be IDE vs AHCI as that is not used for USB boot drives. Not sure why but a few users moved / to inside 137GB and it worked, but others did and it did not work. 

Your Windows on external drive will not boot as Windows does not allow boot from portable drives.

No specific solution, but perhaps a few things to try. Grub reinstall, moving / to beginning of drive (but you then have to erase Windows). Not sure what else.

---

### Post by sdowney717 on 2019-01-26
"Grub reinstall, moving / to beginning of drive (but you then have to erase Windows). Not sure what else."

Interesting about location of files. The IDE drive when in its usb case and plugged into an older 32 bit only pc, does boot the usb drive perfectly.
I suppose I could wipe windows, I dont use it, I only was keeping the NTFS for data.
I had done a update-grub. Is that different from reinstall grub?

"Elf error is usually something related to grub versions. Is grub in MBR different than default install it is booting? Or when you reinstalled did you not select same drive for grub install in Something Else. Otherwise grub defaults to first drive."

The ubuntu install 64bit was a new install when last ubuntu was released.
The mint install 32bit is a fresh newest version of mint install.
So about grub versions, I dont know.
When I installed Mint, I told it to install grub on the drive where I was installing Mint, so sdd.

Neither PC are uefi, they are all legacy bios.

Whole reason I was trying to do this, is my ATSC tuner cards after I installed the latest ubuntu no longer detect the broadcast signal.
Since it was a new version of the os, I thought might be related. So I wanted to setup a usb boot drive, boot Mint and see if they then work.

I did manage to boot Mint from the usb drive on the old PC with a Tuner card in, and it detected the broadcast signal.
Kaffeine will install fine, it shows a tuner card, but when scanning for channels, I get no signal at all on the new ubuntu version PC.
In Mint, I get a signal on the old PC So yeah, maybe I should wipe the usb drive and start fresh..

But even so, why is the new ubuntu OS not detecting the broadcast tuner signal for OTA TV?

w_scan also sees no signals. But the tuner card appears ok in kaffeine, it is detected fine.

Hi OldFred.
A person helping me on another forum tried to setup Mint on an external ssd drives, and it fails the same way as for me.

Do you know if ubuntu can do this, I mean have you had experience installing ubuntu to a portable drive? Maybe something with Mint itself?
 
[https://www.linuxquestions.org/questions/linux-software-2/how-can-i-install-mint-to-an-external-usb-drive-4175646972/page3.html](https://www.linuxquestions.org/questions/linux-software-2/how-can-i-install-mint-to-an-external-usb-drive-4175646972/page3.html)

---

### Post by oldfred on 2019-01-26
I do not know Mint.  Even though you have Ubuntu, moving to Mint sub-forum since your issues are mostly Mint related.

Best to start a separate thread on your tuner issue. I have seen a few threads, but have not followed them.

Some reason for 32 bit? That is effectively obsolete. Ubuntu only supports it with upgrades, not new installs. And various software has stopped supporting 32 bit.

---

### Post by sdowney717 on 2019-01-26
> **oldfred said:**
> I do not know Mint.  Even though you have Ubuntu, moving to Mint sub-forum since your issues are mostly Mint related.

Best to start a separate thread on your tuner issue. I have seen a few threads, but have not followed them.

Some reason for 32 bit? That is effectively obsolete. Ubuntu only supports it with upgrades, not new installs. And various software has stopped supporting 32 bit.

regarding 32 bit, the old PC can not run 64 bit os.
After I could not get 64 bit Mint to boot on the ubuntu 64 bit pc as an external bootable drive, I thought to try it on a different PC, then I discovered the old pc was 32 bit only. So was stuck trying work with 32 bit os for the tuner testing. There is always a reason for my madness.

---

