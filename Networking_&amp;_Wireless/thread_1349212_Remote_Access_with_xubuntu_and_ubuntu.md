---
title: "Remote Access with xubuntu and ubuntu"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by Alasta on 2009-12-08
Hello ,everyone I have searched around for this , but with no joy so far . I have two PCs in my living room ,One p4 Gb ram running 9.10 Ubuntu . The other I want to use to play music through my nice stereo .This PC is running Xubuntu 9.10 ( p 3 600 256 mb ram  ) This is fine for running spotify and playing back music , and is connected to my wi fi router with a cable . What would be cool would be to control the Xubuntu PC remotely from the main PC , eventually with a view to doing away with the monitor on the second PC .

Thank you in advance 


Alastair

---

### Post by spydeyrch on 2009-12-08
Well, to get what you are looking for, it is going to be kind of 3 steps. You need to configure your ubuntu machine to do RDP (remote desktop protocol), you need to fingure your xubuntu machine to accept rdp requests, and you need to configure your router to forward the requests. Once you get those things step up, then you can get rid of the second monitor, the one on your xubuntu machine, and just run everything through your ubuntu machine. The one issue that I can potentially see, is that your xubuntu machine might get bogged down running RDP, especially with only 256 megs of ram. But I am not too shure because I have never run it with so little ram. I always try to have at least 2 gigs in my machines. But hey, you can always give it a try, right! :-)
 
If you would like a more detailed step-by-step process, let me know and I will see if I can walk you through it. I do it all the time on my windows machines, and sometimes from my ubuntu machine to my windows machine but I haven't tried it going from linux to linux. The principle is the same so it shouldn't be that difficult. Let me know.
 
-Spydey :p

---

### Post by gradinaruvasile on 2009-12-08
Linux (and thus Ubuntu) do not support RDP (server, it has many clients for it). The RDP server is Windows-only technology.

What Ubuntu (Gnome actually) has is a server VNC built in (called vino).
The normal (Gnome) Ubuntu has it and you are a few clicks away from sharing your desktop.

But the problem is that Xubuntu doesnt have this preinstalled.  You can install it but it will bring lots of unneeded packages and can be a problem if you are low in RAM. On top of these issues vino is not optimized at all and can be heavy on the CPU.
This would be the simplest thing but:
You MUST log in graphically before the server starts. Meaning you need keyboard/Display. If you leave it permanently running you can remove these.


One (advanced) solution is to log in remotely via ssh(ssh -X user@ip) with the -X switch. Ssh is the Linux equivalent (sort of) RDP. 
This way you can run programs from the remote machine on your X server.
Ex: You log in (in a terminal), type nautilus and the window (the file browser) that opens is run by YOUR X server not the target machine's. But everything you do affects only the remote machine.

If you are using only some applications i would say the ssh way is the most efficient one. Ssh runs low on resources and its very stable, its one core Linux application used on every server. You dont even need a running X server (graphical interface) on the remote machine (but it must be installed to load some needed libraries).
But needs some expertise (in this case really not that much) in terminal commands. Its essential that you know the program name you want to run basically. If you are willing to learn, try it.
Ex:
open a terminal in your box.
log in on the remote computer:

ssh -X user@ip

After giving password, the terminal will be a gateway to the other computer.
You want to launch some program from the remote box, just type its name in the terminal such as firefox for Firefox browser etc. and press enter. Also if you use a program that has icon in the systray, the icon will show up in your computers systray.

---

### Post by Alasta on 2009-12-11
Thank you for that , I will have an experiment this weekend , I think

---

### Post by Alasta on 2009-12-31
Well I am cooking with gas here now . I installed debian on the p3 600 and it came with the vnc program . I am able to log in to this PC start spotify and select tracks .My next project is a music PC in the kitchen :guitar:

---

