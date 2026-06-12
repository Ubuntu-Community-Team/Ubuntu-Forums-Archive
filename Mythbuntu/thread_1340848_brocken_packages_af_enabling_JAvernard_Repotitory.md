---
title: "brocken packages af enabling JAvernard Repotitory"
date: 2009-11-29
forum: Mythbuntu
---

### Post by sperwer on 2009-11-29
Hi

I have just added the avernard repository, but it gives me the following broken packages:
libmyth-0.22-0 installed version: 2:0.22.0-fixes22906
mplayer installed version 2:1.0-svn29964-0ubuntu3

How can I fix this problem?
I runing ubuntu 9.10
> 
Problem solved, thx to jyavenard reply nr.: #6

Sperwer

---

### Post by mars76 on 2009-11-29
Hi,

  I have the same packages as i updated them today and i didn't have any problems..

  May be you can re-try  the Update manager..

mars

---

### Post by hirnwurscht on 2009-11-29
Maybe you had bad luck and not all packages were updated/in the repository at the time doing the update.

You should try
```
sudo apt-get update
```
followed by
```
sudo apt-get upgrade
```
in a terminal.

---

### Post by sperwer on 2009-11-29
Thx for ur Help

I did retry update-manager, so far with no luck.
Here is the result:
> E: /var/cache/apt/archives/libvdpau1_0.3-0ubuntu3_i386.deb: trying to overwrite '/usr/lib/libvdpau.so.1', which is also in package nvidia-185-libvdpau 0

Sperwer

---

### Post by hirnwurscht on 2009-11-29
[_Here_]("http://www.nvnews.net/vbulletin/showthread.php?p=2128763") I read that you have to manualy delete a file.

I did, and i was able to install libvdpau1 afterwards.

But beware, I ran into a problem with videoplayback which I still couldn't fix...

[http://ubuntuforums.org/showthread.php?t=1340048]("http://ubuntuforums.org/showthread.php?t=1340048")

---

### Post by jyavenard on 2009-11-29
> **sperwer said:**
> Thx for ur Help

I did retry update-manager, so far with no luck.
Here is the result:


Sperwer

FAQ:
[http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html](http://www.avenard.org/media/Ubuntu_Repository/Entries/2009/11/9_Karmic_and_Using_Avenard_repo.html)

Note that this is the same issue if you were using the mythbuntu weekly repo..

---

### Post by jyavenard on 2009-11-29
> **hirnwurscht said:**
> [_Here_]("http://www.nvnews.net/vbulletin/showthread.php?p=2128763") I read that you have to manualy delete a file.


Do *not* follow this advice; this is only applicable if installing the nvidia drivers using the nvidia installers. Not when using ubuntu packages

---

### Post by hirnwurscht on 2009-11-30
> **jyavenard said:**
> Do *not* follow this advice; this is only applicable if installing the nvidia drivers using the nvidia installers. Not when using ubuntu packages

I did... so how to fix this?
Since I deleted libvdpau.so, there seems to be no way to reinstall it in a good way... :(

OK, fixed it.. I think.

I completely removed every nvidia/libvdpau related package I could find (including mythtv and mplayer from the avenard repo).
Then, instead of installing nvidia-glx-185 as suggested on your site, I noticed those packages are not from your repository, so I installed nvidia-glx-195 and related packages from your repo.
Afterwards, libvdpau1 installed without problems.

Still, I got this weird transparency issue.

I think I'm missing some symbolic links to libvdpau
```
ls -l /usr/lib/*vdpau*
lrwxrwxrwx 1 root root    31 2009-11-30 10:34 /usr/lib/libvdpau_nvidia.so -> vdpau/libvdpau_nvidia.so.195.22
lrwxrwxrwx 1 root root    17 2009-11-30 10:35 /usr/lib/libvdpau.so.1 -> libvdpau.so.1.0.0
-rw-r--r-- 1 root root  6152 2009-11-22 01:37 /usr/lib/libvdpau.so.1.0.0
-rw-r--r-- 1 root root 51120 2009-10-08 16:51 /usr/lib/libvdpau_trace.so

/usr/lib/vdpau:
insgesamt 1656
-rw-r--r-- 1 root root 1633736 2009-11-24 05:24 libvdpau_nvidia.so.195.22
lrwxrwxrwx 1 root root      23 2009-11-30 10:35 libvdpau_trace.so.1 -> libvdpau_trace.so.1.0.0
-rw-r--r-- 1 root root   51232 2009-11-22 01:37 libvdpau_trace.so.1.0.0

```

Maybe it's easier to create those links manually, can someone who has working vdpau with mythtv and the avenard repository post their output of
```
ls -l /usr/lib/*vdpau*
``` ?

thanks

---

