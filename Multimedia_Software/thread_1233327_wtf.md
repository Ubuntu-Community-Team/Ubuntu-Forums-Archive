---
title: "wtf"
date: 2009-08-06
forum: Multimedia Software
---

### Post by Jimstehrman on 2009-08-06
so I guess no one has ever had to do this, but I need to split a 12 Gb .mov file into about 16 Mb sections, I'm trying to this on a mac, and it is dead set to not be helpful. Is there any way to do this in linux or run a command/simple program through BASh?

---

### Post by kodalisrikanth on 2009-08-06
> **Jimstehrman said:**
> so I guess no one has ever had to do this, but I need to split a 12 Gb .mov file into about 16 Mb sections, I'm trying to this on a mac, and it is dead set to not be helpful. Is there any way to do this in linux or run a command/simple program through BASh?
split -b 16384 yourfilename

This will repeatedly crop your file into 16MB files untill it reaches 12GB!!Ofcourse, the file names obtained will not be in .mov extension. You have to explicitly name them. Write a script to finish the naming ... !!


Cheers



:)


Thanks,
Srikanth Kodali

---

### Post by Simian Man on 2009-08-06
> **kodalisrikanth said:**
> split -b 16384 yourfilename

This will repeatedly crop your file into 16MB files untill it reaches 12GB!!Ofcourse, the file names obtained will not be in .mov extension. You have to explicitly name them. Write a script to finish the naming ... !!


split will just split up the bits of the file into pieces.  I don't know the details of the .mov file format, but I can almost guarantee you that the resulting files will not be playable as the chucnks will not have the correct file header info and such.

I'd look into ffmpeg, I wouldn't be suprised if it can do this.

---

### Post by kodalisrikanth on 2009-08-06
yah. you are correct. It will split the bits into pieces. But, the files can be played, if you rename them. 

This is the simple solution, if he dont need all that info. 

but, ffmpeg is preferable for editing.



Thanks,
Srikanth.

---

