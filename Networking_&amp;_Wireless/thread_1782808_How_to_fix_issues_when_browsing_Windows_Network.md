---
title: "How to fix issues when browsing Windows Network"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by travlemon on 2011-06-15
Hello!

I noticed that out of the box, Ubuntu has problems browsing a Windows Network of shared folders.  I always seem to get a blank window when I double click "Windows Network", or in some cases I receive the error "Failed to retrieve share list from server".  This started happening in maybe version 9.10 of Ubuntu.  

Anyway, I found a really good fix for it, and I made a tutorial video on YouTube of me showing how to fix it, and showing a successful result.  

Just keep in mind that I was pressed for time when I made the video, and didn't have time to install regular Ubuntu on my virtual machine, so I used an already installed OS:  MoonOS, which is based on Ubuntu and the fix works just the same across the board for Ubuntu based distros, and it has worked really on any Linux OS that I've tried it on.

Here's the link:  [http://www.youtube.com/watch?v=lqETu4dWQrI](http://www.youtube.com/watch?v=lqETu4dWQrI)

---

### Post by Waddle on 2011-06-15
Thank you this worked perfectly for me! I still have some permission issues trying to get XP to see my Ubuntu shares, but at least i am able to transfer files between the 2 computers.

---

### Post by travlemon on 2011-06-15
> **Waddle said:**
> Thank you this worked perfectly for me! I still have some permission issues trying to get XP to see my Ubuntu shares, but at least i am able to transfer files between the 2 computers.

You're very welcome!

If you're having issues getting XP machines to see your Ubuntu shares, you can try restarting the Samba service with this command:

```
sudo service smbd restart
```

If you still have trouble, you may need to create the shares the slightly long way.  I've had much luck in installing the package **system-config-samba**.   That program allows you to specify what folders you want to share, and allows you to match Ubuntu users to the WIndows user/password equivalent.  I.E. you can add a Linux user to have permission to a shared folder, and then manually enter the Windows username and password that you want to authenticate as that Linux user.

You can run this command to install the utility, I think it shows up under System>Administration>Samba
```
sudo apt-get install system-config-samba
```

Hope it helps

---

