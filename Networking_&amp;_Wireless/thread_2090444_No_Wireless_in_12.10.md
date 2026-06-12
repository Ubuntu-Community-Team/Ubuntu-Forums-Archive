---
title: "No Wireless in 12.10"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by Ray Huang on 2012-12-02
I am having a problem in 12.04 in bootcamp on my MB pro circa 2009.  When I type in Terminal the commands (iwconfig) to look up my settings I  get :

lo no wireless extensions.

eth0 no wireless extensions.

Then when I type in (sudo lshw -C network) I then get a command to enter my password, which does not work. I use my admin password and nothing.

I am using a Cisco e1200 router and I cannot install the set-up CD or download the set-up  from internet because of an Archive Manager failure. I am stuck.

Ubuntu and I are off to a rocky start. I blame myself as a newbie of course. I can get internet via ethernet though. Wireless works fine on PC in house  and OSX side of machine.
 

TIA,
Ray

---

### Post by Bucky Ball on 2012-12-02
***Post moved to own thread***

Hi and welcome to the forums. I have created a new thread for your post as your problem is similar but *not* the same as the thread you posted on. Jumping on another thread is called hijacking and is not encouraged as it confuses the original issue and this is unfair to those being helped and those helping. It also limits your chances of getting help as you are buried on another thread with a title which may not specifically describe your problem.

Having your post on its own thread increases your chances of getting help specific to your issue. By all means, keep an eye on the other thread for tips and post if you have anything useful to add that might help the original poster.

Good luck.
BB

PS: As you are attempting to run a command and your password is not working I would probably post a thread specifically about that. You are aware that when you type your password in a terminal you will see nothing, this is for security reasons, but when you hit return all will be fine? If you could post the result of the command you mention that would be very helpful. The output of iwconfig shows that the wireless card is not yet happening as you should be seeing something like 'wlan0' for your wireless. 

Have you updated while the ethernet cable is plugged in (while online) and checked 'Additional Drivers'?

---

### Post by Ray Huang on 2012-12-02
Thanks BB. I used to use Forums all of the time, it will all come back to me again. I accidentally started another thread before I saw this one. Feel free to delete either.

---

### Post by Bucky Ball on 2012-12-02
All good. Please post the link to the other thread here and I will have a look and see what's appropriate. They can also be merged. ;)

---

### Post by Ray Huang on 2012-12-02
[I]SOLVED: I went to the software center and downloaded additional  drivers. I activated the Broadcom STA driver and immediately I had  wireless.


			[/I]

---

### Post by Ray Huang on 2012-12-02
[http://ubuntuforums.org/showthread.php?t=2090535](http://ubuntuforums.org/showthread.php?t=2090535) can be merged or deleted if this helps other users.

---

### Post by Bucky Ball on 2012-12-02
Hi Ray,

Please mark both threads as Solved from 'Thread Tools' at the top right of this page to help others and we'll leave it there.

Cheers and enjoy the learning curve, the forums and Ubuntu. ;)

BB

---

