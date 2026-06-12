---
title: "Flash does not work - 12.04"
date: 2012-10-21
forum: Multimedia Software
---

### Post by paranat on 2012-10-21
Hello!

Originally I had several Internet/performance problems which I described in [this thread]("http://ubuntuforums.org/showthread.php?t=2071761"). Now all the other ones are solved, but the issue with Flash remains, and I thought it is more convenient to start a new thread in the appropriate subforum. With the search function I didn't find any other description of this.

So, I have a problem with Flash videos, such as in Youtube, despite having the correct plugins. The flash screen doesn't appear at all, while at the same time the computer seems to be working heavily. Below is a screenshot and a more detailed description. I have tried different browsers to no effect. Also I remember trying the open source flash plugins, which worked neither.

I will quote the relevant posts from the previous thread.

[QUOTE="paranat"]


---
                                                                                  Quote:
                                                                      Originally Posted by **mikewhatever**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12306995#post12306995")                 
                 [SIZE=2][I]"... ...
PS: Which model of Nvidia graphics card is there?

As for flash, first, it doesn't have hardware acceleration on Linux, but  even if it did, it wouldn't apply to old hardware. Troubleshooting  flash sound also seems irrelevant, unless of cause, there are sound  problems. Try turning off Transmission, as it can use a lot of  bandwidth, and thus interfe with streaming videos.
PS: To find flash settings, right click inside a flash video window.[/I]"[/SIZE]
---
                                 
I installed the Lubuntu desktop and switched it on from the login  window. It's much better now, nearly no lag at all. General sluggishness  solved!

Now the only remaining problem is with flash. I'm using a Geforce 6600  GT graphics card. It's rather old - bought some seven years ago, I  think. Flash doesn't work even when Transmission is off. The problem  clearly has nothing to do with bandwidth.

Here's how it looks when I try to load a Youtube video:

[IMG]http://ubuntuone.com/59Efaz1bSY9bZxGVea9HdS[/IMG]

This is all that happens. As you can see, there's no "loading" type of  message at the bottom of the browser screen. However, the computer seems  to be doing something all the time when on the page (the memory keeps  making its sounds and the system slows down). There seems to be no flash  window at all at the blank spot, since no menu appears when  right-clicking on it.

Edit:
To clarify, the package that I have installed is  "ubuntu-restricted-extras", since I'm using a 32-bit system. I also  tried "flashplugin-installer", but there was no difference.                                                                                                           

[/QUOTE]

[QUOTE="steeldriver"]
Hmmm... that's not a flashblock plugin icon at the top right of your  browser window by any chance?

Another thought is you might want to see if there's a specific  lubuntu-extras - I seem to remember it making a difference on Xubuntu  whether I chose xubuntu-extras or plain ubuntu-extras (I don't remember  the details sorry - just a note in the back of my mind)
[/QUOTE]

The icon is for a plugin called Flash-aid. It's supposed to solve conflicting flash plugin installations. I tried it to no effect.

I installed lubuntu-restricted-extras, which made no difference.

I also installed [this]("http://ubuntuforums.org/showthread.php?t=766683") collection of packages and rebooted, which also made no difference.

---

### Post by goldshirt9 on 2012-10-21
I had a similar issue with Kubuntu.
couldn't play flash video and any quick time video's.
gave up and re installed Ubuntu.
I know that's no help but
I believe flash is being or has been pulled for Firefox / the latest android "jellybean"

have you tried chrome as i believe that has flash built in.:confused:

wish i could help more :(
best of luck. :KS

---

### Post by claracc on 2012-10-21
What adobe flashplayer plugin release have you installed?

---

### Post by paranat on 2012-10-21
> **claracc said:**
> What adobe flashplayer plugin release have you installed?

I have the package "flashplugin-installer" version "11.2.202.243ubuntu0.12.04.1".

I also have installed the latest version of lubuntu-restricted-extras and ubuntu-restricted-extras. I already tried removing all but lubuntu-restricted extras in order to remove conflicts, but it made no difference.

[QUOTE="goldshirt9"]I had a similar issue with Kubuntu.
couldn't play flash video and any quick time video's.
gave up and re installed Ubuntu.
I know that's no help but
I believe flash is being or has been pulled for Firefox / the latest android "jellybean"

have you tried chrome as i believe that has flash built in.:confused:

wish i could help more :sad:
best of luck. :KS[/QUOTE]

I just installed Lubuntu desktop on Ubuntu 12.04 in order to make my system faster... :) The same Flash problem was in Unity desktop.

I tried Chrome and Chromium. Now there appears a Flash window and the computer does not work endlessly, but in the Flash window it says "Plugin download failed" and in the upper edge of the browser window "Plugin Shockwave Flash could not be downloaded".

[IMG]http://ubuntuone.com/3BMPX8DwAR5z561eMuln3C[/IMG]

---

### Post by claracc on 2012-10-21
As you have the lovinglinux addon flash-aid, I will try to install an older flash player plugin, I would say [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip), through the custom way of flas-aid.

As your graphics card is old, perhaps, it doesn't support the flash player plugin 11.2 series but the previous one 11.1.102.63.

Be aware that you are assuming security risks running old flash player plugins.

---

### Post by paranat on 2012-10-25
> **claracc said:**
> As you have the lovinglinux addon flash-aid, I will try to install an older flash player plugin, I would say [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip), through the custom way of flas-aid.

As your graphics card is old, perhaps, it doesn't support the flash player plugin 11.2 series but the previous one 11.1.102.63.

Be aware that you are assuming security risks running old flash player plugins.

!!!

!!!

It worked!

I would have never believed! :) Thank you! Now I must be careful not to update it!

All three of my original problems are now solved! Wonderful! Imagine -- I beared with these problems for 8 months until I bothered to ask for help here, and now within a few days everything is fixed!

---

### Post by claracc on 2012-10-25
You are welcome.

Glad you got fixed your problem.

---

### Post by raydar on 2012-11-16
Thank you, claracc!

I had this same problem in Ubuntu 12.04 on a 32-bit machine with an ATI RV280 [Radeon 9200 PRO] where the flash plugin version 11.2 wouldn't work, but reverting to version 11.1 fixed the problem.

(FYI, a similar thread: [http://ubuntuforums.org/showthread.php?p=12358003#post12358003](http://ubuntuforums.org/showthread.php?p=12358003#post12358003) )

---

### Post by claracc on 2012-11-16
You are very welcome.

---

### Post by LUCASBSTANLEY on 2013-11-09
how can i do this without flash-aid

---

