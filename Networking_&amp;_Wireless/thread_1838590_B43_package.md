---
title: "B43 package"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by Brizlitman on 2011-09-03
Hi, i just began using ubuntu and i've noticed that i can't get the wifi to turn on. i downloaded the b43-fwcutter package. Could someone please tell me how to do the extraction?

---

### Post by nm_geo on 2011-09-03
> **Brizlitman said:**
> Hi, i just began using ubuntu and i've noticed that i can't get the wifi to turn on. i downloaded the b43-fwcutter package. Could someone please tell me how to do the extraction?

By the way welcome to the forums...

Run this in terminal please and post result.. What version are you running?

```
lspci -nn | grep 0280
```

---

### Post by Brizlitman on 2011-09-03
11.04

---

### Post by nm_geo on 2011-09-03
> **Brizlitman said:**
> 11.04

Okay 
Ctrl    Alt     T
should open a terminal..

then copy and paste this command in the terminal..

```
lspci -nn | grep 0280
```

Copy and paste results .. That will tell us the card number we need..

---

### Post by Brizlitman on 2011-09-03
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

---

### Post by nm_geo on 2011-09-03
> **Brizlitman said:**
> 01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

EXcellent we are almost there..

```
rfkill list all
```That tells us your not blocked by wifi switch or software.

Then in terminal

```
sudo apt-get install firmware-b43-installer
```You will be Golden after that... if you have all "no"  answers to the rfkill list all

---

### Post by Brizlitman on 2011-09-04
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

now for the second one:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer

---

### Post by nm_geo on 2011-09-04
> **Brizlitman said:**
> 0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

now for the second one:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
kobina@ubuntu:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer

My fault I assumed you had the computer hooked up with ethernet cable.
So right now how are you communicating to the forum?  Another computer?

Can you put an etherent cable into the computer we are working on?

---

### Post by Brizlitman on 2011-09-04
I installed ubuntu via wubi. therefore, i am using a dual-boot. i am using windows on the forums. I don't have access to an ethenet cable either

---

### Post by josephmills on 2011-09-04
**installing b43fwcutter with-out the internet ** 

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

---

### Post by nm_geo on 2011-09-04
> **Brizlitman said:**
> I installed ubuntu via wubi. therefore, i am using a dual-boot. i am using windows on the forums. I don't have access to an ethenet cable either

Ok I have a link where chili555 explained and got this working for someone with the same condition.

[http://ubuntuforums.org/showthread.php?p=11075482#21](http://ubuntuforums.org/showthread.php?p=11075482#21)

Read through message 21 my link should take you right there and the firmware you need is in the b43.zip file.  Of course you have to get it to Ubuntu and into the correct directory.

---

### Post by Brizlitman on 2011-09-04
OH YEAH! YOU GUYS ARE AWESOME. UBUNTU ROCKS. Thanks a million,it works

---

### Post by nm_geo on 2011-09-04
> **Brizlitman said:**
> OH YEAH! YOU GUYS ARE AWESOME. UBUNTU ROCKS. Thanks a million,it works

EXCELLENT chili is fixing things and he ain't here LOL please mark solved at top..

---

