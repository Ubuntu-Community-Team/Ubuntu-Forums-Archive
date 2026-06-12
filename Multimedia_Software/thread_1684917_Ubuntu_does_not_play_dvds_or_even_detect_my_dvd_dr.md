---
title: "Ubuntu does not play dvds or even detect my dvd drive"
date: 2011-02-09
forum: Multimedia Software
---

### Post by TechHippo on 2011-02-09
today, I installed Ubuntu 10.10 and my dvd drive wont work. it doesnt display in disk utility. or play dvds. anysuggestions?

---

### Post by tommcd on 2011-02-09
Have you tried inserting a data DVD, or even the Ubuntu CD that you used to install Ubuntu, into the DVD drive to see if it mounts?

For playing encrypted DVD movie discs you need to install **libdvdcss2**. See this on proprietary codecs: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)
To see if the DVD drive is detected, open a terminal and run: ```
dmesg | tail
``` And note the last output. Then insert a DVD or a CD into the drive and run *dmesg | tail* again. The output should indicate that a disc was detected. For example, I get this when I insert a music CD into my DVD drive:
```
bash-4.1$ dmesg | tail
sr 8:0:0:0: [sr0] Result: hostbyte=0x00 driverbyte=0x08
sr 8:0:0:0: [sr0] Sense Key : 0x5 [current] 
sr 8:0:0:0: [sr0] ASC=0x64 ASCQ=0x0
sr 8:0:0:0: [sr0] CDB: cdb[0]=0x28: 28 00 00 00 00 20 00 00 02 00
end_request: I/O error, dev sr0, sector 128
sr 8:0:0:0: [sr0] Result: hostbyte=0x00 driverbyte=0x08
sr 8:0:0:0: [sr0] Sense Key : 0x5 [current] 
sr 8:0:0:0: [sr0] ASC=0x64 ASCQ=0x0
sr 8:0:0:0: [sr0] CDB: cdb[0]=0x28: 28 00 00 00 04 20 00 00 02 00
end_request: I/O error, dev sr0, sector 4224
```
Note that **sr0** is my DVD drive.

---

### Post by Jonners59 on 2011-02-26
Interesting!

I have two Drives on my machine I am using at the moment.  I am having trouble with a couple of CDs with windows apps on. One works on most machines but not others and the other will not work on any.  The drive will not mount being not recognised....

I ran your cmd ```
dmesg | tail
``` with the offending CD in one of the drives and this is what I got:



```
[ 2630.811833] sr 1:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 2630.811849] end_request: I/O error, dev sr0, sector 0
[ 2630.811856] Buffer I/O error on device sr0, logical block 0
[ 2630.811863] Buffer I/O error on device sr0, logical block 1
[ 2630.811869] Buffer I/O error on device sr0, logical block 2
[ 2630.811874] Buffer I/O error on device sr0, logical block 3
[ 2630.811879] Buffer I/O error on device sr0, logical block 4
[ 2630.811884] Buffer I/O error on device sr0, logical block 5
[ 2630.811889] Buffer I/O error on device sr0, logical block 6
[ 2630.811894] Buffer I/O error on device sr0, logical block 7

```

And in the other drive...

```
[ 2760.748598] end_request: I/O error, dev fd0, sector 0
[ 2760.748605] Buffer I/O error on device fd0, logical block 0
[ 2772.925052] end_request: I/O error, dev fd0, sector 0
[ 2775.758999] [UFW BLOCK] IN=eth0 OUT= MAC=00:14:85:26:9c:03:00:50:7f:9a:e1:78:08:00 SRC=192.168.1.1 DST=192.168.1.62 LEN=156 TOS=0x00 PREC=0x00 TTL=255 ID=14896 PROTO=UDP SPT=514 DPT=514 LEN=136 
[ 2785.088547] end_request: I/O error, dev fd0, sector 0
[ 2785.088582] FAT: Unrecognized mount option "utf8" or missing value
[ 2791.230740] [UFW BLOCK] IN=eth0 OUT= MAC=00:14:85:26:9c:03:00:50:7f:9a:e1:78:08:00 SRC=192.168.1.1 DST=192.168.1.62 LEN=117 TOS=0x00 PREC=0x00 TTL=255 ID=14904 PROTO=UDP SPT=514 DPT=514 LEN=97 
[ 2797.265139] end_request: I/O error, dev fd0, sector 0
[ 2809.436584] end_request: I/O error, dev fd0, sector 1
[ 2809.436610] qnx4: unable to read the superblock
```

So what is going wrong do you think...?

---

### Post by tommcd on 2011-02-27
> **Jonners59 said:**
> 
 I am having trouble with a couple of CDs with windows apps on. One works on most machines but not others and the other will not work on any.  The drive will not mount being not recognised....
I ran your cmd dmesg | tail with the offending CD ...
Well, as near as I can tell, the system seems to be aware of the disk, but all of these lines seem to indicate that the system can not read the problematic disc:
```

630.811849] end_request: I/O error, dev sr0, sector 0
[ 2630.811856] Buffer I/O error on device sr0, logical block 0
[ 2630.811863] Buffer I/O error on device sr0, logical block 1
[ 2630.811869] Buffer I/O error on device sr0, logical block 2
...

```
If the problematic disc will not mount on *any* system, then I would conclude that the disc itself is faulty.

Does the problematic disc automount on a Windows system?
If it does, the I would try copying the Windows apps to a flash drive, or another CDR. Then see if Ubuntu can find the apps on the flash drive or different CDR.

If the disc will not even mount on a Windows system, then it is safe to conclude that the CD is defective.

---

### Post by Jonners59 on 2011-03-11
OK, that turned out to be a faulty disc, BUT the Windows MS Office 2007 is not faulty.  It works fine on Windows machines and on other PCs running Ubuntu/Wine/Crossover...

Tried copying the CD on to stick, makes no difference.

Ideas?

---

### Post by tommcd on 2011-03-11
> **Jonners59 said:**
> OK, that turned out to be a faulty disc ...
Well, if the disc is bad, there is not much you can do as far as I know. Perhaps try cleaning the disc, then try mounting it on different computers if you can. Sometimes a bad disc will mount sporadically. You may get lucky and get the disc to mount.

---

