---
title: "Digital audio output detected but not working"
date: 2008-07-17
forum: Mythbuntu
---

### Post by GyroTech on 2008-07-17
Hi all,

I have an MSI Media Live box and have followed instructions on this site and on the MythTV wiki to get the digital audio working (updating the BIOS to 1.61 and disabling 8ch audio in the bios) and the iec958 device is listed in alsamixer and is unmuted.
aplay -L still lists the device as discarding all input\output...

```
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

I know audio works fine in general as the analog outputs work just fine.

Any ideas??

Thanks

---

### Post by lifecomm on 2008-07-17
> **GyroTech said:**
> Hi all,

I have an MSI Media Live box and have followed instructions on this site and on the MythTV wiki to get the digital audio working (updating the BIOS to 1.61 and disabling 8ch audio in the bios) and the iec958 device is listed in alsamixer and is unmuted.
aplay -L still lists the device as discarding all input\output...

```
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

I know audio works fine in general as the analog outputs work just fine.

Any ideas??

Thanks
Disregard

---

### Post by GyroTech on 2008-07-17
Any chance you remember what magical method you used to finally kick it into working??

The best I can do it get IEC958 to have a box with '00' in it instead of 'MM', no volume bar above it like the other devices...

---

