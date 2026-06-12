---
title: "Wireless on an HP TX1340 laptop with ndiswrapper"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by bizt on 2009-07-17
Hi,

Ive just newly made the leap from Windows to Linux and got Ubuntu 9x on my HP TX1340ae (TX1000 range) laptop

Ive followed the instructions from a few pages and they all recommend ndiswrapper and the set of drivers that I appear to have. One page is:

[http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/](http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/)

To confirm the model of wireless card Ive done:

[FONT=Courier New]lspci[/FONT]

.. which returns:

[FONT=Courier New].
.
.
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)[/FONT]

Now, I follow through the instructions and pretty much nothing. When I do the following however:

sudo ndiswrapper -l

.. I get:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4328) present (alternate driver: ssb)

It appears that the driver is installed (I think) but I dont really know what the warnings are. Also should I now have wireless available? .. or do I need to set this up? Apologies for the lameness of my attempts at any alternative but I really dont know enough yet .. its all so new, not that I was any wiz at windows either mind u lol

Anyway if anyone could offer any help it would be much appreciated

Cheers
Bizt

---

### Post by Ayuthia on 2009-07-17
Did you try using the Broadcom STA driver from System->Administration->Hardware Drivers?  You should not really need ndiswrapper.

However, if you want to use NDISwrapper, you might want to first check and see what modules are currently loaded:
```
lsmod|gre -e b4 -e ssb -e ndis -e wl
```
If b43, ssb, or wl show up, the ndiswrapper module will not work.  You will need to do the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```
If it shows wireless sites, then all is well.  Otherwise, you can come back and post what happened along with:
```
lshw -C network
```

The warnings that were given about blacklist and ndiswrapper is letting you know that in the future all things in /etc/modprobe.d will need to have an .conf extension.  If you already have a blacklist.conf file out there, you should combine the information that is in blacklist into it.

---

### Post by bizt on 2009-07-18
Yeh that seemed to fix it thanks! Yeh I was getting ssb appearing (whatever that is) after doing:

lsmod|grep -e b4 -e ssb -e ndis -e wl
.. so followed your steps and I now have a list of available wireless connections. Btw I did have a look in System->Administration->Hardware Drivers and where the the wireless card was it had a green light icon next to it and status was "driver enabled but currently not in use". Funny enough I get the same message now even though I using the wireless ..? Not that Im complaining or anything, it works now! :D

Thanks again
Bizt

---

### Post by bizt on 2009-07-18
Hi again,

Ive just restarted my laptop and notice that the wireless connections are no longer there. When I run the line:

lsmod|gre -e b4 -e ssb -e ndis -e wl
.. I get that ssb appearing again. I can get the wireless back on by just running through your instructions but whats the best means for having this setup (and if the wireless is available, automatically connect) when ubuntu starts up?

Also, what is ssb? Why does this prevent wireless from working?

Cheers
Bizt

---

### Post by ddrichardson on 2009-07-18
You can blacklist the ssb module by adding a line to /etc/modprobe.d/blacklist.conf:```
blacklist ssb
```As for the warnings about the .conf files, ignore it as it will be addressed in a later release of the module tools.

---

### Post by ddrichardson on 2009-07-18
Sorry, your question - ssb module is for Sonics Silicon Backplane more commonly referred to as SiBa. Its a backplane bus protocol used in Broadcom SoC devices.

---

### Post by bizt on 2009-10-31
> **Ayuthia said:**
> Did you try using the Broadcom STA driver from System->Administration->Hardware Drivers?  You should not really need ndiswrapper.

However, if you want to use NDISwrapper, you might want to first check and see what modules are currently loaded:
```
lsmod|gre -e b4 -e ssb -e ndis -e wl
```If b43, ssb, or wl show up, the ndiswrapper module will not work.  You will need to do the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```If it shows wireless sites, then all is well.  Otherwise, you can come back and post what happened along with:
```
lshw -C network
```The warnings that were given about blacklist and ndiswrapper is letting you know that in the future all things in /etc/modprobe.d will need to have an .conf extension.  If you already have a blacklist.conf file out there, you should combine the information that is in blacklist into it.


Hi again, I have just installed Ubuntu 9.10 and now I cannot connect the way described above. Ive used the same link to that I provided above in my first post and your technique to disable ssb (I had it all in a handy script that when I want to connect to wireless I just ran that, worked every time thanks :p ). 

Just to confirm that the driver is installed (sudo ndiswrapper -l) I get:

```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4328) present (alternate driver: ssb)
```Note: by this point I have run the code you provided to ensure ssb wasnt messing things up for me here, dont know if the part about "alternative driver: ssb" was there with v9.04. Mind you, if I run "lsmod|grep -e b4 -e ssb -e ndis -e wl" it only shows "ndiswrapper" and no "ssb" too

As you instructed should I get any errors, at this point Ive tried running the following (as super user as it gave me a warning before):

```
lshw -C network
```.. and got this:

```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:c8000000-c8003fff memory:c9200000-c92fffff(prefetchable)

```I dont really know a great deal about where the problem is but hopefully this will be clearer to somebody. I would like to start getting to grips with 9.10, I understand its still in early release though. Maybe this is an issue that an update will resolve, I dont know. Anyway if any one can offer some advice I would much appreciate it, otherwise Ill just go back to using 9.04 on my laptop

Cheers
Bizt

---

