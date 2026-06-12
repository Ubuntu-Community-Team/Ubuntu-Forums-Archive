---
title: "Can't access a drive on the network since Ubuntu reinstall"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by Ghostlove on 2011-03-28
This was working for me in 10.10 until I was forced to reinstall Ubuntu. I have a Western Digital Live Hub, basically a hard drive that sits under my telly and lets me stream media from the computer or transfer media to it from the computer. I could access it fine a couple of days ago, but then I reinstalled Ubuntu and now I get the error "Unable to mount location, Failed to retrieve share list from server". Anyone have any idea how I can access it again?

---

### Post by papibe on 2011-03-28
I do not have experience with that device, but if I have to guess, it uses smb (Windows) to share its disks. What I would do is update your Ubuntu machine (in case there's a Samba update), reboot, and try again.

If that doesn't work... Did you configure any setting of Samba? like change the workgroup or something like that?

Regards.

---

### Post by Ghostlove on 2011-03-29
> **papibe said:**
> I do not have experience with that device, but if I have to guess, it uses smb (Windows) to share its disks. What I would do is update your Ubuntu machine (in case there's a Samba update), reboot, and try again.

If that doesn't work... Did you configure any setting of Samba? like change the workgroup or something like that?

Regards.

I updated Ubuntu, there appeared to be a Samba update so I installed and rebooted but it hasn't helped.

I don't even know what Samba is so I don't think I configured any of its settings.

---

### Post by ndefontenay on 2011-03-29
Samba is the protocole that allows you to gain access to windows style file sharing.

If you have a drive (windows term) on the network, you most likely need Samba to access it.

Try this from the command line (Applications>Accessories>Terminal):
sudo apt-get install smbfs smbclient

We'll make sure anything you need is installed.

Then try to connect to it again. 
If it still doesn't work we will debug a bit further.

Nico

---

### Post by ndefontenay on 2011-03-29
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

Might help. It looks a bit hard but there's a lot of good explanations in there.

Samba will be a breeze after that.

---

### Post by Ghostlove on 2011-03-29
Okay if I go to smb://<IP of drive>/ I can get into it fine. It's just getting to it from my network folder which isn't working. How odd!

The even stranger thing is that before my re-install I didn't need to do anything like this to access it, just clicking it in the Network folder worked.

---

### Post by Morbius1 on 2011-03-29
Something in your network or something you enabled on your Ubuntu machine like the firewall is preventing you from converting a machine name to an ip address.

If the Western Digital Live Hub has a static ip address or if it can be set to have a static ip address then once you connect to it using smb://<ip address> bookmark it ( Bookmarks > Add bookmark ).

---

### Post by Ghostlove on 2011-03-29
> **Morbius1 said:**
> Something in your network or something you enabled on your Ubuntu machine like the firewall is preventing you from converting a machine name to an ip address.

If the Western Digital Live Hub has a static ip address or if it can be set to have a static ip address then once you connect to it using smb://<ip address> bookmark it ( Bookmarks > Add bookmark ).

It actually plopped a link to itself on my desktop after I'd managed to open it, which is handy. How do I adjust Ubuntu's firewall please?

---

