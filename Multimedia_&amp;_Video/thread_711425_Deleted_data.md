---
title: "Deleted data"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by ssharps711 on 2008-02-29
I deleted my external. I reformatted it on accident. I've found some hardware that can get it back. Getdataback works but I can't seem to get past step 2. It says something along the lines of choosing a file system but there is no options to choose from. I know the data is still on it because it all comes up in the scan but I can't seem to access it.

Strange I know. Anyone familiar with Getdataback?

---

### Post by aysiu on 2008-02-29
> **ssharps711 said:**
> I deleted my external. I reformatted it on accident. I've found some hardware that can get it back. Getdataback works but I can't seem to get past step 2. It says something along the lines of choosing a file system but there is no options to choose from. I know the data is still on it because it all comes up in the scan but I can't seem to access it.

Strange I know. Anyone familiar with Getdataback?
I don't know anything about Getadataback, but if you install *testdisk* and run the command ```
photorec
``` you should be able to recover your erased data.

---

### Post by ssharps711 on 2008-02-29
Problem is; it's not erased per say, just reformatted. I'll try this but it sounds waaaay too simple.

---

### Post by aysiu on 2008-02-29
> **ssharps711 said:**
> Problem is; it's not erased per say, just reformatted. I'll try this but it sounds waaaay too simple.
That's okay. I had a friend who repartitioned her whole drive and reformatted it, and I was able to recover almost all of her files using *photorec* (it took many hours, though, as it was a big drive).

I can't make any guarantees, but it should work.

---

### Post by ssharps711 on 2008-02-29
Thanks a lot. I'm actually in windows right now trying another program Data Recovery Wizard which is supposed to take a little over 2 days... 250gb... Like I said I really need this work back. So thanks again.

---

### Post by wieman01 on 2008-03-03
> **aysiu said:**
> I don't know anything about Getadataback, but if you install *testdisk* and run the command ```
photorec
``` you should be able to recover your erased data.
Hello Aysiu, 

Thanks for that hint. I mistakenly erased an important file last night on a 'ext3' file system. I have not written any other data on it since, so is there a chance that I can recover it using your program?

That would be good news indeed.

Would this also hold true for a mounted but encrypted volume?

---

### Post by aysiu on 2008-03-03
> **wieman01 said:**
> Hello Aysiu, 

Thanks for that hint. I mistakenly erased an important file last night on a 'ext3' file system. I have not written any other data on it since, so is there a chance that I can recover it using your program? Yes, but I would boot a live CD, and it might take a really long time, as I believe *photorec* will try to recover every file on your drive, not just the one you deleted.

> Would this also hold true for a mounted but encrypted volume? I don't know.

---

### Post by wieman01 on 2008-03-03
Thank you, Aysiu. Since the file is on a dedicated partition, there should be no need for a LiveCD, is that right? My data partition is a separate one and the system won't write anything on to it during the boot process. So installing it using my installed system should be OK I guess.

---

