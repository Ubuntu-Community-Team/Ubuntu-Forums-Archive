---
title: "Run Script on network connection"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by boblemur on 2009-03-01
Hey all,

I wanted to run a script when ever the eth0 or eth1 connected/reconnected

so once on boot and again when ever i change wifi access point or plug the ethernet cable in.

Im trying to do this because, i want to make it automaticly detect where i am (from the ip and some pings) and set /etc/hosts, and my firefox proxy accordingly.

thanks for any help in advanced

---

### Post by puppywhacker on 2009-03-01
in the /etc/network/interfaces file you can add the "up" statement.

Some examples can be found here
/usr/share/doc/ifupdown/examples

```
iface eth1 inet static
        address 192.168.1.2
        netmask 255.255.255.0
	up /usr/somescript.sh

```

---

### Post by eosha on 2009-12-29
My interfaces file is basically empty. My wireless connection isn't showing up in it. Can I add this command so it runs for ALL interfaces, not just the ones listed?

Also, I tried putting it in /etc/network/if-up.d/ but the wireless connection scripts don't seem to call if-up directly.

Other ideas?

I currently have the script running hourly via cron. This works, but it's inelegant.

---

### Post by bwashed on 2010-01-09
I'm trying to do something similar. My script start fine on on-up and on-down.

```
#!/bin/sh
echo `date` $0 >> /home/<username>/testupdown.txt

```

Put this piece of code in a file, make it executable and copy into the directories
/etc/network/if-down.d  
/etc/network/if-post-down.d  
/etc/network/if-pre-up.d  
/etc/network/if-up.d

Now watch testupdown.txt with [FONT="Courier New"]tail -f testupdown.txt[/FONT] in a different terminal window.

---

### Post by bwashed on 2010-01-09
I don't claim this is the way to do it btw. I've seen comments stating that using [https://launchpad.net/upstart](https://launchpad.net/upstart) is the preferred way to hook into events on Ubuntu.

---

### Post by iponeverything on 2010-01-09
this can also be done with nm:
[http://sysadminsjourney.com/content/2008/12/18/use-networkmanager-launch-scripts-based-network-location](http://sysadminsjourney.com/content/2008/12/18/use-networkmanager-launch-scripts-based-network-location)

---

### Post by fiasco_averted on 2011-10-04
It seems like you'll be running this on a netbook or laptop, so I would recommend making the script only run when connected to your home network otherwise you might look like a malware package calling home when you take your computer to a school corporate network.  

I second iponeverything's recommendation of NetworkManager.

---

