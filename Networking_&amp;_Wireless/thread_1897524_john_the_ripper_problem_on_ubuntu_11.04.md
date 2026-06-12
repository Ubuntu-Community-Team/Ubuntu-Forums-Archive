---
title: "john the ripper problem on ubuntu 11.04"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by arunes007 on 2011-12-19
i have gone throgh following steps in downloading the package of john the ripper on ubuntu 11.04
as going through...
```
sudo apt-get install john 
```
i got error "no password hashes loaded" on my system.
browsing throgh web i find that john the ripper does not support "sha512" encryption....
then i have done like this...



i have downloaded the package by typing:
 wget [www.openwall.com/john/g/john-1.7.8.tar.gz]("http://www.openwall.com/john/g/john-1.7.8.tar.gz")
  
 wget [www.openwall.com/john/g/john-1.7.8.tar.gz.sign]("http://www.openwall.com/john/g/john-1.7.8.tar.gz.sign")

 
 [B]now i have to 
[/B]
**Unzip, patch and compile the program**
 ```
 

 #tar -zxvf john-1.7.8.tar.gz
 #cd john-1.7.8
  
```
 The patch lets “john” call crypt(3) to encode passwords when it sees unsupported encryption. There are** 3 files **we need to change/create: Makefile, crypt_fmt.c and john.c.
  
 **Append “-lcrypt” to line “LDFLAGS = -s”, making the line reads as:**
  
 "LDFLAGS = -s -lcrypt"
I didnt get the last two lines....what ldflags or -lcrypt and how to 
append or patch the file i didnt nw plz help....

---

### Post by nothingspecial on 2011-12-19
Closed.

---

