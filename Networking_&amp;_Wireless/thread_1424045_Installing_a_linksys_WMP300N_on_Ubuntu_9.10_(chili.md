---
title: "Installing a linksys WMP300N on Ubuntu 9.10 (chili555)"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by DogoDave on 2010-03-07
Hi Chili555, i am great_canadian from the irc channel

---

### Post by chili555 on 2010-03-07
Please do:```
sudo rmmod -f b43 ssb
sudo modprobe wl
sudo lshw -C network
```The first two may produce no output, but please post the *lshw*. Thanks.

---

### Post by DogoDave on 2010-03-07
dave@dave-desktop:/$ sudo rmmod -f b43 ssb
ERROR: Removing 'b43': No such file or directory
ERROR: Removing 'ssb': No such file or directory
dave@dave-desktop:/$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
dave@dave-desktop:/$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:2f:2a:b2:39
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=1GB/s
       resources: irq:18 memory:fe9e0000-fe9fffff ioport:cf80(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:03:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       configuration: latency=64
       resources: memory:feaf8000-feafbfff

---

### Post by chili555 on 2010-03-07
> All config files need .conf: /etc/modprobe.d/ndiswrapperDid you already try ndiswrapper? What was your experience? What does this tell us?```
ndiswrapper -l
```Also, please edit the title of the thread to take my name out. I really don't want people calling me out for help, except you, of course.

I'm still trying to figure out why *wl* doesn't grab this card.

---

### Post by DogoDave on 2010-03-07
I had previously tried these intructions that i kept finding from doing searches. The ones from anewguy  [http://ubuntuforums.org/showthread.php?t=539208](http://ubuntuforums.org/showthread.php?t=539208)

dave@dave-desktop:/$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4329) present (alternate driver: ssb)

---

### Post by chili555 on 2010-03-07
Please do:```
sudo modprobe ndiswrapper
iwconfig
```Do you have a wireless interfcase, wlan0, perhaps?

Also, please let me see:```
cat /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist
```

---

### Post by DogoDave on 2010-03-07
dave@dave-desktop:/$ sudo modprobe ndiswrapper
[sudo] password for dave: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
dave@dave-desktop:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dave@dave-desktop:/$ cat /etc/modprobe.d/ndiswrapper
alias pci:v000014E4d00004329sv00000060sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004329sv*sd*bc*sc*i* ndiswrapper
dave@dave-desktop:/$ cat /etc/modprobe.d/blacklist
# broadcom default no firmware, using ndiswrapper instead
blacklist bcm43xx


dave@dave-desktop:/$ 


Also I can't seem to get the topic to change.....i thought it would be simple and was my plan once you had found the thread.....do i need to make a request to a mod to get the original topic modified?

---

### Post by chili555 on 2010-03-07
If this works, I will fall off my chair:> alias pci:v000014E4d00004329sv00000060sd00001737bc*sc*i* ndiswrapper
alias pci:v000014E4d00004329sv*sd*bc*sc*i* ndiswrapperI believe the first line is a typo. We shall find out. Please do:```
ls /etc/modprobe.d
``` Do you have both a blacklist and a blacklist.conf?```

sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
sudo gedit /etc/modules
```If it is not there already, add:```
ndiswrapper
```Proofread, save and close gedit. Post back and let me know.

---

### Post by DogoDave on 2010-03-07
dave@dave-desktop:/$ ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     dkms.conf
blacklist               blacklist-framebuffer.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist-modem.conf        ndiswrapper.conf
blacklist-bcm43.conf    blacklist-oss.conf
blacklist.conf          blacklist-watchdog.conf
dave@dave-desktop:/$ sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
mv: cannot stat `/etc/modprobe.d/ndiswrapper': No such file or directory
dave@dave-desktop:/$ sudo gedit /etc/modules
dave@dave-desktop:/$ 


This was the gedit file i added ndiswrapper at the bottom as it was not there.... I then clicked save and closed it

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
ndiswrapper


I think you are probably aware and perhaps had me remove the driver at some point but I admit i am lost and just following instructions at this point, but you know when you go to System>Administration>Hardware Drivers...the only only that appears now is that broadcom STA wireless driver....but it doesn't seem to have a matching chipset in the list it gives in the description .....it now list this one as the active driver and the other is just no longer there

---

### Post by chili555 on 2010-03-07
Wow! You have a lot going on there:> blacklist  blacklist-bcm43.conf blacklist.confLet's see:```
cat /etc/modprobe.d/blacklist-bcm43.conf
```We will do some more housecleaning after we see that file.

---

### Post by DogoDave on 2010-03-07
Lol yeah thats the problem when you don't understand what a command is doing you can't even guess when you are doing things to help or hinder.

This was the result of that command

dave@dave-desktop:/$ cat /etc/modprobe.d/blacklist-bcm43.conf
# Warning: This file is autogenerated by bcmwl-kernel-source. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
dave@dave-desktop:/$ 

Also i edited my above post with more info for you that you may already be aware of or are expecting but thought I would let you know whats happening

---

### Post by chili555 on 2010-03-07
Please do:```
sudo rm /etc/modprobe.d/blacklist
```Reboot and tell me what's happening with the wireless.

---

### Post by DogoDave on 2010-03-07
Hey you got something working now just not sure how much

If I go to System>Adminisration>Network it now show the Wireless Connnection, Wired Connection, and Point to Point connection icons.... in the past the wireless one was never there.

Also now when I go to System> Administration>Window Wireless Drivers it opens and shows me an icon and says bcmwl5 and it say hardware present: yes
....in the past when i tried opening that it always gave a warning at the beginning that it could not determine it hardware was present.

Lastly the System>Administration>Hardware Drivers ....is still reporting the same broadcom STA driver as currently being active but not in use



I am not sure if that mean problem is solved and I just need to learn how to enable and connect to my wireless or if we have more to do yet.

---

### Post by chili555 on 2010-03-07
Do you see the Network Manager icon at the top right? After you disconnect the ethernet cable, click the icon, see your network and connect. Post back to report your success!

---

### Post by DogoDave on 2010-03-07
No can't get it to connect.

up in the top toolbar or whatever you call it there is a black square void which I am assuming is normally where the network connection status is

If I go to System>Adminitration>Network....i have to click wireless and go to properties then if I uncheck roaming mode and click on the drop arrow for the network name it does see my network and I have tried both setting it to WPA2 and WPA with my network key but it just says 
NETWORK disconnected you are now offline

---

### Post by chili555 on 2010-03-07
> up in the top toolbar or whatever you call it there is a black square voidSee if you can right click it and add a notification area. Network Manager should be one of the things that appears. If not, try to add it in the notification area. NM will look like two computer monitors with an **[COLOR="Red"]X[/COLOR]** in it.

---

### Post by DogoDave on 2010-03-07
No network manager in the list that comes up, just network monitor that looks like two extension cords plugged together....also I accidentally hit something that removed my display setting button and 1 other that I don't know what it was, still have the date,time and mail ones though

---

### Post by chili555 on 2010-03-07
You did this first, right?

---

### Post by DogoDave on 2010-03-07
Ah yes that restored the icons that went missing

---

### Post by chili555 on 2010-03-07
> **DogoDave said:**
> Ah yes that restored the icons that went missingNow, I suggest you detach the wire and try to connect.

---

### Post by DogoDave on 2010-03-07
OK so got the notification area restored and then got the options to connect to wired or wireless connections.....

I am now able to connect to my wireless network only if I disable the WPA security.....but if it is enabled then the network monitor icon just spins forever and then says not connected....is there a limit to the level of encryption that Ubuntu wireless drivers can handle?

I am currently submitting this post over my wireless network

---

### Post by chili555 on 2010-03-07
> is there a limit to the level of encryption that Ubuntu wireless drivers can handle?It depends on the driver and the card; however, you are using Windows drivers within ndiswrapper. You can, with some drivers, see what your card and driver can do with:```
sudo iwlist wlan0 auth
```Mine, as an example, says:> wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMPAre you sure your encryption method and password all match, in the router and NM? PSK vs. TKIP vs. whatever?

NM is twitchy and a bit slow, but it should connect in a minute or so.

I am very glad that the wireless is at least working!

---

### Post by DogoDave on 2010-03-07
Yes that is finally some good news.....thanks for sticking with it for so long ....much appreciated

Okay so i get the following

dave@dave-desktop:/$ sudo iwlist wlan0 auth
[sudo] password for dave: 
wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		WPA
          Current Key management :
		PSK
          Current Pairwise cipher :
		TKIP
          Current Pairwise cipher :
		TKIP
          Current Authentication algorithm :
		open

Looks like I should be able handle wpa2 on TKIP but perhaps not AES
but as soon as I put encryption back on my network I can't connect to it even though I do get a prompt asking for my network key.

The prompt recognizes that it is WPA or WPA2 i have turned it down to just WPA thinking that it couldn't handle it but it just keeps trying to connect and asks me for the password/network key over and over

---

### Post by chili555 on 2010-03-07
When you right-click NM and edit connections-wireless, is NM trying to use the ndiswrapper driver for WPA or wext? Whichever it is, please try the other.

---

### Post by DogoDave on 2010-03-07
I don't know I don't see anything that says ndiswrapper....only time I have seen that is when typed in terminal....other then that I haven't seen it again

---

### Post by DogoDave on 2010-03-07
I rebooted to see if perhaps it just needed to refresh itself like so often happens with windows when playing with network settings....

anyway now up in the NM icon it just says Wireless Networks and then grayed out it says "device not managed" and it won't even show anything else but it is showing enabled when you right click the NM icon

---

### Post by chili555 on 2010-03-07
Please post:```
lsmod | grep ndis
```Are you looking in NM for wireless when the ethernet cable is attached?

I will change to my one computer with NM and try to get more information.

---

### Post by chili555 on 2010-03-07
Sorry, NM does not allow you to specify the WPA driver, Wicd, does. I am continuing to google. I hope this behavior is not a quirk with Broadcom cards that use ndiswrapper.

While we are at it, please do:```
sudo gedit /etc/modprobe.d/ndiswrapper.conf
```Change it to:```
alias pci:v000014E4d00004329sv*sd*bc*sc*i* ndiswrapper
```In other words, remove the first, longer line. Proofread, save and close gedit.

I am not confident it will make a difference in connecting, but, as I said, we shall see.

---

### Post by chili555 on 2010-03-07
Please post:```
ls /etc/ndiswrapper
```If one of the folders inside is bcmw15, please post:```
ls /etc/ndiswrapper/bcmw15
```Thanks.

---

### Post by chili555 on 2010-03-07
I would also like to see, while the router is set for WPA, the result after you try and fail to connect:```
sudo cat /var/log/syslog | grep -e wlan -e ndis
```Thanks.

We will either conquer this or kill your keyboard trying!

---

### Post by DogoDave on 2010-03-07
OKay 

First command 

dave@dave-desktop:/$ lsmod | grep ndis
ndiswrapper           185532  0 


Second Command

sudo gedit /etc/modprobe.d/ndiswrapper.conf

performed and file edited as specified first line removed and other entry matches what you posted saved and exited.

Third Command(s)

dave@dave-desktop:/$ ls /etc/ndiswrapper
bcmwl5
dave@dave-desktop:/$ ls /etc/ndiswrapper/bcmw15
ls: cannot access /etc/ndiswrapper/bcmw15: No such file or directory

Forth Command 

sudo cat /var/log/syslog | grep -e wlan -e ndis

Are you sure you want me to post this its about 50+ lines or so that look like this 
port 67 interval 4
Mar  7 16:26:47 dave-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Mar  7 16:26:55 dave-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Mar  7 16:27:08 dave-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11


Also I couldn't do it after a connect and fail because the wireless functionality has just disappeared ....now when I click on the NM icon under where it says Wireless Networks it just has grayed out text saying "device not managed" and it won't let me do anything with it.  Also System>Adminitration>Network doesn't matter if I select the wireless network set it to roam enable or specify the network setting, or if the check box is checked or not makes no difference at this time.  NM just continues to say that the device is not managed and I can no longer get any sort of wireless activity to occur.

To answer your question, Yes I am and have done both,....disconnected the ethernet cable and tried as well as just disconnected via the option disconnect in NM and tried connecting wireless....In both instances it reacted the same way connecting briefly and then disconnecting and unable to remain connected....when the ethernet was still in it would then revert back to the Auto eth0.,....that was until i reboot and lost wireless all together again.


Had to leave for a birthday party ...will keep checking this thread and plugging away ....but please if it is driving me nuts and its my problem, it can't be any fun for you, so don't kill yourself on this.  Thanks again

---

### Post by -TJ on 2010-03-08
Hello Everyone,
I have the same problem working the WMP300N my Ubuntu 9.10 Desktop 64Bit. Is it alright if I may also join this discussion? I also need help... Or we could start a new thread here: [HTML]http://ubuntuforums.org/showthread.php?t=1424336[/HTML]

---

### Post by YMS_1975 on 2010-03-20
Didn't feel the need to start a new thread since this one was here. I've done a lshw -c network, and here are the results.

I do NOT have a wired connection, and would like to get this up and running.
The funny thing is, I had Karmic Koala up and running on this pc before. I had uninstalled it, but would like it back up and running as it was before.

Why won't it see my network card?

---

### Post by chili555 on 2010-03-20
> **YMS_1975 said:**
> Didn't feel the need to start a new thread since this one was here. I've done a lshw -c network, and here are the results.

I do NOT have a wired connection, and would like to get this up and running.
The funny thing is, I had Karmic Koala up and running on this pc before. I had uninstalled it, but would like it back up and running as it was before.

Why won't it see my network card?Does it need firmware? Please do:```
dmesg | grep b43
```Does it complain about not finding the needed firmware? Can we get it and transfer it with a USB key?

---

### Post by YMS_1975 on 2010-03-21
> **chili555 said:**
> Does it need firmware? Please do:```
dmesg | grep b43
```Does it complain about not finding the needed firmware? Can we get it and transfer it with a USB key?

Chili555 --- Old friend, how are you? Not sure if you remember or not, but you helped save me before (when I had the exact same problem with my laptop). You're definitely a big help to both me & the rest of the Ubuntu community.  :D

As for the message that code generated, see the attachment to this post.
Do I have a USB key? Not quite. I've got my laptop next to the boys PC (the one that's having this problem) and I type in what you tell me to, do a screen capture, burn it to CD, put the CD in my laptop and upload it via my laptop.

It's tedious, but without a wired connection, it's all I've got.

---

### Post by chili555 on 2010-03-21
> **YMS_1975 said:**
> Chili555 --- Old friend, how are you? Not sure if you remember or not, but you helped save me before (when I had the exact same problem with my laptop). You're definitely a big help.  :D

As for the message that code generated, see the attachment to this post.
Do I have a USB key? Not quite. I've got my laptop next to the boys PC (the one that's having this problem) and I type in what you tell me to, do a screen capture, burn it to CD, put the CD in my laptop and upload it via my laptop.

It's tedious, but without a wired connection, it's all I've got.Attachment not included.

You don't need a screen capture. You can do:```
command > command.txt
```Burn the text file to CD. You can also copy and paste from the terminal to a text document. You could, for example, do:```
iwconfig
lsmod
uname -r
```Then copy each individually to one big text document. If it's very long, post it as an attachment or use: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)  Great to see you again, my friend!

---

### Post by YMS_1975 on 2010-03-21
> **chili555 said:**
> Attachment not included.

You don't need a screen capture. You can do:```
command > command.txt
```Burn the text file to CD. You can also copy and paste from the terminal to a text document. You could, for example, do:```
iwconfig
lsmod
uname -r
```Then copy each individually to one big text document. If it's very long, post it as an attachment or use: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)  Great to see you again, my friend!

Wouldn't you know it? As soon as I posted the message, I realized that I did not attach the file, then I had a media error. Took a while to  find another blank CD.

Anyways, it's posted up now.

---

### Post by chili555 on 2010-03-21
> I've got my laptop next to the boys PC (the one that's having this problem)Do you have the ability to connect his computer to the ethernet connection and do:```
sudo apt-get install bcmwl-kernel-source
```You might have to do:```
sudo rmmod -f b43
sudo modprobe wl
```

---

### Post by YMS_1975 on 2010-03-21
> **chili555 said:**
> Do you have the ability to connect his computer to the ethernet connection and do:```
sudo apt-get install bcmwl-kernel-source
```You might have to do:```
sudo rmmod -f b43
sudo modprobe wl
```

that's the problem, I can't connect it to the ethernet cable. it's all the way downstairs.

I only have my laptop next to this PC. My laptop has wireless access. Is there anything we can do to fix this?

---

### Post by chili555 on 2010-03-21
Burn to a CD from here: [http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)

Be sure to get the i386 or x86_64 version matching his machine. Be sure to get all the dependencies, dkms, libc6-dev and linux-libc-dev. Generic headers will do no good. Run:```
uname -r
```on his machine and grab the linux headers to match. For example, linux-headers-2.6.31-20-generic. 

Install with:```
sudo dpkg -i *.deb
```If you get stuck .... well, you know.

---

### Post by YMS_1975 on 2010-03-21
> **chili555 said:**
> Burn to a CD from here: [http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)

Be sure to get the i386 or x86_64 version matching his machine. Be sure to get all the dependencies, dkms, libc6-dev and linux-libc-dev. Generic headers will do no good. Run:```
uname -r
```on his machine and grab the linux headers to match. For example, linux-headers-2.6.31-20-generic. 

Install with:```
sudo dpkg -i *.deb
```If you get stuck .... well, you know.


Followed everything you said to a tee (or so I believe), and I got this message.

See the attached.

**EDIT :** You can disregard the attachment. I opened up a terminal, typed in "sudo dpkg -i" and then dragged the file next to that, and then it did something. LOL....ummm, I did this indvidually for each file, and yes it seemed to do something. Then I tried going to System > Administration > Hardware Drivers and it now states "Broadcom STA wireless driver" (and that definitely wasn't showing up before)...so it did SOMETHING.

I tried to activate it, then rebooted but nothing happened.  :(

---

### Post by YMS_1975 on 2010-03-21
Here's what shows up now...(which wasn't there before).

---

### Post by chili555 on 2010-03-21
First, drag and drop the files from the CD to your desktop. Next, open the terminal and change to the directory where the files are now located:```
cd Desktop
```Sometimes, when files get written to, and transferred from a CD, they are "read only." Let's not take any chances:```
sudo chmod 777 *.deb
```And now, let's install them in mass:```
sudo dpkg -i *.deb
```Any improvement?

---

### Post by YMS_1975 on 2010-03-21
> **chili555 said:**
> First, drag and drop the files from the CD to your desktop. Next, open the terminal and change to the directory where the files are now located:```
cd Desktop
```Sometimes, when files get written to, and transferred from a CD, they are "read only." Let's not take any chances:```
sudo chmod 777 *.deb
```And now, let's install them in mass:```
sudo dpkg -i *.deb
```Any improvement?

I installed them, although....they seemed to install one by one, instead of all at once. I got an error message when doing it all at once saying : 

[B]dpkg : error processing *.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
*.deb[/B]

But they did install one by one, because the box came up, and I clicked on Install Package for each file.

So I know they installed.

---

### Post by chili555 on 2010-03-21
Now can you activate the STA driver? If not, please try:```
sudo rmmod -f b43
sudo modprobe wl
```That's WL, not W-one. Now does Network Manager give you an option to connect? If this does it, we can blacklist *b43*.

---

### Post by YMS_1975 on 2010-03-21
> **chili555 said:**
> Now can you activate the STA driver? If not, please try:```
sudo rmmod -f b43
sudo modprobe wl
```That's WL, not W-one. Now does Network Manager give you an option to connect? If this does it, we can blacklist *b43*.

Nope.

For the first sudo command I get :

ERROR : Removing 'b43': No such file or directory

And for the second sudo command I get : 

FATAL : Module wl not found.

:confused:

---

### Post by chili555 on 2010-03-21
Let's reboot and refresh our beverages; chocolate milk for the boy, please!

Now, let's see:```
dmesg | grep -e b43 -e wl > dmesg.txt
```Move dmesg.txt to a CD and post it here.

I assume your absence was to buy a CD-RW?!

---

### Post by YMS_1975 on 2010-03-21
> **chili555 said:**
> Let's reboot and refresh our beverages; chocolate milk for the boy, please!

Now, let's see:```
dmesg | grep -e b43 -e wl > dmesg.txt
```Move dmesg.txt to a CD and post it here.

I assume your absence was to buy a CD-RW?!

LOL....not quite. Had to pick up some quick groceries for wifey. She's not too pleased with me at the moment, as I've been on the boys PC trying to figure out how to get this thing to work for two days now.

For some reason, it doesn't wanna upload the .txt file, so I'll just copy and paste it from the CD.

Hmmmm.....for some reason, it's blank.

---

### Post by chili555 on 2010-03-21
Please run the following:```
iwconfig > iwconfig.txt
dmesg > dmesg.txt
lsmod > lsmod.txt
sudo lshw -C network > network.txt
cat iwconfig.txt dmesg.txt lsmod.txt network.txt > test.txt
zip test.zip test.txt
```Attach test.zip to your reply. I am going a bit overboard, because there are only so many blank CDs in the world and your son needs his college fund.

---

### Post by chili555 on 2010-03-23
I will be looking forward to your *test.zip* in order to proceed. I am anxious to get your son into the Ubuntu family!

---

### Post by YMS_1975 on 2010-03-23
> **chili555 said:**
> I will be looking forward to your *test.zip* in order to proceed. I am anxious to get your son into the Ubuntu family!

Ok boss,

Here it is....test.zip!  :)

---

### Post by chili555 on 2010-03-23
It looks like you installed ndiswrapper to try to get it going. What does the command:```
ndiswrapper -l
```say to us? You can jot it down on a postit. They are cheaper than CDs.

---

### Post by YMS_1975 on 2010-03-23
> **chili555 said:**
> It looks like you installed ndiswrapper to try to get it going. What does the command:```
ndiswrapper -l
```say to us? You can jot it down on a postit. They are cheaper than CDs.

If I type in "ndiswrapper -l" it says : 

[B]"The program 'ndiswrapper' is currently not installed. You can install it by typing : sudo apt-get install ndiswrapper-common.
ndiswrapper: command not found"[/B]

---

### Post by chili555 on 2010-03-23
Here is a part of your lsmod:> i2c_viapro              7312  0 
gameport               11368  1 snd_via82xx
[COLOR="Red"]ndiswrapper [/COLOR]          185404  0 
ppdev                   6688  0 
joydev                 10272  0 I wonder how the module loaded if the package is not even installed? Post, from a postit:```
ls /etc/modprobe.d | grep -e black -e ndis
```Thanks.

---

### Post by YMS_1975 on 2010-03-23
> **chili555 said:**
> Here is a part of your lsmod:I wonder how the module loaded if the package is not even installed? Post, from a postit:```
ls /etc/modprobe.d | grep -e black -e ndis
```Thanks.

[B]blacklist-ath_pci.conf
blacklist-bcm43.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf[/B]

[Manually typed out : hope there's no typos]

---

### Post by chili555 on 2010-03-23
Looks good to me! What is the outcome of:```
sudo modprobe wl
```

---

### Post by YMS_1975 on 2010-03-23
> **chili555 said:**
> Looks good to me! What is the outcome of:```
sudo modprobe wl
```

FATAL: Module wl not found.

---

### Post by chili555 on 2010-03-23
Let's search for it:```
sudo updatedb
locate wl.ko
```My result, for comparison, is:> /lib/modules/2.6.31-19-generic/updates/dkms/wl.ko
/lib/modules/2.6.31-20-generic/updates/dkms/[COLOR="Red"]wl.ko[/COLOR]
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/2.6.31-19-generic/i686/module/wl.ko
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/2.6.31-20-generic/i686/module/wl.ko
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/.wl.ko.cmdThe one I highlighted is the one I just modprobed without error.

The .ko extension is not needed in modprobe.

---

### Post by YMS_1975 on 2010-03-23
> **chili555 said:**
> Let's search for it:```
sudo updatedb
locate wl.ko
```My result, for comparison, is:The one I highlighted is the one I just modprobed without error.

The .ko extension is not needed in modprobe.

/etc/laptop-mode/conf.d/wireless-iwl-power.conf 
/home/yousaf/Desktop/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb 
/lib/firmware/iwlwifi-1000-3.ucode 
/lib/firmware/iwlwifi-3945-1.ucode 
/lib/firmware/iwlwifi-3945-2.ucode 
/lib/firmware/iwlwifi-4965-1.ucode 
/lib/firmware/iwlwifi-4965-2.ucode 
/lib/firmware/iwlwifi-5000-1.ucode 
/lib/firmware/iwlwifi-5000-2.ucode 
/lib/firmware/iwlwifi-5150-2.ucode 
/lib/firmware/iwlwifi-6000-4.ucode 
/lib/modules/2.6.31-14-generic/kernel/drivers/gpio/twl4030-gpio.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/input/misc/twl4030-pwrbutton.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/iwlwifi 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/mwl8k.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/rndis_wlan.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/wl12xx 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/wl3501_cs.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/net/wireless/wl12xx/wl12xx.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/rtc/rtc-twl4030.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/wlan-ng 
/lib/modules/2.6.31-14-generic/kernel/drivers/staging/wlan-ng/prism2_usb.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/usb/otg/twl4030-usb.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/uwb/wlp 
/lib/modules/2.6.31-14-generic/kernel/drivers/uwb/i1480/i1480u-wlp 
/lib/modules/2.6.31-14-generic/kernel/drivers/uwb/i1480/i1480u-wlp/i1480u-wlp.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/uwb/wlp/wlp.ko 
/lib/modules/2.6.31-14-generic/kernel/drivers/watchdog/twl4030_wdt.ko 
/lib/modules/2.6.31-14-generic/kernel/net/netfilter/ipvs/ip_vs_wlc.ko 
/lib/modules/2.6.31-14-generic/kernel/sound/soc/codecs/snd-soc-twl4030.ko 
/lib/udev/keymaps/hewlett-packard 
/lib/udev/keymaps/hewlett-packard-2510p_2530p 
/lib/udev/keymaps/hewlett-packard-compaq_elitebook 
/lib/udev/keymaps/hewlett-packard-pavilion 
/lib/udev/keymaps/hewlett-packard-presario-2100 
/lib/udev/keymaps/hewlett-packard-tablet 
/lib/udev/keymaps/hewlett-packard-tx2 
/sbin/iwlist 
/usr/lib/openoffice/basis3.1/program/libchartviewli.so 
/usr/lib/openoffice/basis3.1/program/libfwlli.so 
/usr/lib/openoffice/basis3.1/program/libswli.so 
/usr/lib/openoffice/basis3.1/share/gallery/www-graf/ylwleft.gif 
/usr/lib/perl/5.10.0/B/Showlex.pm 
/usr/lib/purple-2/newline.so 
/usr/lib/pymodules/python2.6/dbus/lowlevel.py 
/usr/lib/pymodules/python2.6/dbus/lowlevel.pyc 
/usr/share/app-install/desktop/kwlan.desktop 
/usr/share/app-install/desktop/twlog.desktop 
/usr/share/app-install/icons/_usr_share_qGo_pics_Bowl.png 
/usr/share/app-install/icons/kwlan.png 
/usr/share/app-install/icons/twlog.png 
/usr/share/aspell/en-common.cwl.gz 
/usr/share/aspell/en-variant_0.cwl.gz 
/usr/share/aspell/en-variant_1.cwl.gz 
/usr/share/aspell/en-variant_2.cwl.gz 
/usr/share/aspell/en_CA-w_accents-only.cwl.gz 
/usr/share/aspell/en_CA-wo_accents-only.cwl.gz 
/usr/share/aspell/en_GB-ise-w_accents-only.cwl.gz 
/usr/share/aspell/en_GB-ise-wo_accents-only.cwl.gz 
/usr/share/aspell/en_GB-ize-w_accents-only.cwl.gz 
/usr/share/aspell/en_GB-ize-wo_accents-only.cwl.gz 
/usr/share/aspell/en_US-w_accents-only.cwl.gz 
/usr/share/aspell/en_US-wo_accents-only.cwl.gz 
/usr/share/doc/bcmwl-kernel-source 
/usr/share/doc/bcmwl-modaliases 
/usr/share/doc/bcmwl-kernel-source/README 
/usr/share/doc/bcmwl-kernel-source/changelog.Debian.gz 
/usr/share/doc/bcmwl-kernel-source/copyright 
/usr/share/doc/bcmwl-modaliases/README 
/usr/share/doc/bcmwl-modaliases/changelog.Debian.gz 
/usr/share/doc/bcmwl-modaliases/copyright 
/usr/share/doc/linux-firmware/licenses/iwlwifi 
/usr/share/doc/linux-firmware/licenses/iwlwifi/LICENSE.iwlwifi-ucode 
/usr/share/doc/wamerican/wamerican.scowl-word-lists-used 
/usr/share/doc/wbritish/wbritish.scowl-word-lists-used 
/usr/share/ghostscript/8.70/lib/gs_wl1_e.ps 
/usr/share/ghostscript/8.70/lib/gs_wl2_e.ps 
/usr/share/ghostscript/8.70/lib/gs_wl5_e.ps 
/usr/share/gnome/help/gnome-access-guide/C/figures/stickywindowlatch.png 
/usr/share/gnome/help/gnome-access-guide/C/figures/stickywindowlock.png 
/usr/share/hal/fdi/information/10freedesktop/10-iwl-rfkill-switch.fdi 
/usr/share/jockey/handlers/broadcom_wl.py 
/usr/share/jockey/handlers/broadcom_wl.pyc 
/usr/share/jockey/modaliases/bcmwl 
/usr/share/laptop-mode-tools/modules/wireless-iwl-power 
/usr/share/man/cs/man8/iwlist.8.gz 
/usr/share/man/fr/man8/iwlist.8.gz 
/usr/share/man/man8/iwlist.8.gz 
/usr/share/pyshared/dbus/lowlevel.py 
/usr/share/sgml/entities/Hewlett-Packard 
/usr/share/sgml/entities/Hewlett-Packard/HPcalc 
/usr/share/sgml/entities/Hewlett-Packard/HPservice 
/usr/share/sgml/entities/Hewlett-Packard/HPsym 
/usr/share/sgml/entities/Hewlett-Packard/HPtexchars 
/usr/share/sgml/entities/Hewlett-Packard/HPtif 
/usr/share/sgml/entities/Hewlett-Packard/catalog 
/usr/src/bcmwl-5.10.91.9+bdcom 
/usr/src/bcmwl-5.10.91.9+bdcom/Makefile 
/usr/src/bcmwl-5.10.91.9+bdcom/dkms.conf 
/usr/src/bcmwl-5.10.91.9+bdcom/lib 
/usr/src/bcmwl-5.10.91.9+bdcom/patches 
/usr/src/bcmwl-5.10.91.9+bdcom/src 
/usr/src/bcmwl-5.10.91.9+bdcom/lib/LICENSE.txt 
/usr/src/bcmwl-5.10.91.9+bdcom/lib/wlc_hybrid.o_shipped_i386 
/usr/src/bcmwl-5.10.91.9+bdcom/patches/0001-MODULE_LICENSE.patch 
/usr/src/bcmwl-5.10.91.9+bdcom/patches/0002-Makefile.patch 
/usr/src/bcmwl-5.10.91.9+bdcom/patches/0003-DEV_WL_IF.patch 
/usr/src/bcmwl-5.10.91.9+bdcom/patches/0004-broadcom-sta-5.10.91.9-linux-2.6.30.patch 
/usr/src/bcmwl-5.10.91.9+bdcom/patches/0005-NET_DEVICE_OPS.patch 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include 
/usr/src/bcmwl-5.10.91.9+bdcom/src/shared 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/bcmdefs.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/bcmendian.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/bcmutils.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/bcmwifi.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/epivers.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/linux_osl.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/linuxver.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/osl.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/pcicfg.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/proto 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/typedefs.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/wlioctl.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/proto/802.11.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/proto/802.1d.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/proto/bcmeth.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/proto/bcmevent.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/proto/ethernet.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/include/proto/wpa.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/shared/linux_osl.c 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys/wl_dbg.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys/wl_export.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys/wl_iw.c 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys/wl_iw.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys/wl_linux.c 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys/wl_linux.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys/wlc_key.h 
/usr/src/bcmwl-5.10.91.9+bdcom/src/wl/sys/wlc_pub.h 
/usr/src/linux-headers-2.6.31-14/arch/blackfin/include/asm/rwlock.h 
/usr/src/linux-headers-2.6.31-14/arch/x86/include/asm/rwlock.h 
/usr/src/linux-headers-2.6.31-14/drivers/net/wireless/iwlwifi 
/usr/src/linux-headers-2.6.31-14/drivers/net/wireless/wl12xx 
/usr/src/linux-headers-2.6.31-14/drivers/net/wireless/iwlwifi/Kconfig 
/usr/src/linux-headers-2.6.31-14/drivers/net/wireless/iwlwifi/Makefile 
/usr/src/linux-headers-2.6.31-14/drivers/net/wireless/wl12xx/Kconfig 
/usr/src/linux-headers-2.6.31-14/drivers/net/wireless/wl12xx/Makefile 
/usr/src/linux-headers-2.6.31-14/drivers/staging/wlan-ng 
/usr/src/linux-headers-2.6.31-14/drivers/staging/wlan-ng/Kconfig 
/usr/src/linux-headers-2.6.31-14/drivers/staging/wlan-ng/Makefile 
/usr/src/linux-headers-2.6.31-14/drivers/uwb/wlp 
/usr/src/linux-headers-2.6.31-14/drivers/uwb/i1480/i1480u-wlp 
/usr/src/linux-headers-2.6.31-14/drivers/uwb/i1480/i1480u-wlp/Makefile 
/usr/src/linux-headers-2.6.31-14/drivers/uwb/wlp/Makefile 
/usr/src/linux-headers-2.6.31-14/include/linux/wlp.h 
/usr/src/linux-headers-2.6.31-14/include/linux/i2c/twl4030.h 
/usr/src/linux-headers-2.6.31-14/include/linux/spi/wl12xx.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwl3945 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwl3945.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwl4965.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwl5000.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwlagn.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwlwifi 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwlwifi.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/mwl8k.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/twl4030 
/usr/src/linux-headers-2.6.31-14-generic/include/config/wl12xx.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/wlan 
/usr/src/linux-headers-2.6.31-14-generic/include/config/gpio/twl4030.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/input/twl4030 
/usr/src/linux-headers-2.6.31-14-generic/include/config/input/twl4030/pwrbutton.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/ip/vs/wlc.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwl3945/spectrum 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwl3945/spectrum/measurement.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/iwlwifi/leds.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/mtd/ubi/wl 
/usr/src/linux-headers-2.6.31-14-generic/include/config/mtd/ubi/wl/threshold.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/pcmcia/wl3501.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/regulator/twl4030.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/rtc/drv/twl4030.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/scsi/lowlevel 
/usr/src/linux-headers-2.6.31-14-generic/include/config/scsi/lowlevel.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/scsi/lowlevel/pcmcia.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/snd/soc/twl4030.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/twl4030/core.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/twl4030/usb.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/twl4030/watchdog.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/usb/net/rndis/wlan.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/usb/serial/keyspan/usa49wlc.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/uwb/wlp.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/uwb/i1480u/wlp.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/wlan/80211.h 
/usr/src/linux-headers-2.6.31-14-generic/include/config/wlan/pre80211.h 
/usr/src/linux-headers-2.6.31-14-generic/include/linux/wlp.h 
/var/lib/dkms/bcmwl 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/source 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/Makefile 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/dkms.conf 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/lib 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/patches 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/lib/LICENSE.txt 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/lib/wlc_hybrid.o_shipped_i386 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/patches/0001-MODULE_LICENSE.patch 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/patches/0002-Makefile.patch 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/patches/0003-DEV_WL_IF.patch 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/patches/0004-broadcom-sta-5.10.91.9-linux-2.6.30.patch 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/patches/0005-NET_DEVICE_OPS.patch 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/shared 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/bcmdefs.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/bcmendian.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/bcmutils.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/bcmwifi.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/epivers.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/linux_osl.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/linuxver.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/osl.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/pcicfg.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/proto 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/typedefs.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/wlioctl.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/proto/802.11.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/proto/802.1d.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/proto/bcmeth.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/proto/bcmevent.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/proto/ethernet.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/include/proto/wpa.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/shared/linux_osl.c 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_dbg.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_export.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_iw.c 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_iw.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.c 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wl_linux.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wlc_key.h 
/var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/src/wl/sys/wlc_pub.h 
/var/lib/dpkg/info/bcmwl-kernel-source.list 
/var/lib/dpkg/info/bcmwl-kernel-source.md5sums 
/var/lib/dpkg/info/bcmwl-kernel-source.postinst 
/var/lib/dpkg/info/bcmwl-kernel-source.postrm 
/var/lib/dpkg/info/bcmwl-kernel-source.prerm 
/var/lib/dpkg/info/bcmwl-modaliases.list 
/var/lib/dpkg/info/bcmwl-modaliases.md5sums

---

### Post by chili555 on 2010-03-23
Please do:```
locate dkms
```Just tell me if you see this:> /lib/modules/<whatever>/updates/dkms/And this:> /usr/sbin/dkmsYes or no will be sufficient.

Did you install it from Ubuntu package search?

---

### Post by YMS_1975 on 2010-03-23
> **chili555 said:**
> Please do:```
locate dkms
```Just tell me if you see this:And this:Yes or no will be sufficient.

Did you install it from Ubuntu package search?


Neither of those terms showed up.

Wow this is confusing.

---

### Post by chili555 on 2010-03-23
Please do:```
sudo dpkg -i Desktop/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb 
```Any errors or missing dependencies?

You can actually just do:```
sudo dpkg -i Desktop/bcmwl
```Press Tab and the rest will fill in. Press Enter and note any errors.

---

### Post by YMS_1975 on 2010-03-23
> **chili555 said:**
> Please do:```
sudo dpkg -i Desktop/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb 
```Any errors or missing dependencies?

You can actually just do:```
sudo dpkg -i Desktop/bcmwl
```Press Tab and the rest will fill in. Press Enter and note any errors.

When I type in : sudo dpkg -i Desktop/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb...here's what i get : 

[B]yousaf@yousaf-desktop:~$ sudo dpkg -i Desktop/bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb 
(Reading database ... 114126 files and directories currently installed.) 
Preparing to replace bcmwl-kernel-source 5.10.91.9+bdcom-0ubuntu4 (using .../bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb) ... 
Removing all DKMS Modules 
Done. 
Unpacking replacement bcmwl-kernel-source ... 
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ... 
Adding Module to DKMS build system 
Doing initial module build 
/usr/sbin/dkms: line 35: patch: command not found 

Error! Application of patch 0001-MODULE_LICENSE.patch failed. 
Check /var/lib/dkms/bcmwl/5.10.91.9+bdcom/build/ for more information. 
Installing initial module 

Error! Could not locate wl.ko for module bcmwl in the DKMS tree. 
You must run a dkms build for kernel 2.6.31-14-generic (i686) first. 
Done. 
update-initramfs: deferring update (trigger activated) 

Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic 
yousaf@yousaf-desktop:~$ 
[/B]

---

### Post by chili555 on 2010-03-23
Please see post #40. You must get and install all the dependencies: dkms, libc6-dev and linux-libc-dev. Linux-headers you correctly have. Until each and every of these are installed and any dependencies they may have that are not currently on your system, we are destined to :confused:

Please try again.

---

### Post by YMS_1975 on 2010-03-23
> **chili555 said:**
> Please see post #40. You must get and install all the dependencies: dkms, libc6-dev and linux-libc-dev. Linux-headers you correctly have. Until each and every of these are installed and any dependencies they may have that are not currently on your system, we are destined to :confused:

Please try again.

Ok....I'll try that again tomorrow.

It's getting late (damn).  :(

Kids wanna sleep. LOL.

I'll do it step by step tomorrow, and post the results.

Thank you sooooooooooooooooooooo much for your help though.
This is definitely not easy (for me). You're helping a lot.

:)

---

### Post by chili555 on 2010-03-24
Here is my suggested approach to getting your son's wireless going.

First of all, I am not at all sure that bcmwl-kernel-source will actually drive the device. However, your dmesg in post #35 says it's a Broadcom [COLOR="Blue"]4321[/COLOR]. The description for bcmwl-kernel-source says, "These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, [COLOR="Blue"]BCM4321[/COLOR]-, and BCM4322-based hardware." So, it should work; however, many searches suggest the method that works is ndiswrapper. We shall see.

First, you need to install all the packages that are dependencies of bcmwl-kernel-source. It won't work otherwise. Check the dependencies here: [http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)

The little red balls indicate that these are REQUIRED. I know from your posts that you have the correct linux-headers package. I suspect that the installation of dkms might fix it, but, until you can install bcmwl-kernel-source without error or complaint, the driver will not function correctly.

Some of the packages you are going to install may complain about other missing dependencies. If so, I'd try to get them from the install CD. Drop it in the tray and do:

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install <whatever_is_missing>
```

apt-get will whine about not being able to reach the internet, but that may be safely ignored. If the package is available on the CD, it will install it. If not, you will have to go to [http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/) and find it.

Once that is all done, do:

```
sudo modprobe wl
iwconfig

```You will know you have done the work correctly when wl installs with no complaint. Do you have a wireless interface, wlan0, perhaps? Can you click the Network Manager icon and connect?

If not, we will do some troubleshooting and think about ndiswrapper.

---

### Post by YMS_1975 on 2010-03-24
> **chili555 said:**
> Here is my suggested approach to getting your son's wireless going.

First of all, I am not at all sure that bcmwl-kernel-source will actually drive the device. However, your dmesg in post #35 says it's a Broadcom [COLOR="Blue"]4321[/COLOR]. The description for bcmwl-kernel-source says, "These package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, [COLOR="Blue"]BCM4321[/COLOR]-, and BCM4322-based hardware." So, it should work; however, many searches suggest the method that works is ndiswrapper. We shall see.

First, you need to install all the packages that are dependencies of bcmwl-kernel-source. It won't work otherwise. Check the dependencies here: [http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)

The little red balls indicate that these are REQUIRED. I know from your posts that you have the correct linux-headers package. I suspect that the installation of dkms might fix it, but, until you can install bcmwl-kernel-source without error or complaint, the driver will not function correctly.

Some of the packages you are going to install may complain about other missing dependencies. If so, I'd try to get them from the install CD. Drop it in the tray and do:

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install <whatever_is_missing>
```

apt-get will whine about not being able to reach the internet, but that may be safely ignored. If the package is available on the CD, it will install it. If not, you will have to go to [http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/) and find it.

Once that is all done, do:

```
sudo modprobe wl
iwconfig

```You will know you have done the work correctly when wl installs with no complaint. Do you have a wireless interface, wlan0, perhaps? Can you click the Network Manager icon and connect?

If not, we will do some troubleshooting and think about ndiswrapper.

Hey Bill,

I've tried doing this but nothing seems to work. Can I call you, or you call me (like last time)?  :D

---

