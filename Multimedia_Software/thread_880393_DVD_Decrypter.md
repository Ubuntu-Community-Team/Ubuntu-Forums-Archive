---
title: "DVD Decrypter"
date: 2008-08-04
forum: Multimedia Software
---

### Post by RealG187 on 2008-08-04
In windows I used to use DVD Decrypter. This weekend I had to copy a protected DVD for the first time in a while. The first time since I removed windows and switched to Ubuntu. I tried right clicking on the disk icon and choosing "Copy Disk" and made an ISO, but it doesnt play proper.

I had to goto the windows machine and use DVD Decrypter and transfer it over, it worked.

But is there a peogram like DVD Decrypter for Ubuntu? When I first started using it, I think I seen a program called something like xDVD Decrypter. But I bet its not in the repositories anymore, like XMMS or other stuff (VM Ware).

Also, I heard the evil Macrovision bought DVD Decrypter out, so they stopped making it. Can the last version of it do newer DVDs, or since then have they made new DRM (which I dont know how that could happen since of they would then old DVD players wouldnt play newer disks, and since DVD Decrypter only has to read the DVDs the same way a player does (by decoding them) them, any DVD that can be played can be copied).

I was able to copy "Knocked Up" using DVD Decrypter 3.5.4.0. (On the cover it lied it said "Unrated and Unprotected" but on the back it said 18A, and I clearly had trouble copying it due to it's protection!)

And while I am talking about DVDs, is there a program that I can make an AVI, MP4, etc file from a DVD Folder (with VOB, IFO, BUP files)?

---

### Post by lisati on 2008-08-04
I don't know how well they handle encrypted disks but there's DCDRip and K9copy (I have a Windows machine for that kind of thing, including DVD Decryptdr and DVDShrink)

---

### Post by RealG187 on 2008-08-04
Can anyone confirm DCDRip and K9copy? Which one would be more like DVD Decrytper.

I wonder If I would decrypt a DVD using DVD Decrypter and another program (like DCDRip oe K9copy) would I get the exact same files? (Like same CRCs)

---

### Post by iheartubuntu on 2008-08-08
As long as you get all your Essential Packages installed (instructions here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) ) then you should be OK to use K9COPY. I use it and it copies fine. I first make an ISO, then I use Brasero to copy the ISO to disc. Alternatively, you can right click any ISO and "write to disc" too.

On all Ubuntu computers the disc plays fine. So far, on all my stand alone DVD players the movies play fine too, but on Windows computers, the disc appears empty.

---

### Post by oronte on 2008-08-08
Use DVD decrypter under Wine (works the same).

---

### Post by RealG187 on 2008-08-08
> **oronte said:**
> Use DVD decrypter under Wine (works the same).

When I dbl click the exe it does nothing, the terminal gives this

> mpg@MIKED5:~$ wine '/home/mpg/Backup/PSP Backup/MPG PSP Duo/PSP/COMMON/SetupDVDDecrypter_3.5.4.0.exe' 
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"Z:\\home\\mpg\\Backup\\PSP Backup\\MPG PSP Duo\\PSP\\COMMON\\SetupDVDDecrypter_3.5.4.0.exe": Bad EXE format for 
mpg@MIKED5:~$ 


---

### Post by FakeOutdoorsman on 2008-08-09
I use vobcopy to acquire a decrypted vob file:
> vobcopy copies DVD .vob files to harddisk, decrypting (if you have libdvdcss installed) them on the way (thanks to libdvdread and libdvdcss) and merges them into file(s) with the name extracted from the DVD.
It's in the universe repository.

---

### Post by RealG187 on 2008-08-10
> vobcopy copies DVD .vob files to harddisk, decrypting (if you have libdvdcss installed) them on the way (thanks to libdvdread and libdvdcss) and merges them into file(s) with the name extracted from the DVD.
Would the file it makes be an ISO?

Also I wonder, are the decrypted VOB files the EXACT same files no matter what decrypting program you use on any OS? So would using vobcopy on Ubuntu produce the exact same files that DVD Decrpyter would on windows, or would the files be different but still have the same video (what would be different, the headers)

---

### Post by FakeOutdoorsman on 2008-08-10
> **RealG187 said:**
> Would the file it makes be an ISO?
No.  It's been awhile since I've used it, but I believe it would just create VOB files.
[QUOTE=RealG187]Also I wonder, are the decrypted VOB files the EXACT same files no matter what decrypting program you use on any OS? So would using vobcopy on Ubuntu produce the exact same files that DVD Decrpyter would on windows, or would the files be different but still have the same video (what would be different, the headers)[/QUOTE]
I doubt it would create the exact same files since they probably use different decrypting libraries, but I assume the resulting video quality would be identical.

---

### Post by RealG187 on 2008-08-10
It says it makes a file named based on the volume label, I dont think you can rename VOBs, so it probably means it makes a folder named after the labal and places the VOBs in there.

How does this encrpyiton work, doesn it encrypt the files and when the player reads it is decrpyts them by using keys stored on a part of the disk that is not copied by computer programs (like now Xbox and PS2 games have a part of the disk that is not copied, and the console checks for that part, but a modchip skips that crap and loads the game as it should) and the reason why this isnt copied ie because blank media dont have that part of the disk.

So the decrpyter program reads the keys and uses them to decrypt the file, I would imagine since the same data on the disk and the same keys would produce the same file. Like no matter what program you use to unzip a file, the output file(s) is/are always the same...

---

### Post by FakeOutdoorsman on 2008-08-10
I don't know how the de|encryption works.  I just ignorantly use it.  You can check the md5sum of the VOBs from both vobcopy and DVD Decrypter to see if the file is exactly the same.

---

### Post by cariboo on 2008-08-11
Check out this tutorial for DVD Shrink and DVD Decrypter:

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)

Jim

---

### Post by RealG187 on 2008-08-11
@ FakeOutdoorsman
I could do that or use my favorite program [Beyond Compare]("http://bestwikiever.wikidot.com/Beyond_Compare") (I swear I have no affilation with them, I just love that program! So much I downgraded my wine to get it working!)

@ cariboo907
I tried DVD Shrink and when it read the disk it said "none" under encrpyiton, so I assume it wasnt configured proporly to read the disk. I will read the thing you posted, as that is probably what is wrong...

---

### Post by pparks1 on 2008-08-11
I can confirm that k9copy alone provides the functionality of dvd decrypter and dvd shrink.

This is from a comprehensive Ubuntu desktop setup guide that I maintain on another webforum.  This does assume that you have things like libdvdcss already installed for getting around the encryption on the disc.



sudo apt-get install k9copy
Applications, Sound and Video, k9copy
select the large movie file, expand the options and select only the items that you want
In the lower right, I suggest removing the check for "Keep original menus"
click the DVD button.
Choose a location for the ISO file
Once completed you can burn the .ISO file. Applications, Sound and Video, Brasero Disk Burning

---

### Post by RealG187 on 2008-08-12
I can use any other program to burn it too (I have Nero Linux and K3B which I think came when I installed "Kubuntu-Desktop"), however you said Brasero because that ones comes with Ubuntu automatically I assume...

I am not sure if I want to reduce the quality or not... But then again I cant use Double Layer... Last I checked they were like $10 a blank disk. I bought some new ones for way cheaper but I think they are 8x and the drive I use only burns DBL Layer at 2.4X (I use a IDE Drive on my laptop via USB to IDE Adapter to burn). To read the one in my laptop is fine, but when it burns DVDs (Single Layer) the verify fails. The one I use works fine for single layer DVDs but not these new ones, however it did burn successfully to those 2.4x ones...

---

### Post by RealG187 on 2009-05-13
When I try to transcode to MPG using K9Copy I get


> A Fatal Error Occurred
The application k9copy (k9copy) crashed and caused the signal 8 (SIGFPE).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc.

When I click show details> Application: k9copy (k9copy), signal SIGFPE
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb5d648e0 (LWP 6876)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x08079b24 in _start ()
#0  0xb8097430 in __kernel_vsyscall ()

---

### Post by pythonscript on 2009-08-09
> **cariboo907 said:**
> Check out this tutorial for DVD Shrink and DVD Decrypter:

[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)



 I had that tutorial working fine, but after I reinstalled ubuntu (jaunty 32-bit, same os as the system it was working fine on) I can't get DVD Decrypter to work. Here's the contents of my /etc/hdparm.conf file. I'm guessing DMA isn't enable, but how do I enable this? Thanks!

```
## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
dma = on
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -s Turn on/off power on in standby mode
#poweron_standby = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode
# --security-freeze Freeze the drive's security status
# security_freeze
# --security-unlock Unlock the drive's security
# security_unlock = PWD
# --security-set-pass Set security password
# security_pass = password
# --security-disable Disable drive locking
# security_disable
# --user-master Select password to use
# user-master = u
# --security-mode Set the security mode
# security_mode = h

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#    mult_sect_io = 16
#    write_cache = off
#    spindown_time = 240
#}

#/dev/discs/disc1/disc {
#    mult_sect_io = 32
#    spindown_time = 36
#    write_cache = off
#}

#/dev/cdroms/cdrom0 {
#    dma = on           
#    interrupt_unmask = on
#    io32_support = 0
#}

#/dev/hda {
#    mult_sect_io = 16
#    write_cache = off
#    dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}


/dev/scd0 {
dma = on
}
```

I'm also having the same k9copy error, no matter what DVD I use. I've heard great things about that app, but it doesn't solve the problem for me yet given all the crashes.

---

### Post by cowboy7305 on 2009-08-09
I use K9 copy .only thing i had to work out was you had to safe to your desktop to get it to work,in configure, Dvd make output directory  to your desktop then use K3b to copy ,works every time for me  faster than any thing in windows and its free

---

