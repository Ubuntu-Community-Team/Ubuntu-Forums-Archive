---
title: "Intermittent wifi"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by JonathanCR on 2010-12-01
Hi there,

I am running 10:04. I have had no problems getting the wireless to work. However, I have found that in some locations, the computer has enormous difficulty getting connected.

It always sees the wireless networks that I know are there. So the wifi is working and there appears to be no issue with its driver. However, it has difficulty connecting. What happens is that I click on the network that I want it to connect to. The little wifi icon ripples for a bit as it makes the effort, then a bubble comes up with the name of the network and the message "You have been disconnected." - not that I ever was connected. After this I have to click on the icon again and select the network I want to connect to again, to make it try again. Eventually, it usually does connect, and after that the connection is fine, but it may take many attempts before this happens.

I think the problem is where the signal is relatively weak. In my flat, where the router is nearby, this never happens; Ubuntu connects almost as soon as the computer is turned on. In a house where the router is on another floor and there are known strength problems, the issue occurs. In a public location where I don't know where the router is but I know the signal is variable, the issue occurs. Note, however, that even in these cases, it has no problem *seeing* the network - it just doesn't want to connect to it. Note also that when I use Windows (this is a dual-boot machine) there isn't the slightest problem of this kind; it connects to exactly the same networks first time and doesn't mess about.

So I have two questions. First, is there any way I can resolve this and get Ubuntu to connect to networks that it can see without difficulty? Second, if I can't, is there a way to make it automatically keep trying until it has successfully connected? It is very annoying having to keep an eye on it while it is trying, and then, if it fails, select the network again and wait while it tries again. If I could make it so that it does this itself without supervision until it's connected, that at least would be a big step forward.

The laptop is an HP Pavilion DV4, but I'm not sure what its wireless card is.

Thanks!

---

### Post by uncaspi on 2010-12-01
Try to set power save mode to off. Determine the name of the card. i.e eth1,wlan0, ra0 etc.Open a terminal and type sudo ifconfig or sudo iwconfig
Suppose it is wlan0 you  then type

sudo iwconfig wlan0 power off

---

### Post by JonathanCR on 2010-12-01
Thank you, I'll try that next time I'm near one of those problematic wifi networks.

---

### Post by uncaspi on 2010-12-01
You can also try the sens option.

sudo iwconfig wlan0 sens -80

---

### Post by JonathanCR on 2010-12-02
Unfortunately neither of those things works. The sens command returns an error message:

Error for wireless request "Set Sensitivity" (8B08) :
    SET failed on device wlan0 ; Operation not supported.

And the power off command doesn't have any discernible effect at all.

---

### Post by uncaspi on 2010-12-02
Then your driver/card don't support sens

The command should cause the card to be more sensitive to weak signals from AP.

---

### Post by JonathanCR on 2010-12-03
So is there nothing I can do about it? It seems weird that Windows has no problem whatsoever with this, whereas Ubuntu really struggles; and also that, with Ubuntu, when I *do* finally manage to connect, there is no problem either. It doesn't drop the signal once it's got the connection.

---

