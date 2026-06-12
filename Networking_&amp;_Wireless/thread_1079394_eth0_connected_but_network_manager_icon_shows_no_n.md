---
title: "eth0 connected but network manager icon shows no network"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by nightshade209 on 2009-02-24
i got my ethernet connection up and running, and it works perfectly well, but i have a minor annoyance: the network manager applet in the notification area says "Wired network : device is unmanaged". Does that mean it cannot recognize my eth0 connection??

---

### Post by Iowan on 2009-02-24
What it *probably* means (obviously guessing a bit - I don't have Intrepid), is that Network Manager is not managing the interface 
...but you say it's working anyway?

---

### Post by nightshade209 on 2009-02-25
Yes, it is working properly. Cud u explain wat u mean by Network Manager is not managing the interface? When setting up my connection, i used the sudo pppoeconf method, so tht means i configured it using Network Manager right?

---

### Post by superprash2003 on 2009-02-25
did you manually setup static ip or edit the /etc/network/interfaces file?

---

### Post by nightshade209 on 2009-02-26
neither... as i said, i used ```
sudo pppoeconf
``` the very first time i ran ubuntu, after that i havent touched anything even remotely connected to netwrok settings... during the initial setup, i used all the default options that ubuntu provides...

---

### Post by James4 on 2009-02-27
I have the same problem.
at first place my network manager was working well, then I installed kde and cuz I couldn't connect to my ethernet device in kde I installed pptp and now my gnome network manager says 'Device Unmanaged'.
I wonder if there is anything to make it manage my device again so I don't have to use 'pon dsl-provider' command in terminal.

---

### Post by YWELLC on 2009-02-27
I upgraded to Intrepid last night and had the exact same problem.  I Googled it and found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417")

I am not sure exactly which combination of steps I used from that post to get it working, but I remember when I set "Managed = true" in the /etc/NetworkManager/nm-system-settings.conf it broke my (then working) connection, though ifupdown (eth0) did appear in the nm-applet as "Managed" and the red X went away.  I then added a new wired connection and checked off both "Automatically connect" and "System Setting" and re-booted, which seemed to solve the problem, as my ethernet connection resumed and the nm-applet said it was managing the device.

For what it's worth, I can check the exact (working) settings and report back when I get home if you are still having a problem.

---

### Post by James4 on 2009-02-27
wow.
thanks pal. you just saved me.
I just edited the file /etc/NetworkManager/nm-system-settings.confand turned managed (ifupdown) into 'true' and it got working again.
thanks again.

---

### Post by YWELLC on 2009-02-27
No problem - I have received SO much help from these forums, it's nice to give a little something back if/when I can.

Also, you should change the title of this post to include [SOLVED] now that you have found your solution.

Cheers!

---

### Post by nightshade209 on 2009-02-28
i checked out the link for the bug u gave, but my /etc/network/interfaces looks very different from what is given there, except for the first two lines; so hw do i fix it?

---

### Post by YWELLC on 2009-02-28
Post the output of:

```
cat /etc/network/interfaces
```

and

```
cat /etc/NetworkManager/nm-system-settings.conf

```

Sorry about the comment to changing the post to solved in my last post, I didn't realize it wasn't the OP who got it fixed.

---

### Post by nightshade209 on 2009-03-01
Output of ```
cat /etc/network/interfaces
```is
```
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```

and output of ```
cat /etc/NetworkManager/nm-system-settings.conf
```is
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

---

### Post by YWELLC on 2009-03-01
Try this:

```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Change

Managed=false

to

Manged=true

Then open up the NM applet via System>Preferences>Network Configuration

and if there is anything listed there other than "ipupdown", (for me this is Wired Connection 1) click edit, and check off "Connect Automatically" and "System Setting" then reboot the system.

Hopefully that will resolve this minor annoyance.

---

### Post by nightshade209 on 2009-03-04
> **YWELLC said:**
> Try this:

```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Change

Managed=false

to

Manged=true

Then open up the NM applet via System>Preferences>Network Configuration

and if there is anything listed there other than "ipupdown", (for me this is Wired Connection 1) click edit, and check off "Connect Automatically" and "System Setting" then reboot the system.

Hopefully that will resolve this minor annoyance.

I am afraid this didnt work for me. My network connection stopped working when i changed Managed=false to Managed=true; and there are absolutely no connections listed in the NM applet, not even the ipupdown u mentioned.

---

### Post by YWELLC on 2009-03-05
Same thing happened to me, after I made NM manage my connection I had to manually add the connection info through the applet.  Try changing it back to "managed=true" and then goto System>Preferences>Network Configuration and then go to the "DSL" tab and click on "Add New", then insert the appropriate configuration for your DSL connect, click on "system setting" and "connect automatically."  

I do not know what exactly you will need to enter in there to make it work as I have never had to configure a PPPoe connection, but I'd bet a good place to look for the settings would be in your pppoeconf configuration file.

You might want to look where this post says to:
[https://www.linuxquestions.org/questions/linux-networking-3/does-pppoeconf-have-a-config-file-223624/]("https://www.linuxquestions.org/questions/linux-networking-3/does-pppoeconf-have-a-config-file-223624/")

---

### Post by nightshade209 on 2009-03-09
after doing what you said, my network applet shows 2 connections : ifupdown and the new connection (DSL connection 1)... However, when my pc boots up, the ifupdown is selected by default and to get the connection working, i have to manually select DSL connection 1... Moreover, i can't delete the ifupdown connection as it says i do not have sufficient permissions... Is there any way to make the DSL connection the default one?

---

### Post by gm.matias on 2009-12-25
I had the same problem and wrapped it up in this article: [http://www.gmmatias.com/device-not-managed-status-in-wired-networks-2009-12-07](http://www.gmmatias.com/device-not-managed-status-in-wired-networks-2009-12-07)

---

### Post by markrocha on 2010-03-25
Hi there,
 
I'm new here, and I'm not sure if this is the right place to post this problem - but it was the closest related topic i could find.
 
I use Ubnuntu 9.10, and i wanted to change my bluetooth manager to BlueMan (instead of the default gnomeBluetooth) and in the process, ended up uninstalling my gnome-network-manager. The reason why it happened, is because it manages the all network connections - including wireless, wired, and blutooth network devices. 
 
Now the problem is, how do i get it back? I obvioulsy can't download it cos i can't connect to the net ... what do i do? I have the Ubuntu 9.10 CD ... will that help?

---

### Post by PAgore on 2010-05-18
@YWELLC:

Thank You!
You solved my problem!!!  :)

---

