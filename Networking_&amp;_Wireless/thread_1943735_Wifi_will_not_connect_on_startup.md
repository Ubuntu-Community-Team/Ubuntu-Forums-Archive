---
title: "Wifi will not connect on startup"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by strausd on 2012-03-20
Hi! First time Ubuntu user and total noob here. I just built a new system and finally got the wifi working thanks to this post:
[http://ubuntuforums.org/showthread.php?t=1608095#1](http://ubuntuforums.org/showthread.php?t=1608095#1) 

The problem I am having now is that whenever I start the system up, I have to run "sudo modprobe rt3562sta" and then enter my password for the wifi to start working. 

I tried the step where I edit /etc/modules file and add "rt3562sta.ko" to the end, but when I tried to do that I could not edit the file. So I followed another post I found to edit the file:
[http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-load-the-sound-card-module-during-boot-478688/#9](http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-load-the-sound-card-module-during-boot-478688/#9)

Now every time I view the file, the line is in correctly (at least I think so). 

Also, "rt3562sta" is listed in the additional drivers application but it is inactive. Could that be why? I am a little afraid to activate it since it took me so long to get it working...

The wifi is still not connecting whenever I boot. Can anyone help me? And I am very new to this so try and dumb down your answers for me :D

Thanks in advance for the help!

---

### Post by KennyJack on 2012-03-20
Hi Strausd,

I fully understand your frustrations trying to get wireless to work with Ubuntu, as I have been there myself :)  I am not qualified to answer your problem, but just to give you a tip if you want your questions answered in a quicker fashion, be sure to state current OS version and hardware information, if possible.  It can help speed up the process.  Good luck!

---

### Post by strausd on 2012-03-20
> **KennyJack said:**
> Hi Strausd,

I fully understand your frustrations trying to get wireless to work with Ubuntu, as I have been there myself :)  I am not qualified to answer your problem, but just to give you a tip if you want your questions answered in a quicker fashion, be sure to state current OS version and hardware information, if possible.  It can help speed up the process.  Good luck!

Thanks for the tip!

I am currently running Ubuntu 11.10 and am using this wireless adapter:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166011](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166011)

And incase it is also needed, motherboard and CPU:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157277](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157277)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103951](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103951)

---

### Post by Bucky Ball on 2012-03-20
You need:

```
**sudo** nano /etc/modules
```You need to add the sudo to edit that file. When done; control+x, enter. ;)

Incidentally, have you plugged in via a cable and gotten all updates then check 'Additional Drivers'? Try that if you haven't.

---

### Post by strausd on 2012-03-20
> **Bucky Ball said:**
> You need:

```
**sudo** nano /etc/modules
```You need to add the sudo to edit that file. When done; control+x, enter. ;)

Incidentally, have you plugged in via a cable and gotten all updates then check 'Additional Drivers'? Try that if you haven't.

Thanks for the help!

I tried that and put in the last line, but the wifi is still not working when I boot up. I am still required to do "sudo modprobe rt3562sta" to get it working. 

And I did check additional drivers. It shows the rt3652sta driver and when I click on it, the bottom says it is not active. But after doing the terminal command to get wifi working, it will change the "this driver is not activated" in additional drivers to "A different version of this driver is in use." 

Should I try activating that driver?

---

### Post by Bucky Ball on 2012-03-20
Yes! Activate that driver in 'Additional Drivers' and see what happens ... ;)

Best to try is reboot so no drivers are installed (avoiding conflicts) then activate the driver in 'Additional Drivers' ...

---

### Post by strausd on 2012-03-20
> **Bucky Ball said:**
> Yes! Activate that driver in 'Additional Drivers' and see what happens ... ;)

Best to try is reboot so no drivers are installed (avoiding conflicts) then activate the driver in 'Additional Drivers' ...

Its working now! Thanks for your help!

---

### Post by Bucky Ball on 2012-03-21
My pleasure and excellent news! Enjoy the OS and post back on a new thread with any other questions/problems/issues. ;)

---

