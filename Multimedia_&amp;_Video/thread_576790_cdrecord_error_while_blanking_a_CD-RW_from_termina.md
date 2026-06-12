---
title: "cdrecord error while blanking a CD-RW from terminal"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by nickagian on 2007-10-15
Hello!

 I`m trying to blank a CD-RW from the terminal with the command

```
 cdrecord dev=ATA:0,1,0 -v -eject speed=4 blank=all
 
```

The above gives me always this result :

```
TOC Type: 1 = CD-ROM
scsidev: 'ATA:0,1,0'
devname: 'ATA'
scsibus: 0 target: 1 lun: 0
Linux sg driver version: 3.5.27
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... giving up.
wodim: Invalid argument. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
 
```

I have also tried to unmount the device first and then do the same, but the result doesn`t change.

My DVD-RW device is /dev/hdd and mounted to /media/cdrom1

The command ```
  cdrecord dev=ATAPI -scanbus 
``` gives me back

```
 scsibus0:
        0,0,0     0) 'SONY    ' 'DVD-ROM DDU1622 ' 'AS72' Removable CD-ROM
        0,1,0     1) 'SONY    ' 'DVD RW DW-D22A  ' 'BYS2' Removable CD-ROM
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
 
```

I have googled about similar situations but I am not sure what should I do to fix it.

However, the same task with K3b seems to work fine... :mad: 

I would appreciate some help with this ...

P.S. : The same happens when I try to burn something on a CD.

---

### Post by paxmark1 on 2007-10-16
I could be wrong, but standard k3B uses wodim now instead of cdrecord.

See if wodim -scanbus yields the same results as cdrecord.  

wodim quite picky and flakey with my slim cheap APOS internal dvd-rw, but works with my LG external dvd-rw/  

Wodim appears to be the new back end tool for all flavours Debian, but other than a man page there is not much info out there about it.  

I am checking out burning .isos and such on cd-rw via the command line with wodim but need to buy some -dvd+rw to try growisofs and wodim out on dvds, I have made too many coasters with k3b and wodim to try it anymore with my APOS dvd-rw.

---

### Post by nickagian on 2007-10-16
> **paxmark1 said:**
> I could be wrong, but standard k3B uses wodim now instead of cdrecord.

See if wodim -scanbus yields the same results as cdrecord.  

wodim quite picky and flakey with my slim cheap APOS internal dvd-rw, but works with my LG external dvd-rw/  

Wodim appears to be the new back end tool for all flavours Debian, but other than a man page there is not much info out there about it.  

I am checking out burning .isos and such on cd-rw via the command line with wodim but need to buy some -dvd+rw to try growisofs and wodim out on dvds, I have made too many coasters with k3b and wodim to try it anymore with my APOS dvd-rw.

Thanks for the reply! I tried to use wodim after reading your post but the result was the same.

After that I tested some other things and found that the problem was at the definition of the parameter 'dev'. When I changed the 

```
cdrecord dev=ATA:0,1,0 -v -eject speed=4 blank=all
```

to

```
cdrecord dev=/dev/hdd -v -eject speed=4 blank=all
```

then everything was fine! :)

One last tip for others who may read this thread for help. Before trying to blank a CD via cdrecord or wodim, _first unmount the device_!

---

