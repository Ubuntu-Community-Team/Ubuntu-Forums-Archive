---
title: "Eth0 mount failed after update"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by Luc Verbeurgt on 2010-05-16
I am a brandnew linux user.

I installed the Ubuntu Desktop 10.4 on my new MacBook Pro under a Parallels Desktop (VM).
The install wend fine and after rebooting I was a happy new Ubuntu user.
Had to reconfigure the ethernet port of my virtual machine and I had internet access.

After 5 minutes, Ubuntu displayed a message that there were updates available, which I ran successfully.

After the reboot however I got the following message :
"An error occurred while mounting /media/psf
Press S to skip mounting or M for manual recovery"

After pressing M, a maintenance shell started under "root@ubuntu".
As new user, I did not want to mess around as root (I would know what to enter).
So I pressed ctrl-D which brought me back to the above message and I typed S.

Ubuntu started ok however I lost my eth0 interface.
In the network tools, I only find the Loopback interface, no eth0 anymore.

Do I have to reinstall from scratch ?

LucV

---

### Post by MvdH73 on 2010-05-18
I am having the exact same message, since I upgraded to the new Ubuntu version.
I have a Macbook, use Mac OS 10.5.8, and run Ubuntu in a virtual machine using Parallels.
If I ignore the message (and skip mounting), I can still use my Ubuntu VM, but I would like to know what is wrong and how to resolve it.

---

### Post by czw on 2010-05-29
I had the very same problem. The solution is to reinstall the Parallels tools. You will probably have to do this every time that a package prefixed with "linux-" is installed. Do NOT select the "Upgrade" option. Remove the driver, reboot and install it again.

---

### Post by harpazo on 2010-06-16
Solved:

I had the same problem after an update.  Parallels tools has to be reinstalled. 
To do that here's what I did:

Start Ubuntu.  When the error message is displayed "error mounting /media/psf" click "S" to skip
and Ubuntu will mount with no network connection.

On your Mac desktop, click on the "Virtual Machine" link for parallels desktop at the top of the page, then select either "Install Parallels Tools" or "Re-install Parallels Tools" from the menu.  This will mount the Parallels Tools in Ubuntu as a CD.  (showed up on my Ubuntu desktop).

I then opened a terminal and typed the command "sudo nautilus" - when Nautilus started I clicked on the Parallels CD on the left menu and browsed the contents, then clicked on the "Install" document.  Then followed the prompts, and rebooted Ubuntu after the install completed. 

Hope this helps
Harpazo

---

### Post by MvdH73 on 2010-06-24
Thanks, Harpazo! That did the trick for me.

---

### Post by ketzerato on 2010-07-15
After having succesfully installed through Parallels 5 (on Snow Leopard 10.6.4) Ubuntu 10.4 Lucid Lynx installation, with network-sound-visual capabilities running ok, on my
  Model Name:	MacBook
  Model Identifier:	MacBook4,1
  Processor Name:	Intel Core 2 Duo
  Processor Speed:	2.4 GHz
  Number Of Processors:	1
  Total Number Of Cores:	2
  L2 Cache:	3 MB
  Memory:	2 GB
  Bus Speed:	800 MHz
  Boot ROM Version:	MB41.00C1.B00
  SMC Version (system):	1.31f0
  Serial Number (system):	XXXXXXXXXXX
  Hardware UUID:	XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXX
  Sudden Motion Sensor:
  State:	Enabled

After having latter updated all Ubuntu softwaware through Ubuntu Update Manager;. After having lost all network capabilities. And after having lost all hope on installing Parallels Tools, i came to restore Parallels virtual drivers by doing it so:

1) I went to System > Administration > Hardware drivers

2) I selected "Parallels virtual network driver" and it said "The driver is active but is not in use"

3) I deactivated it with "Deactivate" button (now it said "The driver is not active")

4) I re-activated the "Parallels virtual network driver" with former "Deactivate" and latter "Activate" button

5) And there you go! Network connection came back.

6) Take also steps 1-5 for "Parallels toolgate driver"

Hope it's of use


PS Bad news is i can't make it to be permament. I have to do it all over again every time i start ubuntu...any idea how to fix this?

---

### Post by Andrea Bernasconi DG on 2010-08-03
I upgraded to Ubuntu 10.10 under Mac OS X 10.6.4 and Parallel 5.
At boot I have the message "An error occurred while mounting /media/psf" and I type S.
Then under Ubuntu I do not see Mac OS file system.

Any suggestion?

---

### Post by Charpkun on 2010-12-12
I've encounter a very similar problem going from 10.04 to 10.10. However, unlike other users, I have been unable to boot into the UI after skipping the mount. I just end up with a shell prompt. Is there a way to reinstall the parallels tools drivers from the shell prompt? And will this resolve the issue for certain? I've been stuck at his problem for a few days now. Thanks in advance for the help

---

### Post by Charpkun on 2010-12-12
> **Charpkun said:**
> I've encounter a very similar problem going from 10.04 to 10.10. However, unlike other users, I have been unable to boot into the UI after skipping the mount. I just end up with a shell prompt. Is there a way to reinstall the parallels tools drivers from the shell prompt? And will this resolve the issue for certain? I've been stuck at his problem for a few days now. Thanks in advance for the help

Here's a link to the original thread I created asking for help. It contains some screenshots that may be helpful.
[http://askubuntu.com/questions/17044/upgrading-to-10-10-causes-mountall-error-in-parallels](http://askubuntu.com/questions/17044/upgrading-to-10-10-causes-mountall-error-in-parallels)

---

### Post by wilsonpenha on 2011-02-17
Hi,

I just got this same problem, 

yesterday I had a ubuntu regular updates, bcz I was working on something I did not restart my machine as requested by ubuntu, then today when I turned it on, it won't load my network connection and after a hour of the investigation I found that the update did delete my adapter eth0 from the /etc/network/interfaces,

So I just add it again like this:

root@hwork-lnx:/etc/network# vi interfaces 
auto eth0
iface eth0 inet dhcp
auto lo
iface lo inet loopback

save it, then do that :

root@hwork-lnx:/etc/network# ip addr flush eth0
root@hwork-lnx:/etc/network# ifup eth0

then it start to work again :

It is very sad to have a System that stop to work properly after a simple system update, 

I would ask ubuntu team to better test their new releases before send it to users, 

I could fix it, but I know there are people would before prefer to reinstall it all or even replace it.

Best regards,

Wilson

---

### Post by kmkrause on 2011-08-06
I'm having this problem right now with the added twist of not being able to login to Ubuntu after I press "s" to skip. This is the first time that I am trying to login after upgrading to 10.10. It seems like the upgrade has wiped out my login information?? 

What can I do next?

---

### Post by jrabe01 on 2011-09-02
I have the same problem and am unable to get past the S or M prompt

---

### Post by Rhaurison Bergamin on 2012-01-10
> **jrabe01 said:**
> I have the same problem and am unable to get past the S or M prompt

Remove/comment the following line in /etc/fstab:

#none  /media/psf   prl_fs   sync,nosuid,nodev,noatime,share 0 0

---

