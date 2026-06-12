---
title: "autho eth0 option gone"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by kmaster228 on 2009-08-21
hey all recently after powering up my laptop i found that auto eth0 option was not there and that was the default network option i was using, and when i click the network icon it says device unhandled, im not quite sure what to do can some one help me?

---

### Post by Iowan on 2009-08-21
What is in */etc/network/interfaces*?  It should only have a couple of lines relating to "lo".

---

### Post by kmaster228 on 2009-08-23
thank you for your reply, this is the contents of /etc/network/interfaces

```

auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual


```

---

### Post by Eudoxia on 2009-08-23
Same thing happened to me after running sudo pppoeconf.

I reinstalled :(

Currently trying to solve another problem with the internet

---

### Post by shredder12 on 2009-08-23
Its a regular problem.. jst change you /etc/network/interfaces file to the following..

```

auto lo
iface lo inet loopback


#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
#provider dsl-provider

#auto eth0
#iface eth0 inet manual


```

 I have jst commented the last 5-6 lines..
Now, reboot your system and then your network manager should no more say that wired network devices are not managed.
Then.. jst right click on the network manager and go to edit connections and add a new connection named auto eth0.. 

I had the same problem after configuring my pppoe modem
and this solved my problem..
Hope this works for you..

---

