---
title: "Ndiswrapper error after upgrade"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by ckuter on 2012-09-07
In am using Ubuntu 12.04 on an old Compaq Presario 2108CL laptop.  I use a Trendnet tew-421pc pcmcia style wireless card.  I successfully installed ndiswrapper and the Mrv8000c.INF windows driver.  The wireless access to the internet worked fine.  After an upgrade, neither light on the pcmcia card would light up and I could not access the net.  

I get the following responses from the terminal mode:  

calvin@calvin-Presario-2100-PF879UA:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
mrv8000c : driver installed
	device (11AB:1FAA) present
calvin@calvin-Presario-2100-PF879UA:~$ ls /etc/ndiswrapper
mrv8000c
calvin@calvin-Presario-2100-PF879UA:~$ ls /etc/ndiswrapper/mrv8000c
11AB:1FAA.5.conf  mrv8000c.inf  mrv8000c.sys
calvin@calvin-Presario-2100-PF879UA:~$ sudo depmod -a
calvin@calvin-Presario-2100-PF879UA:~$ sudo modprobe ndiswrapper 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

How do I prevent the WARNING items from occurring on my next upgrade?

---

### Post by chili555 on 2012-09-09
I'm not sure I understand your question. Is your issue that your wireless isn't working now or is your issue that you get a mostly harmless warning? Let's fix the warning:```
sudo mv  /etc/modprobe.d/ndiswrapper  /etc/modprobe.d/ndiswrapper.conf
``` Is your wireless working correctly?

---

### Post by ckuter on 2012-09-09
I was not working until I reinstalled it via terminal commands.  I want to fix it so I do not have to do this after upgrades.  The linux computer is not at the house now, and I will try you commands when I get it back. 

Thanks

---

### Post by chili555 on 2012-09-09
> **ckuter said:**
> I was not working until I reinstalled it via terminal commands.  I want to fix it so I do not have to do this after upgrades.  The linux computer is not at the house now, and I will try you commands when I get it back. 

ThanksIf it's not working perfectly, post back and we'll be glad to help you.

---

### Post by ckuter on 2012-09-23
UPgraded the again today and wifi quit working.  Go it working again, but it should not disappear after an upgrade.
I tried your mv command without success.  The computer did not see the pcmcia wifi card ( no blinking light ).  I got it to work again after following Step 5 in the WifiDocs/Device/RENDnet_tew-421pc_H/W:B1_(ndiswrapper).  When I followed Step 6, it disappeared again.  Went back to step 5 and it works.

What sceen shots do you need?

---

### Post by chili555 on 2012-09-23
The document you followed suggests using a compiled from source code version of ndiswrapper. That's the nature of compiled software; it is compiled only for your current kernel. You could try, instead, the Ubuntu version. What is your preference?

---

### Post by ckuter on 2012-09-23
My preference is the longer last type, so I guess it is the Ubuntu version.  I assume I get that via Synoptic Pakcage Manager.  What if anything must I do to un-do the version I have installed?

Thanks.  Obviously I am not an experienced Ubuntu user.

---

### Post by chili555 on 2012-09-23
> What if anything must I do to un-do the version I have installed?Please do:```
cd ndiswrapper-1.29
sudo su
make uninstall
apt-get install ndiswrapper-common
apt-get install ndiswrapper-dkms
apt-get install ndiswrapper-utils-1.9
modprobe -r ndiswrpaaer
modprobe ndiswrapper
echo ndiswrapper > etc/modules
exit
```Is it working now? Any errors or warnings?

---

### Post by ckuter on 2012-09-23
Now it does not work at all.  No lights on the pcmcia card.  I used ndiswrapper throughout. After typing in "echo ndiswrapper > etc/modules", it responded   :  "Bash: etc/modules: No such file or directory"

I confirmed there is no modules directory by using Nautilus.  How do I make this directory?

---

### Post by chili555 on 2012-09-23
You needn't make the directory. You only need correct my regrettable mistake! Sorry about that!```
sudo su  [COLOR="Red"]<--if you are not already[/COLOR]
echo ndiswrapper >[COLOR="Red"]>[/COLOR] [COLOR="Red"]/[/COLOR]etc/modules
exit
```Let's do some diagnostics, please run and post:```
sudo modprobe ndiswrapper
ndiswrapper -l
iwconfig
```Thanks.


____________________________

Note to chili: Preview Post!

---

### Post by ckuter on 2012-09-23
sudo modprobe ndiswrapper   
>>> nothing appeared on the terminal after that

ndiswrapper -l
>>> The program 'ndiswrapper' is currently not installed.  You can install it by typing:  sudo apt-get install ndiswrapper-common
calvin@calvin-Presario-2100-PF879UA:~$ 

OK I then typed in  sudo apt-get install ndiswrapper-common and got this

calvin@calvin-Presario-2100-PF879UA:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
calvin@calvin-Presario-2100-PF879UA:~$ 

iwconfig
>>>  calvin@calvin-Presario-2100-PF879UA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

calvin@calvin-Presario-2100-PF879UA:~$ 


This is where I started.  Any thoughts?

---

### Post by chili555 on 2012-09-23
Please confirm that you installed without error or warning ndiswrapper-dkms and ndiswrapper-utils-1.9 as above.

This is a bit mysterious!

---

### Post by ckuter on 2012-09-23
It seems to be working now.  In between messages, I went into Synaptic Package Manager and reinstalled the 3 ndiswrapper files.  Wifi is working, but there is some kind of problem with ndisgtk that I am not going to worry about.

Thanks for taking time out of your day for helping me.  I learned the difference between compiling for a one shot deal versus using a longer term approach.

---

### Post by chili555 on 2012-09-23
> Thanks for taking time out of your day for helping me. My pleasure. I enjoy it. If you'd like to address the ndisgtk issue, fire away.

---

