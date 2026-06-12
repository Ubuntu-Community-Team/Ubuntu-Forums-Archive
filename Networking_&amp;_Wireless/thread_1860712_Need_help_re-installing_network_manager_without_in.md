---
title: "Need help re-installing network manager without internet (dual boot with vista)"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by scot^2 on 2011-10-15
I am running Ubuntu 11.04 on a dual boot with Vista.  I accidentally deleted Network Manager, and so I cannot access the internet on Ubuntu.  I do still have access though on Vista.

I see this issue has been discussed before on the forums but none of the solutions could I get to work.

Note that I am new to Ubuntu.

I usually use a public wireless hotspot for internet access.

Network Manager is checked in Start up Applications.  When I click Edit it says nm-applet.

Also, when I first ran Ubuntu I deleted most of the notification area icons because I didn't like or need them.  I think I did this through Synaptic by uninstalling some "indicators".  (I had read about doing it somewhere here if I recall correctly.)

Thanks.

---

### Post by scot^2 on 2011-10-15
One thing I tried.  I downloaded (through the working internet connection on Vista) NetworkManager-0.9.1.90.tar.xz and network-manager_0.8.4~git.20110319t175609.d14809b-0ubuntu3_i386.deb.

When I then restart the computer and log into Ubuntu I copied these folders and placed them on the Ubuntu desktop.  In each there is a "configure" file.  I can right-click these configure files and choose "Run in terminal".  The terminal appears and runs for a few seconds, then closes.  I can't detect any changes though, i.e., there is still no icon or anything listing available wireless networks, for example.

Thanks again.

---

### Post by ubu_dynamite on 2011-10-15
Could try this
Insert the install CD into a drive and at the prompt, type

Applications -> Accessories -> Terminal

```
sudo apt-cdrom add
```
Gnome
```
sudo apt-get install network-manager-gnome
```
or if you use kde
```
sudo apt-get install network-manager-kde
```

---

### Post by scot^2 on 2011-10-15
Thanks for responding.

Actually, I don't have a cd.  I downloaded/installed Ubuntu online from their homepage.

I use Gnome by the way.

Given that I have those two folders I mentioned on my Ubuntu desktop, can I use a terminal command to access what I need there?

Thanks again.

---

### Post by ubu_dynamite on 2011-10-15
You could try to install the deb with dpkg but you may be missing some dependencies.
Other way you could try is mounting the iso and ad that as repository  in your sources.list.

---

### Post by scot^2 on 2011-10-15
I tried using dpkg (for the first time) and I got an error saying that no such file exists.  Note that I tried it with the .deb extension and without since I'm not sure about the syntax.  Here's a screenshot.  It also shows those desktop folders/files I alluded to.[IMG]http://imageshack.us/photo/my-images/849/screenshoteh.png/][IMG]http://img849.imageshack.us/img849/4360/screenshoteh.th.png[/IMG][IMG]http://imageshack.us/photo/my-images/849/screenshoteh.png[/IMG][[img=http://img849.imageshack.us/img849/4360/screenshoteh.th.png]](http://imageshack.us/photo/my-images/849/screenshoteh.png/)

Can you give a step-by-step on how to add the .iso as a repository?  I am assuming you mean the original Ubuntu installation file which I have mounted on the desktop (in the screenshot).  Synaptic only allows you to add from a CD or certain places on the internet from what I can tell.

---

### Post by scot^2 on 2011-10-23
I never solved the original issue.  I decided to let it go and uninstall Ubuntu 11.04.  I am now trying 11.10.

Thanks anyway.

---

