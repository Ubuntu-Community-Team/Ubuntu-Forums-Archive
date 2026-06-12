---
title: "Auto Shutdown Home Server?"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by 337Manni on 2009-10-23
I have a PC with Ubuntu Alternate 9.04 installed across a RAID 1 array.
   
  I would like to use this PC as a server / NAS for mainly media and have it located out of the way. The PC would only be in use some of the time (possibly a couple of hours a day) and the contents would be going to Ubuntu / Kubuntu and XP clients.
   
  I have managed to set up the system to wake on LAN (WOL) and have tested this successfully (Not tested with XP as of yet) . However I would like to power down the PC without having to go to it (I may be locating it in the loft you see).
   
  The reason for posting is I’m not sure of the best way of doing this, or how to do it.
   
  The first thought I had was to send a command from the ubuntu or XP client to shut down the server. The only way I could find to do this was to login to the server with ssh and power down the server. This seemed a long way of doing this as I didn’t want do anything special with it.
   
  I then also thought that the server could be in use by more than one client at a time, so this method could be flawed anyway.
   
  I then started thinking about the server shutting itself down. This would be easier to do from and end user point of view as they didn’t have to remember to power it off.
   
  I know I can put the system to sleep if the system is idle for X minutes, but I would like to shutdown the server after X minutes to save as much power as possible. Also I would like to make sure no one is in the middle of using the server (they could get called away for something when using it) when it is shut down. This would possible have to monitor the LAN?
   
  If I couldn’t shutdown like this I would also consider Hibernate or Sleeping.
   
  Is this possible and can anyone help assist in doing this with me?
   
  Kind Regards.

---

### Post by 337Manni on 2009-10-24
Anyone?

---

### Post by 337Manni on 2009-10-25
Has anyone any idea how I could power down the system over a LAN or by itself if idle?

---

### Post by 337Manni on 2009-10-26
Is it possible to send terminal commands over a home network[FONT=monospace]?[/FONT]

---

### Post by SideSwipe on 2009-10-26
It is indeed possible to send terminal commands over a network, the easiest way I know of is to install an OpenSSH server (either via Synaptic or apt) on the machine.

Then on your client computers install an OpenSSH client of your choice (for Windows I'd recommend Putty, which I think there is also a version for Linux) and connect :)

Tis what I do in work when I need to control one our servers in the server room!

---

### Post by Iowan on 2009-10-26
The SSH client should already be installed on Ubuntu. The server part will (probably) need to be installed... 
Then **sudo shutdown -h now** should work. (**sudo halt** also works).

---

### Post by 337Manni on 2009-10-27
Thanks for the reply's. Much appreciated.

I'll have a try at this when I'm back home, but is there a way of simplifying this or automating it? This is going to be used by the rest of the family. An icon on the desktop in XP would probably be the simplest way. Double click and the server shuts down. Hopefully Putty should be easy to use.

Another thought is that in the power management settings there is an option to sleep if idle for X minutes. Could this be modified to shutdown instead of sleep?

---

### Post by Lars Noodén on 2009-10-27
To add to what @Iowan wrote, in addition to shutting down immediately [shutdown](http://manpages.ubuntu.com/manpages/karmic/en/man8/shutdown.8.html) can also be used to specify a time to turn off the machine.  

```

# relative time
 sudo shutdown -h +61 "turning off in an hour and one minute from now"
# or absolute time
 sudo shutdown -h 17:00 "we'll shut down for the day at five o'clock"

```

One thing to double check is if your hardware requires an explicit power-off or halt. (-P or -H).** Some hardware will need one or the other or both and the OS will turn off but the power still run...  :(

```

# from /etc/sudoers
%admin ALL=(ALL) NOEXEC: NOSETENV: NOPASSWD: /sbin/shutdown -[rhHPkc] [+0-9n][0-9\:ow]*

```

When testing scripts or parameters for shutdown, you can try -k to avoid actually shutting down the system.  It's more useful in a mult-user environment.  

If you have another machine available, even a router, on the same subnet with a wake-on-lan tool and if the server's network hardware can be activated with wake-on-lan, then you have ways to turn the machine on and off remotely.

---

