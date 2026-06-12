---
title: "Problems connecting with wireless - Please Help!"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by Chris220 on 2008-12-24
Hi all,

I'm posting regarding my problems involving connecting to the internet through my wireless connection. Here's what I've been through and where I am so far:
First day: I recieved the Ubuntu 8.10 disk, installed it and set up dual boot with Windows XP. Everything seemed to work, internet worked by default.
Second day: Internet is broken. The nm-applet does not show my wireless connection when I click on it, only a greyed out box for Wired connection, which I don't have. Tried installing NdisWrapper to get my drivers to work, but I can't get it to install or work properly. Whenever I run the Frontend, it says that it cannot find the module.

I have tried SO much to get connected to the internet, and I really am desperate for some help. Please, if you know anything, help me! I'd be eternally grateful!

I have installed updates, so could it be something to do with those? If so, how am I to fix it without an internet connection!?

-EDIT- Changed title, thanks for showing me that guide!

I have a Linksys WMP300N V2 adapter.
I know that's not on the list, but it worked yesterday, I was on Pidgin and everything >_<
It seems to have stopped working after the updates! Could this have caused the problem?

If not, could someone point me to a tutorial on how to install NDISWrapper properly, or perhaps Wicd? I need to be able to do it without having internet access on Ubuntu, but I do have internet access on XP on the same Harddrive.

---

### Post by ieee488 on 2008-12-24
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Chris220 on 2008-12-24
Thanks for that, I've changed post somewhat. Is it possible to change the title?

---

### Post by Chris220 on 2008-12-25
BUMP

Sorry, but I really am desperate...

---

### Post by dav9000 on 2008-12-25
Hi. I have had the same problem as you I think. After yesterday updates, this morning network-manager wasn't able to connect through wlan. Ethernet was ok but it was impossible to connect on wlan0.

So... I installed WICD, a connections manager similar to NETWORK MANAGER. Check install instructions in [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) and you are done.

Goodbye nm, hello wicd.

Hope this solves your problems.

---

### Post by Chris220 on 2008-12-25
Thank you for the reply! How do I install it without having an internet connection though? I could try compiling the tar.gz source, but tbh, I don't know how to!

Could you walk me through it?

---

### Post by dav9000 on 2008-12-25
Don't you have ethernet connection?

---

### Post by Chris220 on 2008-12-25
No, sorry! If I did, I would be using that over wireless anyway probably (I'm on a desktop PC)... but how can I install Wicd without an internet connection?

---

### Post by dav9000 on 2008-12-25
I guess you will have to download sources in your XP box and compile them in your Ubuntu partition. I'm very sorry I cannot be any useful at this point, since I have no idea how to do it.

Maybe any other person might help you.

---

### Post by Chris220 on 2008-12-25
Well, thanks for your help! I'll give it a go in a minute, as soon as I finish my Shoop Da Whoop! picture ;)

---

### Post by Chris220 on 2008-12-25
> **dav9000 said:**
> I guess you will have to download sources in your XP box and compile them in your Ubuntu partition. I'm very sorry I cannot be any useful at this point, since I have no idea how to do it.

Maybe any other person might help you.
Ok, I've managed to download a .deb file for Wicd. But, when I open it with Debi, it says it conflicts with "network-manager". I assumed this was the default connection applet which doesn't work for me, so I uninstalled it. I rebooted and nm-applet was gone. I tried the .deb file again, but it still says it conflicts with "network-manager". Please help!

---

### Post by Chris220 on 2008-12-25
BUMP

Please, I just need to know how to stop this conflict between the two programs!

---

### Post by gordintoronto on 2008-12-25
> **Chris220 said:**
> Well, thanks for your help! I'll give it a go in a minute, as soon as I finish my Shoop Da Whoop! picture ;)

I managed to download a .deb file by following a link from the wicd.net site to sourceforge, using another computer, then move it to my Ubuntu system on a flash drive, and install it from there.  That was three months ago, so the version number has probably changed.  At that time, the current file was wicd_1.5.3_all.deb

To install: dpkg -i file.deb

Ubuntu likes .deb files!

---

### Post by Chris220 on 2008-12-25
Thanks for teaching me about the dpkg command!

But it comes up with an error saying that network-manager is installed and the two packages conflict. How can I stop this conflict?

---

### Post by Chris220 on 2008-12-25
Doesn't anyone know how to stop the conflict? Please, I really am sick of this problem -_-

---

### Post by speed32219 on 2008-12-25
wicd replaces network manager I believe.  It should have de-installed Network manager when you installed wicd.

---

### Post by Chris220 on 2008-12-25
It should have done, but it didn't. It's just complaining of conflicts. How can I rid my system of Network-manager manually? Any specific command I can run?

Thanks for the reply anyway!

---

### Post by speed32219 on 2008-12-25
Here ya go!

Installing Wicd, you just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

Note:  If using intrepid replace hardy with intrepid above.

You'll also need to add the key used for signing Wicd by running the following command in a terminal: 

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.

---

### Post by Chris220 on 2008-12-26
I did all of what you said, but when I tried to get the key it says "gpg: no valid OpenPGP data found."

Any idea why?

---

### Post by Chris220 on 2008-12-26
-UPDATE-
When I go to Add/Remove Applications, and refresh the list, I get the error:
```
W: GPG error: http://apt.wicd.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A

```
I thought that might help...

---

### Post by Chris220 on 2008-12-26
I have an internet connection now, I fixed it. But it drops out occasionally and it's a lot weaker than it is when it's connected through my Windows XP. It's also quite a bit slower...

My router is a Linksys WMP300n. If it is a driver problem (the dropping out and slowness thing), what is a good NDISwrapper or Linux driver for WMP300n?

---

### Post by DWade on 2008-12-26
Please note..  I only glanced thru the post, so I could have missed something,

but....  I have found the following problem with the intrepid updates...
when 8.10 ubuntu updates to kernel 2.6.27.11 generic, the network manager quites working properly.  I have and air and this was the first version I did not have to blacklist airprime, and add all the other commands to.

When it boots up .11 kernel it can no longer find the ttyACM0, and can no longer connect.

Yet, if I boot from Kernel 2.6.27.9, everythings works find.  

So at you grub boot try booting the older kernel.  if that works, then down load out of add remove programs startup manager and have it select the older kernel for default boot.

An Here I am going to ask does this need to be place as a bug or can it be looked at from here?

Also how do I uninstall the 2.6.27.11 kernel.  Just use the package manager and select linux-image-2.26.27.11-generic?

---

### Post by Baldrick_NZ on 2008-12-26
> **Chris220 said:**
> I have an internet connection now, I fixed it. But it drops out occasionally and it's a lot weaker than it is when it's connected through my Windows XP. It's also quite a bit slower...

My router is a Linksys WMP300n. If it is a driver problem (the dropping out and slowness thing), what is a good NDISwrapper or Linux driver for WMP300n?

This one appears to be an issue related to Interpid 8.1 only...

If it helps any, I had the same problem with regard to speed and signal strength. I found the following command in terminal yields an exceptionally  good result... ```
sudo iwconfig wlan2 rate 54M
``` Use 'iwconfig' in terminal 1st to identify what your wlan number is and use that where I have wlan2.

The difference in speed can be confirmed my using a simple 'before and after' speed test. (I used the one at [www.nzdsl.co.nz](www.nzdsl.co.nz)).

The only problem is that the code seems to disappear when ever a system restart or shut down is performed. To counter this (until I can work out a permanent fix) I have created a custom application launcher on one of my panels which I click every time the PC starts up.

I've also found that Wicd is tends to read a little light with regard to signal strength. I have installed Network Activity Monitor also by right clicking on the panel. This gives me, I feel, a more accurate picture of signal strength and shows my packet transfer rate as well.

Hope this helps.

---

### Post by Chris220 on 2008-12-27
First off, thanks Baldrick for that advice, I tried it and it seemed to make a bit of a difference. However, the signal strength is still only at 35% when it is usually between 90% and 100% on my Windows XP.

@DWade - Thanks for the information. I have two questions:
1.) If I use an older kernel, will I lose all  my settings and everything from my newer kernel?
2.) What are the disavantages of an older kernel?

---

### Post by DWade on 2008-12-27
> **Chris220 said:**
> 

@DWade - Thanks for the information. I have two questions:
1.) If I use an older kernel, will I lose all  my settings and everything from my newer kernel?
2.) What are the disavantages of an older kernel?

#1 I do not believe so.  all my setting are the same. It just boots up the older kernel..  The kernels are located in the grub menu.  I used startup manager to change the default to Kernel 2.6.27.9

#2 The newer kernel has some update and enhancements.  what I don't know have to go to the change logs and see.

But with the newer kernel the network applet fails to recognize ttyACM0 as the air card and keeps trying ttyUSB0, ttyUSB1 etc.

I first tried to blacklist airprime to see it would find it but it did not.

so I am not sure what the differences are.

---

### Post by Chris220 on 2008-12-27
Ok, it all works now anyway. My only issues are the fact that the connection is no where near as strong or fast as it should be, like it is on XP. Could it be a driver issue?

---

### Post by Baldrick_NZ on 2008-12-27
> **Chris220 said:**
> Ok, it all works now anyway. My only issues are the fact that the connection is no where near as strong or fast as it should be, like it is on XP. Could it be a driver issue?

Check out the last part of my last post..
> I've also found that Wicd is tends to read a little light with regard to signal strength. I have installed Network Activity Monitor also by right clicking on the panel. This gives me, I feel, a more accurate picture of signal strength and shows my packet transfer rate as well.


Also, is your router a max 54Mb transfer? Some are higher these days. If your's is higher then you may need to replace the 54M in the code to the max rate of your router for it to work. IE: sudo iwconfig wlan0 rate 108M - if your router is 108Mb transfer.

The other thing is to check the name of your wlan connection. Yours might not be wlan0 in which case the code above prolly wont work too well if at all. To check this open terminal and type iwconfig.

This should help with regard to your signal issues..

---

### Post by Chris220 on 2008-12-28
Well, I'm not sure what my max transfer is, I will have to find out... I know that my connection is wlan0 though, so that bit is ok!

So, are you suggesting that the network monitor is not reading the signal right?

And I still can't install Wicd, I keep getting that error about "no valid openPGP data" or something similar...

---

### Post by Chris220 on 2008-12-29
Ok, now I can install wicd.

Only, when I'm using Wicd, it doesn't pick up my network. How do I make it find a network?

---

### Post by Chris220 on 2008-12-30
Bump

---

### Post by breadisawesome on 2009-01-11
Ive been following this and for the most part, for I have a WMP300N and a WRT300N, it has at least has helped assure a connection with an unsecured neighbor's network, but mine is encrypted, WPA - Personal TKIP, and cant for the life of me connect to it.  chris did you fix your problem and was your network secured or does anybody else have anything to add that could help fix my problem.

---

### Post by Chris220 on 2009-01-11
I did manage to get it working in the end, yes. My network is WEP security, so I just had to type in the keycode and it connected. That was after installing all the Drivers and so on.

I found the WPA - Personal bit:

Right click on nm-applet
Click Edit Connections
Click the Wireless tab
Click on your network (Mine is "Auto Mountains")
Click Edit (the button on the right)
Go to the "Wireless Security" tab
Change Security to "WPA and WPA2 Personal"
Type in the code

Hopefully that might work, but it is only a guess.

---

### Post by breadisawesome on 2009-01-11
Thats what I have been trying. With nm only the STA driver would allow me to actually see wireless connections around, but could never find my router and was 50/50 when connecting to a neighbors network.  Then with wicd it can find my router, but it wont connect.

wicd says its putting down the interface and just stops trying to connect.  Ive just tried disabling my security and connecting that way.  And it still wont connect.  This is puzzling, because through 5 other laptops and ps3's they can connect to the router just fine.

When under windows it likes to connect no problem as well but with ubuntu and the WMP300N it doesnt.

---

### Post by Chris220 on 2009-01-11
That is strange... well apart from Wicd and NM, I only know of one other wifi manager; Wifi Radar. I couldn't even make it open though, let alone connect. It's in the repository (I think) so try it out... tell me if you get any better results than I did!

---

### Post by breadisawesome on 2009-01-11
Well first off, I would like to thank you for your help and the help other provided you to get me as far as I did.  

I fixed it and all I did was reinstall ubuntu and made sure I was on a wired connection, downloaded the Broadcom STA wireless drivers and it worked.  Then applied the updates. 

What I orginally did was as soon as ubuntu was installed I tried to dl the drivers and wasnt connected to the internet.  I think ubuntu might have a slight problem with cases like this, I think it what happens is ubuntu decides after not being able to download the driver that it has it and tries to operate without it.  And then since ubuntu thinks you have a proper driver it will never officially download the driver.  

But that of course is just my guess.  And either way it works now and im happy.

Thanks everybody.

---

### Post by theozzlives on 2009-01-11
If your not connected to the net you can't download nothin. That's why a 56k modem is in the minimum system reqs.

---

### Post by Chris220 on 2009-01-11
> **breadisawesome said:**
> Well first off, I would like to thank you for your help and the help other provided you to get me as far as I did.  

I fixed it and all I did was reinstall ubuntu and made sure I was on a wired connection, downloaded the Broadcom STA wireless drivers and it worked.  Then applied the updates. 

What I orginally did was as soon as ubuntu was installed I tried to dl the drivers and wasnt connected to the internet.  I think ubuntu might have a slight problem with cases like this, I think it what happens is ubuntu decides after not being able to download the driver that it has it and tries to operate without it.  And then since ubuntu thinks you have a proper driver it will never officially download the driver.  

But that of course is just my guess.  And either way it works now and im happy.

Thanks everybody.
It's great to know you got it working! Just out of interest, how strong is your signal? Because mine is usually 100% on my XP. Then when I am on Ubuntu (it's dual boot) the signal is like 25% at best. I am using the windows drivers with Ndiswrapper... are the broadcom drivers better?

---

