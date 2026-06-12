---
title: "Cannot get VLC to Install"
date: 2011-10-14
forum: Multimedia Software
---

### Post by Monsuco on 2011-10-14
I seem to be having dependency issues for VLC. I am running Kubuntu 11.10 x64. When I try to install VLC I get the following:
```

monsuco@EarthBound:~$ sudo apt-get install vlc
[sudo] password for monsuco: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1.1.12-1~getdeb1) but it is not going to be installed
       Depends: libavcodec52 (>= 4:0.6-1~) but it is not installable or
                libavcodec-extra-52 (>= 4:0.6-1~) but it is not installable
       Depends: libavutil50 (>= 4:0.6-1~) but it is not installable or
                libavutil-extra-50 (>= 4:0.6-1~) but it is not installable
       Recommends: vlc-plugin-notify (= 1.1.12-1~getdeb1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.12-1~getdeb1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
monsuco@EarthBound:~$ 

```
How do I fix this?

---

### Post by hsoulen on 2011-10-14
You can see what the output of this is:

```
sudo dpkg --configure -a
```

And post your output.

If it shows dependency issues you can try the below:

```

apt-get clean 
apt-get auto clean
apt-get update

```

Cheers,

Hank

---

### Post by Monsuco on 2011-10-14
Nope that didn't work.

```
root@EarthBound:~# sudo dpkg --configure -a
root@EarthBound:~# 

```
Looks like nothing's there.

---

### Post by 4Orbs on 2011-10-14
[This how-to]("http://ubuntuforums.org/showthread.php?t=766683") can probably solve your problem.

---

### Post by Monsuco on 2011-10-14
Looks like I fixed it myself. It took a bit of work, but I found a PPA for VLC.
```

sudo add-apt-repository ppa:n-muench/vlc

```
VLC works.

---

