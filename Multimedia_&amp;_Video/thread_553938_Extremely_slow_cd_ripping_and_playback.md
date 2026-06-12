---
title: "Extremely slow cd ripping and playback"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by magnulu on 2007-09-18
Hello,

I rip my audio cds using abcde (with cdparanoia and lame). Sometimes it goes smoothly, but most of the time it takes a very long time (like 20-something hours!). It does not seem to matter if the CD is visibly screatched or not. In the slow cases, cdparanoia gives the :-P smiley (Unreported  loss of streaming in atomic read operation) and most of the progress bar output says V (Uncorrected error/skip). Altough, the finished mp3 file plays smoothly!

The problem seems to occur more often towards the end of the cd.

CD audio playback is also choppy and slow.

When I insert an audio cd into the tray, dmesg tells me this:
> [65967.631992] end_request: I/O error, dev sr0, sector 0
[65967.631996] printk: 8 messages suppressed.
[65967.631999] Buffer I/O error on device sr0, logical block 0
[65967.632002] Buffer I/O error on device sr0, logical block 1
[65967.632004] Buffer I/O error on device sr0, logical block 2
[65967.632006] Buffer I/O error on device sr0, logical block 3
[65967.632007] Buffer I/O error on device sr0, logical block 4
[65967.632009] Buffer I/O error on device sr0, logical block 5
[65967.632011] Buffer I/O error on device sr0, logical block 6
[65967.632013] Buffer I/O error on device sr0, logical block 7
[65967.641533] end_request: I/O error, dev sr0, sector 0
[65967.641537] Buffer I/O error on device sr0, logical block 0
[65967.641540] Buffer I/O error on device sr0, logical block 1
[65967.652259] end_request: I/O error, dev sr0, sector 1024
[65967.660894] end_request: I/O error, dev sr0, sector 1028
[65967.669318] end_request: I/O error, dev sr0, sector 1024
[65967.677064] end_request: I/O error, dev sr0, sector 1028
[65967.686156] end_request: I/O error, dev sr0, sector 1024
[65967.693094] end_request: I/O error, dev sr0, sector 1028
[65967.701225] end_request: I/O error, dev sr0, sector 1024
[65967.707073] end_request: I/O error, dev sr0, sector 1028

and the terminal spits out some libdvdread and libdvdnav messages (are these available in a log file? for now I have transscribed them from the other computer):
> libdvdread: Using libdvdcss version 1.2.9 for DVD access
Error getting volume name, setting to "Unknown"
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO

These errors don't occur when I insert a DVD. I also have no problems playing or ripping DVDs using various methods.

I run a clean Feisty (32 bit) install with 2.6.20-15-386 on a Gigabyte 965P-DS3 motherboard with a Pentium Dual Core 2ghz processor. lshw tells me I have an "Optiarc DVD RW AD-5170A 1.11 Jul19,2006", altough it says Sony on the sticker.


This is what I have tried:
1. Made sure the physical connection was good, and tried changing the drive from master to slave (according to a tip in some thread somewhere). No help.

2. I tried running cdparanoia with the --disable-paranoia option, which resulted in very good ripping speed, but some VERY minor glitches in the ripped audio. This makes me speculate that there is something wrong with the communication between the cdrom and my dear ubuntu.

3. "Enabling DMA"
$ hdparm /dev/sr0 gives me this:
> /dev/sr0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

$ hdparm -d1 /dev/sr0 
> /dev/sr0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Have googled the problem, but no one seems to come up with a solution to this. I have not tried all the solutions proposed, cause not one of them seemed to work for others. I have however tried to put combined_mode=libata at the kernel line in /boot/grub/menu.lst, but without any improvement.

4. Getting drunk
This eased my mind, for a while, but was not as enjoyable as it could have been, due to missing important audio.


Now I'm stuck AND hung over, and in great intellectual pain. Is the DMA setting the problem (why then is there noe problems with DVDs), and how do I successfully enable it? Do my CDs have some kind of copy protection (why then can I rip the same CDs in 10 minutes using my G4 and itunes?)? Is a simple kernel bug creating all this inhumane frustration? Or do I simply overlook the single most simple solution of all times?

Please help me, I want to enjoy life to it's fullest, using open source software and listening to music at the same time. Is it possible? Do I have to succumb to pirated ways to get my music digital? 

Oh, and as I run my ubuntu as a settop box with mythtv and would very much appreciate a CLI only solution!

Thanks in advance!

Regards,
Magnus Lundberg

---

### Post by glenmo on 2007-09-18
i don't have any answers for you, but i did come across this thread while researching why my copied audio cds sound like intermittent noise... i tried enabling dma (thanks for the cmd) and i got the exact same results... i'll be checking this thread.

did you try ripping to another format?  does it still happen?

---

### Post by magnulu on 2007-09-19
Hola!

About the noise: are you using cdparanoia to rip the audio? Which encoder do you use? When I run cdparanoia with the --disable-paranoia option, I (sometimes) also got some minor noise. With the paranoia option turned on, no noise, but also sloooooow speed, up to 20-something hours.

My best guess for finding out where your noise problem occurs is doing this:
> cdparanoia -v 
It will give you a verbose output of the process, and maybe make you wiser. If the wav file itself has noise in it, something goes "wrong" duing ripping (could be a badly scratched disk, or something like the mystery I'm battling). If the wav file is clean, there could be something wrong with your encoding process.

Get smarter at cdparanoias homepage: [http://www.xiph.org/paranoia/](http://www.xiph.org/paranoia/)

I have not tried to rip to different formats, as the problem occurs where cdparanoia rips to wav, ergo BEFORE the encoding process takes place.

---

