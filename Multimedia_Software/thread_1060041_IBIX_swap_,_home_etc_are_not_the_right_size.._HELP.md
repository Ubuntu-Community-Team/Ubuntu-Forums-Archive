---
title: "IBIX swap , home etc are not the right size.. HELP?"
date: 2009-02-04
forum: Multimedia Software
---

### Post by forestwalkerjoe on 2009-02-04
i have this lap top i am converting to a DUEL booted WIN/IBIX linux system. 
It has given me some trouble with install and i have most of it all worked out.. DVD is issued still.. DIAL OUT MODEM.. and well. 
I found out when i did the LIVE CD and then INSTALL that i chose the wrong sizes for ROOT , HOME and SWAP. 
i know that the partition thing can allow me to change those.. but i need help to make sure i dont mess up all the work we got done in here over the past week.. every single day. Thank you PYTHIAS for all the hard work. 

this is an older SONY VIAO.. and if i knew the command codes to pull up the discription.. i would.. but i dont. 
I really need some one to help me resize the areas mentioned.. so that i am properly using the resources i have on this OLD thing. 
I also have notes out there asking for help getting the DVD working again. I was able to get the codexs in there.. and it DID work.. then stopped not long after i installed the MIRO program.. at least i think MIRO did this. 
I also have trouble with the DIAL OUT MODEM PPPOE not detecting the modem at all. 
So any one who wants ta help me out.. i have those each on different threads. 
then i have MORE fun styled questions.. as as soon as i am confident of this lappys install.. i am setting up to install UBUNTU on my desktop.. once i am confident i know how to do it with out a lot of help.. i'll take these to the HOST FAMILY and set up their DUEL BOOTED SYSTEM.. 
ANY TAKERS? 

FWJ

---

### Post by caljohnsmith on 2009-02-04
How about opening a terminal (Applications > Accessories > Terminal) and post:
```
sudo fdisk -lu
```
And please identify all your partitions. We can work from there if you want.

---

### Post by forestwalkerjoe on 2009-02-04
here is the output you requested.. i still am not clear on how to read all that. My windows is Win 2k In the first one. 
thanks for helping. 

rj@rj-laptop:~$ sudo fdisk -lu
[sudo] password for rj: 

Disk /dev/sda: 30.0 GB, 30005821440 bytes
16 heads, 63 sectors/track, 58140 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x96819681

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    24595514    12297726    c  W95 FAT32 (LBA)
/dev/sda2        24595515    58605119    17004802+   5  Extended
/dev/sda5        24596271    40979231     8191480+  83  Linux
/dev/sda6        40979295    45329759     2175232+  82  Linux swap / Solaris
/dev/sda7        45329823    58605119     6637648+  83  Linux
rj@rj-laptop:~$

---

### Post by caljohnsmith on 2009-02-04
How much RAM does that computer have? I notice your swap partition is about 2 GB, so do you have 1 GB of RAM? Considering the HDD is only 30 GB, I think I would shrink your swap partition so it is 1 GB (assuming you have 1 GB of RAM or less). Also, your other two linux partitions, sda5 and sda7, are 8.1 GB and 6.6 GB respectively. Do you know which is your root and which is your home partition? How about also posting:
```
mount
```

---

### Post by forestwalkerjoe on 2009-02-04
i have this thing divided up.. i cant recall what the total is on the hard drive. I thought it was 60 or 80 gig. if i had that chance i could go back and redo it all. but i dont have disks for the win 2k. 
i do know i put too much in the swap and too much in the other one.. but not enough in the ROOT one. 

rj@rj-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rj)
rj@rj-laptop:~$

---

### Post by caljohnsmith on 2009-02-04
According to fdisk, your HDD is only 30 GB, so that unfortunately doesn't give you much freedom when it comes to changing your partition sizes. Also, based on the output of "mount", sda5 is your root partition, but your sda7 partition is not mounted anywhere. How about posting the following:
```
sudo mount /dev/sda7 /mnt && ls -l /mnt
df -h
```

---

### Post by forestwalkerjoe on 2009-02-04
ok. i am confused on how large the drive is.. or if Windows has a hidden partition. 
but either way.. lets see what can be done with what seems to show. 
you asked for OUT PUT: 

here is is: 
rj@rj-laptop:~$ sudo mount /dev/sda7 /mnt && ls -l /mnt
[sudo] password for rj: 
total 20
drwx------  2 root root 16384 2007-09-03 21:45 lost+found
drwxr-xr-x 15  501  501  4096 2009-01-27 23:36 rj
rj@rj-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             7.7G  6.2G  1.2G  85% /
tmpfs                 125M     0  125M   0% /lib/init/rw
varrun                125M  216K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M  2.7M  122M   3% /dev
tmpfs                 125M  148K  125M   1% /dev/shm
lrm                   125M  2.0M  123M   2% /lib/modules/2.6.27-7-generic/volatile
/dev/sda7             6.3G  145M  6.1G   3% /mnt
rj@rj-laptop:~$

I would also like to ask you. I played with a few linux distro's. Many were different from each other. PUPPY.. PCLINUX.. Ubuntu now.. Freespire 2 versions. Damnsmall.. Mandriva mandrake.. Slack ware.. but that was very short. 
Each had troubles and benifits.. i was looking for the one that would do best for me. 
Last year.. 14 months ago.. i had installed 8 of them on my system. Testing and trialing them on my desk top. ONCE i found the one i wanted.. at that time was PCLINUX.. i deleted each. the man who was helping me in the Freespire forums.. sudenly disappeared and i was not able to get adaquate help to put ONE version back on. 
My attempts now.. are two fold.. to set up this lap top to be support for a family who are losing a VIRUS battle on hard drive. SO i can restore system windows.. then duel boot it to ubuntu. 
and to install for myself on Desktop.. I am typing on the Lap top now. 
Here is my real question:
i have become confused over time with the different types of linux.. coding in terminal and gui etc.. 
I have chosen to use UBUNTU now.. and i want to know how i can learn all this terminal code command stuff you guys in here seem to natively know. 
is it a matter of schooling? a good book i can read? not really wanting to read a book.. or is there a class in here that teaches basics? i keep seening folks write SH this.. dash H some such.. or APT-GET so on so forth.. i am getting better with understanding APT GET things.. but i want to know.. each of these codes. What they mean.. and what changes to them cause what effect. 
I dont want to distract you from our primary issue.. but i really would like to know how to LEARN this. I will USE the ONE LINUX now.. no confusing issues with that.. and i will study like some one obsessed.. if some one will teach me. 
thanks again 
I'll be back online tomorrow morning.. i take this little lappy to work with me.. with no net connection there. 
FWJ

---

### Post by caljohnsmith on 2009-02-05
OK, so your root sda5 Ubuntu partition is 85% full, while your sda7 home partition is only 3% full. Therefore, I wouldn't recommend shrinking sda5 at all; what you could do is shrink your sda6 swap partition from the end by 1 GB so the total size of your swap is 1 GB, and then you could expand your sda7 home partition from the beginning to use that 1 GB of space. Or if you plan on installing lots of programs in Ubuntu, you could instead shrink swap by 1 GB from the beginning, and give the 1 GB to your Ubuntu root partition sda5. It's up to you. Also, how about posting:
```
cat /etc/fstab
du -sh /home/rj
```
For some reason your home partition does not seem to be getting mounted properly, which is probably why it is only 3% full right now; all your personal files are probably in the /home/rj directory in your root sda5 partition. 

About learning the linux commands, for one thing I wouldn't recommend trying to memorize all of them with all their different flags and options, because that's too much work. Of course it will be helpful to memorize some of the more basic and important ones like you have all ready started doing, like apt-get, fdisk, cat, ls, df, etc. What I like to do is keep my own "cheat sheet" of commands with useful examples of how to use them with their different options, and it's something I've built-up over time as I come across useful examples. That way I don't have to memorize everything, I just have to remember "oh, there's a command for that" and then I go look it up if it's not all ready one of the commands I have memorized. Also, if you want to learn more about any individual command, you can type:
```
man <command>
```
And that will give you the manual page for <command>. Here is a website that you might find helpful in learning more about linux commands:

[http://www.linuxcommand.org](http://www.linuxcommand.org)

And also, I would recommend downloading this collection of linux command PDF documents:

[http://drop.io/linux_command_refs](http://drop.io/linux_command_refs)

Hope that helps some.

---

### Post by forestwalkerjoe on 2009-02-05
here is your output:

rj@rj-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=4e1de464-d3c7-4be0-9430-474ebfcc3f83 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e7b56a01-669f-4e83-bd41-bfa06eb0d841 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
rj@rj-laptop:~$ du -sh /home/rj
1.1G	/home/rj
rj@rj-laptop:~$


 I also have this intermitant problem. 
some one was trying to work it out for me.. but it comes and goes. 

I keep having issues with failure to "something" at boot up. It seems like the code that the computer reads.. to start functions.. is failing to read the part about refresh rate or loading the driver that runs the Graphics card. 
When i log into the Win side of my duel os.. there isn't a problem.. so i can safely say.. its not the hardware. 
it was EVERY TIME.. each and every time i would shut down.. and then later restart.. i would have to fight to get it to load the screen.. JUST a black screen.. no sounds nothing. 
the guy who helped me had me request some sort of update. to some config file.. and it went away for a few days. sudo dpkg-reconfigure -phigh xserver-xorg
My thoughts are.. 
Is it possible to load the code into the kernal or some thing? so that it will find and load the right stuff each time.. with no possible failure? 
Screen failure is very frustrating. 
When it fails.. there is just a black screen.. no sounds.. no way for me to solve the issue other than hold the button down till the system turns off. NOT great on the system. 
I am sure there is a solve. I am just not great enough with HOW this stuff works or what code to write. 

FWJ

---

### Post by caljohnsmith on 2009-02-05
Your fstab file confirms what we all ready knew, i.e. that you aren't yet using your home partition. How about opening your fstab:
```
gksudo gedit /etc/fstab
```
And add the following lines at the end:
```
# sda7 home partition:
/etc/sda7  /home  ext3  relatime,errors=remount-ro   0 0
```
Next do:
```
sudo mv /home /home_backup
sudo mkdir /home
sudo mount /dev/sda7 /home
sudo cp -ax /home_backup/rj /home
```
Then reboot, and please post the output of:
```
cat /etc/fstab
mount
du -sh /home/rj
```
And we can work from there.

---

### Post by forestwalkerjoe on 2009-02-05
Ohhh K... first i would rather like to know.. what did we just do? 

and second.. I'd like to suggest.. some thing within my plan was to find out if i made one too many divides of partition.. as in.. i dont need the extra area. I know root is must have. swap is required.. but HOME? can i absorb that back into the root or some thing? so that the whole area is larger? or what have you? 
i am not sure if the code commands you have had me do.. shows you what is really there. RAM, divided partitions.. CPU speed etc. but i must resize and reconfig to best options.. to make sure this booger works to the best possible. 

IF this is possible.. I'll be more careful to construct my next install with ROOT.. largest.. swap.. 2 times ram.. and not make another home file thing. i can go into MY COMPUTER and mount the Windows partition if i really must share files from there to here or DOES IT REQUIRE the home file for windows to see.. if i need to get a file FROM UBUNTU to windows? 

the family i was telling you about.. will be largely using the windows side of their future install.. for synching their ZUNE.. 4 cell phones..Games and sending things to printer.. and ONLY "IF" they are having trouble with printer iN ubuntu. 
my doing this lap top change.. shows ME how to do it the right way.. in the lap.. then my own desk top PC.. then onto theirs. 



Here is the requested OUTPUT:

rj@rj-laptop:~$ cat /etc/frstab
cat: /etc/frstab: No such file or directory
rj@rj-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=4e1de464-d3c7-4be0-9430-474ebfcc3f83 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e7b56a01-669f-4e83-bd41-bfa06eb0d841 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# sda7 home partition:
/etc/sda7 /home  ext3  relatime,errors+remount-ro 0 0
rj@rj-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rj)
rj@rj-laptop:~$ du -sh /home/rj
1.1G	/home/rj
rj@rj-laptop:~$

---

### Post by caljohnsmith on 2009-02-05
In your first post you said you wanted to resize your root, home, and swap partitions, so I assumed you wanted to keep your home partition since you didn't say anything about getting rid of the home partition. But now that you say you want to get rid of your home partition and instead have /home in your root directory, so you will have to undo the steps we did:
```
sudo umount /dev/sda7
gksudo gedit /etc/fstab
```
And remove the lines in fstab that you added to mount sda7 on /home. Did you run the command to copy your /home/rj directory to /home_backup/rj? If you didn't, that's good since you now don't want a home partition. If you did that command though, you will have to move /home_backup/rj back to your /home/rj directory. If you aren't sure, then please post:
```
ls -l /
```

---

### Post by forestwalkerjoe on 2009-02-05
i am sorry to have caused confusion. 
I will give into your suggestions here.. but it seemed i had created wrong sized partitions.. and wanted to see if the ones i had were all needed and hOW BIG. 
it seems to me that it might be a better use of space to put HOME.. IN ROOT.. and take swap down a notch. 
I think i started out talking about just resizing.. but the goal was to possibly remove home and integrate it.. but i am new enough to not be sure if that was even possible. 
Sorry for not being clear. 
I will do the suggested stuff you posted.. and then we can find out how to do the full home to root and resize thing. 

rj@rj-laptop:~$ sudo unmount /dev/sda7
[sudo] password for rj: 
sudo: unmount: command not found
rj@rj-laptop:~$ gksudo gedit /etc/fstab
rj@rj-laptop:~$ ls -l /
total 88
drwxr-xr-x   2 root root  4096 2009-01-29 23:27 bin
drwxr-xr-x   3 root root  4096 2009-01-30 00:03 boot
lrwxrwxrwx   1 root root    11 2009-01-27 16:28 cdrom -> media/cdrom
drwxr-xr-x  15 root root 13820 2009-02-05 14:11 dev
drwxr-xr-x 145 root root 12288 2009-02-05 15:04 etc
drwxr-xr-x   3 root root  4096 2009-01-27 16:48 home
lrwxrwxrwx   1 root root    33 2009-01-29 23:54 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx   1 root root    32 2009-01-27 16:56 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root 12288 2009-01-31 00:09 lib
drwx------   3 root root 16384 2009-01-27 16:28 lost+found
drwxr-xr-x   3 root root  4096 2009-02-05 12:46 media
drwxr-xr-x   2 root root  4096 2008-10-20 05:27 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 15:53 opt
dr-xr-xr-x 129 root root     0 2009-02-05 04:45 proc
drwxr-xr-x  24 root root  4096 2009-02-05 15:04 root
drwxr-xr-x   2 root root  4096 2009-01-30 20:59 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 15:53 srv
drwxr-xr-x  12 root root     0 2009-02-05 04:45 sys
drwxrwxrwt  17 root root  4096 2009-02-05 15:04 tmp
drwxr-xr-x  13 root root  4096 2009-02-03 18:07 usr
drwxr-xr-x  15 root root  4096 2008-10-29 16:12 var
lrwxrwxrwx   1 root root    30 2009-01-29 23:54 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx   1 root root    29 2009-01-27 16:56 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
rj@rj-laptop:~$ 

um.. thank you very much for being helpful. It seems like many of you in here are always working.. and i am not sure if THANK YOU comes up very often.. but honestly.. THANK YOU.

FWJ

---

### Post by caljohnsmith on 2009-02-07
OK, so you still have your home directory in your sda5 root partition, so what you could do is boot your Live CD, run gparted (System > Admin > Partition Editor), right-click the swap partition and select "swapoff", and delete the swap partition sda6 and also your home partition sda7. Then resize your sda5 main partition to go to almost the end of the drive, but leave 1 GB of space for your swap partition at the end of the drive. Recreate your swap partition with the 1 GB of space, and once gparted is done doing everything, next do:
```
sudo fdisk -lu
```
Find which is your new swap partition (probably be sda6 again), and then do:
```
sudo mkswap -U e7b56a01-669f-4e83-bd41-bfa06eb0d841 /dev/[COLOR="Blue"]sdaX[/COLOR]
```
Replace sdaX with whichever is the swap partition. Then reboot into your Ubuntu install, and post the output of:
```
sudo fdisk -lu
sudo blkid -c /dev/null
free
df -h
```
So I can check that the changes went OK.

---

### Post by forestwalkerjoe on 2009-02-10
Sorry i was not able to get back to our work yet. i had multiple issues.. one being the[ BLACK SCREEN ISSUE ]("http://ubuntuforums.org/showthread.php?t=1061015")resurfaced. 
I have had another person helping me try and resolve that. 
in the mean time i have a screen image of my G-Parted.. i have as of yet not moved on your last post request. 
there seems to be several issues that are involved.. not the least is HOME is not accessing correctly. 

some one is helping me to modify the Kernel.. i think.. to add the needed info for the system to load the Savage x driver and not run only in vesa.. which is much like Donkey Kong on this lap top. 

I am sorry this photo is so large.. i have not figured out how to Edit the Screen shot program here in Ubuntu.. once i am sure that what we do here will not mess up the other guys work.. and vice versa.. i'll proceed with your suggestions. i am sure i am nearing a break through on multiple issues. Screen being black.. partitions being correct again.. home mounting.. 3d working.. and a few others. thanks for being there for us when we need you. 

[http://i152.photobucket.com/albums/s196/forestwalkerjoe/Gparted.png]("http://i152.photobucket.com/albums/s196/forestwalkerjoe/Gparted.png")

i am not sure why i posted this image.. other than making sure we know exactly what i have already done.. and then .. they why.. so we can make sure its all the right stuff. if you want the ram and so forth.. so we can chose the right sizes.. i was able to find a code lshw.. thing that is very long.. but its listed in my last post in my name.. Ubuntu Black screen issue. 
thanks

---

### Post by caljohnsmith on 2009-02-11
Trying to use Ubuntu 8.10 with 256 MB of RAM is a bit of a strain for Ubuntu I think. Can you buy some more memory for that computer? That would really help, and memory is quite cheap these days. That might help your black screen issue, or even if it doesn't, it will only help to have adequate RAM on that computer.

---

### Post by forestwalkerjoe on 2009-02-11
I cant find the link right now for this.. but another person is also working with me.. largely on this Black screen issue.. apparently there is a flaw with Ubuntu , a Memory HOLE, that can be solved and also an issue with the board that doesn't signal the Brightness to turn onto high.. so therefore.. it doesn't chose to be bright by default. 
with that comes the issue that i think the line of code it is supposed to read is both IN the Kernel and then in the HOME file.. at least.. i think. HOME is not marked right.. and i don't know how to remake that.. with out messing every thing up.. and HOME Doesn't Mount on start up. 
AS to RAM. i am still not sure what kind of ram i am looking for.. i am not hard ware slick.. so I'll have to track that down.. and then.. i can do a search on Ebay to get that up and purchased. 
Have any idea what kind of ram this is off hand? this is a  Sony Viao PCG-xG39K system.

---

### Post by redroad55 on 2009-02-11
On your laptop power down > unplug all power > press power button and hold for 5 sec. > turn over laptop unscrew small cover > remove one of the sticks of memory by pulling straight placing your fingers in a way that you make no contact with anything that conducts electricity .. Take note of how the stick of memory is positioned (for example the side with the label is facing this way)so that when you put it back in the laptop you will return it in the same way .. Place the memory on a piece of paper with the label facing up record the information on the paper > return memory to the slot > put the cover back on .. List the imfo from the label back here ..Best to you

---

### Post by forestwalkerjoe on 2009-02-11
I did some research and the Viao page says that the max on ram for this model is 256. Yet.. when we lshw code.. it says can expand to 1 gig. 
I have hunted all over the house but the screw driver i used to use for glasses is gone. I need some thing that small to get these screws off on the back bottom. 
Also, when i did a search.. i found batteries Galore for this exact model.. last time i did a search for these.. 3 or 4 years back.. they wanted over 200 bucks for them. NOW they are about 30 bucks. This is a Two slot battery system.. so that is a Good thing. 
YET Ram.. seems to only be sold in Sticks of 128.. so far as i can find. prices vary from 10 bucks plus 6 bucks shipping Each to 15-22 bucks per stick.. and then 6 to 10 bucks shipping. 
I have only just come back to work after being laid off for two months.. so that Ram issue may have to wait a little while. 
Yeah yeah.. it really is that hard up for money right now. 

Are you saying that the 8 mgs video ram is not enough to do the kind of changes we need? or the 256 ram? At least for now? 

FWJ

---

### Post by redroad55 on 2009-02-11
The 8mb video is the aperture don't confuse that with system ram..If you choose to, even adding a 128mb stick in the empty slot would be a big help ..Post back

---

### Post by forestwalkerjoe on 2009-02-11
i still today have not had time to get the hardware open.. i "AM"
 looking into getting another ram stick. i was hoping to solve this black screen, no home mounting, resize the system set of issues. 
You know.. whats odd.. is i play games with the system to get it to load in Savage 3d.. i some times have to reboot over and over.. and play the fix X , etc.. or even go into promt and do the Dpkg xorg config thing.. but i get in.. after some time.. and then if its in Vesa.. i connect to the net and do the dpkg and reboot .. while its working.. and there is no black screen.. the system works SWEET> 
i can see how some more ram might help.. but all the things i wanted to work are working very tightly. 

as said in other post.. i have a DVD reader.. but not a burner on this lap top. So i can not just make a new ISO.. which i have never created a burn of an ISO before either.. not so sure how i would do that. even if i used the Desktop which i have rarely ever used the burner on it. 

FWJ

---

