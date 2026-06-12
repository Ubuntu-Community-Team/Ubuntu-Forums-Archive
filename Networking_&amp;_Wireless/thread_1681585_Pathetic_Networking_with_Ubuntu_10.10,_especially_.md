---
title: "Pathetic Networking with Ubuntu 10.10, especially after update"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by gurudev1000 on 2011-02-04
Hi,
I want to try Ubuntu but time after time something new pops up that makes me very frustrated.

this time, it's my internet. I have a new cable internet now. Before it was automatic login which wasn't a problem. Now it's cable login usrname and p/w which works perfectly find when you 'search networks' in Windows 7. but with Ubuntu, I have to add the connection which is fine. Problem arises when I click on the network manager icon and click on the connection and it simply doesn't connect. I need to click literally 20 times for it to connect once. this has gotten worse after updating.

If I don't get a good resolution to it, I don't think I have any hopes for this version of Ubuntu atleast.

Thanks for any Help.

---

### Post by gurudev1000 on 2011-02-06
Isn't there any solution to this? Perhaps changing the default network manager of Ubuntu to something more robust? what do I do?

---

### Post by Grova on 2011-02-06
I am using a BCM4318. Many say that the sta driver works wonders and that the additional broadcom driver will give you problems.

I just installed 10.10 yesterday and could not get any connection. Even wired!
Finally found my solution and my wired works flawless. Just activated the additional driver for my wireless card and tried connecting to me home network. 

At first, it did not connect, even with correct credentials. 
Then i did the same thing as i did for my wired network. (Manually assigned addresses)

Make sure your DNS address is not setup to be your default gateway/router address.

A thread i just posted on this exact issue:
```
http://ubuntuforums.org/showthread.php?t=1682734
```

---

### Post by gurudev1000 on 2011-02-12
> **Grova said:**
> I am using a BCM4318. Many say that the sta driver works wonders and that the additional broadcom driver will give you problems.

I just installed 10.10 yesterday and could not get any connection. Even wired!
Finally found my solution and my wired works flawless. Just activated the additional driver for my wireless card and tried connecting to me home network. 

At first, it did not connect, even with correct credentials. 
Then i did the same thing as i did for my wired network. (Manually assigned addresses)

Make sure your DNS address is not setup to be your default gateway/router address.

A thread i just posted on this exact issue:
```
http://ubuntuforums.org/showthread.php?t=1682734
```

Thanks for replying. But I get conection with the new cable guys internet by adding a new connection in the DSL tab instead of the WIRED tab of 'edit network connections.' There I clicked on ADD and simply added my service name and username in the required fields. This seems to be the info that is required since sometimes it does connect and once it connects I have full quality internet connection.

My only problem is understanding why it can't connect on a single attempt and why I have to use up literally 100's of mouseclicks everyday to get connected to the internet!

---

### Post by gurudev1000 on 2011-02-14
BTW, I just tried the Alpha2 of Natty. The net connection works perfectly once I add it!! I hope it continues with the final version too.

---

### Post by thefasterblueone on 2011-02-14
Try using "WICD" to manage your network. The default Network Manager is notorious for bad connections.

WICD is in the Ubuntu Software Center, just install it and see if your connection improves. Also try to go through your settings and fine tune them to get a better connection. 

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

