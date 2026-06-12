---
title: "No Network Manager"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by timmy_G_da_Man on 2009-01-04
I've recently installed ubuntu on my computer, and for whatever reason, I can't connect to the internet, period.  I looked into all the trouble shooting, yet one problem came up, they all require the network manager, which I don't have. I looked into it, and I don't believe that it installed with the OS. Any suggestions on how I can fix it, or am I going to need to reinstall it?

---

### Post by 2hot6ft2 on 2009-01-04
Up in the right top there should be an applet for the network manager. Right click on it and check the Enable Network for both Networking and Wireless. Or do you not have it?

---

### Post by timmy_G_da_Man on 2009-01-04
As I mentioned, it isn't installed. I looked everywhere, even the packet manager, which said that it wasn't installed, and since I can't get online...

---

### Post by 2hot6ft2 on 2009-01-04
> **timmy_G_da_Man said:**
> As I mentioned, it isn't installed. I looked everywhere, even the packet manager, which said that it wasn't installed, and since I can't get online...
Is it listed in Synaptic?
"network-manager-gnome" if using ubuntu
"network-manager-kde" if using kubuntu

If it's listed in there, whichever one is right for what you're running since you haven't said.
You could do this.
highlight it and select "Mark for Installation"
It may popup a box saying other things are required.
Mark them
Click on File then generate download script and save it somewhere.
Take it on a flash drive or in a shared folder to a pc that is online and double click the script choose "Run in Terminal" (if it's a linux pc) and it will download everything into the location where the script is. That is if it's running linux.

If it's running windows. Double click on it and when it asks what to open it with choose Wordpad NOT Notepad.
Copy the lines and paste them one by one into IE's address bar (See attached pic for more details, ONLY the highlighted part) and hit Enter and it will download that package.

Do that for each item and save them to take back to ubuntu.

Once you download the packages you can go back to
System>Administration>Synaptic Package Manager
Click on File then "Add downloaded Packages"
point it to where the packages are
and it will install them for you.

---

### Post by timmy_G_da_Man on 2009-01-06
It's listed in the add/remove programs, but I couldn't find it in synaptic.

---

### Post by timmy_G_da_Man on 2009-01-06
Well I found a place to download some of the files manually, if I need anymore help I'll ask.

---

