---
title: "Lost eth0 entry after taking regular updates - no internet now"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by molly.moggins on 2012-06-06
I have been running 12.04 for a while now and today I have a problem which seems to have arrived with the latest set up updates via update manager.

I have no internet connectivity at all and ifconfig no longer shows an entry for eth0, my wired connection.

When I use the system settings tool under Network I get an error message saying "network services are not compatible with this release" which flashes up in a box after I see a brief message saying that my network cable is unplugged - which it isn't.

I am forced to use a Windows laptop to access the internet and I have no idea what to do about fixing this. 

I saw a suggestion elsewhere that I should install wvdial which I did and I ran wvdialconf but that told me it was unable to detect a modem.

I am not sure that was about my problem anyway. 

I am also posting this in the Upgrades forum.

---

### Post by DennisNoVA on 2012-06-06
Ditto for me.  I lost my wireless connection with exactly the same signs.

I have a wireless card.  When I couldn't get it to work after yesterday's upgrade (6/5/2012) I tried my wired connection.  

ifconfig shows no wlan0 or eth0

So unless someone comes up with a live CD fix or USB stick fix this may take a reinstall.  Most unhappy with no network.  

This is being written from Windows, all the hardware still works under Windows.
Definitely hardware and pretty definitely yesterday's updates.

---

### Post by molly.moggins on 2012-06-06
I have found a workaround elsewhere, which is to start the network manager manually.

My internet is back now

**sudo service network-manager start**

It would be good to know what caused this problem though and get it fixed permanently.

---

### Post by gordond on 2012-06-15
Ditto:

Thanks for the solution Molly. Off to try it.

Namaste.

---

### Post by gordond on 2012-06-16
Worked for me Molly.

In my case networking was already running (even though nothing could access the Internet except, I discovered, the updater that caused the problem in the first place!). So I had to stop Network-Manager first - then restart it. Normal service was then resumed - but only until next boot up when it's back to square one with no Internet access. 

Hope a permanent fix is forthcoming soon.

Thanks again Molly.

Namaste.

---

### Post by DrKosy on 2012-06-16
Same problem here and thank's to molly same solution here ):P
There is only one problem left. During boot up ubuntu tries to configure network connections. This takes nearly 2 Minutes and fails at the end. Usually I have a boot time of half a Minute. So is there any way to get rid of this pre start network konfiguraion?

---

### Post by indie56 on 2012-06-16
Hello:
I also lost my internet connection. Restarting NM does not work for me.
I have a rt3090sta, which is shown to be active but not i use.
Can somebody please help me in this.
Thanks
Indie

---

