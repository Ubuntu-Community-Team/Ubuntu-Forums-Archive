---
title: "Broken packages stuck in limbo"
date: 2009-12-14
forum: Multimedia Software
---

### Post by Mrsongs on 2009-12-14
While trying to install a workable flashplugin-installer, I somehow managed to get a broken packages message. Whenever I attempt to fix the broken packages, the process fails, and I get this message:

E: /var/cache/apt/archives/lib32asound2_1.0.20-3ubuntu6_amd64.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/lib32bz2-1.0_1.0.5-3_amd64.deb: subprocess dpkg-deb --control returned error exit status 2

When I attempt to remove the packages, I get this message:

E: /var/cache/apt/archives/lib32bz2-1.0_1.0.5-3_amd64.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/lib32asound2_1.0.20-3ubuntu6_amd64.deb: subprocess dpkg-deb --control returned error exit status 2

I have inserted and removed the 64 bit alpha flash plugin many times. Flash, of course, does not work.  I have attempted the processes described in the 64 bit forum and in the 64 bit flash wiki. Can anyone help?

---

### Post by Mrsongs on 2009-12-29
> **Mrsongs said:**
> While trying to install a workable flashplugin-installer, I somehow managed to get a broken packages message. Whenever I attempt to fix the broken packages, the process fails, and I get this message:

E: /var/cache/apt/archives/lib32asound2_1.0.20-3ubuntu6_amd64.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/lib32bz2-1.0_1.0.5-3_amd64.deb: subprocess dpkg-deb --control returned error exit status 2

When I attempt to remove the packages, I get this message:

E: /var/cache/apt/archives/lib32bz2-1.0_1.0.5-3_amd64.deb: subprocess dpkg-deb --control returned error exit status 2
E: /var/cache/apt/archives/lib32asound2_1.0.20-3ubuntu6_amd64.deb: subprocess dpkg-deb --control returned error exit status 2

I have inserted and removed the 64 bit alpha flash plugin many times. Flash, of course, does not work.  I have attempted the processes described in the 64 bit forum and in the 64 bit flash wiki. Can anyone help?



Well, as it turns out, these were two separate issues. Before I could fix the broken passages, I ran Nautilus as root, went to /var/cache/apt/archives/ and removed the offending cached packages, at which point apt-get knew to download new ones. YMMV.

The flash problem got fixed by the kind folks in the multimedia forum updating the link to a newer alpha version of 64 bit flash.

---

### Post by HappyFeet on 2009-12-29
> **Mrsongs said:**
> I ran Nautilus as root, went to /var/cache/apt/archives/ and removed the offending cached packages, at which point apt-get knew to download new ones. YMMV.



For future reference,
```
sudo apt-get clean
```
will clean out /var/cache/apt/archives

It's just a tad quicker this way. Glad to hear you got everything sorted.

---

