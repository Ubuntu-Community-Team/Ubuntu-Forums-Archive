---
title: "Root partition recovery. Grub failed"
date: 2022-05-20
forum: MINT
---

### Post by besmart on 2022-05-20
Hello! Thanks for your attention to my problem.
I&#8217;ll try to describe the issue from the beginning and I&#8217;m sorry for my English.

I have the 1Tb HDD with win7 and Linux mint (previously there was only  win7 system). Later I added the 250Gb SSD with win7 and Linux mint as  well. After adding SSD, Grub detected all 4 operating systems. It worked  perfectly. I used SSD as a system drive and HDD as a storage for media  files. Both drives are GPT-based. 

But half a year ago Grub stopped detecting Linux mint on the HDD. I have  a lack of knowledge in this area and looked for some information in  google. I decided that it was a problem with the ext4 file system and  tried to recover using superblocks via fsck. There was the response that  superblocks were damaged and I postponed solving this issue. Win7 on  the HDD can still boot via boot menu.

I continued using two operating systems on the SSD. But several days ago  Grub failed. There was a message &#8220;minimal bash-like line editing is  supported&#8221;. Win7 on the SSD works normal. I decided that something  happened with ext4 file system again and tried to recover it with  superblocks. I tried the first one and it failed as well. 

I think, it was my mistake. I should have solved the Grub issue another  way. I found the information that it needs to boot into the Live USB  stick and type several commands. But now it&#8217;s impossible because the  root file system is damaged. &#8216;/home&#8217; partition can be mounted and I  copied necessary information.

I used TestDisk to detect partitions on the SSD. The current partition  structure looks good. But after quick search the intersection between  two partitions is revealed and they&#8217;re pointed as Deleted. Deeper search  helped to find the root partition that matches the current partition  structure and there is the access to files on this partition. But deeper search can't find two Windows reserved partition and I can't recover the needed disk structure as a result.

Is it possible to restore the root partition on the SSD and fix Grub? Or  is there only way to reinstall the system? I can&#8217;t figure out the  TestDisk output and further steps to perform. I need a direction what  information I should look for. 

As for the HDD, I can&#8217;t get access to files on the Linux partitions  using TestDisk. In the last resort I&#8217;ll try to restore files from  &#8216;/home&#8217; using DMDE and it&#8217;s not necessary to restore the root partition.

As it&#8217;s already been mentioned, win7 systems works on the both drives. 
I also attached screenshots with the drives smart info, TestDisk search results, and GParted.

1. SSD SMART
2. SSD TestDisk current partition structure
3. SSD TestDisk quick search
4. SSD TestDisk found root partition
5. SSD GParted

Can't add more screenshots about HDD because of 5 per post restriction.

---

### Post by oldfred on 2022-05-20
You should only have one Microsoft reserved per drive. That is a required unformatted partition.
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
Since unformatted gparted will show an error, that you can just ignore.

But error on ext4 partition is not normal. If in gparted you click on triangle/error message what does that say.
Often you just need fsck or e2fsck on ext4 partition(s).

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

If that does not work this may tell more, but cannot fix drive issues as its normally just reinstalls grub.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by QIII on 2022-05-20
Moved to MINT as a more appropriate sub-forum.

---

### Post by besmart on 2022-05-21
oldfred, thanks a lot for your help!

You're right. There is only one Windows reserved partition. It was just listed twice in TestDisk.

Sorry, I hurried to type the commands and didn't clicked on gparted error message.

There was an error message after this command (sda5 in my case). See the second screenshot
sudo e2fsck -C0 -p -f -v /dev/sda5

This command helped! 
sudo e2fsck -f -y -v /dev/sda5

I briefly watched the manual for this command and it seems the key difference is a '-p' parameter.

This is the link  to the Bootinfo summary report:
[URL="http://*******.us/nvIky7"]http://*******.us/nvIky7
[/URL]I'd already tried to use Boot-repair before created this topic. But there was no the "Recommended repair" button. This time, when the root partition was recovered with help of the second command, this button appeared, and I didn't click on it. After rebooting grub started working normally and detected both mint and windows systems.
Looking at the report, the message "No boot loader is installed in the MBR of /dev/sda" seems strange considering that the system is working.

It seems I can try to recover the ext4 HDD partitions using e2fsck as well.

sda - SSD
sdb - liveUSB stick
sdc - USB stick for screenshots

---

### Post by besmart on 2022-05-21
So, I tried to recover the HDD partitions the same way.
 
The commands did no effect on root partition (first screenshot).

After this command
sudo e2fsck -f -y -v /dev/sda6
the /home partition was recovered but not as expected. All the found files were placed in the hidden "lost+found" directory.

P.S. The main problem was solved in this topic. Should I start another one about my HDD?

---

### Post by oldfred on 2022-05-21
Best to have topic in question title, so start a new thread. 
Since Mint put it in the Mint sub-forum even though issue may be common. We do not know what changes Mint does as not an official flavor.

Why are both drives sda?

The MBR is only used for now very old BIOS boot. So it should not have a boot loader in MBR, boot files are in ESP - efi system partition.
Microsoft has required vendors to install Windows in UEFI/gpt mode since 2012, so almost all hardware is UEFI. BIOS mode available primarily for old BIOS hardware now 10 years old.

---

### Post by besmart on 2022-05-21
> **oldfred said:**
> Best to have topic in question title, so start a new thread. 
Since Mint put it in the Mint sub-forum even though issue may be common.  We do not know what changes Mint does as not an official flavor.

A title may be almost the same. My HDD has windows and linux OS as well, and there is also a grub issue.
QIII has already moved the thread to Mint sub-forum.

> **oldfred said:**
> Why are both drives sda?

The SSD was physically disconnected.
Here is the link  to the Bootinfo summary report of my HDD:
[http://*******.us/H9szYr](http://*******.us/H9szYr)

---

