---
title: "Sharing Files with a Simple Network"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by br4ndonn4bors on 2012-03-16
Hello, World!
I have Ubuntu 11.10, and I can go on there and see my Windows XP computer just fine. 
However, when I'm on Windows, I cannot see the Ubuntu computer.
I want to share files between the two.

What is my problem? 
Any advice would help a lot.

I'm still new to ubuntu so I don't know the network configurations like windows.

Also, I both computers are on a wired network.. if that matters.

---

### Post by Bucky Ball on 2012-03-16
You would probably need to install Samba in Ubuntu or share the partitions/directories in Ubuntu if it is already installed. Try [HERE]("http://www.google.com.au/#hl=en&sugexp=frgbld&gs_nf=1&cp=23&gs_id=4c&xhr=t&q=install+samba+ubuntu+11.10&pf=p&sclient=psy-ab&oq=install+samba+ubuntu+11&aq=0&aqi=g4&aql=&gs_sm=&gs_upl=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597HERE"). ;)

Try:

```
sudo apt-get install samba
```Apparently all you need with 11.10.

There are other ways of doing it but this is common ...

---

