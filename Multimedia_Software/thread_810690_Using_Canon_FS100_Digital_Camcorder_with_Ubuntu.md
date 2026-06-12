---
title: "Using Canon FS100 Digital Camcorder with Ubuntu"
date: 2008-05-28
forum: Multimedia Software
---

### Post by manthony121 on 2008-05-28
I just bought a Canon FS100 digital camcorder, and just finished figuring out how to get it to talk to my laptop running Ubuntu 7.04.  If anyone is interested, here is what I found out:

Ubuntu will automatically mount to camcorder after plugging it into the USB port, after you follow the prompts on the screen of the FS100.  Once mounted, you can find the directory where the video files live:

/media/CANON/SD_VIDEO/PRG001/

This directory will contain the individual video files, with names such as MOV001.MOD and MOV001.MOI.  The MOI files can be ignored (index files, perhaps?), and the MOD files are "mpg" files and can be safely renamed as such:

/media/CANON/SD_VIDEO/PRG001$ cp *.MOD /home/joe/homevideo
/media/CANON/SD_VIDEO/PRG001$ cd ~/homevideo
~/homevideo$ sudo umount /media/CANON
~/homevideo$ ls *.MOD | awk '{print("mv "$1" "$1)}' | sed 's/MOD/mpg/2' | /bin/sh

The awk/sed script is a handy little script that will rename a batch of files.  If you want to see what it will do without committing your changes, just run it without the trailing '| /bin/sh'.

Your video files will now be recognized as 'mpg' files, and can be viewed/edited with the usual applications.

---

### Post by Petermca on 2008-06-05
Hi,
I've just got an FS100 aswell and I found your post quite useful.  I'm not that good on Linux yet and I was wondering if you could explain what I am supposed to do with the script:
(
/media/CANON/SD_VIDEO/PRG001$ cp *.MOD /home/joe/homevideo
/media/CANON/SD_VIDEO/PRG001$ cd ~/homevideo
~/homevideo$ sudo umount /media/CANON
~/homevideo$ ls *.MOD | awk '{print("mv "$1" "$1)}' | sed 's/MOD/mpg/2' | /bin/sh
)
Ubuntu has detected the camcorder and everything just as you said but i'mn not sure what to do next...
Am I supposed to put this into the terminal?  And will this change the video files on my SD card to mpg?
Thanks Pete

---

### Post by manthony121 on 2008-06-05
> **Petermca said:**
> Hi,
I've just got an FS100 aswell and I found your post quite useful.  I'm not that good on Linux yet and I was wondering if you could explain what I am supposed to do with the script:
(
/media/CANON/SD_VIDEO/PRG001$ cp *.MOD /home/joe/homevideo
/media/CANON/SD_VIDEO/PRG001$ cd ~/homevideo
~/homevideo$ sudo umount /media/CANON
~/homevideo$ ls *.MOD | awk '{print("mv "$1" "$1)}' | sed 's/MOD/mpg/2' | /bin/sh
)
Ubuntu has detected the camcorder and everything just as you said but i'mn not sure what to do next...
Am I supposed to put this into the terminal?  And will this change the video files on my SD card to mpg?
Thanks Pete
The 4 line script is to be typed in a terminal window.  Everything to the left of the '$' character is the prompt that Linux will give; the part you type is to the right of the '$'.

Line 1:  Substitute the name of the directory where you wish to keep your video files for the string '/home/joe/homevideo'.  If you need to create a directory, you would type:  

....$ mkdir /home/joe/homevideo

Again, substitute your own username for 'joe'.

Line 2: $ cd <path-to-video-files-directory>

This changes your current working directory to the one where you just copied the MOD files.

Line 3: this 'unmounts' the camcorder from the computer.  Note that all the video files are still on the camera, unchanged.  You can delete them by hand if you wish.

Line 4: this renames all the MOD files to <filename>.mpg  You may have to add some spaces to the 'awk' command:  awk' { print("mv "$1"  "$1) }' to get it to work properly.  If you get an error about syntax, that is probably the problem.

Good luck!

Mark

---

### Post by manthony121 on 2008-06-05
> **manthony121 said:**
> The 4 line script is to be typed in a terminal window.  Everything to the left of the '$' character is the prompt that Linux will give; the part you type is to the right of the '$'.

Line 1:  Substitute the name of the directory where you wish to keep your video files for the string '/home/joe/homevideo'.  If you need to create a directory, you would type:  

....$ mkdir /home/joe/homevideo

Again, substitute your own username for 'joe'.

Line 2: $ cd <path-to-video-files-directory>

This changes your current working directory to the one where you just copied the MOD files.

Line 3: this 'unmounts' the camcorder from the computer.  Note that all the video files are still on the camera, unchanged.  You can delete them by hand if you wish.

Line 4: this renames all the MOD files to <filename>.mpg  You may have to add some spaces to the 'awk' command:  awk' { print("mv "$1"  "$1) }' to get it to work properly.  If you get an error about syntax, that is probably the problem.

Good luck!

Mark
One more thing: if you took any still photos with the camcorder, they will be in a separate directory, and can be read by any of the usual photo viewing applications.

---

### Post by Petermca on 2008-06-06
Hi again,
Could you recommend some good software for editing movies?  Or do you think its better to use the canon software (Dual boot with Vista)?

Thanks Pete

---

### Post by Petermca on 2008-06-06
PS: Thanks for all the help it worked!!

---

### Post by manthony121 on 2008-06-11
I haven't done much video editing (yet), but Kino seems to be the popular FOSS offering.  I'm not familiar with Windows based video editing, either, but I would think that the Linux tools should work well enough that you wouldn't have to suffer the humiliation of booting into Vista just to do that.

Glad to help out.

---

### Post by shiellb on 2008-06-25
Good evening all.  I also have just purchased a Canon FS100.  Would the script be the same for Hardy Heron 8.04?  Thanks.

---

### Post by manthony121 on 2008-06-28
> **shiellb said:**
> Good evening all.  I also have just purchased a Canon FS100.  Would the script be the same for Hardy Heron 8.04?  Thanks.

I have not tried 8.04, but the script should work for any version of any variant of Linux.  The commands used:  cd, cp, umount, sudo, ls, awk, and sed, are universally available.

Have fun with the FS100.  It's a sweet little device.

---

### Post by pwc on 2008-07-04
I just got the FS11(identical to FS10 and FS100 except for internal flash size). I was very happy to see manthony121´s post after I installed Kino and realized it needed firewall - thanks manthony121. However, when I connect with usb it will not mount, ubuntu 8.04 on my desktop does not see anything-nothing shows up. The camera shows in green: PC connect. I tried terminal command "mount usb" and got: 

 wayne@antec:~$ mount usb
[mntent]: line 16 in /etc/fstab is bad
mount: can't find usb in /etc/fstab or /etc/mtab

I'm stuck here, can anyone help. Hope I'm not to late on this thread.

Thanks

---

### Post by pwc on 2008-07-05
OK I'm still stuck, but here is a bit more info. When I do a "lsusb" command in terminal I get:

wayne@antec:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

But with the Canon pluged in to usb I get:

wayne@antec:~$ lsusb
Bus 002 Device 006: ID 04a9:319d Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
 
So somewhere in Ubuntu the device is recognized but does not show up on desktop. What do I need to do to fix this, anybody know! I meant "firewire" in last post not "firewall" guess my 68 year old computer(brain) just misfired.

Thanks to anyone that can help.

---

### Post by manthony121 on 2008-07-05
> **pwc said:**
> OK I'm still stuck, but here is a bit more info. When I do a "lsusb" command in terminal I get:

wayne@antec:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

But with the Canon pluged in to usb I get:

wayne@antec:~$ lsusb
Bus 002 Device 006: ID 04a9:319d Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
 
So somewhere in Ubuntu the device is recognized but does not show up on desktop. What do I need to do to fix this, anybody know! I meant "firewire" in last post not "firewall" guess my 68 year old computer(brain) just misfired.

Thanks to anyone that can help.

Look at the display screen on the camera.  It will be telling you to plug in the power charger.  I don't have my camera right here, so I can't give you a blow-by-blow, but the camera will tell you what you have to do to connect.  You don't have to do anything on the Ubuntu side at this point.  The fact that it is showing up under 'lsusb' means that the connection is good, but the camera wants a few things from you before it will start talking.  Follow the prompts, and it should be OK.

---

### Post by manthony121 on 2008-07-05
> **pwc said:**
> OK I'm still stuck, but here is a bit more info. When I do a "lsusb" command in terminal I get:

wayne@antec:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

But with the Canon pluged in to usb I get:

wayne@antec:~$ lsusb
Bus 002 Device 006: ID 04a9:319d Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
 
So somewhere in Ubuntu the device is recognized but does not show up on desktop. What do I need to do to fix this, anybody know! I meant "firewire" in last post not "firewall" guess my 68 year old computer(brain) just misfired.

Thanks to anyone that can help.
I compared your post with what comes up when I plug in the FS100.  When the camera says "PC Connect" in green, I have a Desktop icon labeled "CANON", and a mounted filesystem at "/media/CANON/"  If you aren't getting this, I'm not sure what to tell you.  Is the USB icon on the camera display flashing?  Mine flashes until the connection is established, then stays on without flashing.

---

### Post by Logical Dream on 2008-07-05
I have problem with my Sony Cyber SHot camera too 

idle@ubuntu:~$ lsusb
Bus 005 Device 006: ID 054c:0010 Sony Corp. DSC-S30/S70/S75/F505V/F505/FD92 Cybershot/Mavica Digital Camera
Bus 005 Device 004: ID 174f:a311  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000 

system can see It but ,Its not mounted ... There is no options on Camera 
I try ti install usbmount package but still nothing . 

Any idea ? 

tnx


EDIT :

> idle@ubuntu:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/idle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=idle)


After install gthumb I got :
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

---

### Post by Logical Dream on 2008-07-05
I found a Archive tread [http://ubuntuforums.org/archive/index.php/t-425940.html](http://ubuntuforums.org/archive/index.php/t-425940.html)
but when I opened /etc/udev/rules.d/45-libgphoto2.rules It was empty . 
I added this : 
# udev rules file for libgphoto2 devices (udev < 0.9
#
#BUS!=&#8221;usb*&#8221;, GOTO=&#8221;libgphoto2_rules_end&#8221;
SUBSYSTEM!=&#8221;usb_device&#8221;, GOTO=&#8221;libgphoto2_rules_end&#8221;
ACTION!=&#8221;add&#8221;, GOTO=&#8221;libgphoto2_rules_end&#8221;

Now, restart udev:

sudo /etc/init.d/udev restart

,but again nothing :/

---

### Post by pwc on 2008-07-05
Thanks manthony121 for your response, everything is as you describe except for the CANON icon on Desktop and no mounted file system at "/media/CANON". However with terminal command: 

sudo mkdir /media/CANON
sudo mount /dev/sdc1 /media/CANON 

I do get the mounted file system in /media/CANON. 
The "sdc1" comes from the info in terminal command: "sudo fdisk -l"

Now this genius does not come from me, I found it at this thread:
[http://ubuntuforums.org/showthread.php?t=846283&highlight=mount+usb](http://ubuntuforums.org/showthread.php?t=846283&highlight=mount+usb)

This is as for as I've got so far but I'm sure by following that thread and combining it with manthony121's first post I"ll be able to set it up to plug it in and get the media files like you normally see with usb devices.
And Logical Dream this should solve your problem also.
I&#314;l post back when I finish, probably tomorrow.

Thanks again,
pwc

---

### Post by manthony121 on 2008-07-05
> **pwc said:**
> Thanks manthony121 for your response, everything is as you describe except for the CANON icon on Desktop and no mounted file system at "/media/CANON". However with terminal command: 

sudo mkdir /media/CANON
sudo mount /dev/sdc1 /media/CANON 

I do get the mounted file system in /media/CANON. 
The "sdc1" comes from the info in terminal command: "sudo fdisk -l"

Now this genius does not come from me, I found it at this thread:
[http://ubuntuforums.org/showthread.php?t=846283&highlight=mount+usb](http://ubuntuforums.org/showthread.php?t=846283&highlight=mount+usb)

This is as for as I've got so far but I'm sure by following that thread and combining it with manthony121's first post I"ll be able to set it up to plug it in and get the media files like you normally see with usb devices.
And Logical Dream this should solve your problem also.
I&#314;l post back when I finish, probably tomorrow.

Thanks again,
pwc
It sounds like the firmware in your camera might be a little different from that in the FS100.  Once you get the camera mounted, however, you should be OK.  Best of luck.

---

### Post by Logical Dream on 2008-07-06
ok PWC Ill wait for that as this didnt help till now .

---

### Post by pwc on 2008-07-07
OK, I finally got some time to play with this again. First I was wrong about the mounted files in /media/CANON, that turned out to be files in sdc1(3rd hd). Sorry about that but I still think there's hope, here is what I did.
With the Canon FS11 connected to pc and on, I do terminal command:

wayne@antec:~$ sudo fdisk -l

I could post the full results here but I'm just showing what shows up in addition to what would show if Canon is not connected. It saves lots of space and is of no interest.

Disk /dev/sde: 16.4 GB, 16441147392 bytes
255 heads, 63 sectors/track, 1998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        1999    16051712    c  W95 FAT32 (LBA)

This has got to be the video camera, it has a 16 GB internal disk and I'm sure it's formatted to FAT32. So Ubuntu sees it but doesn't mount.

Now I do the command: 

wayne@antec:~$ sudo mount /dev/sde1 /media/CANON
mount: special device /dev/sde1 does not exist
sudo

I then try:  wayne@antec:~$ sudo mount /dev/sde1
[mntent]: line 16 in /etc/fstab is bad
mount: can't find /dev/sde1 in /etc/fstab or /etc/mtab
 
So that's where I'm at now and manthony121 if I could see your /etc/fstab file it might help. I also think you're right about the firmware being different. And that makes me think I should try my Canon with the 8 GB flash drive I bought with the camera, it might see and mount  like yours. I'll do it later, after a couple hrs of this I'm frustrated and brain dead.

Later, pwc

---

### Post by manthony121 on 2008-07-07
I'm not sure what to say, if "/dev/sde" shows up on "fdisk -l", but can't be found when you issue a mount command.  Have you tried mounting without the partition number?  "sudo mount /dev/sde /media/CANON"?

I don't think the fstab listing matters if the mount command can't find the device.

---

### Post by shiellb on 2008-07-07
Thanks for the help.  I've just returned from a 7 day canoe trip in northern Ontario.  Shiellb

---

### Post by pwc on 2008-07-08
I did try that manthony121 and at one point the CANON icon actually showed up on Desktop, however I never could get to the video files and after 2-3 hrs of trying I gave up out of frustration. My last post was just a summary of what I had done that is repeatable. And after that my computer broke(not because of what I did on this problem), But here's an interesting bit of info, I dug out my old 5-6 yr old computer with Suse 10.1 on it(that's a late 2005-early 2006 version of Suse) which I haven't used in 2 yrs. After using it for a day or so I was curios if it would see the Canon. Plugged it in, turned it on, and right on Desktop was the sd_video folder! Opened it and found prg001/mov001.mod. I copied the mov001.mod file to Desktop, unmounted and unplugged Canon. Then opened mod file with MPlayer and watched 5 min video I had made. All that in just few minutes. So now we know that linux can recognize the Canon FS11 it's just something in Ubuntu 8.04 that won't allow it. I think now it's probably the etc/fstab file that needs changing, thats why I asked to see yours. 
It will be at least a couple of weeks before I get back to Ubuntu since the computer will be in shop for a week or so and then I'm going away for about a week. I will check back in to this tread and thanks again for your first post.

pwc

---

### Post by manthony121 on 2008-08-05
As I was going thru the videos piling up on my hard disk, I realized that the storage method described at the beginning of this thread does not preserve the date when the recording was made.  It only records the date when the files were moved off the SD card.  Presumably, the date/time info is stored in the "MOI" files that accompany each "MOD" file.

Also, I have found that you cannot burn these MOD/mpg files to a dvd using the "tovid" suite of tools.  Even though "tovid" recognizes them as mpg files, they need to be re-encoded before they can be processed further.  If you do not do this, everything goes OK until you get to the "makedvd -burn fname.xml" step.  Then you get a lot of error messages.

THEREFORE:  I am amending the original command line for saving the video files as follows:

$cp -p *.MOD /home/joe/homevideo

Note that the "-p" switch has been added, to preserve original file timestamp.

When it comes time to put movie files on DVD, the different mpg files can be merged with a simple "cat":

$cat MOV001.mpg MOV002.mpg MOV003.mpg > filename.mpg

To re-encode for use with "tovid":

$tovid -force -in filename.mpg -out filenameX

Note that you must use the "-force" switch to force the re-encoding, otherwise tovid will just create a link to the original file, and dvd authoring will fail, as described above.

Hope this helps.

---

### Post by kah00na on 2008-08-22
I have had good luck just pulling the card out of the FS100 and putting it into my card reader.

---

### Post by flymw on 2008-09-10
regarding mounting problems, did you try connecting in **playback mode**?

my FS100 did not mount in Ubuntu Hardy when I connected it via USB because I was in recording mode

only when I changed to playback mode the FS100 immediately prompted me for connection type and everything worked fine

hope this is not too basic, just thought I'd mention since I didn't read about it anywhere...

---

### Post by bayvista on 2009-02-19
Thanks for this great Howto. Just tried it with Intrepid 8.10 and it works fine. A word of caution. If you find it taking a long time to dowmload the video files, make sure that you have connected to a USB2.0 port. I don't know how to check this. My download took forever so I bought a USB2 card and after that, it went like a rocket.

I can recommend Kino for editing. I have used it for a year now and find it great. However, you cannot capture from a Memory Card, only from Firewire.

I am going to check this camera out with Wine to see if it works with the supplied Windows software. I'll report back later.

---

### Post by griztown on 2009-03-09
Has anyone tried passing their FS100 into a Virtual Machine running WindowsXP?  When I attempt to do this it only recognizes the removable drive but not the camera.

---

### Post by bayvista on 2009-03-12
Can't get this working under Wine. However, as Ubuntu recognises the FS100 as a USB Stick, it's easy to copy the files to your Home Folder. Why do you need Windows?

---

### Post by ShouriChatterjee on 2009-06-19
I am on Jaunty 9.04. The Canon FS-11 works out of the box. I plugged it in through USB, the camera asked me to plug in a power supply cord, and it mounted on my Desktop as CANON. The files were in /media/CANON/ as reported for the FS-100.

I didn't have to do any tweaking of the fstab on Jaunty.

---

### Post by dmelliot on 2009-11-17
You should be able to do the renaming a bit easier using the rename command.

Something like this should work:
rename 's/MOD/mpg/' *.MOD

Add the -n switch if you want to take (n)o action, it will just give you a preview of the rename first.

---

### Post by ThomasNovin on 2010-03-11
Hasn't anyone else seen the strange filenames? I have the Canon Legria FS36 (movies stored on on-board flash).

. I will probably return it because A) Movies are named in some strange fashion, not just MOV028 MOV029 MOV030 etc. but MOV028 MOV02A MOV02B MOV02C MOV030. Don't really see the logic behind the filenames.

B) The cameras filesystem is mounted read-only and I cannot change that (AFAIK). So I have to erase the downloaded movies from the camera from the camera menu. I have tried 'sudo mount /dev/sdc1 -o remount,rw' but that didn't work.

---

### Post by manthony121 on 2010-03-11
The file names use base-16 numbering: ...028 029 02A 02B 02C 02D 02E 02F 030...

If you delete any clips from the camera menu, you will have missing numbers.

Don't know about the r/o mounting issue.

---

### Post by ThomasNovin on 2010-03-12
> **manthony121 said:**
> The file names use base-16 numbering: ...028 029 02A 02B 02C 02D 02E 02F 030...

If you delete any clips from the camera menu, you will have missing numbers.

Don't know about the r/o mounting issue.

Ah of course they are.. then I could easily do a script to rename them. 

What I can do from the camera menu is to complete wipe the memory. Menu > Memory Oper. > Initialize > Built-in Mem > Initialize "Quickly erases all data files in the built-in memory".

Probably the numbering will continue at the last position but I will have to check that.

Edit: Checked right away and nope, the numbering will start from MOV001 again.

---

### Post by quinnten83 on 2010-04-04
I just bought a FS100 second hand, and i'm finding that the video looks very interlaced when played back on the computer.
Also the 16:9 format is not automatically recognized in mediaplayer.
I read on another thread that I should leave them like this if I plan to make video DVD's, but is there anything I can do to make playback on the computer nicer looking?
also, if I decide to use a video editor in linux will it automatically correct these issues if I export to a different format, like .AVI?
Please bear with me here, I am not a videophile, I don't really know what I am doing here.

---

### Post by manthony121 on 2010-04-06
> **quinnten83 said:**
> I just bought a FS100 second hand, and i'm finding that the video looks very interlaced when played back on the computer.
Also the 16:9 format is not automatically recognized in mediaplayer.
I read on another thread that I should leave them like this if I plan to make video DVD's, but is there anything I can do to make playback on the computer nicer looking?
also, if I decide to use a video editor in linux will it automatically correct these issues if I export to a different format, like .AVI?
Please bear with me here, I am not a videophile, I don't really know what I am doing here.

Many video players, such as vlc, allow you to chose a de-interlace method on playback, and will also let you select an aspect ratio, if it is not correctly recognized.

If you are going to copy to a different format (transcoding), there are several ways to "deinterlace" the video stream, and different transcoding software will have different choices.  As with many things Linux, you can learn an awful lot about how video is encoded and stored on computer by digging into these programs.  Most will have reasonable defaults if you just want to get the job done.

---

