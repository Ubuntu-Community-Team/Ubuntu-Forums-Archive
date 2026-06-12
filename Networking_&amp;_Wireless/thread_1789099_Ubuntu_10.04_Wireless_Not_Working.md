---
title: "Ubuntu 10.04 Wireless Not Working"
date: 2011-06-23
forum: Networking &amp; Wireless
---

### Post by TRaptor on 2011-06-23
Hi,
Just upgraded to the newest version of Ubuntu(unity), and my wireless isn't working. I have the 14e4:4315 Wireless Card so I followed this posts instructions: [http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44) . And still have no wifi, when I click the icon in the menu bar it says under "Wireless Networks": "wireless is disabled by hardware switch", which ins't true because on my Vostro 1520, there is only one switch and it is in the on position. 

I've tried 3 versions of ubuntu and none of them work with wifi... getting tired of it.

---

### Post by TRaptor on 2011-06-23
> **TRaptor said:**
> Hi,
Just upgraded to the newest version of Ubuntu(unity), and my wireless isn't working. I have the 14e4:4315 Wireless Card so I followed this posts instructions: [http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44) . And still have no wifi, when I click the icon in the menu bar it says under "Wireless Networks": "wireless is disabled by hardware switch", which ins't true because on my Vostro 1520, there is only one switch and it is in the on position. 

I've tried 3 versions of ubuntu and none of them work with wifi... getting tired of it.

Also, not sure if this will help any, but it works with the ethernet cable.

---

### Post by chili555 on 2011-06-23
Is the module dell-laptop loaded?```
lsmod | grep dell
```Does your wireless start working if you unload it?```
sudo rmmod -f dell-laptop
```If so, we can make it persistent.

---

### Post by TRaptor on 2011-06-23
> **chili555 said:**
> Is the module dell-laptop loaded?```
lsmod | grep dell
```Does your wireless start working if you unload it?```
sudo rmmod -f dell-laptop
```If so, we can make it persistent.

That removes "Wireless Networks" from the drop down when I click the network icon in the menu bar. Wireless still doesn't work.

BTW: "Enable Networking" is checked!

Thanks.

---

### Post by josephmills on 2011-06-23
could we please see a ```
rfkill list all 
```

```
dmesg | grep  b43 
```
```
lsmod
```

Hi there Chili555 nice to see you again :P

---

### Post by chili555 on 2011-06-23
I tried the shortcut and it was a dead-end; hey, this just isn't my day! Let's take a deeper look. Please reload dell-laptop:```
sudo modprobe dell-laptop
```Now please run and post:```
rfkill list all
dmesg | grep -e b43 -e wl
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by TRaptor on 2011-06-23
> **chili555 said:**
> I tried the shortcut and it was a dead-end; hey, this just isn't my day! Let's take a deeper look. Please reload dell-laptop:```
sudo modprobe dell-laptop
```Now please run and post:```
rfkill list all
dmesg | grep -e b43 -e wl
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

The "rfkill list all" has both "Soft and Hard" blocked as yes. And the "dmesg | grep -e b43 -e wl" gives no output. 

@josephmills the lsmod is quite lengthy and would take me forever to type out here as I dont have internet to my laptop. If its what you guys need I can figure out a way to get it over.

Thanks.

---

### Post by chili555 on 2011-06-23
Take it, Joseph; I'll pour myself a cool one and chill out!

---

### Post by josephmills on 2011-06-23
> **TRaptor said:**
> The "rfkill list all" has both "Soft and Hard" blocked as yes. And the "dmesg | grep -e b43 -e wl" gives no output. 

@josephmills the lsmod is quite lengthy and would take me forever to type out here as I dont have internet to my laptop. If its what you guys need I can figure out a way to get it over.

Thanks.

what about ```
dmesg | grep b43 
``` you dont have the internet at all how are you typing this? try the "fn"button plus f2 then ```
rfkill unblock all 
``` then are they still all blocked ? next look lets see ```
lsmod | grep b43 
``` thanks

---

### Post by TRaptor on 2011-06-23
> **josephmills said:**
> what about ```
dmesg | grep b43 
``` you dont have the internet at all how are you typing this? try the "fn"button plus f2 then ```
rfkill unblock all 
``` then are they still all blocked ? next look lets see ```
lsmod | grep b43 
``` thanks

I am using my mac to type this. 

The "dmesg | grep b43" doesn't output anything. And I did that keyboard shortcut and then ran the "rfkill unblock all" and then did the "lsmod | grep b43" and that didn't give me anything. After that I ran "rfkill list all" and they are still both blocked.

---

### Post by josephmills on 2011-06-23
do you have a ext usb or a blank cd or dvd and a burner on that mac ? also lets see what kernel you are using ```
uname -r 
```

---

### Post by TRaptor on 2011-06-23
> **josephmills said:**
> do you have a ext usb or a black cd or dvd and a burner on that mac ?

I have a WD ext hard drive.

---

### Post by ZekeGraal on 2011-06-23
I know this is completely in the middle of this, but I found [this thread]("http://ubuntuforums.org/showthread.php?t=1307077&page=2") that says its a bug with the old BIOS on the 1520.. good luck :]

---

### Post by josephmills on 2011-06-23
```
uname -r
```

---

### Post by TRaptor on 2011-06-23
> **josephmills said:**
> ```
uname -r
```

That gives:
```
2.6.38-8-generic
```

I think I am going to try ZekeGraal's suggestion and see how it goes. The dell system is complete garbage, but its what I have to work with so... :(

---

### Post by josephmills on 2011-06-23
> **TRaptor said:**
> That gives:
```
2.6.38-8-generic
```

I think I am going to try ZekeGraal's suggestion and see how it goes. The dell system is complete garbage, but its what I have to work with so... :(

you mods and driver + firmware is not there it will not work

---

### Post by josephmills on 2011-06-23
download this then move it over to your ubuntu box tell me when you get that far [http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2) you can put it in your home folder

---

### Post by TRaptor on 2011-06-23
> **josephmills said:**
> you mods and driver + firmware is not there it will not work

Will reinstalling ubuntu get me my needed mods and drivers + firmware?

---

### Post by josephmills on 2011-06-23
eff the compat that will be to complicated just do this 
download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it Wireless**
[IMG]http://img862.imageshack.us/img862/8053/screenshotba.png[/IMG]





Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 
[IMG]http://img850.imageshack.us/img850/4563/screenshot1kl.png[/IMG]






Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/Wireless/* /lib/firmware/
``` 
[IMG]http://img101.imageshack.us/img101/5329/screenshot5ei.png[/IMG]






Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step
[IMG]http://img151.imageshack.us/img151/5092/screenshot3ln.png[/IMG]





Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 
[IMG]http://img143.imageshack.us/img143/3945/screenshot4zv.png[/IMG]





Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ?

---

### Post by josephmills on 2011-06-23
> **TRaptor said:**
> Will reinstalling ubuntu get me my needed mods and drivers + firmware?

no there are third party and that is why they don't work out of the box

---

### Post by TRaptor on 2011-06-23
> **josephmills said:**
> eff the compat that will be to complicated just do this 
download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it Wireless**
[IMG]http://img862.imageshack.us/img862/8053/screenshotba.png[/IMG]





Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 
[IMG]http://img850.imageshack.us/img850/4563/screenshot1kl.png[/IMG]






Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/Wireless/* /lib/firmware/
``` 
[IMG]http://img101.imageshack.us/img101/5329/screenshot5ei.png[/IMG]






Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step
[IMG]http://img151.imageshack.us/img151/5092/screenshot3ln.png[/IMG]





Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 
[IMG]http://img143.imageshack.us/img143/3945/screenshot4zv.png[/IMG]





Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ?

Followed those directions and still no wireless. Could it be that the BOIS is buggy and updating the BOIS would fix the problem: [http://ubuntuforums.org/showthread.php?t=1307077&page=2](http://ubuntuforums.org/showthread.php?t=1307077&page=2)

Rebooted ubuntu and it says "Sorry, the package 'firmware-b43-installer4.150.10.5-5' failed to install or upgrade." What does that mean?

---

### Post by josephmills on 2011-06-23
> **TRaptor said:**
> Followed those directions and still no wireless. Could it be that the BOIS is buggy and updating the BOIS would fix the problem: [http://ubuntuforums.org/showthread.php?t=1307077&page=2](http://ubuntuforums.org/showthread.php?t=1307077&page=2)

Rebooted ubuntu and it says "Sorry, the package 'firmware-b43-installer4.150.10.5-5' failed to install or upgrade." What does that mean?

go to synaptic and type in bcm into the search bar and take a screen shot of it for us please nothing should be installed but the but the bcmwl-kernel-source remove that  then reboot then install it again then you guessed it reboot again then let us see a ```
dmesg | grep b43
``` thanks

---

### Post by TRaptor on 2011-06-23
> **josephmills said:**
> go to synaptic and type in bcm into the search bar and take a screen shot of it for us please nothing should be installed but the but the bcmwl-kernel-source remove that  then reboot then install it again then you guessed it reboot again then let us see a ```
dmesg | grep b43
``` thanks

Here is the screenshot:

---

### Post by josephmills on 2011-06-23
> **TRaptor said:**
> Here is the screenshot:

remove them all but the bcmwl-kernel-source
then reboot

---

### Post by TRaptor on 2011-06-24
> **josephmills said:**
> remove them all but the bcmwl-kernel-source
then reboot

Did that and still no wireless.

---

### Post by josephmills on 2011-06-25
```
sudo -s 
``` then ```
modprob b43 
``` then ```
 echo b43 >> /ect/modules 
``` then ```
 exit 
``` then reboot with out the  cable in anything ?

---

### Post by MartinusEx on 2011-06-25
Hi,

I do not want to disencourage you but wireles seems to be an issue within Natty itself.
I tried to install natty on a toshiba sattelite, we had wirelass and lan and internet for a short time, then it went dead and did not come back up again regardless of our doings.

But what worked for us was WICD which manages your wireless connections.
Shame on natty, it did not help very long.

My friend downgraded to maverick and wireless works most of the time.


So first try (install and see if it works) WICD then drop natty.

rgds

Martin

---

### Post by chili555 on 2011-06-25
> **josephmills said:**
> remove them all but the bcmwl-kernel-source
then rebootbcmwl-kernel-source installs a blacklist file; I wonder if it's holding b43 back.> then
Code:

modprob b43

It's *modprobe*.> echo b43 >> /ect/modulesIt's */etc/modules*.

---

