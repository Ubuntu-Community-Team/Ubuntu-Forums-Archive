---
title: "Facebook poker app problem"
date: 2009-04-23
forum: Multimedia Software
---

### Post by UnBr34KaBl3 on 2009-04-23
Flash Poker on Facebook is not working.I just installed Jaunty and I just can't get it to work. I can only see the normal facebook stuff and the top of the poker app witch probably is HTML. The main poker app flashes for a second and then disappears while the gift thing at the bottom of the page continues to load forever. I'm using firefox and I tried to install pretty much everything that came upp in a search for "flash" in the add/remove programs app but it didn't work. A solution anyone?

I'm not realy sure if this is the right place to post this but I thought it fitted best here.

---

### Post by cariboo on 2009-04-23
Do you have flash installed? If not install the ubuntu-resricted-extras meta package. It will install flash, jave and most of the codecs needed to install most types of audio/video media. The ubuntu-restricted-extras package is in the repositories, and you can use Add/Remove Programs or Synaptic Package Manager to install it.

---

### Post by UnBr34KaBl3 on 2009-04-23
Thank you. I will try that and come back.

EDIT: I have a problem with installing ubuntu-restricted-extras. The Add/remove program tells me to use synaptic becouse its in conflict with another app but I cant find the package in synaptic.

EDIT2: Installed it but now its just a big green box there and no poker :(

---

### Post by michaeldt on 2009-04-25
When you're on a page with flash (assuming you're using Firefox) click the blue icon in the bottom right of the window. You might find that it's using swfdec for Flash instead of Adobe.

---

### Post by UnBr34KaBl3 on 2009-04-25
It works now, almost. It loads but it doesn't show any servers. However I can play of I press the "Find me a seat" button. Everthing works perfecty exept it doesnt show any servers, suggestions?

---

### Post by JK3mp on 2009-04-25
The creators weren't too interested in making it linux compatable i find alot of apps that don't work, a few that do, a few that do but only partially.

---

### Post by zobcat on 2009-05-23
FF3 for Windows under WINE gets it up and running 100%.

---

### Post by alikebabay on 2009-05-29
> **UnBr34KaBl3 said:**
> It works now, almost. It loads but it doesn't show any servers. However I can play of I press the "Find me a seat" button. Everthing works perfecty exept it doesnt show any servers, suggestions?
I am with you man:) Just click find me a seat, It will get you in the game. I have got this problem after updating to flash 10 for bbc iplayer. I hope poker guys will fix it soon. You can also try downgrading to flash 9... 
P.s. Usually gets you in the game with 100/200 blinds or 1/2 blinds.

---

### Post by zobcat on 2009-05-30
```
sudo apt-get install wine
```

then download the latest [firefox for windows]("http://www.mozilla.com/products/download.html?product=firefox-3.0.10&os=win&lang=en-US")

open the .exe (right click > open with wine) 

this loads the installation of firefox for windows.

navigate to the facebook poker app. A banner drops to install flash. Click the install button. Download flash. Install flash. Play Texas Hold 'em.

---

### Post by yodeloo on 2009-07-07
I've ubuntu 8.04 with flashplayer 9. After a certain time gaming with poker, it become impossible to raise (with textfield, or with slidebar). It becomes sometimes after writing something in chat, but without too.

Anybody else has this problem ?
Any ideas about how to fix it ?

Thanks,

Yod

---

### Post by StivnC on 2009-07-21
> It works now, almost. It loads but it doesn't show any servers. However I can play of I press the "Find me a seat" button. Everthing works perfecty exept it doesnt show any servers, suggestions?Is there no work around to be able to see the games but without using FF in Wine?
The Find me a seat does not work for the Sit N Go Tournaments and that's what I mostly play.
Thanks
PS I'm new to Ubuntu.

Update: I tried downgrading to Flash 9 this worked but made the sound in YouTube stop working.

---

### Post by alikebabay on 2010-01-08
Have all the problems mentioned above (no tables, trouble to raise). Seamonkey 1.1.17 (old one) works just fine with minor glitches. But hey, this is 2009 now, we gotta be able to use newest software(without resorting to wine). How about joint appeal to zynga, to make facebook poker ubuntu compatible? (new seamonkey doesn't work for poker eiter...)

---

### Post by NightHawk_UK on 2010-02-10
I solved this issue by replacing the flash-plugin with the beta version from adobe using the code below.

I am new to this so let me know if it can be done better.

My system Ubuntu 9.10 64bit - Firefox 3.5.7

I tried this on both 32bit and 64bit system, note i used perfectbuntu to set up my flash from [http://www.category5.tv/](http://www.category5.tv/) if you find the files are not in the same place as mine.

in the terminal at your home directory:

(get the file using)
```
_wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p3_linux_022310.tar.gz_[]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.gz")
```(uncompress it)
```
tar -zxvf flashplayer10_1_p3_linux_022310.tar.gz
```(rename the old file for safety)
```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.soOLD
```(replace the old file)
```
sudo cp ~/libflashplayer.so /usr/lib/flashplugin-installer
```Restart Firefox

Thats all i did and everything is working now.

Hope it helps.

I also wrote a small bash script to switch between these two files as some sites do not support the Beta version yet, well i only came across one so far ;)

---

### Post by phlosy on 2010-02-12
i can get my facebook page but when i go to texas holdem poker it start loading then stop and go to another page sayin page cant be found.can u please help me.;)

---

### Post by Jehvo on 2010-02-14
> **NightHawk_UK said:**
> I solved this issue by replacing the flash-plugin with the beta version from adobe using the code below.

I am new to this so let me know if it can be done better.

My system Ubuntu 9.10 64bit - Firefox 3.5.7

I tried this on both 32bit and 64bit system, note i used perfectbuntu to set up my flash from [http://www.category5.tv/](http://www.category5.tv/) if you find the files are not in the same place as mine.

in the terminal at your home directory:

(get the file using)
```
wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.gz")[gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.gz")
```(uncompress it)
```
tar -zxvf flashplayer10_1_p2_linux_121709.tar.gz
```(rename the old file for safety)
```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.soOLD
```(replace the old file)
```
sudo cp ~/install_flash_player_10_linux/libflashplayer.so /usr/lib/flashplugin-installer
```Restart Firefox

Thats all i did and everything is working now.

Hope it helps.

This worked for me :D
Thanks man

---

### Post by waynefoutz on 2010-02-14
It will be nice when html5 replaces all these flash apps.

---

### Post by freshinstall on 2010-03-03
> **NightHawk_UK said:**
> I solved this issue by replacing the flash-plugin with the beta version from adobe using the code below.

I am new to this so let me know if it can be done better.

My system Ubuntu 9.10 64bit - Firefox 3.5.7

I tried this on both 32bit and 64bit system, note i used perfectbuntu to set up my flash from [http://www.category5.tv/](http://www.category5.tv/) if you find the files are not in the same place as mine.

in the terminal at your home directory:

(get the file using)
```
wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.gz")[gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.gz")
```(uncompress it)
```
tar -zxvf flashplayer10_1_p2_linux_121709.tar.gz
```(rename the old file for safety)
```
sudo cp /usr/lib/flashplugin-installer/libflashplayer.so /usr/lib/flashplugin-installer/libflashplayer.soOLD
```(replace the old file)
```
sudo cp ~/install_flash_player_10_linux/libflashplayer.so /usr/lib/flashplugin-installer
```Restart Firefox

Thats all i did and everything is working now.

Hope it helps.

:D Thanks alot this is the solution.  I would do the install a little differently, if you are using firefox simply find your firefox dir and copy the .so under the plugins dir.  Chrome loads the plugin from usr/lib/adobe-flashplugin so replace the .so that is there if you are a chrome user.  This should be done as root.

Finally I dont have to leave ubuntu to get my poker on!

---

