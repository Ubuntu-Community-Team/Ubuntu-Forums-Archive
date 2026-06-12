---
title: "Wired and Wireless won't connect."
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by Amcfar75 on 2011-05-05
I have recently developed a problem with my computer connecting to the internet which has totally stumped me and is currently forcing my to use windows much to my frustration.:( I am using ubuntu 10.04 on a Toshiba Satellite laptop. My wireless and wired network connections will not connect. They are all present in the menu and i can click on them but the connection tries to connect and then just times out and fails to connect. Everything still works fine in windows Vista. The more confusing thing is i tried some live disks to see if they would work but they all did exactly the same thing including a live disk of ubuntu 9.10 which used to work perfectly and live disks of openSUSE 11.4 and Mint 10. I struggling to tell if this could be a hardware problem or not. The fact that the live disks wouldn't work suggests a hardware problem but the fact that Vista still works totally throws that argument. I have looked all over these forums and elsewhere and have found some similar ish problems but non seem to have the severity of this one as all of those seem to be wireless only problems. The only thing that i was doing at the time this started was i had just set up a new secondary user account but i suspect that may be coincidental. 
I have been using Ubuntu for almost 3 years and have really enjoyed the experience and the community support but i really don't want to be forced back to windows by this please help. 
Many Thanks

---

### Post by Amcfar75 on 2011-05-07
Just an update on the situation. It turns out that i can connect with no problem to my uni open network. This suggests that the problem is with the router. I do not know much about routers but i did manage to set my home router which normally has WPA security to an open network with no security and found it still didn't work wirelessly or while wired in. Anybody got any advice on what to try with my router or things i need to try in Ubuntu to try and fix it?

---

### Post by agentsmith23 on 2011-05-07
Do you have your computer setup for DHCP automatic or do you have it setup manually? If you have it set up manually do you have it set to the correct subnet for your router? Can any other computers or devices connect to the router?

---

### Post by Amcfar75 on 2011-05-08
Thanks for replying. I have everything automatic and my flatmate's Vista machine has no problem connecting to the router. My router is on all its default settings. My Vista partition has no problem connecting to the router either. I have noticed that my ubuntu installation has been saying it has been failing to get some updates even when it did connect to the internet at uni as it has an invalid key or something along those lines. I can't get a copy of the actual error message just now as i need an internet connection on my Ubuntu side to get it(only available in uni at the moment). I will post that up tomorrow. Apologies for my general ignorance of some of the finer details of connecting a computer to the internet.

---

### Post by Amcfar75 on 2011-05-09
Here is the error message i get every time i run update manager. It will download some updates but not all of them i think. 

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found [IP: 193.63.235.250 8080]
Some index files failed to download, they have been ignored, or old ones used instead."

I do not know what causes this problem or how to solve it. Any help on this would be greatly appreciated. I am not sure if this is the cause or even linked to the wireless problem but it may be part of it so any advice is appreciated.

---

