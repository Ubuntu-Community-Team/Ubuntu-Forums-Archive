---
title: "Ubuntu 9.04 and UbuDSL"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by nerotkd on 2009-04-26
Hello! First, sorry about my bad english, i'm from Argentina...

Yesterday, I have updated Ubuntu to Jaunty Jackalope, and my connection stop working (After that, i was using 8.10 and UbuDSL as a modem manager, with a Speedtouch 330 modem)...

After a little search in google, I found that a 9.04 compatible version was now downloadable in ubudsl.com
But, it doesn't works for me...
I installed it, (everything looks okay..) configured it...

But the applet doesn't work:
. It takes 2minutes~ to appear the icon on the top bar... And its not normal...
. It never works. I don't know how to describe what happens. But it takes a lot of minutes to OPEN THE UI.... And it hangs on.

---

### Post by advocatus on 2009-04-26
Hi! I also have a couple of glitches (fresh 9.04 install + ubudsl_1.0.0.295-1jaunty_i386.deb)

1. Daemon problems upon startup. (Workaround: sudo /etc/init.d/ubudsld start)

[[IMG]http://img14.imagevenue.com/loc756/th_35918_Screenshot_122_756lo.jpg[/IMG]](http://img14.imagevenue.com/img.php?image=35918_Screenshot_122_756lo.jpg)

2. Button images missing in applet GUI.

 [[IMG]http://img250.imagevenue.com/loc113/th_32258_UbuDSL_122_113lo.jpg[/IMG]](http://img250.imagevenue.com/img.php?image=32258_UbuDSL_122_113lo.jpg)

---

### Post by Yperborea on 2009-04-26
I have exactly the same problem. I can connect to the web just after the UbuDSL configuration (without restarting my computer), but as the applet is not working (same error message as advocatus and nerotkd), I can't connect anymore everytime I restart my computer because the applet can't be launched. 
As a consequence, in my case, I have to uninstall and install Ubudsl again every time I start my computer, if I want to be connecter to the web.
I use fresh 9.04 install + ubudsl_1.0.0.295-1jaunty_i386.deb, as advocatus, and my modem is a Speedtouch 330 (Alcatel) one.

(Sorry for my bad english too...I'm french. I hope you understood my problem :()

---

### Post by t0mppa on 2009-04-26
Since this looks like a problem concerning UbuDSL itself, rather than something to do with purely Ubuntu side of networking, have you tried sending an email with your log attached to it to [email]ubudsl@gmail.com[/email]? Like it says on the UbuDSL website about encountering problems not listed in the FAQ.

Seems like the easiest way of troubleshooting for me, as then you're bound to catch someone who knows what he's talking about. Here on the forums, you might or might not reach a person with lots of UbuDSL experience, depending on how popular the software is (haven't personally seen any other threads abou it).

---

### Post by Yperborea on 2009-04-26
I tried to an hour ago!

UbuDSL's answer:

[I]We are terribly sorry but the development of UbuDSL has temporarily
been suspended. If you have a problem with UbuDSL please contact your
local Linux distribution's community.[/I]

---

### Post by t0mppa on 2009-04-26
Allright, let's hope there's someone on the forums who can help the three of you then.

---

### Post by advocatus on 2009-04-26
[QUOTE=Yperborea]I have exactly the same problem. I can connect to the web just after the UbuDSL configuration (without restarting my computer), but as the applet is not working (same error message as advocatus and nerotkd), I can't connect anymore everytime I restart my computer because the applet can't be launched. 
As a consequence, in my case, I have to uninstall and install Ubudsl again every time I start my computer, if I want to be connecter to the web.
I use fresh 9.04 install + ubudsl_1.0.0.295-1jaunty_i386.deb, as advocatus, and my modem is a Speedtouch 330 (Alcatel) one.
problem :()[/QUOTE]

You might try my workaround: Right-click on desktop->Create Launcher and enter command **gksudo /etc/init.d/ubudsld start**. It's a nuisance, but works for me.

[QUOTE=Yperborea]We are terribly sorry but the development of UbuDSL has temporarily
been suspended. If you have a problem with UbuDSL please contact your
local Linux distribution's community.[/QUOTE]

Strange, it was released (or at least re-packaged) 4 days ago -> [http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/]("http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/")

At least we got the source, someone might figure it out :)

---

### Post by Yperborea on 2009-04-27
> You might try my workaround: Right-click on desktop->Create Launcher and enter command **gksudo /etc/init.d/ubudsld start**. It's a nuisance, but works for me.

It doesn't work with my evil computer. I'm giving way to despair [-o<

---

### Post by advocatus on 2009-04-28
> **Yperborea said:**
> It doesn't work with my evil computer. I'm giving way to despair [-o<

Try this first

```
sudo kill -9 `pidof ubudsldaemon`
```

then
```

sudo /etc/init.d/ubudsld start
```

Anyway, the author (adrian) seems to be tied up at the moment according to Polish Ubuntu forums.

---

### Post by javierock on 2009-04-30
Hi Guys

I've got exactly the same problem.
Every time that i want use internet on my USB modem i have to Configure the UbuDSL connection...and that's annoying.

I'm not sure if that's the reason, but in the Startup Applications doesn't appears the UbuDSL Daemon, just the Applet, however, adding the daemon (usr/sbin/ubudsldaemon) to the startup applications doesn't fix the problem.

I send an e-mail to Ubdsl@gmailcom but i receive an automatic response...the same message that wrote Yperborea.

(Sorry for my English)

---

### Post by Darles on 2009-05-01
Hi,

I have the same problem. I found that i can get it running with:

```
sudo ubudsldaemon
```

And then after that i can use the internet fine but i have to start the daemon each time i boot.

---

### Post by JohnMetal on 2009-05-07
Hiii

I have this problem too

So I make this:

-Installed UbuDSL Intrepid (8.10)
-So, Synaptic will broke...then boot in recovery mode and go to option "dpkg" to repair Synaptic
-Open UbuDSL Applet
-Use  the comand posted by Darles (This have to be maked every time you booted) 
> sudo ubudsldaemon-And internet is working =]
Sorry by english

I'm from Brazil:)

---

### Post by balcis on 2009-05-08
my problem is not to do the settings after every boot. I just can not connect to the internet. I install ubudsl, then it says it started daemon, I check it, but when I ran the applet, it says daemon is not running and it's interface is so deadly slow! after I stop the daemon, it's UI starts to respond then? here's my command output.

```
root@BALCIS-EV-UBUNTU:~# /etc/init.d/ubudsld stop
 * Stopping UbuDSL Daemon ubudsldaemon                                          
UbuDSL Daemon: Signal 15 handled
  - No daemon instance found!
                                                                         [ OK ]
root@BALCIS-EV-UBUNTU:~# /etc/init.d/ubudsld start
 * Starting UbuDSL Daemon ubudsldaemon                                   
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be 
ignored in a future release.
[ OK ]
root@BALCIS-EV-UBUNTU:~# UbuDSL_Applet
disconnected 
invalid 
loadModules() 
Applet::loadModules(): "/usr/lib/ubudsl/modules/libubudsl_module_connection_log_viewer.so" module_init symbol resolved successfully. 
ConnectionLogModule: module_init.
Applet::loadModules(): "/usr/lib/ubudsl/modules/libubudsl_module_sound.so" module_init symbol resolved successfully. 
SoundModule: module_init.
UbuDSL Daemon: Signal 15 handled
  - No daemon instance found!

```

---

### Post by JohnMetal on 2009-05-13
[B][U]Balcis

[/U][/B]_You'are using Ubudsl 9.04?Try use the 8.10 version, the interface of the Jaunty Ubudsl is slow for me too_[B][U]
[/U][/B]

---

### Post by balcis on 2009-05-13
> **JohnMetal said:**
> [B][U]Balcis

[/U][/B]_You'are using Ubudsl 9.04?Try use the 8.10 version, the interface of the Jaunty Ubudsl is slow for me too_[B][U]
[/U][/B]

if i try to install it, it just gets back to the login screen and then my wireless (usb) keyboard and mouse don't work. then i start with system rescue option and use "dpkg" but it still doesn't work, bu today i tried to install 8.10 version again and i just had to copy "ubudsld" file from the deb package to /etc/init.d/ manually, (because it was 0 byte) so i tried to get it work, it said "it couldn't register the service ubudsld" or something and again and again i couldn't get ubudsl applet recognize ubudsl daemon is running. 

so; sadly, until i'm able to connect to the internet (thanks to ubudsl 'til this time) i'm on pardus that makes me connect through my usb adsl modem easily or windows 7. i'm following this thread for any possible solutions also.

---

### Post by rogper on 2009-05-20
I'm having the same issue... Every thing worked smootly in 8.10 but after updating to 9.04 :(
I have the USB modem **Sagem F@st 800 E4 **and I have to run the Daemon every time I want to connect to the internet. Sometimes I need to restart the PC because the Daemon is running but apparently sleeping and when that's the case it never connects even if I run the Daemon again.

Once I've read a message warning that Ubuntu is abandoning some kind of configuration storage (sorry I'm writing from mind)... so I thought that may be the issue.

Anyway I give a Big Thanks to the developer of UBUDSL, without this great application I wouldn't have Internet at all ;)

---

### Post by john lennon on 2009-05-22
My 2 cents...

I've installed a new version of ubuntu 9.04 and after few hours to try to make ubudsl for 9.04 to work, I tried [JohnMetal]("http://ubuntuforums.org/member.php?u=816873") tips...
It's working perfectly (except that it's a little bit frightening for a linux newbie like me).

.Install ubuntu 9.04
.Install ubudsl for 8.10 using Synaptic (that crashes Synaptic)
.Reboot in recovery mode and ask for dpkg
.Reboot in normal mode
.kill -9 `pidof ubudsldaemon`
./etc/init.d/ubudsl start

It seems you have to do the 2 latest operations after every system restart (if anybody knows how to do that automatically, it will help me - I'm really a linux newbie ;)).

And the UbuDSL_Applet works perfectly now (after killing and restarting the daemon, the applet icon appears)

...

Thanks to JohnMetal for the tips.

---

### Post by advocatus on 2009-05-29
Seems to be fixed now ;)

[http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/ubudsl_1.0.0.300-7jaunty_i386.deb]("http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/ubudsl_1.0.0.300-7jaunty_i386.deb")
[http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/ubudsl_1.0.0.300-7jaunty_amd64.deb]("http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/ubudsl_1.0.0.300-7jaunty_amd64.deb")

---

### Post by Darles on 2009-05-29
Yeah works great for me. Thanks advocatus!

Darles

---

### Post by rogper on 2009-05-29
Yeah! Works great again here too :) Thanks a bunch!

---

### Post by Yperborea on 2009-05-30
Greaaaaaat! Thank you very much for this news. Work perfect for me.:D

---

### Post by AndrasITC on 2009-06-08
I also had a problem with my sagem adsl modem, but now it is ok. Now I have a new problem. The ubudsl shows that I am connected, but I cannot access the internet. I set the proxy in the Firefox but it doesn't help. Also when I try to update my Ubutnu 9.04 from the terminal window, it reports an error. What else do I have to set?

---

### Post by Pug59 on 2009-07-10
> **advocatus said:**
> Seems to be fixed now ;)

[http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/ubudsl_1.0.0.300-7jaunty_i386.deb](http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/ubudsl_1.0.0.300-7jaunty_i386.deb)
[http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/ubudsl_1.0.0.300-7jaunty_amd64.deb](http://ppa.launchpad.net/adrian5632/ubuntu/pool/main/u/ubudsl/ubudsl_1.0.0.300-7jaunty_amd64.deb)

1st post and a big thanks after joining here and doing a search i found this thread and using the 64bit package i'm now surfing the net via Ubuntu 9.04 and a Speedtouch 330 modem yehaa 

thanks so much ):P;)

---

