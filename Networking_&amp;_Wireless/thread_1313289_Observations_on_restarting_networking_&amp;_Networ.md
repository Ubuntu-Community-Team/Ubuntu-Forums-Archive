---
title: "Observations on restarting networking &amp; NetworkManager"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by lotuseclat79 on 2009-11-03
I run from the Karmic 9.10 Live CD, with packages added via tarball after booting up.  I have a Verizon FiOS router/connection to the Internet.

I never turn on my router until my setup, and initkarmic scripts are complete which initialize iptables among installing the tarballs, etc.

Occasionally, I run into the problem of a hinky turn on of the router and am left with no connection - only to have to reboot and start over again.

Previously, in Jaunty, Ubuntu 9.04, I would issue the following two commands to correct the situation - real simple and always worked for me, and sometimes just to be sure of the networking state, I would issue a stop for both before issuing the restart:
$ sudo /etc/init.d/networking restart
$ sudo /etc/init.d/NetworkManager restart

Since Karmic is different with the upstart-job, I have noticed that I am still able to issue:
$ sudo /etc/init.d/networking restart
which always seems to work, but the other command does not work and suggests using service/upstart commands.

What I have observed on a successful attempt by saving both before and after I turn the router on of the output of $ sudo ps x, is that the following process enables the NetworkManager connection with networking which I assume connects the router with the computer's hardware network device driver:
/sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid
/usr/lib/NetworkManager/nm-dispatcher.action

So, the next time I am left in the state where when I turn on my router and am still left disconnected, I will manually try each command in order to see what happens:
sudo /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid
sudo /usr/lib/NetworkManager/nm-dispatcher.action

I know there is advice to use the service command and/or upstart, but the user documentation at this point in time appears to be lacking or is just not coherent to us mere mortals (take note networking Gods!) ):P):P):P

If you are a knowledgeable Karmic network developer reading this and have a simple solution that works - please post it here.

-- Tom

P.S.  The experiment did not work, i.e. the network was down message resulted.

---

### Post by preserve on 2010-01-30
I am still in Jaunty and was having the same problem. What finally worked for me was to write a script that does the job. It finally worked when I added a modprobe -r and then a modprobe for the specific wireless driver modules. That may be because I am using ndiswrapper and a windoze driver. The sequence of events is important.

1. Right click to remove check marks in "Enable Wireless" and "Enable Networking" in the NetworkManager applet.
2. The script runs the following commands: /etc/init.d/Network Manager stop
3. /etc.init.d/networking stop
4. modeprobe -r ssb
5. modprobe -r b44
6. modprobe -r ndiswrapper
7. I have to power down then power up the wireless router but may not be necessary with every router.
8. Now reverse the order of steps 2 thru 6, this time loading modules and starting the two processes.

The modules chosen to reload will depend on the wireless NIC you use. The "Enable Networking" and "Enable Wireless" will be checked after starting NetworkManager. It may connect on the first attempt or with WPA, answering the password question once does the trick. This is more of a bandaid than a fix in NetworkManager but is better than having to reboot each time the wireless goes down. My wireless is the wmp54gs (Broadband BCM4318 chip.) The driver with ndismanager is wmp54gsa. Hope it works for you.

---

