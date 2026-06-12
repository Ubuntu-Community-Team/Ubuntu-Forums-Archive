---
title: "Is thre an official repository for Zoom client ?"
date: 2015-12-06
forum: Multimedia Software
---

### Post by oygle on 2015-12-06
Seems Zoom is similar to Google hangouts, skype,etc. When I go to join a meeting, am redirected to this page - [https://zoom.us/download](https://zoom.us/download)

If I set the 'Linux type' to Ubuntu, it displays the following ..

>  deb (for Ubuntu 12.04+)
Version 1.1.33228.1124
*
Zoom's rpm packages are signed with a GPG key. Please run "rpm --import package-signing-key.pub" to import the key in case package management utility asks for a missing public key.

Download Public Key

Key fingerprint: 3960 60CA DD8A 7522 0BFC B369 B903 BF18 61A7 C71D

and the file to download is [https://zoom.us/client/latest/ZoomInstaller_i386.deb](https://zoom.us/client/latest/ZoomInstaller_i386.deb)

Is there an official Ubuntu repository for the Zoom client please ?

---

### Post by Rob Sayer on 2015-12-06
It doesn't seem to be in the repositories.  You can check easily with Synaptic Package Manager, which I generally use for installing if not the terminal.  I don't think synaptic comes with Kubuntu so open a terminal and copy/paste:

```
sudo apt-get update
```

to refresh the software sources list and then

```
sudo apt-get install synaptic
```

Then install gdebi, which will install packages from .deb files.  If it isn't in the repos this is the best way to install IMO.  It'll resolve needed dependencies.  Note you need to be connected to the internet for this to work.

That stuff about rpm packages isn't relevant for ubuntu or ubuntu based systems.  That's the Red Hat/Fedora/some others packaging system.

---

### Post by oygle on 2015-12-08
Thanks Rob. I do have Synaptic package manager installed. Seems this isn't in the repositories.

---

### Post by Bucky Ball on 2015-12-08
> **Rob Sayer said:**
> It doesn't seem to be in the repositories.  You can check easily with Synaptic Package Manager, which I generally use for installing if not the terminal.  I don't think synaptic comes with Kubuntu so open a terminal and copy/paste:

```
sudo apt-get update
```

to refresh the software sources list and then

```
sudo apt-get install synaptic
```

Then install gdebi, which will install packages from .deb files.  If it isn't in the repos this is the best way to install IMO.  It'll resolve needed dependencies.  Note you need to be connected to the internet for this to work.

Software Centre will install .deb files. You just need to click the file and SC will pop up and do its thing. No need to install all this. :)

@oygle: This thread has been marked as solved. This doesn't seem to be the case from your posts. If it is, please share how you fixed. Thanks.

---

### Post by oygle on 2015-12-08
> **Bucky Ball said:**
> @oygle: This thread has been marked as solved. This doesn't seem to be the case from your posts. If it is, please share how you fixed. Thanks.

The thread subject is "Is thre an official repository for Zoom client". I have already stated ...

> Seems this **isn't** in the repositories.:lolflag:

---

### Post by Bucky Ball on 2015-12-09
All good. Just checking. :D

---

