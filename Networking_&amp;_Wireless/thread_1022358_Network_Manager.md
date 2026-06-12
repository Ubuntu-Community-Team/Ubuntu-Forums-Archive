---
title: "Network Manager"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by Maintech on 2008-12-26
I have upgraded an 8.04 to 8.10 and have found the network manager to be completely different. The internet connection works but the manager doesn't see the connection. I have tried putting in all the details in the manager but I still have the yellow triangle. I was told there is a fix for this. I tried goggling for the answer but have been unable to find it. Can anyone point me to the correct url that explains how to make it work correctly. My setup requires a static (manual) connection. I wish I could just turn the manager off and use the 'old' way but I will do whatever is necessary.

Thank you.

---

### Post by ercferret18 on 2008-12-26
just right click on the network applet and click edit connections, then click add.

---

### Post by Maintech on 2008-12-26
> **ercferret18 said:**
> just right click on the network applet and click edit connections, then click add.
I did this as stated in my original post.

---

### Post by Maintech on 2008-12-26
Come on. I know someone out there has the answer. I can't get NetworkManager to see my connection. The internet connection works but the manager won't let me set it up to monitor my existing connection. If I could run the applet in a sudo command prompt I think it would work. I think the permissions are set wrong on it.It doesn't even ask for a password to change it's settings and I know that isn't right. I put in all the static ip addresses just fine and then close it. No popup for admin rights. Then when I open it back up all the info I just put in is gone. Someone give me a hint or a url to some information. I have googled for hours and found nothing, looked at all the docs/manpages/and help FAQ's, been on an irc forum, and I'm about out of patience and resources.

---

### Post by AlexBellisBrown on 2008-12-26
Type iwconfig wlan1 in the terminal and post what it outputs please. :) Lets seeif we can get to the bottom of this.

---

### Post by Maintech on 2008-12-26
> **AlexBellisBrown said:**
> Type iwconfig wlan1 in the terminal and post what it outputs please. :) Lets seeif we can get to the bottom of this.
No such device. However, I know it is eth1 and is up and running. I can do ifconf and get all the information.

---

### Post by AlexBellisBrown on 2008-12-26
Ok... well lets just try iwconfig in terminal, forget the wlan1

---

### Post by Maintech on 2008-12-26
> **AlexBellisBrown said:**
> Ok... well lets just try iwconfig in terminal, forget the wlan1
lo        no wireless extensions.

eth1      no wireless extensions.

This isn't a wireless connection. This is a static wired connection. Like I say, it works. I am using the computer now. I just can't get the NetworkManager to "see" my eth1 connection because it won't let me be admin to change the settings.

---

### Post by Maintech on 2008-12-26
> **AlexBellisBrown said:**
> Ok... well lets just try iwconfig in terminal, forget the wlan1
lo        no wireless extensions.

eth1      no wireless extensions.

This isn't a wireless connection. This is a static wired connection. Like I say, it works. I am using the computer now. I just can't get the NetworkManager to "see" my eth1 connection because it won't let me be admin to change the settings.

---

### Post by AlexBellisBrown on 2008-12-26
Ahhhhh right... sorry, my mistake, im in wireless mode tonight... its been a long day. Could you do ifconfig for me this time? :) Hope we get somewhere with this before i go to bed... its 2:18am here!

---

### Post by Maintech on 2008-12-26
> **AlexBellisBrown said:**
> Ahhhhh right... sorry, my mistake, im in wireless mode tonight... its been a long day. Could you do ifconfig for me this time? :) Hope we get somewhere with this before i go to bed... its 2:18am here!
eth1      Link encap:Ethernet  HWaddr 00:04:5a:7a:3f:33  
          inet addr:10.10.10.10  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::204:5aff:fe7a:3f33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2223324 (2.2 MB)  TX bytes:467791 (467.7 KB)
          Interrupt:18 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1008 (1.0 KB)  TX bytes:1008 (1.0 KB)

It works fine. As stated above, I just need to get the NetworkManager to recognize it. It is the applet that sits in the top task bar. I have tried to find it on the hard drive so I could run it sudo from command line and I think that would fix it but so far ... no luck.

---

### Post by AlexBellisBrown on 2008-12-26
Give this a try 

sudo ifconfig eth0 192.168.1.11 up

Replace the ip address with your own (if you know it)

---

### Post by AlexBellisBrown on 2008-12-26
If not, we can try to open it up on another alias, by doing 

sudo /sbin/ifconfig eth0:0 192.168.1.11 up

then restart the network

sudo /etc/init.d/networking restart

---

### Post by Maintech on 2008-12-26
> **AlexBellisBrown said:**
> Give this a try 

sudo ifconfig eth0 192.168.1.11 up

Replace the ip address with your own (if you know it)
eth0: ERROR while getting interface flags: No such device

I have a degree in networking. I set up all the computers in my house. This just seems to be an issue with "NetworkManager" in the 8.10 Ubuntu because I have never run across this issue in the past. The closest thing was in Solaris where I had to copy one file and past it into another to get it to work. Like I say, I am posting this from the computer I am trying to "fix". And, the fix is just how the applet reads on the task bar. It doesn't "see" Eth1. And I can't make it.

---

### Post by AlexBellisBrown on 2008-12-26
Arrg!!! Ive made an errorin my terminal commands above. I wrote eth0 instead of your eth1. I was trying the commands on my laptop before posting them, try the commands again with the correct eth1 instead of the incorrect eth0. My mistake, sorry.

Im of to get some sleep finally. Look over this link if you want to keep trying: its very helpful.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by bab1 on 2008-12-26
See [http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")

---

### Post by Maintech on 2008-12-26
> **bab1 said:**
> See [http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")
Thank you for the reply. It was very interesting. I have found what I was looking for earlier and tried it but it didn't work. The program is this:
Killall nm-applet
sudo nm-connection-editor
That lets me run the applet in 'root' mode so I have all priveleges. But, I don't. I noticed on one of the other computers that do work properly that the box to enable "system setting" is enabled but will not enable on this computer. Not even when I sudo. So, either the permissions are set incorrectly on some software or there is an issue with recognizing the device for some reason. When I sudo and run the software it does let me input all the ip, subnet, gateway, etc and it does save them. All is set identical to what the system is using that I posted earlier. Yet, it still doesn't see Eth1 and I don't know how to make it see it. I've run out of ideas.

---

### Post by bab1 on 2008-12-27
Maintech,

Unfortunately (or maybe fortunately in the long run), NM is changing and as Paul stated in his article very misunderstood.  

First I must say up front that I do not have any MN controlled interfaces in any of the 6 Ubuntu hosts I am currently running.  In the past I have managed large Solaris and Linux systems in a university setting, so I have lots of diagnostic experience with student induced misconfiguration.

I would be wary of advice that say "try this...".  To me that just means "I don't know the answer but I'm not going to admit it". 

The problem is too specific and many people have complained about  it.  With all the variations that people can set up it is hard to give specific advice.  

Look in the /etc/NetworkManager directory.  There you will find the conf file that controls the NM applet.  There is a setting for ignoring specific interfaces.  This would allow the user to manually configure the interface and allow NM to configure the other interfaces.  Remember, NM was first introduced to manage laptop wireless.  Most laptops have both a wireless and wired interface.  See post #14 of [http://ubuntuforums.org/showthread.php?t=1012963&page=2]("http://ubuntuforums.org/showthread.php?t=1012963&page=2")


I'll bet that the interface you are concerned with is configured to be ignored or is partially configured.

Edit:  You might want to peruse the NM  Mailing List Archives at: [http://mail.gnome.org/archives/networkmanager-list/]("http://mail.gnome.org/archives/networkmanager-list/")

---

### Post by ambar_N on 2008-12-27
Hi.. there...
I was a newbie in this world, n I have same problem with u a couple weeks ago n already solved.

This problem is happen due to there is a bug in the Gnome Network Manager, and what was I've done to solve this problem is :

Remove Gnome Network Manager :
```

update-rc.d -f NetworkManager remove

```

Then configure network interface manually on /etc/network/interfaces

```
#nano /etc/network/interfaces
```

That should be like this :
> 

auto lo eth0
iface lo inet loopback
iface eth0 inet static
address ___IP address___
netmask ___netmask______
gateway ___gateway______



Then if u using domain resolver, edit ur /etc/resolv.conf
```
#nano /etc/resolv.conf
```
add ur domain IP there...
> 
nameserver __ur server IP___


Restart ur networking service 
```

#/etc/init.d/networking restart

```

Or better u reboot ur system.

I'm success solve the problem using this step, hope u too...
Sorry for my English..... good luck....

---

### Post by iponeverything on 2008-12-27
Network Manager will not manage anything that is in /etc/network/interfaces

If you want to use NM to manage eth1, remove all traces of it from your /etc/network/interfaces file.

---

### Post by zika on 2008-12-27
@ Maintech:[B]

no[/B], You don't need to remove NM. Just get him out of the loop.

as it is already mentioned, (post #14 is mine, among many other posts on this subject) there are two ways to do that.

First (preferable) is to use /etc/network/interfaces i /etc/resolve.conf files. once You get information in those files NM will stop (usually) taking care about those interfaces. if You get good connection out of that You might forget about NM. uncheck it in System->Sessions list and enyou. also, You might make change that's mentioned in #14.

Second (I've done it many times with success) is to be very patient and persistent in making over and over all the changes required (don't forget System and auto) in NM windows until it remebers them and then reboot.

if You have wired connection and no wireless You do not need NM.

do not make any radical changes like removing it because You will regret them when upgrade or dist-upgrade comes.

---

### Post by AlexBellisBrown on 2008-12-27
In this situation would Wicd be any better than NM?

---

### Post by Maintech on 2008-12-27
> You might forget about NM. uncheck it in System->Sessions list and enyou

I turned it off in sessions because it isn't needed. I wasn't aware you could do this. The issue (I think) was originally caused because I "upgraded" from 8.04 to 8.10 instead of doing a 'fresh install'. I have another computer that had a fresh install of 8.10 when it was first released and someone told me a quick and easy way to get networkmanager working correctly. I should have written it down. In my situation it isn't needed though.

However, I sure hope the coders of NetworkManager determine what they have done wrong so that in the following releases all (wired, wireless, static, and dhcp) work correctly. It is a nice app when it works.

Thank you all for your help and patience.:)

---

