---
title: "Maverick wireless issue"
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by davepoth on 2010-09-05
At least I think it is. Wireless stopped working about two hours ago, and it's taken me this long to find the router with a bit of cat5 in our holiday let!

Any hints as to what I should be looking for? any known issues?

---

### Post by cariboo on 2010-09-05
It would help if you let us know what type of wireless device you have, make, model and chipset.

---

### Post by perspectoff on 2010-09-05
> **cariboo907 said:**
> It would help if you let us know what type of wireless device you have, make, model and chipset.

There are many, many threads about wireless issues and Network Manager on Lucid, and the same problem has been around forever.

In each version of Ubuntu, Network Manager gets closer and closer to working reliably for wireless, but never works 100% and I always have the same problems you are having. I have tried it in every release, and in every release (including Lucid) I remove Network Manager and go back to Wicd. I don't particularly see why the problem would have gone away in Maverick.

Take my advice, friend, and do the same.

 sudo apt-get remove network-manager network-manager-gnome
 sudo reboot
 sudo apt-get autoremove

 sudo apt-get install wicd
 sudo reboot

Be happy!

---

### Post by cariboo on 2010-09-05
> **perspectoff said:**
> There are many, many threads about wireless issues and Network Manager on Lucid, and the same problem has been around forever.

In each version of Ubuntu, Network Manager gets closer and closer to working reliably for wireless, but never works 100% and I always have the same problems you are having. I have tried it in every release, and in every release (including Lucid) I remove Network Manager and go back to Wicd. I don't particularly see why the problem would have gone away in Maverick.

Take my advice, friend, and do the same.

 sudo apt-get remove network-manager network-manager-gnome
 sudo reboot
 sudo apt-get autoremove

 sudo apt-get install wicd
 sudo reboot

Be happy!

Removing Network-Manager and replacing it with wicd is not a solution for some of us, while all of my wireless devices work quite well with network-manager they don't work properly with wicd. This includes a Prism chipset, a Broadcom chipset, a Ralink chipset and a windows only that  needs ndiswrapper and a 32-bit version.

My purpose in asking about hardware, is that in order to solve a problem, we need as much information as possible. Just saying it doesn't work is no help to anyone.

---

### Post by perspectoff on 2010-09-05
> **cariboo907 said:**
> Removing Network-Manager and replacing it with wicd is not a solution for some of us, while all of my wireless devices work quite well with network-manager they don't work properly with wicd. This includes a Prism chipset, a Broadcom chipset, a Ralink chipset and a windows only that  needs ndiswrapper and a 32-bit version.

My purpose in asking about hardware, is that in order to solve a problem, we need as much information as possible. Just saying it doesn't work is no help to anyone.

Ah, but if his hardware works with Wicd and not Network-Manager, why should he stick with Network Manager and then spend weeks or months trying to find out why Network Manager doesn't work?

---

### Post by cariboo on 2010-09-05
We're here to help the op solve his problem, not argue which is better. It may be something simple that he is missing.

---

### Post by ktp on 2010-09-05
ah, how do you know his hardware, which we don't know yet, works with Wicd?  It might work with Wicd, which would be useful information, but it might not.

Since this is beta where we want to find issues and report them...and hopefully get it fixed and since network-manager is default, I think it be more useful to find out what is going on and write up a bug with as much information we can find.

---

### Post by coffeecat on 2010-09-05
> **perspectoff said:**
> Take my advice, friend, and do the same.

 sudo apt-get remove network-manager network-manager-gnome
 sudo reboot
 sudo apt-get autoremove

 sudo apt-get install wicd
 sudo reboot

I really find this sort of proselytising advice tiresome. Network manager works well for me on several machines with several different wireless chipsets. And, despite all those alleged threads, I'm sure NM works for most people. Just because wicd works for your setup doesn't justify generalising from the particular. And telling someone to install wicd before finding out what hardware they have is presumptious - in my view.

And what all the evangelical wicd-fans seem to forget is that if you install wicd and you change your mind, it's an eye-watering exercise to get network manager back again. I know. I went down this path in Karmic when I had problems with an Atheros wireless chipset. I was fool enough to believe that wicd might help. It was a horrible experience and it didn't solve my flaky connection. Never again. And, of course, in my case it was a driver issue which was quickly and easily fixed with a backports package. After which Network Manager worked just fine. And has continued to do so in Lucid and in Maverick.

---

### Post by tjeremiah on 2010-09-05
the only problem I have and its been present since I first started using ubuntu (8.04) is how slow sometimes it takes Ubuntu on startup to connect to my wireless HIDDEN network. And then sometimes. when it does finally connect, some pages take up to two minutes to load. I tried disabling IPv6 everything suggested during the Lucid testing days too. Though I have noticed the "two minute stall" issue isnt as high as it was in the past, the Ubuntu wireless still takes forever to connect to my hidden network on start up.

---

### Post by cariboo on 2010-09-05
Hiding the essid only slows done the determined cracker. Hiding the essid is only meant to stop casual users from connecting to your access point. How long does it take to connect if you don't have it hidden?

---

### Post by xebian on 2010-09-05
> **cariboo907 said:**
> Hiding the essid only slows done the determined cracker. Hiding the essid is only meant to stop casual users from connecting to your access point. How long does it take to connect if you don't have it hidden?

Are you trying to be funny?:lolflag:

---

### Post by cariboo on 2010-09-06
> **xebian said:**
> Are you trying to be funny?:lolflag:

I take it you've never played with airmon-ng. :)

---

