---
title: "poor wifi performance kubuntu 12.10"
date: 2012-11-04
forum: Networking &amp; Wireless
---

### Post by Linux_noob616 on 2012-11-04
i am experiencing terrible ping times (4000ms plus) in large clumps when on wifi on Kubuntu 12.10. I had Ubuntu installed, But i much favor the KDE interface. so i decided to switch to Kubuntu.

But ever since i have had terrible ping times and extremely poor performance on the internet over all. is there something i am missing? I am on an HP G6 if it matters at all.

---

### Post by Linux_noob616 on 2012-11-05
Anyone have any input?

---

### Post by danelwillis on 2012-11-05
try using a different network manager i know KUbuntu uses network manager but try using Wcid network manager

---

### Post by Linux_noob616 on 2012-11-05
trying wcid, still getting rather high pings(200ms) compared to when wired (120ms) but i'm not having random jolts of 4000+ms anymore.

How do i remove my old wireless manager from the panel?

EDIT: I spoke to soon, the second i started surfing the web i got high pings again

---

### Post by danelwillis on 2012-11-05
when you say remove from panel are you on about the panel at the bottom of the screen or the actual linux

---

### Post by Linux_noob616 on 2012-11-05
Panel at the bottom of the screen, But sadly my issue isn't fixed with wcid..

---

### Post by danelwillis on 2012-11-05
well to remove the program sudo apt-get remove <insert network manager here>
and to remove off the panel right click on panel an unlock widgets the right click on network manager an it should say remove from panel

---

### Post by robtygart on 2012-11-05
Is it just with your Kubuntu computer? 

Have you tried resting your modem? Just unplug it for about 30sec and replug.

---

### Post by Linux_noob616 on 2012-11-05
Yes, in Ubuntu it worked just fine, Then i decided i didn't want Unity and wanted KDE instead. So i switched to Kubuntu at the time of the upgrade, i even tried a fresh install to solve it and it didn't help

---

### Post by robtygart on 2012-11-05
No I am talking about a different "Computer". 

With my internet sometimes it bogs down and I will need to unplug the modem/Router and plug it back in, and it gets a better connection. 

Are you running a proxy? 

Settings>NetworkSettings>Proxy (Does it say "No Proxy") 

Did you do your updates? (If my computer is trying to get update information it slows down)
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Linux_noob616 on 2012-11-05
Yes, works great on all my other PC's in the house, and even when my laptop is plugged into the router directly. It's just wifi

And yes i have tried the update and upgrade

---

### Post by VanillaMozilla on 2012-11-05
I would run a trace route to your Web site to see where the bottleneck is.
traceroute6 yourwebsite

Or use Network Tools.

---

### Post by Linux_noob616 on 2012-11-06
Correct me if i am wrong, but wouldn't that just troubleshoot my connection? Because it is clearly Kubuntu, if i use Ubuntu on the same machine i get Wifi that doesn't suck. It also works fine on Windows. this is all on the same laptop. and the same network.

Hell, if i bring my laptop to a coffee shop i get better performance on Windows or Ubuntu then Kubuntu.

---

### Post by wildmanne39 on 2012-11-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by VanillaMozilla on 2012-11-07
> **Linux_noob616 said:**
> Correct me if i am wrong, but wouldn't that just troubleshoot my connection?
Your complaint is slow pings.  Traceroute6 troubleshoots pings.  If you want to find out where the bottleneck is, that will do it, even if you think it's the first hop.

It will take a minute to do it, and lots of time arguing in advance whether it will give you useful information.

Oh wait, you're saying the same computer works OK with a wired connection?  Never mind.

---

