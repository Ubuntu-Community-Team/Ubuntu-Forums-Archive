---
title: "Cisco vpn installation troubles"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by dkinfl on 2009-03-08
Hello.  I just switched to ubuntu on my new laptop after it came preloaded with vista 64 bit.  Ahem.  Anyway ubuntu is great!  it installed easy and is very light weight.  


However I am unable to install the cisco vpn client, which is necessary for my job.  I have downloaded versions that have been patched and followed other forum posts, but I still get this error.

Failed to make module “cisco_ipsec.ko”.

I am running 8.10 32 bit, kernel 2.6.27-11-generic.  Has anyone run into this even after patching the vpn install files?

Thanks for any info.

---

### Post by jonobr on 2009-03-24
Hello


Due to network configuration changes where I work, I now need to connect to a secure network, more often now then I used.

I usually used to setup a vpn from my windows box as I had to do it infrequently.

I did a search on ubuntu posts to see what the best approach was and I came across your post.

I figured I was going to have trouble setting up a cisco vpn client to get this done.

Anyway, I went to synaptic and loaded vpnc,
I then loaded the gui front end kvpnc (which people have said is a little buggy but the best one).

I cranked up the client, loaded in my pcf file which is my connection info for a normal cisco client, 
It walked me through a kwallet setup, and then ran the connection,
It asked me for a user name and password, I supplied it and bang I got in.
Figuring I had done something wrong, I started pinging around and remote desktopped to a few maachines and everything worked.
I used all default settings,

I then remembered your post and came back to it  as they used to have an old army saying
> if your attack is going well, its an ambush

Looking at it, I think you got a client that was not from synaptic.

Below are some details on my machine which may be useful for you,
but Im thinking if you can, try installing vpnc and kvpnc and see if that helps you out.
Let me know If I can get you more info


Thanks

kpvnc version 0.9.0 with kde 3.5.10

Ibex intrepid 8:10

32 bit Kernel


```
:~$ uname -a
Linux  2.6.27-11-server #1 SMP Thu Jan 29 20:19:41 UTC 2009 i686 GNU/Linux

```

---

### Post by dkinfl on 2009-03-30
After doing some reading, I was able to install vpnc and import my settings from my PCF file, and create the tunnel just fine.  Maybe not quite as nice as the Cisco software, but works none the less.s

---

### Post by jonobr on 2009-03-31
hello

one thing I notice, is that when I leave the client up for a long time, around 24 hours or so,
when I come back to it, the connection is open, but not passing traffic.
I need to close and reopen to get it working.
):P

---

### Post by mister_doctor on 2009-04-01
> **jonobr said:**
> hello

one thing I notice, is that when I leave the client up for a long time, around 24 hours or so,
when I come back to it, the connection is open, but not passing traffic.
I need to close and reopen to get it working.
):P

That might be the device accepting the vpn connection (router, PIX device, ASA device) doing that. At my office our policy is that after 20 minutes of inactivity, the connection is dropped.

---

### Post by jonobr on 2009-04-01
I originally thought it was some server side time out or inactivity timer not disconnecting the kvpnc client correctly,
Trying using a windows machine it seems to stay connected.

Im not too concerened with whats happening, as reconnection is relatively pain free

---

