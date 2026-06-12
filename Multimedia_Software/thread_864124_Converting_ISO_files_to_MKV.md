---
title: "Converting ISO files to MKV"
date: 2008-07-19
forum: Multimedia Software
---

### Post by njb on 2008-07-19
I'm wondering wich program is the best for converting a .ISO file wich is an image of a blueray disk to an .MKV file

:popcorn:

NjB

---

### Post by warp99 on 2008-07-19
> **njb said:**
> I'm wondering wich program is the best for converting a .ISO file wich is an image of a blueray disk to an .MKV file

:popcorn:

NjB

Well you can mount the .iso then extract the files if not encrusted with DRM. So first mount the file:

```
mount -o loop -t iso9660 blueray.iso /media/cdrom
```

then copy the files to your local drive and use mencoder or ffmpeg to make the conversion. Your kernel needs to have UDF 2.5 file support in order for this to work. More information is available here:

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD?](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD?)

---

### Post by Kalectro on 2009-03-31
I tried this but it gives me an error
> 
       mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       Manchmal liefert das Syslog wertvolle Informationen &#8211; versuchen
       Sie  dmesg | tail  oder so

dmesg | tail output: ISOFS: Unable to identify CD-ROM format.

it works for regular CDs and DVDs but not for Blueray :(

any help?

---

### Post by Kalectro on 2009-03-31
finally got it :)
for everyone else having this problem try 'udf' instead of 'iso9660'

---

### Post by aLiEnTxC on 2010-07-24
yes, or you use auto like there: [http://agnipulse.com/2008/08/easily-mount-iso-files-as-virtual-drives-in-ubuntu/](http://agnipulse.com/2008/08/easily-mount-iso-files-as-virtual-drives-in-ubuntu/)

And for ppl who looking for a howto to convert with mencoder I found today this:

[http://www.serenux.com/2009/02/howto-encode-a-blu-ray-rip-into-a-smaller-format-without-losing-quality/](http://www.serenux.com/2009/02/howto-encode-a-blu-ray-rip-into-a-smaller-format-without-losing-quality/)

---

