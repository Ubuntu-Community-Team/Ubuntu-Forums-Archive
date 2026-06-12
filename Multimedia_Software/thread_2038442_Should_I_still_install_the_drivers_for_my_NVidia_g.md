---
title: "Should I still install the drivers for my NVidia graphics card?"
date: 2012-08-06
forum: Multimedia Software
---

### Post by Dural on 2012-08-06
I used to have the NVidia update program on my Windows 7 partition but when Ubuntu discovered that it seceretly created a user name SOLELY to download updates for my card I promptly uninstalled it.
[http://superuser.com/questions/394037/remove-nvidia-update-and-updatususer](http://superuser.com/questions/394037/remove-nvidia-update-and-updatususer)

[http://linux.slashdot.org/story/12/08/01/1618225/proprietary-nvidia-linux-driver-contains-privilege-escalation-hole](http://linux.slashdot.org/story/12/08/01/1618225/proprietary-nvidia-linux-driver-contains-privilege-escalation-hole)
Then I come and see this. I want to use the hardware acceleration for my card but not if it comes at the expense of my safety.

Graphics Card: NVidia GeForce 9600M GT
Laptop Model: HP HDX 16 1140-US

---

### Post by Laiquendi on 2012-08-06
Why don't you use standard Ubuntu "Additional Drivers" application? :)

---

### Post by Dural on 2012-08-06
^ I do, in Linux. I put that link there because I think NVidia doesn't put out secure drivers. The first link only happens in Windows to my knowledge. What I'm worried about is that I will install the Linux drivers and risk exposing my computer so that any one can attack it and mess things up. That's why I want to know if I should wait until the patch it (if they do) or stick to Nouveau.

---

### Post by vexorian on 2012-08-06
If you are worried about security then you should not.

Instead use the open source nvidia drivers . You WILL get poorer performance.

In reality, I am not sure the exploit is so dangerous. The hackers would have to target specifically Linux users with nvidia cards and the proprietary drivers. That's is a very small percentage. I think a hacker would prefer trying to exploit something that could access more users. But if you are concerned you could be the target of targetted attacks, then avoid these drivers until you have a notice this was fixed.

Something else you should know is that the exploit needs to run inside your computer to work. (It is a trick to gain root access). So you would have to be first hit by a different exploit so that the hacker can put the nvidia exploit in your computer and be able to get root. In my opinion, this is very far-fetched unless you have good reason to believe a hacker is interested in you specifically. (I guess, if you administer a web server or company or something).

---

