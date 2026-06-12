---
title: "resolv.conf: no such file"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by otakuon on 2011-02-09
Trying to fix a friend's Dell Mini with Ubuntu 8.04.  It stopped resolving host names so obviously I figured there was a DNS issue.

Sure enough, when I run:

```
sudo dhclient eth0
```I get the following errors:

```
chown: failed to get attributes of '/etc/resolv.conf': no such file or directory
chmod: failed to get attributes of '/etc/resolv.conf': no such file or directory
mv: cannot move '/etc/resolv.conf.dhclient-new' to '/etc/resolv.conf': no such file or directory
```I tired 
```
cat /etc/resolv.conf
```And also received no such file or directory.

If I go through the GUI file manager, I do not see resolv.conf.  However, if I ls the /etc directory, resolv.conf is listed.

If I try both lsattr to see the attributes or chattr to change them (with sudo) I get.

```
No such file or directory while trying to stat /etc/resolv.conf
```It would appear that the resolv.conf file has had some rather wonky permissions applied to it and has been rendered all but invisible to the OS.  I have tried both moving and copying the resolv.conf.dhclient-new file to resolv.conf but get the "no such file or directory" response with both of them.  If I change the target name to something like resolv.conf.bak it works, but of course that doesn't do me any good. The resolv.conf file must be present as it won't let me overwrite it...even with super-user access. Any suggestions on what I should do next?

Thanks!

---

### Post by Iowan on 2011-02-09
Have you tried **sudo touch /etc/resolv.conf**?

---

### Post by otakuon on 2011-02-10
Yeap...touch also returns no such file or directory.

EDIT:  I have attached pictures to show that I am not crazy (please note the resolv2.conf and resolv.conf.bak were files I created to make sure I had write permissions to the /etc directory).

---

