---
title: "DVD burning impossible since upgrade to intrepid"
date: 2009-03-11
forum: Multimedia Software
---

### Post by fredsaule on 2009-03-11
Hello everybody,

Since my upgrade to 2.6.27-11-generic, I'm experiencing unstable situations : it is impossible to burn anything, whatever the soft used (Nero, Brasero or gnomebaker).

Symptom : the burning starts, then hangs for ever (until I reboot to take the DVD). On the DVD I find the structure of what Iwanted to burn, but the data is not there.
I have dumped a serious number of DVD to this days, making tests.

First some basic info :

My kernel is 2.6.27-11-generic.

```
$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'PLEXTOR' 'DVDR   PX-760A'
-------------------------------------------------------------------------

$ wodim --scanbus
scsibus2:
	2,0,0	200) 'PLEXTOR ' 'DVDR   PX-760A  ' '1.03' Removable CD-ROM
	2,1,0	201) *
	2,2,0	202) *
	2,3,0	203) *
	2,4,0	204) *
	2,5,0	205) *
	2,6,0	206) *
	2,7,0	207) *

$ wodim -version
Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd 
Wodim 1.1.8
Copyright (C) 2006 Cdrkit suite contributors
Based on works from Joerg Schilling, Copyright (C) 1995-2006, J. Schilling
```

If I try to stop the burning (which does not burn anything) I have the following message :

```
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

During the so called burning, my syslog says:

```
Feb 21 10:00:17 fredsaule kernel: [ 2171.792531] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 21 10:00:17 fredsaule kernel: [ 2171.792537] sr 2:0:0:0: [sr0] Sense Key : Blank Check [current] 
Feb 21 10:00:17 fredsaule kernel: [ 2171.792540] sr 2:0:0:0: [sr0] Add. Sense: No additional sense information
Feb 21 10:00:17 fredsaule kernel: [ 2171.792545] end_request: I/O error, dev sr0, sector 0
Feb 21 10:00:17 fredsaule kernel: [ 2171.792549] Buffer I/O error on device sr0, logical block 0
Feb 21 10:00:17 fredsaule kernel: [ 2171.794052] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Feb 21 10:00:17 fredsaule kernel: [ 2171.794057] sr 2:0:0:0: [sr0] Sense Key : Blank Check [current] 
Feb 21 10:00:17 fredsaule kernel: [ 2171.794061] sr 2:0:0:0: [sr0] Add. Sense: No additional sense information
Feb 21 10:00:17 fredsaule kernel: [ 2171.794065] end_request: I/O error, dev sr0, sector 0
Feb 21 10:00:17 fredsaule kernel: [ 2171.794068] Buffer I/O error on device sr0, logical block 0
```

On the other side Gnomebaker is VERY unstable (multiple drag&drops end up in crash of the window).

I have no solutions... HELP !

SeeYa
FREDSAULE

---

### Post by fredsaule on 2009-03-12
WARNING : I edit my post for a bad news : my firmware upgrade did not fix my problem.



Alleluja !!

That was difficult, but the problem is solved : it was coming from the firmware version of the DVDROM !!

This cleans the new kernel of any flaw : the problem was coming from the delay between the evolution of the kernel and the age of my DVD's firmware (as a linux user be careful with Plextor products).

A last word : I was saved by the live DVD of Windows (called BoulDows in the french version, but it's also known as Windows XPE). All firmwares flashing apps 
are running on Windows only (very few easy and safe solutions running on Linux!!). For the flashing procedure I could boot on the live windows, then plug my USB key (containing my flashing app), and trigger the flash procedure.

As a result I could upgrade from 1.03 to 1.07. Now I can burn as I used to, with the soft I want.

Hope this will help someone !

FREDSAULE

---

### Post by tekknokrat on 2009-03-31
I have also this issue with intrepid and with all kernels 2.6.27-xx and higher.

My drive is plextor 712sa (sata) attached to either onboard via (using sata_via) or pci silicon image controller (using sata_sil).

The firmware was updated to latest for this drive 1.0.9 ([http://www.plextor.com/english/support/downloads/firm_712.htm](http://www.plextor.com/english/support/downloads/firm_712.htm)).

Should this really drive specific?

---

### Post by fredsaule on 2009-04-01
Well... Here is the truth : My problem is still not solved.

My final analysis is the following:
_ the firmware upgrade has not changed my situation,
_ when I use a former kernel it works,
_ my logical conclusion is that a module is loaded with the new kernel which is not supported by my DVD burner.

_ in my lasts tests I have tried to plug another DVD burner (in USB) and the result was deadly (nothing could be burnt). Which does not seem normal (in ubuntu it is possible to burn on a USB drive!).

My next step is to log in an old kernel, list the loaded modules, make the same with my updated kernel, and list the difference. That should help to identify the rotten module.

the other solution is to wait for the new ubuntu release and light candles for an upgrade solving the issue.

If you have any idea, please post your actions !

FREDSAULE

PS : for my PX-760A there is no 1.09 firmware available.

---

### Post by tekknokrat on 2009-04-01
> **fredsaule said:**
> Well... Here is the truth : My problem is still not solved.

My final analysis is the following:
_ the firmware upgrade has not changed my situation,
_ when I use a former kernel it works,
_ my logical conclusion is that a module is loaded with the new kernel which is not supported by my DVD burner.

_ in my lasts tests I have tried to plug another DVD burner (in USB) and the result was deadly (nothing could be burnt). Which does not seem normal (in ubuntu it is possible to burn on a USB drive!).

My next step is to log in an old kernel, list the loaded modules, make the same with my updated kernel, and list the difference. That should help to identify the rotten module.

the other solution is to wait for the new ubuntu release and light candles for an upgrade solving the issue.

If you have any idea, please post your actions !

FREDSAULE

PS : for my PX-760A there is no 1.09 firmware available.

Hi Fredsaule,

For me the first step was also to update firmware but this also did not solve my issue so I was kind of annoyanced when I read that you had success this way. I also dropped a mail to plextor pointing them to this thread - I was to impatient awaiting your answer. But so we have information from upstream.

I have good news and bad news for you.
Bad news first, the problem still exists with 2.6.29 kernel, I had a test within fedora and same message, same problem.
Good news there are also other people having this issue.

Its not some issue with a another module loaded but some changes in libata on which these modules depends. For me its the same issue with sata_sil / sata_via. That there are also problems with usb writers sounds strange to me.

As i am using Fedora by now these are the bugs i am curently monitoring:

 - [https://bugzilla.redhat.com/show_bug.cgi?id=459364](https://bugzilla.redhat.com/show_bug.cgi?id=459364)
 - [https://bugzilla.redhat.com/show_bug.cgi?id=493080](https://bugzilla.redhat.com/show_bug.cgi?id=493080)

---

### Post by fredsaule on 2009-04-01
Do you think the problem is solved through buying a different DVD burner (different brand, but still SATA) ?

Would you have a chance to try and burn a DVD through a USB burner ?

Rgds,
FREDSAULE

---

### Post by tekknokrat on 2009-04-01
> **fredsaule said:**
> Do you think the problem is solved through buying a different DVD burner (different brand, but still SATA) ??

Rgds,
FREDSAULE

Dont think so, also you stated that you tried with usb version was this another dvd writer?

Google also tells me that other writers also involved.

[http://www.google.de/search?hl=de&q=](http://www.google.de/search?hl=de&q=)[sr0]+Sense+Key+%3A+Blank+Check+[current]+&btnG=Suche&meta=

---

### Post by fredsaule on 2009-04-02
Yes. To be more specific, as my internal DVD burner could not burn properly with the new kernel I thought I could use a USB DVD burner (in a 5 1/4 external USB case) to a avoid the problem. I my mind the problem is related to SATA management. Using a USB burner I could avoid the problem.

It was indeed a different DVD burner (a Pioneer DVR-115DBK connected throught IDE to the USB port).

But the result was the same : burning starts, then hangs... then I need to reboot to collected a disposable DVD (file structure, but no data). Even worst : I could not burn with the USB burner, even using the old kernel ! If you have the chance to test my experience on your side I would be interested in the result.

Rgds,
FREDSAULE

---

### Post by 4Foot on 2009-04-12
I had this problem with my last machine and Ubu 7.10. It worked like a dream with my Plextor internal until I changed DVD Media and then I would get an immediate hang of the burning process. 

I went out and bought a Sony burner and still no joy. If I downgraded to Ubu 7.04 it worked like a charm. Tried and had the same problem with Mint 5, Fedora 9 and was quite convinced that it was some kind of kernel specific problem. I also upgraded my PC to a new motherboard ( Asus ) and cpu ( AMD Phenom ) during this time.

I was overjoyed to find my internal Sony burner working perfectly when I moved up to Ubu 8.10 for the last few months. However last week I changed DVD Media again, simply a new stack of Fuji DVD+R's for an older stack of the same brand and kind, and the burning process choked immediately. Same old problem. 

I installed 9.04 hoping the new kernel would fix things but no joy. I had a few of the older Fuji's around and they still work just fine in the Beta Jaunty on my internal Sony but none of my new Fuji's or two packs of Memorex DVD+R's that I bought to test with will burn internally. They all give me roughly the same message with occasional bits of extra information like " SCSI problems".

I have an old Pioneer burner which I put in a 5 1/4" USB/Firewire box and it works perfectly with all the media I can throw at it using the USB port.

I have no solution but am anxiously awaiting the final 9.04 release of Ubu or it that fails to fix this then the release of Fedora 11 in a few weeks so I can give that a try.

In the meantime I will continue to monitor this problem in the forums as there are a lot of folks having this problem and as you can see from my story it goes back several releases. I hope someone can figure out a solution.

Cheers

4Foot

---

### Post by 4Foot on 2009-04-20
Update on burning problem.

Beta of Jaunty and RC of Jaunty both choke on same DVD Media that froze my machine before. I hit on an older stack of media and they work fine at 16X but still no joy with two other brands/batch.

I am leaning towards some problem with the recognition of the media by the software. There seems to be a problem with all of my UBU burner programs not being able to properly read the media info imbedded in the disk itself. There must be some kind of table that the burning software refers to once it reads this info so that it can set the proper parameters for burning.

It cannot be the burner, different media in same burner works fine. Ditto on the burning portion of the software itself, as the same programs work with different media.

If anyone has any ideas how to update this media library I sure would appreciate a solution.

Cheers

4Foot

---

### Post by tekknokrat on 2009-04-21
Hi 4foot,

can we clarify that we are not talking about different problems in this scope. My issue appears with different chipsets via,sil,usb and different burner (both plextor so far).
When I have a blank disc (regardless if cd/dvd) inserted on bootup I get the error message in dmesg. Burning stalls and bricks media.

Can you please post output of your dmesg. Should look like this:

> cdrom: This disc doesn't have any tracks I recognize!
end_request: I/O error, dev sr0, sector 0
Buffer I/O error on device sr0, logical block 0
end_request: I/O error, dev sr0, sector 0
Buffer I/O error on device sr0, logical block 0


Cheers,
Gunnar

---

### Post by BikeHelmet on 2009-04-26
Hello. I have the same issue as you, but for my SATA hard drives.

[See Here]("http://ubuntuforums.org/showthread.php?p=7154870#post7154870")

I tried earlier kernels, but same issue.

```
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.
```

Same Buffer I/O errors, too. I don't know how to fix it - I may buy a SATA PCI card and try running the drives off it, since I know the drives/cables/ports/controller are fine. (they work great in Windows)

---

### Post by fredsaule on 2009-05-10
Hello,

Did my upgrade to Jaunty. My burning issue is solved... finally.

Thx to all the answers.

Rgds
FREDSAULE

---

### Post by 4Foot on 2009-05-10
> **tekknokrat said:**
> Hi 4foot,

can we clarify that we are not talking about different problems in this scope. My issue appears with different chipsets via,sil,usb and different burner (both plextor so far).
When I have a blank disc (regardless if cd/dvd) inserted on bootup I get the error message in dmesg. Burning stalls and bricks media.

Can you please post output of your dmesg. Should look like this:



Cheers,
Gunnar

Gunnar:

I apologise but I seemed to have misssed notice of your post and now two weeks have gone by without my replying to your question.

I am not sure what you mean by "blank disk inserted on bootup". Do you mean on bootup of the computer or of the software burning program? I don't get any error message at either of those times, but only after I have begun the burning process. Disk rotates, lights flash, hope springs from my heart and then the man behind the curtain is revealed and The Wizard's voice says, "Ignore the man behind the curtain" , or "error", or "something is very, very wrong here". None of which is the least bit enlightening.

I don't know quite how to summon dmesg but if you tell me I will try. For now, I am just using my external burner with my Memorex (-R's by the way, not +'s) and putting Fujifilm in my internal burner where they work just fine.

Some things, particularly in the computer world, defy understanding and just require acceptance. I am at peace with my burners and Jaunty. For now.

4Foot :)

---

### Post by efsandino on 2009-05-10
Hi i have the same problem my DVD blank media is not recognize in my UBUNTU 8.10 Intrepid Kernel 2.6.27.11-generic and i remember i could burn dvd of the same media, but i the dvd is burned off course it reads... how to solve the problem ????

---

### Post by efsandino on 2009-05-11
Listen i have restarted and the DVD Blank was recognized but when try to burn i get these errors:

Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_LBU1TU toc = nil
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_start_progress
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /media/D2/quemar/vicenteFernandez.iso (size = -1799473152)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage Called brasero_job_set_progress (0,001937)
BraseroChecksumImage Called brasero_job_set_progress (0,003985)
BraseroChecksumImage Called brasero_job_set_progress (0,007294)

BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage setting new checksum (type = 0) d2ccbb53282bd3d58374a8938fd136bb ( before)
BraseroChecksumImage finished track successfully
BraseroChecksumImage stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
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
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=3
	-use-the-force-luke=tracksize:1218503
	-use-the-force-luke=tty
	-Z
	/dev/scd0=/media/D2/quemar/vicenteFernandez.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/media/D2/quemar/vicenteFernandez.iso of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: /dev/scd0: reserving 1218503 blocks
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stdout:           0/2495494144 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/2495494144 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=3h/WRITE ERROR]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Error no manejado, abortando"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Error no manejado, abortando (brasero_burn_record burn.c:2524)

---

### Post by mbirth on 2009-05-15
I have the same problem with a Samsung SE-T084M (external USB burner). It worked flawlessly with Intrepid under both: Nero and Brasero. Since Jaunty Beta, every try to burn any DVD with Nero completely hangs my notebook at 1% with some unspecific SCSI error. I then can only power-cycle the whole thing.

Trying to LightScribe a disc brings the message "The disc is not properly aligned or invalid disc.".

My last try with Brasero is some weeks ago. AFAIR it also aborts shortly after Lead-In but I'm not sure whether it also hung my notebook.

The burner already has the latest firmware. Maybe I'll try to check whether the media catalog of the burner is up-to-date (using [MCSE]("http://forum.rpc1.org/viewtopic.php?f=2&t=41228&st=0&sk=t&sd=a&start=125")).

I hope this will be fixed soon...

Cheers,
  -mARKUS

---

### Post by efsandino on 2009-05-15
Finally i could burn but for that i just updated my UBuntu 8.10 to Ubuntu 9.04 with the alternate cd installation an now is ok... THis recognize my blank DVD and i could burn, i hope if there is some new upgrade is will be still working but first i will burn all my info and then try these updates..

---

### Post by tekknokrat on 2009-05-15
> **4Foot said:**
> Gunnar:

I apologise but I seemed to have misssed notice of your post and now two weeks have gone by without my replying to your question.

I am not sure what you mean by "blank disk inserted on bootup". Do you mean on bootup of the computer or of the software burning program? I don't get any error message at either of those times, but only after I have begun the burning process. Disk rotates, lights flash, hope springs from my heart and then the man behind the curtain is revealed and The Wizard's voice says, "Ignore the man behind the curtain" , or "error", or "something is very, very wrong here". None of which is the least bit enlightening.

I don't know quite how to summon dmesg but if you tell me I will try. For now, I am just using my external burner with my Memorex (-R's by the way, not +'s) and putting Fujifilm in my internal burner where they work just fine.

Some things, particularly in the computer world, defy understanding and just require acceptance. I am at peace with my burners and Jaunty. For now.

4Foot :)

I mean bootup of the system. But it doesnt matter if you input cdrom/dvd later only that the message could be seen in boot log (If you can see booting messages at start)

Steps to reproduce that you have the issue:
===========================================

That apply to 4Foot and all others

 - insert blank dvd/cdrom (dont use a R/W for testing this)
 - look in dmesg output in /var/log/messages or dmesg cmd

$ dmesg | grep sr[0-9]

Should give you output of initial poster (fredsaule)

Please don't keep on posting burning problems when you dont have this errors in dmesg log as this thread originates to this specific problem! Thanks.

---

### Post by 4Foot on 2009-05-15
Tekknokrat:

My reading of the output in dmesg is a little bit fuzzy but I am willing to conclude that my problem is NOT the exact same problem at that of fredsaule, the original poster. I did not know that when I started posting in this thread or I would not have interfered with fredsaule's quest for answers. All I knew was that the header of the thread indicated that someone was having problems burning DVD's after an upgrade. In that, our problems were identical, so I added my two cents in hope of aiding in finding a solution to both our problems in the spirit of collaboration which makes forums like this useful and effective. I apologise if my chipping in got in the way. I will unsubscribe from this thread and seek answers elsewhere, thank you very much for your help.

4Foot

---

### Post by tekknokrat on 2009-05-15
> **4Foot said:**
> Tekknokrat:

My reading of the output in dmesg is a little bit fuzzy but I am willing to conclude that my problem is NOT the exact same problem at that of fredsaule, the original poster. I did not know that when I started posting in this thread or I would not have interfered with fredsaule's quest for answers. All I knew was that the header of the thread indicated that someone was having problems burning DVD's after an upgrade. In that, our problems were identical, so I added my two cents in hope of aiding in finding a solution to both our problems in the spirit of collaboration which makes forums like this useful and effective. I apologise if my chipping in got in the way. I will unsubscribe from this thread and seek answers elsewhere, thank you very much for your help.

4Foot

Thanks 4Foot, 
For your help - try to burn with commandline tool e.g. for DVD (growisofs) and see if there's appearing an error. This gives more specific output:

```
growisofs -dvd-compat -Z /dev/sr0=/media/D2/quemar/vicenteFernandez.iso
```

Than search for messages similar to the error messages of growisofs (if you get them) in forum or open a new one thread.

---

### Post by mbirth on 2009-05-15
After inserting a blank (new) DVD-RW:

```

[99967.069484] cdrom: This disc doesn't have any tracks I recognize!
[99967.372650] end_request: I/O error, dev sr1, sector 0
[99967.372660] Buffer I/O error on device sr1, logical block 0
[99967.374637] end_request: I/O error, dev sr1, sector 0
[99967.374642] Buffer I/O error on device sr1, logical block 0

```

Same comes when inserting a blank DVD+R.

Cheers,
  -mARKUS


P.S.: I was able to format the DVD-RW using growisofs, but when it tried to burn actual data onto it, it failed. From reading the dmesg output, it looks like the something reset the USB connection to the burner. There are several "usb-storage: device found..." messages between the "Buffer I/O error"s.

P.S.[2]: Now after power-cycling the burner and inserting the formatted DVD-RW, there was no message of non-recognized tracks and growisofs now burns my iso file.

P.S.[3]: Okay, I don't know why, but growisofs now burns any ISO I throw at it (using "growisofs -Z /dev/sr1=image.iso"). Even with the "no tracks recognized" message. Will try Nero again...

P.S.[4]: So, Nero works ... again. Seems to be the 2.6.28-12 kernel which made things work again. (Installed it 2 days ago and didn't try burning since then.)

---

