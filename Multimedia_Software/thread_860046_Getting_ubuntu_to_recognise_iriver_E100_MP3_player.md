---
title: "Getting ubuntu to recognise iriver E100 MP3 player"
date: 2008-07-15
forum: Multimedia Software
---

### Post by Chris2691 on 2008-07-15
Does anybody know how to get Ubuntu Hoary to recognise an iriver E100 MP3 player.
My computer has no problem recogonising an ipod when its connected via USB but it will not recogonise my iriver E100 player. The iriver player is connected to the computer via an MSC connection to a USB.
Any help will be appreciated

Thanks

Chris

---

### Post by nikgare on 2008-07-15
Does your computer see the device at all?
What's the output of lsusb?

---

### Post by Chris2691 on 2008-07-15
The computer does see it as sdd

---

### Post by nikgare on 2008-07-19
Is it automaounted?
Is it used just like a mass storage device, or does it need special care like Ipods?

---

### Post by JoshHendo on 2008-07-20
You will need to format it in the correct format. Change it to the connection type that allows for hard disk mounting (MSC, not MTP).

Connect it to your Ubuntu computer via USB, and launch gparted from the terminal.
If you don't have gparted installed, run: sudo apt-get install gparted.

You need to launch gparted as root, so use: sudo gparted.

Look at the terminal output once gparted has been launched. It should say that it wasn't able to recognise something. Possible /dev/sbX (X being a variable in this instance). In gparted, there should be a drop down menu (could be on something like /dev/sda by default). Choose the one that you read in the terminal (if there is only two in the list, it is the one that isn't selected by default. This is a list of hard disks etc, the default one will/should be the one Ubuntu is installed on).

Now, in the main part of gparted it should say "Unallocated Space". Right click on it and allocate whatever it wants you to allocate to it (I can't remember what it is, though you want the selection "MS-DOS", thought that is default). Now, it should still say unallocated space still. Right click on it, select new again, and select the partition type you want. You will want to make a partition of the entire disk, and you will probably want it to be FAT32 (unless you are planning on having a single file larger than 4gb on it). Follow the steps, close the program when it is finished, disconnect and reconnect your E100 and it should be able to see the list.

If you need screenshots (I just did it, but I can do it again if you need more specific details) I can post them here.

- Josh

Also, if you happen to find a way to get MTP working, that would be great. I am thinking a similar thing needs to be done (it be partitioned in such a way that Ubuntu can recognise), though for now I am happy with my player working)

---

### Post by Chris2691 on 2008-07-21
Spot on: Thanks for your help

---

### Post by JoshHendo on 2008-07-29
> **Chris2691 said:**
> Spot on: Thanks for your help
Glad I could be of assistance :).

If I get it working in MTP mode I will post here, as I wouldn't mind being able to use that (better music management), but having music is just good enough for me for now... it could be a format issue with MTP, but it is harder to re-format, and currently I have it setup so it works (to change I need to re-format it using the actual unit).

- Josh

---

### Post by jeffbarish on 2008-07-30
Are you now able to access both internal and external memory on the E100?  When I connect my E100, only external memory mounts.  When I connect the E100 to Windows, I get two drives, one for internal the other for external.

---

### Post by jeffbarish on 2008-07-30
Ah, I am able to mount the internal memory manually (sudo mount -t vfat /dev/sdc /mnt), it just doesn't automount.  Maybe connecting a USB device is able to trigger only one action, in this case mounting external memory.

---

### Post by MentalOxide on 2008-08-07
Hello Ubuntu minds, 

I've been following this thread closely as my e100 difficulties are seemingly a combination of all the problems mentioned on this thread, however, my player is still unusable. Here is the history. 

My e100 has been working perfectly for about 2 months, and then last week, when i tried to delete some old albums from it a message told me that I did not have the necessary authority to do this because it was a read only drive.  I had made sure that it wasn't on 'hold' and rebooted several times, but to no avail. I also pressed the reset button, but again no effect. I read on the net that others had encountered this problem and that formatting the internal memory using the e100s own formatting function solved the problem. So i did that, but instead of solving the problem, my e100 failed mount, (at least visibly on the desktop) When i use the lsusb function it is visble however. It is visible through the 'Places' menu, but when i click on this, ubuntu tells me that i cannot access it, and that 'there is probably no media on this device.'

I then followed JoshHendo's gparted instructions to the word, however   when I created a new disk label for it, it had no effect, and remained unallocated and unreadable. 

And so this is where I am upto. 
Interestingly, when I plug it into a Windows machine, the connection menu on the e100 offers me only two options - 'power only' and 'power and play', but not 'power and data'.... and when i plug it into my ubuntu machine it gives me all three options. 

Any ideas would be much appreciated, as I've just begun a six month backpacking journey of south america, and these 10 hour bus rides are going to get horrible pretty soon without some audio. Thanks in advance.

---

### Post by jeffbarish on 2008-08-07
When I was desperate to get some music into my E100 and nothing else was working, I removed the microSD card and put it in a USB memory card reader.

When you reformatted, did you choose MCS?

---

### Post by devosion on 2008-08-08
I just wanted to mention thanks MentalOxide. I managed to get my iRiver lplayer connected through MSC. Hopefully MTP support will be integrated soon.

---

### Post by MentalOxide on 2008-08-08
Thanks for the prompt response jeff. 
In answer to your question, the e100´s internal formatting feature doesn´t offer me a choice of msc or mtp. however once reformatted im able to select msc or mtp from the settings menu. Msc is chosen by default. (ps I am not using a microSD chip, so that isnt the problem)

Here´s another development too.
I´ve been able to find another public computer with active usb´s and i am now seeing all three options (power and data, power and play, power only) and it is mounting fine on this windows machine. (Oh how I hate having to say that!)

Do you think attempting to manually mount the e100 in ubuntu would help?
I´ve seen some guides to doing so on the net, although playing with that fstab file looks a little dangerous for a noob like me. Then again, when you´re self taught like me, you tend to get used to breaking computers. ha ha.

---

### Post by jeffbarish on 2008-08-09
Yes.  I have not been able to get the internal memory to automount.  I thought that the presence of external memory might have been the problem, but perhaps something else is happening as you are observing the same problem even though you aren't using external memory.  Try the mount instruction I provided previously (sudo mount -t vfat /dev/sdc /mnt).  Using that command avoids the need to modify fstab.  If it works, you can worry about fstab then.

---

### Post by MentalOxide on 2008-08-09
ok, thanks jeff, I tried that command (sudo mount -t vfat /dev/sdc /mnt) although for me it was 'sdb' and there was communication to the e100, signifified by a brief 'do not disconnect' message on the e100, however there is still no drive visible on the desktop, and when i naviagate through 'Places - computer'menu and click on the e100 drive, i receive the message 'Unable to mount media - There is probably no media on the drive.' Hmmph... is it time to worry about fstab now?

---

### Post by jeffbarish on 2008-08-09
Navigate to /mnt.  Or open a terminal window and cd /mnt.  You will not get a drive on the desktop.  Navigating to the E100 as you did works for external memory only.  I base my suggestions on observation as I don't see why Ubuntu/E100 behave this way.

---

### Post by MentalOxide on 2008-08-10
Hmmm.. sorry to continue the frustration Jeff, but i found nothing in /mnt (via nautilus), even when I 'showed hidden items'. Initially I thought this was an e100 issue, however since it has worked successfully on a windows machine, I'm guessing its ubuntu that has the bug.

---

### Post by jeffbarish on 2008-08-10
Type mount at a command prompt (after you follow previous instructions to mount the E100) to confirm that you successfully mounted the E100.

---

### Post by MentalOxide on 2008-08-18
hi all, 
im back from a week in the southern Andes, and now Ive found an internet connection. Hi jeff, thanks for not forgetting about me. I navigated to cd /mnt and typed mount and i received the following information:
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-15-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)


Does this mean anything to you? I see the words 'errors' in the first line as the most worrying.

---

### Post by jeffbarish on 2008-08-18
Well, /dev/sdb is not mounted on /mnt.  In fact, nothing is mounted on /mnt, which is why you don't see any files there when you navigate to it.

What is the output when you try to mount the E100 (mount -t vfat /dev/sdb /mnt)?

Do you understand that typing mount alone just lists what is mounted while mount with the other stuff actually performs the mount?  From what you said before, it seems as if mounting /dev/sdb worked for you before, so we should see it in the list of mounted devices.

Do you have someone local who knows Ubuntu?  It is hard trying to debug your system through a forum.

---

### Post by MentalOxide on 2008-08-18
OK, thanks again for all your patience Jeff, I'm sure this is getting a bit frustrating for you. Unfortunately I don't know anyone who uses ubuntu here, in fact Im the ony person I know who uses it both here and at home in Australia. So I'm completely self taught (which shows). I ran into a brazilian guy who worked in IT and was familiar with Linux. He played around for an hour or two, and said that if i manually mounted it (including modifying the fstab file) it would probably work. 

Anyway, back to the terminal code.
I typed    mount -t vfat /dev/sdb /mnt  and it told me that only root could do that, so I used sudo mount -t vfat /dev/sdb /mnt and I got this:

laptop: ~$ sudo mount -t vfat /dev/sdb /mnt
mount: /dev/sdb already mounted or /mnt busy
mount: according to mtab, /dev/sdb is already mounted on /mnt

as I mentioned before, lsusb lists \Bus 005 Device 006: ID 4102:1041 iRiver, Ltd. 
and when I navigate through nautilus iriver e100 is visible as a drive, but when i attempt to mount it (right mouse click) i'm told: unable to mount media - there is probably no media in the drive.

---

### Post by jeffbarish on 2008-08-18
If it's already mounted, then it should have shown up on the output you quoted in post 19.  If you are getting the message that it's already mounted and then you are producing the mount list you quoted in post 19, something is wrong that is beyond me.  If you can't mount it because it's already mounted, it should appear in the output of "mount".  At that point, you should be able to cd to /mnt and see something with ls.  As I said before, my experience indicates that until you get it mounted properly, the e100 that appears in a graphical file manager is the external memory.  When you do get it mounted, the internal memory will not be identified as e100.  You will get to it by clicking on the /mnt folder.  Since you don't have any external memory, the complaint that there is "probably no media in the drive" makes sense.  If this advice doesn't solve your problem, I have nothing else to offer and am sorry that I couldn't help.  Well, just one other thought: a 4GB miniSD card costs a little more than $10.  Get one and use it instead of the internal memory.  Good luck.

---

### Post by MentalOxide on 2008-08-18
Well, thanks anyway for all your time and effort Jeff. It was above and beyond the level of help I'd expected, and it was much appreciated. I guess I'll just check back here form time to time, hoping   for a solution. Till then, I guess I'll be doing all my tranfers to the e100 via internet cafes, or i'll switch back to my trusty old chinese knock-off mp3 player. It aint pretty, but it never fails.  Thanks for everything.

---

### Post by jlukescott on 2008-08-18
Just a quick note on writing the partition table for the E100 in MSC mode: I had a lot better luck using fdisk instead of parted or gparted. In parted, my partitions were overstepping the bounds of the memory, or something to that effect, so I kept getting corrupt files when I copied music over. 

If anyone is having wackiness when writing files or when setting up the partition table, then give fdisk a try. Here are the steps:
- switch the E100 to MSC mode
- run command "ls /dev/sd* -al" for future reference...
- plug it into the computer and select Power & Data
- run command "ls /dev/sd* -al" again, and note what device name was added (this is the E100)
- run 'fdisk' on that device, i.e. "fdisk /dev/sdd"
- write a new partition table & new primary partition to the device
- save changes & exit (I think the option is "w" in fdisk)
- after exiting, run "mkfs.vfat /dev/sdd1" (or whatever the device is)
- either mount /dev/sdd1 to a mount point, or unplug & re-plug the E100 to get it to show up in your file browser.

---

### Post by MentalOxide on 2008-09-24
hi again all, 

jlukescott, i've been using gparted to try and reformat my e100, and its definately formatted now, problem is, my linux still wont mount it, and im forced to find internet cafes with open usb ports to load anything onto my iriver. its becoming a tiring chore.  will your fdisk plan help me? if you need to know the history of my problems thus far, just check the past posts of this thread. cheers.

---

### Post by Grippon on 2008-09-30
Hi this is a compilation of what I have read in various threads, including this one and bug reports Its very quick and dirty, still, I hope you find this useful.
iRiver E100 ubuntu 8.04
Problem: MTP does not work
Work around until someone finds something better:
On the iRiver E100
Use windows to update the firmware (if necessary) I am currently at 1.10, and I was at 0.31 or at least thats what the iRiver Firmware updater told me.
When you have completed updating your firmware, Navigate to Settings->Advanced-> Transport Options and select MSC save your settings, When it asked me to format I said yes. If you have data on your iRiver you should back it up. Formatting is generally destructive, my iRiver is new so, there is no risk of loss.

connect your iRiver to your Ubuntu machine and select power and data


On ubuntu:
lsusb  should give you something like
Bus 006 Device 025: ID 4102:1041 iRiver, Ltd.
Notice the stanza below, specifically int="0x1141"  use lsusb to get the correct 0xnnnn number for your system
add a xml stanza below for hal recognize the iRiver E100.

sudo vi /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi

<!-- E100 -->
          <match key="@storage.originating_device:usb.product_id" int="0x1141">
            <addset key="portable_audio_player.access_method.protocols" type="strlist">storage</addset>
            <append key="portable_audio_player.output_formats" type="strlist">audio/x-ms-wma</append>
            <append key="portable_audio_player.output_formats" type="strlist">application/ogg</append>
            <append key="portable_audio_player.input_formats" type="strlist">audio/mpeg</append>
            <append key="portable_audio_player.playlist_format" type="strlist">audio/x-iriver-pla</append>
            <append key="portable_audio_player.playlist_path" type="strlist">Playlists/%File</append>
            <append key="portable_audio_player.audio_folders" type="strlist">Music/</append>
            <append key="portable_audio_player.audio_folders" type="strlist">Recordings/</append>
       </match>
(reference [https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/261685](https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/261685))
Restart hal (May not be neccessary, I did it anyway)
/etc/init.d/hal restart

check fdisk to see where the system put your iRiver. the entry complaining about Partition 1 having different physical/logical beginnings is what you want.
fdisk -l

create a mount mount and edit /etc/fstab
sudo mkdir /media/iriver
vi /ect/fstab
add the line (mount the /dev/sdX, its not a typo, don't use a partition number.
/dev/sdX /media/iriver vfat rw,user,noauto 0 0

mount it
mount /media/iriver

I used banshee to write ogg files directly to the /media/iriver/Music directory.

---

### Post by bp1509 on 2008-12-26
d

---

### Post by EhrinJ on 2009-03-04
I followed the instructions earlier in this thread, and I have Ubuntu 8.10 recognising my e100...

But the second I try and alter any files or folders on the iRiver, everything goes 'BOOM'. The Mp3 player crashes/freezes and Ubuntu unmounts it.

HAL recognised the player fine the first two times. The third time it acted as a read-only drive, and now...well *shrugs*

Any help at all would be appreciated, as the above quoted hint doesn't seem to help for me.

---

### Post by Ipharus on 2009-03-27
Hi All,

I've just bought one of these little trinkets (iriver E100)
It came with firmware version 1.05 and it didnt mount the internal memory on my ubuntu jaunty, only the micro sd card. So i put it in my windows machine, and yes, all there, so i did some firmware upgrading till version 1.16 and now all is working fine (i've only tried MSC/UMS)
I might try MTP with rhythmbox, one day, or maybe not, just general storage is how i like it best.

Firmware updater download:
[http://211.39.137.201/download.asp?filename=2009030517193198027.zip&filepath=/file/down/](http://211.39.137.201/download.asp?filename=2009030517193198027.zip&filepath=/file/down/)

E100*New Firmware Ver 1.16
-. Customers who purchase*E100 can upgrade their players 
** either by Firmware updater* or Iriver plus3

Please check your connection mode before updating New firm ware.

How do I check my connection mode? 
**Menu-> Setting -> Advanced -> Connection mode
If your player ' s connection mode is MTP, please use Firmware updater to*upgrade New Firmware. 
If your player ' s connection mode is UMS, please use iriverplus3 to*upgrade New Firmware. 
*
*
-. Upgraded Points
1. Revise malfunction of broken letters

---

### Post by JohnyN on 2010-04-21
Hey guys,
since karmic there are problems again. However, manual mount works successfully.
Now I'm running Lucid 10.04 beta 2 with latest updates and my iRiver e100 has firmware 1.16 (I haven't upgraded it since it works in 9.04).
I'm pretty sure that in Ubuntu 9.04 it works good, ubuntu automatically mounts device (both internal and external microSD memory). However since Ubuntu 9.10 I'm experiencing this bug. Every time, when I want to load some music to my player, I have to manually mount it and copy files with root privileges.

Thanks for help

---

