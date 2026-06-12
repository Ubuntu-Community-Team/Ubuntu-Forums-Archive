---
title: "A complicated question"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by KFwLsKvVAs on 2010-10-09
Hello,

So here's what you have to know before I can ask the question:  

I have a laptop and 2 desktops all running ubuntu 10.04.  The desktops are slower than sh|t and i've already upgraded their memory to the highest that they'll take, they're just really old.  The laptop is super fast and amazing.  

The question: Is there any way to use the operating system of my laptop from either one or both of the 2 desktops?  I know how to connect to my laptop from the desktop over ethernet, and once i accidentally logged in to my laptop from a desktop in the terminal, then forgot i was logged in to the laptop and entered sudo reboot and rebooted my laptop, but i'm not trying to browse it, i want to use the video of the laptop over the ethernet to the desktop, and use the desktop's video to be a second monitor, and be able to use the mouse and keyboard of either to input.  Or somehow tie them all in together and combine all their memory to running a single operating system somehow?  

I don't exactly know where to post this thread so I guessed networking is the closest fit.

---

### Post by GregBrannon on 2010-10-09
I think what you're asking is not exactly possible, but I could be wrong.  Some variation of what you have in mind might improve the performance of your laptops, like running complex applications on your desktop across the network for display on your laptops.

Even better, I suggest you optimize the laptop OSes for the laptops' capabilities.  I suspect you're asking the laptops to do more than they can.  You might try posting the laptop specs for suggestions on appropriate OSes to run on them.

Either way, good luck!

---

### Post by SeijiSensei on 2010-10-09
It's fairly easy to run applications on one machine and display them on another.  That's what X-Windows was designed to do.  So you could, from the desktop, use the command "ssh -X laptop-name" to open an SSH session on the laptop, then run Firefox on the laptop from the command prompt in the SSH session.  The application will run on the laptop, but it will be displayed on the desktop.

If the remote host complains that it can't write to the display, you'll need to grant it permission by typing "xhost +" in the terminal before running "ssh -X".

---

### Post by KFwLsKvVAs on 2010-10-09
ah thank you, this is exactly what i was trying to do.  much appreciation.

---

