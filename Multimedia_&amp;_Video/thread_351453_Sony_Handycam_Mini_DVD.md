---
title: "Sony Handycam Mini DVD"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by Uncle Che on 2007-02-01
Have a video project at school at the moment. I need to get some video off of a mini DVD that my students made on a Sony Handicam. 

When I try to mount the /dev/hdc with sudo I get this error, both in terminal and on Nautilus

mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any hints on how to mount it or anything to get this project?

---

### Post by dviejo on 2007-11-13
Hey,

The same problem for me.

dmesg said:

UDF-fs: minUDFReadRev=250 (max is 201)
Unable to identify CD-ROM format.

 It appears can't recognize mini DVD file system. Do someone know what fs is used by handycam mini DVD?

---

### Post by wrathkeg on 2007-12-13
Maybe this  will help? 

[http://library.pantek.com/Mailing%20Lists/lists.ubuntu.com/ubuntu-users/07/08/3094.html]("http://library.pantek.com/Mailing%20Lists/lists.ubuntu.com/ubuntu-users/07/08/3094.html")

Haven't tried it yet (only just got home with my new handycam!)

WK

---

### Post by Sun_Wukong on 2008-02-17
Hi folks,

Those mini-DVD are in UDF v2.5 format
Right now, Linux only supports v2.01. A patch exists for kernel 2.6.20+.

You can read more [here]("http://en.wikipedia.org/wiki/Universal_Disk_Format") on Wikipedia.
I'm gonna have a look at some BSD to see if I can get my video files this way.

Take care
SW

---

