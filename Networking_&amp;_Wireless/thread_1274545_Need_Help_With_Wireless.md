---
title: "Need Help With Wireless"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by Daniel Ogden on 2009-09-24
Hello all. I have had it with Windows and have decided to switch to Linux. I just installed Ubuntu 9.04 and everything started working great except for the wireless internet. I have a AWD154 wireless card and after some poking around found this write up for installing ndiswrapper; [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501) .  I used ndiswrapper 1.55 and got to the part on the write up where you verify the installation without any problems.  Did the following:

ndiswrapper -v

Recieved:
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.28-11-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 

The next part is where I am getting hung up.

pam@pam-desktop:~/driver$ sudo ndiswrapper -i mrv8000c.inf
couldn't open mrv8000c.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.

The .inf and .sys files are in the driver directory.

No clue what to do next.

---

### Post by Cuba71 on 2009-09-24
You're already half way there.  You have the Windows drivers and ndiswrapper installed.
I'd recommend you read the sticky at the top of this forum.

[Here]("http://ubuntuforums.org/showthread.php?t=885847")

---

### Post by Daniel Ogden on 2009-09-24
One more thing. I did check the list of supported cards and my card is supported by ndiswrapper. Any help is greatly appreciated, if there is no way to make it work and someone can recommend an economical card that will work out of the box that would be great also. Thanks.

---

### Post by Daniel Ogden on 2009-09-24
> **Cuba71 said:**
> You're already half way there.  You have the Windows drivers and ndiswrapper installed.
I'd recommend you read the sticky at the top of this forum.

[Here]("http://ubuntuforums.org/showthread.php?t=885847")

Have been through that. None of the results in step one match mine. I get this:

pam@pam-desktop:~$ ndiswrapper -l
pam@pam-desktop:~$ 

Which is nothing? Please bear with me as I am totally new to Linux. I have some technical knowledge but this is a large stretch for me and completely foreign.

---

### Post by Daniel Ogden on 2009-09-25
Bump. Again, even knowing what wireless card I could buy that would work without all this set up would be appreciated. I have Cat 5 strewn about my house at the moment, and that just won't do.

---

