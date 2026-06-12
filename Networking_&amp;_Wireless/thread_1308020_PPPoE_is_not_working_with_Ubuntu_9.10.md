---
title: "PPPoE is not working with Ubuntu 9.10"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by razibhasan on 2009-10-31
Hello there,
I have installed Ubuntu on my desktop a few hours ago. Unfortunately, I don't get internet connection with ubuntu 9.10.

Here is how I connected to the internet on my Windows OS and MAC OSX Snow Leopard.

- There is a switch in my home where the uplink is connected.
- From the switch one cable goes to my MacBook Pro and another one is in my PC.
- It requires a User ID and Password to be connected to the internet (using PPPoE) both on Mac and Windows 7.
- They don't use any IP or anything (I mean IPV4).

I have tried several times but no luck. Simply it doesn't connect to the internet.

I have used the following method on Ubuntu 9.10.

- From the Network Icon on the system tray I clicked the right button - Edit Networks >> DSL >> I have gave my user ID and Password there (Service name was left blank).

Duh! It doesn't work. Why is everything so complicated on Linux? On Ubuntu 9.04 I was running the internet fine but with 9.10 it doesn't work at all.

Any help?

---

### Post by bogdan.veringioiu on 2009-11-01
Hi.
It looks like you are hitting the bug 432205:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/432205)
It looks like it is fixed, but you need to upgrade your network manager via ppa.
Or, as a workaround (until the fix is pushed in the main stream of updates), you can set up your connection, using pppoeconf:
```
sudo pppoeconf
```
..(then follow the wizard and enter the username, pass, and go with the defaults).
Then connect with:
```
sudo pon dsl_provider
```
..assuming your connection name is dsl_provider.

See additional forum threads:
[http://ubuntuforums.org/showthread.php?p=8204222#post8204222](http://ubuntuforums.org/showthread.php?p=8204222#post8204222)
[http://ubuntuforums.org/showthread.php?t=1307107&highlight=network+manager+dsl](http://ubuntuforums.org/showthread.php?t=1307107&highlight=network+manager+dsl)

Bogdan

---

### Post by alanrr_sr on 2009-11-01
Can empathy work with this workaround? I am not able to connect with it.

---

### Post by bogdan.veringioiu on 2009-11-02
Actually, I tried yesterday to connect with empathy, after setting up the pppoe connection, but i was not able to...
I suspect the integration with networkmanager, and the fact that the internet connection is not managed by nm..
Bogdan

---

### Post by NunoZA on 2010-01-08
Just wanted to say thanks, this sorted my PPPoE connection out.

---

### Post by kuurozaki on 2010-01-09
same problem on my unr 9.10.. I can't get the adsl connection to work... after updating the network manager via ppa its work! thanks bogdan.veringioiu :D[URL="http://ubuntuforums.org/member.php?u=95800"]
[/URL]

---

### Post by ajsc on 2010-01-10
I am unable to use sudo pppoeconf as it does not provide the option of entering service provider name field.  could some one tell me how and which file to download from ppa through windows and how to install it in karmic.

---

### Post by Fiable.biz on 2010-01-20
And, for a newbie coming from Mandriva who have installed Ubuntu yesterday, **what is "ppa"?**

---

### Post by bogdan.veringioiu on 2010-01-20
Hi.
See this:
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

"Personal Package Archives (PPA) allow you to upload Ubuntu source packages to be built and published as an apt repository by Launchpad."

Developers maintain different versions (usually newer versions, or development branches) of software packages.
You can add the ppa url in apt sources list, and install the packages.
Bogdan

---

### Post by Fiable.biz on 2010-01-20
Thank you. But I remind you that the problem is that I don't have the network on that computer, so that adding any URL would not change anything for the moment. Or do you mean I should launch "sudo pppoeconf", then "sudo pon dsl_provider", **and** then I should upgrade my network manager from that? You wrote "**or**, as a workaround", so I thought your advice was to download the package from another computer and install it, but I don't know how and [ajsc]("http://ubuntuforums.org/member.php?u=882126") above has the same problem as me.

On the page you gave me the url of, if I look for "network manager", I get... 181 results... Which PPA is to be chosen?
Should I download all the 6 *.dev "Built files" of
[https://launchpad.net/ubuntu/+source/network-manager/0.8~a~git.20091013t193206.679d548-0ubuntu1/+build/1292626]("https://launchpad.net/ubuntu/+source/network-manager/0.8%7Ea%7Egit.20091013t193206.679d548-0ubuntu1/+build/1292626")
?

---

### Post by bogdan.veringioiu on 2010-01-20
Sorry, the response was kind in a hurry.
You can try, indeed 2 things:
1)Configure your connection with pppoeconf.
Then connect to the internet with 
> sudo pon dsl_provider

The apt url for the network manager ppa trunk are:

> deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
You will find them on this page:
[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

Try adding the lines above at the end of your /etc/apt/sources.list.
After this, you do:
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BC8EBFE8

then
> sudo apt-get update
sudo apt-get upgrade
In this way, you will upgrade network manager to the version maintained in the trunk.
After a reboot, you should be able to configure your dsl connection from within network manager.

2)Go to a computer that has an internet connection,
and manually download the package network-manager (for karmic)
from
[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

After this, try to install it. However this is something I did not try...

Let me know if any of these steps works for you.
Cheers
Bogdan

---

### Post by Fiable.biz on 2010-01-20
Thank you very much indeed. The installation of Ubuntu is not very smooth (2 problems for a default installation), but now it works. Since the initiator of this thread never appeared again, to my mind, this thread can be tagged as solved. Maybe copying what you wrote to the wiki would be a good idea.

---

### Post by bogdan.veringioiu on 2010-01-21
I am glad you have it working.
Indeed this is a very frustrating bug, regarding network manager.
I hope in lucid this bug will not exist with the default installation.

Bogdan

---

### Post by ajsc on 2010-02-15
Man this network manager sucks.  I have tried the network manager version of ppa. But it is still buggy.  For example while trying to switch from one dsl connection to another the computer refuses to connect to the second dsl connection. Also sometimes the computer hangs and caps lock and scroll lock lights just keep on blinking.  Any solutions.

---

### Post by JlyGrnMigt on 2010-02-26
So I added that source, ran the update manager, installed, and rebooted.  Now the network manager doesn't appear in my top bar at all, not even to tell me I'm disconnected.  

I'm currently connected through the workaround, but would like to use my vpn so I need network manager to work.  What am I doing wrong?

---

### Post by bogdan.veringioiu on 2010-02-26
Hi JlyGrnMigt.
What version of ubuntu are you using?
If you open a terminal, and type "nm-applet", what you get?
Bogdan

---

### Post by JlyGrnMigt on 2010-02-27
> **bogdan.veringioiu said:**
> Hi JlyGrnMigt.
What version of ubuntu are you using?
If you open a terminal, and type "nm-applet", what you get?
Bogdan

I'm using UNR 9.10.

when I type that command, it tells me 
An instance of nm-applet is already running.

** (nm-applet:3013): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

I should add that it's now appearing in my top bar because I was attempting to use wireless at a cafe this morning (it didn't work...but that's happened here before this whole mess).  It tells me "device not managed" for the wired connection, which I am using now.

---

### Post by bogdan.veringioiu on 2010-02-27
Ok.
Now that you have the upgraded version of the network manager, you should be able to configure your dsl connection in nm.
Try to create the dsl connection, disconnect pppoe, and connect via network manager.
Bogdan

---

### Post by JlyGrnMigt on 2010-02-27
Hi Bogdan, thanks for your help here.  Because I was getting the "device not managed" error with NM, I followed the directions in this thread: [http://ubuntuforums.org/newreply.php?do=newreply&p=7612600](http://ubuntuforums.org/newreply.php?do=newreply&p=7612600)

I rebooted, selected my dsl connection from the list, and it worked!

My computer is now rockin' out in Los Angeles while I sit here in China ;)

---

### Post by bogdan.veringioiu on 2010-02-28
Hi.
Glad that you made it working.
Cheers.
Bogdan

---

