---
title: "Problem sharing a folder"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by jscho84233 on 2010-11-05
Hi,

I am having problems sharing a folder on a USB drive attached to my Ubuntu computer.

I right click on the folder I want to share, click "Sharing Options", check all the check boxes and press "create share", then "add the permissions automatically". All the windows then disappear, and when I right click on said folder and click Sharing Options, all the boxes are unchecked again.

I can see the Ubuntu computer from Windows (7), but there are no shares in there.

Am I doing something wrong here? Many thanks!

---

### Post by cipherboy_loc on 2010-11-05
1) What type of share? Samba (SMB) share?
2) What is the format of the USB drive?



Thanks,
Cipherboy

---

### Post by jscho84233 on 2010-11-05
Hi,

Yeah, it's a samba share, and I'm not sure about the format. How can I determine this? Right click and properties does not show the format. If it is relevent, when I go to the Permissions tab in the properties, it says "The permissions of "Volume" could not be determined."

Thanks!

EDIT - I plugged the drive into my win7 laptop, and its format is NTFS.

---

### Post by jscho84233 on 2010-11-05
After cipherboy asked what format the disk was, I figured that there was a problem with the file format.

I did a bit of searching and found this guide: [http://ubuntuforums.org/showthread.php?t=1586804](http://ubuntuforums.org/showthread.php?t=1586804)

I followed it, and I can now share the USB disk to my windows computer. 

Thank you very much for the pointer, cipherboy!

---

