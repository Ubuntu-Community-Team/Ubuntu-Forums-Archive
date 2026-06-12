---
title: "libdvdcss2 and win32codecs Help requested"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by cebe11 on 2008-03-01
I always seem to have problems getting these installed.  I solved it once but forgot how I did it!

Anyway, I'm following these directions for Feisty:

```
For Ubuntu Feisty Fawn Users

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

Now you need to copy the key using the following command

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

Update the source list using the following command

sudo apt-get update

Install Codecs using the following command

sudo apt-get install w32codecs libdvdcss2
```

When I do the sudo apt-get update I see the following errors:

```
Failed to fetch http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/source/Sources.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


```


And then finally :
```
sudo apt-get install w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

Suggestions???

---

### Post by logos34 on 2008-03-01
Try this guide instead:
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

i.e.
> sudo wget [http://www](http://www).**medibuntu.org/sources.list.d/feisty.list -O **
/etc/apt/sources.list.d/medibuntu.list

---

### Post by cebe11 on 2008-03-01
Thanks that worked now.

---

### Post by K_V_B on 2008-03-02
I have a dapper system, and did the following:

```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
sudo apt-get update
```


When I try to install the w32codecs I still get:

```
me@home:/etc/apt$ sudo apt-get install w32codecs 
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
```

I've defined the medibunut source correctly as far as I can see, and it is included in the apt update. But the w32codecs package is still not known. 

What should I do?

---

### Post by K_V_B on 2008-03-02
Mmm. Posting here really clears the mind. I had overlooked that I am on a 64 bit system. I need the w64codecs...

---

### Post by retrow on 2008-04-24
The link for medibuntu worked perfectly for 32bit hardy.

---

### Post by nolanz2 on 2008-06-09
this worked like a charm!

---

