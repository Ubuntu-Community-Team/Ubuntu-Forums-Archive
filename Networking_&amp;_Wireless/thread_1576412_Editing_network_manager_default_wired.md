---
title: "Editing network manager default wired"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by hornetster on 2010-09-17
Have searched for this and am sure the answer is out there somewhere, but I can't find it....
My wired network is configured as AUTO, and is DHCP, I can add a new static config, but can't get it to load, as the original AUTO always loads on a reboot. I need to be able to run sudo Network manager so I can reconfigure the default... How do you do that??

Thanks, John.

---

### Post by dineshs on 2010-09-17
While setting static IP you should hit enter after giving gateway.otherwise the changes will not be saved
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

---

### Post by hornetster on 2010-09-19
On a reboot, the original configuration (AUTO) always loads, but if I try to edit this configuration, I can't as the option to edit is greyed out, as by default I don't have permissions to edit, without SUDO (I assume). How do I SUDO in to edit this setup??
(I'm sure it's been done before...)
Thanks.

---

### Post by grahammechanical on 2010-09-19
If you do not have permissions to edit, as you say, then you are  not logged on as Administrator. Go to Users and Groups. What are you listed as? Administrator? Custom? Desktop? You can change your account type Administrator. Under Advanced Settings you can give yourself lots of permissions, including Administer the System. You will need your log-on password to Authenticate yourself as the person who installed the OS or sudo in other words.

This might give you access to edit Auto Eth0 from Connect Automatically. It should then become Eth0.  All with a bit of luck.

regards

---

### Post by hornetster on 2010-09-19
Thanks for the reply. I usually use Suse and appreciate that you need admin access to edit stuff like this, but thought that in ubuntu there actually is "no administrator" (or root) and you need to sudo, or theoretically it should ask you if root access is required (there used to be a button to upgrade your credentials in network manager....?) Am trying to use the "Ubuntu method"...
Thanks John

---

### Post by hornetster on 2010-09-20
I can't believe this is so difficult! A basic requirement of a PC on a network is that it can talk to other PCs. Surely Ubuntu isn't that "dumbed down" that everything HAS to be set automatically? 
A simple, and fairly common request, to know how to setup a static IP, and the Network Manager that Ubuntu relies on, can't do it?? And there are many other similar posts in this and other forums. 
OK, I'll go back to basics and set it up manually, but why should I have to? If I was talking one of many other distros that aren't quite "up there" I would expect to have to do that....
Thanks, John.

---

### Post by Iowan on 2010-09-20
> **hornetster said:**
> On a reboot, the original configuration (AUTO) always loads, but if I try to edit this configuration, I can't as the option to edit is greyed out.
I'm probably missing something obvious... if you click on the connection (even Auto eth0) you *should* be able to edit it from Network Manager. Then you *should* be able to uncheck the "Connect automatically" option...

---

### Post by hornetster on 2010-09-20
No, as I said, when I log in if I click on AUTO in Network Manager, the option to edit this is "greyed out" so I cannot do anything with it, including disable connect automatically....
Have now configured manually for my static IP, just disappointed that Ubuntu wouldn't/couldn't let me do this through the relevant utility....

Thanks, John.

---

### Post by Iowan on 2010-09-20
> **hornetster said:**
>  just disappointed that Ubuntu wouldn't/couldn't let me do this through the relevant utility....:confused: It should! It does on my machine... not that it helps you. You might check */etc/network/interfaces* to verify that only the two lines for "lo"  are there.

---

### Post by hornetster on 2010-09-20
> **Iowan said:**
> :confused: It should! It does on my machine... not that it helps you. You might check */etc/network/interfaces* to verify that only the two lines for "lo"  are there.

Yep...:confused:

---

### Post by bobbobly on 2011-09-19
I know this is an old thread but I have been struggling with this as well and I have a few machines that do this and a few that work properly and allow me to edit the interface. I found a way to get this working and wanted to share the solution here.

If you can't edit the default auto connections the edit the file /etc/NetworkManager/nm-system-settings.conf or /etc/NetworkManager/NetworkManager.conf (depends on the version you are using) and it should look something like this:

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


```

Add a line to tell Network manager not to auto configure interfaces (replace 00:00:00:00:00:00 with your mac address, multiples separated by commas)

```

[main]
plugins=ifupdown,keyfile

no-auto-default=00:00:00:00:00:00,00:00:00:00:00:00

[ifupdown]
managed=false


```

now restart network manager
```
sudo service network-manager restart
```

Then open the edit interface and add the wired connection manually and make sure you fill in the mac address field.

*** Update ***

I just found out what is going on when I read this page from Network Manager
[http://live.gnome.org/NetworkManagerConfiguration]("http://live.gnome.org/NetworkManagerConfiguration")

At the very bottom of the page it talks about Administration and Privilige and indicates that it uses PolicyKit for user rights and sure enough on the machines it didn't work on they didn't have policykit installed so a simply running the command below and rebooting fixed the issue without any other configuration.
```

sudo apt-get install policykit-1-gnome

```

---

### Post by hornetster on 2011-09-19
Thanks for that Bobbobly(?) :)
Sure that will help someone in the future...
John.

---

