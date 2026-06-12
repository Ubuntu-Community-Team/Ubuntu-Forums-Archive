---
title: "Wireless disabled at start"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by Zilioum on 2010-11-16
When I boot my notebook  (Ubuntu 10.10), wake it up from standby or hibernation the wireless connection is always disabled. I can enable it by right-clicking on the network manager icon in the panel and click on "Enable Wireless". After I've done that the wireless works flawlessly.
I couldn't find any solution to this problem, because all the threads I've found so far are about wireless not working at all.
Is there an option I have to set? Or is there a way to enable it with a script run on startup?

Cheers

---

### Post by dineshs on 2010-11-16
See if this helps
[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)

---

### Post by Zilioum on 2010-11-16
Thanks for your post. I tried the solution, but it doesnt work. My NetworkManager.state file looks fine and already did before I tried the solution.
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```
I also never had to force-shutdown after hibernation as described in the bug.

Any other suggestions?

---

### Post by grahammechanical on 2010-11-16
Someone in another post said that their solution was to save current session. I have just tried unsuccessfully to find that post because I cannot tell you how to do that. As a test I just suspended my machine. I was not given the option to save current session. When I resumed I still had internet connection because I am connected by ethernet cable but the system did not detect any availbale wireless networks until I disabled and then enabled wireless. It is as you say.

Regards.

It was iokara08 who found the solution of saving current session. I cannot find out how to do this. My machine is a desktop, so perhaps I do not have that option.

---

### Post by Zilioum on 2010-11-23
Let's try it that way: Does anyone know how to enable wireless on the command line, to "click" the "enable wireless" button via the terminal so to speak?
I tried ```
sudo ifconfig wlan0 up
```
but it doesn't work. I can enable/disable the card with ifconfig but when enabled, "enable wireless" still isn't checked by default.

---

### Post by blazerw on 2010-11-26
This will do it:
```
nmcli nm wifi on
```

The above is the NetworkManager command line interface. All this command does is enable wifi. The same as right-clicking the network icon and choosing enable wireless.

I created a file in /etc/profile.d called enable_wifi.sh that only has the above command in it. This makes wifi enabled whenever I log in.

---

### Post by Zilioum on 2010-11-26
Thanks a lot, that's exactly what I was looking for.

---

### Post by Zilioum on 2011-05-05
I think I might have found the solution when upgrading to 11.04. There wireless was hard blocked and I used rfkill to unblock it. Maybe in 10.10 it was just always soft blocked.

If you have this problem, try the following.

See if any of your devices are blocked.
```
rfkill list
```

If yes, unblock them all.
```
rfkill unblock all
```

You can unblock a specific device by replacing 'all' with the name of the device.

---

### Post by chesspupul on 2011-12-01
Might work if you take a new look at the problem....
 
SOLUTION! (at least for me on my win7 laptop)
I just had this problem when I reinstalled the OS from the OEM disc (not the factory install disc) I figured the OEM disc had a driver conflict. And I even tried updating the latest Wireless driver. But I incorrectly pointed the finger at the wireless lan driver. 
The HOT KEY strip (the one with the buttons that turn white when you touch them just above the keyboard) on my laptop also controls the Wi-Fi Radio on/off button. This was the problem. You need the original driver for that strip, even if your volume on the strip is working.
Background. Think of your wireless lan as two seperate devices... the radio is compared to the cord of an ethernet connection. The wireless lan card is the ethernet card. When you think about it as one device it is easy to see why so many people assume the problem is with the wireless lan card. But the important part is that a laptop usually divides the two up to save power. Controlling the radio from a button on the keyboard (or a function key) (mine is FN +F2) is another reason to think of the two as seperate items.
Before reaching this conclusion I tried using "allow the computer to turn this device off to save power" I also had tried High performance power option modes and other wireless radio from the control pannel in both plug-in and battery modes. I tried the turn wireless netork on and off as well. There were plenty of reasons to think this was going to fix the problem.
I alos tried going with the above script but found that "WisWBSet.exe" was missing from windows 7. I also tried a Java script but could not find the key code for the FN button, nor the combination of the FN button (hold) and the F2 key combo. 

So update your HOTkey strip driver... see if that doesnt fix your problem.

---

