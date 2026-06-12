---
title: "Failed to download package ( Ubuntu software center )"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by h3lLx0x on 2010-09-12
Hi there. I'm so sorry if I posted it on the wrong section but I need help on installing Netbeans from the Ubuntu software center. Tried this thing about 2 and 3 times. :\

Here is the screenshot. For your information, I'm using wireless and ubuntu 10.04 lucid lynx. 

In the detail tab :

> 
Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b18-1.8.1-0ubuntu1_i386.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b18-1.8.1-0ubuntu1_i386.deb) Hash Sum mismatch
Failed to fetch [http://my.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-doc_6b18-1.8.1-0ubuntu1_all.deb](http://my.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-doc_6b18-1.8.1-0ubuntu1_all.deb) Hash Sum mismatch


[IMG]http://img43.imageshack.us/img43/3158/failedqb.png[/IMG]

---

### Post by MaindotC on 2010-09-12
Either you have a network connection problem that for some reason cuts out after a specified length of time or download, or there is a problem reaching the repository.  Try [alternative methods ](http://is.gd/f6C2A)for downloading netbeans.

---

### Post by h3lLx0x on 2010-09-12
I already tried the netbeans alternative ways but I got problem with the JavaSDK. Thats why I used the Ubuntu software center. By the way what is the way to prevent this from happening. The problem is the ubuntu software center unable to fetch.

---

### Post by MaindotC on 2010-09-12
Does this happen for all applications you install using the software centre or just Netbeans?  What errors are you having with the SDK?

---

### Post by h3lLx0x on 2010-09-12
Only with Netbeans and Eclipse as for now.

I'm having problem on corrupted Netbeans sh file. I already downloaded the netbeans sh file for about 3 times.

---

### Post by MaindotC on 2010-09-12
I'm not really sure what the problem is buy I'll give you a work around, because I can't get anything to install with Ubuntu Software Centre and I never use it anyway - always used Synaptic or apt.  Open Synaptic, type in "netbeans", install.  I'll look into the software centre business.

---

### Post by h3lLx0x on 2010-09-12
I get this error the same error as the first post one :

```


W: Failed to fetch http://archive.mmu.edu.my/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b18-1.8.1-0ubuntu1_i386.deb
  Hash Sum mismatch


W: Failed to fetch http://archive.mmu.edu.my/ubuntu/pool/main/o/openjdk-6/openjdk-6-doc_6b18-1.8.1-0ubuntu1_all.deb
  Hash Sum mismatch

```

---

### Post by MaindotC on 2010-09-12
I found the following suggestion by googling:```
apt-get update
apt-get upgrade
apt-get clean
apt-get autoclean
```

You can also just wget the package and then install it that way:```
wget [http://archive.mmu.edu.my/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b18-1.8.1-0ubuntu1_i386.deb](http://archive.mmu.edu.my/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b18-1.8.1-0ubuntu1_i386.deb)
```

---

