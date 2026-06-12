---
title: "ASUS Optical Out Doesnt seem to be detected"
date: 2011-05-08
forum: Multimedia Software
---

### Post by Replicator2011 on 2011-05-08
Hey Guys

I am new to Ubuntu but finding its a pretty cool system to use.


I have a question regarding Audio.

I have a pair of Logitech Z5500D speakers and its connecting via a optical cable but I dont think Ubuntu is finding the optical driver.

Could you please tell me what I need to do in order to get my audio working.

---

### Post by Replicator2011 on 2011-05-09
Update:

I managed to get sound working but notice it is extremely scratchy.


What can I do to rectify this?

---

### Post by lidex on 2011-05-11
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

