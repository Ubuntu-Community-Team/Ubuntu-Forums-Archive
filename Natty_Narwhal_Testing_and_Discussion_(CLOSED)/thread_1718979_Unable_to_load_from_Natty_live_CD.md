---
title: "Unable to load from Natty live CD"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ubuntrocks on 2011-04-01
Hi all,

I have downloaded and burned Natty live CD. When trying to run from it, I get the following error message right after booting:
```
casper/vmlinuz: file not found
```

And after that I get thrown to a menu where I can choose to boot from local disk or install Ubuntu. I'm running Lenovo Thinkpad edge 13.3" with intel core i3. I'd like to take Ububtu 11.04 to a test drive before installing it.

I will appreciate your advice how to track the source to the problem. Please take into account that I am newbie to Ubuntu.

Thanks in advance!

---

### Post by ajgreeny on 2011-04-01
Check the md5sum of the iso file you downloaded to check that it is a good download, then if it is OK, burn your CD again at as slow a speed as you can, and do not use the computer for anything else while burning.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ubuntrocks on 2011-04-01
> **ajgreeny said:**
> Check the md5sum of the iso file you downloaded to check that it is a good download, then if it is OK, burn your CD again at as slow a speed as you can, and do not use the computer for anything else while burning.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thanks for the reply. I checked the sha1 (didn't find md5 on ubuntu's site), it was correct. Also slowing down the burning speed didn't help.

I should have mentioned that I had the same problem with Alpha 2, and then I decided to wait for a more mature version. So I think the problem is real, not a media issue.

---

### Post by digitalbrain on 2011-04-01
Maybe you downloaded the wrong iso version. I think you should download and try a stable version such as Ubuntu 10.10 (Maverick) or 10.04 (Lucid). Beta versions may have problems. Don't forget that.

---

### Post by ubuntrocks on 2011-04-01
> **digitalbrain said:**
> Maybe you downloaded the wrong iso version. I think you should download and try a stable version such as Ubuntu 10.10 (Maverick) or 10.04 (Lucid). Beta versions may have problems. Don't forget that.

I know. Maverick works fine on my machine from Live CD. But I wanted to test Natty. If the problem is going to be solved anyhow, I don't mind waiting for the final release. But can I know for sure? Shouldn't I look into it and let the developers know in case there is a problem, before the final release?

---

### Post by dino99 on 2011-04-01
stupid question but be sure to select booting from cd/dvd into bios

---

### Post by ubuntrocks on 2011-04-01
> **dino99 said:**
> stupid question but be sure to select booting from cd/dvd into bios

Thanks for the tip. :)

I made sure the BIOS is configured correctly. I do get an error message after booting from the live cd, so the problem can't be in the BIOS.

---

### Post by dino99 on 2011-04-01
but you get "file not found"; when you burn a cd/dvd always do it at the slowest speed

---

### Post by ubuntrocks on 2011-04-01
> **ubuntrocks said:**
>  Also slowing down the burning speed didn't help.

I should have mentioned that I had the same problem with Alpha 2, and then I decided to wait for a more mature version. So I think the problem is real, not a media issue.

> **dino99 said:**
> but you get "file not found"; when you burn a cd/dvd always do it at the slowest speed

As I said earlier, I re-burned the live cd with slower speed, but it didn't help. Also, the fact that I encountered the same problem with Alpha 2, and the fact that I succeeded running 10.10, makes me think the problem does not lie in the burning procedure.

---

### Post by rbrick49 on 2011-04-01
2 ubuntu rocks I had the same problem yesterday from daily zsync I used brasero to burn the dvd it never works for me, today I used k3b and everything is ok

---

### Post by ubuntrocks on 2011-04-01
> **rbrick49 said:**
> 2 ubuntu rocks I had the same problem yesterday from daily zsync I used brasero to burn the dvd it never works for me, today I used k3b and everything is ok


I used the native Windows 7 burning progra but I'll give k3b a shot as well. Thanks.

---

### Post by rbrick49 on 2011-04-01
> **ubuntrocks said:**
> Hi all,

I have downloaded and burned Natty live CD. When trying to run from it, I get the following error message right after booting:
```
casper/vmlinuz: file not found
```

And after that I get thrown to a menu where I can choose to boot from local disk or install Ubuntu. I'm running Lenovo Thinkpad edge 13.3" with intel core i3. I'd like to take Ububtu 11.04 to a test drive before installing it.

I will appreciate your advice how to track the source to the problem. Please take into account that I am newbie to Ubuntu.

Thanks in advance! and thats what I got from brasero when I burnt the dvd

---

### Post by ubuntrocks on 2011-04-02
Re-downloaded the iso file, verified the sha1sum, burned it with k3b on the slowest speed available (x10), and still I get the same error message. I think it's not a media issue.

---

### Post by rbrick49 on 2011-04-02
I used the alternative amd 64 file on the ubuntu downloads daily build page not the one on the top plus I downloaded it on ubuntu not windows brasero burnt the disc ok even did the checksum but some how or other brasero corrupts everything I try to burn even music and videos by the way I used a dvd disc to burn to
good luck

---

