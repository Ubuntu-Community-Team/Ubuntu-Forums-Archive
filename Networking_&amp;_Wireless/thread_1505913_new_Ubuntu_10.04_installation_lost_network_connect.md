---
title: "new Ubuntu 10.04 installation lost network connectivity"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by patfla on 2010-06-09
I converted my ideapad y550p to a Windows 7 and Ubuntu dual boot according to the following:

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

Which worked fine.  Network was working for a while.

Decided I preferred KDE to Gnome and at some point added the KDE desktop by installing

kubuntu-desktop

KDE worked fine and networking continued to work.

And then the network (wireless - wlan0) seemed to up and quit.

I read these instructions:

[http://ubuntuforums.org/showthread.php?t=1494628](http://ubuntuforums.org/showthread.php?t=1494628)

which didn't help.

I've used all of 

ifconfig
sudo iptables -L
sudo lshw -C network
looked through /etc/resolv.conf
etc

all to no avail.

I could simply reinstall however that won't teach me what went wrong.

Oh.  I'm almost certain the problem is with dhcp because I can do:

sudo dhclient

and it simply loops over and over broadcasting to 255.255.255.255 asking for an IP address and it never seems to get one.

I assume the problem must be with the Ubuntu installation because then I reboot the same machine into Windows 7 and it has no problem getting a network address.

---

### Post by Iowan on 2010-06-09
Check */var/lib/NetworkManager/NetworkManager.state* Values should *probably* be "true". [This]("http://ubuntuforums.org/showthread.php?t=1505217") thread has some suggestions - you might want to make backup copies somewhere before deleting the file...
[This]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") option hasn't been helpful lately, but is offered as something to try...

---

### Post by patfla on 2010-06-09
Thanx Iowan.

That was interesting.  I'd been putting up with this for the last day before I first posted so, prior to your response, I simply reinstalled Ubuntu reformatting the target partition, etc.  Which was quick.

The first thing I did was to login into Gnome and add kubuntu-desktop (KDE that is).

Reboot, etc and login to KDE.

Now here's the wrinkle.  As part of locking down my home network, I've set my router so that it doesn't broadcast its SSID.

Once logged into KDE I couldn't for the life of me figure out how to specify that the desired network was unadvertised (its SSID).  So this time, having things a little clearer in my head, I logged out of KDE and back into Gnome.  In Gnome I was able to specify the SSID and connect to the network.  ifconfig now finds an IP address and everything downstream of that works.

I figured that doing something like this, even if in Gnome, would set system values so that when I log out of Gnome and back into KDE I would find something suitable (that is, my secret SSID cached someplace) so that I'd be able to connect from KDE.

And this did work.

So I guess my problem is/was specifying the SSID from kunbuntu which I suppose I should take to a kubuntu forum somewhere.

Is there anyway to specify an SSID value to dhclient or some other command-line tool?

---

