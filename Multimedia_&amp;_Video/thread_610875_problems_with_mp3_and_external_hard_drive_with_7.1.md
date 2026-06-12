---
title: "problems with mp3 and external hard drive with 7.10"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by Bart Ellebaut on 2007-11-12
Hey,
I have updated to Kubuntu Gusty Gibbon (7.10) and now I have trouble with my mp3 player and me external hard drive. They worked fine with the Feisty Fawn, but now my laptop doesn't recognize them, so I can't upload any music or my files for school.
what should I do?
thx

---

### Post by MrFSL on 2007-11-12
can you please post more information?

Make and model of external storage
Make model and possibly specs of computer system
Means of connecting the two - USB? Firewire?

Next after connecting the device, what is the output of:
```
dmesg | tail
```

---

### Post by mcki0154 on 2007-11-12
I have the same problem,

I have a maxtor 200 gb external drive
a toshiba satelite l-25 laptop

I started with Gutsy Gibbon and my drives worked fine, but for some reason they just stopped working.

Whenever I try to mount my drive I get the error messege

"record 5 has no file magic: input/output error failed to mount '/dev/sda1': input/output error NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware.  In the first place run chkdsk /f on windows then reboot into windows twice.  the usuage of the /f parameter is very important! if you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper directory, (e.g. /dev/mapper/nvidia_eahaabcc1).  Please see the 'dmraid' documentation for the details

I don't have windows, so I do not know what to do.  and on top of that I don't understand what any of these requests mean.

---

### Post by sciencectn on 2007-11-24
I also have the same problem; Ubuntu is not recognizing my Maxtor external hard drive no matter what I do. I ran dmesg | tail and it only recognized the internal hard drive.

---

### Post by mcki0154 on 2007-11-24
So here was what I found out....


My Maxtor HD was messed up because i happened to switch from an XP laptop to my Ubuntu OS WITHOUT safely removing the device before I physically removed the USB cord.  YOU MUST UNMOUNT/SAFELY REMOVE THE EXTERNAL HD BEFORE YOU PHYSICALLY DISCONNECT THE HD!!!!

Solutions.

I went through A LOT of Ubuntu forums (affiliated and non-affiliated) and tried nearly every solution possible that DID not require any access to an XP OS system.  But much to my dismay, I could not resolve the solution without access to a WINDOWS OS system, this is because the ever so important program for NTFS HD's (CHKDSK) can only be found on a WINDOWS OS. 

 Unless someone has made a LINUX alternative, for god's sake CANONICAL figure it out.  It is obvious that this is direly needed for anyone who does not dual boot their comp and uses an external NTFS HD.

1) get friend with WINDOWS to perfrom "CHKDSK" from the command line, a.k.a "Run" in the system toolbar.  

2) partition your current internal to facilitate a dual boot, and then do it yourself

3) make a hack for a linux CHKDSK, then tell the world!!!!

---

### Post by MrFSL on 2007-11-24
Not exactly the same but:
```
sudo apt-cache show ntfsprogs
```

> ntfsfix - Fix common filesystem errors and force Windows to check NTFS.


---

### Post by szaka on 2008-02-18
> **mcki0154 said:**
> "record 5 has no file magic: input/output 

This is typical when the disk is dying and starts to develop bad sectors (hardware faults).

---

