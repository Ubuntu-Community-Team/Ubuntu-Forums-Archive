---
title: "[SOLVED] Trouble connecting to wireless home network (Atheros AR5007)"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by theytookpenny on 2008-12-13
I was able to set up my wireless card using the following the following command:
```
 sudo apt-get install linux-backports-modules-intrepid-generic
```

I was successfully able to connect to my home network about five or more times but when I set up a new usplash theme with startup-manager it would not connect again. In fact, my wireless card could not see any of the local networks around my area. However, when I went to school, it could detect the public connection. I tried to undo changes by setting back the usplash theme, but nothing has really happened and I'm quite sure that couldn't be the problem. I still can connect to my home network if I am wired, but other than that I can't even see it. I want to fix this before I go to back to school because I'm afraid the same thing will happen there. If there is anything you can help me with I will be very very grateful.

My system specs are:
Processors: AMD Turion(tmO 64 X2 Mobile Technology TL-60
Memory: 3GB
Disk Space: 200GB
Graphics Card: NVidea GeForce 7150M/ nForce 630M
Wireless Card: Atheros AR5007

And I'm not sure, but for some reason when I install things I always get the i386 verson instead of AMD64, should I be worried?

Thanks for any help offered and even for just looking at this post.

EDIT: When I type iwconfig in the terminal I get this output:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

---

### Post by mapalma on 2008-12-13
1- Disable Atheros 802.11 wireless LAN card from System, Hardware Drivers

2- Download:
[http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic)

3- Reboot

---

### Post by theytookpenny on 2008-12-13
But I've already installed that package... I have "*Support for 5xxx series of Atheros 802.11 wireless LAN cards*" already selected. I'm not sure if you're talking about that driver or the other one which is "*Support for Atheros 802.11 wireless LAN cards*". Can you please tell me which one you mean and what this will do other than the obvious of what it's supposed to do? Sorry if I'm not being specific either, I mean how will reinstalling fix this problem and how can I make sure it doesn't happen again.

---

### Post by theytookpenny on 2008-12-14
BUMP... I need to fix this if at all possible.

---

### Post by theytookpenny on 2008-12-14
Ok, I tried you're method.. sort of.

This is what I did:

1. Downloaded from ubuntu the linux-backports-modules-intrepid-generic
2. Uninstalled that same package from my system.
3. Did a sudo apt-get clean
4. Deactivated the driver
5. Reboot
6. Installed the downloaded package
7. Activated the driver

And yea.. I still can't see my network.. or any of the ones near here.

---

### Post by theytookpenny on 2008-12-14
After doing a bit of research I found out that the new Network Manager has been giving a lot of people problems with not only their wifi but wired connections as well and that the solution was to use a different connection manager (In this case WICD). Thanks to [this thread]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/353009535931") I was able to fix this error.



For those who have an available wired lan connection, follow this guide. If you can't do that with you're laptop, but have an available computer and a mass storage device skip to the bottom.

This is what I did (Step by step so that Newbies can do it too)

1. Go to  *Menu* >* System* > *Administration* > *Software Resources*
2. In the Software Resources window, click on *Third-Party Software*
3. Click the "+ Add" button and type the following in the pop-up:
```
deb http://apt.wicd.net hardy extras 
```

4. Click "+Add Source", close Software Resources, and allow it to update sources.
5. Go to Menu > Applications > Accessories > Terminal
6. Type the following:
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add - 
```

7. Type password if necessary. It should say "Ok" when it's done.
8. Now type the following
```
sudo apt-get install wicd
```
It will say that network-manager and network-manager gnome-will be uninstalled.

9. For those who have a notification area type: ```
wicd-client
```
For those who don't the code is: ```
wicd-client -n
```
A new pop up window should appear with the words "WICD Manager in the title bar". If this does not show, look in the notification area.

10. Click on the arrow next to the name of the network you want to connect to.

This only if you use encryption on your connection, if you don't, simply click "Connect" and you should be done. You can do the optional step 15, but I'm pretty sure you can figure that out on your own.

11. Click on "Advanced Settings"
12. If you're using dchpi, ignore all the boxes in the popup window and skip directly down to "Use Encryption". Make sure the check box next to it is checked.
13. Select the type of encryption the network uses and input the password, click ok.
14. All that's left is to click connect.

15. Optional: if you want to automatically connect to that network everytime you're plugged in/near the wifi source, check "Automatically connect to this network"

----------------------------------------

If you don't have an available cable to access the internet and have another computer then you can download [this deb file]("http://downloads.sourceforge.net/wicd/wicd_1.5.6_all.deb?modtime=1228387182&big_mirror=0") onto a flash drive/ipod/phone and hook it up to you're computer. It contains wicd v1.5.6 for both i386 and amd64 systems. Once you get it up an running, go through the guide to add it to the repositories and configure (you don't have to do step 8.)

Hopefully, this will help someone else!

Instructions to install can be found in the [Official WICD website]("http://wicd.sourceforge.net/download.php") - Look for the Ubuntu section.

----------------------------------------


[COLOR="Red"]**Please Leave Feedback**[/COLOR]

If this guide worked for you, please leave a thank you post so that I can validate how accurate it is and maybe even post a whole atheros guide on a different website. If it didn't, then post anyway so I can help you =)

---

### Post by AADude on 2008-12-14
I don't get how to download WICD if we have no internet connection...

---

### Post by theytookpenny on 2008-12-14
If you can view this post, then you probably have access to the internet. One way you can download it is by connecting you're laptop/computer to a wired lan connection, I'm sure if this is you're personal network you can do that with a spare cable. Another way is to use a usb flash drive/ipod/phone and download [this deb file]("http://downloads.sourceforge.net/wicd/wicd_1.5.6_all.deb?modtime=1228387182&big_mirror=0"). This is the 1.5.6 version.. and I have no idea if that is the latest.

Once you get it up and running follow the steps above to add it to the repositories and then update.

---

### Post by djrogers510 on 2009-01-04
This post saved my life.  Thanks!!!  I will never again get a laptop with an Atheros WiFi 'card'.  Talk about proprietary!!

---

