---
title: "Hardy Heron upgrade + dvd playback issues"
date: 2008-04-25
forum: Multimedia Software
---

### Post by odin79 on 2008-04-25
Hi all, I'm starting a new thread as I have spent countless hours searching the forum. My problem is that I can't play DVD's anymore after upgrading from Gutsy to Hardy. All my DVD's worked fine in Gutsy (started automagicaly). They also play in WinXP (I have dual boot).

Now, before you start telling me to install liblibdvdcss2, libdvdread3 libxine1-ffmpeg and so on; I have gone through ALL the stickys with no luck so far.

CD's and normal data DVD's open fine when inserted, comercial DVD's do not.

When I try to play a dvd wih gxine I get the following errors:
-The xine engine failed to start, no input plugin was found.
-read error from /dev/dvd

I thought that maybe it had something to do with my region so I installed regionset, but just got this message:

"regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive."

Totem gives the following message:
"Totem was not able to this disc: Please check that a disc is present in the drive."

VLC gives the following:

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/scd0 with libdvdcss.
libdvdread: Can't open /dev/scd0 for reading
libdvdnav: vm: faild to open/read the DVD
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/scd0 is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block 0 from disc
[00000307] cdda access error: cannot read sector 0
[00000307] cdda access error: could not read block 1 from disc
[00000307] cdda access error: cannot read sector 1
[00000307] cdda access error: could not read block 2 from disc
[00000307] cdda access error: cannot read sector 2
[00000307] cdda access error: could not read block 3 from disc
[00000307] cdda access error: cannot read sector 3
[00000307] cdda access error: could not read block 4 from disc
[00000307] cdda access error: cannot read sector 4

Any help on how to resovle would be greatly appreciated. I'm starting to loose faith here.

Thank you!

EDIT: When I tried installing libdvdnav3 I got an error saying "E: Couldn't find package libdvdnav3"

---

### Post by cor2y on 2008-04-25
You will have to compile or use the medibuntu repos to get libdvdnav.
Its not in the official repos.

---

### Post by odin79 on 2008-04-25
I have libdvdnav4 installed. The reason I tried with libdvdnav3 was that is has been mentioned in the forums. Still no luck.

---

### Post by mc4man on 2008-04-25
Your region would have been set along time ago in xp, that's not an issue. Do dvds mount ?, ie. an icon shows up on desktop.

Edit: forget that libdvdnav3 thing

---

### Post by odin79 on 2008-04-26
My normal data-dvd's mount fine, as well as blank dvd's (icon shows up). Same goes for cd's. But when I try to mount commercial dvd's (movies and games): Nothing. Not one of my movies have will play, and I tried with several.

It obviously has something to do with encoding, missing codecs and such, but I'm at at a loss at which codecs I might have missed. Seems like I have tried them all. Could it be some hidden setting somewhere, or some changes that Hardy did to my dvd-driver?

Halp and thanks for your help so far guys! =)

---

### Post by omicrondelta on 2008-04-26
Re-build your opensource dvd-player of choice and link to libdvdcss... Debian packages are not... End of thread...



Sorry if I'm a little cryptic, but the boys and girls behind everything have been for me... If I can do it... You can DO Eeet!!! I just Ogle my DVDs... 




So Say We All...

---

### Post by odin79 on 2008-04-26
I purged vlc and libdvdcss2 and reinstalled. Opened vlc from terminal and tried to play dvd:

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: BSG_S2_Disc04
libdvdnav: DVD Serial Number: 34d45d20
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/******/.dvdnav/BSG_S2_Disc04.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/scd0 is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block 0 from disc
[00000307] cdda access error: cannot read sector 0
[00000307] cdda access error: could not read block 1 from disc
[00000307] cdda access error: cannot read sector 1
[00000307] cdda access error: could not read block 2 from disc
[00000307] cdda access error: cannot read sector 2
[00000307] cdda access error: could not read block 3 from disc
[00000307] cdda access error: cannot read sector 3

As you can see it seems like vlc is using libdvdcss, but that it still can't access the dvd.

EDIT: Would be great if this could be fixed as it now is the only thing making me hold on to Windows XP. Also, I really do not want to make a fresh install as I have spent enougt time on this problem already.

Thanks!

---

### Post by omicrondelta on 2008-04-26
> **odin79 said:**
> I purged vlc and libdvdcss2 and reinstalled. Opened vlc from terminal and tried to play dvd:

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: BSG_S2_Disc04
libdvdnav: DVD Serial Number: 34d45d20
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/******/.dvdnav/BSG_S2_Disc04.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/scd0 is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block 0 from disc
[00000307] cdda access error: cannot read sector 0
[00000307] cdda access error: could not read block 1 from disc
[00000307] cdda access error: cannot read sector 1
[00000307] cdda access error: could not read block 2 from disc
[00000307] cdda access error: cannot read sector 2
[00000307] cdda access error: could not read block 3 from disc
[00000307] cdda access error: cannot read sector 3

As you can see it seems like vlc is using libdvdcss, but that it still can't access the dvd.

EDIT: Would be great if this could be fixed as it now is the only thing making me hold on to Windows XP. Also, I really do not want to make a fresh install as I have spent enougt time on this problem already.

Thanks!

Did you build your VLC or apt-get it?  I see that the CSS is in there... Just Ogle it buddy... Do I have to write a tutorial?... Can I get a "So Say We All"?

---

### Post by lancern on 2008-04-26
Well I had not tried to play a dvd yet so after reading your post..I gave it a try..and it did not work for me either..when I inserted the dvd totem opened up and said "Location not found"..then In totem I click on the movie drop down and it shows the movie name and I click it and get this "could not read from resource"..also tried VLC and MPlayer..with no luck..So now you dont feel so alone:)
so far thats the only prob I have had..But as far as giving up windows..I will prob always use it for gaming..

---

### Post by omicrondelta on 2008-04-26
One thing is, is you have to realize that the opensource community is diverse, and your hard-drive has lots of gigabytes free... There's no all-in-one media solution yet... Ogle for bought DVDs and build it yourself... Just like daddy always said... You feel better about it when you do it yourself...


Not like I'm bragging or anything... I'm 1/2 drunk... 6 pack in the pail... But I've been a Linux user (and nuttin' but... well maybe Windows for 2 and OSX for under 1) for 11 years... You can do Eeet... I'm just a Class 1 truck-driving B.Sc. Computing Science dropout by trade...

edit:

I edit my posts on a regular basis... Re-proofin' all da time... Cheers to being a drunk red-neck Linux user... Woo Hoo!!! I got sound again bee-yatch!!!




SO SAY WE ALL...

p.s. Is it just me... Or does the interface on Firefox3 suck... I miss the interface of Firefox2, but not the malloc() leaks...

---

### Post by lancern on 2008-04-26
> **omicrondelta said:**
> Do I have to write a tutorial?

Please do :!:

Edit: 
Better yet just make us a .deb that will work so we dont hurt our feble brains..

---

### Post by odin79 on 2008-04-26
Thanks lancern, those are my exact error messages. As I already said all was well in Gutsy.

Omnicron (or somebody else); if you could give us some instructions about how to fix it woulb be great!! =)

---

### Post by dajs on 2008-04-26
no dvd for me either, nothing happens when I insert a dvd in my dvd drive!

---

### Post by lancern on 2008-04-26
[http://www.jbkempf.com/blog/post/2008/03/28/Build-VLC-media-player-under-Ubuntu-Hardy-804](http://www.jbkempf.com/blog/post/2008/03/28/Build-VLC-media-player-under-Ubuntu-Hardy-804)

You could try this..Im just to lazy to try it my self :lolflag:

---

### Post by bwallum on 2008-04-26
Are you running libdvdcss2 from the medibuntu repos?

You can tell by looking at System>Administration>Software Sources:Third Party Software.

If you don't have it then add the repository by opening a terminal and entering this code:-

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
then the add the key
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Using System>Administration>Synaptic Package Manager, search and then add libdvdcss2

---

### Post by dajs on 2008-04-26
yes, I installed it already
the dvd just won't mount
it worked on my last ubuntu... so it must work

---

### Post by omicrondelta on 2008-04-26
> **odin79 said:**
> Thanks lancern, those are my exact error messages. As I already said all was well in Gutsy.

Omnicron (or somebody else); if you could give us some instructions about how to fix it woulb be great!! =)

When I sober up and read everything again in the morning, I'll be happy to make the world a better place... Cheers everyone... g'night, g'day, and gd'afteroon...

---

### Post by omicrondelta on 2008-04-26
You'll love the warm fuzzy feeling you get when you make it work the way you want...

---

### Post by omicrondelta on 2008-04-26
DVD::Rip is a good place to start... Then Ogle... I've never had bought DVDs working under any other apps on Linux...




gonna fire up the XP partition (sick of VMWare... dual-bootin this bitch laptop now) and write a few lines of code for my Parallax microcontroller (frak off gputils) project...


I be drunk and gonna crash, and bow my head to the pros like the newb that I am... G'night and cheers...

---

### Post by bwallum on 2008-04-26
In vlc player go to preferences. Press reset all. Check in 'input/codecs' that the DVD device points to /dev/scd0 (or, if you have a different setting to whatever your dvd drive has been mounted to). Apply and navigate back to vlc player main screen. When you do File>Open Disc it should point to the same device name. Does it?

---

### Post by odin79 on 2008-04-26
That's right, "device name" points to /dev/scd0. But I still get the [00000306] cdda access error: could not read block from disc
and
[00000306] cdda access error: cannot read sector 

errors.

Hum. :-/

---

### Post by lancern on 2008-04-26
[http://www.jbkempf.com/blog/post/2008/03/28/Build-VLC-media-player-under-Ubuntu-Hardy-804](http://www.jbkempf.com/blog/post/2008/03/28/Build-VLC-media-player-under-Ubuntu-Hardy-804)

well I tried the guide here to make VLC..
followed everything to a T..and every step worked great accept for the very last step "make"..said no make file found...I dont feel so fuzzy...

---

### Post by gwpritch on 2008-04-26
Try this...
Through Add/Remove install Ubuntu Restricted Extras package.
Fixed what sounds like the same problem for me.
Good Luck.

---

### Post by odin79 on 2008-04-26
Already have it. Acctually I have just about every codec installed that is possible to find (maybe that's the problem, who knows). Glad it worked for you though.

---

### Post by lancern on 2008-04-26
all is working for me now..I installed other media players and the one called Kaffeine told me it could not find libdvdcss..(thank you Kaffeine)..tried to install it in terminal and it said no install packages found..Had to enable some 3rd party repos in Synaptic..and then was able to install it..I rebooted and now VLC Totem and Mplayer can play dvd movies  :guitar:

You dont need to build your own VLC to play dvds..I just wana be a user not a developer :lolflag:

---

### Post by bwallum on 2008-04-26
If you are not attached to it remove gxine. It will clash with gstreamer.

Open /etc/fstab, copy and paste the contents to the forum.

---

### Post by lancern on 2008-04-26
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2bcac765-95fa-45cc-bc72-d663ffc85a5b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=EA9488619488325D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=CED5-3EC2  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=e145129b-1b2e-4262-83ce-49e3373516de none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

yes I will uninstall those kde apps they really clash with the gnome theme :p

---

### Post by bwallum on 2008-04-26
Are you running a sata dvd drive or an pata dvd drive?

---

### Post by dajs on 2008-04-26
I got it too work too :)
I purged everything and installed only kaffein and the dvd stuff. Now it also works on VLC.
No idea why it didn't work the first time.

---

### Post by bwallum on 2008-04-26
Try a # before your /dev/scd0 line, save and reboot. Then try vlc and a dvd again. Good luck.

---

### Post by odin79 on 2008-04-26
The contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=a6acc5b8-96b1-4f7e-a0ae-25455e1b6866 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=1941799a-5204-4330-a25b-5c1980c14f08 /home           ext3    defaults        0       2
# /dev/sda1
UUID=02D4BE49D4BE3EAB /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=BAACD13DACD0F53B /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=6038A8D238A8A90C /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=b21c73c6-54e5-42f5-aa73-712a088ecf2c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


I purged gkine as suggested and installed kaffeine. When I started kaffeine it said something about DMA modes. I'm using a SATA DVD+RW.

Still can't play. Halp =(

EDIT:

I changed the line
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

to

/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

(in compliance with the fstab file on the page 3. But to no avail. Is it a DMA problem maybe?

---

### Post by odin79 on 2008-04-26
I found a hint in another post concerning DMA, so I ran the command:

sudo hdparm -I /dev/scd0

Here is the output, I'm not quite sure what it means though.

/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       Optiarc DVD RW AD-7170A                 
	Serial Number:      
	Firmware Revision:  1.02    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(cannot be disabled)
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
	CBLID- above Vih
	Device num = 1

---

### Post by lancern on 2008-04-26
hmm..did kaffeine say anything about libdvdcss and did you check if its installed?..
I also got the msg in kaffeine about the DMA mode..I did nothing to fix that and it still worked for me..

---

### Post by odin79 on 2008-04-26
Sorry I did not see any messages about libdvdcss2.

For the record, I have checked it several times already. Just did an apt-get:

libdvdcss2 is already the newest version.

What should my fstab say?
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0 ?

Is there some other settings I need to set? Is /dev/scd0 what I should refer to as my DVD? Sorry if questions are stupid, but it has always worked before.

EDIT: I just noticed something when using vlc:

libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: BSG_S2_Disc04
libdvdnav: DVD Serial Number: 34d45d20
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/richard/.dvdnav/BSG_S2_Disc04.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/scd0 is empty, aborting

See, it recognizes the dvd-title, but it also says that "file /dev/scd0 is empty". How can that be???

---

### Post by lancern on 2008-04-26
well that drunk guy omicrondelta was saying somthing about ogle ..its a dvd player..I had also installed that..maybe it some how magically made it all work..hey its worth a try :)

---

### Post by mc4man on 2008-04-26
Just as a longshot try deleting the folders in .dvdcss
What is the name of title - seems like tv series (bsg ? ) I'll ck. if any issues with structure protection
to ck. for drive and links 
```
sudo lshw -C disk
```

---

### Post by odin79 on 2008-04-26
.dvdcss in my /home/ folder? Already did that.

The result from lshw:

 *-cdrom                 
       description: DVD-RAM writer
       product: DVD RW AD-7170A
       vendor: Optiarc
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.02
       serial: [Optiarc DVD RW AD-7170A 1.02 Jul14,2006
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
  *-disk:0
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANK2233843
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=1cde1cdd
  *-disk:1
       description: ATA Disk
       product: WDC WD4000AAKS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 12.0
       serial: WD-WCAPW2502426
       size: 372GiB (400GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ef41e167

BSG is battlestar galactica, great series. But the problem is with all my commercial dvd's. Also it seems like a widespread problem.

Lancern: I will give ogle a shot, but I don't see the point of installing a gagazillion media players. :-/

Anyways, I'm calling in for the night now, will continue tomorrow. Thanks all! =)

---

### Post by mc4man on 2008-04-26
another possibility
[http://ubuntuforums.org/showthread.php?t=747326](http://ubuntuforums.org/showthread.php?t=747326)  post 4
note place dvd in drive first

---

### Post by odin79 on 2008-04-26
Tried your method:

"Could not open location; you might not have permission to open the file."

Ogle didn't work.

---

### Post by mc4man on 2008-04-26
Have you tried running vlc from the cli ? ie. vlc /dev/cdrom1 or vlc /dev/cdrom  , vlc /dev/dvd1, vlc /dev/dvd ,ect Try all possible entries
have you rebooted yet ?

---

### Post by snerfu on 2008-04-27
I just had a similar problem and found this thread.  I think someone mentioned it earlier but I thought I would post my findings.  Since I got my dvd working, I don't have the error messages I was getting but it would find libdvdcss just fine and report an error trying to crack the key for the main title on the disc.  I tried the recommendation to set the environment variable for libdvdcss with no luck.  I ended up trying out that regionset utility, and it showed my drive to have no region set.  So I used that to set it to region 1.  Initially I still couldn't play a dvd so I gave it a reboot, and when it came back I was able to play my dvds just fine with both totem and vlc.  I can not say for sure it was one of the other things I did that actually fixed it before I did the reboot.  Just thought I would share that bit of information with everyone.

I definitely didn't have this problem back in gutsy. Could something have changed with libdvdcss or another package between the two that forced applications to suddenly care about region encoding where they did not before?

---

### Post by mc4man on 2008-04-27
> Could something have changed with libdvdcss or another package between the two that forced applications to suddenly care about region encoding where they did not before?Probably just luck of the draw  for you, having a region set is pretty basic to consistent playback, certainly if rce is present I believe.
@odin79 - wouldn't hurt to recheck region, this time have dvd in drive (mounted), if you haven't already

---

### Post by odin79 on 2008-04-27
I just rebooted and tried your commands, here are the results:

Commands:
vlc /dev/dvd
vlc /dev/cdrom

:~$vlc /dev/dvd
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Can't stat /dev/dvd
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000292] main input error: no suitable access module for `/dev/dvd'
[00000283] main playlist: nothing to play

----
Commands:
vlc /dev/dvd1 
vlc /dev/cdrom1

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/richard/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/dvd1 is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block 0 from disc

---

When using dvd1 and cdrom1 the disc starts to spin (followed by errors, but when using dvd and cdrom, it sits there idle (but without the 'cdda access error: could not read block 0 from disc' errors). This might indicate that cdrom1 and dvd1 are correct, yes?

mc4man, as I mention already my region 2 dvd's work fine in Windows XP, but I will try regionset, it's worth a shot. :-)

---

### Post by odin79 on 2008-04-27
Hum when I run regionset I get the following:

sudo mount cdrom0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0

My media catalog contains the following entries

ls /media/
cdrom  cdrom0  floppy  floppy0  sda1  sda5  sda6

I might be wrong, but shouldn't dvd also be in there? I also tried "sudo mount cdrom0", but with the same results.

EDIT: Could one of you with working dvd's post me the contents of your /etc/fstab, as well as telling me which codecs and media players you have installed? Some other essential stuff that I'm missing?

Gonna boot up Windows now to check the dvd there, just to be sure.

---

### Post by bwallum on 2008-04-27
Did you have a go at commenting out the dvd drive entry in fstab? Just put a # in front of the line. Save and reboot. You do not need to specify your dvd drive in fstab. fstab is used to auto mount drives at boot, that is your hard drives normally.

---

### Post by bwallum on 2008-04-27
This is my fstab. I have a pata dvd drive. I have inserted an entry for a dvd drive just to mimic your fstab. It is commented out with a #. I can run dvds. It mounts when media (a disk) is put in the drive. I have subsequently deleted the /dev/hda line. I suggest commenting it out so you can see what happens to your system first before deletion.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=57087ac6-33b7-4eb5-ad7b-0cb7c7f8e921 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=aa03ddee-0768-4313-a895-338d56af11bc none            swap    sw              0       0
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by turnpin on 2008-04-27
I had a problem with not being able to detect movie DVDs after a fresh Hardy install.  Installing libdvdcss2 from the medibuntu repository seemed to work for me.

I followed the instructions from [here]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by odin79 on 2008-04-27
Ok I commented out the line:
#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

But it didn't seem to make any difference. I also checked my dvd in Windows: Worked fine.

I tried to start "Das Boot" with vlc:

:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 256C80B7
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/richard/.dvdnav/DVD_VIDEO.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/scd0 is empty, aborting
[00000304] main private error: cannot pre fill buffer
[00000307] cdda access error: could not read block 0 from disc
....... and so on

It can't read the blocks or something.

<sigh> I'm starting to loose faith here.

---

### Post by mc4man on 2008-04-27
> I'm starting to loose faith here.
I don't blame you, enabling dvd playback normally is quite trival. i think there is some miscommunication as to whether dvds are mounting. The results of vlc /dev/dvd are what you expect from either trying to access a device with no media or as in your case a device that doesn't exist. On the other hand vlc /dev/dvd1 is the proper command for you, the error reflects finding unmounted media and no udf fs. For instance If I put a cd in drive and ran 
```
doug@doug-desktop:~$ vlc /dev/dvd
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread patched to play DVDs with DVD-Movie-Protect
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/doug/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000295] vcd access error: invalid entry points number
[00000281] main playlist: nothing to play
```
almost the same
put a dvd in the drive and either run  dmesg | tail or ck. in /etc/mtab - should show whether media is mounting

did you do a fresh install of hardy or an upgrade from gutsy ?

---

### Post by odin79 on 2008-04-27
I did an upgrade from Gutsy. All other aspects of Hardy is ok (even wireless which was screwing around for a while).

I did take a look at this post: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) . especially point 9 under troubleshooting:

"9. Are you having trouble with new DVDs? Please refer to this link and concentrate on the solution for VLC."

The link is [http://tobias.rautenkranz.ch/libdvdread_ifo.html](http://tobias.rautenkranz.ch/libdvdread_ifo.html) .

But I don't know how to apply the patch they refer to there. Any ideas? It seems like the problem I have.

Quote: 
"The correct offset, i.e. the file, can be found in the IFO files bypassing the wrong offsets in the UDF file system"

---

### Post by odin79 on 2008-04-27
Here is the result from dmesg | tail:

------

[ 1088.633155] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1088.633159] end_request: I/O error, dev sr0, sector 64
[ 1088.672736] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1088.672740] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1088.672743] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1088.672747] end_request: I/O error, dev sr0, sector 64
[ 1088.712444] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1088.712449] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1088.712451] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1088.712456] end_request: I/O error, dev sr0, sector 64
richard@avalon:~$ dmesg | tail
[ 1088.633155] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1088.633159] end_request: I/O error, dev sr0, sector 64
[ 1088.672736] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1088.672740] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1088.672743] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1088.672747] end_request: I/O error, dev sr0, sector 64
[ 1088.712444] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1088.712449] sr 0:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 1088.712451] sr 0:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1088.712456] end_request: I/O error, dev sr0, sector 64

---

Note: Would it help reinstalling Hardy? I really dont wanna do it unless I'm sure it will help!

---

### Post by mc4man on 2008-04-27
If the dvds aren't mounting (udf fs) then obviously no playback can occur.If no help in terms of fixing this is presented (I don't know enough of inner workings to help) I'd do a fresh install. my guess is you did an upgrade from gutsy or something odd occured from fresh. Having the drive at /dev/hda seems suspect If you do a fresh install after updating ect. I'd go right into enabling dvd playback and get it over
a quick method is to install 
libdvdcss2
vlc - that's all you need for vlc (installing vlc fills in needed libs )
totem-xine
gsteamer0.10-plugins-ugly (0.10.7-3)
that's all you'll need additionally for totem

edit; when I was testing stuff for vlc autoplay I must have done 5 or so fresh installs here's post on quickly enabling dvd playback [http://ubuntuforums.org/showthread.php?p=4734003#post4734003](http://ubuntuforums.org/showthread.php?p=4734003#post4734003)  #14

---

### Post by odin79 on 2008-04-27
Okay I tried to open a picture cd made on windows. When I insert it, it appears under "Places" as "UDF Volume". 

I also get a message saying 

"Unable to mount the Volume UDF Volume. Mount block device /dev/scd0 is write protected, mounting read only mount: Wrong fs type, bat option, bad superblock on /dev/scd0, missing codepage or helper program, or other error. In some cases useful info is found in syslog. -try dmesg | tail."

The CD works fine in Windows.

I also tried burnig some movies to a DVD just to test, which worked fine. I also can view the files, but when I try to play the movies I get errors saying:

"[00000297] vcdx access error: fread (): Input/output error
[00000297] access_file access error: read failed (Input/output error)"

The movies play fine in VLC when opened from the disc.

So to summarise:
1. I can burn DVD's.
2. I can view the files on CD's and DVD's, but I can't read them, not even pictures.
3. With commercial DVD's I can't even see the contents, but I'm guessing this is related to 1 and 2.

Seems like the Hardy upgrade f****d up my DVD config, that is just such a show stopper! :-( I was hoping to avoid a reinstall, but if nothing else helps....

Anyways thanks for trying to help me guys, you were of great helpe even if we couldnt fik it!! :-)

---

### Post by bwallum on 2008-04-27
I'm sorry we couldn't help. I can say that playing dvds on Heron is certainly possible and from my experience worked painlessly. I have also been riding the beta so my system is a composite of all the updates through that up and down period. Its worth doing a reinstall but before you do could you tell me if you removed the /dev/sdc0 entry from fstab?

Regards and good luck
Bob

---

### Post by odin79 on 2008-04-27
Yes I did remove and rebooted, no change. I will let you know how it goes after the reinstall!

---

### Post by mc4man on 2008-04-27
@odin79 - just noticed your post #50 about dvdnav patch for vlc (also works for totem) 
I don't think thats your problem, the titles it address's are rare and doesn't affect mounting or retrieving keys only playback.
It is a good thing to have though
One way is to go to site, click on link below debian which will bring you to a page with repo links to add to sources. after doing that you would in synaptic or apt-get install package libdvdnav-ifo4 
What I do instead is go a little further down the page to linux i386 and dl libdvdnav.so.4.0.0 to my desktop. Then run
```
cd Desktop
chmod a+x libdvdnav.so.4.0.0
```
then using gksudo nautilus navigate to /usr/lib and shift delete the existing
libdvdnav.so.4.0.0 and replace it with one from desktop ( you could also do this from terminal instead of gksudo ... )

if successful you'll see this from cli
```
VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread patched to play DVDs with DVD-Movie-Protect
libdvdread: Using libdvdcss version 1.2.9 for DVD access
```

mplayer can also be patched, for that go here [http://tobias.rautenkranz.ch/03-udf.patch](http://tobias.rautenkranz.ch/03-udf.patch) and copy into a text file that is used to patch dvdread inside of mplayer source before compiling
[http://ubuntuforums.org/showthread.php?t=652528&page=2](http://ubuntuforums.org/showthread.php?t=652528&page=2)

---

### Post by mc4man on 2008-04-27
reevaluating
what I was seeing was that when you replace a cdrw drive with a dvdrw drive udev fails to recognize the difference and won't assign any dvd links in /dev, fixed by deleting the entries in 70-persistent-cd. rules and rebooting
ie. irrelevant to this threads issue

---

### Post by Fury5000 on 2008-04-28
I was able to get DVDs working fine with the help of this string but something that worked in Gutsy isnt working in Hardy... I took a few fav dvd's and used k9copy and turned them into .iso's that I keep on my pc.  In VLC these files used to play with the DVD menu's intact and working.  These same .iso files now sitting on the new OS will play but without DVD menus and seem to start off playing some of the extras.  What would cause VLC to handle these iso's a different way?.. I even burned another dvd to an .iso on the Hardy install but it does the same thing.  Any clues? Sorry to hijack also...

---

### Post by Craigupdegrove on 2008-04-29
I am having a sort of different problem. My blank dvd's won't mount commercial Dvd'd and pre written dvd's read fine please help

---

### Post by odin79 on 2008-04-29
Ok I have reinstalled now, but it didn't seem to help. Hardy really hates my DVD-player. Also the installation process was painfull to say it the least. I acctually had to install Gutsy and then do a upgrade from there because Hardy got an I/O error at around 75% into the installation. First I thought that the CD might be defect, so I burned a new one (with lower burn-speed) and then checked it for defects before installing. But no, at the exact same point: 75% it failed.

I guess hardy does something weird to the DVD-setup at some time. Ah well... Anyways, the reinstallation wasn't all in wain. My system feels more responsive now than before, I just have to make do with no DVD for now.

I haven't tried your tricks yet mc4man as I'm to tired to fight more with Hardy for today. But I will give it a shot tomorrow. 

Again guys: Thanks for the help, I really appreciate it!

---

### Post by bwallum on 2008-04-29
Good to hear you're back. May I suggest you get a new dvd drive. Top quality opticals are going for around £15-£25 -- $30-$50 at the moment. Sony are too MS DMR restrictive. Samsung, Liteon and Pioneer are better bets or Phillips for the brand.

---

### Post by mc4man on 2008-04-29
> But I will give it a shot tomorrow. 
That was only possibly in regards to updating over gutsy,  I'm sure from a fresh install everything is good in that regard.

---

### Post by KCormier on 2008-04-29
Howdy all!  I have all my movies backed up onto iso as well and have them playing over the network (through nfs mounts).  After upgrading to xubuntu 8.04 the video was all jumpy and no audio.  On the other hand, if I open vlc from the command line, then open the file, it works fine.  Worth a shot for you all! :)  Something about opening it through the gui?

---

### Post by odin79 on 2008-04-30
I need a holliday....

Ok here is what I did:
-deleted from /dev/ the following entries: cdrom1, cdrw1, dvd1, dvdrw1.
-rebooted, the same entries were back in place.
-there is no entry for either cdrom, cdrw, dvd or dvdrw.
-when I insert a cd/dvd now, I can't even see the contents of it (doesn't seem like it mounts). Where as I could before.

When I run "ls /dev/ -l" I get the following:
lrwxrwxrwx  1 root   root           4 2008-04-30 18:14 dvdrw1 -> scd0
lrwxrwxrwx  1 root   root           4 2008-04-30 18:14 dvd1 -> scd0
lrwxrwxrwx  1 root   root           4 2008-04-30 18:14 cdrw1 -> scd0
lrwxrwxrwx  1 root   root           4 2008-04-30 18:14 cdrom1 -> scd0

For "/media/":
lrwxrwxrwx 1 root root       6 2008-04-28 22:45 cdrom -> cdrom0

mc4man: No harm done as the dvd didnt work in Hardy before this.

bwallum: I dont see the point of buying a new dvdrw when it works fine un both Gutsy and WindowsXP.

What should I link to where mc4man? When I play a dvd in vlc, what path should I use?

EDIT: Now I managed to open a dvd i burnt a couple of days ago. I can see the movies (Matrix in AVI format). When I try to open the files:

 vcdx access error: fread (): Input/output error
[00000350] access_file access error: read failed (Input/output error)

DVD plays fine in Gutsy and Win.

---

### Post by spike7 on 2008-05-01
Hi all!
I have problems with playing DVDs after upgrading to Hardy too.
With the same system on Gutsy I had no problems.
The packages are default and latest (ubuntu+medibuntu).

The summary is: xine, totem(gstreamer), vlc don't work. Mplayer does play the DVD, but there are sometimes errors in the picture (those colorful squares and lines).
With xine and vlc the DVD-menu works and I can start the movie, but after some seconds it stops with the error messages listed below. Even the scene selection works (tried to play different scenes - some seconds play then it stops again). totem/gstreamer only comes up with an error message.


A list of the error messages:

totem/gstreamer
```
$ totem /dev/scd0
** Message: Error: Could not read from resource.
dvdreadsrc.c(919): gst_dvd_read_src_create (): /play/source

```

xine
```
$ xine --verbose=2
[... lot of info ...]
xine: found input plugin  : DVD Navigator
libdvdnav: Using dvdnav version 1.1.11.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdcss debug: opening target `/dev/scd0'
[...]
libdvdcss debug: decrypting disc key d0:8c:85:7a:14
libdvdcss debug: trying player key 01:af:e3:12:80
libdvdcss debug: decrypted disc key is 00:00:00:00:5c
[...]
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000155
libdvdcss debug: title key found in cache 00:00:00:00:00
libdvdread: Elapsed time 0
[ rest of VOBs, load plugins, other msg ]
libdvdcss error: read error
[ repeat about 40 times ]
input_dvd: Error getting next block from DVD (Error reading from DVD.)

---------------------- (ERROR) ----------------------
The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: not disc in drive). (Error reading from DVD.)

['Read error from:' 'Error reading from DVD.']
------------------ (END OF ERROR) -------------------
```

vlc
```
$ vlc
VLC media player 0.8.6e Janus
[00000298] dvdread demuxer error: read failed for 2/4 blocks at 0x49
[00000287] main playlist: nothing to play
```

mplayer
```
$ gmplayer dvd://1
[...]
VO: [xv] 720x576 => 1024x576 Planar YV12 
a52: CRC check failed!  0.011 ct:  0.092  54/ 54 35% 12%  3.1% 9 0 
a52: error at resampling
A:  11.9 V:  11.9 A-V:  0.034 ct:  0.055 288/288 24%  7% 31.0% 32 0 
[...]
```

Sorry for the long post, but maybe it helps to solve the problem...
Thanks for any hints!

---

### Post by odin79 on 2008-05-01
It would be nice to know what changes they did to the way cd's/dvd's are mounted.

---

### Post by LostInBrittany on 2008-05-01
Same problem here, with both laptop and desktop.
I'm unable to mount any DVD, neither commercial (movies) nor data ones...

I hope somebody find a solution soon

---

### Post by spike7 on 2008-05-01
I don't have any problems with mounting the discs, but reading (and writing) doesn't really work. I can read/write some data and then get I/O errors. I just tried to burn a CD (as root). 2MB were written - then: error.
In a way this looks very much like hardware failure, but since I never had any troubles until a couple of days ago when I upgraded the system and other people are experiencing problems too, I tend to think it's the software.

On two laptops where made a fresh install of Hardy there are no such problems. Strange...

EDIT: This seems to be independent from libdvdcss, libdvdread etc. A backup .iso of a movie I have on my harddisk is working like a charm with each of the players (xine, totem, vlc, mplayer). And in case you wonder: The movie is encrypted - I can see the output of libdvdread about retrieving the CSS keys.

---

### Post by odin79 on 2008-05-01
IMHO this is a HW problem as the HW works in both Windows and Gutsy (for several ppl). Also it is REALLY hard to troubleshoot. mc4man has been very helpfull, even though we didn't find a solution.

---

### Post by Fury5000 on 2008-05-01
> **KCormier said:**
> Howdy all!  I have all my movies backed up onto iso as well and have them playing over the network (through nfs mounts).  After upgrading to xubuntu 8.04 the video was all jumpy and no audio.  On the other hand, if I open vlc from the command line, then open the file, it works fine.  Worth a shot for you all! :)  Something about opening it through the gui?

Yes...I found this to work also... I had found a really old locked hardy development thread about this problem.  If you open VLC first.. then open any iso or folder containing movie iso's it works perfectly.  But open an iso by rt-click open with... and you get what looks like a damaged movie.  I dont know why this broke in Hardy.  On a side note...I could not get Hardy to install on my second laptop.. put Mint on and it plays everything perfectly out of the box.  I have yet to fully grasp why we have to struggle with this on the flagship of linux os's...

---

### Post by mc4man on 2008-05-01
@ odin 79 
your /dev links are fine as is and considering you have a fresh install playback 'should' work. The thing about the dev links was an unrelated issue. What is interesting was this post [http://ubuntuforums.org/showthread.php?t=756200](http://ubuntuforums.org/showthread.php?t=756200) which was 'solved' by going back to an earlier kernel. In your case though not that much use, they probably had installed from beta and so had different kernels to boot to and anyway at the end of the day the current kernel should work.
I think maybe you should try taking this one more time from the top,- is inserted media mounting properly ? (by that I mean is an icon appearing on desktop,and an entry in places with _no action on your part other than inserting disk_)

---

### Post by spike7 on 2008-05-01
I can confirm that it seems to be a kernel issue. 
Installed Gutsy - DVD works. Upgraded to Hardy - DVD doesn't work. Start Hardy with Gutsy-kernel: DVD works.

---

### Post by mc4man on 2008-05-01
@ spike - do you have a sata or ide dvd drive?

---

### Post by spike7 on 2008-05-01
an IDE drive:
```
$ cdrecord -checkdrive dev=/dev/scd0 
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-H12N '
Revision       : 'UL01'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R

```

---

### Post by Pollywoggy on 2008-05-01
I had the same problem with audio CD's, so I don't know if it is related but in my case, I found that the symlink pointing from /dev/scd0 to /dev/cdrom disappeared during the upgrade to Hardy.  I made the symlink and this fixed the problem.

---

### Post by bwallum on 2008-05-01
I've just set up a new install on a fresh i386 machine. I've hit the same problem.

Polly, can you do a detailed how to for the symlink fix please?

---

### Post by mc4man on 2008-05-01
@ bwallum.
probably best for pollywoggy to respond though you can ck. in /dev, the 5 links dvd, dvdrw, cdrw, cdrom, sr0 should all link to scd0 (if you have sata drive will probably be dvd1,sr1, ect.)

---

### Post by odin79 on 2008-05-01
Ok first of all some info of my setup.

-In /dev/: dvdrw1, dvd1, cdrw1 and cdrom1 all links to scd0.
-I have all possible codecs installed. All movies I have (AVI, mpeg, and so on) all plays in VLC when opened from the hard drive.
-I can burn CD's and DVD's.

As for taking it from the start, when I insert a DVD (in this example a DVD with all three Matrix movies in AVI-format):
1. I insert DVD.
2. It mounts, icon appears on desktop.
3. I open the DVD and see my files. All well so far right?
4. I open VLC from terminal, selects "File->open file" and selects one of the AVI files. The path in VLC is "/media/Matrix/Matrix/Matrix.CD01.avi". 
5. The DVD starts to spin, but then I get errors in the terminal.

VLC media player 0.8.6e Janus
[00000297] vcdx access error: fread (): Input/output error
[00000297] access_file access error: read failed (Input/output error)
[00000297] access_file access error: read failed (Input/output error)
....

EDIT: I believe that the "vcdx access error: fread (): Input/output error" is the same error I got when installing Hardy.

When I stop the playback:
[00000303] main private error: cannot pre fill buffer

I also tried to select "File->Open disc". Device name: /dev/scd0.

Errors I get from this:

libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title:  
libdvdnav: DVD Serial Number: 
libdvdnav: DVD Title (Alternative):   ,  
libdvdnav: Unable to find map file '/home/odin79/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000305] dvdread demuxer error: DVDRead cannot open source: /dev/scd0
[00000307] vcd access error: no movie tracks found
ioctl(): No medium found
[00000307] vcdx access error: error reading Info sector (150)
[00000307] access_file access error: file /dev/scd0 is empty, aborting
[00000309] main private error: cannot pre fill buffer
[00000312] cdda access error: could not read block 0 from disc
[00000312] cdda access error: cannot read sector 0
....

As you can see it is driving me nuts, I have NO idea why it won't play.

---

### Post by mc4man on 2008-05-01
> As you can see it is driving me nuts that's an understatement I'm sure. Do you have a regular dvd movie you could try in vlc.Maybe open vlc from cli with vlc /dev/dvd1.  Have you tried to copy one of the avi's off of the disk ?
the reasoning behind copy one of the avi's to hdd is it's not encrypted and playback from hdd would take drive out of equation

---

### Post by michael_nz on 2008-05-02
Hi Odin79,

I had a very similar problem, and tried many things from this thread before I fixed it.  The solution was to add the kernel parameter all_generic_ide on boot.

I'll try to make this detailed enough for anyone who might need it:
[LIST=1]
[*] Open up a terminal.
[*] Make a backup of your grub settings:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_orig
```
[*] Open the settings file:
```
sudo gedit /boot/grub/menu.lst
```
[*] Find the line
```
## ## End Default Options ##
```
after a whole lot of commented stuff.
[*] Find the first Linux entry after that.  It will look something like this:
```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c566310-834c-4aaa-924c-94eabe4e455f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

```
This is on a fresh install of Hardy.
[*] Add " all_generic_ide" to the end of the "kernel" line.  For me that results in:
```

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9c566310-834c-4aaa-924c-94eabe4e455f ro quiet splash all_generic_ide

```
Your UUID will be different, and there might be other differences as well -- that's fine.  Be careful not to change anything else.
[*] Save the file and restart the computer.
[/LIST]

I don't know what changed between Gutsy and Hardy to break this, but I had related problems booting from the install CD.

Hope this helps,
Michael

---

### Post by LostInBrittany on 2008-05-02
Michael, I've already tried that yesterday, it doesn't work for me.

In a precedent post, I've seen that I should have a symbolic link from /dev/dvdrw to /dev/scd0. I haven't that link, I have the other four (/dev/dvd, /dev/cdrom, /dev/cdrw and /dev/sr0). Do you think it can be important ?

---

### Post by michael_nz on 2008-05-02
> Michael, I've already tried that yesterday, it doesn't work for me.

That's a pity.  There seem to be a few problems with almost the same symptoms.

> In a precedent post, I've seen that I should have a symbolic link from /dev/dvdrw to /dev/scd0. I haven't that link, I have the other four (/dev/dvd, /dev/cdrom, /dev/cdrw and /dev/sr0). Do you think it can be important ?

I doubt it.  Maybe it's missing because your drive can't write DVDs?  It's easy enough to try though:
```
sudo ln -s /dev/scd0 /dev/dvdrw
```

And to remove it again if you want to:
```
sudo rm /dev/dvdrw
```

Michael

---

### Post by odin79 on 2008-05-02
> **mc4man said:**
> that's an understatement I'm sure. Do you have a regular dvd movie you could try in vlc.Maybe open vlc from cli with vlc /dev/dvd1.  Have you tried to copy one of the avi's off of the disk ?
the reasoning behind copy one of the avi's to hdd is it's not encrypted and playback from hdd would take drive out of equation

Yes I have tried to copy an avi-file from DVD to HD:

cp: reading `Matrix.CD01.avi': Input/output error

That is all. It doesn't seem like it's an encryption problem!? 

@michael_nz: I will try out your recepie.

It seems like a lot of ppl are having these problems. It's quite annoying as this is the last thing I need to get to work before I can drop Windows for good. =(

---

### Post by bwallum on 2008-05-02
Did you try micheal_nz's fix?

---

### Post by odin79 on 2008-05-03
THANK YOU THANK YOU THANK YOU!!! Adding all_generic_ide to the /boot/grub/menu.lst did the trick. All DVD's are working fine now, both data and commercial dvd's.

So for the record, what fixed the dvd-read problem for me was modifying /boot/grub/menu.lst and adding all_generic_ide to this line:

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=00b67842-5536-4a1d-8cba-c11b12cac714 ro quiet splash all_generic_ide

And then reboot.

Thank you all for taking the time to help me. Hope some other sorry dude is able to find this post!

---

### Post by lancern on 2008-05-03
:guitar: Congratz :guitar:

Finely..most ppl would have given up but you toughed it out.

---

### Post by odin79 on 2008-05-03
Lol yeah I know, pertinacious as hell. But I really would like to drop Windows altogheter, and now I have no reason not to. =)

---

### Post by michael_nz on 2008-05-03
> **odin79 said:**
> THANK YOU THANK YOU THANK YOU!!! Adding all_generic_ide to the /boot/grub/menu.lst did the trick. All DVD's are working fine now, both data and commercial dvd's.


Woohoo! :)

---

### Post by Kowalski_GT-R on 2008-05-03
trying it now, fingers crossed!

EDIT: no cigar here...Ubuntu sucks! no, joking...:-)

---

### Post by bwallum on 2008-05-03
> **michael_nz said:**
> Woohoo! :)

Plus 1 ! Thank you very much!

---

### Post by odin79 on 2008-05-03
Kowalski, you need to find out if it is an encryption error or a read error. The how-to is in this thread.

---

### Post by ScarySquirrel on 2008-05-04
> **odin79 said:**
> My problem is that I can't play DVD's anymore after upgrading from Gutsy to Hardy. All my DVD's worked fine in Gutsy (started automagicaly). They also play in WinXP (I have dual boot)."
I discovered the same problem when I upgraded to the Heron version.  Bloody thing is beaking my dvds.
I received the following laconic error, titled "An error occurred" when I tried to run my CSS encrypted DVDs:
"Could not read from resource."
I suspect that this issue is more widespread than even the forum posts here indicate.

---

### Post by CyDharttha on 2008-05-04
So is this the same as the /dev/dvd1 problem in the following thread?: [http://ubuntuforums.org/showthread.php?p=4878593#post4878593](http://ubuntuforums.org/showthread.php?p=4878593#post4878593)

Is it possibly caused by an upgrade as opposed to fresh install, or are both affected?

---

### Post by ScarySquirrel on 2008-05-04
In true linux tradition, I have done the following:
     A. Complained about my problem on the forums.
     B. Subsequently solved my problem myself.
     Time for step C.
     An easy way to fix this that does not involve the Terminal follows:
     1.  On your desktop, in the upper right, three menus exist.  Click the menu labeled "System."
     2.  A series of menus should then "drop" down, appearing below the word "System."  Click the menu labeled "Administration" among those.
     3.  Another large menu will appear.  Among its options, find the option labeled, "Synaptic Package Manager", and click that.  This option has a little open box with a gear superimposed to its left.
     4.  A window will appear asking you for authorization to change important parts of your system.  Don't worry.  It's not just you.  The heron spares none from this indignity.
     5.  The "Synaptic Package Manager" should now appear.  It has several icons near the top of its window, some of which are in gray, labeled "Reload", "Mark All Upgrades", "Apply", "Properties", and "Search".
     6.  Click the icon labeled "Search".
     7.  Type the name of the item for which you are searching "libdvdcss".  This is the name of the program that your media player will use to open your DVDs.  
     8.  Once you have typed the name of what you are searching for in the little "formbox" that appeared once you clicked the "Search" icon, click the "search" button in that same little "formbox" window.
     9.  Among the results of your search should appear the "package" labeled "libdvdcss2".  Click the little gray box to its left, and click "Mark for Installation" in the small window which then appears.  If another window appears, click "Mark" or "OK" or "Close" in that window as well.  It's just asking you permission for installing some necessary supporting programs.
     10.  Click the "Apply" icon, which should now have a green color in it.
     11.  A window labeled "Summary" will appear. Click the green button labeled "Apply" in the lower right of this window.
     12.  Two windows will appear, but you don't have to do anything about them except close the second window when it has finished its little tasks, when a "close" button appears.
     13.  Insert your DVD into your DVD Drive.
     14.  An icon will appear on your desktop, indicating that your computer has successfully recognized, or "mounted" your DVD.
     15.  Click the newly-appeared icon with the "right" mouse button.  A small menu should appear, which is sometimes referred to as the "context menu" or "right-click" menu.  In this menu should be an option called "Open with Movie Player".
     16.  Click it.  If your movie doesn't play, read and try some of the more difficult advice in this forum, or send me a polite message which contains at least one full sentence.

---

### Post by ScarySquirrel on 2008-05-04
> **CyDharttha said:**
> Is it possibly caused by an upgrade as opposed to fresh install, or are both affected?
This difficulty affects both a fresh installation and the upgrade.  
I have tried both.

---

### Post by dbw on 2008-05-05
I was having a very similar problem.  I noticed that Hardy had reset my links in /dev, so none of my apps knew where the dvd drive was.  If you are having the same problem, make sure that your /etc/fstab points your /media/*dvd* (or whatever it is) to a real /dev/*device*, and adjust the settings of your favorite media programs to point to the correct /dev/*device*.

---

### Post by classem2003 on 2008-05-08
I tried this approach and it works as far as you know the name of the media folder where the folder is created,( /media/whatever) that happen to be the name of the label of the disk, so it changes with the disk. It seems that /media/cdrom is no longer mounted automatically. I have posted another solution to this at

[http://ubuntuforums.org/showthread.php?p=4908140#post4908140](http://ubuntuforums.org/showthread.php?p=4908140#post4908140)

It worked for me.

---

### Post by s6long1 on 2008-05-09
whoever suggested adding the generic_ide to the bootloader is awesome in my book! :guitar:
i kinda had the same problem, kinda didnt. i had all the codecs and media players you could think of, and my dvds (commercial) would be mounted...but when i tried to play them, the video and audio would stutter and be jumpy so much that they were unplayable. my mouse would start jumping around too, and everything would act really sluggish, making me think my memory or cpu was being hogged by totem, but vlc had the same problem. well, problem solved though, thanks guys! now i can watch my movies without windoze! :popcorn:

---

### Post by MerrickB on 2008-05-12
> **omicrondelta said:**
> Re-build your opensource dvd-player of choice and link to libdvdcss... Debian packages are not... End of thread...

Sorry if I'm a little cryptic, but the boys and girls behind everything have been for me... If I can do it... You can DO Eeet!!! I just Ogle my DVDs... 

Thanks much for the point to Ogle.  Loaded it up, and it did what I expect a DVD player in an OS to do:  Access the Menus, Accept Mice Commands, and Play the movie the way that I want it to play.  

I'll still look into trying to fix both totem and VLC, but Ogle worked like a charm the first time installed (unlike the others).  :biggrin:

---

### Post by asino89 on 2008-05-13
Thank you all, but special thanks to [michael_nz](http://ubuntuforums.org/member.php?u=568872)!

I had experienced the same problems that you are reporting here (dvds that cannot mount, commercial dvds which can't be played and so on...)...
What helped me (after a failed troubleshooting in the italian forum) was a link to michael's post [here](http://ubuntuforums.org/showpost.php?p=4859820&postcount=80)!

Now everything just works fine!

I don't know if mine is just one of many kinds of problems, but i think it's useful to let you know that that solution worked!

Thanks to all again!

---

### Post by halfmanhalfbug on 2008-05-16
Same problem here. Fglrx and all the codecs are installed and working but playback of encoded DVDs is very choppy and out of synchronization. Adding "all_generic_ide" to the boot parameters, as described by michael_nz, fixed it. Now, anyone know what "all_generic_ide" does? I have read that it helps on machines with multiple hard-drives but mine's a laptop with one drive.

---

### Post by Chuckels550 on 2008-05-16
My DVDRW drive has been on the fritz since I upgraded from Mythbuntu 7.10 to 8.04.  I have tried adding "all_generic_ide" to the boot parameters, as described by michael_nz, that didn't help.  Using a symbolic link between /dev/dvd and /dev/dvd1 did make it possible to play movie dvds, but I still cannot use the drive to play or rip audio CDs.

---

### Post by MerrickB on 2008-05-16
> **ScarySquirrel said:**
> This difficulty affects both a fresh installation and the upgrade.  
I have tried both.

While a n00b myself to Linux and Ubuntu (but not computers, as I've been working with Windows and Mac primarily for about 20 years), and freshly back to it since 8.04, I find myself at a loss for words as to what changed so drastically with the OS and how it handles encrypted DVDs.  

I followed the instructions at [COLOR="Silver"][http://ubuntuforums.org/showthread.php?t=766683&highlight=DVD+Playback]("http://ubuntuforums.org/showthread.php?t=766683&highlight=DVD+Playback")[/COLOR] with no problems following terminal instructions (I tend to do a lot of terminal input because of the work I do with Servers). 

The first time I followed the instructions, I had cherry picked through the listing of it, as I didn't need everything else non-free and wanted to play movies like I used to back in Gutsy and Feisty.  I noticed immediately that I was having problems with Totem and VLC playing encrypted DVDs -- completely circumventing the menu and going right into the movie (which could be a problem, given I have quite a few foreign films), or even having problems recognizing a DVD mounted at all.  

Saw Omicron mention Ogle, and loaded it up and was thankful that I could play all DVDs regardless of Hardy recognizing the DVD as being mounted or not.  But I didn't like the fact that following the instructions in the thread aforementioned, it left junk (a partially working VLC) in my menu, and wanted to continue troubleshooting the problem.  

I attempted a reinstall of all the necessary libs (2, 3, and 4) including VLC, through Synaptic (as you had provided here for the other n00bs), and noticed that VLC was now seeing the menus (yet still couldn't access them) and  screen quality was banded and heavily pixelated; I knew I was onto something about the libs not being bound correctly (according to someone else at the beginning of the thread).  It's not as though I'm running a PATA or SATA DVD Drive, it's a standard IDE: 

$ cdrecord -checkdrive dev=/dev/scd0
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Memorex '
Identification : '16X-DDL-IN      '
Revision       : '1.A3'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R

So, mimicking Odin's attempt, I decided to wipe the partition (I'm a dual-booter) and following the complete instructions once again from the sticky for Hardy users.  

Before testing it out however, as a precaution, once I followed **all** the instructions in the sticky, rebooted once I had complete, and applied all the necessary patches/updates, I installed Ogle because it had worked the last time.  

VLC works like a charm (right out of the box), so does MPlayer (with just a little bit of tweaking).  Both recognize the drive, does what they're supposed to do according to the sticky (access the drive, accesses the menus, picture quality is where it's supposed to be).  Totem still ignores the menus and goes right into the movie (can't access the menus from the window either), Gnome Mplayer's output is messy (pixelated, and garbled), and Ogle doesn't even recognize the drive anymore. 

So I decide, "all right, OGLE doesn't work, I'll simply uninstall it."  The instant I do that, while VLC recognizes the drive, and will start at the menu it does so with positively no sound.  Accessing any of the menu options ends with VLC going south and forcing me to pkill it.  *sighs*  So I put Ogle back in, removed it from my Applications Menu for the time being, and consider my problem solved because I've been at this for about 5 days now.    

I'm going to keep Michael_NZ's [http://ubuntuforums.org/showpost.php?p=4859820&postcount=80]("http://ubuntuforums.org/showpost.php?p=4859820&postcount=80") information on editing the GRUB menu on the back burner as I suspect that if it worked for Odin the odds are pretty good that it's going to work for me as well.  

Good luck to anyone that continues to have problems, I've got mine working the way I want it.

---

### Post by mc4man on 2008-05-16
> noticed immediately that I was having problems with Totem and VLC playing encrypted DVDs -- completely circumventing the menu and going right into the movie more than likely that's from vlc using %U (by default), setting vlc as your 2nd autoplay choice with launch command of %m resolves that. (as i guess you did )
> the instant I do that, while VLC recognizes the drive, and will start at the menu it does so with positively no sound In vlc going into settings -> prefs -> audio output modules and selecting alsa can fix that in alot of cases
> totem still ignores the menus and goes right into the movie
If you wish just install totem-xine and then run  ```
sudo update-alternatives --config totem
``` choose 2 and totem-xine will become the default totem choice (has menu support)

---

### Post by MerrickB on 2008-05-17
> **mc4man said:**
> more than likely that's from vlc using %U (by default), setting vlc as your 2nd autoplay choice with launch command of %m resolves that. (as i guess you did )
 In vlc going into settings -> prefs -> audio output modules and selecting alsa can fix that in alot of cases

If you wish just install totem-xine and then run  ```
sudo update-alternatives --config totem
``` choose 2 and totem-xine will become the default totem choice (has menu support)

Thanks for the information.  Both did the trick for me.  While Totem will occasionally go right to the movie (it didn't in Gutsy), at least with Xine in place, Totem will accept menu access.  

Although I'm kind of surprised that leaving the Audio to the "Default" setting would cause VLC to hang/crash the way that it did.  But as I'm fond of telling myself, it's a learning experience.  :smile:

---

### Post by mc4man on 2008-05-17
> My DVDRW drive has been on the fritz since I upgraded from Mythbuntu 7.10 to 8.04. I have tried adding "all_generic_ide" to the boot parameters, as described by michael_nz, that didn't help. Using a symbolic link between /dev/dvd and /dev/dvd1 did make it possible to play movie dvds, but I still cannot use the drive to play or rip audio CDs. maybe try the same thing with /dev/cdrw and possibly /dev/cdrom

---

### Post by Gregory Sands on 2008-05-18
Ok I too am having issues with DVD playback of commercial disks.  With Gutsy I installed Automatix and the obtained the codec from there.  Automatix will not work with Hardy so that theory is blown.  Got any other ideas?:popcorn:

---

### Post by gigaferz on 2008-05-18
why you just dont  go back to 7.10?

Just wait  a few weeks or months to see if this will get fixed

I did this:> 

 Re: DVD movies not playing
hello,

After enabling the medibuntu repos,installing libdvdcss2 and w32codecs (only,nothing xine related) choosing a better server and selecting X11 in vlc, I got a dvd movie playing
Thank you

however the playback is horrible, it is an old computer but, it used to play dvd with no problems, 

this is the link
[http://ubuntuforums.org/showthread.php?t=773512](http://ubuntuforums.org/showthread.php?t=773512)

---

### Post by Chuckels550 on 2008-05-23
> **mc4man said:**
> maybe try the same thing with /dev/cdrw and possibly /dev/cdrom

I did and no joy.

---

### Post by mc4man on 2008-05-23
> I did and no joy. 
read thru this thread and see if it applies to you. If maybe but unsure post from sudo lshw -C disk and the contents of 70-persistent-cd rules
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

edit; if you have just 1 entry in rules with the links to dvd1, cdrw1, ect. you can edit as shown, delete the appropriate links in /dev and reboot and see.

---

### Post by Chuckels550 on 2008-05-25
> **mc4man said:**
> read thru this thread and see if it applies to you. If maybe but unsure post from sudo lshw -C disk and the contents of 70-persistent-cd rules
[http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)

edit; if you have just 1 entry in rules with the links to dvd1, cdrw1, ect. you can edit as shown, delete the appropriate links in /dev and reboot and see.

Thanks - that fixed it.  That should be a sticky.

---

### Post by cpjkennedy on 2008-05-25
Thanks, michael_nz!  That fixed my problem!  Now I just have to deal with a bit of mild interlacing, but at least I can play DVDs!

---

### Post by kadafi69 on 2008-05-26
Ive just found this thread, its exactly the problem im having. yet ive tried everything here and to no avail its still not working.

i have all the codecs installed, tried ogle, uninstalling then re-installing packages.

tried the all_generic_ide in grub

this is a fresh install of hardy, not an upgrade.

also im not getting a long error list in vlc, it just says

> Unable to open 'dvd:///dev/cdrom'

ive tried changing the cdrom address to cdrom0, dvd etc etc

---

### Post by mc4man on 2008-05-26
> ive tried changing the cdrom address to cdrom0, dvd etc etc 
You need to supply more info, for starters are your discs being mounted (showing up on desktop) _If not_ that's a separate issue
Are you using ubuntu or kubuntu?
_If they are_ and your using ubuntu try accessing the disk from either the device or the mount point (bypass any links) in terminal

vlc /dev/scd0   (or scd1  (device))

vlc /media/cdrom    (mount point)

---

### Post by kadafi69 on 2008-05-26
im using ubuntu 64bit. no the discs are not being mounted. nothing is showing up at all. I have nautilus set so that no mounted devices show up on my desktop (bit of a neat freak!). yet there is nothing to tell me anything is mounted, no disks show up in nautilus, or anywhere else for that matter.

---

### Post by mc4man on 2008-05-26
> I have nautilus set so that no mounted devices show up on my desktop Why don't you undo whatever you did to achieve that, put a dvd in (preferably a commercial dvd movie) and after the light on dvd drive goes solid if it's not mounted run dmesg | tail  and see what it says. Can you see drive in places?

---

### Post by kadafi69 on 2008-05-26
> **mc4man said:**
> Why don't you undo whatever you did to achieve that, put a dvd in (preferably a commercial dvd movie) and after the light on dvd drive goes solid if it's not mounted run dmesg | tail  and see what it says. Can you see drive in places?

ok so i changed the nautilus setting back. i tried a commercial dvd (24) it mounts, i try a back up of syrianna, nada. so i run the dmesg thing

> [   42.711874] Bluetooth: RFCOMM socket layer initialized
[   42.711893] Bluetooth: RFCOMM TTY layer initialized
[   42.711895] Bluetooth: RFCOMM ver 1.8
[   45.070380] lirc_dev: IR Remote Control driver registered, major 61 
[   45.071474] lirc_streamzap: no version for "lirc_unregister_plugin" found: kernel tainted.
[   45.071907] usbcore: registered new interface driver lirc_streamzap
[   45.071912] lirc_streamzap $Revision: 1.24 $ registered
[   45.462766] eth0: no IPv6 routers present
[   64.461424] Inbound IN=eth0 OUT= MAC=00:30:1b:b8:e8:59:00:04:e2:bd:43:b2:08:00 SRC=192.168.2.1 DST=192.168.2.137 LEN=362 TOS=0x00 PREC=0x00 TTL=64 ID=40734 PROTO=UDP SPT=1900 DPT=57942 LEN=342 
[   67.995556] Inbound IN=eth0 OUT= MAC=00:30:1b:b8:e8:59:00:04:e2:bd:43:b2:08:00 SRC=192.168.2.1 DST=192.168.2.137 LEN=364 TOS=0x00 PREC=0x00 TTL=64 ID=40747 PROTO=UDP SPT=1900 DPT=57942 LEN=344 


i have no idea what any of this means.

the drive does not show up in places. its like i havent put a disk in the drive.


edit

i see that it mentions lirc, i recently tried installing a infra red remote, to no avail, the device semi works and is still attached to the pc, could this be a problem?

---

### Post by mc4man on 2008-05-26
> i tried a commercial dvd (24) it mounts So is where your at that a commercial disks mounts but a dvdr doesn't? If so to can you playback 24?

---

### Post by kadafi69 on 2008-05-26
> **mc4man said:**
> So is where your at that a commercial disks mounts but a dvdr doesn't? If so to can you playback 24?

well ive since been trying different combinations, some commercial disks mount and i get playback, some dont. some dvdr disks mount and playback, the vast majority dont. 

ive ruled out the lirc thing as ive realised this problem has been going on before i started messing around with the infra-red remote.

---

### Post by mc4man on 2008-05-26
> _some commercial disks mount and i get playback_, some dont. _some dvdr disks mount and playback_, the vast majority dont.
From the Os side this isn't a dynamic situation, your either setup correctly or not. The fact you do get playback means you are, particularly with the commercial disks which provide a known constant filesystem (udf 1.02). ((another way to ck. if a disk is mounted and the fs is look in system monitor))
i think you'll have to look at your hardware(dvd drive) and or source media

---

### Post by kadafi69 on 2008-05-26
this is highly annoying, i really dont want to have to re-install xp so that can view these dvds!

---

### Post by YODAR on 2008-05-26
> **omicrondelta said:**
> One thing is, is you have to realize that the opensource community is diverse, and your hard-drive has lots of gigabytes free... There's no all-in-one media solution yet... Ogle for bought DVDs and build it yourself... Just like daddy always said... You feel better about it when you do it yourself...


Not like I'm bragging or anything... I'm 1/2 drunk... 6 pack in the pail... But I've been a Linux user (and nuttin' but... well maybe Windows for 2 and OSX for under 1) for 11 years... You can do Eeet... I'm just a Class 1 truck-driving B.Sc. Computing Science dropout by trade...

edit:

I edit my posts on a regular basis... Re-proofin' all da time... Cheers to being a drunk red-neck Linux user... Woo Hoo!!! I got sound again bee-yatch!!!




SO SAY WE ALL...

p.s. Is it just me... Or does the interface on Firefox3 suck... I miss the interface of Firefox2, but not the malloc() leaks...
===========================================================

I am happy as a pig in slop. Ii used Brasero to copy a DVD I bought  from an internet distributor (Sharpe's rifles) and it copied and played fine even tho brasero's checksum proggy said there was an error. 

The Resulting copy seems to work however it is lower in resolution

I am surprised how painless it is. I didnt try to play it in Linux, I used my DVD player

yodar

---

### Post by odin79 on 2008-06-10
Please note: all_generic_ide may fix cd/dvd, but for me it made my harddrive speed REALLY slow so I had to remove that option from boot.

So now my dvd-rom doesn't work again!!!

---

### Post by mc4man on 2008-06-10
@ odin 
are the dvds mounting or is it back to nothing showing up (no desktop icon, in places, in dmesg, ect.) or is the drive not even found by the Os (grep 'CD-ROM' /var/log/dmesg)

---

### Post by jackthecoiner on 2008-06-11
michael_nz, THANK YOU!  I was totally dreading having to do a full reinstall from CD and you've saved me from that fate.  My DVD player is back and mounting properly.  Long live Ubuntu Forums!

---

### Post by jackthecoiner on 2008-06-11
> **odin79 said:**
> Please note: all_generic_ide may fix cd/dvd, but for me it made my harddrive speed REALLY slow so I had to remove that option from boot.

So now my dvd-rom doesn't work again!!!

Sorry to hear that.  Did adding the boot option slow your read speed, write speed, or both?  I haven't done extensive testing yet, but I am not seeing a major performance hit with my SATA hard drives after adding the option.

Someone raised the question earlier, but I haven't seen it answered: what, exactly, does adding the all_generic_ide option do?

---

### Post by TrashmanL on 2008-06-12
When I got my new laptop with Hardy installed, I had the same problem. I installed everything from Medibuntu and got the same error. I found out that /dev/dvd DIDN'T EXIST on my system. My DVD drive turned out to be /dev/hda

Hardy would automount the data CDs/DVDs, so mounting wasn't an issue, but since gxine would access the device directly, and it was pointing to the wrong device, they wouldn't play. Two options on this, you can go to gxine preferences, media, dvd tab and change the device to the right one. I don't know what might be the right device on your machine. My internal drives are /dev/sda1, dev/sda2, dev/sda3, so my dvd player was /dev/hda. If your main drive is /dev/hda1 (like my other machine) I would suspect /dev/hdb or /dev/hdc.

It might also just be /dev/dvd1 as opposed to /dev/dvd I found out later that I have symbolic link /dev/dvd1 that points to hda that I didn't create

I had to change it not only in gxine, but in most of my other players as well. 

To avoid that, I suspect you could just make /dev/dvd a symbolic link to the right device (likewise /dev/cdrom1 if its the same drive, as it is on mine)

---

### Post by Raleford on 2008-07-06
> **TrashmanL said:**
> When I got my new laptop with Hardy installed, I had the same problem. I installed everything from Medibuntu and got the same error. I found out that /dev/dvd DIDN'T EXIST on my system. My DVD drive turned out to be /dev/hda

Hardy would automount the data CDs/DVDs, so mounting wasn't an issue, but since gxine would access the device directly, and it was pointing to the wrong device, they wouldn't play. Two options on this, you can go to gxine preferences, media, dvd tab and change the device to the right one. I don't know what might be the right device on your machine. My internal drives are /dev/sda1, dev/sda2, dev/sda3, so my dvd player was /dev/hda. If your main drive is /dev/hda1 (like my other machine) I would suspect /dev/hdb or /dev/hdc.

It might also just be /dev/dvd1 as opposed to /dev/dvd I found out later that I have symbolic link /dev/dvd1 that points to hda that I didn't create

I had to change it not only in gxine, but in most of my other players as well. 

To avoid that, I suspect you could just make /dev/dvd a symbolic link to the right device (likewise /dev/cdrom1 if its the same drive, as it is on mine)

This is basically the same as how I fixed the issue. In VLC Player, open the preferences tab (under settings) and go to input/codecs. it will have a spot that asks for the DVD location (by default it's blank. You have to figure out where the actual DVD is on your setup. The way I found it was i used the browse feature with a DVD in the drive. it wouldn't let me actually open the whole dvd, so I went further into the DVD and picked a file (i used autorun.inf) and double-clicked it. I then manually deleted the /autorun.inf in the path of DVD and it's working just fine now in VLC. it does appear that it might be different on different systems, the path for me is /media/cdrom0/

---

