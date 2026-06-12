---
title: "Wireless on minimal install"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Oxwivi on 2010-11-16
I want to connect to my wireless AP with WPA authentication. I read some guides, but they required modifying some file with text editors, which I can't do on a minimal install. Is there anyway to connect by directly mentioning the SSID and paraphrase?

---

### Post by chili555 on 2010-11-16
I am not aware of any method to connect to a WPA network only with terminal commands. Are you able to write to files using *echo*? For example:```
sudo su
echo "auto wlan0" >> /etc/network/interfaces
echo "iface wlan0 inet dhcp" >> /etc/network/interfaces
echo "wpa-essid you_router" >> /etc/network/interfaces
echo "wpa-psk your_passwd" >> /etc/network/interfaces
exit
```The symbols >> mean to append, not over-write.

Next try to connect:```
sudo dhclient wlan0
```If it connects, the 'auto' declaration will start it on boot automatically.

---

### Post by Oxwivi on 2010-11-18
Echo command works, so using those commands will let me connect to my network?

---

### Post by chili555 on 2010-11-18
It certainly should, substituting your details of course. You can check your work afterwards with the command *cat*; for example:```
cat /etc/network/interfaces
```If you have made a mistake, you will have to write the file over from scratch. The first line will have to over-write the file:```
sudo su 
echo "auto lo" > /etc/network/interfaces
etc., etc.
```Here we used > for overwrite instaed of >> for append.

I don't know how minimal your install is, but I'd install vim as soon as possible. It's a command line text editor that, despite its hard-core reputation, is easy to use.

Post back if you get stuck.

---

### Post by Oxwivi on 2010-11-18
Thanks, but the problem is I got two desktops with one wifi adapter. I'll try it when I can access someone else's system.

---

### Post by chili555 on 2010-11-18
> I got two desktops with one wifi adapterIt would have been very nice to know these details right from the start. Even now, you have provided precious little information, such as which is the minimal install, the host or the guest? Are to trying to make the minimal install a simple router?

Good luck to you.

---

### Post by Oxwivi on 2010-11-18
You misunderstand, I am just a simple user who thinks all the softwares packaged into a regular Ubuntu install is akin to Window's bloat with all the similar unused programs.

Setting up a router on command line is not worth the trouble, though I'm not familiar with the method to do so.

Anyway, the bottom line is, I just want internet access to a minimal Ubuntu install so I can install the desktop environment and other necessary softwares.

Speaking of which, on one of my attempt (where I relayed internet from my second desktop with wire) everything installed properly, including the network manager except that the icon won't show. I can't connect to wireless like that.

---

### Post by chili555 on 2010-11-18
> thinks all the softwares packaged into a regular Ubuntu install is akin to Window's bloat with all the similar unused programs.I agree, however Ubuntu doesn't allow you to check off the items you want and skip the ones you don't like Fedora did many years ago. The standard install is fine for 90% of all users. A lot of others, including me, simply remove things gradually. I also understand that downloading a 600 Mb CD where 300 Mb is not needed, particularly on a slow connection, is troublesome.

I am certain I did misunderstand. When I read a reply that says, "Yes, but my problem is..." I feel like I am being given new information which is a reason my suggestion won't work. I dislike trying to solve problems with half the information.

Are you sure your wireless card is working? If so, I suggest you proceed as outlined and post back if it doesn't work as expected.> everything installed properly, including the network manager except that the icon won't show. I can't connect to wireless like that.Didn't you try to just add the applet back to the panel? If so, what went wrong?

---

### Post by Oxwivi on 2010-11-19
Well, the applet is supposed to appear in the notification area which was present, but not a single icon. I had installed network-manager-gnome at the command line, and thinking it didn't load at startup, I ran nm-applet at the Terminal which responded saying it was already running.

Does the command line solution allow nm-applet to connect automatically to my network?

---

### Post by chili555 on 2010-11-19
> Does the command line solution allow nm-applet to connect automatically to my network?The command line solution I suggested above will connect automatically on boot with no human intervention.

---

### Post by Oxwivi on 2010-11-19
No need for nm-applet? Then I shall forgo installation of network manager in it's entirety. Oh, and I presume there's the need of wpasupplicant package?

---

### Post by chili555 on 2010-11-19
If you expect to connect to WPA or WPA2 networks, then yes.

---

### Post by Oxwivi on 2010-11-19
Okay, one last thing, how do I  share the internet through my ethernet card with command line?

I am truly grateful for your help. I learned many things. :D

---

### Post by chili555 on 2010-11-19
Connection sharing is a bit above my level of expertise, but you might check here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by Oxwivi on 2010-11-19
All right, will see what I can do about it, thanks for everything! I'll tag this thread solved if I am successful when I attempt to connect to the network on command line.

Cheers!

---

### Post by chili555 on 2010-11-19
Are you certain the wireless card is working correctly?```
iwconfig
```

---

### Post by Oxwivi on 2010-11-20
Yes, I am using it right now on the Live CD. Why do you ask?

---

### Post by chili555 on 2010-11-20
I asked because connecting by any method, whether manual or GUI, such as Network Manager, will only be possible if the wireless interface is working correctly. It appears yours is.

I suggest you go for it! I will be interested to hear your progress.

---

### Post by Oxwivi on 2010-11-20
Okay, I tried it on the install I mentioned, and it worked perfectly. But only after a reboot. And with the experiment of removing wpasupplicant, I found it was indeed required.

Anyway, I don't like to reboot on command line, so I will just connect the adapter to my other system and get internet with eth0. By the way, this is the primary Pentium IV system, and the other system is Pentium III rubbish, with a HDD so old, it's bigger than the current ones and only 3 GB. Won't run Ubuntu for some reason not even the Live CD.

But I really wish I could get the nm-applet working properly in the primary system. How do I do VPN with command?

---

### Post by chili555 on 2010-11-20
I'm glad it worked. Obviously, you did a good job with the commands.

VPN is beyond my area of expertise, I suggest you start a new thread specifically mentioning VPN in the title.

Are you able to ssh into the machine where NM isn't working?

---

### Post by Oxwivi on 2010-11-20
SSH has never been attempted by me. Don't have two Linux systems to use it with, and I've no use trying to connect with Windows systems. FYI, the VPN is for anonymisation purposes.

---

### Post by Oxwivi on 2010-11-20
I don't have to Linux systems to try SSHing with, and no use trying to attempt it with Windows. FYI, the VPN in question is for anonymisation purposes.

---

### Post by chili555 on 2010-11-20
I guess I'm really confused. Are you setting up wireless on a minimal install with command line only or are you setting up wireless on a system running a desktop? If a desktop, I wonder why you were not able to edit files with gedit. See Applications > Accessories > Text Editor. You can start it with root privileges with:```
sudo gedit /some/file
```ssh is available in Windows with putty.

[http://www.putty.org/](http://www.putty.org/)

Do you really need anonymity from one computer you own on your network to another computer you own on your network? Or am I confused again?

---

### Post by Oxwivi on 2010-11-20
What are you confused about? It's a desktop yes, but did you forget the minimal install?

Like I said, I don't need to do SSH with Windows.

Do you not know of VPN that anonymises your connections?

---

### Post by chili555 on 2010-11-20
Why would you do a desktop minimal install without any text editor; not even vi?> What are you confused about?> Do you really need anonymity from one computer you own on your network to another computer you own on your network? I'm tired of all this. I answered your original post and it works.

Good-bye.

---

### Post by Oxwivi on 2010-11-20
Please ignore the scream: "VPN FOR ANONYMITY ONLINE!"

---

