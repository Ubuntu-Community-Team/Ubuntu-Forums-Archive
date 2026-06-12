---
title: "Ubuntu failing to start after ATI driver install"
date: 2010-03-15
forum: Multimedia Software
---

### Post by Arcticfrost on 2010-03-15
I'm new to the forms so I'm not sure this has been asked before, if it has a link to the thread would be very much appreciated since I can't seem to find anything on the subject by searching. 

Anyway, I recently installed Ubuntu 9.1 on my computer but I am having trouble with my ATI driver and now after installing the driver when I go to boot Ubuntu it begins to boot with the white Ubuntu logo displayed but then the screen just goes blank, which I an assuming is now really at the login screen but just isn't being displayed.

Now I think it's something that I did while installing the driver.
(I'm using an ATI radeon HD 5770 graphics card and I was attempting to install catalysis control center 10.2 btw)

I don't have a copy of the terminal commands so this is to my knowledge what I did.

First I logged on as super user
located the driver installer on my computer
then I ran the command: 
sh ./ati-driver-installer-10-2-x86.x86_64.run 
At which point the installer started and I went through the install procedure and at the end the installer said that the installation was complete.
Now here's where I might have messed up, at the end of the installer I couldn't quite figure out what I should do next but it sounded like I should run aticonfig in the terminal, which I did after exiting the installer at which point I got a very large body of text in the terminal which look like the computer configuring it self, after this I then closed the terminal and rebooted where it then failed to start like I described earlier.

Now upon further inspection of the instructions ATI included, which I suppose I should have read from the get go, that after the installer finished I should run the command: 
/usr/bin/aticonfig --initial 
assuming I have a version of X.Org newer than 7. 

So my question is, is this where I went wrong and how I would I go about getting ubuntu to boot properly again?

---

### Post by Mark Phelps on 2010-03-16
It's not an Ubuntu boot problem; it's an ATI driver problem.

Presuming you want to get back into Ubuntu first, and fix the video driver problems later, your best choice for now would be to remove the ATI drivers and replace them with the open source drivers.

See the link below for details:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

