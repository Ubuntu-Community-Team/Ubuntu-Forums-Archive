---
title: "Can't Install StrongVPN PPTP on 10.04"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by jjtstan on 2011-08-06
I'm having problems installing strongvpn pptp on ubuntu 10.04.  I've followed the instructions on 

[http://vpnblog.info/ubuntu-pptp-strongvpn.html](http://vpnblog.info/ubuntu-pptp-strongvpn.html) and

Unfortunately I have no network manager icon.  I've used Synaptic Package Manager to install all network manager related packages, and restarted the machine.  The system monitor shows "nm-applet Sleeping."  So perhaps if I could wake up the nm-applet (assuming that is the network manager applet) I could solve the problem that way.

I was also advised to try this method:

[http://mystrongvpn.com/forum/viewtopic.php?id=964](http://mystrongvpn.com/forum/viewtopic.php?id=964)

However, after creating this file, and running "sudo pon <filename>" where <filename> was the name of the file I created, I still had no vpn access.

Any other suggestions on how to get this set up?

In case it's not already obvious, I'm quite the rookie, so please take that into account with the advice.  Thanks in advance.

---

### Post by jjtstan on 2011-08-06
Some more failed attempts to fix this problem:

I basically followed the instructions in this post, and got the same error messages:

[http://www.linuxforums.org/forum/ubuntu-linux/165651-solved-ubuntu-10-04-network-manager-applet-icon.html](http://www.linuxforums.org/forum/ubuntu-linux/165651-solved-ubuntu-10-04-network-manager-applet-icon.html)


> john@dell-desktop:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:7491): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

john@dell-desktop:~$ killall nm-applet
john@dell-desktop:~$ nm-applet &
[1] 7505
john@dell-desktop:~$ ** (nm-applet:7505): DEBUG: old state indicates that this was not a disconnect 0

john@dell-desktop:~$ ^C


Then I tried restarting network manager, and got this:

> john@dell-desktop:/etc/init.d$ sudo restart network-manager
** Message: NM disappeared
network-manager start/running, process 8278
john@dell-desktop:/etc/init.d$ ** (nm-applet:7505): DEBUG: old state indicates that this was not a disconnect 0
** Message: NM appeared
** (nm-applet:7505): DEBUG: foo_client_state_changed_cb

** (nm-applet:7505): WARNING **: nma_menu_vpn_item_clicked: no active connection or device.


The network manager icon has now appeared.  I can click on the icon, get a VPN option, and then click on StrongVPN.  However, nothing happens when I select Strong VPN.  

I tried running grep ppp /var/log/messages > pppoutput so that I could provide IT service with the file.  I got several permission denied errors.  So I shut down the terminal, restarted it, and successfully ran grep ppp /var/log/messages > pppoutput.  

However, the network manager icon has now disappeared again.  And when I retry the restart, I get this:

> john@dell-desktop:~$ sudo restart network-manager
[sudo] password for john: 
network-manager start/running, process 8827
john@dell-desktop:~$ 


Where to from here?

---

### Post by jjtstan on 2011-08-06
Something else I've tried without success:


> john@dell-desktop:~$ service network-manager stop
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.84" (uid=1000 pid=12710 comm="stop) interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
john@dell-desktop:~$ service network-manager start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.85" (uid=1000 pid=12714 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
john@dell-desktop:~$ 


---

