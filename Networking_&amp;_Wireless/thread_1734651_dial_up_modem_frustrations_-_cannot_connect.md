---
title: "dial up modem frustrations - cannot connect"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by TCMGO on 2011-04-20
[FONT=Times New Roman]I am not a geek, but a frustrated newbie, so please bear with my request. I have been working for the last week trying to connect my serial hardware external modem (courier 56K v.everything) within an Ubuntu 10.4 environment. I have asked several questions in the “Absolute Beginner Talk” forum, for which many have tried to help, but am still stumped (I am Linux challenged). I live in the boonies where I am presently forced to use dial up, so this has got to work, else I cannot update Ubuntu or download software. After trying various suggestions, which my very limited Linux skills fail me, I opted for the suggestion that I download gnome-ppp, install and then use it. Seeing how I cannot download it through Synaptic Package Manager (which I was advised to but can’t as it is my Linux computer that I am trying to connect), I downloaded the zipped file (gnome-ppp_0.3.23_Oubuntu2.tar.gz ) to a USB stick, copied it to the home directory and then extracted it, wherein a new directory was created with many files in it. From here I have been unable to install it through the command line (not sure how), nor have I been able, as was suggested, to install it via the Synaptic Package Manager (can’t get it to see the file, not sure how to). I need explicit (Newbie) instructions on how either to connect the modem without gnome-ppp, or instructions on how to get gnome-ppp installed. Please help . . . thank you [/FONT]

---

### Post by prankstar008 on 2011-04-20
I am assuming that your tar.gz contains the source code of gnome-ppp. This is great if you want to build it yourself. However, it would be much easier to install if you had the deb file which, when double clicked, will launch synaptic package manager. From synaptic, you can just click install and everything will be done for you. Try downloading the file below, and I hope it solves your original problem :-)

[http://ubuntu.wikimedia.org/ubuntu//pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb](http://ubuntu.wikimedia.org/ubuntu//pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb)

---

### Post by TCMGO on 2011-04-20
Thank you for replying.  I downloaded the file to my USB stick and then double-clicked it while booted in Ubuntu 10.4, wherein it begian to install gnome-ppp until it hit this message:
 
[COLOR=red]Error: Dependency is no satisfiable: wvdial[/COLOR]
 
Do I need to download or install wvdail first.  
 
How do I remedy this error?
 
Thanks again

---

### Post by prankstar008 on 2011-04-20
I accidentally pasted the link to the Ubuntu 8.04 package.  Try this.

[http://ubuntu.wikimedia.org/ubuntu//pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-1ubuntu2_i386.deb](http://ubuntu.wikimedia.org/ubuntu//pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-1ubuntu2_i386.deb)

---

### Post by TCMGO on 2011-04-20
I downloaded the new package you suggested, copied to the desktop, double clicked it and got the same message:
 
[COLOR=#ff0000]Error: Dependency is no satisfiable: wvdial[/COLOR]

What does this error mean and is thier a fix?  Thank you again for your help

---

### Post by prankstar008 on 2011-04-20
Here is the packages page that shows ALL of the dependencies that gnome-ppp has

[http://packages.ubuntu.com/lucid/net/gnome-ppp](http://packages.ubuntu.com/lucid/net/gnome-ppp)

Meaning, gnome-ppp depends on all the listed packages to be installed (and those packages usually have dependencies of their own :-/). The good news is that when you DO get your internet working, apt-get takes care of all this for you.

Here is another thread that might be of some use.
[http://ubuntuforums.org/archive/index.php/t-1246756.html](http://ubuntuforums.org/archive/index.php/t-1246756.html)

---

### Post by _duncan_ on 2011-04-21
@ TCMGO

I stopped testing dial-up 3-4 releases ago, so take my advice with the proverbial grain of salt:

1. The only way to get on-line from a fresh Ubuntu install without downloading additional stuff is to configure the PPP daemon using the terminal command pppconfig. You need to execute this with root privileges, hence:```
sudo pppconfig
```

You will be prompted to enter root password, after which you will be greeted with a user interface reminiscent of the old MS-DOS days. If I remember correctly, instructions on how to navigate the menus are included in the first screen, so please read the instructions very carefully before proceeding.

At the end of this exercise, assuming you answered all the connection parameters correctly, you will have a fully-configured PPP daemon.

2. You also need to add you user ID to the 'dip' group:```
sudo adduser <your user ID> dip
``` **You need to log out from your user account and log back in for the changes to take effect.**

3. If steps 1 and 2 are done correctly, you only need to type 'pon' or 'poff' (without the quotes) to connect/disconnect respectively.

4. The command 'plog' (without quotes) will give you a status report of your connection. This is particularly useful when troubleshooting whether the parameters entered in step 1 are correct.

5. After achieving initial connection, you need to update the package list to download stuff from the ubuntu repositories. This can be done using synaptic package manager, but can also be done using the terminal:```
sudo apt-get update
```Depending on the version you're using, this step will download approximately 30 MBs worth of info and will take more than an hour on dial-up (more like 2 hours, actually).

6. Now you can download the GUI dialer gnome-ppp, either using synaptic or the terminal:```
sudo apt-get install gnome-ppp
``` This will pull in not only gnome-ppp, but also all required dependencies. Be prepared for another long download.

7. Turn off the connection using 'poff'.

8. You should find gnome-ppp in the menus. Not sure about this, but probably Application > Internet > Gnome-PPP. You need to configure this (i.e. enter connection parameters) before making your first GUI dial-up connection.


P.S. Doing this from rote memory so there are bound to be some inaccuracies in the instructions.

---

