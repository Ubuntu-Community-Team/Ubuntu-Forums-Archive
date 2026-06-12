---
title: "Building fglrx on 2.6.34 with DKMS"
date: 2010-05-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-05-08
At last I can post this somewhere!

I have adapted patches to get fglrx to build (in DKMS!) on 2.6.34:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573748](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573748)

---

### Post by dino99 on 2010-05-08
nice job, thanks

if you could open your ppa on launchpad it would help a lot of people :p

---

### Post by piccir on 2010-05-28
Hello
Can you explain how to apply these patches?
I have the module source in /var/lib/dkms/fglrx/10-4/source
Thank you
piccir

---

### Post by jfernyhough on 2010-05-29
Copy the attached files to the given locations:

/usr/src/fglrx-8.723.1/dkms.conf
/usr/src/fglrx-8.723.1/patches/fglrx-2.6.33.patch
/usr/src/fglrx-8.723.1/patches/fglrx-2.6.34-rc4.patch

Then reinstall or rebuild fglrx.

Do not copy to /var/lib/dkms as any files here are regenerated on each installation. Also remember that these locations are for the Ubuntu fglrx package, not the AMD installer.

---

### Post by rafalcieslak on 2010-05-31
Thanks a lot! Great job;) it solved my problem perfectly.

---

### Post by Nphyx on 2010-06-03
Thanks for this, saved me a ton of trouble :)

---

### Post by PGHammer on 2010-06-04
> **Nphyx said:**
> Thanks for this, saved me a ton of trouble :)

Unfortunately, that does no good with 2.6.34-5 or later; any idea what breaks with those and later kernels?

---

### Post by null_pointer_us on 2010-06-04
The patches work fine here (upgraded to this w/ dkms enabled):

```
$ apt-cache policy linux-image-generic

linux-image-generic:
  Installed: 2.6.34.5.4
  Candidate: 2.6.34.5.4
  Version table:
 *** 2.6.34.5.4 0
        500 http://us.archive.ubuntu.com/ubuntu/ maverick/main Packages
        100 /var/lib/dpkg/status
```

From memory, here are instructions that should work for a fresh installation:

1. Verify dkms is installed:

```
sudo apt-get update
sudo apt-get install dkms
```

2. [COLOR="DarkOrange"]**System -> Administration -> Hardware Drivers**[/COLOR] and try to activate fglrx. This will fail.

3. Put the patches in the folders as described in [comment #4]("http://ubuntuforums.org/showpost.php?p=9378209&postcount=4"); create the folders if needed.

4. [COLOR="DarkOrange"]**System -> Administration -> Hardware Drivers**[/COLOR] and try to activate fglrx. This should succeed.

5. Check for compiled kernel modules:

```
$ dkms status

fglrx, 8.723.1, 2.6.32-22-generic, x86_64: installed 
fglrx, 8.723.1, 2.6.34-5-generic, x86_64: installed
```

---

### Post by jfernyhough on 2010-06-04
There are new fglrx packages in X-Swat; installing now.

--edit
Nope, it fails trying to apply patches. Going back to my manual method. :D

I guess I really should find out how to build a package and put it in a PPA.

---

### Post by jfernyhough on 2010-06-05
Excellent, the new fglrx packages in X-Swat build nicely for .34 and .35!

[https://edge.launchpad.net/~ubuntu-x-swat](https://edge.launchpad.net/~ubuntu-x-swat)

Thanks Robert (sarvatt)!

Wonder if I'll get any credit for the patch work... not according to the changelog... :(

---

### Post by aviramof on 2010-06-05
> **jfernyhough said:**
> Excellent, the new fglrx packages in X-Swat build nicely for .34 and .35!

[https://edge.launchpad.net/~ubuntu-x-swat]("https://edge.launchpad.net/%7Eubuntu-x-swat")

Thanks Robert (sarvatt)!

Wonder if I'll get any credit for the patch work... not according to the changelog... :(

Your definitely going to get credit from me thank you very much for the fglrx ppa:):):)

---

