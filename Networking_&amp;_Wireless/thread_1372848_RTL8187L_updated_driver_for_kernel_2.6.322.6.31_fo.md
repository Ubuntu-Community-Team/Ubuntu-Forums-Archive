---
title: "RTL8187L updated driver for kernel 2.6.32/2.6.31 for ALFA AWUS036H"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by promicin on 2010-01-05
Hi, i have ALFA AWUS036H 500mw wireless card which uses RTL8187L chipset. Ubuntu 9.04 and 9.10 come with preloaded rtl8187 driver but they DO NOT work for internet surfing. However they do work with aircrack suit for injecting etc. Specific problem is: They only work with really close ranged AP, anything far and you will have random disconnects or inability to connect. So basically its unstable compared to patched driver.

To get this alfa card working for internet access, the only way currently is to use any LInux distro with Kernel 2.6.30 and lower. Starting from Kernel 2.6.31 they have made some changes to net api structure which wont let you patch the driver with the patch available at aircrack website which is normally used to make this driver suitable for internet browsing. Refer to this thread for more info: [http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

I am currently using backtrack 4 pre final but i was going to install kubuntu 9.04 till i recieved an email from realtek with a new driver that compiles in kernel 2.6.31. I tested it on Kubuntu 9.10 and it compiled fine but i could not make it run. Under NetworkManagement for Kubutnu, the problem is that it keeps asking for WEP key and gives me the message 'wlan4 failed to connect' instantly after i enter the key, so its possible that its not compatible with NetworkManagement. I havent tried it with wicd yet, it may work. Manually, i tried to connect it with the commands: iwconfig wlan4 ap XXXXX key XXXX and then iwconfig and it shows the essid which is new because with previous default drivers that come with 9.10, running the above command would not work and if you did iwconfig it will say ESSID: ""

So there is hope here which is good, its just a matter of time till some good people out there patch this driver to make it work not only in 9.10 but also with its network management plasma thats so cool to look at. And then finally i can call 9.10 my new home lol

here is the driver: [http://www.4shared.com/file/188631523/a725eefa/rtl8187L_linux_26103901042010r.html](http://www.4shared.com/file/188631523/a725eefa/rtl8187L_linux_26103901042010r.html)

---

### Post by promicin on 2010-01-07
bump for feedback

---

### Post by promicin on 2010-01-08
its also posted on the bugtracker here [https://bugs.launchpad.net/ubuntu/+bug/455354](https://bugs.launchpad.net/ubuntu/+bug/455354)

if you have the same issue, i suggest you contact realtek at jasaonchang(at)realtek.com and explain to them that ubuntu/kubuntu 9.10 comes with rtl8187L driver that seems to work, detects all the networks properly and even connects to them HOWEVER if the AP is 70% or lower in signal strength then you cannot surf the internet or have any internet activity that includes even pinging ALTHOUGH you will stay connected to the AP just wont have any internet activity. This is the real issue with the rtl8187L driver and it needs to be fixed for karmic 9.10 or kernel 2.6.31+

Also request people at aircrack-ng to make a patch for the driver i have provided here [http://forum.aircrack-ng.org/index.php?topic=5755.msg34768#msg34768](http://forum.aircrack-ng.org/index.php?topic=5755.msg34768#msg34768)

Go to the first page to see instructions of how to compile r8187 driver which works with ubuntu 9.04 or with kernel 2.6.30 and lower.

Please, people we need your voices to make this happen. Thanks

---

### Post by bedhead75 on 2010-01-08
I've confirmed the bug on launchpad and also sent an e-mail to Realtek.  I notice that when I turn off encryption on my network, my internet download speed increases 10X (80kb/s with wpa2, 800kb/s with an open network).  Has anyone else noticed this?

  Obviously this issue needs to be fixed as using only open networks are a security issue.

---

### Post by promicin on 2010-01-08
Technical details about this issue here: [http://bugzilla.kernel.org/show_bug.cgi?id=14168](http://bugzilla.kernel.org/show_bug.cgi?id=14168)

---

### Post by bedhead75 on 2010-01-11
I e-mailed Realtek and they sent me the latest drivers, which apparently are exact same as the ones in the link that you posted up earlier.  You said they now compile fine in Ubuntu 9.10 but there are still some issues with them and network manager...and perhaps additional issues right?  I'm just curious but how they work if you manually configure your networks using the terminal interface, and has the internet connectivity improved for connecting to more distant (<70%) networks?  What exactly doesn't work still?  I'm pretty new learning how to compile and stuff so I'm just curious if fiddling with these new drivers are worth my while or not.  Thanks.

---

