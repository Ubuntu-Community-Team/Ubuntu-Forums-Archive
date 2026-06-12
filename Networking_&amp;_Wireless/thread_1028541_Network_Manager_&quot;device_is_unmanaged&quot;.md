---
title: "Network Manager: &quot;device is unmanaged&quot;"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by nwu on 2009-01-02
I'm using Network Manager 0.7.0 on Ubuntu 8.10, with a Linksys WUSB100. After getting the rt2870.inf driver (from the "Win2K" folder on the CD), the card works great and lets me connect to the Internet, but I've found a small problem (it's not really a big issue, but I'd like to figure it out mostly so I can know how to use Network Manager better):

After I log into Ubuntu, Network Manager connects to my specified "connect automatically" network, but when I click on the icon, instead of there being a list of available networks, etc., under "Wireless Networks," there is simply "device is unmanaged." This means I can't change the network I want to connect to, look at connection statistics, etc. Oddly enough, if I unplug and replug my wireless card, Network Manager *does* manage my card, and I can see the list of networks, etc.

I've already tried both of the recommended modifications in [[COLOR="Navy"]this post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5926426"), but both times, Network Manager did not even detect my wireless card upon rebooting.

Thanks.

---

### Post by asg8516 on 2009-03-07
I too faced this problem with my Ubuntu Intrepid.

I found the following solution for the same:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417)

Hope that saves your day.

Happy Computing! :)

---

### Post by nwu on 2009-03-07
That thread is fairly long though; which post contains the solution you were referring to?

---

### Post by mchaggis on 2009-04-09
The following worked for me from that thread
> Whatever updates occurred in the last day set all the devices to managed=false in /etc/NetworkManager/nm-system-settings.conf

Change that and "sudo killall nm-system-settings" and it'll start working again.

Simple do the following:

```
sudo vi /etc/NetworkManager/nm-system-settings.conf
```

Change "managed=false" to "managed=true"

```
sudo killall nm-system-settings
```

The network manager then notifies you that the network was detect and attempts to connect you, so if all of your settings are correct then you'll have nothing to worry about.

---

### Post by Flimm on 2009-05-09
Thanks, that worked for me! (Replacing vi with nano of course)

---

### Post by n0deal on 2009-05-12
Thank you very much for the pointer. I was pulling my hair out trying to figure out why my wireless connection on my ubuntu 8.10 box suddenly stopped working. Cheers!

---

### Post by radixor on 2009-05-12
Thanks very much! This worked for me!

---

### Post by flarkit on 2009-05-19
> **mchaggis said:**
> The following worked for me from that thread


Simple do the following:

```
sudo vi /etc/NetworkManager/nm-system-settings.conf
```

Change "managed=false" to "managed=true"

```
sudo killall nm-system-settings
```

The network manager then notifies you that the network was detect and attempts to connect you, so if all of your settings are correct then you'll have nothing to worry about.

And your tip worked for me too! Thank you, thank you, thank you

---

### Post by Madh2orat on 2009-05-30
This worked for me as well, I was going a little bit crazy trying to figure it out.

What caused it to happen in mine -I believe- was using the aircrack-ng suite, somewhere in there putting my card into monitor mode must have dont it, but thanks to this post, it's all working again.

Thank you all so much.

---

### Post by guroos on 2009-06-09
i hope this works for me as well..........i'm gonna check it out..

well......***thanking u*** in anticipation

---

### Post by snowman2428 on 2009-07-09
mchaggis, you are the man. props to you.

---

### Post by filron on 2009-08-03
worked for me also, many thanks for saving my sanity!

---

### Post by ironsharpensiron on 2009-08-08
Thank You!

finally it works :)

---

### Post by Steve H on 2009-08-13
Brilliant! Worked for me!

Thanks

:)

---

### Post by TBlake on 2009-09-05
Worked for me on Ubuntu Studio 9.04.  Had to substitute in "nano" for "vi" like someone else mentioned.

---

### Post by vkpal on 2009-09-08
Thanks a ton, was going all over and this fixed it!

---

### Post by Firubat on 2009-09-10
yes worked for me too after i had a wired connection that was working but did not show up on the network mannager.
and i used "gedit" to change it
Thanks alot!

---

### Post by pilcheck on 2009-09-21
Thanks for the tip!

I'm giving Ubuntu Studio 9.04 a run and this fixed my issue.

The network manager wasn't installed (sudo apt-get network-manager)
then after that, the NM stated that the "device is not managed"

Followed the tip and I'm up and running!

---

### Post by intuited on 2009-12-19
At the risk of being accused of looking for the root cause of the problem..... any idea what would cause this?  Why would the setting have been changed to unmanaged in the first place?  Is this likely to happen again?
I guess I'm looking for a more specific reason than "because of updates".  In particular, maybe this is an issue that package maintainers should be made aware of, since it does impact usability.

---

### Post by peepingtom on 2009-12-20
It's an issue because people make modifications to /etc/network/interfaces . By default, NetworkManager will not manage any interfaces that are specified here because they're likely to be part of a way more complicated setup that nm would break.

---

### Post by satya_461 on 2010-07-06
worked for me too.. I had this problem on ubuntu 10.04 after some update..

Thank you very much..

---

### Post by ufu1 on 2010-07-06
> **peepingtom said:**
> It's an issue because people make modifications to /etc/network/interfaces . By default, NetworkManager will not manage any interfaces that are specified here because they're likely to be part of a way more complicated setup that nm would break.

people? i didn't make any modifications in /etc/network/interfaces. i haven't been doing any updates to try stop from happening.. not the safest way to go but internet was down so i made do. almost feel like i can't touch anything and it'll break because it does !! :S

good to have a fix though. thank you

---

### Post by Olangu on 2010-07-17
You would be better off if you comment out the interface in /etc/network/interfaces 

This change is very welcome for everyone who like to have more control of their interface by using the old way (/etc/network/interfaces). Now network-manager wont mess with settings there.

---

### Post by autonomouse on 2010-08-10
Similar issue on my netbook running Kubuntu netbook edition 10.04. I found that I also had to do the following before the killall step:

```
sudo vim /var/lib/NetworkManager/NetworkManager.state
```

(replacing vim for nano, vi, or whatever if you want), then change: 

```
NetworkingEnabled=false
```

to:
```
NetworkingEnabled=true
```

Only then did it work. 

(Source: [http://ubuntuaddict.com/kubuntu-how-to-fix-network-manager-disabled-ubuntu-10-04-lucid/](http://ubuntuaddict.com/kubuntu-how-to-fix-network-manager-disabled-ubuntu-10-04-lucid/) )

---

### Post by bornbyforce on 2010-08-24
First thanks to the people who provided the answer here.

The answer is up there in my case. I just want to clarify a few things for people who have the problem as I had it.
OK first let me add that I had a bad experience upgrading to Lucid with WPA and I am now back with Jaunty. I may have missed out something or it might be bugs introduced with the recent mass changes in gnome. Either way the following happened on a ipw2200 (Intel Pro Wireless internal wireless card) on a Sony Vaio Laptop with Jaunty.
The card was working out of the box with any of the Ubuntu installations that I have tried including Jaunty and Lucid.
I had a problem with the switch of my wireless (a hardware problem).
First solution was of course buying an external wireless card. Having that working was a bit of a hassle but you may search my posts in other threads for details. At the end of the day it was working until I got my replacement board and installed and started the machine.
With the external (USB) wireless inside and switch on, it was working fine using the external card. And interestingly turning laptop's switch off was actually turning off the external card. Both with the external card connected or disconnected and both with switch on or off, the Internal card was UNMANAGED. I tried the tests in various ubuntu help resources and I was even able to scan the neighborhood for wireless networks with the internal card in command line which confirmed there was not hardware or driver problem.
The solution was of course what you see in this thread HOWEVER...
I tried it several times before getting it right. Things have to happen exactly in the right order.
lets assume starting state is connected to Internet and reading this post with your external card.
Turn the wireless switch off.
Take external card  out of USB.
Turn the wireless switch back on.
Edit conf file (not necessarily at this step but make most of sense)
kill the processes
I believe you are now connected back again!

Hope this helps.

---

### Post by gatman3 on 2010-10-01
Let me just add that this also happened to me with Kubuntu 10.04 after my machine was accidentally powered off while in a sleep (suspend-to-RAM) state.

Restoring my networking required the edits to both the /etc/NetworkManager/nm-system-settings.conf file and the /var/lib/NetworkManager/NetworkManager.state file as detailed in earlier posts to this thread.

I just wanted to point out that failed recovery from suspend-to-RAM (and presumably suspend-to-disk) are also mechanisms that can trigger this networking problem.

---

