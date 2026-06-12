---
title: "Questions related to removing network manager"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by ub07 on 2012-07-15
My computer is a laptop running Ubuntu 12.04. I connect to the internet primarily via a ppp dial-up connection and very occasionally through Wi-Fi. To solve a problem that I talked about in this thread: [http://ubuntuforums.org/showthread.php?t=2022680]("http://ubuntuforums.org/showthread.php?t=2022680"),
I removed the network manager. That solved the problem. Now I need to configure my network manually.

The computer now waits at boot for a network configuration, but I don't want to log on to any networks at boot. I know how to set /etc/network/interfaces to automatically dial via wvdial at boot, but I don't want to do that. I just want to boot up and use Gnome PPP or WiFi when I need to. 

How do I tell the system that I do not want it to look for a network at boot? Remove the "auto" parameter in the file /etc/network/interfaces? If so, do I also remove it from the loopback entry?

Also, are there any good third-party network managers for Wi-Fi? I found a couple in the Software Center, but I don't know which is best.

Thanks.

---

### Post by redmk2 on 2012-07-15
> **ub07 said:**
> My computer is a laptop running Ubuntu 12.04. I connect to the internet primarily via a ppp dial-up connection and very occasionally through Wi-Fi. To solve a problem that I talked about in this thread: [http://ubuntuforums.org/showthread.php?t=2022680]("http://ubuntuforums.org/showthread.php?t=2022680"),
I removed the network manager. That solved the problem. Now I need to configure my network manually.

The computer now waits at boot for a network configuration, but I don't want to log on to any networks at boot. I know how to set /etc/network/interfaces to automatically dial via wvdial at boot, but I don't want to do that. I just want to boot up and use Gnome PPP or WiFi when I need to. 

How do I tell the system that I do not want it to look for a network at boot? Remove the "auto" parameter in the file /etc/network/interfaces? If so, do I also remove it from the loopback entry?


Also, are there any good third-party network managers for Wi-Fi? I found a couple in the Software Center, but I don't know which is best.

Thanks.
Yes you can (should) remove the 'auto' parameter from any interface that you don't want up at boot time.  The interface lo is virtual so you can leave it as 'auto' since it should only bring up a 127.0.0.0/8 network.

I use WICD on my laptops.  It works great.

---

### Post by ub07 on 2012-07-15
I removed the "auto" from everything, but the system is still waiting for a network configuration at boot. In fact, it seems that it is ignoring anything that I put in the interfaces file.

---

### Post by ub07 on 2012-07-15
I've traced the source of the delay to the file /etc/init/failsafe.conf. The beginning of that file has the line:

>  start on filesystem and net-device-up IFACE=lo 

Where is the script that brings up the net-device? It is not /etc/network/interfaces.

---

### Post by redmk2 on 2012-07-15
> **ub07 said:**
> I removed the "auto" from everything, but the system is still waiting for a network configuration at boot. In fact, it seems that it is ignoring anything that I put in the interfaces file.

The system doesn't perform correctly if you don't have the interface lo brought up.  You should always configure this to automatically be up upon boot.

---

### Post by redmk2 on 2012-07-15
> **ub07 said:**
> I've traced the source of the delay to the file /etc/init/failsafe.conf. The beginning of that file has the line:



Where is the script that brings up the net-device? It is not /etc/network/interfaces.

This is now all handled by upstart scripts.  Apparently the user now does not have to configure the lo interface.  See the upstart script```
/etc/init network-interface.conf
```

Upstart is best described [**_[COLOR="Blue"]here[/COLOR]_**]("http://upstart.ubuntu.com/cookbook/").

It appears that the hang is caused by Plymouth.  The script you mention adds a 20 second pause if the network is not up when that 'failsafe' script is run.

[COLOR="Blue"]Edit: As a temporary hack I suppose you could reduce the pauses to 0 (pause = 0).  I'm sure there's a more graceful method to this for the long term.[/COLOR]

---

### Post by ub07 on 2012-07-15
> **redmk2 said:**
> The system doesn't perform correctly if you don't have the interface lo brought up.  You should always configure this to automatically be up upon boot.

Done. No effect.

---

### Post by ub07 on 2012-07-15
> **redmk2 said:**
> This is now all handled by upstart scripts.  Apparently the user now does not have to configure the lo interface.  See the upstart script```
/etc/init network-interface.conf
```

Upstart is best described [**_[COLOR="Blue"]here[/COLOR]_**]("http://upstart.ubuntu.com/cookbook/").

It appears that the hang is caused by Plymouth.  The script you mention adds a 20 second pause if the network is not up when that 'failsafe' script is run.

[COLOR="Blue"]Edit: As a temporary hack I suppose you could reduce the pauses to 0 (pause = 0).  I'm sure there's a more graceful method to this for the long term.[/COLOR]

Thanks for this helpful information, though I will have to investigate exactly what Plymouth is. But, yes, Plymouth is definitely a problem. 

The failsafe.conf file actually adds 2 minutes of boot time (20 sec, 40 sec, and finally 60 sec in steps). My workaround has been to comment out the sleep statements (as advised to someone else on another forum for another problem). But as you have said, it is not very graceful and not very satisfactory. I'm sure there is a better way of doing it.

---

### Post by ub07 on 2012-07-16
I'm going to mark this thread solved because I thought about it carefully, and I think that reducing the sleep wait to 0 in /etc/init/failsafe.conf is the best possible solution. I remember that in the past, I had a Linux distribution that would say "failed" when it came to network configuration in the boot script. I really don't want to take away functionality that I might need in the future by doing further surgery. And as it stands now, all I have to do is to put the wait times back to their original values to recover the failsafe.

I'm still wondering how the network manager was able to bypass this failsafe because I'm using the same system, i.e. no network, as I was when the network manager was installed.

---

