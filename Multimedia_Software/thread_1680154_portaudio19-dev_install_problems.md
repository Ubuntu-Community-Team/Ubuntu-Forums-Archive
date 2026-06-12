---
title: "portaudio19-dev install problems"
date: 2011-02-02
forum: Multimedia Software
---

### Post by Graemej on 2011-02-02
Using Ubuntu 10.10 on Dell E1505, 1.5GB ram.
I am trying to install portaudio19-dev on my machine which has jackd2 already installed. when I attempt to install it it wants to remove jackd2 and install jackd1. If I allow this and then remove jackd1 to reinstall jackd2 it forces the removal of portaudio19.dev

I know others have jackd2 and portaudio19-dev installed and did not have my problem so I am looking for help on this issue. Thanks in advance

```
$ sudo apt-get install portaudio19-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libjack-dev libjack0 libportaudiocpp0
Suggested packages:
  jackd1
The following packages will be REMOVED:
  jackd2 jackd2-firewire libjack-jackd2-0 libjack-jackd2-dev
The following NEW packages will be installed:
  libjack-dev libjack0 libportaudiocpp0 portaudio19-dev
0 upgraded, 4 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/420kB of archives.
After this operation, 229kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by Graemej on 2011-02-03
Bump

---

### Post by vininim on 2011-11-18
[https://bugs.launchpad.net/ubuntu/+source/portaudio19/+bug/132002/comments/3](https://bugs.launchpad.net/ubuntu/+source/portaudio19/+bug/132002/comments/3)

"portaudio19-dev depends on libjack-dev which indirectly suggest installation of jackd1. By installing libkjack-jackd2-dev before installing portaudio19-dev this dependency will already be met, and you can install it without having to downgrade jackd."

Sorry about the necromancy, but this thread is getting google top hit before the bug comment.

---

