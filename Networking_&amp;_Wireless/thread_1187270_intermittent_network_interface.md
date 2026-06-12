---
title: "intermittent network interface"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by duffrecords on 2009-06-14
One of my computers is having an intermittent network problem.  Every few minutes (it's different each time) the network interface seems to stop listening.  I can't ping it from other machines on or off my home network, but from that computer I can ping anything.  After I do that, it's back to normal and other machines can ping it again.  Or, if I wait several minutes, it will eventually fix itself.  If I'm using that computer directly, there's never any loss of connectivity to other machines.  This is not specific to any one application; it happens with MythTV, VNC, and even a simple SSH session.  How can I troubleshoot this?

---

### Post by superprash2003 on 2009-06-15
is this a wired or wireless interface?

---

### Post by dibuntux on 2009-06-15
I also have an intermittent network problem since upgrading from 8.10 to 9.04 on a 64 bit system. Sometime everything works, and sometimes not. If I have Skype on, I can tell by seeing the Icon grey & searching for a connection; on FireFox it does not load any sites. I have to manually disconnect & connect again on Network Manager.
And sometimes I cannot connect to a machine on the same LAN.
I have VMWare server 2 with bridged eth0: that always work OK! Sometimes FireFox cannot load sites and Windows in VMWare is working correctly on the internet. Sometimes I can connect to the internet from Windows but cannot connect to local shares on the SAME machine via samba.
My LAN is wired, with one switch and one ADSL router to the internet. I use fixed IP.

I also found this in syslog :
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 

But could not find any suggestions.

Anyone? TIA

---

### Post by duffrecords on 2009-06-15
It's wired.  I've tried replacing the ethernet cable with a new one and I've tried a different port on the router.

---

### Post by superprash2003 on 2009-06-15
you could try changing MTU values , may work [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by duffrecords on 2009-06-19
It turns out the problem was one I suspected but didn't want to accept as a possibility: I'm using a real-time kernel, as this system is used primarily as an audio workstation.  I rebooted using the vanilla kernel and haven't had the problem since.  Of course, now the system is not suitable for real-time audio work.  I wish I could switch kernels on the fly without rebooting.

---

### Post by dibuntux on 2009-06-20
Sorry, in my case I determined the problem, with the help of the VMWare forum, and I forgot to post it here.

It is known problem with VMWare, server 2 in my case, and the bridge eth0.

As soon as you stop the server with
sudo /etc/init.d/vmware stop
networking just work fine!
and if you start it again 
sudo /etc/init.d/vmware start

it keeps going. For now I just keep stopping and starting the server at every session. Annoying but it works.
Thanks

---

