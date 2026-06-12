---
title: "could not read from resource"
date: 2008-09-29
forum: Multimedia Software
---

### Post by pshown on 2008-09-29
I have done what is outlined in the Official Documentation as it relates to playing DVD's with Totem Movie Player.The error description:cannot from resource is displayed. I have also installed gxine After installing I cannot go to the media tab for applications to use as the default player. It does not even show up as an option. All I want to be able to accomplish at this moment is to play a DVD. If/When other issues arise ai will deal with them accordingly.

---

### Post by mc4man on 2008-09-29
Why don't you go here and follow thru, should resolve your dvd playback issues. (a region should also have been set on the dvd drive **once**
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

As far as gxine, it should be added to the list of default choices *automatically*. It may of not been because at the time you installed it there was no .local/share/applications folder with a file mimeapps.list inside.
The easiest way to get that rolling is to go back to file management -> media and change a default choice. (change the cd audio and dvd movie )
Then exit out, start gxine up, close, and  go back and see if gxine is available as a choice. If not, it's trivial to add it to the proper line or add the proper line in mimeapps.list if not there.

Note:
mimeapps.list is a dynamic file where your file associations and default x-content choices are stored and or added (*can only be added manually following 'proper methods'*, one has to be *very careful* editing in there.
If need be I'll link or give you instructions on that.

---

### Post by pshown on 2008-09-29
OK I now have gxine showing uo as a media choice. When I  insert the DVD gxine opens an gives the error reading nav package. I went to the link you gave me and tried as best I could to follow the instructions. Running Totem movie player I am still getting the original error. I am a newbe at Linux and I really want to use it but if I can't get my multimedia functions working I will have to stay with Windows.

---

### Post by pshown on 2008-10-01
I have two SATA optical drives in my system. Could this be causing the DVD playback errors?

---

### Post by mc4man on 2008-10-01
Put a dvd in one of your drives and then run this from the terminal and post results from the terminal window
```
sudo lshw -C disk
```


edit:
> I have done what is outlined in the Official Documentation
assuming that yuo also ck.'ed that a region was set on the drives. Read sticky for a top of this forum for that and other relevant info.

> I have two SATA optical drives in my system. Could this be causing the DVD playback errors

In some cases sata dvd drives can be an issue, results from above would be informative in that regard

---

### Post by pshown on 2008-10-01
Here are the results of the terminal print out. The TSSTcorp drives listed are the Samsung SATA SH-203N optical drives. Any further help would be great.Thank you in advance.

pshown@pshown-desktop:~$ sudo lshw -C disk
[sudo] password for pshown: 
  *-disk:0                
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANK2390113
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration:ansiversion=5 signature=6b169308
  *-disk:1
       description: ATA Disk
       product: ST3500630AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 9QG4HEK7
       size: 465GiB (500GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=fd1c14c0-489b-448d-a982-1ede68d6fbd1
  *-disk
       description: ATA Disk
       product: Maxtor 34098H4
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: YAC6
       serial: M0000000
       size: 38GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=20d52521
  *-cdrom:0
       description: DVD-RAM writer
       product: CDDVDW SH-S203N
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: SB02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: DVD-RAM writer
       product: CDDVDW SH-S203N
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@5:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: MP830Storage
       vendor: Canon
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdd
       version: 0113
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdd
pshown@pshown-desktop:~$ sudo lshw -C disk

---

### Post by pshown on 2008-10-01
Hey MC4man,
With your help and reviewing the Sticky more closely I can now play DVD's.

Thanks For Your Help

---

