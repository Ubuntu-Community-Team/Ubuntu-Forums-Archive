---
title: "Acer AO722 Ubuntu 12 wireless problem - Belkin"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by piotrbb1 on 2013-02-20
Hello,

First I'd really like to thank you the forum people for great help they've been giving me so far. Although I'm a new member it's simply because all my problems so far have been resolved by simply reading the old threads. Now I have a problem that just puzzles me so I have to ask sb's help. Here it goes:
The computer is Acer AO722
System - Ubuntu 12
Problem - my computer used to access the Internet(sometimes after a long struggle), now it goes as far as veryfying IP. I have tried both Network Manager and Wicd. I've never had any problems with networks not secured by password. I've never had any problems with other routers - it's Belkin that is doing my head in. Another interesting thing - I also have Ubuntu on my other laptop - Lenovo G550 - connects to Belkin wireless - no problems. Lenovo even deals better with Belkin than my PC - Windows 7. I don't want to mess around with wireless settings because, as I already mentioned, wireless works well with unsecured networks. Any idead about what to do with all this? Thanks for help :-)

---

### Post by wildmanne39 on 2013-02-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by piotrbb1 on 2013-02-21
here it is

---

### Post by piotrbb1 on 2013-02-21
Ok, sorry, I tried to upload the script instead of the netinfo.txt. Stupid of me.

Here it is. :p

---

### Post by westie457 on 2013-02-21
[s]You have posted the wireless script file in error.

If you do not have a netinfo.txt file yet try the suggetions in this post. [http://ubuntuforums.org/showpost.php?p=12317058&postcount=8](http://ubuntuforums.org/showpost.php?p=12317058&postcount=8)[/s]

Thank you.


EDIT Too late.

---

### Post by piotrbb1 on 2013-02-21
So my last reply is OK? Or should I try something else?

Thanks :p

---

### Post by westie457 on 2013-02-21
First plug in an ethernet cable (I know it sounds like a silly suggestion, a lot of people forget).

Open a terminal and run ```
sudo apt-get install bcmwl-kernel-source
``` Wait 2 minutes and click the Network icon (top-right) for any networks found. If none run ```
sudo modprobe wl
```

Do the wait and check procedure, if nothing unplug the cable and reboot. It should now be working.

Let us know what happens.

Thank you.

---

### Post by piotrbb1 on 2013-02-21
Unfirtunatelly it did not help. I was afraid it wouldn't as right after writing the first command in the terminal it stated that it already exists in my version of the system (12.04)

As for the second command the answer was that it will be ignored from no on.

---

### Post by piotrbb1 on 2013-02-21
What I don't understand is I never once had a problem with the unprotected wireless connections. It's just the protected one, namely Belkin that gives me pains. It keeps asking me the password and either reports bad password or stops at the stage of veryfing IP (Network manager and Wicd). The other computer with Ubuntu (lenovo g550), which connects to Belkin better than a PC with Windows 7 makes it even weirder.

Last time I had this problem using Wicd instead of Network Manager solved it. I can see this time it won't be that easy.

Thank you very much for helping me by the way. I really appreciate it :-)

---

### Post by wildmanne39 on 2013-02-21
Hi, please try what is in this link.
[http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896](http://askubuntu.com/questions/250858/broadcom-wireless-bcm4313-on-12-04-lts/250896#250896)
Thanks

---

### Post by piotrbb1 on 2013-02-21
My GOD you are good!!! Thank you VERY much. The last suggestion worked. I would have never related my problem to the upgrade. Case closed. Now I know why it is said Ubuntu is the best system there is, because of you, of course, the forum people.

Thanks again and all the best (reply written on the AO 722 wireless connection :-)

---

### Post by wildmanne39 on 2013-02-21
Glad it worked.
Enjoy!

---

