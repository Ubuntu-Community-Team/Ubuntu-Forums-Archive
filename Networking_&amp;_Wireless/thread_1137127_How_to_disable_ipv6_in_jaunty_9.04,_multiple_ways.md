---
title: "How to disable ipv6 in jaunty 9.04, multiple ways"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by Claus7 on 2009-04-25
Hello,

I write this thread as a result of my exploitation of the subject: remove this ipv6 thing in jaunty as it puts impediments in the internet access of many people (including myself).

Jaunty Jackalope 9.04, even though a descent distro, is so advanced that it has by default built in its kernel the ipv6 protocol, that handles more or less the communication one has with the internet. That means that "easy" ways of disabling it is not an option, except if someone is very lucky. You will see that in many people some solutions didn't work, so it depends on what you want to do and what works for you so as to pick the right one. Keep reading:

[LIST=1]
[*]if internet is working fine for you then you do not have to bother about it. Your isp, your modem or rooter and the web sites you are visiting are "good" enough with ipv6 so no bother for you.


[*]firefox is working nice, opera almost not at all, and if you leave firefox open for sometime you see that even though google works, other that that you cannot enter any web page. In order to make firefox work again you have to close your pc, close your rooter for about 5' and open all of these back again.

The easiest solution would be to abandon opera and disable ipv6 protocol only for firefox. Unfortunately opera doesn't allow someone to do so, even in its 10 alpha release, till the rime of writing.

So here:
[http://ubuntuforums.org/showpost.php?p=1656712&postcount=2](http://ubuntuforums.org/showpost.php?p=1656712&postcount=2)
you can disable ipv6 for firefox only.


[*]Nothing works as it should. Internet is bad and you want to disable ipv6 in your entire system. Now, there are a couple of solutions about that. In my case apart from the recompilation of the kernel none worked, even though I had the 2.6.28-11-generic kernel (in order to find out yours, open a terminal and type uname -r, and presto! you will see the version of your kernel).


[LIST]
[*]Easy method enough, yet you should pay attention, when you boot if you have any errors like: " unknown option 'ipv6.disabe' ignoring ". If you do, then that's bad. Either that method does not work for you or you have typed the string in the wrong line.
[http://ubuntuforums.org/showpost.php?p=7060074&postcount=27](http://ubuntuforums.org/showpost.php?p=7060074&postcount=27)


[*]Very easy method:
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=7086902&postcount=39](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=7086902&postcount=39)
Yet, there you might face access problems. In other words you might not be allowed to change the value of the file in question or this file might not exist. With vi editor I was unable to change this value. Just reboot and see if ipv6 is disabled or not. After a reboot it didn't work for me so one solution that I think is putting this in .bashrc and see if it will work.


[*]Hard one! Recompilation of kernel:
[http://ubuntuforums.org/showpost.php?p=7033690&postcount=9](http://ubuntuforums.org/showpost.php?p=7033690&postcount=9)
Be patient and good luck!
[/LIST]
[/LIST]

Disabling ipv6 from firefox only I think that it is the easiest method and the fastest one. Up to now it is working for me.

The method:
[http://ubuntuforums.org/showpost.php?p=7011211&postcount=4](http://ubuntuforums.org/showpost.php?p=7011211&postcount=4)
does **not** work in jaunty.

Regards!

---

### Post by Claus7 on 2009-04-25
Hello,

if you have tried the above and things are still not working then the problem might not be ipv6, yet your dns service provider. After all the above (without tampering with the kernel) I had still problems with my internet connection. Firefox sometimes was not entering web pages and opera could not find any address at all or it took ages in order to open one. So this:
[http://ubuntuforums.org/showpost.php?p=2810501&postcount=17](http://ubuntuforums.org/showpost.php?p=2810501&postcount=17)

cleared things once again! I'm writing now from opera, so I think that it is a good sign that things are working as they should. I haven't changed anything as far as ipv6 is concerned.

My kindest regards!

---

### Post by BlackDex on 2009-04-27
I Have the same problem.
I can't get it disabled, and it is causing a lot of RX errors etc...

I realy need it to be disabled.

---

### Post by Claus7 on 2009-04-27
Hello,

this solve entirely the dns issue, which is an updated link and you can find in the thread I propose above.
[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

I can see that ipv6 not disabled in opera, causes some issues in some sites, yet up to now minor. 

BlackDex I do not know how you face such errors. Other than my first post in this thread, I do not know how ipv6 can be disabled.

Regards!

---

### Post by dmglouis on 2009-05-12
> **Claus7 said:**
> 
Very easy method:
[http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=7086902&postcount=39](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=7086902&postcount=39)
Yet, there you might face access problems. In other words you might not be allowed to change the value of the file in question or this file might not exist. With vi editor I was unable to change this value. Just reboot and see if ipv6 is disabled or not. After a reboot it didn't work for me so one solution that **I think is putting this in .bashrc and see if it will work**.


Umm, sorry if this is an obvious question. I opened up the .bashrc file in my home directory and its filled with a bunch of stuff and I'm unsure of where to insert the ```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
``` line. Also, since sudo su is necessary when doing it manually, will anything else need to be added (like sudo in front)?

Thanks

---

### Post by Brandon Williams on 2009-05-13
> **dmglouis said:**
> Umm, sorry if this is an obvious question. I opened up the .bashrc file in my home directory and its filled with a bunch of stuff and I'm unsure of where to insert the ```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
``` line. Also, since sudo su is necessary when doing it manually, will anything else need to be added (like sudo in front)?

Thanks

If you want that setting when you boot, then add the following line to /etc/sysctl.conf
```
net.ipv6.conf.all.disable_ipv6=1
```
You will have to use sudo to open the file.

---

### Post by loomsen on 2009-05-18
> **dmglouis said:**
> Umm, sorry if this is an obvious question. I opened up the .bashrc file in my home directory and its filled with a bunch of stuff and I'm unsure of where to insert the ```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
``` line. Also, since sudo su is necessary when doing it manually, will anything else need to be added (like sudo in front)?

Thanks

> You will have to use sudo to open the file.

I'd seriously suggest reading the basics of a linux system. YOU CAN'T open devicefiles, nor will you be able to remove modules which are cooked into the kernel. 

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

You can stop echoing things to your kernel, you won't be able to mod away whats built in.

```
grep -i ipv6 /boot/config-`uname -r`
```

Btw, this has been discussed in the master kernel thread quite a while...

IPv6 is quite bugging, but the handling for those who don't have it has improved.

```

dmesg | grep -B1 -i ipv6
```

Took 7-10 seconds for each network card upon boot for me.... I can't post output anymore cause I recompiled cpl of days ago. But I posted some sample output in the master kernel thread.

---

### Post by Brandon Williams on 2009-05-18
> **loomsen said:**
> I'd seriously suggest reading the basics of a linux system. YOU CAN'T open devicefiles, nor will you be able to remove modules which are cooked into the kernel.

I think you may need to read posts more carefully before commenting. My suggestion was to use sysctl (via sysctl.conf) to change the setting that dmglouis was trying to set. I did not suggest opening the file in the proc filesystem that represents this setting, although, yes, you can open this file as a way to change the setting in the running kernel. Whether or not the setting has any impact on the system, I don't know. I don't have any problems with IPv6, so I don't have a way to test it. Previous posters have suggested that changing this kernel parameter may be a solution, and my suggestion allows the kernel setting to be changed on boot.

Also, no one suggested opening a device file, although those can also be opened. You're right that you can't remove a module that is cooked into the kernel, but no one has suggested attempting to do that. All of the suggestions are potential work-arounds. If you have specific experience that shows that one or more of the suggested work-arounds do not in fact help, please comment on that.

---

### Post by binbash on 2009-05-19
Very easy way to disable ipv6 : [http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

---

