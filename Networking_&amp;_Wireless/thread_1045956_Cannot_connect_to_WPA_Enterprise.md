---
title: "Cannot connect to WPA Enterprise"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by nwillettjeffries on 2009-01-21
Apologies in advance if this is a dupe. I've done my best to search the forums for a solution to my problem but to no avail...

**The Problem:** My laptop will not connect to my college's WPA Enterprise network.

**Relevant information:** 
I am running 8.10. I was able to connect to the same network under 8.04.

The laptop is a dell e1505.

My wifi card is an Intel PRO/Wireless 3945ABG. Wireless is working in windows so I don't believe there is anything wrong with the hardware.

In 8.10, I am able to connect to WEP and Open Networks. WPA seems to be the only issue.

I think (though I'm not 100% certain) that I'm running the wext driver.

The college network is WPA Enterprise with PEAP and MSCHAPv2. Hardy's network manager requests a username, password, and certificate. I provide all 3. In 8.04, network manager would automatically get the certificate. Now in 8.10, I direct network manager to a copy of the certificate that I have downloaded over ethernet. The certificate file has the .cer file extension.

When I attempt to connect, I will get one green dot on the network manager icon in the notification tray. However, I will never actually connect to the network (which would show 2 green dots and then bars). Eventually, network manager will pop up the window titled "Wireless Network Authentication Required." Further attempts to connect always result in the reappearance of this window.

My wpasupplicant version is: 0.6.4-2
My network-manager version is:0.7~~svn20081018t105859-0ubuntu1.8.10.1

I have read about cases where some people saw their network passphrase displayed in hex. This has not happened to me.
[B]
Things I have tried that did not work[/B]:
I have tried replacing network manager with WICD.

I have tried manually editing the connection settings in gconf-editor.

I have tried reinstalling wpasupplicant.

I have tried setting PEAP version to both 0 and 1.

Any help would be appreciated. I can provide logs (or any other information) if I am told the appropriate commands.

Thanks in advance.

---

### Post by iamthemicrowave on 2009-01-21
same thing happened to me, cant connect to my college network, and a billion other people are having this problem...welcome to the club

---

### Post by nwillettjeffries on 2009-01-21
It would seem that if so many people are having this problem and have been having it since 8.10 came out then we'd have a solution or at least some idea of what is wrong by now.

Any help would be greatly appreciated. This bug is a deal breaker for me. I don't have time to do a fresh install of 8.04 so I basically have to cobble things together in windows right now.

---

### Post by nwillettjeffries on 2009-01-21
Alright, after some additional fiddling around I've got this solved.

Here are the details:
Please note that my problem was with WPA Enterprise, NOT WPA2.
As mentioned above, I had tried switching to wicd from network manager and using gconf-editor to manually edit my settings but neither of these methods worked.

As a last ditch effort, I installed jaunty packages for wpasupplicant, network manager and a few others as detailed in this bug comment:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272185/comments/174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272185/comments/174)

So first step is to go to that link and follow the directions there. Be extremely careful as messing up with those directions can break your install.

However, once I had done that, wireless was still not up. You need to completely clear the old connection info before it will work. 
To do that I took the following steps:
1. Disable wireless by right clicking on the network manager applet and unchecking "Enable Wireless"
2. Right click on the network manager applet and select "Edit Connections"
3. Select the wireless tab and delete the wifi connection you are having problems with.
4. Go to Applications > Accessories > Passwords and Encryption Keys
5. Click on the Passwords tab.
6. Delete all entries for the wifi network you are attempting to connect to. Entries will be labeled "Network Secret for [Your network's name here]" 
7. Now you are going to set up the wifi connection that you deleted in step 2 and 3. Right click on the network manager applet and select "Edit connections"
8. Select the wireless tab and then click the button labelled "add new connection" (or something like that). Input the appropriate information and it should hopefully work now.

Good Luck...

---

