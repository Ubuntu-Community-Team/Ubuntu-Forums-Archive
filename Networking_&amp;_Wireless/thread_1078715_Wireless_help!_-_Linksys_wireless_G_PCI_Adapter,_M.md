---
title: "Wireless help! - Linksys wireless G PCI Adapter, Model: WMP54G"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by theDuggler on 2009-02-23
I recently partitioned my computer and now have Windows XP and Ubuntu (8.04) on it, but the wireless card doesnt work in Ubuntu (it works fine in windows). (Linksys wireless G PCI Adapter, Model: WMP54G)

I've tried a bunch of things on this forum, including using the ndiswrapper, but nothing has worked yet. With ndiswrapper I couldn't even see the wireless network option, only the wired network option. I removed ndiswrapper and right now, it will show me the available wireless networks that I could potentially connect to, and it tries to connect to something but never succeeds.

I live in an apartment building with only wireless as an option (Airlink101 300N), although I can use a laptop to get wired if necessary. Our wireless is also password encrypted, I'm not sure if that makes it more difficult. 

I am also really unfamiliar with most of ubuntu/this stuff, so the more information and details the better.

I'd really like to use ubuntu, but I need the internet to get my work done as well, so I'm stuck with XP until I can get the card working, so an help would be very appreciated.

---

### Post by Crafty Kisses on 2009-02-23
Hey there my friend! Let's see if we can't get this card up and running with ndiswrapper, you said you already tried ndiswrapper, and made things worse, that's kind of weird, but we will give it another shot, I'll walk you through it step by step. So first you want to navigate to Terminal and run the following command:
```
sudo apt-get install ndiswrapper-common
```
That will install ndiswrapper for you, once ndiswrapper is installed you need to get the XP drivers for your PCI wireless card, which I got them for you, so you can download them right [here.]("ftp://ftp.linksys.com/international/drivers/wmp54g_dr_wiz.zip") Once you have the drivers, extract the file to your desktop, and click the "Drivers" folder, and there should be an .inf file in there, so what you want to do is navigate to that folder via Terminal, so run the following:
```
cd /home/username/Desktop/filename/Drivers
```
I'm just assuming the folder is called "filename" and the folder where the .inf file is, is called "Drivers" remember substitute your own information. Once your in that directory, you want to run the following:
```
sudo ndiswrapper -i <drivername>
```
Where "drivername" is, rename it with the .inf file, once you have done that make sure the driver is installed by running the following:
```
sudo ndiswrapper -l
```
If the drivers are installed correctly, you should get results similar to this:
```
Installed ndis drivers:
{name of driver} driver present, hardware present
```
If you get results like that, the driver install was successful, but you're not quite done yet, you need to make sure the ndiswrapper modules are loaded, so run the following command:
```
sudo modprobe ndiswrapper
```
Once the ndiswrapper modules are loaded, time to get the proper dependencies for the ndiswrapper module, so run the following:
```
sudo depmod -a
```
Once you have done that, you're almost done, make sure the module loads at every start, so run these commands:
```
sudo ndiswrapper -m
sudo ndiswrapper -ma
```
Then once you have done that, reboot by running the following:
```
sudo shutdown -r now
```
Then once you're back into Ubuntu the wireless should work. If you have any problems post back, and I'll help you further.

---

### Post by theDuggler on 2009-02-23
Thanks! I will be trying this later tonight when I get access to a laptop, I'll let you know how it goes. Thanks!!!!!!!!!!!11!

---

### Post by theDuggler on 2009-02-23
Hi, so I'm in the process of trying it again, and I'm stuck on your third command. The first line (sudo apt-get install ndiswrapper-common) seems to work fine and I get

~$ sudo apt-get install ndiswrapper-common
[sudo] password for brenna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.4kB of archives.
After this operation, 94.2kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main ndiswrapper-common 1.50-1ubuntu1 [11.4kB]
Fetched 11.4kB in 45s (252B/s)                                                 
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 113664 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ...
Setting up ndiswrapper-common (1.50-1ubuntu1) ...

but typing in sudo ndiswrapper -i bcmwl5.inf gives 

Error: no ndiswrapper utils found!

I tried restarted to see if that helped. but it didn't, and I really have no idea what else to try.

---

### Post by Crafty Kisses on 2009-02-24
Did you download the driver I gave you in my original post? Then once you have the driver downloaded, save it to your desktop then extract the file on to your desktop, then navigate to it so for example, I'm guessing you extracted the file and it's called "Driver" and inside the Driver folder is another folder called "Drivers", so in order to get to that file, we have to do the following:
```
cd /home/username/Desktop/Driver/Drivers
```
Once you have done that, then run the commands I gave you.

---

### Post by theDuggler on 2009-02-24
Scratch that, I downloaded the utils package too and that seemed to fix that part.

---

### Post by theDuggler on 2009-02-24
I did that, and all the commands seemed to work fine, but the wireless still doesn't seem to work and it seems to be the same problem as before. I can still see the networks but they don't seem to connect

This is some of the output if that helps.

username:~$ sudo ndiswrapper -l
bcmwl5 : driver installed


username:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper

And the others didn't have output.
It looks pretty normal to me, but I also don't know what to expect.

---

### Post by Crafty Kisses on 2009-02-24
Well reboot and see if you can connect.

---

### Post by theDuggler on 2009-02-24
Hey, so I had rebooted twice and had the same problem, but this third reboot seems to have a different problem. The wireless still doesn't work but now while trying to connect I get no green lights whereas before I would get one.

---

### Post by Crafty Kisses on 2009-02-24
Did you load the ndiswrapper modules?
```
sudo modprobe ndiswrapper
```

---

### Post by theDuggler on 2009-02-24
Twice

---

### Post by Crafty Kisses on 2009-02-24
If that doesn't work remove the driver by running the following:
```
ndiswrapper -e <drivername>
```
Then try download this [driver.]("http://www.ralinktech.com.tw/data/drivers/IS_AP_STA_2500_D-3.2.0.10_VA-3.2.0.0_RU-2.1.3.0_VA-2.1.3.0_AU-2.0.3.0_VA-2.0.3.0_021209_1.0.1.0_Free.exe") Once you have the driver downloaded it should be an .exe, then right click on the .exe and select "Extract here". Then use that driver and follow my steps again.

---

### Post by theDuggler on 2009-02-24
I did all of those instructions, and I just tried restarting and typing that (sudo modprobe ndiswrapper) before I connected to wireless and it doesn't seem to change the problem. Also, I'd like to say thanks for sticking with this for so long! I really appreciate it!

---

### Post by Crafty Kisses on 2009-02-24
Did you try the new driver?

---

### Post by theDuggler on 2009-02-24
hey, I just saw what you posted while I posted, and I tried it, but I think I'm getting something weird. 


username:~$ sudo ndiswrapper -e bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory
username:~$ sudo ndiswrapper -l
bcmwl5 : driver installed

and then I tried making sure it wasn't just being in teh wrong directory sort of problem, 

username:~$ cd Desktop/Drivers/Drivers
username:~/Desktop/Drivers/Drivers$ sudo ndiswrapper -e bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory

---

### Post by Crafty Kisses on 2009-02-24
Hmmm, weird then try putting the driver name without the .inf at the end.

---

### Post by theDuggler on 2009-02-24
That seemed to work, and I'm just waiting for the driver to install. it keeps failing, and saying "could not be saved, because the source file could not be read." is that jsut my internet being ridiculous and I should keep retrying?

---

### Post by Crafty Kisses on 2009-02-24
That's really weird, I'll try downloading it and get back to you.

---

### Post by theDuggler on 2009-02-24
Well I think it's just my internet beingn ridiculous, if I keep retrying when it fails it starts up again,a nd this tiem it hasn't failed but it seems like it will be taking a while to finish, so I'm going to bed and I'll retry the process tomorrow night. 

Thank youfor all your help!

---

### Post by theDuggler on 2009-02-24
Hello again,

So i got the .exe you posted above, but i'm not sure how to extract it. Archive Manager does not seem to support .exe, so I googled for a bit and found that some people seemed to be using "cabextract" for extracting .exe's. So, I got this installed, but this tells me

user:~/Desktop$ cabextract Drivers2.exe
Drivers2.exe: no valid cabinets found

(I tried doing this before renaming the driver as well). Is there a different way I should be extracting this file?

---

### Post by Crafty Kisses on 2009-02-24
When you download the .exe you should just be able to right click on it and select "Extract here".

---

### Post by theDuggler on 2009-02-24
I didn't have that as an option, which was why I got cabextract, but that didn't work either.

---

### Post by mudman00 on 2009-05-28
Good moring, afternoon, evening.....I have the installed the latest iteration of Ubuntu, version 9.04....I am not able to use the wireless feature on my aging machine...

I have a Linksys 2.4 ghz PCI Adapter Card, model WMP54G....it is plugged into an ASUS mother board with an AMD chip set if that makes any difference.

When I left click on the connection icon I get a drop down window that has the Auto eth0, VPN Connection, Connect to Hidden Wireless Network and Create New Wireless Network option in bold and active. 

However, I am not seeing, or detecting any wireless networks eventhough my router is about three feet away and I know of several in the immediate vicinity. I am currently running a cable to the machine rather than using wireless but want to it upstairs where there is no phone line...hence the desire for the wireless function.

Do I need to follow the directions that have already been layed out in ths thread? Do I need to down load a driver for the linkys card?

Thank you for any and all help
Craig

---

### Post by Spike1158 on 2009-06-22
Codename, i would hug you and buy you a beer if i knew you personally! I've been running around for the past 2 days trying EVERY method of blacklisting and disabling IPV6 thinking it was my problem. The last thing I was going to try was recompiling the kernel, and i did not want to do that. This was the easiest guide for installing/configuring ndiswrapper out there, and it took all but 2 minutes to do :)

So thank you for taking youre time and writing that how-to for someone else, because it ended up solving my half internet speed problem.

---

