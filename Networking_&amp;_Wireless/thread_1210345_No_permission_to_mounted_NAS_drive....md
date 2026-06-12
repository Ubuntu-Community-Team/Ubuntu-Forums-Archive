---
title: "No permission to mounted NAS drive..."
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by m0116815 on 2009-07-11
Hi all, I'm a new Linux user, still trying to find my way around Ubuntu. I'm running Jaunty 9.04 on a Dell Optiplex GX240. It runs fine, but there are one or two things I can't figure out.

Before I explain the problem, I should first mention that I'm logging on to this computer remotely, usually through ssh (putty). All help is appreciated of course, but help that relies on command-line access only (and not gnome or kde) is appreciated a bit more :)

The problem involves my (old) Western Digital MyBook WE, a 500Gb NAS drive. I'm trying to mount it so that it will stay mounted even after rebooting the PC. I'm trying to mount it to two different points (one in my ~/, the other in /var/www/ for an apache server). I hope that isn't a problem to begin with.

The mounting itself doesn't give any errors or warnings when I do this:

sudo mount -t cifs //192.168.2.3/jodie fluffy -o username=jodie,passwd=#####

I can also add this to /etc/fstab:

//192.168.2.3/jodie /home/jodie/fluffy cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

(with the .smbcredentials file containing username and password).

Now the problem:

jodie@Pigwidgeon:~$ ls fluffy/
ls: cannot open directory fluffy/: Permission denied

However, $ sudo ls fluffy/ works.

Sadly, this does not:
jodie@Pigwidgeon:~$ sudo chmod 775 fluffy/
chmod: changing permissions of `fluffy/': Permission denied

The exact same happens with the /var/www/ mount point. Strangely, the directory is visible from the web...


Any ideas on what I'm doing wrong?

---

### Post by m0116815 on 2009-07-11
Also, I have gotten this to work... but by accident so I don't remember how. It didn't require installing new software, though.

</shameless bump>

---

### Post by m0116815 on 2009-07-12
If this is a completely obvious question that has been answered here many times, I'd also love to get some help on finding the thread :-)

---

### Post by m0116815 on 2009-07-12
Heh, this works:

smbmount //192.168.2.3/jodie fluffy/ -o username=jodie,passwd=#####

So how do I do this with mount?

---

### Post by m0116815 on 2009-07-13
Hope > Experience :)

---

### Post by m0116815 on 2009-07-29
ttt

---

### Post by dmizer on 2009-07-29
See the second link in my sig, it includes troubleshooting steps.

---

