---
title: "Nikon NEF files"
date: 2011-09-25
forum: Multimedia Software
---

### Post by mateusamp on 2011-09-25
Hi there comunity,

I'm new on Ubuntu and trying to let windows behind.
But I'm having some problem with my photos that I do in RAW NEF files.
The think is that Caputure NX From Nikon don't support linux.
Anyway, the Shotwell can show my photos in really low resolution, impossible to work on it.
So, does anyone knows a solution to have a better resolution on NEF file in Ubuntu?
and is it possible to convert the NEF file into JPEG?

Thanks!
Mat.

---

### Post by ajgreeny on 2011-09-25
I think this may help you
[http://ubuntuforums.org/showthread.php?t=827407](http://ubuntuforums.org/showthread.php?t=827407)

---

### Post by mateusamp on 2011-09-25
Thanks a lot!
I will try the solutions there.

---

### Post by shantiq on 2011-09-26
> **ajgreeny said:**
> I think this may help you
[http://ubuntuforums.org/showthread.php?t=827407](http://ubuntuforums.org/showthread.php?t=827407)


thanx man cool tip


this looks like it is the [**ticket**]("http://rawtherapee.com/downloads")


```
sudo apt-get install rawtherapee
```

or in software center

> RawTherapee is used to adjust some of the most often changed parameters when optimizing digital images. A normal user often just wants to adjust the white balance or brightness of a photo he took. Instead of using a big and expensive image editor you could use a small and fast tool like RawTherapee. More and more cameras also support RAW formats. RAW files usually offer higher color depth than JPGs. So the adjustments are done with the high color depth and then afterwards converted to or saved as JPGs. RawTherapee supports JPG, PNG and TIFF. All image processing is done in 16 bit/channel mode. Different to other RAW converters it can use EAHD as demosaicing algorithm. The raw loading engine of RawTherapee is based on dcraw.




this lets you do it in a second in GIMP too    ```
sudo apt-get install gimp-ufraw
```

---

