---
title: "How do get cinelerra"
date: 2009-11-18
forum: Multimedia Software
---

### Post by tropdoug on 2009-11-18
I have added the repositories and the pgp key as laid out on the cinelerra site, but when I try to install it this is what I get

```
he following packages have unmet dependencies:
  cinelerra: Depends: liblame0 (>= 3.97) but it is not installable
             Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
             Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
             Depends: libraw1394-8 but it is not installable
             Depends: libquicktimehv (= 1:2.1.0-2svn20071030) but it is not going to be installed
E: Broken packages

```When I go through the above packages 1 by 1 with sudo apt-get install I find some new packages replacing these obsolete ones, but when I get to the third one down, it cannot find a replacement or updated package. 

I don't know what to do from here? 

Can anyone help please I am using 9.10 with an AMD dual core processor

---

### Post by ilil on 2009-11-19
I think cinelerra is not buit properly for Karmic. So, you can ask for new build on cinelerra' site or try to build it yourself.

---

### Post by gordintoronto on 2009-11-30
> **tropdoug said:**
> 
  cinelerra: Depends: liblame0 (>= 3.97) but it is not installable
             Depends: libmjpegtools0 (>= 1:1.8.0) but it is not installable
             Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
             Depends: libquicktimehv (>= 1:2.1.0) but it is not going to be installed
             Depends: libraw1394-8 but it is not installable
             Depends: libquicktimehv (= 1:2.1.0-2svn20071030) but it is not going to be installed
E: Broken packages
[/code]When I go through the above packages 1 by 1 with sudo apt-get install I find some new packages replacing these obsolete ones, but when I get to the third one down, it cannot find a replacement or updated package. 


I am using Cinelerra under Jaunty, and have libopenexr6 installed.

---

