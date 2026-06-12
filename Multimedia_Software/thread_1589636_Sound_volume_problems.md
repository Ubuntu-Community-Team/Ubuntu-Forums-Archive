---
title: "Sound volume problems"
date: 2010-10-06
forum: Multimedia Software
---

### Post by meem1029 on 2010-10-06
I am running Ubuntu 10.04 on a Sony Vaio EC laptop.  I am having problems with my volume being very low under Ubuntu, even if I turn all the options to full, I can barely hear it.  This happens both through the built in speakers and through headphones.  I know it is not a hardware problem since both work fine in Win7 dual boot.  Also, this problem occurs both in Rhythmbox and chromium.

---

### Post by meem1029 on 2010-10-06
Also, I forgot to mention that the sound worked just fine for about a month after I installed Ubuntu, but within the last week has stopped working.  I do not believe I changed any settings shortly before this started.

---

### Post by Yellow Pasque on 2010-10-06
Did you upgrade any relevant packages (alsa, linux-image/headers, etc.) ?

If you can remember when you lost volume, check in /var/log/ (apt or dpkg logs) to see if there's a corresponding change.

---

### Post by meem1029 on 2010-10-06
Now that you mention it, I looked and I did upgrade linux-headers, and I think that was about when I upgraded to the new kernel cuz the update manager said to.  The previous version is still appearing on GRUB, so I will try booting to that and seeing if that works.

---

### Post by meem1029 on 2010-10-06
Ok, that worked.  I'm not sure what the problem is, but at least I know how to avoid it.  I'm assuming that there aren't any problems associated with booting into a slightly older kernel.  Is that correct?

---

### Post by lidex on 2010-10-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

