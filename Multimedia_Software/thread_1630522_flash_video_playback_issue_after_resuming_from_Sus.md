---
title: "flash video playback issue after resuming from Suspend"
date: 2010-11-25
forum: Multimedia Software
---

### Post by aditya.sharma on 2010-11-25
After upgrading from 10.04 to 10.10 on my 64 bit laptop, I find that flash videos are unplayable after resuming from Suspend (to RAM). This occurs on both Chrome and Firefox, for all the websites I tried: Youtube, Facebook, Vimeo and others too.

I searched if there already are any fixes, this thread seems to be related but I am not able to see any improvement after restarting my browser, either Firefox or Chrome. 
[http://ubuntuforums.org/showthread.php?t=1561791](http://ubuntuforums.org/showthread.php?t=1561791)
This webpage looks relevant, but the fixes mentioned here still dont work for me:
[http://askubuntu.com/questions/10905/why-does-chrome-video-performance-substantially-degrade-after-waking-from-suspend](http://askubuntu.com/questions/10905/why-does-chrome-video-performance-substantially-degrade-after-waking-from-suspend)


Any suggestions? This is making my decision to upgrade Ubuntu look like a really bad one.

---

### Post by aditya.sharma on 2010-11-25
Actually trying these commands mentioned in this forum and then restarting the browser fixed the issue for me.

[http://ubuntuforums.org/showpost.php?p=9958308&postcount=11](http://ubuntuforums.org/showpost.php?p=9958308&postcount=11)


sudo mkdir /etc/adobe 
echo "OverrideGPUValidation=true" >~/mms.cfg 
sudo mv ~/mms.cfg /etc/adobe/



I had tried all sort of things like reinstall of flash packages etc, finally it was the above three commands which worked. I wonder if it is some thing which is wrong in Adobe plugin or Linux suspend which is causing this to break.

---

### Post by enigmatichus on 2011-03-30
Thank you very much, you saved me!! As always this forum is useful and professional. Thanks again! :)

---

