---
title: "VAAPI on Intel Atom Cedar trail chipset."
date: 2012-09-06
forum: Mythbuntu
---

### Post by captainvideo on 2012-09-06
I am running MythBuntu 12.04 (32 bit) with an Intel Atom DN2800MT motherboard (Cedar trail chipset.) I installed the cedar trail proprietary drivers using apt-get and 1080i OTA video works great.
 
The proprietary bundle included a VAAPI driver, so I read the how-to at [www.mythtv.org/wiki/VAAPI]("http://www.mythtv.org/wiki/VAAPI") and assumed that since the driver was installed, I could skip step 3 (complling the driver). I followed all the other steps, but after setting up the Vaapi profile, videos will not play. I receive the error "Failed to open video output."
 
Should I not have skipped step 3? Any ideas?
 
Thanks

---

### Post by nickrout on 2012-09-06
> **captainvideo said:**
> I am running MythBuntu 12.04 (32 bit) with an Intel Atom DN2800MT motherboard (Cedar trail chipset.) I installed the cedar trail proprietary drivers using apt-get and 1080i OTA video works great.
 
The proprietary bundle included a VAAPI driver, so I read the how-to at [www.mythtv.org/wiki/VAAPI]("http://www.mythtv.org/wiki/VAAPI") and assumed that since the driver was installed, I could skip step 3 (complling the driver). I followed all the other steps, but after setting up the Vaapi profile, videos will not play. I receive the error "Failed to open video output."
 
Should I not have skipped step 3? Any ideas?
 
ThanksSounds like an issue you would find far more knowledge about on the mailing list. I have seen vaapi discussed there a few times.

---

### Post by joshoekstra on 2012-09-06
Does mythfrontend --version show you using_vaapi?

---

### Post by captainvideo on 2012-09-06
Yes.

---

