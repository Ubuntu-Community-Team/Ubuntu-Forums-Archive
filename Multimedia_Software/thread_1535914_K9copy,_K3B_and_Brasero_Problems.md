---
title: "K9copy, K3B and Brasero Problems"
date: 2010-07-21
forum: Multimedia Software
---

### Post by uzzo2 on 2010-07-21
Hey guys, I recently switched distributions, I let a guy talk me into switching from Ubuntu 8.04 to Mint 9. Since the switch, I have had a lot of issues that I have mainly worked out myself. I have posted all of it on the Mint forum, but there hasn't been much help available there. I have been told that Mint 9 is based on the newest release of Ubuntu (Lucid Lynx), so I thought I would post over here to see if anyone could help me. The only thing that's still giving me fits are the 3 software programs above. Using k9copy and trying to burn directly to disc, I am getting the error that I took the screenshot of. I then burned it as an iso image and saved it, then tried to use k3b and brasero to burn it that way and got errors with both of those programs.

From k3b:

Devices
-----------------------
LITE-ON DVDRW LH-20A1S 9L08 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]
ATAPI DVD A  DH20A4P 9P55 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-23-generic

Used versions
-----------------------
cdrecord: 1.1.10

cdrecord
-----------------------
scsidev: '/dev/sr1'
devname: '/dev/sr1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW LH-20A1S  '
Revision       : '9L08'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 

From Brasero:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_E402FV.bin toc = none
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_1KZ2FV.bin toc = none
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=16
	-use-the-force-luke=tracksize:2246459
	-use-the-force-luke=tty
	-Z
	/dev/sr1=/home/phil/Desktop/Spirit Of 76.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/phil/Desktop/Spirit Of 76.iso of=/dev/sr1 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr1: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2842)

Thanks in advance for any help, I have been able to make a few copies of the iso image. I just don't understand why it's worked a few times and not all the time.

---

### Post by uzzo2 on 2010-07-24
Bump, Anybody got ANY ideas, Should I move this to another section? This seems to be a software issue, but I don't see a section for software.

---

### Post by pwebster25 on 2010-08-10
Same problem here.  I lost the ability to burn cds a couple weeks ago with an update in 9.10.  I finally gave up and upgraded to 10.04 but same problem.  I get what appears to be the same error messages when burning cds in Brasero.

I see references to this problem in the following posts:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1535920](http://www.uluga.ubuntuforums.org/showthread.php?t=1535920)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9674829](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9674829)
[http://ubuntuforums.org/showthread.php?t=1167212](http://ubuntuforums.org/showthread.php?t=1167212)
[http://ubuntuforums.org/showthread.php?t=1291337](http://ubuntuforums.org/showthread.php?t=1291337)

So far no solutions.  One thing that may be different for me is that this cd burner is an internal burner that is hooked up by USB (via an external USB cable).  Crazy, but that is required to burn from itunes in winxp in virtualbox.  It won't burn audio cds on an internal cd burner but it will on an external usb burner.  It has worked great like this for months and months.  Just stopped working and these same messages.  

I've tried the reasonable solutions in these other posts but still producing coasters or frisbees with these cds.

I appreciate your help.

---

### Post by wandalalakers on 2010-08-10
Try updating your version of kde by using the ppa.
[https://launchpad.net/~kubuntu-ppa/+archive/ppa](https://launchpad.net/~kubuntu-ppa/+archive/ppa)

This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources.

deb [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu) lucid main 

Signing key:
    1024R/8AC93F7A (What is this?) 
Fingerprint:
    E4DFEC907DEDA4B8A670E8042836CB0A8AC93F7A

---

### Post by pwebster25 on 2010-08-10
I have a hunch this is a kernal issue, so there might be something in the standard kernal that knocked out cd writing.  Any solutions for those on standard ubuntu 10.04, instead of kubuntu?

---

### Post by uzzo2 on 2010-08-10
I think I may have inadvertently figured my problem out last week. I used k3b and burned the image in the bottom drive. The next day, I tried to do the same thing and got different errors with every try. It was "cannot fixate disc and input/output error" mostly. So, just for the heck of it, I put the blank in the top drive and it burned it with no problem. At this point I was starting to believe I had a problem with the bottom burner. I took the cover off and decided to move the SATA cable to a different port. I usually use the top burner for the original and the bottom for the blank. I decided to switch up and put the original in the bottom and blank on top. I started up k9copy and it did its thing, no problem. Then I switched it up and did it with the one that I had been having problems with the blank in the bottom. I started k9 up and it backed up and burned a perfect copy. I haven't used it since then but I came to the conclusion that either the bottom burner is on its way out, or the the SATA cable wasn't making a good connection in the port it was in. Or, that port was just bad, hope this helps.

---

### Post by pwebster25 on 2010-08-11
I wish this helped me.  I am nearly certain that it isn't a hardware problem but I have no idea what to do next with the wodim or brasero software.

---

### Post by uzzo2 on 2010-08-11
I wish I could help you more, I used the suspect drive again today. My wife downloaded a movie from frostwire, an avi file. I used DeVeDe to convert it to an iso image and burned it with no problems.

---

