---
title: "Infiniband nightmare"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by pooyaplus on 2009-01-27
Hi,

I have been looking for a way to install infiniband network adapter on an AMD 64 cluster. I could not find the solution in the forum nor with hours of googling. 

The only solution is to use the OFED package which is based on RPM packages.

I installed the RPM on my ubuntu and went through the installation process, but encountered this error:
```
Failed to build ibutils RPM 
See /tmp/OFED.9819.logs/ibutils.rpmbuild.log
```

Any helps would be greatly appreciated.

---

### Post by pooyaplus on 2009-01-28
Bump...](*,)

---

### Post by pooyaplus on 2009-01-28
OK. is there a way to install the infiniband without the need for RPMs?:(

---

### Post by pooyaplus on 2009-01-28
Here is the error log attached.

---

### Post by theozzlives on 2009-01-28
do```
sudo alien filename.rpm
``` it'll make a .deb file (you might have to install alien from the repositories.

---

### Post by infinitejones on 2009-01-28
Now I'm no expert but here's your problem:

```
make: *** /lib/modules/2.6.27-7-generic/build: No such file or directory.  Stop.
```

which suggests to me that you need to install kernel headers and source like this:

```

sudo apt-get install linux-headers-2.6.27-7-generic
sudo apt-get install linux-source
```

That'd be my guess, anyway. Maybe do some googling with that error message before you do anything, and see if you can find any other information that either backs up that solution, or shows that it definitely won't work...

Also, this is almost too obvious so maybe it won't work, but have you tried using alien to convert the rpm to a deb?

---

### Post by kreggz on 2009-01-28
suggest you download it from [http://www.openfabrics.org/downloads/OFED/ofed-1.4/OFED-1.4.tgz](http://www.openfabrics.org/downloads/OFED/ofed-1.4/OFED-1.4.tgz) and compile it from there.

There doesn't seem to be a deb for it though as you have discovered already. You should be able to run the rpm on centos or fedora

before you compile anything make sure you have build-essential

---

### Post by pooyaplus on 2009-01-28
> **infinitejones said:**
> Now I'm no expert but here's your problem:

```
make: *** /lib/modules/2.6.27-7-generic/build: No such file or directory.  Stop.
```

which suggests to me that you need to install kernel headers and source like this:

```

sudo apt-get install linux-headers-2.6.27-7-generic
sudo apt-get install linux-source
```

That'd be my guess, anyway. Maybe do some googling with that error message before you do anything, and see if you can find any other information that either backs up that solution, or shows that it definitely won't work...

Also, this is almost too obvious so maybe it won't work, but have you tried using alien to convert the rpm to a deb?
I have the kernel source and generic packages already installed.

> **kreggz said:**
> suggest you download it from [http://www.openfabrics.org/downloads/OFED/ofed-1.4/OFED-1.4.tgz](http://www.openfabrics.org/downloads/OFED/ofed-1.4/OFED-1.4.tgz) and compile it from there.

There doesn't seem to be a deb for it though as you have discovered already. You should be able to run the rpm on centos or fedora

before you compile anything make sure you have build-essential

That's where I got my package.

---

### Post by pooyaplus on 2009-01-28
> **theozzlives said:**
> do```
sudo alien filename.rpm
``` it'll make a .deb file (you might have to install alien from the repositories.

Unfortunately, the package I have downloaded from openfabrics does not include a single rpm to convert to a .deb package.:(

---

### Post by kreggz on 2009-01-28
The RPM is designed for Red Hat Server. There does not seem to be a deb file so if you can't get the RPM to work try compiling the source.

Have you tried this already?

3. Installing OFED Software
============================

The default installation directory is: /usr

Install Quick Guide:
1) Download and extract: tar xzvf OFED-1.4.tgz file.
2) Change into directory: cd OFED-1.4
3) Run as root: ./install.pl
4) Follow the directions to install required components. For details, please see
   OFED_Installation_Guide.txt under OFED-1.4/docs.

---

### Post by pooyaplus on 2009-01-29
Yes, I have been struggling with that perl installation script for two bloody days. I managed to meet almost all the dependencies except the last package. I can not recall the name of that package now - but that was a generic make of open-iscsi or something. 

Anyways, I am just wondering how on earth debian based dists have to install their infinband!!

---

### Post by kreggz on 2009-01-29
ahh there's a deb for open-iscsi

sudo apt-get install open-iscsi

---

### Post by pooyaplus on 2009-01-31
Yes, that's right. The package as I said is a generic make of the open-iscsi which is open-iscsi-generic (not available in ubuntu repo).

Anyways, I managed to install the infiniband on one of the nodes. 
```
PERL INSTALLER SCRIPT --all
```

If I could manage to install it on the other nodes and could configure the IP and bounding features, will make a tutorial asap.

Thanks guys.

---

### Post by pooyaplus on 2009-02-01
Is the **mark as solved** gone? I can not find it in the thread tools.

---

### Post by jsimon on 2010-05-06
> **pooyaplus said:**
> Yes, that's right. The package as I said is a generic make of the open-iscsi which is open-iscsi-generic (not available in ubuntu repo).

Anyways, I managed to install the infiniband on one of the nodes. 
```
PERL INSTALLER SCRIPT --all
```If I could manage to install it on the other nodes and could configure the IP and bounding features, will make a tutorial asap.

Thanks guys.

Can you please tell us how you were able to configure your infiniband card? A tutorial would be great. If you don't have the time, just a brief overview of what did to get it up and running would help a lot. 

PS: Does ```
PERL INSTALLER SCRIPT --all
``` mean that you ran the install script with the --all flag and it worked?

---

### Post by anothracc on 2012-03-29
I'm interested in this too, now.  I'm having the same problems as detailed above but the fix is not specific enough for me to use.

Does anyone know how to do this?

---

### Post by westie457 on 2012-03-29
> **anothracc said:**
> I'm interested in this too, now.  I'm having the same problems as detailed above but the fix is not specific enough for me to use.

Does anyone know how to do this?

You would probably be better off by starting you own thread about your problem. This thread has not had any replies for nearly 2 years and the software has moved on since then.

---

### Post by howefield on 2012-03-29
Old Thread closed.

---

