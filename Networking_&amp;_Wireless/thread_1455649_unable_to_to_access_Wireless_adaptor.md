---
title: "unable to to access Wireless adaptor"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by rhlongo on 2010-04-16
Not a newbie to computers, but I am to Linux/Ubuntu. I set up an older computer with Ubuntu 9.10 and tried to get my Linksys AE1000 Wireless N adapter to work. My first mistake was not checking in advance to see if this adapter would work, but I have taken the leap and I am intent on making it work. I ran lsusb and it gives me a device number (13b1:002f) so I know it can be seen and I have also installed indisgtk the GUI for Wirless drivers. I have tried some suggestions from other posts to no avail.

I'm looking for some suggestion?

Thanks in advance!

---

### Post by wah fun on 2010-04-16
It is very possible that ubuntu is trying to use either a default driver for your card or another driver is interfering with ndiswrapper. Try the following.

First: As root, go to /lib/modules/(your kernel)/drivers/staging. Look for a folder with your card name. If there is none, then there isn't a testing driver that might be trying to control your adapter. If there is, simply open the folder and change the name of the driver inside. You might just want to append the name with .disabled but you can change it to anything.

If there is no folder with your card name, then as root go to /lib/modules/(your kernel)/drivers/net/wireless. Open the folder and look for a folder with your card name. If there is just open the folder and rename the driver inside. If there is none, then look for the b43 folder (it is in this same directory. Open the folder and rename the b43.ko driver. The reason you rename this driver is that it interferes with ndiswrapper. Do the same for the driver in the b43legacy folder.

Now reboot and your adapter should work. Hope this helps.

---

### Post by rhlongo on 2010-04-16
I feel silly for this question, what is the best way to get access to the root folder in the file browser. Everyone says it is locked to protect problems, but does not tell you how to get access. I know it will be easier to unlock it!

---

### Post by nerdy_kid on 2010-04-16
```

gksu nautilus PATH[optional]

```

---

### Post by rhlongo on 2010-04-16
Thanks for the help so far! I just noticed you said to look for a folder with your card name, may be my error, but I am trying to install a USB adaptor.

Completed as instructed and after re-boot still no sign of life from the adaptor. I tried to go back and view the folders, when I tried to access the root by the command you provided below, It returned an error 255, cannot open usershare directory, says to ask the sys admin to enable sharing.

I can see I have a lot to learn, windows ruined my understanding on how things work!

Hopefully you have something that will help, I am determined to make it work!

Thank you!

---

### Post by btdriver on 2010-04-17
Let me know if you have success getting the Linksys AE1000 USB wireless adapter to work with Karmic using the Windows driver and ndiswrapper.  I have been trying over the course of the last week to get this device working using the Ralink rt2870sta Linux driver and the Karmic-delivered rt2870sta Linux driver but have not had success yet.

---

### Post by codermsu on 2010-04-20
The driver you need is rt3572sta.  You can download the source from ralink's website.  

You then need to open up the rtusb_dev_id file and add an entry for your usb id under 3572 section and build, add to /etc/modules, etc. 

I have had this card working with this driver, however, there has been some kernel panics.  Both radios work. N transfer speeds.  Just a little buggy.

---

### Post by btdriver on 2010-04-20
I downloaded and installed the Ralink rt3572sta driver, and I now have wireless connectivity.  Thank you very much. I have been working on this for a week trying to get various versions of the rt2870sta Linux driver and the delivered XP Windows driver (with ndiswrapper) to work with no success.
 
I have to ask.  How did you determine that the rt3572sta driver was the right one?  I came to the conclusion that I should use the rt2870sta driver based on the fact that the delivered Windows XP driver had file names of the form rt2870.*.

---

### Post by nerdy_kid on 2010-04-20
> **codermsu said:**
> The driver you need is rt3572sta.  You can download the source from ralink's website.  

You then need to open up the rtusb_dev_id file and add an entry for your usb id under 3572 section and build, add to /etc/modules, etc. 

I have had this card working with this driver, however, there has been some kernel panics.  Both radios work. N transfer speeds.  Just a little buggy.

um this guy is new... even *i* am not quite sure how to do that, and ive been using linux for a while.

---

### Post by dummptyhummpty on 2010-04-20
> **nerdy_kid said:**
> um this guy is new... even *i* am not quite sure how to do that, and ive been using linux for a while.

There's a guide out there for the Linksys USB600N which has basically the same steps.


[LIST=1]
[*]You need your device id (type lsusb at the terminal).
[*]Then you need the drivers from [http://www.ralinktech.com](http://www.ralinktech.com).
[*]Follow the directions in the readme about changing HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT to "y" in the config.mk file.
[*]Find "rtusb_dev_id.c" in the common folder.
[*]Find the line "#endif // RT2870 //".
[*]Add your device id right above this, following the format of the other device ids.
[*]Open a terminal to the root of the folder where you have extracted these files and type "sudo make" and then "sudo make install".
[*]Edit /etc/modules and add "rt3572sta".
[*]Reboot and you should be working. You might need to add rt2870sta to /etc/modprobe.d /blacklist.conf  (follow the format). I added: rt2800usb, rt2860sta, rt2x00usb, rt2x00lib, rt2870sta.
[/LIST]

**Note: *Try this at your own risk.*** I'm not an expert, but the previous steps worked for me. I welcome any corrections. Thanks to codermsu for pointing out the correct drivers to use.

---

### Post by rhlongo on 2010-04-21
Update!  I started again and loaded XP to make it easier to acccess the internet then I am going to install Ubuntu as a dual boot. I am having issues getting this adaptor to connect to the router also. At least on XP, the driver installs and can see the router, there are issues on loggin on. Wondering if there is a connection! checking further, hoping all works!

---

### Post by codermsu on 2010-04-25
I should probably elaborate on this some more, since my initial reply was very vague and written when I was very tired.

kai4785 over on the Fedora forums found this thread and it helped him get this card working.  He put together a very nice step-by-step write-up over there.  

[http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558)

His instructions should work perfectly on Ubuntu.  

Also, I would recommend using wicd, wicd-client over network-manager.  Or I understand what wicd is doing where I can't say the same of network-manager.  wicd is using the values you provide it to generate a wpa_supplicant.conf file that it can run pre-up.  

FWIW, I previously mentioned I was having kernel panics using this driver.  It appears that this issue was related to setting my wireless nic to use the same static ip address that the wired nic previously held.  I haven't narrowed it down completely, but 'sudo ifconfig eth0 down' finally allowed my ae1000 to consistently connect and be assigned an ip correctly.



If you wanted to set this up sans gui, you could snag wicd-curses or create an entry in /etc/network/interfaces for ra0.  Create a wpa_supplicant.conf file and then add something like:
pre-up wpa_supplicant -Bw -Dwext -ira0 -c/etc/wpa_supplicant/wpa_supplicant.conf
post-down killall -q wpa_supplicant

---

### Post by cjmarti1986 on 2010-05-17
Hello everyone I just Stumble onto this site and AM having complete confusion about install the drivers. Im New to Ubuntu and this has just been a nightmare. I dont know that Im doing and by following those steps I'm still confused. After I download the driver I have no idea where to send it or edit it I have the folder on my desktop and I did the command "lsusb" which gave me 
 ```
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:002f Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hu
```

I see that It picked up the Linksys 

**B**ut Where Do I need to put the drivers?

---

### Post by cjmarti1986 on 2010-05-17
nvm Problem solved.... Just have to read word for word and take the time to understand the procedures for linux...

---

### Post by ColdScottTea on 2010-08-10
> **cjmarti1986 said:**
> nvm Problem solved.... Just have to read word for word and take the time to understand the procedures for linux...

I'm new to Ubuntu and Linux.

I'm at the same place you were at. I tried to follow the instructions at ([http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558))
but I don't understand them all and I must be doing something wrong.
I just tried to copy all the commands off the tutorial into terminal one by one hitting enter after each command, and then I rebooted. Still no internet connection.

I'm not sure how to do the "Step 3) Follow the directions in the readme about changing HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT to "y" in the config.mk file."

And after I complete the driver install, will Ubuntu use the ae1000 to connect to the internet automatically or do I have to configure it somehow.

I'm reading as much as I can to try and get it done on my own, but need some help/direction.

Thank you very much for any help.

*First I need help installing the driver. In the "Readme_STA" it tells me to edit the "Makefile"

"2> In Makefile
set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
define the linux kernel source include file path LINUX_SRC
modify to meet your need."

In my "Makefile" is says,

"RT28xx_MODE = STA
TARGET = LINUX
CHIPSET = 3572
OSABL = NO"

Mode = STA and Target = Linux, am I done? I'm not sure how to, "define the linux kernel source include file path LINUX_SRC modify to meet your need".

Thats only step 2, Steps 3 and through 7 are equally confusing to me.

Is there a list of commands I can just copy and paste one at a time to get this working?, or is that what the Fedora tutorial I mentioned above is, and I'm just not doing it right?

Sorry for all the words, I figured the more info the better.

Thanks in advance.

---

### Post by mervunit on 2011-02-03
> **ColdScottTea said:**
> I'm new to Ubuntu and Linux.

I'm at the same place you were at. I tried to follow the instructions at ([http://forums.fedoraforum.org/showthread.php?p=1353558](http://forums.fedoraforum.org/showthread.php?p=1353558))
but I don't understand them all and I must be doing something wrong.
I just tried to copy all the commands off the tutorial into terminal one by one hitting enter after each command, and then I rebooted. Still no internet connection.

I'm not sure how to do the "Step 3) Follow the directions in the readme about changing HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT to "y" in the config.mk file."



Ok. There is a file when you unpack the driver files in folder /os/linux called config.mk. All you gotta do is open it up with gedit and you'll see those fields in there =n just change them to =y and save the file. I had tried using the same walk-thru at fedora forum too but it wouldn't compile when i ran sudo make or sudo make install. It did a lot of unneeded changes that did not work. I just did everything word for word hummptydumpty said and it works perfectly! no link light though.

---

### Post by waydaws on 2011-02-14
> **dummptyhummpty said:**
> There's a guide out there for the Linksys USB600N which has basically the same steps.


[LIST=1]
[*]You need your device id (type lsusb at the terminal).
[*]Then you need the drivers from [http://www.ralinktech.com](http://www.ralinktech.com).
[*]Follow the directions in the readme about changing HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT to "y" in the config.mk file.
[*]Find "rtusb_dev_id.c" in the common folder.
[*]Find the line "#endif // RT2870 //".
[*]Add your device id right above this, following the format of the other device ids.
[*]Open a terminal to the root of the folder where you have extracted these files and type "sudo make" and then "sudo make install".
[*]Edit /etc/modules and add "rt3572sta".
[*]Reboot and you should be working. You might need to add rt2870sta to /etc/modprobe.d /blacklist.conf  (follow the format). I added: rt2800usb, rt2860sta, rt2x00usb, rt2x00lib, rt2870sta.
[/LIST]

**Note: *Try this at your own risk.*** I'm not an expert, but the previous steps worked for me. I welcome any corrections. Thanks to codermsu for pointing out the correct drivers to use.

Just a small correction...
In step 7, don't do "sudo make" - just do "make" 
But, after "make", then do "sudo make install" as he has shown above.

---

### Post by ericrichards420 on 2011-03-11
Hey guy, I dont know if you have got that ae1000 usb card to work yet or not, the ndis-wrapper is not the way to go for that card. cisco makes a driver just for linux. check out my thread and see if it helps you out any. [http://ubuntuforums.org/showthread.php?t=1701471&highlight=ae1000](http://ubuntuforums.org/showthread.php?t=1701471&highlight=ae1000)

---

### Post by ericrichards420 on 2011-03-11
.

---

### Post by sixtyfourk on 2011-03-12
I have followed the the instructions in this thread and successfully compiled and installed the driver.

However, I cannot connect to any wireless networks -- the connection just times out and continues to ask for the password.  I am using WPA2 Personal, and I am certain I have put in the correct password.

I have tried both the latest source code from Ralink: 2010_1215_RT3572_Linux_STA_v2.5.0.0 and the older RT3572_drv2400.  Same result with both.

Thanks in advance!

---

