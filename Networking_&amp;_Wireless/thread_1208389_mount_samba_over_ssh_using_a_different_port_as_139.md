---
title: "mount samba over ssh using a different port as 139"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by ernstblaauw on 2009-07-09
Hi,

I have a Network Media Tank at home, whoch supports ssh but does not offer support for sshfs. Therefore, I want to tunnel the samba through ssh to my Ubuntu 9.04 laptop, so I can access my NMT from anywhere. I seems to be easy (according to the tutorials I found) to mount the smb share if you use the standard 139 port, but that's already in use on my laptop. That's the reason I try to use port 2139.

Therefore, I set up a ssh tunnel to the NMT:
```
ssh -f -N -L 2139:172.19.3.2:139 root@user.dyndns.org -i /home/user/.ssh/nmt/id_rsa_root.openssh -p 2022

```
and after that, I tried to mount the HD of the NMT on my laptop
```
smbmount //localhost/share /home/user/nmt -o port=2139,username=nmt,password=1234,ip=127.0.0.1

```
However, I get the following error:
```
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

As you can see, I did not succeed in mountin gthe share over ssh. Can someone help me solving this issue?
Thanks!
Ernst

---

### Post by ernstblaauw on 2009-07-09
A little bump, as this thread has been dropping on the thread list :-)

---

