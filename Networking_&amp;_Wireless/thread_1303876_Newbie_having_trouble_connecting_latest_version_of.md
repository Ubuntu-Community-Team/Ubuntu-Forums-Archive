---
title: "Newbie having trouble connecting latest version of Ubuntu to internet via DSL ?"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by logicfox* on 2009-10-28
Hello, I'm a bit of a Linux newbie. I just downloaded and installed the latest version of Ubuntu as a dual boot with my Windows XP Pro OS. I can't connect to the internet with my Ubuntu, even though everything's still fine on Windows. I have a Westell 6100F modem with a DSL connection. Verizon is my internet service provider. I have tried clicking on the Network Manager in the top-right and hitting "DSL", "Add", but it doesn't work. It just gives me blank spaces, and I don't know what to put in them. I've tried some stuff, but nothing works. I have tried multiple things, but to no avail :( If anybody could help out a poor newbie in need, I'd appreciate it. Thanks!

---

### Post by razorboy5 on 2009-10-28
run network manger by

alt+f2 and type

nm-applet

then try lookin on the top right see if ur wireless is visible

---

### Post by Iowan on 2009-10-28
My DSL modem takes care of all the dirty work - I connect to it like a router.  Might not work for you, but try using "Auto eth0" and see if it gets IP address. (**ifconfig -a**)

---

### Post by Alcarcalimo on 2009-10-29
I have the same problem. My Ubuntu Jaunty DSL connection was working fine, but my Karmic isn't. According to [this post]("http://www.linuxquestions.org/questions/showthread.php?p=3713785#post3713785"), Karmic no longer accepts DSL connections.

If this is true is there a way to go around this problem?

---

### Post by Iowan on 2009-10-29
That'd be unfortunate for those of us who just "upgraded" to DSL.  I suspect there's still a way via /etc/network/interfaces...

---

### Post by James.Dedon on 2009-10-31
I can confirm that this is a bug.  See bug #438771 on Launchpad.  Your best bet is to stay with Jaunty for now if you don't have any other way to connect.  I also had the same problem during the release candidate and had to reinstall Jaunty to use my DSL connection.  

It really blows my mind how this bug made it into the final release.  There have been a few bugs listed in launchpad for almost a month and they're still not assigned!

---

### Post by normanp on 2009-10-31
> **James.Dedon said:**
> I can confirm that this is a bug.  See bug #438771 on Launchpad.  Your best bet is to stay with Jaunty for now if you don't have any other way to connect.  I also had the same problem during the release candidate and had to reinstall Jaunty to use my DSL connection.  

It really blows my mind how this bug made it into the final release.  There have been a few bugs listed in launchpad for almost a month and they're still not assigned!

So whose job was it to deal with this? Can they respond on this forum please?

Is Ubuntu trapped by version numbering to release in October even if it not ready - now that has to be really crazy! Better to announce a delya and release Ubuntu 9.12 - what is wrong with that?

---

### Post by mutesounds on 2009-10-31
I have no problem using my DSL connection on 9.10

---

### Post by aventura_alex on 2009-10-31
[SIZE=4]I'm facing the same problem as many of you. I tried to install 9.10 from windows xp in 2 ways. First time I even uninstalled my 9.04 Ubuntu and run a clean install. Second time I reinstalled 9.04 and then updated to Karmic. No matter how I did, it was always the same: dsl internect connection used to work then dsl internect connection doesn't work any more. I'm partially glad to learn that there is a bug reported and I'm not the only one facing this problem, what gives me hope it will be fixed soon. I have a **[COLOR=Blue]bet[/COLOR]** on this though, I think there might be something related to **[COLOR=Blue]ipv6 support[/COLOR]**, since before there was only ipv4 support and things used to go smoothly. As I can't stay too long away from my Ubuntu I will reinstall my jaunty and wait till the problem is fixed. **[COLOR=Blue]I hope they let us know[/COLOR]** when it is the case so that we don't need to try to reinstall every other week with no success.
by the by, my first time here. Nice to meet you folks :)

:popcorn:

[/SIZE]

---

### Post by freakcode on 2009-10-31
For those having problems with DSL on 9.10: you try configuring the connection via the terminal with 'pppoe-conf'. This bypasses Network Manager and make things just work.

PS: I'm baffled by this bug. I can't believe after so many releases Ubuntu still manages to break things that were just working, like sound or network connection. I'm going Mac on my next acquisition.

---

### Post by Neilkd on 2009-10-31
I just obtained Ubuntu 9.10 on the basis that it was the latest & greatest. Rather disappointed to discover that I can't connect to the net with my DSL connection.
 
I'm a total newbie to Linux so can someone please explain how to configure via the terminal using pppoe-conf. I tried <Alt>F2 and entered pppoe-conf and clicked run. Error message telling me that it couldn't find the command.
 
Any help will be appreciated.

---

### Post by rax0 on 2009-10-31
I'm impressed by Karmic but a little bit disappointed, I managed to get my DSL working but not with Network-manager, I'll explain all what I did, maybe you'll find some steps useless but I'll mention them anyway,

First go to the terminal ( Alt+F2 then write gnome-terminal)

1. ```
sudo pppoeconf
```enter you password

then follow the steps and enter you (username/password)

then you can either use 

```
sudo  pon dsl-provider
```, ```
sudo poff -a 
```or use gpppon (you should install it first)

or ```
sudo ifconfig ppp0 up
```I'm still experimenting but one of them should work fine with you.

---

### Post by meho_r on 2009-10-31
> **freakcode said:**
> For those having problems with DSL on 9.10: you try configuring the connection via the terminal with 'pppoe-conf'. This bypasses Network Manager and make things just work.

PS: I'm baffled by this bug. I can't believe after so many releases Ubuntu still manages to break things that were just working, like sound or network connection. I'm going Mac on my next acquisition.

I'm not sure if it's Ubuntu's fault. Network Manager has always been a very buggy piece of software. However, this bug is solved using [Network Manager daily PPA.](https://launchpad.net/~network-manager/+archive/trunk)

---

### Post by Neilkd on 2009-10-31
Hi, Thanks for your help. I went through the steps you gave and can now connect to the internet. Unfortunately the process also destroyed my automaticaly established local network connection. 
 
Any isead how I can get that back and have both? Network Manager seems to be sulking after being bypassed for the pppoe connection.

---

### Post by bob brazie on 2009-10-31
How do I become root to run this command?

New to this.

---

### Post by rax0 on 2009-10-31
> **Neilkd said:**
> Hi, Thanks for your help. I went through the steps you gave and can now connect to the internet. Unfortunately the process also destroyed my automaticaly established local network connection. 
 
Any isead how I can get that back and have both? Network Manager seems to be sulking after being bypassed for the pppoe connection.

I usually open /etc/NetworkManager/nm-system-settings.conf as root and edit "managed=flase" to "true" then save and restart, that should do it.

> **bob brazie said:**
> How do I become root to run this command?

New to this.

use "sudo" before you commands, or "sudo su" (alone) and write the commands after that.;)

---

### Post by d0b33 on 2009-11-01
> **Neilkd said:**
> Hi, Thanks for your help. I went through the steps you gave and can now connect to the internet. Unfortunately the process also destroyed my automaticaly established local network connection.

You'll need to comment out a few lines that pppoeconf made here...
```
sudo gedit /etc/network/interfaces
```

this is mine...
```
#default>
auto lo
iface lo inet loopback

#pppoeconf>
iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

#auto eth0
#iface eth0 inet manual
```

---

### Post by bob brazie on 2009-11-01
Thanks but I get a command not found when I try pppoe-conf.

---

### Post by rax0 on 2009-11-01
it's "pppoeconf" not "pppoe-conf"

and to everyone, it's really fixed now, with this/ 
          
> I'm not sure if it's Ubuntu's fault. Network Manager has always been a very buggy piece of software. However, this bug is solved using [Network Manager daily PPA.]("https://launchpad.net/%7Enetwork-manager/+archive/trunk")

---

### Post by yiit on 2009-11-01
use this ppa instead:

[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

---

### Post by 600WPMPO on 2009-11-01
> **meho_r said:**
> I'm not sure if it's Ubuntu's fault. Network Manager has always been a very buggy piece of software. However, this bug is solved using [Network Manager daily PPA.](https://launchpad.net/~network-manager/+archive/trunk)

> This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources.

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main 

Signing key:
    1024R/BC8EBFE8
Fingerprint:
    8B6C49916FD28CBDFC5DA3A2248DD1EEBC8EBFE8 

> Adding the PPA to Ubuntu

Step 1: Copy the first line from the apt sources.list entries section of the PPA overview page.


Step 2: On your Ubuntu computer, open System > Administration > Software Sources.

Step 3: Click the Third Party Software tab.


Step 4: Click the Add button.

Step 5: Paste the line you copied in step 1 and click the Add Source button.

Step 6: Now copy the second line from the apt sources.list entries section of the PPA overview page and paste it in just as you did in steps 4 and 5.

When prompted, reload the software sources information. Don't worry if you see a warning about unverified software sources; we're going to fix that next.
Telling Ubuntu how to authenticate the PPA

Now Ubuntu knows about the PPA. It also needs to know how to check the software hasn't been tampered with since Launchpad built it.


Step 1: On the PPA's overview page you'll see the PPA's OpenPGP key id. It'll look something like this: 1024/12345678. Copy it, or make a note of, the portion after the slash, e.g: 12345678.

Step 2: Open your terminal and enter:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678

Replace 12345678 with the key id you copied in step 1.

Step 3: Finally, tell Ubuntu to re-load the details of each software archive it knows about:

sudo apt-get update

You're now ready to install software from the PPA!

Ok.. i understand, but tell me how will I update when I cannot connect to the net in the first place?

---

### Post by mariovs on 2009-11-02
Exactly 600WPMPO, I also have been trying for days to find a fix and I keep finding this PPA but I have no idea on how to install those files offline.

---

### Post by rax0 on 2009-11-02
For people who can't get the packages, you can download these files (for i386 only)

```


[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091031t155342.d08484c-0ubuntu2~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8%7Ea%7Egit.20091031t155342.d08484c-0ubuntu2%7Enmt1_i386.deb")


```

tell me, if you need another file(s). :KS

---

### Post by mariovs on 2009-11-02
Thats fantastic Rax0, any chance for a 64 bit version?

---

### Post by mariovs on 2009-11-02
Okay, I've downloaded the amd64 packages from those directories, can someone please let me know how to run them? should I just run them as one would any deb package? if is there any steps other then simply running them required?

Thanks

---

### Post by mariovs on 2009-11-02
Just installed those packages with dpkg -i, but after restarting it didnt see to do anything...:(

---

### Post by rax0 on 2009-11-02
Now go and create a new DSL connection, that should work.

p.s.: sorry for the late reply.

---

### Post by mariovs on 2009-11-02
I dont use DSL actually, I just connect via Auto Eth0, since I connect to my router and the password is stored on it.
I tried creating a new Auto Eth0 and it still didnt help, even with "Apply to all" checked off.

Any ideas?

---

### Post by rax0 on 2009-11-02
What do you get with "sudo ifconfig" in terminal?

---

### Post by mariovs on 2009-11-02
It says that the command doesnt exist. But going to the Network tools and selecting ethernet as opposed to loopback options I can see that I am assigned a local IP address.

---

### Post by rax0 on 2009-11-02
I have another solution, since you need eth0 only, you can use WICD [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) they say it's better anyway,

you need to remove the Network-manager and Network-manager-gnome first

```
sudo apt-get remove network-manager natwork-manager-gnome
```

pick this file first (64 I guess)

```
http://us.archive.ubuntu.com/ubuntu/pool/universe/u/urwid/
```

than 

```
http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/
```

install them, and everything should be OK, after that you can choose between keeping it or updating/reinstalling the NM.

hope that'll help.

---

### Post by 600WPMPO on 2009-11-02
```
http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb

http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091031t155342.d08484c-0ubuntu2~nmt1_i386.deb
```

Rax0, I installed these files, made a new DSL connection, but it doesn't connect. what to do now?



> **rax0 said:**
> I have another solution, since you need eth0 only, you can use WICD [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) they say it's better anyway,

you need to remove the Network-manager and Network-manager-gnome first

```
sudo apt-get remove network-manager natwork-manager-gnome
```

pick this file first (64 I guess)

```
http://us.archive.ubuntu.com/ubuntu/pool/universe/u/urwid/
```

than 

```
http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wicd/
```

install them, and everything should be OK, after that you can choose between keeping it or updating/reinstalling the NM.

hope that'll help.

I doubt that wicd will work in Karmic. There's already a bug posted: [Bug 388110] [NEW] wicd not recognizing wired connection in karmic

here [https://lists.ubuntu.com/archives/universe-bugs/2009-June/102127.html]("https://lists.ubuntu.com/archives/universe-bugs/2009-June/102127.html")

---

### Post by rax0 on 2009-11-03
I'm sorry, I made a mistake earlier, 

you need to install all these files to fix the problem
```

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-util1_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-util1_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/m/modemmanager/modemmanager_0.2.git.20091031t001131.107f950-0ubuntu2~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/m/modemmanager/modemmanager_0.2.git.20091031t001131.107f950-0ubuntu2%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091102t055646.67067af-0ubuntu2~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8%7Ea%7Egit.20091102t055646.67067af-0ubuntu2%7Enmt1_i386.deb")


```those are for i386 only!
it should work this time.

and don't forget to restart the computer too.

---

### Post by 600WPMPO on 2009-11-03
> **rax0 said:**
> I'm sorry, I made a mistake earlier, 

you need to install all these files to fix the problem
```

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-glib2_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-util1_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/libnm-util1_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/m/modemmanager/modemmanager_0.2.git.20091031t001131.107f950-0ubuntu2~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/m/modemmanager/modemmanager_0.2.git.20091031t001131.107f950-0ubuntu2%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8~a~git.20091030t185830.82011df-0ubuntu1~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager/network-manager_0.8%7Ea%7Egit.20091030t185830.82011df-0ubuntu1%7Enmt1_i386.deb")

[http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8~a~git.20091102t055646.67067af-0ubuntu2~nmt1_i386.deb]("http://ppa.launchpad.net/network-manager/trunk/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8%7Ea%7Egit.20091102t055646.67067af-0ubuntu2%7Enmt1_i386.deb")


```those are for i386 only!
it should work this time.

and don't forget to restart the computer too.

I installed all the files but its not working.

I think there is a problem. I did "sudo pppoeconf" earlier, which did not connect the net. Instead, NetworkManager applet in panel says "wired networks, device not managed". 

Maybe these new files are not working because of this ?

Please help

---

### Post by rax0 on 2009-11-03
That's true, I said before:

> I usually open /etc/NetworkManager/nm-system-settings.conf as root and edit "managed=flase" to "true" then save and restart, that should do it.

I do this after every fresh install, it should work with you too.

---

### Post by 600WPMPO on 2009-11-03
Thanks a lot, rax0 !!!! finally I'm able to connect DSL !! :grin:

Is there a way to auto-connect it at startup..?

---

### Post by MysteriousHoatzin on 2009-11-03
Oh, wise gurus of these here Ubuntu forums:

I tried to follow rax0's last few posts (installing all of those packets and all), but for some reason network manager refuses to even see my wireless network or any of the neighbor ones.

I run a little Thinkpad T30. I had no issues with Intrepid, then Jaunty would refuse to connect every other time I started the computer, which was annoying but remediable with a simple [FONT="Courier New"]$ sudo /etc/init.d/networking restart[/FONT]. In Karmic, however, [FONT="Courier New"]$ sudo /etc/init.d/networking restart[/FONT] doesn't seem to do anything. Any ideas? Thanks a ton!

---

### Post by rax0 on 2009-11-04
> **600WPMPO said:**
> Thanks a lot, rax0 !!!! finally I'm able to connect DSL !! :grin:

Is there a way to auto-connect it at startup..?

No problem, go modify your DSL connection, and check "auto connect on startup" (I'm not sure if it works though)

> **MysteriousHoatzin said:**
> Oh, wise gurus of these here Ubuntu forums:

I tried to follow rax0's last few posts (installing all of those packets and all), but for some reason network manager refuses to even see my wireless network or any of the neighbor ones.

I run a little Thinkpad T30. I had no issues with Intrepid, then Jaunty would refuse to connect every other time I started the computer, which was annoying but remediable with a simple [FONT=Courier New]$ sudo /etc/init.d/networking restart[/FONT]. In Karmic, however, [FONT=Courier New]$ sudo /etc/init.d/networking restart[/FONT] doesn't seem to do anything. Any ideas? Thanks a ton!

I'm sorry, I don't have any experience with wireless connections.

---

### Post by 600WPMPO on 2009-11-04
Well, rax0 ... I'm back to square one.

When I posted last, I just installed your files and restarted the system. It connected to the net. I opened firefox, posted here on ubuntuforums and happily shut down. 

Then, after 4-5 hours later, I turn on my computer and try to connect to the net, but again the "insufficient privileges" error messages comes. Then DSL authentication would ask again and again for my password. I'm again offline.

How can it happen when I had not done anything...? :mad:

Please help..

---

### Post by rax0 on 2009-11-04
umm.. I think you need to go to the main menu> Accessories> Passwords and Encryption Keys


Then, under the Passwords section, you'll find a folder named "Passwords: default", open it and double click on "Network secret for ***/pppoe/password"

In the new windows, you'll find the word "Password" after an arrow, click on it and change the password, and click "always allow" (if it is showed)

then, try to connect to DSL through the nm-applet, and enter the same password.

---

### Post by 600WPMPO on 2009-11-04
rax0, I again turned on the system after about 2 hours of last post. Now it is not asking for password/authentication, but simply not allowing to connect. 

As I click on my DSL connection via NM, a small rotating circle does its thing in the upper panel and the notification says "Disconnected". Then it automatically connects to the native eth0. Just like it did on a fresh install. 

I even tried installing the deb files again, but no result.

Please help..

---

### Post by rax0 on 2009-11-04
Try what I said, it should work

---

### Post by 600WPMPO on 2009-11-04
> **rax0 said:**
> umm.. I think you need to go to the main menu> Accessories> Passwords and Encryption Keys


Then, under the Passwords section, you'll find a folder named "Passwords: default", open it and double click on "Network secret for ***/pppoe/password"

In the new windows, you'll find the word "Password" after an arrow, click on it and change the password, and click "always allow" (if it is showed)

then, try to connect to DSL through the nm-applet, and enter the same password.

rax0, I am unable to open the "Paswords:default" folder. If I double-click it, the properties box comes up. If I right-click it, a menu appears in which there is no option to open it.

What to do ?

Please help..

---

### Post by rax0 on 2009-11-04
How about clicking on the left arrow?

---

### Post by 600WPMPO on 2009-11-04
> **rax0 said:**
> How about clicking on the left arrow?

Left arrow ? I'm sorry, I can't see any..where do I find it

All I can try is:

Applications -> Accessories -> Passwords and Encryption Keys

Passwords tab

Right-click "Passwords: login"

Select "Change Password"



p.s. I knew I was dumb, but now I fear I'm getting blind too !! :lolflag:

---

### Post by rax0 on 2009-11-04
Try to change from that location, restart, then connect and enter the same password when prompted, other than that, I don't think I know that much,

P.S. LOL

---

### Post by 600WPMPO on 2009-11-04
I tried the password bit but didn't seem to change anything.

However, **I'm able to connect to the net now...!!!!** here's how (courtesy P4man)

I edited the settings for the auto ethernet and enabled the "available to everyone" checkbox. I then set MCU to 1500.

---

### Post by Nuevo2 on 2009-11-05
This is one of the threads I have been following since installing Karmic and finding I couldn't connect to the internet. I just wanted to pass on that the following Launchpad bug report contained both a diagnosis of the problem and successful work arounds:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757)

Hope it helps some of you too. Thanks to those who have been helping us.

---

### Post by 600WPMPO on 2009-11-05
You can follow a similar thread with successful workarounds here:

[http://ohioloco.ubuntuforums.org/showthread.php?t=1304843](http://ohioloco.ubuntuforums.org/showthread.php?t=1304843)

---

### Post by SawyerLX on 2009-11-06
i agree with that attitude, i too can't believe this big ol Bug in the Network Manager is real buggy-had to use terminal  mode to run pppoeconf.  This is a major bug and is very disapointing; as i referqred an associate to use it via my copy of the cd iso for him to take home and try :(

---

### Post by aventura_alex on 2009-11-06
Does anyone know if the development team is addressing the problem and if they're going to make it available from the main page?
Is there an official thread on the subject?
:popcorn:

---

### Post by _khAttAm_ on 2009-11-07
This ppa worked for my 64-bit install.
[https://launchpad.net/~network-manager/+archive/trunk](https://launchpad.net/~network-manager/+archive/trunk)

---

### Post by khaktus on 2009-11-18
The same issue for me on DSL. I was working on 9.04 for a few months without problem, now absolutely no internet connection on 9.10 - neither in Mozilla, nor in Synaptic. However, as I run dual boot with XP, on Windows, network connection is fine. Lucky me...

There are so many bugs launched and so many forums with dozens of workarounds for experts, creating new bugs... Can somebody write a step by step solution for newbie?

[COLOR=Red]0. The network is **not** working. (Don't tell me to download something).
1. What to do/rewrite/edit/launch to make a temporary workaround - network somehow working (mozilla, synaptic, or whatever)
2. What to do to download/get somehow some official fix (not creating new bugs) ... if it already exists.[/COLOR]

I'm not satisfied with answers like "upgrade NM with ppa" or "try pppoeconf"... it doesn't tell me much.
[B]
Please, someone, make a clear summary. [/B]

Do not send me another links to read endless forums... I have spent hours reading them... I'm used to the plurality of responses and solutions while working with Ubuntu, but having such a major problem, I'm loosing my patience. It is a major issue and newbies are not able to spend days reading forums, that offer so many workarounds, that need to be topped by other workarounds... I need to see what to do right now and not to read what hundreds of people tried... Where is Ubuntu's official solution? They should have a step by step fix on the first page of their web.

---

### Post by MysteriousHoatzin on 2009-11-18
> **khaktus said:**
> The same issue for me on DSL. I was working on 9.04 for a few months without problem, now absolutely no internet connection on 9.10 - neither in Mozilla, nor in Synaptic. However, as I run dual boot with XP, on Windows, network connection is fine. Lucky me...

There are so many bugs launched and so many forums with dozens of workarounds for experts, creating new bugs... Can somebody write a step by step solution for newbie?

[COLOR=Red]0. The network is **not** working. (Don't tell me to download something).
1. What to do/rewrite/edit/launch to make a temporary workaround - network somehow working (mozilla, synaptic, or whatever)
2. What to do to download/get somehow some official fix (not creating new bugs) ... if it already exists.[/COLOR]

I'm not satisfied with answers like "upgrade NM with ppa" or "try pppoeconf"... it doesn't tell me much.
[B]
Please, someone, make a clear summary. [/B]

Do not send me another links to read endless forums... I have spent hours reading them... I'm used to the plurality of responses and solutions while working with Ubuntu, but having such a major problem, I'm loosing my patience. It is a major issue and newbies are not able to spend days reading forums, that offer so many workarounds, that need to be topped by other workarounds... I need to see what to do right now and not to read what hundreds of people tried... Where is Ubuntu's official solution? They should have a step by step fix on the first page of their web.

This is something that is probably a bigger issue to getting Ubuntu recognized as a serious contender than flickerless login or super-fancy unstylable notification popups.
:/

---

### Post by imsdunn on 2009-11-30
> **rax0 said:**
> That's true, I said before:

I usually open /etc/NetworkManager/nm-system-settings.conf as root and edit "managed=flase" to "true" then save and restart, that should do it.

I do this after every fresh install, it should work with you too.



Thanks rax0, this worked for me!

---

### Post by AlexanderDGreat on 2010-03-16
Thanks rax worked for me too, I installed Ubuntu from a minimal cd / server, then network-manager-gnome, but I can't manage it although I have Internet, so I did what you said. Now it's okay!

---

