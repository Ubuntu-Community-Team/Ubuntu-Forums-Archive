---
title: "Really confused .."
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by vikrant82 on 2007-09-30
Hi,

I am really confused with what's going on here. I have three kinds of DVDs .

1. Automatically Mounts perfectly. Icon on desktop. No issues
2. Cannot be mounted automatically. 
      Has to do sudo mount /media/cdrom, and it mounts fine ...
3. Cannot be mounted whatever hell i do.
 
All of these DVDs were written in UDF with the same writer. 3rd type was written using Cheetah burner in XP. Others in Ubuntu using Gnome Baker.

However all of these mount perfectly, in a win xp like a roar.

Another thing, for the 3rd type , run my virtual box, load cdrom for guest XP, and there roars my dvd again. 

eh!! 

Ok. i knw what's coming next, fstab and log entries .... 
Have tried almost everything for my fstab enry, auto, udf, iso9660 utf8 ...

Logs read like this for third type :
```

Oct  1 01:11:04 localhost kernel: [ 3264.368000] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct  1 01:11:04 localhost kernel: [ 3264.368000] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
Oct  1 01:11:04 localhost kernel: [ 3264.368000] sr 0:0:1:0: [sr0] ASC=0x10 <<vendor>> ASCQ=0x90
Oct  1 01:11:04 localhost kernel: [ 3264.368000] end_request: I/O error, dev sr0, sector 0
Oct  1 01:11:04 localhost kernel: [ 3264.368000] Buffer I/O error on device sr0, logical block 0
Oct  1 01:11:10 localhost kernel: [ 3270.280000] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Oct  1 01:11:10 localhost kernel: [ 3270.280000] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
Oct  1 01:11:10 localhost kernel: [ 3270.280000] Info fld=0x0
Oct  1 01:11:10 localhost kernel: [ 3270.280000] sr 0:0:1:0: [sr0] Add. Sense: Tracking servo failure
Oct  1 01:11:10 localhost kernel: [ 3270.280000] end_request: I/O error, dev sr0, sector 0
Oct  1 01:11:10 localhost kernel: [ 3270.280000] Buffer I/O error on device sr0, logical block 0

```
Alright looks like a hardware issue ? But how it flies on WinXP ? And why only this particular new scratchless Sony DVD.

[ Set out to refit my cdrom, and broke my lcd hinges ] :(

---

