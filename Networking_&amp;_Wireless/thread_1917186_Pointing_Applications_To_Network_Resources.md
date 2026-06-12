---
title: "Pointing Applications To Network Resources"
date: 2012-01-29
forum: Networking &amp; Wireless
---

### Post by yogiman.uk on 2012-01-29
Hi

I have all of my media (Video, Music, Pictures) stored on a network attached storage device.

I find that when I want to access that media via some of my applications that the location is not recognised. Location does not exist is the normal error.

So if I were using Windows I would simply map a drive letter to the location I wish to access. E.G: - netuse m: \\servername\sharename$

Obviously I realise that Linux does not use drive letters so I wonder how I make a remote location appear to be a local location.

Can I create some kind of symbolic link?

I would appreciate any help you can offer.

Thanks


yogiman!

---

### Post by Morbius1 on 2012-01-29
You need to mount the remote share first. So If you do that through Nautilus it will create a mount point ( i.e., sort of a mapped drive ) automatically in your home folder at:
> /home/your-user-name/.gvfs/share-name on server-nameYou will have to enable: "Show hidden files" in your application or any application like gedit in order to select it from the "Open Files" dialog box.

---

### Post by yogiman.uk on 2012-01-29
Hi thanks for the reply.  Is there a way for me to be able to automount this location?

Thanks

Yogiman!

---

### Post by Morbius1 on 2012-01-29
The easiest way is with Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by yogiman.uk on 2012-01-29
Morbius, your a star, thank you for the help :)

---

