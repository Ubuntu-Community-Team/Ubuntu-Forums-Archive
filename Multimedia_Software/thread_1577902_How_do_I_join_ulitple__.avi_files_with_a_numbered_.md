---
title: "How do I join ulitple  .avi files with a numbered extension?"
date: 2010-09-19
forum: Multimedia Software
---

### Post by notquitestr8t on 2010-09-19
This should be easy but despite all the hints and tricks I've read, I cannot make this work. 
 I have 130+ files with the names filename.avi.001, filename.avi.002, filename.avi.003...all the way up to filname.avi.132.
How do I join them? A simple cat command does not work, neither does avimerge or any other utility I can find. I'm guessing because the file extension is a number and not .avi. Is there and easy way to rename them all and then join them? I can't be the only one with this issue but I've scoured the forums and found nothing.
Thanks,
CO

---

### Post by mbott on 2010-09-19
Is there a linux/Ubuntu equivalent of HJ Split?  HJ Split will run under Wine, btw.

-- 
Mike

---

### Post by Bonster on 2010-09-19
HJ Split has a Java version that works on any system with Java installed

[http://www.hjsplit.org/java/]("http://www.hjsplit.org/java/")


Edit: They got a Linux version now, just extract and run it

[http://www.hjsplit.org/linux/]("http://www.hjsplit.org/linux/")

---

### Post by mbott on 2010-09-19
> **Bonster said:**
> HJ Split has a Java version that works on any system with Java installed

[http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)

Wasn't aware of that.  Nice!

-- 
Mike

---

### Post by hsoulen on 2010-09-20
Hi there, why does cat not work?

cd <folder with all files>
sudo cat *.* > filename.avi

This should work perfectly as long as the files are all part of the same video.

Hank

---

### Post by notquitestr8t on 2010-09-22
Thanks everyone. As much as I wanted to avoid it, I ended up booting into Windows and using HJ Split. I just now got the other replies. I will try the java version on my Ubuntu system and also the cat command again. I did not separate all the files into one folder so that may do it. Thanks again.
CO

---

### Post by hsoulen on 2010-09-23
> **notquitestr8t said:**
> Thanks everyone. As much as I wanted to avoid it, I ended up booting into Windows and using HJ Split. I just now got the other replies. I will try the java version on my Ubuntu system and also the cat command again. I did not separate all the files into one folder so that may do it. Thanks again.
CO

I never considered that the files were in a folder with other files! Yes, that would be the problem with using cat for sure!

Good catch.

Hank

---

### Post by Raizen44 on 2010-12-16
> **Bonster said:**
> HJ Split has a Java version that works on any system with Java installed

[http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)



THanks! I've been looking for this for quite some time now...:D

---

