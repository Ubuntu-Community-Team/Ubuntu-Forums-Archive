---
title: "Network services unavailable until user logs into the GNOME desktop"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by lrrodrig on 2009-11-30
This has been a problem for a while, but the frustration level has just gone to the redline.

After a reboot, no network services are available on the machine until AFTER a user logs into the GNOME desktop. If a user logs in to a vtty, they can access services just fine, but remote users cannot. I know for a fact that this affects apache, samba and sshd.

I've not configured any funky firewall of any sort, nor have I gone out of my way otherwise to block access. The block goes away within moments after a login to GNOME.

Any help resolving this would be greatly appreciated.

---

### Post by lrrodrig on 2009-12-01
Am I the only one since 2004 to run across this problem (there's an old thread from back then that just kind of falls off without a resolution). 

Obviously the problem isn't with Upstart, since the services are available locally from a tty login. It makes me think of a firewall or network issue (maybe the interface isn't being plumbed until the user logs in)?

Actually I'll pursue that last thought, but I'd still like someone else to weigh in with their thoughts.

---

### Post by lrrodrig on 2009-12-01
Additional thoughts on my part:

When I set up this machine, I setup the network using the Network Manager applet. When I look at /etc/network/interfaces, the configuration I created in Network Manager isn't there (I don't use DHCP, so I should see the information I supplied to the applet). This leads me to think that network configurations provided there are only created after a user logs in from GDM. That would certainly explain why the services worked from the loopback address (oh, how I wish I'd thought to try the staticly-assigned non-routable address instead of that oh-so-convenient 'loopback' shortcut), but not from another machine on the LAN.

So, I've placed my network configuration in /etc/network/interfaces and next time I have to reboot the machine for anything, I'll test it and let you guys know.

If, however, any of you think I've lost my mind, let me know. :D

---

### Post by Chas_E_Erath on 2009-12-01
Hi lrrodrig,

I have lots of thoughts on this, but before I blab drivel, I'd like to know if there is wireless stuff involved.  After that, I'll try and blab pertinent drivel.

Thanks.
Chas.

---

### Post by lrrodrig on 2009-12-02
There's a wireeless keyboard and mouse... ;)


I kid! Seriously, no wireless network anywhere in this machine.

---

### Post by gradinaruvasile on 2009-12-02
> **lrrodrig said:**
> Additional thoughts on my part:

When I set up this machine, I setup the network using the Network Manager applet. When I look at /etc/network/interfaces, the configuration I created in Network Manager isn't there (I don't use DHCP, so I should see the information I supplied to the applet). This leads me to think that network configurations provided there are only created after a user logs in from GDM. That would certainly explain why the services worked from the loopback address (oh, how I wish I'd thought to try the staticly-assigned non-routable address instead of that oh-so-convenient 'loopback' shortcut), but not from another machine on the LAN.

So, I've placed my network configuration in /etc/network/interfaces and next time I have to reboot the machine for anything, I'll test it and let you guys know.

If, however, any of you think I've lost my mind, let me know. :D

Network Manager IS NOT compatible with the interfaces file.
The only thing that is supposed to be in it is

auto lo
iface lo inet loopback

for Network Manager (or Wicd for that matter) to work.

And AFAIK Network Manager starts only when the user logs in. 

Use Wicd if you want to have a graphical network manager that starts even without logging in.

Network Manager and Wicd dont work right if you have other settings than those above in the interfaces file.

Or dont use Network Manager nor Wicd, only edit the interfaces file.

That's good if your computer uses fixed settings and you know a bit of networking. 
The most stable solution because it uses the built in Linux networking (thats a proven and very stable part of the Linux kernel) without GUI stuff that in turn depend on X sessions. 
The downside is that you dont have graphic monitoring if the cable is unplugged etc.

---

### Post by Chas_E_Erath on 2009-12-02
I'm afraid I'm not much help...my powers are meager and (usually) lacking...

Its a hack, but I'd try stopping & starting services via /etc/rc.local to see what happens - as well as turning off avahi & network-manager.  (not necessarily in that order)

Good luck.
Chas.

---

### Post by gradinaruvasile on 2009-12-02
I would say the best solution right now is that you just install Wicd. It will start at boot and does not need to log in to GDM.

First make sure your /etc/network/interfaces file has only the following lines:

auto lo
iface lo inet loopback

Then, in a terminal:

sudo apt-get install wicd

this will remove network-manager and replace it with Wicd. Restart.

---

### Post by lrrodrig on 2009-12-02
I'll take a look at the Wicd thing later tonight and keep editing the interfaces file as a backup.

Truth be told, I much prefer editing the interfaces file. I'm a FreeBSD guy from way back, and poking values into a configuration file just seems like the "proper" way to do things.

---

### Post by Iowan on 2009-12-02
Network Manager (dunno about WICD) *should* ignore interfaces configured in */etc/network/interfaces*... The interfaces file *should* work at boot time. Dunno if Karmic does things differently, though.

---

### Post by lrrodrig on 2009-12-08
Well, I'd say this counts as solved. Editing /etc/network/interfaces (and don't forget 'auto eth0'!) resolved the problem. Upon login, a quick look at Network Manager revealed that it was no longer attempting to configure eth0.

I have to say, I was rather surprised at the difference in the way the network is treated depending on where you configured it. That's probably quite unreasonable on my part, since one of the reasons we use a *nix is that it's NOT a monolithic GUI driven OS. :D

---

