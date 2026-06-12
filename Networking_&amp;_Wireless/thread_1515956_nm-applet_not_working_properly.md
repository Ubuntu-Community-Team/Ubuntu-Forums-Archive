---
title: "nm-applet not working properly"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by xenocrates on 2010-06-23
Hi everybody

I've been having some problems recently with my wireless internet connection.

Whenever I boot up my computer, I get the notification area in the top bar, but the network manager applet does not show. When I open up gnome-system-monitor I see that nm-applet --sm-disable is running, like it should, but still it doesn't show up.

What's more is, that I am unable to connect to my wireless network as a result of this. I have tried doing it all manually through iwconfig, but it does not support passphrases, and so I cannot get past the point, where I register my essid. When doing it manually I have also noticed that even after I specify essid the wlan does not associate itself with my access point.

Eventually, though, the nm-applet will magically appear in the notification area and and authentication screen will appear, prompting me to enter the networks WPA or WPA2 passphrase. No matter how many times I enter the passphrase I still have to enter it again next time I reboot. Anyway, after I fill in the passphrase and press enter, the window freezes. After about five minutes waiting it unfreezes and my connection is established.

I have tried searching the web for a solution, but no one seems to have my specific problem. It's always that the nm-applet is not running or they somehow lost the notification area or something like that. So I now resort to writing in here. Not that it's a bad thing. I just hoped I could solve this more or less on my own.

I'm not an actual linux  geek, so I'm not that familiar with the inner workings and how to mess around with the config files and whatnot. I've tried what I knew would be safe to do. I even reinstalled network-manager-gnome and network-manager packages, hoping that would do the trick, but it didn't.

I really hope that someone out there has any suggestions. If you need any log information I will be happy to post it, but i'm not sure what is relevant and what is not. There are so many log files in the system log viewer :)

Cheers :)

---

### Post by wilee-nilee on 2010-06-23
If the panel does not open and show it in a normal way you can restart it with this command in the terminal.
```
killall gnome-panel
```

---

### Post by xenocrates on 2010-06-23
> **wilee-nilee said:**
> If the panel does not open and show it in a normal way you can restart it with this command in the terminal.
```
killall gnome-panel
```

Unfortunately, using the above command does not solve my problem. I am convinced that the problem lies not with the panel, but with the network manager and/or the network manager applet.

---

### Post by wilee-nilee on 2010-06-23
> **xenocrates said:**
> Unfortunately, using the above command does not solve my problem. I am convinced that the problem lies not with the panel, but with the network manager and/or the network manager applet.

If you have changed the theme or have added themes you might just have to go to appearances in system-preferences and see if changing the theme helps.

 What I will tell you from experience is that being convinced that a specific program is the problem may keep you locked into a fix idea that is not the problem. Just because the applet doesn't show and your also not experienced (your words here) doesn't mean it is the root of the problem. It is unlikely that it is the NM applet, it isn't auto running probably because you need to open it and set it to connect automatically.
[ATTACH]161314[/ATTACH]

Really I suspect the messing around with the config stuff is part of the problem, the nm program is pretty automatic, if you have checked for hardware drivers in that section in preferences. You might post the output of ```
lspci
``` to identify the network card

---

### Post by xenocrates on 2010-06-23
> **wilee-nilee said:**
> If you have changed the theme or have added themes you might just have to go to appearances in system-preferences and see if changing the theme helps.

 What I will tell you from experience is that being convinced that a specific program is the problem may keep you locked into a fix idea that is not the problem. Just because the applet doesn't show and your also not experienced (your words here) doesn't mean it is the root of the problem. It is unlikely that it is the NM applet, it isn't auto running probably because you need to open it and set it to connect automatically.
I have not changed the theme before this problem started. But when I try to open the connection manager it, too, freezes for a loong time, before letting me make any changes, whatsoever (however it is not grayed like programs that are not answering usually is - neither is the authentication screen where I need to enter my passphrase). When it finally unfreezes I can edit the wireless connection and enter the passphrase as well as set the gateway and DNS if I want to, but none of this helps, since I still have to wait for the wireless icon to magically appear in the notification area, even though it is shown as running in the system-monitor.

---

### Post by LindisfarneJazzClub on 2010-06-23
I just had the same problem, searched the forums and found this:
 
[http://ubuntuforums.org/showthread.php?t=1515583&highlight=network+manager+icon+applet](http://ubuntuforums.org/showthread.php?t=1515583&highlight=network+manager+icon+applet)
 
As Iowan replies: try adding a notification area to your top bar.
This could be done by right-clicking the top bar, then clicking *Add to panel.* Scroll down to *Indicator Applet* and click Add.
This should add the NetMan applet, as well as Volume Control and PowerMngr
 
Good luck!

---

### Post by xenocrates on 2010-06-23
That is not really what I am experiencing. I already tried it without any luck a while back. But thanks anyway :) Appreciate the help

---

### Post by Pabbajati on 2010-06-23
I just thought I'd share that I'm having the same problem: the applet not showing since yesterday evening (when I also had a boot problem) but can see that it exists. No internet connection. Small difference is that the applet doesn't later appear.

Tried cable connection to internet router but did not activate network manager and I got no response.

I haven't had a chance to try out the suggestions yet as I am not (obviously) on my Linux machine as no internet connection now.

I did however try adding the applet to the notification area with the pull down menu but it isn't there to select from the long list of other things (I do remember it being there once...).

I had changed the notification panel colour the day before but it was working fine then..have tried changing it back but still no applet!

Should I post separately about the boot problem?

Thanks to all.

---

### Post by xenocrates on 2010-06-23
I've tried running the following command:
```
sudo lspci | grep Ethernet
```
Which gave me the following output:
```
07:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 16)
08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```
Hope that helps :)

---

### Post by Cuppa-Chino on 2010-06-26
I have the same issue on one computer here:

by running nm-applet manually I can get network connection fine but I have to start it manually

I am totally unclear where I should look for the error at the moment

I even tried making a script that waits for 10 sec and then runs nm-applet no luck if its in startup applications (how can I find those manually??) but when I run the script from shell then its all fine again....

---

### Post by xenocrates on 2010-06-26
That is not the same issue as mine. I can not fix my problem by manually starting nm-applet, since it is already running and doing a killall and then starting it again does not do any good.

I suggest you go look in the System->Preferences->Startup Applications and then add nm-applet

---

### Post by f6iqa on 2010-07-02
With last update, I have added the notification zone (last in available option) and it works fine. The problem I had is that wireless icon turned into speaker icon thus giving two similars icons on the pannel. I removed one and I get stuck with the problem described in this thread. Now network icon is back again.

---

### Post by Cuppa-Chino on 2010-07-05
> **xenocrates said:**
> That is not the same issue as mine. I can not fix my problem by manually starting nm-applet, since it is already running and doing a killall and then starting it again does not do any good.

I suggest you go look in the System->Preferences->Startup Applications and then add nm-applet

not my issue -- I manually start nm-applet (from cli or from launcher icon) without a problem, my issue is to do with startup applications not working I fear

---

### Post by ufu1 on 2010-07-05
I'm having same problem as xenocrates:
nm-applet running okay but icon doesn't show up in panel (actually I think it flicks on and then disappears on login)
second problem is when this happens (and before) wireless connection stops working (device not managed i think)
there's another problem i've just started getting - with normal boot my wired connection doesn't work. to get the wired connection to work i start up in recovery mode and drop to shell with networking then works no problem. I then startx. this doesn't fix icon problem and i don't know if it fixes wireless problem

---

### Post by ufu1 on 2010-07-05
hmmm.. added a notification area and icon re-appeared.

can see message for wireless now: device not managed. It's really frustrating as wireless works fine if i reinstall.
also i haven't tried it again but the last few times i had to boot in recovery mode, drop to prompt with networking then startx every time for wired network to work.

any ideas please?

---

### Post by ufu1 on 2010-07-05
hmmm.. added a notification area and icon re-appeared.

can see message for wireless now: device not managed. It's really frustrating as wireless works fine if i reinstall os.
also i haven't tried it again but the last few times i had to boot in recovery mode, drop to prompt with networking then startx every time for wired network to work.

any ideas please?

---

