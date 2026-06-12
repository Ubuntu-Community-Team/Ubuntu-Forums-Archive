---
title: "Share all connected USB disks"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by markosjal on 2011-08-01
Hello, I have an XBMC system based on ubuntu 10.10 and I want to be able to share automagically any USB disk that is connected. I do not need authentication. I tried sharing /media from a root nautilus window and I get errors when connecting from windows. 

To be clear on this I want to share WHATEVER USB disk gets connected. I will not know the name in advance.


Is this at all possible?

---

### Post by markosjal on 2011-08-01
Any help on this? I don't think I can share /media as a user. It just says updating permissions and never stops!

Maybe this is a problem in my installation?

---

### Post by parabol2112 on 2011-08-01
I suppose this won't help you much, but I'm having the exact same issue with my home network.  I've read that Samba is only configured to be able to share things on the Filesystem.  It could also be a disk mounting problem.  

It looks like there's some info about editing smb.conf in this tutorial here: [http://ubuntuforums.org/showthread.php?t=1740312](http://ubuntuforums.org/showthread.php?t=1740312)

Alas, it's mostly for dealing with Ubuntu/Windows configuration issues.

Also, the answer might be buried somewhere in the Samba manual:
[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/)

It's not much, but let me know if you can figure out how to share folders on a USB drive.

---

### Post by Morbius1 on 2011-08-01
I can't help thinking that this is an incredibly bad idea but I think you are missing just one more step.

* You used nautilus to share /media with guest access.

* The problem is that any external USB device formatted in fat32 or ntfs will mount with you as owner and permissions of 700 - meaning only you have access. The remote guest isn't you so there is no access. The solution is to make the remote guest appear to be you as far as your shares are concerned.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
force user = markosjal
```[COLOR=Blue]*Or whatever your actual linux login user name is.*[/COLOR]

Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```I'm assumming here that all your samba shares are created in Nautilus. If you have classic shares set up in smb.conf then a global "force user" may not be what you want.

If you run into problems with your existing shares post the output of the following commands and we can approach this another way:
```
testparm -s
``````
net usershare info --long
```

---

### Post by markosjal on 2011-08-01
Morbius1

thanks for the advice I will try it. I do not know if the shares will hold up if I just ran XBMC as standalone, but I can always run it from GUI. 

 you say this is a "bad idea" but you say not why.  Let me clarify this is an XBMC system used in a home . All users should be able to have read and write access to the external disks. oh and if someone deletes a file erroneously, not the end of the world. So why is it such a bad idea?

---

### Post by Morbius1 on 2011-08-02
> you say this is a "bad idea" but you say not why./media is the used by the system as a temporary mount location for just about everything. So if you have an internal disk that houses Windows for example and you mount it by going to Nautilus then it's mounted to /media. Now it's shared across the network automatically. 

This may not describe you situation - just something to remember.

---

