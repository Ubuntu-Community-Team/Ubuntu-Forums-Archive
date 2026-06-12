---
title: "Intrepid Ibex 8.10 Wireless Problems"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by Antibuntu on 2008-12-10
Just to start, I don't know anything about Ubuntu, I'm the biggest noob you will ever see. 

Now, the problem. I used Wubi to install Ubuntu 8.10 (my friend told me to) and now I'm stuck. I can't access the internet or anything.

I have a Santis Wlan Siemens USB adapter and I have the Windows driver CD for it. I don't know how to install the driver or set up a wireless network. I have all my network info, so I can use that if you tell me where to put it all.

Please, I need help, a lot of it. I'm feeling so down. Finally, after countless attempts to install Ubuntu it works!... and then I realize I can't do **** with it.

---

### Post by clekstro on 2008-12-10
Let's see what we can work out.  I'm no linux pro, but if the program "ndiswrapper" works here, it should be a piece of cake.

Normally, to install system software (or linux drivers) you would navigate to system > administration > synaptic package manager.  Insert the install cd and search within synaptic for "ndiswrapper."  This program allows you to use your windows driver under linux.  

To install click the square to mark for installation, then click the green apply arrow.

Once installed, remove the cd and insert the windows driver cd.  You will have to use the command line to install the *.inf file located in one of the windows folders.  I would recommend the XP .inf file if you've got it.  

Installing the driver should not be too problematic.  Open up a terminal: Applications > Accessories > Terminal.  type the command *ndiswrapper*.  This should list the command options, just in case I mess this up.  Navigate to the path of the inf file you're wanting to install with the 'cd' command followed by the path, for example:

*cd /media/cd0* if this is where the driver cd files are located

To simplify this, you could also just insert the disk, and, when prompted, use the file manager to find the .inf file, copy it to the desktop and 'cd' into the desktop path with *cd Desktop* .  

Either way will work.

Now back to the terminal: *ndiswrapper -i filename.inf*  If it complains about not having the necessary permissions, then preface the command above with *sudo* to grant yourself root/administrator rights.  It should install without problem.

With root permissions, I believe you must now activate the wireless module with the modprobe command:

*sudo modprobe ndiswrapper*

Check and see in the top right corner, in the network manager applet, if you can see wireless networks.  If so, enter your details and try to connect.  I'll be crossing my fingers for you.  If you need some more help, just ask.

Also, as a matter of courtesy, read up a little before asking questions.  The search function of the forums ensure that questions are answered, and while I'm happy to help someone just starting out, the information I've given is not a voodoo recipe, but the result of my own googling and forum-scouring.  Welcome to the Community!

---

