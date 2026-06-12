---
title: "Dvd copy"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by rfurman24 on 2007-06-25
I have read the forums and do not see a clear answer to my exact need. I have a young child who does not take very good care of her dvds. I need to make exact copies to dvd dual layer discs. I want the easiest possible way to do it. Will k3b do this or will I need to rip them and then burn them? Some of them are newer and may have copyright protection. I am not sure. Thanks in advance.

---

### Post by Milky The Brown Cow on 2007-06-25
try the instructions here:

[http://209.85.165.104/search?q=cache:hk1HCHaJhscJ:www.arsgeek.com/%3Fp%3D462+dvd+dual+layer+copy+ubuntu&hl=en&ct=clnk&cd=1&gl=us&ie=UTF-8](http://209.85.165.104/search?q=cache:hk1HCHaJhscJ:www.arsgeek.com/%3Fp%3D462+dvd+dual+layer+copy+ubuntu&hl=en&ct=clnk&cd=1&gl=us&ie=UTF-8)

They start about 2/3 down the page. Sorry for it being in the form it is, but apparently the site doenst exist anymore and this is a google cached page. ;)

Hope this helps!
~max

---

### Post by rfurman24 on 2007-06-26
Still a little muddy on the dvd9 to dvd9. I guess I will just have to try it with K3B since apparently no one using linux has done it. lol. I really appreciate the help.

---

### Post by andrew.46 on 2007-08-04
Hi,

 Read your post while searching for info about dual layer discs:

> **rfurman24 said:**
> I have read the forums and do not see a clear answer to my exact need. I have a young child who does not take very good care of her dvds. I need to make exact copies to dvd dual layer discs. I want the easiest possible way to do it. Will k3b do this or will I need to rip them and then burn them? Some of them are newer and may have copyright protection. I am not sure. Thanks in advance.

 It can be done easily using the command line. You will probably need to install the appropriate libdvdcss package if it is legal for you to do so and then install:

```
sudo apt-get install vobcopy mkisofs
```

 The following commands copy the DVD to your Desktop, then you change to the folder that vobcopy has created and run the mkisofs command. This leaves you with a .iso file to burn to dvd:

```
cd Desktop
vobcopy -v -m /media/cdrom0
cd <MOVIE Folder>
mkisofs -v -dvd-video -o ../MOVIE_Name.iso .
```

 Change MOVIE_Name to whatever you want. This works well and I have done it myself many times.

                Andrew

---

