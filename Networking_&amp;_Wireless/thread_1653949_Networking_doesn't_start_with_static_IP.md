---
title: "Networking doesn't start with static IP"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by Nayruu on 2010-12-27
Hi,

I'm running Ubuntu server 10.04 64 bit and I'm controlling it remotely.

/etc/network/interfaces is configured with eth0 and eth1; and internal and external network, and they are both static IP's.

Now.. this is all correct I believe because I can connect to it just fine, ***once*** somebody runs sudo /etc/init.d/networking restart
My problem that it doesn't automatically start networking or doesn't pick up static IP.. I don't know. And I can't really troubleshoot it well because I can only control it remotely.

My question is can I make some sort of script or startup application that will execute "sudo /etc/init.d/networking restart" right when it boots?
I actually have already tried making a startup application for it, but this failed. I think the error was because you have to run it as sudo, and I can't enter the password or know how to automate it.

My daemon.log says:

Dec 27 15:19:43 kernel: [  718.990004] eth0: no IPv6 routers present
Dec 27 15:19:43 kernel: [  719.030003] eth1: no IPv6 routers present
Dec 27 15:20:12 ntpdate[1355]: can't find host ntp.ubuntu.com
Dec 27 15:20:12 ntpdate[1355]: no servers can be used, exiting
Dec 27 15:21:43 ntpdate[1409]: name server cannot be used, reason: Temporary failure in name resolution

If anyone has suggestions on what could be wrong or how to make a script like that, I'd be really glad to hear it.

Thanks

---

### Post by cariboo on 2010-12-27
What does /etc/network/interfaces look like?

Make sure you have an entry that starts the network interfaces eg:

```
auto lo eth0 eth1
```

---

### Post by Nayruu on 2010-12-27
Yeah, interfaces is alright.

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

auto eth1
iface eth1 inet static
```

Plus correct ip info..

Meanwhile I managed to allow "*sudo /etc/init.d/networking **" to be executed without prompting for a password, and I added a simple shell script to startup applications to run it each time it reboots.

But still, this is unusual I guess.
I also tried *rcconf* and *chkconfig* to add the service to startup, but I couldn't get that to work either, chkconfig gave me a whole lot of errors when attempting to change the state of the networking service, and rcconf didn't list the service at all.

And "*sudo service networking restart*" gave me the error

*restart: Unknown instance:*

And now I have another problem, it seems the nameservers I specficy with the static IP, are not saved in */etc/resolv.conf*
Neither are they in

[I]/etc/resolvconf/run/interfaces
/etc/resolvconf/run/resolv.conf[/I]

This results to not being able to load webpages or use *apt-get*.. I didn't understand it at first since I was still connected to it remotely.

---

### Post by Iowan on 2010-12-29
Is the server located where you could attach a monitor and watch it start up (to see if services like networking actually start - or if an error message pops up)?

---

### Post by PatchesTheCaveman on 2010-12-29
> **Nayruu said:**
> Now.. this is all correct I believe because I can connect to it just fine, ***once*** somebody runs sudo /etc/init.d/networking restart
My problem that it doesn't automatically start networking or doesn't pick up static IP.. I don't know. And I can't really troubleshoot it well because I can only control it remotely.

My question is can I make some sort of script or startup application that will execute "sudo /etc/init.d/networking restart" right when it boots?
I actually have already tried making a startup application for it, but this failed. I think the error was because you have to run it as sudo, and I can't enter the password or know how to automate it.

This is totally a kludge, but you can add the */etc/init.d/networking restart* command to your */etc/rc.local* file so it's executed at the very end of your startup sequence and see if that helps.

It's probably worth investigating what's really causing this problem though.

---

