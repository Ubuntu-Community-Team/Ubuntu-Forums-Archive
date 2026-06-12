---
title: "No Ethernet On 10.04"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Multi_User on 2010-05-01
I have an Asus Eee Box 1501B. 

Just installed a fresh copy (not upgraded) of 10.04 Lucid Lynx standard distribution. 

I used apt-get to install gnome-do, openssh-server, and openssh-client. Then I enabled the Accelerated Nvidia Graphics driver. 

After this, I rebooted and the Ethernet connection (not wireless) fails to connect every time. The [collectNWData]("http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English") script tells me that no IP is assigned to the interface. (And yes, the "connect automatically" option is enabled.)

Then I tried disabling the Nvidia Graphics Driver again but there's no difference.
However the Windows OS on the same machine has no problem getting on the network.

The machine is connected to a Linksys router.

Any ideas on how to fix this?

---

### Post by jaybok on 2010-05-01
I had a similar problem, upgraded to 10.04 from 9.10... rebooted etc., no problems.  Today, no internet and no "network connections" icon in panel.  I am hard-wired via a router.

* Solved the "network connections" problem by opening "Run Application" (Alt+F2), type and run: "nm-applet --sm-disable".  The network connections icon now appears in panel.

* Solved "no internet" issue by clicking on icon and check "enable networking".  After a few min, have internet.

Do not know enough of Ubuntu to know if this would help, but that's my $0.02.

---

### Post by Multi_User on 2010-05-02
WTH, now I cannot even get ethernet access from the Windows install and the LED on the router is not even lighting up for that port.

Time for more debugging over here...

---

### Post by Multi_User on 2010-05-02
OK, this has got to be the weirdest night for me in a long time.

I solved it by... powering off the machine AND pulling the plug for 30 seconds, and then booting it back up again.

The only thing I can suggest is that maybe the NVIDIA Chipset Driver install in Linux did something to the hardware (with its integrated Ethernet) that required a full power-down and restart cycle to clear up. Who knows.

I'll add some keywords here so google will pick this up and maybe other people will find it if they have the same problem:
Ubuntu, Linux, Ethernet, Nvidia, Chipset, Driver, no Ethernet, troubleshooting, diagnostic, ifconfig, Windows 7, Asus, Eee box, EB1501, EB1201

---

### Post by framplinux on 2010-05-04
> **Multi_User said:**
> ...The [collectNWData]("http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/Benutzeranleitung/Usersguide-von/of-collectNWData.html#English") script tells me that no IP is assigned to the interface. (And yes, the "connect automatically" option is enabled.)
And it also tells you to post the contents of collectNWDatat.txt in your favorite Linux forum to provide useful information for us who want to help if you don't have success to solve the problem on your own ;)

---

### Post by Iowan on 2010-05-04
> **Multi_User said:**
> 
I solved it by... powering off the machine AND pulling the plug for 30 seconds, and then booting it back up again.
I can mark your thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") - but so can you :)
(It's that "teach a man to fish" thing...)

---

### Post by Parhel on 2010-11-07
> **Multi_User said:**
> OK, this has got to be the weirdest night for me in a long time.

I solved it by... powering off the machine AND pulling the plug for 30 seconds, and then booting it back up again.

The only thing I can suggest is that maybe the NVIDIA Chipset Driver install in Linux did something to the hardware (with its integrated Ethernet) that required a full power-down and restart cycle to clear up. Who knows.

I'll add some keywords here so google will pick this up and maybe other people will find it if they have the same problem:
Ubuntu, Linux, Ethernet, Nvidia, Chipset, Driver, no Ethernet, troubleshooting, diagnostic, ifconfig, Windows 7, Asus, Eee box, EB1501, EB1201

Mate, I wish I could shake your hand! I have the eb1501 as well.  I installed ubuntu minimal on it so I could have an XBMC box. I wanted to have both wired and wireless connected so my android would work as a remote. After mucking around with wpa_supplicant and networking from the CLI, eventually the ethernet stopped working. I could not get it working again. Even a reinstall of a new OS did not fix the problem!

I was ready to chuck the box out until I stumbled across your post. Many thanks!

---

### Post by Multi_User on 2010-11-07
Glad to be of help! :)

---

### Post by orlywon on 2011-02-10
> **Multi_User said:**
> OK, this has got to be the weirdest night for me in a long time.

I solved it by... powering off the machine AND pulling the plug for 30 seconds, and then booting it back up again.

The only thing I can suggest is that maybe the NVIDIA Chipset Driver install in Linux did something to the hardware (with its integrated Ethernet) that required a full power-down and restart cycle to clear up. Who knows.

I'll add some keywords here so google will pick this up and maybe other people will find it if they have the same problem:
Ubuntu, Linux, Ethernet, Nvidia, Chipset, Driver, no Ethernet, troubleshooting, diagnostic, ifconfig, Windows 7, Asus, Eee box, EB1501, EB1201

Thank you! Thank you!  Thank you!

I was having the same issue with my HP Mini 1010NR using a Marvell 88E8040 controller, I followed your instructions and it works great now.

---

### Post by perspectoff on 2011-02-10
Not unique to your hardware. 

The same problem and solution happened (off and on) on every computer I have used since Lucid. The problem ended up being with Network Manager.

After about 4 months of this occurring intermittently on multiple computers with lots of different hardware, I chucked Network Manager on every computer and now use Wicd instead. No more problems.

You'll see. If your problems ends up recurring a few times over the next few months, try out Wicd.

---

### Post by dgizzle on 2011-02-24
> **jaybok said:**
> I had a similar problem, upgraded to 10.04 from 9.10... rebooted etc., no problems.  Today, no internet and no "network connections" icon in panel.  I am hard-wired via a router.

* Solved the "network connections" problem by opening "Run Application" (Alt+F2), type and run: "nm-applet --sm-disable".  The network connections icon now appears in panel.

* Solved "no internet" issue by clicking on icon and check "enable networking".  After a few min, have internet.

Do not know enough of Ubuntu to know if this would help, but that's my $0.02.

This actually worked for me .. thanks!

---

### Post by jaybok on 2011-02-24
> **dgizzle said:**
> This actually worked for me .. thanks!

Glad could help and contribute.  Enjoy Ubuntu!

---

### Post by christopherbalz on 2011-04-09
Related: [http://ubuntuforums.org/showpost.php?p=10655639&postcount=14](http://ubuntuforums.org/showpost.php?p=10655639&postcount=14)

---

### Post by christopherbalz on 2011-04-09
> **Multi_User said:**
> OK, this has got to be the weirdest night for me in a long time.

I solved it by... powering off the machine AND pulling the plug for 30 seconds, and then booting it back up again.

The only thing I can suggest is that maybe the NVIDIA Chipset Driver install in Linux did something to the hardware (with its integrated Ethernet) that required a full power-down and restart cycle to clear up. Who knows.



Thanks for the fix - worked for me w/ 10.04 and NVidia special-effects recently enabled. I had the same issue with eth0, although wireless was unaffected.

---

### Post by rony123 on 2011-07-28
:confused: I tried all the options posted by you.. I am very new to ubuntu. Can anyone explain me step by step on how to resolve this problem of no ethernet. M very much fed up and on the verge of removing Ubuntu from my lappy
Kindly Help!!!

---

### Post by MorganHite on 2011-10-19
> **Multi_User said:**
> OK, this has got to be the weirdest night for me in a long time.

I solved it by... powering off the machine AND pulling the plug for 30 seconds, and then booting it back up again.

The only thing I can suggest is that maybe the NVIDIA Chipset Driver install in Linux did something to the hardware (with its integrated Ethernet) that required a full power-down and restart cycle to clear up. Who knows.

I'll add some keywords here so google will pick this up and maybe other people will find it if they have the same problem:
Ubuntu, Linux, Ethernet, Nvidia, Chipset, Driver, no Ethernet, troubleshooting, diagnostic, ifconfig, Windows 7, Asus, Eee box, EB1501, EB1201
I had the same problem (on a Dell Vostro 3700 running 10.04 Lucid) and I have to say your solution worked!  I powered off, unplugged for 30 seconds and then powered up again. My jaw nearly hit the floor when I saw the ethernet card was working again. Thanks!

---

### Post by BunTai on 2012-02-28
> **Multi_User said:**
> OK, this has got to be the weirdest night for me in a long time.

I solved it by... powering off the machine AND pulling the plug for 30 seconds, and then booting it back up again.

The only thing I can suggest is that maybe the NVIDIA Chipset Driver install in Linux did something to the hardware (with its integrated Ethernet) that required a full power-down and restart cycle to clear up. Who knows.

I'll add some keywords here so google will pick this up and maybe other people will find it if they have the same problem:
Ubuntu, Linux, Ethernet, Nvidia, Chipset, Driver, no Ethernet, troubleshooting, diagnostic, ifconfig, Windows 7, Asus, Eee box, EB1501, EB1201

Thanks.. its helps!!! :o:o:o

---

