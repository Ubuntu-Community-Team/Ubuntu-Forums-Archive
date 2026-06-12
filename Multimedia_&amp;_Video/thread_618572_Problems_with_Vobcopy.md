---
title: "Problems with Vobcopy"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by MadSavage on 2007-11-20
I'm sorry if this is the wrong area to post this question, but I did some research, and couldn't really find answers to my questions.
I recently received a larger hard drive, and decided to back up some of my older DVD's. I know this is "iffy" territory, but I would still like to know a few things...Both of my questions are concerning vobcopy, only. (I also have the necessary libraries for copy protection.)
First, I tried a program In windows. I forget the program, but it took about 2 hours for me to copy one of my DVD's to the hard drive, and then I had to make it an iso, which took a little time, as well. Anyway...
Using vobcopy, I created a copy of one of my DVD's (a 3 Gig video, by the way), and it took two DAYS to copy, and it didn't copy the entire disk, but it DID "finish the process." 

Could anyone tell me why it took so long, and why it didn't complete the process (since i have ample space on my hard drive.)

I hope I can get some help, and thanks in advance.

***After searching Ubuntu Community Docs, I discovered the solution. It is an encryption playback issue. When I installed livdvdcss2, I didn't realize it didn't install. In one of the community docs, it states that after installing libdvdread, you need to install(?) libdvdcss2 from the libdvdread directory. (Not sure exactly why...I really am kind of new to Linux.)

Thanks for your replies, I appreciate your help!

---

### Post by magicfab on 2007-11-20
Very hard to tell unless you provide exact status / error messages. Did you look at the output of dmesg ? You may find some hint there regarding how the DVD was mounted, etc.

---

### Post by MadSavage on 2007-11-20
> **magicfab said:**
> Very hard to tell unless you provide exact status / error messages. Did you look at the output of dmesg ? You may find some hint there regarding how the DVD was mounted, etc.

I will wait until It's finished it's "new" try at copying, and see if there's an error. The first time I tried it, vobcopy appeared to finish. It didn't give an error output at all, It just looked like it had completed. When I tried to create the ISO, on the other hand,mkisofs claimed it was not dvd-video files, or some such (I searched the directory, and found only half of the files had actually been copied with vobcopy.)

When it finishes this copy, I will report back with more information. Thank you.

---

### Post by mc4man on 2007-11-20
you should probably run vobcopy with a  -v  in the command, that way you'll get a verbose output in the terminal while it's running. If the disk is either phyically damaged or structure protected you will see read  (block) errors. The default for vobcopy is up to 10 read attempts per unreadable sector so the time to complete a rip of a disk with a number of such errors can be quite long. Otherwise a 7+gb disk should rip in about 12- 15 min.

---

### Post by MadSavage on 2007-11-21
> **mc4man said:**
> you should probably run vobcopy with a  -v  in the command, that way you'll get a verbose output in the terminal while it's running. If the disk is either phyically damaged or structure protected you will see read  (block) errors. The default for vobcopy is up to 10 read attempts per unreadable sector so the time to complete a rip of a disk with a number of such errors can be quite long. Otherwise a 7+gb disk should rip in about 12- 15 min.

Yes, I use verbose, but I don't get any errors. However, here is the output from dmesg after the copy finishes.

> [34432.898439] ide: failed opcode was: unknown
[34432.899109] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[34432.899118] end_request: I/O error, dev hdc, sector 4696
[34432.920924] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[34432.920935] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[34432.920939] ide: failed opcode was: unknown
[34432.921616] hdc: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[34432.921624] end_request: I/O error, dev hdc, sector 4700

Now, in Gutsy, I can't play DVD's any more. In Feisty I had no problems, however. I'm assuming that because I can't play DVD's, that, perhaps, that may be where the origin of this problem is. Again, not too sure...I only switched 99% to Ubuntu a month ago, and am relatively new, especially to major video problems. When I try to open a DVD in totem, or vlc, I get the same error "Cannot read from source." However, I can view the contents of, and check chapters/titles of the disks just fine. Any help getting vobcopy to work would be appreciated; I've already had to scrap/re-purchase a dozen DVD's because of scratches, and would rather watch them from my computer than have to pay for them again...

---

### Post by mc4man on 2007-11-21
You should resolve your dvd playback issue first, there are dozens of threads related to that, you may find a problem similar to yours and hopefully a solution. The errors shown in dmesg are somewhat generic and could be caused by a number of things.
Vlc only needs libdvdcss installed for playback of encrypted disks so an obvious question is do you have it installed?
I'm also wondering if you upgraded from feisty to gutsy or do you have a fresh install?

---

### Post by MadSavage on 2007-11-21
> **mc4man said:**
> Vlc only needs libdvdcss installed for playback of encrypted disks so an obvious question is do you have it installed?
I'm also wondering if you upgraded from feisty to gutsy or do you have a fresh install?
 It is a fresh Gutsy Install. And yes, I installed libdvdcss first. (I discovered that I needed it at the beginning of my venture because I was sure I would have copy protected DVD's to backup.) 
So now, I only need to see if there's a difference between Feisty/Gutsy that could have caused my DVD problem. Hopefully, that is the answer, because an old ISO backup I had from Feisty still burned fine, and played fine afterwards on my home theater. Thanks again for your help, it is most definitely appreciated.

---

