---
title: "photo's"
date: 2009-12-31
forum: Multimedia Software
---

### Post by jfloria on 2009-12-31
How do I transfer my photos back to jpeg format so that I can burn a data disc for a microsoft computer, I have tried........ but I have failled.
Please help!

---

### Post by kestrel1 on 2009-12-31
> **jfloria said:**
> How do I transfer my photos back to jpeg format so that I can burn a data disc for a microsoft computer, I have tried........ but I have failled.
Please help!
What format are they currently in? Most picture formats can be recognized by Windows.

---

### Post by drpjkurian on 2009-12-31
> **jfloria said:**
> How do I transfer my photos back to jpeg format so that I can burn a data disc for a microsoft computer, I have tried........ but I have failled.
Please help!

Hi
Open those images in GIMP and click file tab and click save as tab.
You will have a window popped up in which you will get an option of selecting the file type for saving. Select jpeg.
Hope you got it

Regards
Dr Kurian

---

### Post by jfloria on 2009-12-31
I have gimp and will try ..I will let you know thanks

---

### Post by jfloria on 2009-12-31
when i pull up a photo it has a label like this next to it 46856C3-6D1F-6D1F-4CB1-8A82-BD99EBB9FD47, I believe it is grz format, I would like to format all my phots but this allows me to do one at a time.

---

### Post by cgb on 2009-12-31
grz is not a format I am familiar with.  How did these images get put in this format to begin with?  Was this part of some backup program that backed up the images into this format?  I somewhat suspect this due to the filenames.  You can batch convert files but to actually rename the files yet to would be somewhat of a nightmare and would be best accomplished by restoring the files with whatever method they were converted in the first place.  Otherwise one way to convert to jpg format would be with a similar code as below. 

```
mogrify -format jpg -quality 90 *.tif
```

make sure you replace the .tif with whatever the appropriate file type actually is of the current images, possibly .grz if that is correct.

---

### Post by howefield on 2009-12-31
Probably not .grz unless they are compressed.

---

### Post by kestrel1 on 2009-12-31
.grz files would be a compressed file. You need to decrompress them before you can do anything with them.

---

