---
title: "Mythbuntu control center hangs on diskless"
date: 2011-02-12
forum: Mythbuntu
---

### Post by drjenk on 2011-02-12
Hi,
I have successfully booted a diskless frontend, I can watch tv, see my recordings,etc.  
But when I go to do such things as add infrared support through the mythbuntu control center, when I click apply, mythbuntu control center hangs indefinitely.  I followed this procedure to the letter:

[http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless](http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless)

Does anyone know what can be causing this?  Permissions somehow?  I am so close, I just need my remote to work and I'm in business.  

Thanks for any insight.

David J.

---

### Post by drjenk on 2011-02-12
Would it be a matter of doing this:

First mount /proc to the image
sudo mount -o bind /proc /opt/ltsp/i386/proc/
Switch to the image environment
sudo chroot /opt/ltsp/i386
Now do whatever you want as if you were on a frontend. 

Then doing an apt-get for infrared capability?  If so, how do I know the distribution name to use?

Thanks for any help

---

### Post by superm1 on 2011-02-14
> **drjenk said:**
> Hi,
I have successfully booted a diskless frontend, I can watch tv, see my recordings,etc.  
But when I go to do such things as add infrared support through the mythbuntu control center, when I click apply, mythbuntu control center hangs indefinitely.  I followed this procedure to the letter:

[http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless](http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless)

Does anyone know what can be causing this?  Permissions somehow?  I am so close, I just need my remote to work and I'm in business.  

Thanks for any insight.

David J.

There are some limitations with running MCC in a diskless chroot I believe.

You'll probably want to run the command line version of the commands to enable infrared.

if lirc isn't installed:
```
apt-get install lirc

```

if it is:
```
dpkg-reconfigure lirc
```

---

