---
title: "Help with BCM4318 on Compaq Presario V2000"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by zrzhu on 2009-07-30
I downloaded ubuntu 9.04, but the wifi doesn't work. It's BCM 4318 on compaq presario v2000. I tried NDISWrapper, I installed the driver from xp. But I type ifconfig, I don't see anything about the wireless. 

I did these steps according to [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
1. I have a question about the code: 
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklistDo I put above command on terminal at the same time, just copy and paste, or I have to do something else? 
2. It says "Or just edit the /etc/modprobe.d/blacklist file and add blacklist bcm43xx, blacklist b43, blacklist b43legacy and blacklist ssb to the end of the file.)" when I open the balcklist and edit it, but I can't save it, says denied due to permission. 
3. I don't know what I did, there is a new file called blacklist, and "sudo" on the file icon, I can't delete it. Please tell me what should I do with this.

In addtion: 
zong@1234-laptop:~$ sudo modprobe ssb

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'sudo'
WARNING: /etc/modprobe.d/blacklist line 13: ignoring bad line starting with '-e'

WARNING: /etc/modprobe.d/blacklist line 15: ignoring bad line starting with '&#8216;blacklist'

---

### Post by go2dell on 2009-08-03
Wow, sorry nobody has answered this for you before now!  Your problem is so simple.

What the instructions leave out is that you need to use the *sudo* command to edit any system files (pretty much anything in */etc*, for instance).  That's why your attempt to edit the file failed due to lack of permission to do so.  When you use *sudo* you're temporarily becoming "root," a.k.a. the All Powerful User.  Ubuntu disables the root account by default and requires you to type sudo all the time because it's more secure -- in theory, anyway.  The nice thing about sudo, whether on the command line or in your graphical system, is that it "remembers" you for a period of time each time you use it, so you only have to type in the password the first time if you're performing a series of commands.

If you've used the first command from your post -- and your error message indicates you have -- then you already have the necessary file that blacklists the modules that will interfere with ndiswrapper.  Unfortunately, it also appears you didn't type something in the command correctly, so Linux is not a happy camper and refuses to do what you want it to do.  You'll need to fix things before you can continue.

***Assuming you haven't put anything else in the blacklist file*** you can simply open a terminal and type ```
sudo rm /etc/modprobe.d/blacklist
``` and hit <enter>.  If you've done anything else with the blacklist file, then you'll need to edit by hand to remove the bad lines.

Now you can type the first command again, but there's one suggestion here:  at the very end of the command (the part after *sudo tee*) use */etc/modprobe.d/blacklist.conf* so that your commands will be in the correct place.

Since you're using a Broadcom card, you may also want to just toss all this and use the semi-free b43 module already available in Ubuntu.  It eliminates all the futzing around with ndiswrapper.  On my bcm4306 it also happens to be slow as molasses in January, but it's reliable and It Just Works, so I always have a fallback.

I should mention here that I'm trying to switch over to ndiswrapper because my particular card is almost uselessly slow for anything other than Web browsing using b43.  My only problem with getting ndiswrapper running is that my system absolutely refuses to blacklist ssb, and ndiswrapper can't load correctly when ssb loads.  I may be switching back to b43 just to save bothering with the whole thing.

If you want to try b43, first back out all the changes you did to use ndiswrapper and then [click here for instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx").

Good luck, and welcome to Ubuntu! \\:D/

---

### Post by Jazzkatt on 2009-08-20
**Re: BCM 4318 with Jaunty** 			
 			 			 		   		 		 		I'm new to this also and the same problem. 

 First thing I did was plug hard wired into my network and got all available updates.Through System>Administration>Update Manager.

 Second Clicked System>Administration>Hardware Drivers . It found the card I highlighted it a clicked "Activate" It activated it. Still nothing .Reboot still nothing. 
So I thought when Ubuntu was installed the driver was not active so just maybe the network manager could not see it. 

 Third I clicked Applications > Add / Remove . It said the list was out of date so I clicked refresh . after the refresh I clicked Internet, and in the applications box checked KNetworkManager . In the process of installing KNetMgr it updated all installed programs. While the install was still in process of installing I saw my wireless Switch/Light ,light up . 

After Install was complete I unplugged the cat5 clicked network manager in the title bar there was my router . Selected it put in the key and here I am .

This was on a Compaq Presario 5305wm laptop completely stock.
Semperon 3400+ 80 gig HD 1 gig ram
Broadcom BCM 4318e
Duel booting Ubuntu 9.04 Win7
Ubuntu install and updated 8.20.2009 12.00 pm cst.

Hope this helps 
Jazz

---

