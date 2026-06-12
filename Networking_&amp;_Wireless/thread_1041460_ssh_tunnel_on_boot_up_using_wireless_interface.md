---
title: "ssh tunnel on boot up using wireless interface"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by jay2 on 2009-01-16
I have an interface that looks like this:

auto wlan0
iface wlan0 inet static
        address 192.168.1.222
        netmask 255.255.255.0
        post-up perl /root/apconnect.pl



apconnect.pl is a script that sets up a wireless interface, calls up DHCLIENT, and finally executes an ssh tunneling command.

my problem is the tunnel does not start correctly. When I looked at ps aex |grep ssh, i can see the reason why is because ssh keeps using the IF_ADDRESS 192.168.1.222 instead of the ip obtained through DHCLIENT inside the script apconnect. Any idea how to correct this?

---

### Post by kevdog on 2009-01-16
I dont understand your setup -- you have two wireless interfaces?  One needing a static address and the other needs dhclient?

---

### Post by jay2 on 2009-01-17
nope... just one wireless interface.
but if i remove that static ip addresss in the interfaces, i get an error everytime i do /etc/init.d/networking restart.


here's what the script does:

inside, there is a number of access points listed, one by one, it will try to associate, if it fails in the first, it will move on to the next. once successfully associated, it will request an IP address through dhcp. Next, it will test whether dhcp request was successful by looking at the output of ifconfig. Then it will test for internet connection by pinging netcraft.com. Finally an ssh tunnel will be established.

I'm thinking maybe the right way to do this is to put the AP association in one pre-up script, and the internet connection checking in the post up changing the interface to inet dhcp instead of static. But i guess it will complicate everything.
Like when after successfully associating, then DHCP fails on one access point i have to call that associating script again and bring up the interface probably through /etc/init.d/networking restart and then ping check the connection again. If i do that, i will just end up associating with the dead AP again.

---

### Post by kevdog on 2009-01-17
Why dont you put your script in /etc/rc.local?   You could then add some logic at the top of the script to make sure the interface was up, and somehow check that various AP could be seen using iwlist scan.

Another suggestion, if you are going to use the /etc/init.d/networking route, you can't just assign a dynamic address using something like

auto wlan0
iface wlan0 inet dhcp

I would add post-up and pre-down directives, since when the interface is brought down, you should probably break the ssh connection.  Do you have a return value for your script?

---

### Post by jay2 on 2009-01-17
> **kevdog said:**
> Why dont you put your script in /etc/rc.local?   You could then add some logic at the top of the script to make sure the interface was up, and somehow check that various AP could be seen using iwlist scan.

Another suggestion, if you are going to use the /etc/init.d/networking route, you can't just assign a dynamic address using something like

auto wlan0
iface wlan0 inet dhcp

I would add post-up and pre-down directives, since when the interface is brought down, you should probably break the ssh connection.  Do you have a return value for your script?


if i will make the iface dhcp, that would mean AP associating will be done in pre-up script or the built-in support for it. Then after associating, it's time to bring up the interface using DHCP (which may sometimes fail and it will be hard to add another logic that will associate to another AP). So to work around this, I put everything in one post-up script.

The script will:
1. associate to a working ap (verify if association successful)
2. obtain dhcp, verify if successful
3. ping an Internet address, verify if successful
4. if one of the above fails, move on to the next AP.


Then I put the reverse SSH tunnel in another crontab script, making sure it's always up by checking the existence of a process id with a name like ssh -NR, finally setting "AliveInterval" on both ends of tunnel so that everytime there is a failure in the link and the wifi moves to the next AP, the tunnel will be removed cleanly, and ssh tunnel check script will happily create a new tunnel again..


Works perfect for me. If the internet connection on one AP dies, it will move on to the next. SSH reverse tunnel is always ON so I can always ssh to the internal box through an Internet accessible host.

---

