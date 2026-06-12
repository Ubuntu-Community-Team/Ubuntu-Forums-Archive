---
title: "Wireless reinstall on a netbook"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by mr best buy on 2011-01-08
I have ubuntu installed on an HP net book.  I was happy.  When I went to applications I clicked on the icon that would search and update drivers.  It tried to update the broadcom driver and failed.  now I have no wireless internet connection.  Is there an easy way to get back like the windows "system restore" or do I have to do a complete system install?
I am new at this stuff.  i can hook up a wired connection and download and reinstall, but is there a better way?:confused:

---

### Post by Bucky Ball on 2011-01-08
Welcome. Plug in an ethernet cable, get online, and try again. You need to be online to activate the wireless card drivers and firmware for Broadcom cards. Then it is easy as a click or two. 

Once online you should be offered updates and you're card may well be picked up and you will be offered drivers and firmware for it also.

You don't need to reinstall, this should be pretty straightforward. Catch 22, though. To use Broadcom, all software available but you need to get online with a cable first. This software can't be included in the install because of legal reasons (third party software).

---

### Post by PatchesTheCaveman on 2011-01-09
There's a bad update floating around that you might have downloaded.  Follow the instructions in this post to check to see if you have it and fix it if you do:
[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5](http://ubuntuforums.org/showpost.php?p=10312711&postcount=5)

---

### Post by Bucky Ball on 2011-01-09
Patches, that is not affecting everyone as you'll find if you look around a bit more. I am running it problem free. The 2.6.35-** kernels are the only one that will run on my machine. The rest break my graphics driver and wireless! 

So, not *everyone* is affected. You might want to contribute your issues with that kernel here:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

;)

---

### Post by PatchesTheCaveman on 2011-01-09
It is affecting many people with Broadcom-based wireless adapters, which he indicated he had.  (It's also affecting wireless adapters with Realtek, Ralink, and Intel chipsets, a laundry list of USB devices, and some Intel graphics and sound chips.)  His post made it sound like he had a working wireless connection till he "updated", which makes that affecting him likely.

I posted in that thread several times, and also compiled a list of hardware reported broken by posters there and filed a bug in Launchpad with that information.  I've updated that bug twice since, thanks to people on this board discovering going back to the previous kernel fixed their problems.

---

### Post by mr best buy on 2011-01-10
Thank you all for the information about the bad update.  Here is what happened.  When I updated my netbook, my wireless quit working and the little wireless indicator light turned orage from blue.  
I tried plugging in the cable and updating the driver.  The message was something like "Archive failure (0) authenticate (or something like that) This was the same message that I got when I updated it using wireless.  Since the wired and wireless connection gave me the same message, I reinstalled from a flash drive after I deleted and reformatted the hard drive. I checked all the options on the install options including download all the updates.
After I finished and rebooted, my orange lite was blue, meaning that the wireless unit was working, but I had no wireless connection.  I had the wireless symbol at the top of the page, with a red line through it.  So I plugged in my linksys usb wireless adaptor and it immediately begin to work.
Since the wireless worked before I attempted the additional driver update, I am sure there is just something else I can configure or something.  But  I am not familiar with where I should go to do it.  I can continue to use the linksys wireless adaptor, but it is unhandy.
Where do I go to see what is wrong.  Something like device manager in MS.
Or should I go to the additional driver install mistake link, even though I reinstalled and have a blue light? 
Or since I reinstalled and have the wireless symbol all I need to do is reconfigure something else, and if so, how?

---

### Post by Candird on 2011-01-10
So actually i have a similar problem, tried to update lost the connection and then came across the problem "firmware missing", problem being i didnt have the option to use a wired connection.
I have at the very least moved past that problem by going through the process of 

Code:
# tar xfvj broadcom-wl-4.150.10.5.tar.bz

# sudo b43-fwcutter -w/lib/firmware wl_apsta-3.130.20.O.o

# sudo b43 fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
(found this fix in the forums btw) 

and then i did a restart.... 
after the restart it was showing that i had wireless capabilities but not letting me connect to any network 
i have since tried (#rfkill unblock all)

with no success

---

### Post by Bucky Ball on 2011-01-10
> **Candird said:**
> So actually i have a similar problem, tried to update lost the connection and then came across the problem "firmware missing", problem being i didnt have the option to use a wired connection.
I have at the very least moved past that problem by going through the process of 

Code:
# tar xfvj broadcom-wl-4.150.10.5.tar.bz

# sudo b43-fwcutter -w/lib/firmware wl_apsta-3.130.20.O.o

# sudo b43 fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
(found this fix in the forums btw) 

and then i did a restart.... 
after the restart it was showing that i had wireless capabilities but not letting me connect to any network 
i have since tried (#rfkill unblock all)

with no success

Please post in a separate thread. You will get specific help for your issue that way and more of it. It is confusing trying to help two users at the same time. You're issue is not the same as this one. You have no wired connection thus your fix is totally different. ;)

I would refer you both to this post where you might like to add your thoughts:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

---

### Post by superdad0128 on 2011-11-13
bucky ball- i have the "device not ready-firmware missing" problem under wireless. im hooked up via ethernet cable, but i am gettin no offers for updates for drivers or anything. i looked in update manager, nothing. i looked in additional drivers, nothing there. now im getting worried, can you help?

---

### Post by superdad0128 on 2011-11-13
do i actually need to reinstall? drivers not being found, no updates, been workin all night with sudos and what-not...im confused...

---

### Post by Bucky Ball on 2011-11-14
This is a very old and rather dead thread. You would be much better off posting a new one with a descriptive title and as much info as you can give about your card. Post the link back here if you like and I'll have a look. In the new post, include the results of:

```
sudo lshw -C network
iwconfig
ifconfig
```In the output of the first command you will find your wireless card under, 'description: Wireless Interface' section. ;)

---

