---
title: "NFS mount randomly mounts on boot"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by peshko-lnx on 2010-07-10
Here is my entry in the fstab:

192.168.1.11:/mnt/array1/Our_NAS    /media/Our\040NAS    nfs    auto,_ne
tdev,rw,hard,users,intr    0    0

Upon reboot, sometimes it would mount automatically and sometimes it would not. I have not discovered any specific pattern. It is very random. Sometimes it would go many reboots without mounting and on the next it would mount it. I tried putting timeo paramter, played with the parameters, but still have the same issue. My laptop is connected to a wireless network.

When I do mount -a or if I go to Places everything mounts great. It just simply will not mount all the time automatically upon boot, and after wireless connection is established.

Any help to make this working would be appreciated.

---

### Post by peshko-lnx on 2010-07-10
Sorry, should have added that I run 10.04 64-bit.

---

### Post by peshko-lnx on 2010-07-10
<bump>

---

### Post by Morbius1 on 2010-07-10
There is a similar problem in Samba land and might be the same cause -  fstab is being executed before the network is up. 

I came up with a workaround that at least two people said worked :wink:  Maybe it will work for you: [http://ubuntuforums.org/showpost.php?p=9315066&postcount=31](http://ubuntuforums.org/showpost.php?p=9315066&postcount=31)

Basicaly, create a script to do a "mount -a" and place it in /etc/network/if-up.d. Any script placed there will execute only after the network is up.

It's worth a shot and easily reversible if it doesn't work.

---

### Post by peshko-lnx on 2010-07-10
Morbius, that works great for me. I appreciate your input on that!!!

One quick question, has this been reported as a bug. I looked at a couple of bugs, that somewhat get close to what I experience. I am not sure if it is possible to make a permanent solution.

---

### Post by Morbius1 on 2010-07-10
A Samba specific bug has been reported : [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/508186](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/508186)

But I doubt it will get very far. Samba bugs eventually get pushed upstream to Samba itself and it's not a samba problem it's an upstart problem. The way services are started has been changed and upstart is slowly replacing the standard method. It's impacting Samba, CUPS, and apparently NFS.

---

### Post by bjbeeson on 2010-07-30
Thanks your solution worked great.  I have been trying to solve this problem for months.

Thanks again.

---

