---
title: "Letting Windows see Ubuntu"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by Norster on 2008-12-08
I have a dual boot pc running Ubuntu on one hard drive and windows XP Pro on the other.

If I boot to Ubuntu, I can see the Windows drive and use it.
If I boot to windows, I cannot see the Ubuntu drive.

Can anyone suggest how I may achieve this ?

I also have a windows XP Home laptop on my home network, and that cannot see the Ubuntu drive either.

---

### Post by MarblePanther on 2008-12-08
Windows cannot read the ext3 filesystem linux uses

google around, there may be something for windows that will allow you to read ext3, not that i know of (i dont use windows anymore)

windows reads only ntfs and fat by default

---

### Post by 73ckn797 on 2008-12-08
Look on the web for this file: "Ext2IFS_1_11.exe".

Here: [http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html)

I use it in Windows and it does read my Ubuntu drive flawlessly.

---

### Post by Norster on 2008-12-10
> **73ckn797 said:**
> Look on the web for this file: "Ext2IFS_1_11.exe".

Here: [http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html)

I use it in Windows and it does read my Ubuntu drive flawlessly.
Thanks for this link. I have downloaded and set it up, but when I click to the drive, I get 'this drive is not formatted, do you want to format it now?' Obviously I say No, and then cannot see the drive.

Any suggestions - did I set it up wrong ?

---

### Post by Norster on 2008-12-10
> **73ckn797 said:**
> Look on the web for this file: "Ext2IFS_1_11.exe".

Here: [http://www.fs-driver.org/extendeddl.html](http://www.fs-driver.org/extendeddl.html)

I use it in Windows and it does read my Ubuntu drive flawlessly.
Thanks for taking the time to reply. I had another reply which suggested a download, so will try that.

---

### Post by 73ckn797 on 2008-12-14
> **Norster said:**
> Thanks for taking the time to reply. I had another reply which suggested a download, so will try that.


Sorry that I did not reply back soon enough. I do not spend all my time at the computer so I do not always get back with people quickly.

I have not encountered that problem so cannot really offer much help. I would try re-installuing and retrying. I have loaded it it many time without errors.

---

