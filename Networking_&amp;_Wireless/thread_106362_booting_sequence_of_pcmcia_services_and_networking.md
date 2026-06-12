---
title: "booting sequence of pcmcia services and networking"
date: 2005-12-20
forum: Networking &amp; Wireless
---

### Post by lgaboury on 2005-12-20
During the boot process of my Ubuntu laptop machine, the networking services are started before the pcmcia services which causes the call to ntp.ubuntulinux.org to fail.  How can I modify the boot process in order to start the pcmcia services earlier to ensure that my wireless PCMCIA card is enabled before the network configuration is setup?

By the LED on the wireless card, I can see that it gets enabled just a second or so before GDM is loaded.  Once logged-on all network services work properly.  I am just looking at starting the PCMCIA services earlier during the boot process.  Not a huge issue, but your help will be appreciated.  Thanks.

---

### Post by Lambert on 2005-12-20
Look in /etc/rcS.d and notice which ones you want to change. I show pcmcia and pcmciautils starting at 40 for me.

Then do this.

```
sudo update-rc.d -f pcmcia remove
```

this removes the link

```
sudo update-rc.d pcmcia start 39 S .
```

this adds the link back and changes the start time to 39 instead of 40

---

### Post by lgaboury on 2005-12-21
Lambert, thanks for your help.

I looked in /etc/rcS.d and did not see any reference to pcmcia.  I did however noticed that it is present under runlevel 2,3,4,5 as S20pcmcia and runlevel 0,1,6 as K20pcmcia.

The funny thing is that when shutting down the laptop I can see a line stating that PCMCIA is shutting down, yet I can see that PCMCIA is starting when booting up the laptop.  Yet, the wireless card becomes active just as GDM is loading.

I looked at the pcmcia script in /etc/init.d.  There is a mention about laptop-detect.  Does this have anything to do with hotplug devices and this is why the pcmcia card only gets enabled only at the end of the boot process.

I tried to change S20pcmcia to a lower number.  I tried as low as S15.  This did not result in enabling the wireless pcmcia earlier.  In fact, it did not get enabled at all.  I had to run: sudo /etc/init.d/pcmcia start once logged on.

I still would like to ensure that my wireless networking is properly enabled earlier during the boot process.  This will become more important when I setup http and mail services.

Thanks again.

Luc.

---

### Post by Lambert on 2005-12-21
When I answered your question I was logged into dapper so my runlevels are different as there are changes.

When you changed it to 15, I believe there is a script that needs to run before it called makedev so that's why pcmcia didn't start when you changed lower.

Now I'm not sure I can help you but this is what I see. 

My card initializes during networking which is at level S40 so I'm not sure why yours starts so late. You say it starts just before the desktop. I believe the time you say your card initializes is around S99 so you can look in rcS and rc2 to see what's running there.

A test I would suggest trying is bring down your wireless interface and then run this command.

sudo /etc/init.d/networking restart

and see what happens. Your wireless device should come up. If so how long does it take?

---

