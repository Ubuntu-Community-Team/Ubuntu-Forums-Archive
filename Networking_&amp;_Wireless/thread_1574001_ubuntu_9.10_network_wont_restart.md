---
title: "ubuntu 9.10 network wont restart"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by dhotiwalla on 2010-09-13
Hi All,

I'm running ubuntu 9.10 KK on two systems and am very happy with them so far. The only issue I have is with networking.

Both systems have been configured with static IP addresses. If I unplug the network cable, I get the msg "eth 0: link down". When I plug in the network cable, I get the msg "eth 0: link up". However after I plug in the cable, the network does not come up automatically.

running sudo service networking start displays "networking stop/waiting"
running sudo start networking displays the same message

rebooting the system brings up the networking, but this is not a solution as both systems are running as servers and cannot be restarted every time the network/ISP goes down.

How does one resolve this problem?

thanks for you help
Dhoti Walla

---

### Post by MaindotC on 2010-09-13
There is a here'a a [Basic Troubleshooting Guide](http://ubuntuforums.org/showthread.php?t=25557) for determining problems like this.  It sounds to me like NetworkManager is configured improperly.  Can you post a screenshot of your network settings in NetworkManager?

---

### Post by dhotiwalla on 2010-09-13
thanks for your response strLan. I have attached the screen shots

thanks
DhotiWalla

---

### Post by MaindotC on 2010-09-13
> **dhotiwalla said:**
> running sudo service networking start displays "networking stop/waiting"
running sudo start networking displays the same message


NetworkManager controls your network connections so these commands won't affect network operation and /etc/network/interfaces will be ignored.  I don't have a solution for you, but I can suggest a work-around.

Since the machines have static addresses there's really no need for you to have NetworkManager and [it has been a problem recently](http://is.gd/f95LI) and I'm not sure what happened that has caused so many issues.  You could just uninstall the package network-manager from Synaptic and then configure your /etc/init.d/network/interfaces file to reflect the same information you have in NetworkManager: ip address, subnet mask, gateway, and your dns servers in /etc/resolv.conf.  If you do this, you will not see an icon pop-up when the network connection goes down or comes back up.

Another work-around is to install a different application called "wicd".  It basically performs the same functionality as NetworkManager and has attracted users who have had problems with NetworkManager.

Again, this is not a solution, but a work-around.  Please let me know if you want to do this or if you need help configuring the files.

---

### Post by dhotiwalla on 2010-09-13
Hello strLan,

I followed your workaround and installed wicd using synaptic package manager (which automagically uninstalled gnome network manager).

I still face the exact same problem, with the exception that I can manually restart the network using wicd.

Maybe the solution is to manually configure the network as you suggested. Can you tell me how to do so?

thanks
Dhoti

---

### Post by MaindotC on 2010-09-13
This is the [Ubuntu Network Configuration Guide](https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html) via command line and the "interfaces" file for 9.04.  I believe it still applies.

The following configurations should work for the machine you mentioned.  Be sure to edit them with root permissions.

/etc/network/interfaces:```

iface eth0 inet static
	address 192.168.1.123
	netmask 255.255.255.0
	gateway 192.168.1.1
```

/etc/resolv.conf:```

search linksys
nameserver 192.168.1.1
```

Please be sure to consult the documentation to verify any changes you feel are necessary.  You may have to uninstall Wicd to relinquish control of your network interface.  Let me know how it goes!

---

### Post by dhotiwalla on 2010-09-14
Hi strAlan,

I uninstalled wicd and changed my /etc/network/interfaces file as per your suggestion. My network would not come up even after a reboot. Adding auto eth0 to the file made it work after a reboot but unplugging the network cable and plugging it back it would bring down the network and reboot was always required to bring it up again.

But after a few reboots my network stopped working completely, even though I rebooted at least 10 times. I had to reinstall wicd to get my network up again

So I'm back to square 1

thanks
Dhotiwalla

---

### Post by MaindotC on 2010-09-14
Please understand that rebooting is not how you restart your network connection.  I understand you didn't know and that's fine but I just don't want you to get the wrong impression of Ubuntu (or Linux in general).  I'm sorry for not mentioning this before but the command to restart networking is:```
sudo /etc/init.d/networking restart
``` or, if it complains and wants you to use the service command, then type:```
sudo service networking restart[/url].  For wicd, if you have it running and it does not resume your network connection after an uplug, the command is similar:[code]sudo /etc/init.d/wicd restart
```

Configure your static ip address using wicd and try unplugging the cable again.  Check the settings in Wicd that enforce an automatic reconnection if unplugged.  I've been trying it on a virtual machine with static settings and it works fine.

---

### Post by dhotiwalla on 2010-09-14
Hi strAlan,

my fault actually. I was using sudo service networking stop/start and when that did not work, I rebooted the system. Should have mentioned it.

sudo service networking stop/start has no effect on my network, which is quite strange.

sudo service networking stop always displays unknown instance and
sudo service networking start always displays networking stop/waiting

and if I use sudo /etc/init.d/networking start/stop, it politely asks me use the service cmd.

sometimes running sudo /etc/init.d/wicd restart does bring up my network, but other times it does not. I have attahced my wicd configuration.

BTW, thanks a zillon for your perseverance with this issue of mine. I greatly appreciate it!

Dhotiwalla

---

### Post by MaindotC on 2010-09-15
I'm glad to help - but I wish I could do more.  Enable "debug mode", restart wicd, do whatever you have to do to make sure your connection is working, then look at the log files.  You can view them in System -> Administration -> Log File Viewer and then click "open" and choose /var/log/wicd/wicd.log.

When you have that open, unplug the cable and view the log, then plug it back in after about 10 seconds, and continue to monitor the log.  Post the output here in [code] tags.

One thing I've been wondering - are you planning on the cable being unplugged frequently?

---

