---
title: "Ubuntu 10.04 using the Ralink RT2860 WiFi chipset (e.g. EeeBox B202)"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Sven6210 on 2010-05-07
[FONT=Verdana, sans-serif]After having installed Ubuntu 10.04 successfully on my EeePC 900a I also wanted to use it on my EeeBox B202 which is used as a kind of media centre.[/FONT]
 

 [FONT=Verdana, sans-serif]The installation of Ubuntu 10.04 on the EeeBox was not a big issue, but unfortunately the WiFi did not work out of the box. The EeeBox B202 is using the Ralink RT2860 WiFi chipset which apparently worked out of the box with Ubuntu 9.04 and 9.10 but not with 10.04.[/FONT]
 

 [FONT=Verdana, sans-serif]After some reseach I found the solution. This is probably also working for other machines using the Ralink RT2860.[/FONT]
 

 [FONT=Verdana, sans-serif]This manual is largely based on Chris Barker's description, please see[/FONT]
 

 [FONT=Verdana, sans-serif]http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html [/FONT] 
 

 H[FONT=Verdana, sans-serif]ere the description step by step:[/FONT]
 

 **[FONT=Verdana, sans-serif]Step 1[/FONT]**
 [FONT=Verdana, sans-serif]Download latest RT2860 driver source code from Ralink[/FONT]
 

 [FONT=Verdana, sans-serif]Go to [http://www.ralinktech.com/](http://www.ralinktech.com/)[/FONT]
 [FONT=Verdana, sans-serif]Klick on Software[/FONT]
 [FONT=Verdana, sans-serif]Klick on Linux[/FONT]

[FONT=Verdana, sans-serif]Download the driver &#8222;RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)&#8220; dated 01/29/2010, version 2.3.0.0

[/FONT]You need to enter a name and an email and press accept to download
[FONT=Verdana, sans-serif]
*Attention, there is a new driver available since July 2010:*
Download the driver "RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)&#8220; dated 07/16/2010, version 2.4.0.0

When you download the new driver you need to r[/FONT]ename the downloaded file from
2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
to
   2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar
So actually you need to remove the '.bz2' ending. After that you can  double-click the file and 'File Roller' can open it.[FONT=Verdana, sans-serif]
[/FONT]

 **[FONT=Verdana, sans-serif]Step 2[/FONT]**
 [FONT=Verdana, sans-serif]Open and extract the downloaded file to your Home directory. Accept the standard folder and to not change the name[/FONT]
 
[FONT=Verdana, sans-serif]Attention, it is a source of later problems if you do not extract the new directory to your home directory. It must really be in the home directory so that the following commands work. [/FONT]

 [FONT=Verdana, sans-serif]Open a terminal window[/FONT]
 ```
[FONT=Verdana, sans-serif]cd 2010*[/FONT]
```[B]

[/B]**[FONT=Verdana, sans-serif]Step 3[/FONT]**
 ```
[FONT=Verdana, sans-serif]gedit [/FONT][FONT=Verdana, sans-serif]./os/linux/config.mk[/FONT]
```
[FONT=Verdana, sans-serif]Use the find command to locate [/FONT]*[FONT=Verdana, sans-serif]HAS_WPA_SUPPLICANT[/FONT]*[FONT=Verdana, sans-serif] and make sure it is set to y for yes. It should look like this when finished:[/FONT]
 [FONT=Verdana, sans-serif]HAS_WPA_SUPPLICANT=y[/FONT]
 

 [FONT=Verdana, sans-serif]Use the find command to locate [/FONT]*[FONT=Verdana, sans-serif]HAS_NATIVE_WPA_SUPPLICANT_SUPPORT[/FONT]*[FONT=Verdana, sans-serif] and make sure it is set to y for yes. It should look like this when finished:[/FONT]
 [FONT=Verdana, sans-serif]HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y[/FONT]
 

 [FONT=Verdana, sans-serif]Close and save this file.[/FONT]
 

 **[FONT=Verdana, sans-serif]Step 4[/FONT]**
 ```
[FONT=Verdana, sans-serif]gedit [/FONT][FONT=Verdana, sans-serif]./common/cmm_wpa.c[/FONT]
```*[FONT=Verdana, sans-serif]You will get a message that the character encoding was not recognised, choose &#8222;Western&#8220; and press &#8222;Retry&#8220;[/FONT]*
 

 [FONT=Verdana, sans-serif]Use the find command to locate [/FONT]*[FONT=Verdana, sans-serif]MIX_CIPHER_NOTUSE[/FONT]*[FONT=Verdana, sans-serif]. Replace the entire line (keep on one line) with this code:[/FONT]
 [FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;[/FONT]
[FONT=Verdana, sans-serif]
[/FONT][FONT=Verdana, sans-serif]Attention, please make sure you do not leave a part of the original comment after the line break. This is a source of potential later problems.
[/FONT]
**[FONT=Verdana, sans-serif]Step 5[/FONT]**
 [FONT=Verdana, sans-serif]Now we need to compile a new module, in order to do so we first need to have "gcc" installed. If it is not yet installed please do so by following the steps as below. In order to install gcc you need to have a wired internet connection or 3G internet connection at least.[/FONT]
 

 [FONT=Verdana, sans-serif]Go to System[/FONT]
 [FONT=Verdana, sans-serif]Go to Administration[/FONT]
 [FONT=Verdana, sans-serif]Klick Synaptic Package Manager[/FONT]
 [FONT=Verdana, sans-serif]Look for &#8222;gcc&#8220; and choose it to be installed[/FONT] if it is not yet there
 

 [FONT=Verdana, sans-serif]After successfully installing gcc please execute the following commands step by step in a terminal window.[/FONT]
 

 ```
[FONT=Verdana, sans-serif]sudo make[/FONT]
[FONT=Verdana, sans-serif]sudo make install[/FONT]
[FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT]
[FONT=Verdana, sans-serif]sudo rmmod rt2860sta[/FONT]
```

**[FONT=Verdana, sans-serif]Step 6[/FONT]**
 [FONT=Verdana, sans-serif]Rename the old [/FONT]*[FONT=Verdana, sans-serif]rt2860sta.ko[/FONT]*[FONT=Verdana, sans-serif] driver file to [/FONT]*[FONT=Verdana, sans-serif]rt2860sta.ko.dist[/FONT]*[FONT=Verdana, sans-serif] using:[/FONT]
 
```
[FONT=Verdana, sans-serif]sudo mv /lib/modules/2.6.*/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist[/FONT]
```
[FONT=Verdana, sans-serif]Attention: you need to replace the * with the actual directory name of your kernel, please check the folder name with Nautilus.[/FONT]
 

 **[FONT=Verdana, sans-serif]Step 7[/FONT]**
 ```
[FONT=Verdana, sans-serif]sudo depmod -a[/FONT]
[FONT=Verdana, sans-serif]sudo modprobe rt2860sta[/FONT]
```[FONT=Verdana, sans-serif]
After you issue the previous command you should see the Desktop top panel wireless icon come to life as it tries to connect. You will be prompted for a WPA password. Give it a little while and it should connect.[/FONT]
 

 [FONT=Verdana, sans-serif]Not sure this command is necessary but you can use if the Wireless isn&#8217;t started automatically.[/FONT]
 [FONT=Verdana, sans-serif]sudo ifconfig wlan0 up[/FONT]
 

 **[FONT=Verdana, sans-serif]Step 8[/FONT]**
 [FONT=Verdana, sans-serif]Okay at this point you have made a lot of progress and should be happily surfing.[/FONT]
 

 [FONT=Verdana, sans-serif]But, and this is a biggie, what happens if you reboot? Unfortunately, you are back at square one without the RT2860 driver being loaded after a reboot. To remedy this situation, continue with step 9.[/FONT]
 

 **[FONT=Verdana, sans-serif]Step 9[/FONT]**
 [FONT=Verdana, sans-serif]Open a terminal window[/FONT]
 ```
[FONT=Verdana, sans-serif]cd 2010*[/FONT]
[FONT=Verdana, sans-serif]cd os[/FONT]
[FONT=Verdana, sans-serif]cd linux[/FONT]
[FONT=Verdana, sans-serif]sudo cp rt2860sta.ko /lib/modules/2.6.*/kernel/drivers/staging/rt2860/[/FONT]
```[FONT=Verdana, sans-serif]
Attention: you need to replace the * with the actual directory name of your kernel, same as step 6[/FONT]
 

 **[FONT=Verdana, sans-serif]Step 10[/FONT]**
 [FONT=Verdana, sans-serif]Update your modules boot file with the following command:[/FONT]
 

 ```
[FONT=Verdana, sans-serif]gksudo gedit /etc/modules[/FONT]
```[FONT=Verdana, sans-serif]
Ad[/FONT][FONT=Verdana, sans-serif]d the &#8222;[/FONT]*[FONT=Verdana, sans-serif]rt2860sta&#8220;[/FONT]*[FONT=Verdana, sans-serif] on a line at the end of the file and close and save the file.[/FONT]
 

 **[FONT=Verdana, sans-serif]Step 11[/FONT]**
 [FONT=Verdana, sans-serif]Reboot and check to see that you are now automatically connecting to your wireless network![/FONT]
 

 [FONT=Verdana, sans-serif]I hope it works for you as well[/FONT]

---

### Post by hmmr on 2010-05-08
Thanks a lot.

This solution worked perfectly.

I had a similar problem on a akoya mini E1210, which uses the same wifi chips.

Now happily surfing away on my lucid netbook :):p

---

### Post by adamd1972 on 2010-05-08
Thanks so much for putting this out here.  Worked perfectly for me on my Encore ENLWI-N wireless PCI adapter.

---

### Post by Sven6210 on 2010-05-08
[FONT=Verdana, sans-serif]You should not thank me but Chris Baker and many others. I only posted it here so that Ubuntu users can easily find it. The real brain work was done by others in the Ubuntu community.
[/FONT][FONT=Verdana, sans-serif][/FONT]

---

### Post by Sven6210 on 2010-05-09
By the way, after an update of the kernel you will need to repeat the changes from above. I recommend to redo all steps (except the downloading of the driver if there is no new one available). The "*" is a new (latest) directory with a new (latest) kernel.

I just had to do that after I updated to the latest kernel yesterday.

---

### Post by eltonw on 2010-05-09
> **Sven6210 said:**
> By the way, after an update of the kernel you will need to repeat from Step 9. The "*" is a new directory with a new kernel.

I just had to do that after I updated to the latest kernel yesterday.

Rather than having to *[COLOR="DarkRed"]re-compile the driver each time there is an update[/COLOR]*, I installed LUCID thus:
[http://ubuntuforums.org/showthread.php?p=9203922#post9203922]("http://ubuntuforums.org/showthread.php?p=9203922#post9203922 ") [#136]

and I am now running the **2.6.33** kernel, since the first kernel update **from the** Canonical **channel** broke my wireless connection again.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/")

HTH

---

### Post by mkloch on 2010-05-09
I can confirm that the method described above worked for me on my EeePc 1000H with Kubuntu 10.04 install. I'm glad that the process was described so well here. Going through all the steps is not very difficult, but still, that would be nice if things could just work out of the box like in Karmic.

---

### Post by Sven6210 on 2010-05-10
Dear eltonw,

Actually it is not necessary to compile the driver each time you make a kernel update. It is enough to copy the once compiled kernel into the directory with the updated kernel. this is done with the command:

[FONT=Verdana, sans-serif]sudo cp rt2860sta.ko  /lib/modules/2.6.*/kernel/drivers/staging/rt2860/

The command must be launched from the directory where the module is. But it is not necessary to recompile the kernel. Once done it is fine. So not such a big hassle any more.

Best regards

Sven
[/FONT]

---

### Post by nucleuskore on 2010-05-11
Hi  Sven6210

Thank you for your efforts. I have managed to install the driver; I however have to test it at home where I have a WPA network. I will update this post in another six hours from now. 

In the mean time I wanted to point out a few things:

> **Sven6210 said:**
>  [FONT=Verdana, sans-serif]After successfully installing gcc please execute the following commands step by step in a terminal window.[/FONT]
 

 [FONT=Verdana, sans-serif]sudo make[/FONT]
 [FONT=Verdana, sans-serif]sudo make install[/FONT]
 [FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT]
 [FONT=Verdana, sans-serif]sudo rmmod rt2860sta[/FONT]

Now the problem is that inspite  of giving **sudo ifconfig wlan0 down** , the next command gives a failure message saying that the module is still in use. I am guessing that this is probably due to the fact that the connection is being handled by network manager applet. So if you disconnect the network using the network manager applet situated near the clock, and then give **sudo rmmod rt2860sta** , it executes without any error messages.
 
> 
 **[FONT=Verdana, sans-serif]Step 6[/FONT]**
 [FONT=Verdana, sans-serif]Rename the old [/FONT]*[FONT=Verdana, sans-serif]rt2860sta.ko[/FONT]*[FONT=Verdana, sans-serif] driver file to [/FONT]*[FONT=Verdana, sans-serif]rt2860sta.ko.dist[/FONT]*[FONT=Verdana, sans-serif] using:[/FONT]
 

 [FONT=Verdana, sans-serif]sudo mv /lib/modules/2.6.*/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist[/FONT]
 

 [FONT=Verdana, sans-serif]Attention: you need to replace the * with the actual directory name of your kernel, please check the folder name with Nautilus.[/FONT]
 

Please note that the above command **mv** does not rename but moves the file rt2860.sta from /lib/modules/2.6.*/kernel/drivers/staging/rt2860/ to the current folder and saves it as rt2860sta.ko.dist
You can verify this by giving sudo ls /lib/modules/2.6.*/kernel/drivers/staging/rt2860/ and seeing that your folder is now empty. The folder is offcourse repopulated in Step 9.

---

### Post by Sven6210 on 2010-05-12
> **nucleuskore said:**
> 
Now the problem is that inspite  of giving **sudo ifconfig wlan0 down** , the next command gives a failure message saying that the module is still in use. I am guessing that this is probably due to the fact that the connection is being handled by network manager applet. So if you disconnect the network using the network manager applet situated near the clock, and then give **sudo rmmod rt2860sta** , it executes without any error messages.
 
 I did not get this error message. Obviously network manager did not use the WiFi module when I did the change as I first needed to run the patch before I was able to use it at all. If you managed to get your WiFi to work without the patch the reason for the error message might be what you guessed.

> **nucleuskore said:**
> 
Please note that the above command **mv** does not rename but moves the file rt2860.sta from /lib/modules/2.6.*/kernel/drivers/staging/rt2860/ to the current folder and saves it as rt2860sta.ko.dist
You can verify this by giving sudo ls /lib/modules/2.6.*/kernel/drivers/staging/rt2860/ and seeing that your folder is now empty. The folder is offcourse repopulated in Step 9.

You are absolutely right, 'mv' moves a file, but in the above example it actually moves and renames the file. Actually I guess we could leave that step if we would accept not being able to restore the previous original module.

Apart from that I hope everything worked out for you also on a WPA WiFi.

---

### Post by nucleuskore on 2010-05-12
Am sorry to report that it did not work for me. It repeatedly asks for the WPA password. I use AES encryption. 

Anyway I am trying to install as above with the mainline kernel linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb as this does not have the wireless module at all.

**Update: No luck, didn't work** :(

---

### Post by nucleuskore on 2010-05-13
Am using the card with the windows driver. See here
[http://ubuntuforums.org/showthread.php?p=9289963](http://ubuntuforums.org/showthread.php?p=9289963)

---

### Post by BothWayz on 2010-05-13
> **Sven6210 said:**
> 

 **[FONT=Verdana, sans-serif]Step 6[/FONT]**
 [FONT=Verdana, sans-serif]Rename the old [/FONT]*[FONT=Verdana, sans-serif]rt2860sta.ko[/FONT]*[FONT=Verdana, sans-serif] driver file to [/FONT]*[FONT=Verdana, sans-serif]rt2860sta.ko.dist[/FONT]*[FONT=Verdana, sans-serif] using:[/FONT]
 

 [FONT=Verdana, sans-serif]sudo mv /lib/modules/2.6.*/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist[/FONT]
 

 [FONT=Verdana, sans-serif]Attention: you need to replace the * with the actual directory name of your kernel, please check the folder name with Nautilus.[/FONT][FONT=Verdana, sans-serif][/FONT]

I was following the directions up until here but now I'm stumped. How do I know what the directory name of my kernel is?

---

### Post by Sven6210 on 2010-05-14
> **BothWayz said:**
> I was following the directions up until here but now I'm stumped. How do I know what the directory name of my kernel is?
In order to identify the name of the directory where your kernel is open Nautilus and move to the root directory. Then go to the folder "lib" and then the folder "modules". In this folder you will see one or several folders starting with "2.6.". The one with the highest number (the latest kernel) is the right one. use the whole folder name as shown and replace the "2.6.*" with it.

I hope this helps you. If you are still struggling please let me know.

---

### Post by olalaaa on 2010-05-17
> **Sven6210 said:**
> In order to identify the name of the directory where your kernel is open Nautilus and move to the root directory. Then go to the folder "lib" and then the folder "modules". In this folder you will see one or several folders starting with "2.6.". The one with the highest number (the latest kernel) is the right one. use the whole folder name as shown and replace the "2.6.*" with it.

I hope this helps you. If you are still struggling please let me know.
Sven, please explain me - as above - what to put where it said 

cd 2010* (?????)

What is needed to put after 2010 instead of "*"?? This was in a previous page.

Thank you.

Do we have any folder called 2010 ??

---

### Post by aldeby on 2010-05-17
Basically when you type in the root terminal 
```
mv /lib/modules/2.6.
```
instead of typing the * (asterisk) hit the TAB button twice. It will then show all the existing directories starting with 2.6. 
You should choose the one that matches with your currently running system (you can understand this by checking the output of command ```
uname -r
```) 99% of the times the one you should choose is the highest number.

---

### Post by Sven6210 on 2010-05-19
All right, step by step how to identify the name of the directory:

1. Open a terminal window
2. Enter: [FONT=Verdana, sans-serif]cd /lib/modules/
3. Enter: ls

Now you will see all the available directories with kernels. They start with "[/FONT][FONT=Verdana, sans-serif]2.6.". Look for the name of the directory with the latest kernel (highest number) and not the whole name of the directory.

Under step 6 of the manual you replace the "[/FONT][FONT=Verdana, sans-serif]2.6.*" with the name of the directory you just identified.

Hope it works this time

Sven
[/FONT]

---

### Post by NigelLH on 2010-05-20
Hi Sven

Earlier you said not to thank you as others had done the hard work. What you have done is provide a pretty straight forward way of steps to follow that a Linux newbie such as myself can follow and for that I do thank you.

For those reading, I have an Asus EEE PC 1000H running Eeebuntu V3 with the 10.04 update. Following the steps that Sven provided it worked first time.

Now it would be great for the fix to be in the Linux Kernel, but that is a separate question and it should be pretty easy to save the RT2860 file somewhere and after an upgrade, just have a script to place it back in the Kernel

As a question, is it possible to save the file somewhere that is independent of the Kernel and then specify that in Step 10 in the /etc/modules file? In this way, if the Kernel is ever changed, it would still start the file.

Thanks, NigelLH

---

### Post by ^_Pepe_^ on 2010-05-20
Hi all,

To all those this method doesn't work, please, note that rt2860 standard driver from 2.6.32 kernel, DOES work out-of-the-box with WEP security.

I'm a little bit afraid to change to new driver, but I'll do it when I get a couple of free hours.

Unfortunately my router has only WPA with "TKIP or AES" option, and therefore I had several problems in the past with my medion akoya mini.

I'll keep informing of my updates... :)

---

### Post by NigelLH on 2010-05-20
Hi, I understand the concern, the trouble with solving it locally on the wireless access point is that the solution will only work with that access point. By solving the solution on the computer, WPA is no longer an issue where ever you try to connect.

As a Linux newbie (I installed it on Sunday!) I decided that by trying the fix, if things went wrong, it was not to big a deal to reinstall it.

One advantage is that having the /home directory as a separate partition means that re-installing Linux doesn't overwrite it and you can specify it in the installation process.

I hope all goes well when you try it!

NigelLH

---

### Post by Sven6210 on 2010-05-21
Dear Pepe,

Due to the fact that WEP is not considered to be safe any more I suggest to use WPA for all WiFi connections. All my WiFi access points (actually I operate three of them at different locations) use WPA. And I also recommend everybody to change the admin password for the WiFi access points.

Security first, you would also do not leave your car parked unlocked in Paris, London, Berlin, New York or wherever (to be political correct I just mention cities that came to my mid and I do not think that they are more or less dangerous than others).

Best regards

Sven

---

### Post by NigelLH on 2010-05-21
I suspect you might have meant "I hardly suggest to use WEP for any WiFi connection." Which is my understanding.

---

### Post by Sven6210 on 2010-05-23
> **NigelLH said:**
> I suspect you might have meant "I hardly suggest to use WEP for any WiFi connection." Which is my understanding.

You are absolutely right, I updated my above quote. Now it should be O.K.

---

### Post by CapedCrusader on 2010-05-27
Thanks a million Sven! Complicated but worked:)

---

### Post by Sven6210 on 2010-06-01
Is it really that complicated ;)

I am glad it worked for you.

---

### Post by LucidLuvah on 2010-06-01
> **Sven6210 said:**
> Is it really that complicated ;)

I am glad it worked for you.


Not complicated, but still doesn't work for me. :(

I'm only able to access my WNR3500 802.11N with WEP.  Any thoughts?  I've tried WPA (TKIP) and WPA2(AES) but no joy.

Thanks!

---

### Post by Sven6210 on 2010-06-08
> **LucidLuvah said:**
> Not complicated, but still doesn't work for me. :(

I'm only able to access my WNR3500 802.11N with WEP.  Any thoughts?  I've tried WPA (TKIP) and WPA2(AES) but no joy.

Thanks!

Unfortunately I can not help you. The above described way has worked very well for my EeeBox B202. Are you sure you did every step according to the manual? It rather sounds to me that you do not use the newly compiled module.

---

### Post by Holger74 on 2010-06-09
> **Sven6210 said:**
> [FONT=Verdana, sans-serif]After successfully installing gcc please execute the following commands step by step in a terminal window.[/FONT]
 

 [FONT=Verdana, sans-serif]sudo make[/FONT]
 [FONT=Verdana, sans-serif]sudo make install[/FONT]
 [FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT]
 [FONT=Verdana, sans-serif]sudo rmmod rt2860sta[/FONT]

Hello Sven,

my problem is after typing the last command
[FONT=Verdana, sans-serif]sudo rmmod rt2860sta[/FONT]
this error appears:

ERROR: Module rt2860sta does not exist in /proc/modules

I followed every step of your first posting, whats wrong?

i am using an acer revo r3610 but it have the same wlan chipset.

---

### Post by Sven6210 on 2010-06-09
> **Holger74 said:**
> Hello Sven,

my problem is after typing the last command
[FONT=Verdana, sans-serif]sudo rmmod rt2860sta[/FONT]
this error appears:

ERROR: Module rt2860sta does not exist in /proc/modules

I followed every step of your first posting, whats wrong?

i am using an acer revo r3610 but it have the same wlan chipset.


Dear Holger,

Please let me summarize:

[FONT=Verdana, sans-serif]I understand that you successfully run "sudo make[/FONT]"
[FONT=Verdana, sans-serif]I understand that you successfully run "[/FONT]  [FONT=Verdana, sans-serif]sudo make install[/FONT]"
[FONT=Verdana, sans-serif]I understand that you successfully run "[/FONT]  [FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT]"
 [FONT=Verdana, sans-serif]I understand you get the following error message when running "sudo rmmod rt2860sta[/FONT]"

   ERROR: Module rt2860sta does not exist in /proc/modules

Is that right?

In that case I would like to ask you - even if it sounds stupid - whether you are sure you are using the "Ralink RT2860 WiFi chipset"? And whether you are using Ubuntu 10.04? If you are sure for both questions, what happens if you just proceed with the description (continue with step 6). If the module "rt2860sta" does not exist you should not have any trouble running the other commands. And theoretically it should work.

Best regards and good luck

Sven

---

### Post by Swiss-Cheese on 2010-06-13
I am new to Ubuntu and linux so I apologize in advance for what are probably lame questions.

I have attempted this fix to get my eeePC 901 to connect to the internet properly (it links once in a while).

I reached Step 5 but cant seem to enter the 

[FONT=Verdana, sans-serif]sudo make[/FONT]
 [FONT=Verdana, sans-serif]sudo make install[/FONT]
 [FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT]
 [FONT=Verdana, sans-serif]sudo rmmod rt2860sta

When I enter the first line I a message requesting a password.  After I enter my password I get the message ***** No targets specified and no makefile found. Stop.

Not sure what to do.  

Ubuntu so much faster and stable than XP (where wireless works fine) but without wifi, practically useless to me :-(

Are there any "simple" fixes for people like me?

Thanks,
Charles




[/FONT]

---

### Post by nucleuskore on 2010-06-13
see this [http://ubuntuforums.org/showthread.php?p=9304000](http://ubuntuforums.org/showthread.php?p=9304000)

---

### Post by bazzal1941 on 2010-06-13
sven6210 thank you for a simple solution to this problem. The only glitch I had is that my system does not refer to wlan0 but to ra0. Once I discovered this all went smoothly. Hope this helps somebody.

Asus 901 Ubuntu NR 10.04

---

### Post by amitabhishek on 2010-06-13
> **nucleuskore said:**
> see this [http://ubuntuforums.org/showthread.php?p=9304000](http://ubuntuforums.org/showthread.php?p=9304000)

Checked your ndiswrapper method too; didn't work for me.

[IMG][[IMG]http://img294.imageshack.us/img294/9283/screenshotqs.th.png[/IMG]](http://img294.imageshack.us/i/screenshotqs.png/)  Uploaded with [ImageShack.us](http://imageshack.us)[/IMG]


Mine is EEEPC 1001P. Could this be the reason? Any other ideas? 

BTW you dont visit TDF these days?

Edit: Got the correct wifi driver. It works now! :)

---

### Post by Sven6210 on 2010-06-24
> **Swiss-Cheese said:**
> I am new to Ubuntu and linux so I apologize in advance for what are probably lame questions.

I have attempted this fix to get my eeePC 901 to connect to the internet properly (it links once in a while).

I reached Step 5 but cant seem to enter the 

[FONT=Verdana, sans-serif]sudo make[/FONT]
 [FONT=Verdana, sans-serif]sudo make install[/FONT]
 [FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT]
 [FONT=Verdana, sans-serif]sudo rmmod rt2860sta

When I enter the first line I a message requesting a password.  After I enter my password I get the message ***** No targets specified and no makefile found. Stop.

Not sure what to do.  

Ubuntu so much faster and stable than XP (where wireless works fine) but without wifi, practically useless to me :-(

Are there any "simple" fixes for people like me?

Thanks,
Charles




[/FONT]

Hi Charles,

Sorry for getting back so late - I have been travelling and hardly had time to check my private mails or this forum.

The error message "[FONT=Verdana, sans-serif]No targets specified and no makefile  found" [/FONT]indicates that you are in the wrong directory. 

Under step 2 of my description I explain where to upack the downloaded file and how to change into that respective directory.

> **Swiss-Cheese said:**
> 
**[FONT=Verdana, sans-serif]Step 2[/FONT]**
 [FONT=Verdana, sans-serif]Open and extract the downloaded file  to your Home directory. Accept the standard folder and to not change the  name[/FONT]
 

 [FONT=Verdana, sans-serif]Open a terminal window[/FONT]
 [FONT=Verdana, sans-serif]cd 2010*[/FONT]


The error message indicates to me that you are not in the respective directory. Please make sure you are really in the directory you unpacked.

I hope this helps you.

Good luck

Sven

---

### Post by el_heffe on 2010-06-25
OK, running 10.4 here.  Here is the output of my uname -r
```
@minibuntu:~$ uname -r
2.6.32-22-generic

```

Here is the output of my sudo make
```
sudo make
make -C tools
make[1]: Entering directory `/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/tools'
/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/Makefile
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/../../common/cmm_wpa.o
/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/../../common/cmm_wpa.c: In function ‘RTMPMakeRSNIE’:
/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/../../common/cmm_wpa.c:2416: error: expected expression before ‘WPA_MIX_PAIR_CIPHER’
make[2]: *** [/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/../../common/cmm_wpa.o] Error 1
make[1]: *** [_module_/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [LINUX] Error 2

```
Then, for giggles, the output from my sudo make install:
```
sudo make
make -C tools
make[1]: Entering directory `/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/tools'
/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/Makefile
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/../../common/cmm_wpa.o
/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/../../common/cmm_wpa.c: In function ‘RTMPMakeRSNIE’:
/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/../../common/cmm_wpa.c:2416: error: expected expression before ‘WPA_MIX_PAIR_CIPHER’
make[2]: *** [/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux/../../common/cmm_wpa.o] Error 1
make[1]: *** [_module_/home/bheffron/2010_01_29_RT2860_Linux_STA_v2.3.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [LINUX] Error 2

```

So, I see from one of the lines that there is something wrong with the cmm_wpa.c but when I check it I can see nothing wrong with it.  I have pasted the appropriate section below this.

```
UCHAR		p_offset;
WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;// it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode

```


It is all on one line as specified in the how-to.  Also, I sudo cp'd the rt2860sta.ko to /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless because I had been getting errors about the file not being there.  Not too sure where I am going wrong here and would love some help on this.

---

### Post by stuberman on 2010-07-20
Thanks for the clear directions - worked like a charm using the latest RaLink driver v2.4.0.0
 
I too had a small problem after issuing the wlan0 down command. I simply used the Function F2 keys to disable the WiFi system while continuing the directions.
 
BTW - Had intermittent problems with WPA/WPA2 after upgrading to Easy Peasy v1.6 - Ubuntu Lucid Lynx 10.04 and this resolved the problems with staying connected.

---

### Post by kyle6513 on 2010-07-30
> **el_heffe said:**
> -snip-
you're not meant to add it onto the end, the line is meant to look like this,
> WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;// it provide the more flexible cipher combination in WPA-WPA2 and TKIPAES mode

---

### Post by jv2112 on 2010-08-07
Thanks for the posting. It was a help.

I went through all of the steps and it picks up on the card but never connects. It keeps going through a loop of trying to connect where before (i did the steps) nothing. I have other machines that connoect fine to the router so I know it's not that.

If I watch iwconfig I see it has a signal.

I am using WPA & WPA2 security. It is a new card I picked up so I am staring to suspect I got a bad one.

Thoughts ?

Thanks Again

---

### Post by Sven6210 on 2010-08-08
> **jv2112 said:**
> Thanks for the posting. It was a help.

I went through all of the steps and it picks up on the card but never connects. It keeps going through a loop of trying to connect where before (i did the steps) nothing. I have other machines that connoect fine to the router so I know it's not that.

If I watch iwconfig I see it has a signal.

I am using WPA & WPA2 security. It is a new card I picked up so I am staring to suspect I got a bad one.

Thoughts ?

Thanks Again


This sounds strange. Are you sure that you passed each and every step successfully and without error messages?

The biggest source of mistakes:

[LIST=1]
[*]The archive is not extracted to the home directory - make sure you really extract to the home directory
[*]You have other folders in the home directory starting with "2010" in that case you may have a problem when entering "cd 2010*"
[*]When editing *[FONT=Verdana, sans-serif]"cmm_wpa.c" [/FONT]*you leave a part of the comment from the old command when making the update. In that case you will get an error message when compiling the new module and the rest is not going to work.[I][FONT=Verdana, sans-serif]
[/FONT][/I]
[/LIST]
Please make sure none of the above is the case for you and redo the whole manual. As soon as there is any error message let us know at which stage it happens.

Good luck

Sven

---

### Post by jv2112 on 2010-08-08
Thank You so much for replying. 

After back tracing my steps, banging my head and cursing I found some white space and a character out of place in step 3. 

I corrected and viola -----> ALL SET !!!!!!!!! My wife can now leave me alone. She can surf , email all with a brand new distro and Kernel....



:guitar:8-)=D>

---

### Post by Sven6210 on 2010-08-09
> **jv2112 said:**
> Thank You so much for replying. 

After back tracing my steps, banging my head and cursing I found some white space and a character out of place in step 3. 

I corrected and viola -----> ALL SET !!!!!!!!! My wife can now leave me alone. She can surf , email all with a brand new distro and Kernel....



:guitar:8-)=D>


Great it's working now. And I have to admit that I envy you for your wife - well, rather for having a wife using Ubuntu. I have been trying to convince my partner for weeks but she absolutely wants to stay with her Windows Vista. :(

---

### Post by piment on 2010-08-13
I recently purchased a refurbished ASUS Eee PC 901, removed the original Xandros distribution and installed Ubuntu Netbook 10.04. 

Unfortunately experienced WIFI problems straight away.

Fortunately noticed that my system used the [FONT=Verdana]RT2860 network driver, and found this thread! Followed it and WIFI is working brilliantly.

NB. I used the [/FONT][FONT=Verdana]"**RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)**“ dated **07/16/2010, version 2.4.0.0**[/FONT]

Thanks very much!!!

---

### Post by Sven6210 on 2010-08-14
> **piment said:**
> I recently purchased a refurbished ASUS Eee PC 901, removed the original Xandros distribution and installed Ubuntu Netbook 10.04. 

Unfortunately experienced WIFI problems straight away.

Fortunately noticed that my system used the [FONT=Verdana]RT2860 network driver, and found this thread! Followed it and WIFI is working brilliantly.

NB. I used the [/FONT][FONT=Verdana]"**RT2860PCI/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)**“ dated **07/16/2010, version 2.4.0.0**[/FONT]

Thanks very much!!!


Thank you for sharing the new available driver version 2.4.0.0 with us. I updated the initial instruction and added the new driver there.

---

### Post by brawd on 2010-08-14
Hi Sven,

I plodded on until 

sudo ifconfig wlan0 down

 Then I got the error message 'wlan0: ERROR while getting interface flags: No such device'

I tried a couple of probes if it helps


Iwconfig gives;

lo      no wireless extensions

eth0    no wireless extensions

pan0    no wireless extensions

lshw -c network gives;

description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:ddff0000-ddffffff

Any suggestions gratefully received.

regards,

brawd.

---

### Post by brawd on 2010-08-15
Forget the last message.
I was at the Pub last night bemoaning my wireless and a mate pulled out of his pocket a usb wireless jobbie. I installed it this morning and am now surfing.

Anyone on windows want to buy an Edimax?

regards from a Ubuntu wimp,

brawd.

---

### Post by Sven6210 on 2010-08-15
> **brawd said:**
> Hi Sven,

I plodded on until 

sudo ifconfig wlan0 down

 Then I got the error message 'wlan0: ERROR while getting interface flags: No such device'



You can try:
[FONT=Verdana, sans-serif]sudo ifconfig wlan1 down[/FONT]
[FONT=Verdana, sans-serif]sudo ifconfig wlan2 down[/FONT]

Maybe that helps. Or just continue with the other steps and see whether it works anyway.

Good luck

---

### Post by scobak on 2010-08-17
> **Sven6210 said:**
> You can try:
[FONT=Verdana, sans-serif]sudo ifconfig wlan1 down[/FONT]
[FONT=Verdana, sans-serif]sudo ifconfig wlan2 down[/FONT]

Maybe that helps. Or just continue with the other steps and see whether it works anyway.

Good luck


I had the same error message in response to "sudo ifconfig wlan0 down" and "sudo ifconfig wlan0 up".  I continued with the other steps and it worked perfectly once I rebooted.

Thanks.

---

### Post by finnbuntu on 2010-08-20
Hello all,
There is an even simpler way. Just go into Synaptic and install the linux-backports-wireless-lucid-generic package. You do not have to keep repeating a command every time you update the kernel, which is the good thin. It worked for my Eee PC 901 and it should work for you.
Hope it works,
finnbuntu

---

### Post by iokhahon on 2010-08-21
I just had to post my thanks for this solution, flaky Wifi almost had me reaching for the WIndows recovery CD which is a shame because apart from WiFi Ubuntu 10.04 Netbook edition worked well on my eeePC 1000HD. With the source patch applied, I can connect to my WPA wireless router in just a couple of seconds every time, before the fix I only ever managed to connect once before the patch and that connection disappeared after about 30 minutes.
Ubuntu and all the good people who help to improve it (and the end user experience) rock!

---

### Post by tyling81 on 2010-08-22
Hi Sven, I'd follow the instruction til step 5 and I got the error message below

ray@RayzEeePC:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo Thankmake
[sudo] password for ray: 
make -C tools
make[1]: Entering directory `/home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/2.6.32-24-generic-pae/build SUBDIRS=/home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make: *** /lib/modules/2.6.32-24-generic-pae/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

Is there anything I could rectify? before proceed into next step?
 Thanks

---

### Post by Sven6210 on 2010-08-22
> **tyling81 said:**
> Hi Sven, I'd follow the instruction til step 5 and I got the error message below

ray@RayzEeePC:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo Thankmake
[sudo] password for ray: 
make -C tools
make[1]: Entering directory `/home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/2.6.32-24-generic-pae/build SUBDIRS=/home/ray/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make: *** /lib/modules/2.6.32-24-generic-pae/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

Is there anything I could rectify? before proceed into next step?
 Thanks


I am quite sure the problem occurred in step 4 when editing [FONT=Verdana, sans-serif]"gedit [/FONT]*[FONT=Verdana, sans-serif]./common/cmm_wpa.c"[/FONT]*

[FONT=Verdana, sans-serif]Use the find command to locate [/FONT]*[FONT=Verdana, sans-serif]MIX_CIPHER_NOTUSE[/FONT]*[FONT=Verdana, sans-serif]. Replace the entire line (keep on one line) with this code:[/FONT]
 [FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;[/FONT]
[FONT=Verdana, sans-serif]
[/FONT][FONT=Verdana, sans-serif]I think you left a part of the original comment in an additional line and saved the file with this additional line. When trying to compile you get an error message as the remaining comment is not considered as a comment any more and can not be interpreted.

It also happened to me once. Try again and[/FONT] make sure you delete the original line including the comment. I once had the same problem when editing the file.

Good luck

Sven

---

### Post by Sven6210 on 2010-08-22
> **finnbuntu said:**
> Hello all,
There is an even simpler way. Just go into Synaptic and install the linux-backports-wireless-lucid-generic package. You do not have to keep repeating a command every time you update the kernel, which is the good thin. It worked for my Eee PC 901 and it should work for you.
Hope it works,
finnbuntu

Just to avoid any misunderstanding, even when installing the "linux-backports-wireless-lucid-generic package", the instruction for compiling a new WiFi module has to be completed once. The new package allows to use the earlier compiled module with a new kernel.

When a kernel update happens you have two possibilities:
1. Install the linux-backports-wireless-lucid-generic package and the old module will work with the new kernel
2. You redo this manual and you compile a new module for the new kernel

No. 1 is the easier one. 

Thank you for the advice.

---

### Post by tyling81 on 2010-08-24
VOID RTMPMakeRSNIE(
    IN  PRTMP_ADAPTER   pAd,
    IN  UINT            AuthMode,
    IN  UINT            WepStatus,
    IN    UCHAR            apidx)
{
    PUCHAR        pRsnIe = NULL;            // primary RSNIE
    UCHAR         *rsnielen_cur_p = 0;    // the length of the primary RSNIE         
    UCHAR        *rsnielen_ex_cur_p = 0;    // the length of the secondary RSNIE          
    UCHAR        PrimaryRsnie;            
    BOOLEAN        bMixCipher = FALSE;    // indicate the pairwise and group cipher are different//
    UCHAR        p_offset;        
    WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;
        
    rsnielen_cur_p = NULL;
    rsnielen_ex_cur_p = NULL;
 

Hi Sven, this is the replacement yet when i compile it with
sudo Make
Same error shown

---

### Post by Dubbayoo on 2010-08-29
What bitrate are you guys showing for this card? I'm showing 54 Mb/s although yesterday it was 65 Mb/s and occasionally 72 Mb/s.



```
steve@dubbayoo:~$ **iwconfig wlan0**
wlan0     Ralink STA  ESSID:"QuickMagnolia"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 68:7F:74:3B:93:EB   
         ** Bit Rate=54 Mb/s**   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-21 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


Is there another PCI card that "really just works" with 802.11n?

---

### Post by NuclearThermalPropulsion on 2010-09-04
Hello, really new user here, and I'm having problems really early on :S

Namely, I cannot even unpack the damn folder I downloaded from the Ralink page. I try to unpack the '2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2' file, but the program gives an error saying:
'bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors'

What should I do?

---

### Post by gtaskeraus on 2010-09-05
I had the same unpacking problem.  What I did (by accident) was to change the name of the file from *tar* to *tar01* and let it unpack.


The unpacked file was called *tar01. When I tried to unpack that it died on me.

I then renamed it back to *tar.  After unpacking that I had the desired folders out.

I'm still waiting to see if it works properly for me but so far the connection is still holding good.

---

### Post by Sven6210 on 2010-09-05
> **NuclearThermalPropulsion said:**
> Hello, really new user here, and I'm having problems really early on :S

Namely, I cannot even unpack the damn folder I downloaded from the Ralink page. I try to unpack the '2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2' file, but the program gives an error saying:
'bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors'

What should I do?


Please try the following:
Rename the downloaded file from
   2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
to
   2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar

So actually you need to remove the '.bz2' ending. After that you can double-click the file and 'File Roller' can open it. Please unpack the directory into your home directory so that the manual can work.

Hope that solves your issue

Sven

---

### Post by evozero on 2010-09-09
Hi All,
Can anyone confirm they have this card running reliably using wpa2,tkip aes?
I have compiled the  2.4.0.0 RaLink driver following the instructions to edit config.mk & cmm_wpa.c.
Copied over the new rt2860sta.ko to my 2.6.32-25-generic folder, the module loads fine and connects to my wireless securely.
But the connection is very unstable, if you are streaming music you get about 2 minutes before the streaming stops, I don't receive any errors in network manager, but i have to manually disconnect and reconnect to any pages working again. The other issue i know is the latency, really laggy and unresponsive.
I have a dual boot machine and the card work flawlessly in win7, no drops, no speed issues and 100 times more responsive.
I only bought this card a few days back, due to my US robotic card no longer being supported, This is the card everyone recommends for linux and yet the bug priority is low?
Is this really solved and fully tested?
Please Help
Thanks
Ian

---

### Post by stijnblommerde on 2010-09-10
> **Sven6210 said:**
> Dear Holger,

Please let me summarize:

[FONT=Verdana, sans-serif]I understand that you successfully run "sudo make[/FONT]"
[FONT=Verdana, sans-serif]I understand that you successfully run "[/FONT]  [FONT=Verdana, sans-serif]sudo make install[/FONT]"
[FONT=Verdana, sans-serif]I understand that you successfully run "[/FONT]  [FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT]"
 [FONT=Verdana, sans-serif]I understand you get the following error message when running "sudo rmmod rt2860sta[/FONT]"

   ERROR: Module rt2860sta does not exist in /proc/modules

Is that right?

In that case I would like to ask you - even if it sounds stupid - whether you are sure you are using the "Ralink RT2860 WiFi chipset"? And whether you are using Ubuntu 10.04? If you are sure for both questions, what happens if you just proceed with the description (continue with step 6). If the module "rt2860sta" does not exist you should not have any trouble running the other commands. And theoretically it should work.

Best regards and good luck

Sven

I had the same problem as holger. the solution of Sven worked for me. So, it works to continue with step 6, if you receive the error in step 5.

---

### Post by bolojo on 2010-09-12
I have to thank you SVEN6210! You really saved me. I have an EEE PC 901 with Ubuntu Lucid Lynx 10.04 LTS 32 bits and the damn rt2860 wifi n card. After the built of the module i can connect to WPA/WPA2 protected networks and take advantage of WiFi N speed (135Mbps on a Linksys WAG160N) without being wondering

---

### Post by Dubbayoo on 2010-09-12
I have it working but still getting g speeds it seems on 10.04. 

**Bit Rate=54 Mb/s**

---

### Post by jlangholzj on 2010-09-13
Worked for me, kinda

seems as if my connnection with my WPA2 router is very unstable. tends to kick on and off and be generally not happy. However every now and then it WILL connect :evil:

ideas? If you need more info, let me know

---

### Post by Sven6210 on 2010-09-13
> **evozero said:**
> Hi All,
Can anyone confirm they have this card running reliably using wpa2,tkip aes?
I have compiled the  2.4.0.0 RaLink driver following the instructions to edit config.mk & cmm_wpa.c.
Copied over the new rt2860sta.ko to my 2.6.32-25-generic folder, the module loads fine and connects to my wireless securely.
But the connection is very unstable, if you are streaming music you get about 2 minutes before the streaming stops, I don't receive any errors in network manager, but i have to manually disconnect and reconnect to any pages working again. The other issue i know is the latency, really laggy and unresponsive.
I have a dual boot machine and the card work flawlessly in win7, no drops, no speed issues and 100 times more responsive.
I only bought this card a few days back, due to my US robotic card no longer being supported, This is the card everyone recommends for linux and yet the bug priority is low?
Is this really solved and fully tested?
Please Help
Thanks
Ian

It looks like some users her have trouble that the WiFi connection is not stable. Actually I can not really help you in that case. I have a 54 MBit per sec. WiFi network at home (router from German supplier AVM) and it works very stable with all my machines. Also for the Ralink RT2860 I do not have any problem with the stability. I can download even big files of up to 5 GB (I never tried anything bigger than the Debian DVD) and did not face any problem.

In the case your WiFi is not working stable after you have completed this manual you can consider using the Windows driver through ndiswrapper (manual see e.g. [http://ubuntuforums.org/showthread.php?p=9289963](http://ubuntuforums.org/showthread.php?p=9289963)). Maybe this works better for some machines???

Good luck

Sven

---

### Post by Sven6210 on 2010-09-14
For those with an unstable WiFi connection you might have a look on [http://ubuntuforums.org/showthread.php?t=1573039](http://ubuntuforums.org/showthread.php?t=1573039)

It is a combination of this manual (not as detailed) with some additional steps which were not necessary for me but might help those still having trouble.

Good luck

Sven

---

### Post by giantiger on 2010-09-17
> **nucleuskore said:**
> see this [http://ubuntuforums.org/showthread.php?p=9304000](http://ubuntuforums.org/showthread.php?p=9304000)

It worked for me (Hanspree netbook, RaLink RT2860). My wireless was working fine until a software update. I didn't realize it's a driver problem since everything looked fine except kept asking for authentication, and failed to connect with empty ESSID.

I found this instruction is easy to follow.

I didn't try the instruction in original post. Just don't want to compile driver in my netbook. But thanks for sharing your solution.

---

### Post by clight9 on 2010-09-19
Sven, thanks for the instructions.  I am painfully new to linux, and have a few questions.  I would appreciate any help at all.

I actually already installed linux-backports-modules-wireless-lucid-generic, and now my EeePC 901 connects to certain wifi networks flawlessly, including WPA/WPA2 encrypted networks.  However, other connections (from my experience so far, this happens with certain connections that require no password) can't connect at all -- my netbook "sees" the networks, but after a short struggle it will consistently fail to connect.  I have no idea why.  Do you know if following your instructions will help with this problem, or will it make things worse?

Second, I have a REALLY stupid question -- I followed your instructions through almost to the end of Step 5.  I stopped before the command "sudo rmmod rt2860sta" because "sudo ifconfig wlan0 down" had failed and I was told that rt2860sta was in use.  At this point I had second thoughts and simply deleted the unpacked 2010* folder.  My stupid question is: will this halfhearted attempt be likely to screw me up in any way?

Finally, thanks again for helping folks out with this stuff.  I have been tearing my hair out trying to set up the wifi on my new netbook.

EDIT: Before trying these instructions, I thought I'd follow the tip at [http://ubuntuforums.org/showthread.php?t=1466205](http://ubuntuforums.org/showthread.php?t=1466205) and just install linux-backports-modules-wireless-lucid-generic-pae instead of linux-backports-modules-wireless-lucid-generic.  It seems, thus far, to have fixed my previous problems.

---

### Post by ezio cagone on 2010-10-09
Hello I am a newbie everything works until the 

make install

I have installed gcc 4.3 but from a .debian package dowloaded on a windows machine and installed on my xubuntu (broken) warrior. There must be some parts missing on the package I carried accross because it says 

gcc -g bin2h.c -o bin2h
make [1]: gcc: Command not found
make [1]: *** [all] Error 127

When installing the .debian it was trying to download some additional packages which perhaps are the ones missing. 

Where can I find a complete gcc? Is it likely this is the problem?

All help is much appreciated.

P.S. the directory is correct

---

### Post by edco76 on 2010-10-13
Cant get it to work. I DL driver, extract to home directory, when I run the "cd 2010*" command I get

"bash: cd: 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar-3: Not a directory"

---

### Post by edco76 on 2010-10-13
Apparently my problem is getting the driver. When I try to extract I get

"bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now
"

---

### Post by carlenski on 2010-10-13
I had my wireless working with Lucid but things stopped working when I upgraded to Maverick.  
This is on a desktop machine with a wireless adapter ASUS PCE-N13 that uses the Ralink RT2860 chipset.

After lots of scanning through various threads I came across this one and followed the recipe to
build the latest driver.  Things went smoothly to build and install the driver but it still wasn't working.

Finally I realized that the 2.6.35-22 kernel was using the wrong driver:

```
tm@tm-sff:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:71:bc:56:c8:0b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**[COLOR=Red]rt2800pci [/COLOR]**driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:feaf0000-feafffff

```

Just to see what would happen I took the rt2860sta.ko driver I built using this thread and copied it
to the drivers directory, clobbering the old rt2800pci.ko driver:

```
sudo cp rt2860sta.ko /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
```

Wireless is now working.  (Actually it was WPA Authentication that was broken)

This is what I get with the new module

```
tm@tm-sff-desktop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       serial: 70:71:bc:56:c8:0b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR=Red]**driver=RALINK WLAN driverversion=2.4.0.0 **[/COLOR]ip=192.168.2.105 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:feaf0000-feafffff

```

My question is how do I fix this properly?  Why is the new kernel using the wrong driver and how do I
correctly install the proper driver?

---

### Post by Sven6210 on 2010-10-15
> **carlenski said:**
> My question is how do I fix this properly?  Why is the new kernel using the wrong driver and how do I
correctly install the proper driver?


Well, if you did follow this instruction and it worked for you, you actually compiled a new driver (module) and you have solved your problem properly. You only should remind that you install either the backport or you have to redo these steps (compile a new driver) each time you get a kernel update. I decided to recompile the driver each time that I update the kernel.

---

### Post by Sven6210 on 2010-10-15
> **clight9 said:**
> I actually already installed linux-backports-modules-wireless-lucid-generic, and now my EeePC 901 connects to certain wifi networks flawlessly, including WPA/WPA2 encrypted networks.  However, other connections (from my experience so far, this happens with certain connections that require no password) can't connect at all -- my netbook "sees" the networks, but after a short struggle it will consistently fail to connect.  I have no idea why.  Do you know if following your instructions will help with this problem, or will it make things worse?

I do not expect that my manual will make things worse but obviously I can not guarantee it. However I recommend to try it - by trial and error you will learn a lot. Obviously you should not experiment too much if you need the computer for for important business reasons.

> **clight9 said:**
> 
Second, I have a REALLY stupid question -- I followed your instructions through almost to the end of Step 5.  I stopped before the command "sudo rmmod rt2860sta" because "sudo ifconfig wlan0 down" had failed and I was told that rt2860sta was in use.  At this point I had second thoughts and simply deleted the unpacked 2010* folder.  My stupid question is: will this halfhearted attempt be likely to screw me up in any way?

No, deleting the folder 2010* at any stage will not do any harm to your system at all. The manual is designed in a way that you can delete the folder 2010* after you successfully copied the new kernel module to the kernel directory. If you delete the directory before you finished all the steps you just deleted the work you did. You can retry it, don't worry

---

### Post by Sven6210 on 2010-10-15
> **edco76 said:**
> Cant get it to work. I DL driver, extract to home directory, when I run the "cd 2010*" command I get

"bash: cd: 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar-3: Not a directory"

When you download the new driver published in July 2010 you need to rename the downloaded file from

2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
 
to
    
2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar
 
So actually you need to remove the '.bz2' ending. After that you can  double-click the file and 'File Roller' can open it. Please make sure that you extract it to your home directory.

---

### Post by Sven6210 on 2010-10-15
> **ezio cagone said:**
> Hello I am a newbie everything works until the 

make install

I have installed gcc 4.3 but from a .debian package dowloaded on a windows machine and installed on my xubuntu (broken) warrior. There must be some parts missing on the package I carried accross because it says 

gcc -g bin2h.c -o bin2h
make [1]: gcc: Command not found
make [1]: *** [all] Error 127

When installing the .debian it was trying to download some additional packages which perhaps are the ones missing. 

Where can I find a complete gcc? Is it likely this is the problem?

All help is much appreciated.

P.S. the directory is correct


I never installed a package without internet connection and therefore can not offer much help. However I recommend to have a look at the following manuals:

[https://help.ubuntu.com/8.04/add-applications/C/offline.html](https://help.ubuntu.com/8.04/add-applications/C/offline.html)

[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

I hope you will find your answers here. After you manager to successfully install GCC without internet connection please post here and share with us.

---

### Post by Sxynerd on 2010-10-17
I am getting stuck on step 3.  When I search for the file name it returns no results.  When I physically looked through/os/linux I seen nothing either.  

Please help, I am completely lost and have been without wireless for nearly 3 months.

---

### Post by Sven6210 on 2010-10-19
> **Sxynerd said:**
> I am getting stuck on step 3.  When I search for the file name it returns no results.  When I physically looked through/os/linux I seen nothing either.  

Please help, I am completely lost and have been without wireless for nearly 3 months.


I do not really understand your question

You need to be in the home directory when you enter the following command:

```

gedit *./os/linux/config.mk*

```However you should check that you unpacked the package into the home directory. I guess that you made a mistake in step 2 when unpacking the directory and enter the command:

```

cd 2010*

```After that command you should be in the new directory that you jut created when unpacking the directory.

I hope that helps and solves your problem.

---

### Post by Sven6210 on 2010-10-20
Good news for all that are still struggling - I just tried Ubuntu 10.10 on my EeeBox B202 and the WiFi works out of the box for my Ralink RT2860 chipset

---

### Post by tincrowdor on 2010-10-23
> **Sven6210 said:**
> [FONT=Verdana, sans-serif]...[/FONT]
**[FONT=Verdana, sans-serif]...[/FONT]**

 [FONT=Verdana, sans-serif]After successfully installing gcc please execute the following commands step by step in a terminal window.[/FONT]
 

 [FONT=Verdana, sans-serif]sudo make[/FONT]
 [FONT=Verdana, sans-serif]sudo make install[/FONT]
 [FONT=Verdana, sans-serif]sudo ifconfig wlan0 down[/FONT]
 [FONT=Verdana, sans-serif]sudo rmmod rt2860sta[/FONT]
 
...[FONT=Verdana, sans-serif]l[/FONT]

Good instructions, thanks for posting...but I got stuck here. I get some mesages after typing "sudo make" etc in a terminal. I will re-try and re-post if it doesn't work again

Currently posting thru an XP wifi connection as my Ubuntu wifi connection is so erratic...sometimes connects, sometimes stays connected for hours sometimes 1 minute, very often does not reconnect...very frustrating but hope these instructions can fix it

---

### Post by Sven6210 on 2010-10-24
> **tincrowdor said:**
> Good instructions, thanks for posting...but I got stuck here. I get some mesages after typing "sudo make" etc in a terminal. I will re-try and re-post if it doesn't work again

Currently posting thru an XP wifi connection as my Ubuntu wifi connection is so erratic...sometimes connects, sometimes stays connected for hours sometimes 1 minute, very often does not reconnect...very frustrating but hope these instructions can fix it


I guess the mistake happened at step 4

**[FONT=Verdana, sans-serif]Step 4[/FONT]**
 [FONT=Verdana, sans-serif]gedit [/FONT]*[FONT=Verdana, sans-serif]./common/cmm_wpa.c[/FONT]*
 *[FONT=Verdana, sans-serif]You will get a message that the character encoding was not recognised, choose „Western“ and press „Retry“[/FONT]*
 

 [FONT=Verdana, sans-serif]Use the find command to locate [/FONT]*[FONT=Verdana, sans-serif]MIX_CIPHER_NOTUSE[/FONT]*[FONT=Verdana, sans-serif]. Replace the entire line (keep on one line) with this code:[/FONT]
 [FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;[/FONT]
[FONT=Verdana, sans-serif]
[/FONT][B][FONT=Verdana, sans-serif]Attention, please make sure you  do not leave a part of the original comment after the line break. This  is a source of potential later problems.[/FONT]
[/B]
Look at the last sentence, I assume you left a part of the old comment which can not be interpreted and results in errors. It also happened once to me.

Good luck

---

### Post by Shualdon on 2010-10-28
Hi all!
Thank to this tutorial, I was able to use my Edimax EW-7711In (PCI), which uses 3060 chipset. So I figured that I need the rt3562sta driver and not the one that is on the tutorial.
It worked (almost) perfect in 10.04, but now I've upgraded to 10.10, done this tutorial again, but w/o any success.
I can see with lsmod that the driver is running, but I have no network whatsoever.

can anyone help?
thanks :)

---

### Post by Sven6210 on 2010-11-02
> **Shualdon said:**
> Hi all!
Thank to this tutorial, I was able to use my Edimax EW-7711In (PCI), which uses 3060 chipset. So I figured that I need the rt3562sta driver and not the one that is on the tutorial.
It worked (almost) perfect in 10.04, but now I've upgraded to 10.10, done this tutorial again, but w/o any success.
I can see with lsmod that the driver is running, but I have no network whatsoever.

can anyone help?
thanks :)

Sorry, but I do not have any experience on the RT3562 WiFi chipset. What happens if you follow this instruction replacing the driver where necessary?

Do you have a directory "*[FONT=Verdana, sans-serif]/lib/modules/2.6.*/kernel/drivers/staging/[/FONT]rt3562*"?

---

### Post by JayD3e2010 on 2010-11-04
This worked like a charm for me in Ubuntu 10.04; however, early today was attempting to get it to work on Ubuntu Server edition and no dice.  Any suggestions on how to take my current working drivers from my Ubuntu installation and transfer them to a server install.

---

### Post by Chrispy764 on 2010-11-05
Thanks Sven for this info. I know you just posted it here for us to find but I would probably never found it if it was not on the Ubuntu forums. And my thanks to all of those who spent the time to research this and debug the driver for Lucid.

This was my experience:

Steps 1-4 worked fine. Step 5, I already had gcc installed so not an issue. BUT, when I did

"[FONT=Verdana, sans-serif]sudo rmmod rt2860sta"

I got an error, I believe it was 'no such file'??
I ignored it and went on.

Step 6 I did by using <i>sudo nautilus</i> and just renaming it in manually. I prefer using the file browsers over command line. (I am trying to lose my Winodws&reg; habits but I have moments, lol)

Steps 7 I did but I  was still connected with my old Realtek wifi dongle and not my new wifi card, so Step 8 did not apply.

Step 9 I again did with Nautilus by copying and pasting.

And I did step 10. I then shut down and installed my new card and am happily surfing.

I am still connected to a G router but the speed difference in the new Zonet ZEW1642 card is amazing. 
I then copied the rt2860.ko file to my backup folder on a drive that is not affected by upgrades or reinstalls so I can copy it to the kernal folder when needed. 

My only question is for anyone who has used this to go online;

Now when I use Network Manager or ifconfig or iwconfig in terminal, what used to be wlan0 is now ra0. I am assuming that ra means Ralink?? or??

Just curious as long as it works.
[B]
FYI, I just upgraded to Maverick and it still works and using iwconfig, etc and the Network Manager, my wireless now shows up as wlan0 not ra0. [/B] 
[/FONT]

---

### Post by zarkrax on 2010-11-05
This didn't seem to work for me using 10.10

I first of all used the rt2800 module after blacklisting them all the rt2800 and rt2x00 modules I used the bundled rt2860sta module.

Then finally tried the module as per this thread.

The problem was always the same: kept asking for the password on the wpa/wpa2 personal connection.

nm-tool said the status was configuring.

In the end I had to use the NDIS Wrapper as per this thread:

[http://ubuntuforums.org/showthread.php?p=9289963](http://ubuntuforums.org/showthread.php?p=9289963)

But as the OP said on that thread it can take up to three goes before it will connect.


I am running 10.10 64bit installed on windows through wubi.

---

### Post by JayD3e2010 on 2010-11-05
I can confirm that it does not work in 10.10 Server Edition/Desktop.  I simply ended up downloading 10.04 Server Edition and decided to just go with that.

---

### Post by Chrispy764 on 2010-11-06
> **JayD3e2010 said:**
> I can confirm that it does not work in 10.10 Server Edition/Desktop.  I simply ended up downloading 10.04 Server Edition and decided to just go with that.

I should mention that I followed the instructions when I was using Lucid (10.04), I then upgraded to Maverick (10.10), I did nothing else after I upgraded and I am still online. As long as it works I am not going to complain. LOL.

Have you tried upgrading to 10.10 via the Update Center after you get the wifi card working in 10.04? That is what I did and purely by accident, I am sure, the wifi card still works. I am using the Desktop edition but maybe it would work the same with the Server edition.

---

### Post by JayD3e2010 on 2010-11-06
Interesting.  I actually just got the rt2800 chip-set working in 10.10 Server Edition/Desktop Edition, after blacklisting my old driver(rt2800pci) and restarting.  So if you are having trouble with this tutorial working on 10.10, simply follow this tutorial to completion(NOTE:  you will also need to do the final steps that activate the module after reboot), blacklist the driver that your card was using prior to installing the new driver(rt28000pci in my case), and then restart.  You should then be able to do a "sudo ifconfig ra0 up && iwlist ra0 scan" and see the available wireless networks.

---

### Post by JayD3e2010 on 2010-11-06
I may have spoke too soon, I can now see all of the available networks, but yet I have yet to be able to connect to one.

---

### Post by Sven6210 on 2010-11-12
> **Chrispy764 said:**
> I should mention that I followed the instructions when I was using Lucid (10.04), I then upgraded to Maverick (10.10), I did nothing else after I upgraded and I am still online. As long as it works I am not going to complain. LOL.

Have you tried upgrading to 10.10 via the Update Center after you get the wifi card working in 10.04? That is what I did and purely by accident, I am sure, the wifi card still works. I am using the Desktop edition but maybe it would work the same with the Server edition.

Unfortunately I cannot really contribute to the usage of Ubuntu 10.10 due to the fact that my EeeBox with the Ralink RT2860 is still running with Ubuntu 10.04 and will probably remain doing so until the release of the next LTS. As everything works perfectly on that system I do not really see a reason to change anything.

However I tried the live image of Ubuntu 10.10 Desktop 32 bit on my EeeBox and WiFi worked out of the box without requiring any action from my side. As it worked for the live version I assume it should also work for the installed version, unless a kernel update damages anything.

**However I would like to ask a question:**

[LIST=1]
[*]I understood that you were originally using Ubuntu 10.04 and that you used this tutorial in order to get WiFi to work. Did you also install any backport allowing you to use old modules after a kernel update? Or did you redo this tutorial every time you upgraded to a new kernel through the update function?
[*]Which version of ubuntu are you using? 32 or 64 bit? Desktop, server or netbook? Maybe it also depends on the version of Ubuntu people are using?
[/LIST]

Just some thoughts, that might or might not help the one or the other.

Good luck

Sven

---

### Post by Sven6210 on 2010-11-12
> **JayD3e2010 said:**
> I may have spoke too soon, I can now see all of the available networks, but yet I have yet to be able to connect to one.

As far as I understood you installed Ubuntu 10.10 Server Edition on your computer with the Ralink RT2860 chipset. May I suggest you try the live image of Ubuntu 10.10 Desktop Edition 32-bit and see whether WiFi works out of the box? I tried it on my EeeBox and it worked very well.

Maybe this helps to identify the problem more easily?

---

### Post by Sven6210 on 2010-11-12
> **zarkrax said:**
> This didn't seem to work for me using 10.10

I first of all used the rt2800 module after blacklisting them all the rt2800 and rt2x00 modules I used the bundled rt2860sta module.

Then finally tried the module as per this thread.

The problem was always the same: kept asking for the password on the wpa/wpa2 personal connection.

nm-tool said the status was configuring.

In the end I had to use the NDIS Wrapper as per this thread:

[http://ubuntuforums.org/showthread.php?p=9289963](http://ubuntuforums.org/showthread.php?p=9289963)

But as the OP said on that thread it can take up to three goes before it will connect.


I am running 10.10 64bit installed on windows through wubi.

What about giving the live image of 10.10 Desktop Edition a try just to see whether WiFi works here. Maybe the wubi causes any problem? I never used wubi, so it is just an idea. Actually I would expect some problems installing Ubuntu in a Windows. I would always prefer to have a dual boot system with Ubuntu and Windows next to each other on separate partitions.

---

### Post by bourger on 2010-11-15
> **Sven6210 said:**
> 
Actually it is not necessary to compile the driver each time you make a kernel update. It is enough to copy the once compiled kernel into the directory with the updated kernel. this is done with the command:

[FONT=Verdana, sans-serif]sudo cp rt2860sta.ko  /lib/modules/2.6.*/kernel/drivers/staging/rt2860/

The command must be launched from the directory where the module is. But it is not necessary to recompile the kernel. Once done it is fine. So not such a big hassle any more.
[/FONT]

After an upgrade from 2.6.32-21 to 2.6.32-26 and execution of the above command I got this: ```
FATAL: Error inserting rt2860sta (/lib/modules/2.6.32-26-generic/kernel/drivers/staging/rt2860/rt2860sta.ko): Invalid module format
```

---

### Post by Sven6210 on 2010-11-15
> **bourger said:**
> After an upgrade from 2.6.32-21 to 2.6.32-26 and execution of the above command I got this: ```
FATAL: Error inserting rt2860sta (/lib/modules/2.6.32-26-generic/kernel/drivers/staging/rt2860/rt2860sta.ko): Invalid module format
```

If there are major changes in the kernel the WiFi module needs to be recompiled. Alternatively you can install a "backport" package making the old module usable with an updated kernel. I think there was a reference somewhere in this threat or from this threat to another threat, however as I never used it I do not know exactly where it was mentioned.

I just always recompile the WiFi module whenever there is a kernel update - these days there are not that often kernel updates (kernel updates are more frequent after the launch of a distro) and it does not take too long.

---

### Post by Chrispy764 on 2010-11-18
> **Sven6210 said:**
> If there are major changes in the kernel the WiFi module needs to be recompiled. Alternatively you can install a "backport" package making the old module usable with an updated kernel. I think there was a reference somewhere in this threat or from this threat to another threat, however as I never used it I do not know exactly where it was mentioned.

I just always recompile the WiFi module whenever there is a kernel update - these days there are not that often kernel updates (kernel updates are more frequent after the launch of a distro) and it does not take too long.

I had posted that I upgraded to Maverick from Lucid after using this method to install and use my wifi card which is based on a Ralink RT2860 chipset and it still worked without any modifications from me. It appears I was wrong, When looking into the matter it seems for some reason I was using the ndiswrapper and using Windows Wireless Drivers. Removing ndiswrapper made the card useless so I reinstalled Lucid (I can do this with no problems as my home folder is actually a seperate drive that I automount on startup as /home/chris, chris being my user name. I automount it by adding  ***/dev/sbd1   /home/chris   ext4  defaults  0 2*** to /ext/fstab  using *sudo gedit /etc/fstab *before I reboot after (re)installing Lucid. That way all of my files, settings, etc are never overwritten. I used these instruction once again to make the wifi card work. Not a problem, they are VERY good and simple instructions. When I used the update manager to update, It upgraded the kernal from 2.6.32-21 (my default on the boot disk) to 2.6.32-26. Copying the rt2860sta file to the proper place did not work. However, I simply had to follow the instructions to recompile it and it worked just like the first time. I am again going to try upgrading to Maverick and will update this post with what happens.

**I have, since I posted this, updated again to Maverick using the update manger. I chose to not limit the upgrades to only LTS versions, thus I upgraded to 10.10 (Maverick). I only have the folder 2.6.35-22-generic in my /lib/modules folder and have not copied the rt2860sta.ko file to the folder nor have I recompiled it this time. It seems that upgrading to Maverick recognizes the RT2860 card. That may or may not be because I installed it the way this post showed the first time, and then upgraded, but I have not used any backports (that I know of) when upgrading. **
**The fact that my home folder is on a seperate drive and is automounted may or may not be an issue. I am just passing on what I did to get my wifi card to work and that I am using it with Maverick Desktop Edition. ** 

I am running a custom 64bit desktop PC using an Intel Motherboard with a Celeron 3.8ghz processor with 1GB RAM and a 120GB boot drive and a 500GB data drive.

---

### Post by ^_Pepe_^ on 2010-11-19
Hi everyone.

Firstly, thanks to everyone who contribute to this post. It's really helpful.

I can install 2.4 driver in my Medion Akoya Mini, successfully. 

But, I doesn't seem to work after suspension! 

This is my dmesg

```
Nov 19 17:13:09 MAGGI kernel: [  766.397103] ERROR!!! NICInitializeAdapter failed, Status[=0x00000001]
Nov 19 17:13:09 MAGGI kernel: [  766.397563] ERROR!!! H2M_MAILBOX still hold by MCU. command fail
Nov 19 17:13:09 MAGGI kernel: [  766.414206] !!! rt28xx Initialized fail !!!
Nov 19 17:13:11 MAGGI kernel: [  768.722229] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=600
Nov 19 17:13:29 MAGGI kernel: [  786.259921] ERROR!!! BBP write R62 fail
Nov 19 17:13:29 MAGGI kernel: [  786.260311] ERROR!!! BBP write R63 fail
Nov 19 17:13:29 MAGGI kernel: [  786.260632] ERROR!!! BBP write R64 fail
Nov 19 17:13:29 MAGGI kernel: [  786.260987] ERROR!!! BBP write R86 fail
Nov 19 17:13:29 MAGGI kernel: [  786.261330] ERROR!!! BBP write R82 fail
Nov 19 17:13:29 MAGGI kernel: [  786.261669] ERROR!!! BBP write R75 fail
Nov 19 17:13:29 MAGGI kernel: [  786.262019] ERROR!!! BBP write R66 fail
Nov 19 17:13:29 MAGGI kernel: [  786.263364] ERROR!!! BBP write R66 fail
Nov 19 17:13:40 MAGGI kernel: [  798.136219] r8169 0000:01:00.0: eth2: link down
Nov 19 17:13:40 MAGGI kernel: [  798.136951] ADDRCONF(NETDEV_UP): eth2: link is not ready
```

Can anybody give me any hint?

Thanks to all in advance!

^_Pepe_^

---

### Post by ^_Pepe_^ on 2010-11-19
Update!

I've tried to change Fix IP to DHCP, and it works! At least it's a workaround.

Rgds
^_Pepe_^
[Edit: No luck. It's a matter of luck. Sometimes works, sometimes not]

:(

---

### Post by aplath on 2010-11-21
First of all, thanks Sven for this instructions, they are very clear and helpful. However, they do not work for me and perhaps you can shed a little light on the matter.

In step 5, when I tried to execute to rmmod I got the message "ERROR: Module rt2860sta is in use". I went to the network applet and disabled the wireless network before proceeding, it seemed to work fine.

Then in step 7, after the modprobe, the wireless icon did not come to life by itself. When I tried to enable the wireless network manually, there was no such option in the menu.

I tried then to run "ifconfig wlan0 up" but got the message "wlan0: ERROR while getting interface flags: No such device"

I tried to follow the instructions to the end and reboot, but the problem remained. Then I reverted back to the previous driver and rebooted. Got back to the start, wireless connection working, only not with WEP.

My guess is that there's something preventing the new driver to go up, but I'm not sure where to look for clues of what might be causing it. 

Any suggestions would be very welcome! :-)

Thanks!

Andreas

---

### Post by azdavef on 2010-11-24
Thank you ;). I have a linksys n pci card in a desktop running Mint 9 (64 bit).  My connection is running at 130 Mb/s with a linksys n router with WPA encryption.  A note that this "fix" did not work with wicd.  Froze my machine and I had to power off to get it back.  My network was changed from wlan0 to ra0 and works fine with network manager.

---

### Post by Sven6210 on 2010-11-25
> **^_Pepe_^ said:**
> Hi everyone.

Firstly, thanks to everyone who contribute to this post. It's really helpful.

I can install 2.4 driver in my Medion Akoya Mini, successfully. 

But, I doesn't seem to work after suspension! 

^_Pepe_^


Hi Pepe,

is your WiFi generally working after suspend? I am asking because I have had trouble with my EeePC 900a. Actually I was able to suspend the netbook, but when waking it up again it did not reconnect with the WiFi. The same happened when I switched WiFi off with the special key (e.g. during flight in order to save electricity) I was not able to reconnect to WiFi after switching it on again. I always had to restart the computer in order to be able to use WiFi again.

After some research I found a solution. By adding parameters to the kernel I can now suspend and use WiFi when waking the netbook up. I can also switch WiFi off and it automatically reconnects when I switch it on again.

Under [http://ubuntuforums.org/showthread.php?t=1467749](http://ubuntuforums.org/showthread.php?t=1467749) you will find the manual what I had to do.

Maybe this helps you - but maybe your problem has a completely different background. Just an idea for you.

Good luck

Sven

---

### Post by Sven6210 on 2010-11-25
> **aplath said:**
> First of all, thanks Sven for this instructions, they are very clear and helpful. However, they do not work for me and perhaps you can shed a little light on the matter.

In step 5, when I tried to execute to rmmod I got the message "ERROR: Module rt2860sta is in use". I went to the network applet and disabled the wireless network before proceeding, it seemed to work fine.

Then in step 7, after the modprobe, the wireless icon did not come to life by itself. When I tried to enable the wireless network manually, there was no such option in the menu.

I tried then to run "ifconfig wlan0 up" but got the message "wlan0: ERROR while getting interface flags: No such device"

I tried to follow the instructions to the end and reboot, but the problem remained. Then I reverted back to the previous driver and rebooted. Got back to the start, wireless connection working, only not with WEP.

My guess is that there's something preventing the new driver to go up, but I'm not sure where to look for clues of what might be causing it. 

Any suggestions would be very welcome! :-)

Thanks!

Andreas


Dear Andreas,

[FONT=Verdana, sans-serif]when receiving an error message when entering

[/FONT]```
[FONT=Verdana, sans-serif]sudo rmmod rt2860sta[/FONT]
```

please just ignore it and continue with step 6. It should not have any impact on the following steps. Do not disable or change anything with WiFi, just run the different steps in the manual.

I suggest you start again at the beginning and just run through the manual. If you are using Ubuntu 10.04 LTS it should not be a problem.

Good luck

Sven

---

### Post by ^_Pepe_^ on 2010-11-25
> **Sven6210 said:**
> Hi Pepe,

is your WiFi generally working after suspend? I am asking because I have had trouble with my EeePC 900a. Actually I was able to suspend the netbook, but when waking it up again it did not reconnect with the WiFi. The same happened when I switched WiFi off with the special key (e.g. during flight in order to save electricity) I was not able to reconnect to WiFi after switching it on again. I always had to restart the computer in order to be able to use WiFi again.

After some research I found a solution. By adding parameters to the kernel I can now suspend and use WiFi when waking the netbook up. I can also switch WiFi off and it automatically reconnects when I switch it on again.

Under [http://ubuntuforums.org/showthread.php?t=1467749](http://ubuntuforums.org/showthread.php?t=1467749) you will find the manual what I had to do.

Maybe this helps you - but maybe your problem has a completely different background. Just an idea for you.

Good luck

Sven


Hi Sven.

I'm quite confused now. 

This is my case:


[INDENT][LIST]
[*]I'm under last maverick kernel, 2.6.35-23-generic
[*]Now, I'm under 2.1.0.0 driver. Plain vanilla version of kernel. I'm using WEP. I know, know...I must change ASAP, but I have two kids, 1 wife, 1 mountain bike, 2 jobs, 1 Wii,...well...
[*]I've tried to compile 2.4.1.0 driver, with no luck. Good connection after restart, but no luck after suspension
[*]I can switch off and on the Wifi hw with Fn-F11. No problem at all.
[/LIST][/INDENT]


But...now the big deal! I have an old 9.04 into a second partition which...successfully suspends and restores with Wifi on working in seconds. Driver version: 1.8.0.0

:/

Might I install 1.8.0.0 version into 2.6.35 kernel? I've used a .deb from here tp://ftp.debian.org/debian/pool/non-free/r/rt2860-source/rt2860-source_1.8.0.0-3_all.deb, but nothing worked. I think this .deb is ready to 9.04 kernels only.

I'm now trying your suggestion. But I've bought a intel3945 miniPCI in eBay for 9€...

Thanks to all. Great post!

^_Pepe_^

---

### Post by ^_Pepe_^ on 2010-11-25
Hi again, Sven.

Your grub modification tweak to load the kernel worked!

Now I'm able to connect after suspension...and I have a 9&#8364; intel miniPCIe card travelling from Hong Kong.

Anyway, linux users love to solve problems. It doesn't matter to throw 9&#8364; to the wastebasket.

:)

Thanks again!
^_Pepe_^

---

### Post by Sven6210 on 2010-12-10
> **^_Pepe_^ said:**
> Hi again, Sven.

Your grub modification tweak to load the kernel worked!

Now I'm able to connect after suspension...and I have a 9€ intel miniPCIe card travelling from Hong Kong.

Anyway, linux users love to solve problems. It doesn't matter to throw 9€ to the wastebasket.

:)

Thanks again!
^_Pepe_^


Hi Pepe,

I have not been online here for some time but it seems like everything worked out for you and you were able to find the answers for your previous post yourself - is that my right understanding?

Good to hear the kernel parameter worked also for you.

Best regards

Sven

---

### Post by suchathrill on 2010-12-18
This works on my newer HP desktop, except that I can't connect to hidden networks (that don't broadcast their SSID.)

How can I now connect with a hidden wireless network using WPA2 Personal?

edit: "it's not about hidden networks, it connects to one router in my house but not the one i want to use... my laptop with the same version of ubuntu but a different wifi card connects to both routers...

any ideas?"

---

### Post by Sven6210 on 2010-12-20
> **suchathrill said:**
> This works on my newer HP desktop, except that I can't connect to hidden networks (that don't broadcast their SSID.)

How can I now connect with a hidden wireless network using WPA2 Personal?

edit: "it's not about hidden networks, it connects to one router in my house but not the one i want to use... my laptop with the same version of ubuntu but a different wifi card connects to both routers...

any ideas?"

That sounds strange to me. I never had problems to connect to a WiFi access point. When WiFi worked on the computer I was also able to connect with different access points - even when travelling and having many different access points.

Did you try yet changing the channel of the hidden WiFi access point? Maybe that can help? However as one machine has problem and the other machine doesn't, it does not really sound like the channel. However I would look there as well.

Good luck

Sven

---

### Post by brokenromeo on 2010-12-20
Latest kernel update 2.6.35-24-generic seems to fix all of these issues for my eee pc 901...

---

### Post by brokenromeo on 2010-12-20
Spoke too soon...resume from suspend still does not work reliably with the kernel included rt2860 driver...

---

### Post by Cgaldino on 2010-12-28
You really save my wi-fi connection of a Eeepc1000H
The tutorial works properly fine!

Thank shttp://ubuntuforums.org/images/smilies/icon_razz.gif

---

### Post by Sven6210 on 2010-12-30
> **brokenromeo said:**
> Spoke too soon...resume from suspend still does not work reliably with the kernel included rt2860 driver...

I do not really understand your post. Did you use the manual here to update the WiFi module? And did it work? Or do you still struggle?

---

### Post by pvillela on 2010-12-30
Thank you for the excellent solution explanation.  It worked fine with my eee1000 on Ubuntu 10.04.  I had to improvise on a few details, though.  On step 7, I did "cd os/linux" prior to executing "sudo modprobe rt2860sta".  For some reason, on my computer the wireless interface was ra0 instead of wlan0.  Anyway, "sudo ifconfig ra0 down" did not seem to bring the interface down for more than a moment.  I had to bring it down by unchecking "Enable Wireless" on the Network Manager applet.

---

### Post by mymuse666 on 2011-01-07
Sven, I just installed 10.10 and seem to have gotten through the whole manual without any errors. However, when I put in the command "sudo ifconfig wlan0 up" I get the message "Device or resource busy."
Also as perthe other user reporting that the kernel was still using rt2800 driver, mine is reporting he same. When iI tried to follow his instructions to replace the rt2800 driver with the rt2860 it did not work for me. Thanks for your help in advance.

EDIT I went back and corrected the values for the first text document edit and then also redid the steps to "bash" the rt2800 driver. Rebooted, unplugged the ethernet cable and voila, I saw and was able to connect to my network. Thanks Sven for this amazing thread and those that posted their fixes, after a corrupted Win7 install and about 4 hours of trobleshooting i'm in Linux Land!

---

### Post by CLIOG on 2011-01-17
I have 10.10 on EeePC 1000H and rt2800pci sometimes worked and sometimes not (WPA2 hidden SSID). After compiling the driver from sources (thanks Sven) the connection works but there is a tiny problem with that - after every login I have to wait about 20 seconds until the WPA password window and then press the "Connect" button. Is there any way not do to it manually every time?

---

### Post by thantrix on 2011-01-22
I've done all the steps outlined in the first post of this thread.  It even worked for a couple of days, but now I'm back to being unable to connect to any wireless networks. I'm on an EEEPC 901, not an EeeBox, but the only difference I've seen is my ifconfig shows ra0 instead of wlan0. I have no idea what to do next.  Any help would be greatly appreciated.

---

### Post by Sven6210 on 2011-01-23
> **CLIOG said:**
> I have 10.10 on EeePC 1000H and rt2800pci sometimes worked and sometimes not (WPA2 hidden SSID). After compiling the driver from sources (thanks Sven) the connection works but there is a tiny problem with that - after every login I have to wait about 20 seconds until the WPA password window and then press the "Connect" button. Is there any way not do to it manually every time?

Which password are you really referring to? The WiFi passphrase of the password to unlock the password daemon? Actually you only enter the WiFi passphrase once and then give it a new password in the password daemon. Every time you connct with the WiFi you need to release the WiFi passphrase with the defined password. But actually the WiFi passphrase is saved on your machine and you only need the password to release it.

You can start Ubuntu in two ways, with a password and without password. I guess you start Ubuntu without password and therefor the password daemon requires the password every time you build up a WiFi connection.

If you configure Ubuntu to start only with a password, you do not need to unlock the password daemon later when building up WiFi. So WiFi will start directly.

So consider starting Ubuntu only with password and try whether that solves your problem.

Good luck

Sven

---

### Post by Sven6210 on 2011-01-23
> **thantrix said:**
> I've done all the steps outlined in the first post of this thread.  It even worked for a couple of days, but now I'm back to being unable to connect to any wireless networks. I'm on an EEEPC 901, not an EeeBox, but the only difference I've seen is my ifconfig shows ra0 instead of wlan0. I have no idea what to do next.  Any help would be greatly appreciated.

I assume you updated the kernel or any kernel close module. When Ubuntu distributes a new kernel through the Update Center, then the precedure must be run once more. So just repeat all steps and your WiFi will work again.

And keep in mind to redo the steps every time you receive a kernel update.

I hope that helps,

Sven

---

### Post by thantrix on 2011-01-23
Sven, thanks for the quick response, but my post was made after already redoing the steps twice.  

Turns outs my bedroom is on the outskirts of my wireless router's range, so I only get sketchy coverage there.  It works fine closer to the base.

---

### Post by alliance1975 on 2011-02-01
> **Sven6210 said:**
> Dear eltonw,

Actually it is not necessary to compile the driver each time you make a kernel update. It is enough to copy the once compiled kernel into the directory with the updated kernel. this is done with the command:

[FONT=Verdana, sans-serif]sudo cp rt2860sta.ko  /lib/modules/2.6.*/kernel/drivers/staging/rt2860/

The command must be launched from the directory where the module is. But it is not necessary to recompile the kernel. Once done it is fine. So not such a big hassle any more.

Best regards

Sven
[/FONT]

-------------------------------------------------
Sven,

Can the copy command be done right after the new kernel is installed? In other words can I allow the updates and before the computer reboots, copy the compiled file to the new location? I ask because I have it on a headless server. I would have to connect monitor and keyboard to do the copy. No big deal but it would be easier.

---

### Post by acoolbid on 2011-02-08
help needed

when i executed "sudo rmmod rt2860sta" in step5,it alert "error:module rt2860sta does not exist in /proc/modules

what should i do now

---

### Post by linuxser on 2011-02-11
[FONT=Verdana, sans-serif]Okay.... Thanks to @[/FONT][Sven6210]("http://ubuntuforums.org/member.php?u=929104") , I combine his tutorial with this [http://ubuntuforums.org/showthread.php?p=9289963](http://ubuntuforums.org/showthread.php?p=9289963)
[FONT=Verdana, sans-serif]Now, my WLAN working without any problems, i hope that will be forever. :D

Actually, i have problem at Step 5, that because of Mistake at Step 4. I (or maybe anyone else too) was wrong to understanding Sven's description at Step 4
[/FONT]> [FONT=Verdana, sans-serif]Use the find command to locate [/FONT]***[FONT=Verdana, sans-serif]MIX_CIPHER_NOTUSE[/FONT]***[FONT=Verdana, sans-serif]. Replace the entire line (keep on one line)  with this code:[/FONT]
 [FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher =  WPA_TKIPAES_WPA2_TKIPAES;[/FONT]I just replace ***[FONT=Verdana, sans-serif]MIX_CIPHER_NOTUSE [/FONT]***[FONT=Verdana, sans-serif]with [/FONT][FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher =  WPA_TKIPAES_WPA2_TKIPAES;
So, the source be: [/FONT][I][B][FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher = [/FONT][FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher =  WPA_TKIPAES_WPA2_TKIPAES;

[/FONT][/B][/I][FONT=Verdana, sans-serif]If the Step 4
[/FONT]> [FONT=Verdana, sans-serif]Use the find command to locate [/FONT]***[FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher = [/FONT]****[FONT=Verdana, sans-serif]MIX_CIPHER_NOTUSE[/FONT]***[FONT=Verdana, sans-serif]***;***. Replace the entire line (keep on one line)  with this code:[/FONT]
  ***[FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher =  WPA_TKIPAES_WPA2_TKIPAES;[/FONT]***i thing i and others will not missing.

**So, This is my edit for Step 4**:
> [FONT=Verdana, sans-serif]Use the find command to locate [/FONT]***[FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER FlexibleCipher = [/FONT]****[FONT=Verdana, sans-serif]MIX_CIPHER_NOTUSE[/FONT]***[FONT=Verdana, sans-serif]***;***. Replace the entire line  (keep on one line)  with this code:[/FONT]
   ***[FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER  FlexibleCipher =  WPA_TKIPAES_WPA2_TKIPAES;[/FONT]***Thank you very much.....

---

### Post by chip616 on 2011-02-11
Much thanks for the tutorial.  My eeepc 901 is now working with the wireless.

Oddly enough, it worked before on some routers, as long as the wifi was unencrypted.  I noted the change to the WPA_MIX_PAIR_CIPHER command that I am assuming is what has enabled this.

In any case, it now works.  Much thanks.

Frank.

---

### Post by Sven6210 on 2011-02-11
> **alliance1975 said:**
> -------------------------------------------------
Sven,

Can the copy command be done right after the new kernel is installed? In other words can I allow the updates and before the computer reboots, copy the compiled file to the new location? I ask because I have it on a headless server. I would have to connect monitor and keyboard to do the copy. No big deal but it would be easier.

After a new kernel has been installed/downloaded from the repositories I recommend to first reboot the computer and then run the tutorial. Honestly I never tried it the other way round but furst booting the new kernel and then running the tutorial seems like the better solution for me.

Sometimes it may also happen that you only download an updated kernel, not a new kernel version. In that case the old tutorial works sometimes for the updated kernel.

Conclusion:
When updating the kernel and the computer requires you to restart, do the restart first. In case WiFi still works no action is required, in case your WiFi can not connect re-run the tutorial.

---

### Post by Sven6210 on 2011-02-11
> **acoolbid said:**
> help needed

when i executed "sudo rmmod rt2860sta" in step5,it alert "error:module rt2860sta does not exist in /proc/modules

what should i do now

Did you try to continue with the tutorial? If not do so. If it gives you an error message at a later stage please indicate where and when you are getting it. I see good chances that you continue and the rest will work fine for you and you have WiFi after you finished all steps.

Good luck

Sven

---

### Post by linuxser on 2011-02-12
> **Sven6210 said:**
> 
 **[FONT=Verdana, sans-serif]Step 10[/FONT]**
 [FONT=Verdana, sans-serif]Update your modules boot file with the following command:[/FONT]
 

 ```
[FONT=Verdana, sans-serif]gksudo gedit /etc/modules[/FONT]
```[FONT=Verdana, sans-serif]
Ad[/FONT][FONT=Verdana, sans-serif]d the „[/FONT]*[FONT=Verdana, sans-serif]rt2860sta“[/FONT]*[FONT=Verdana, sans-serif] on a line at the end of the file and close and save the file.[/FONT

Hi sven, even if my WiFi working now, i still confused about STEP 10. This is the *modules*'s source:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
Where the "*rt2860sta*" must placed?
In the same line with "***lp***" so the code will be:
> "***lprt2860sta***" or > "***lp rt2860sta***"
Or, in new line after "***lp***", that will be 
> "[B][I]lp
rt2860sta[/I][/B]"
Please explain, so I'm not confused anymore.
Thanks

---

### Post by acoolbid on 2011-02-13
> **Sven6210 said:**
> Did you try to continue with the tutorial? If not do so. If it gives you an error message at a later stage please indicate where and when you are getting it. I see good chances that you continue and the rest will work fine for you and you have WiFi after you finished all steps.

Good luck

Sven

i found another way to make it,still thx a lot  

here is the ppa,hope can help some newcomers a little
[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

---

### Post by Sven6210 on 2011-02-13
> **linuxser said:**
> Hi sven, even if my WiFi working now, i still confused about STEP 10. This is the *modules*'s source:

Where the "*rt2860sta*" must placed?
In the same line with "***lp***" so the code will be:
 or 
Or, in new line after "***lp***", that will be 

Please explain, so I'm not confused anymore.
Thanks

The file should look like:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rt2860sta

```This should do it for you.

---

### Post by Tiler on 2011-02-25
I tried this update on my EeePC 1000 SSD.  It worked flawlessly in that, there were no errors.  I noticed before the wireless connection was wlan0 and now when it connects (less than half the time) it's listed as ra0.

Also,  has anyone tried the firmware update from the same download page?  I downloaded it and wonder if that's my next step.

When I do connect (ra0) I get 65Mbps, it's quite nice.

Quality posting, Sven!

---

### Post by admelfo on 2011-02-26
*gawd*! After all kinds of pissing around -- trying some of these no-doubt wonderful suggestions (the community always is very helpful :)), I finally decided to reset my router. For the heck of it. 

And all is fine. :???: ](*,)

Before I started to beat myself up about it I remembered that, the whole time, wireless was working just fine for my Windows 7 laptop -- so I had no reason to assume that it was a router issue.

Still -- annoying. I share this in the hope of being able to save anyone time and frustration if they encounter this issue.

(Still no idea why choosing the WinNT/2000 option from the grub menu blew away my dual XP/Ubuntu install, which was working just fine -- and which led the issue at hand, b/c I had to reconfig the box as a Ubuntu only machine.)

---

### Post by weeix on 2011-03-03
While compiling the driver with 'make', I got these warnings
```
warning: the frame size of XXXX bytes is larger than 1024 bytes
warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
warning: initialization discards qualifiers from pointer target type
warning: unused variable XXXX
warning: ‘index’ may be used uninitialized in this function
```Is this normal?

BTW, this solves my problem in Lucid.

Thanks a lot! :D

---

### Post by Sven6210 on 2011-03-03
> **weeix said:**
> While compiling the driver with 'make', I got these warnings
```
warning: the frame size of XXXX bytes is larger than 1024 bytes
warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
warning: initialization discards qualifiers from pointer target type
warning: unused variable XXXX
warning: ‘index’ may be used uninitialized in this function
```Is this normal?

BTW, this solves my problem in Lucid.

Thanks a lot! :D

Yes, the warning is normal and I am also getting it. But it has no impact on the result, the module is still compiled and works perfectly for me - and it seems it also solved your problem.

Have fun with your WiFi and Ubuntu

---

### Post by angualupin on 2011-03-05
*Thank you* for this. I wasn't able to connect with my router after upgrading my eeePC to 10.04 (yes, I know, I'm late to the party), but I followed these instructions to the letter and they worked perfectly. It still took some playing around with my router settings to get it to work -- including a hard restart -- but I now have working, secure wireless for the first time in several weeks. Combine that with a new harddrive for my desktop running 10.10 and I am a very happy Ubuntu user. Thank you!

---

### Post by Talon2 on 2011-03-05
I'd like to point out the insanity of the situation.

If less than 10% of the effort that has went into fixing Ralink rt2860/2870 problems would go into getting the right drivers and configuration information into the kernel then we could put an end to the madness that is seen in this thread and others.

I posted this bug a long time ago:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

This bug and many more as well as many threads like this prove to me that we have a company that is Linux friendly because the information and drivers are there but something is breaking down as far as end shipping products such as Ubuntu are concerned.  Someone please tell me why we can't get this fixed.

---

### Post by Sven6210 on 2011-03-14
> **Talon2 said:**
> I'd like to point out the insanity of the situation.

If less than 10% of the effort that has went into fixing Ralink rt2860/2870 problems would go into getting the right drivers and configuration information into the kernel then we could put an end to the madness that is seen in this thread and others.

I posted this bug a long time ago:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

This bug and many more as well as many threads like this prove to me that we have a company that is Linux friendly because the information and drivers are there but something is breaking down as far as end shipping products such as Ubuntu are concerned.  Someone please tell me why we can't get this fixed.

Please consider that the kernel is not programmed by Canonical. Ubuntu is a collection of Open Source software from many projects.

The Linux-kernel is developed by by the kernel developers and as far as I understood Linus himself still has a major role in the kernel development. Also the X11 server, Gnome, LibreOffice, Firefox and all the other parts of a Linux distribution are not programmed by Canonical.

Canonical is more the company who is integrating all these programs and makes them to fit with each other. And what Canonical puts together and distributes for free is based on work of thousands of programmers, many of whom do it voluntarily without being paid. Actually this is the strength and weakness of Ubuntu. It depends on many people and their voluntary work. But it is open to many new ideas and concepts.

---

### Post by alannerd#1 on 2011-03-17
I have used the above method successfully but for ralink rt3090. The differences follow but essentially i just substituted 3090 for 2860 all the way through. This was on a Sony vaio netbook running multi boot ubuntu netbook version ad windows 7 starter.
First used it on 10.04 but have since done so on 10.10.
I only needed steps 1,2,5 (2nd half), 6,7,9, 10 (only used on first time on this pc)
Connection dosnt always work after step 7
2 reboots seem to be necessary to get connection working. Shutdown / restart works but straight restart option dosnt.
After using this procedure to device wlan0 is replaced with ra0 but i've no idea how.
Hope this helps someone get rt3090 going on 10.04 or 10.10.
Thanks Sven and Chris for bothering to specify all this.

---

### Post by TonySilva on 2011-04-20
In step four

make -C tools
make[1]: Entering directory `/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/2.6.32-30-generic-pae/build SUBDIRS=/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-30-generic-pae'
  CC [M]  /home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.o
/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.c: In function &#8216;RTMPMakeRSNIE&#8217;:
/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.c:2424: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;rsnielen_cur_p&#8217;
make[2]: *** [/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.o] Error 1
make[1]: *** [_module_/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-30-generic-pae'
make: *** [LINUX] Error 2
tony@tony-desktop:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ gedit ./common/cmm_wpa.c 
sys:1: GtkWarning: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed

i check the cmm_wpa.c

[IMG]https://lh6.googleusercontent.com/_6SLiO3ubDOc/Ta68wEGfjHI/AAAAAAAAAQE/rCchrrZttQo/s640/Screenshot.png[/IMG]

like this?

gcc is installed

---

### Post by Tiler on 2011-04-21
I must have made a mistake or am missing something.  Every time there's a kernel update, I find myself going through most of the steps again.

Any suggestions?

---

### Post by Sven6210 on 2011-04-22
> **Tiler said:**
> I must have made a mistake or am missing something.  Every time there's a kernel update, I find myself going through most of the steps again.

Any suggestions?

This is absolutely normal, after a kernel update the module needs to be recompiled for the new kernel.

---

### Post by Sven6210 on 2011-04-22
> **TonySilva said:**
> In step four

make -C tools
make[1]: Entering directory `/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/2.6.32-30-generic-pae/build SUBDIRS=/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-30-generic-pae'
  CC [M]  /home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.o
/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.c: In function ‘RTMPMakeRSNIE’:
/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.c:2424: error: expected ‘,’ or ‘;’ before ‘rsnielen_cur_p’
make[2]: *** [/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/../../common/cmm_wpa.o] Error 1
make[1]: *** [_module_/home/tony/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-30-generic-pae'
make: *** [LINUX] Error 2
tony@tony-desktop:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ gedit ./common/cmm_wpa.c 
sys:1: GtkWarning: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed

i check the cmm_wpa.c

[IMG]https://lh6.googleusercontent.com/_6SLiO3ubDOc/Ta68wEGfjHI/AAAAAAAAAQE/rCchrrZttQo/s640/Screenshot.png[/IMG]

like this?

gcc is installed

You simply forgot the ";" (the semicolon) at the end of the line that you added. Add it and it should work.

Good luck

Sven

---

### Post by Tiler on 2011-04-22
> **Sven6210 said:**
> This is absolutely normal, after a kernel update the module needs to be recompiled for the new kernel.

I guess that's that, then.

You've been quite a champion in this thread, Sven.  Thank you!

---

### Post by fangshi on 2011-05-04
Just adapted this method with the rt3592 driver by modifying all rt2860 by rt3562 and it works great on Natty !

Many thanks for your contribution, that had definitely solved my wifi problem!

---

### Post by jbatista on 2011-05-05
I've tried using the stock modules without success. I've gone up to installing the package **linux-backports-modules-wireless-lucid-generic** but without success (I'm sticking with the LTS releases for now, until I'm sufficiently convinced to try the Unity interface from Maverick and Natty).

I also had to blacklist several rt2* modules, e.g. by creating a file /etc/modprobe.d/blacklist-rt2860sta.conf 
```

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib

```
and rebooting to ensure that the blacklisted modules aren't loaded (yes, I realize that I could have stopped the networking service, but I wanted to be *sure*).

Anyway, I followed Sven6210's instructions. It worked up to Step 8.

> **Sven6210 said:**
> 
 **[FONT=Verdana, sans-serif]Step 7[/FONT]**
 ```
[FONT=Verdana, sans-serif]sudo depmod -a[/FONT]
[FONT=Verdana, sans-serif]sudo modprobe rt2860sta[/FONT]
```[FONT=Verdana, sans-serif]
After you issue the previous command you should see the Desktop top panel wireless icon come to life as it tries to connect. You will be prompted for a WPA password. Give it a little while and it should connect.[/FONT]
 

 [FONT=Verdana, sans-serif]Not sure this command is necessary but you can use if the Wireless isn’t started automatically.[/FONT]
 [FONT=Verdana, sans-serif]sudo ifconfig wlan0 up[/FONT]
 

 **[FONT=Verdana, sans-serif]Step 8[/FONT]**
 [FONT=Verdana, sans-serif]Okay at this point you have made a lot of progress and should be happily surfing.[/FONT]
 


At step 8 I'm still unable to connect using Ubuntu Lucid's Network Manager (on a **EeePC 1000H netbook** with i386 kernel and the Ralink RT2860 chip). I haven't tried it with the latest releases (Maverick, now Natty) because I like "stable" stuff :wink: and I've decided to keep with LTS releases.

Anyway, what I've found out is that I still need to turn off the Network Manager (!) and use the **ra0** device instead of **wlan0**. What worked for me uses a series of **iwpriv** commands.

What I've done to connect to an AP called "MyAP" on channel 7 (for example), using WPA2-PSK authentication and AES encryption (also works with TKIP) with a pre-shared key "010101010". Replace your values accordingly. See the file iwpriv_usage.txt that comes with the source (examples d and e towards the end of the file). I write on a console (gnome-terminal or xterm):

```

sudo service network-manager stop ; 
sudo service networking stop ; 
sudo rmmod rt2860sta ; 
sudo insmod rt2860sta.ko ;
sudo ifconfig ra0 up ;
sudo ra0 set NetworkType=Infra ;
sudo ra0 set Channel=7 ;
sudo ra0 set AuthMode=WPA2PSK ; 
sudo ra0 set EncrypType=AES ;
sudo iwpriv ra0 set SSID="MyAP" ;
sudo iwpriv ra0 set WPAPSK=010101010 ;
sudo iwpriv ra0 set SSID="MyAP" ;
sudo dhclient ra0 

```

Prior to running this, I also installed RT2860STA.dat that comes with the source, since the compiled module seemed to look for it. So I did once:
```

sudo mkdir -p /etc/Wireless/RT2860STA ;
sudo cp RT2860STA.dat /etc/Wireless/RT2860STA/ ;

```
Given the iwpriv commands passed, it doesn't seem to be interested in the particular settings in the original file (which should be editted accordingly, e.g. replacing with the correct SSID).

This is so far the only way I can get it to connect. If I attempt to use wlan0 (via modprobe rt2860sta and then using the Network Manager), it doesn't connect! I suppose this might be solved upstream (Maverick, Natty), but this is what works so far on Lucid with a EeePC 1000H. Hopefully I might find a more practical way to use it, instead of relying on a shell script; so this is a "last resort" for me.

---

### Post by Tiler on 2011-05-05
> **pvillela said:**
>  For some reason, on my computer the wireless interface was ra0 instead of wlan0.  
I've found the same.

---

### Post by TocsDeTics on 2011-05-08
Works GREAT at EEEPC 1000H in Natty Narval.

Thaks!!

---

### Post by wajvpitt on 2011-05-11
Every so often, I try the newest version of Ubuntu.  Always, there is some problem that needs fixing.  Often, it is wireless related.  

I've just got an Emachines ER1402 (uses rt3090 part) very cheaply and I put Natty on it.  
The wireless worked just fine to begin with but the computer would hang on shutdown.  Followed this to solve that problem:

[https://answers.launchpad.net/ubuntu/+question/132350](https://answers.launchpad.net/ubuntu/+question/132350)

so now I've blacklisted the rt2800pci driver and I'm using the rt2860sta one.  
 
Solved the hanging, but solving one problem has led to another and now I can't connect to the WPA network I was connected to before (although I can see it).  

Is this the right thread to be looking at?  
Should installing the RT3090 driver solve all my problems?
When will it 'just work'?

---

### Post by andre_orwell on 2011-05-12
build fails for me on Natty.
```

andrew@akoya:/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo make
[sudo] password for andrew: 
make -C tools
make[1]: Entering directory `/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build/ SUBDIRS=/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make[1]: Entering directory `/lib/modules/2.6.38-8-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.38-8-generic/build'
make: *** [LINUX] Error 2

```

Others have posted this problem but no solution has been given. I believe I edited common/cmm_wpa.c correctly.  NB the directory /lib/modules/2.6.38-8-generic/build/ doesn't exist on my system (/lib/modules/2.6.38-8-generic/ does - just no subdirectory called build.  Not sure if that matters.)

update: /lib/modules/2.6.38-8-generic/build/ is part of linux-headers.  Installing it fixes my build problem :-)

---

### Post by Sven6210 on 2011-05-15
> **wajvpitt said:**
> Every so often, I try the newest version of Ubuntu.  Always, there is some problem that needs fixing.  Often, it is wireless related.  

I've just got an Emachines ER1402 (uses rt3090 part) very cheaply and I put Natty on it.  
The wireless worked just fine to begin with but the computer would hang on shutdown.  Followed this to solve that problem:

[https://answers.launchpad.net/ubuntu/+question/132350](https://answers.launchpad.net/ubuntu/+question/132350)

so now I've blacklisted the rt2800pci driver and I'm using the rt2860sta one.  
 
Solved the hanging, but solving one problem has led to another and now I can't connect to the WPA network I was connected to before (although I can see it).  

Is this the right thread to be looking at?  
Should installing the RT3090 driver solve all my problems?
When will it 'just work'?

Did you try running this howto replacing 2860 with 3090 (as this is you WiFi chip-set)? I would recommend to run this manual after each kernel update and things should run well for you. I only tried once on Natty and it worked. But I admit that I only tested it shortly, I am still doing productive works with Lucid.

---

### Post by Sven6210 on 2011-05-15
> **andre_orwell said:**
> build fails for me on Natty.
```

andrew@akoya:/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo make
[sudo] password for andrew: 
make -C tools
make[1]: Entering directory `/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/2.6.38-8-generic/build/ SUBDIRS=/home/andrew/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make[1]: Entering directory `/lib/modules/2.6.38-8-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.38-8-generic/build'
make: *** [LINUX] Error 2

```Others have posted this problem but no solution has been given. I believe I edited common/cmm_wpa.c correctly.  NB the directory /lib/modules/2.6.38-8-generic/build/ doesn't exist on my system (/lib/modules/2.6.38-8-generic/ does - just no subdirectory called build.  Not sure if that matters.)

update: /lib/modules/2.6.38-8-generic/build/ is part of linux-headers.  Installing it fixes my build problem :-)

I guess the problem has been created when you edited ".common/cmm_wpa.c". The original entry for "[FONT=Verdana, sans-serif]WPA_MIX_PAIR_CIPHER" has a comment at the end and that comment jumps to the line below. So when you delete the entire line you probably still miss the rest of the comment in the next line. This does not have the comment symbol any more and can not be interpreted.

I recommend to redo the whole procedure from the beginning (incl. unpacking the driver again) and making sure that you delete the whole comment even though it goes to a new line.

Let us know whether it works then.

Good luck

Sven


[/FONT]

---

### Post by Sven6210 on 2011-05-15
[B]
[SIZE=4][COLOR=Red]Call four your input!!![/COLOR][/SIZE][/B]

Dear all,

I would like to ask you for your help and input. The WiFi issue for RaLink chip-sets is still an issue and also with the release of the latest Natty things do not work perfectly - there are improvements but things are not perfect yet.

Did anybody try this manual for other RaLink WiFi chip-sets and can share his experience here?

From what I know this manual works for the following WiFi chip-sets:

[LIST]
[*]RT2860 - works very reliable with Lucid
[*]RT3090 - works very reliable with Lucid
[*]RT3562 - according to this forum it also works
[/LIST]
Who did try this howto with newer Ubuntu releases (Maverick, Natty) and has positive or negative experience?

[LIST]
[*]Lucid - works very well
[*]Maverick - I do not have experience
[*]Natty - tested shortly and worked well, no long term experience
[/LIST]
Do you have additional input to this? If I get enough feedback I would like to add the experience of the users here to the howto. Hopefully it helps some other Ubuntu users.

Thank you for your feedback

Sven

---

### Post by nanda108 on 2011-06-03
hello!
I have a problem with wireless after this installation. I think my wireless card works after this 11 steps but somehow connection is not possible. I think that I was done all steps right but I have some errors. Please help.

This what I have:

nanda@nanda-laptop:~$ cd 2010*
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ 
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ gedit ./os/linux/config.mk
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ gedit ./common/cmm_wpa.c

(gedit:4245): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo make
[sudo] password for nanda: 
make -C tools
make[1]: Entering directory `/home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/2.6.32-32-generic-pae/build SUBDIRS=/home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make: *** /lib/modules/2.6.32-32-generic-pae/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo make install
make -C /home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.32-32-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/2.6.32-32-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
make: *** [install] Error 2
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo iconfig wlan0 down
sudo: iconfig: command not found
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo ifconfig wlan0 down
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo rmmod rt2860sta
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo mv /lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist
mv: cannot stat `/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko': No such file or directory
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo mv/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist
sudo: mv/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko: command not found
nanda@nanda-laptop:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo mv /lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist
mv: cannot stat `/lib/modules/2.6.32-32-generic/kernel/drivers/staging/rt2860/rt2860sta.ko': No such file or directory


nanda@nanda-laptop:~$ ls /lib/modules
2.6.32-28-generic  2.6.32-31-generic  2.6.32-32-generic  2.6.32-32-generic-pae
nanda@nanda-laptop:~$ sudo lshw -C network 
[sudo] password for nanda: 
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:44:00.0
       logical name: wlan0
       version: 00
       serial: e0:2a:82:55:d6:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 ip=10.42.43.1 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:90300000-9030ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:45:00.0
       logical name: eth0
       version: 03
       serial: 64:31:50:06:d3:ea
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:2000(size=256) memory:90004000-90004fff(prefetchable) memory:90000000-90003fff(prefetchable) memory:90020000-9003ffff(prefetchable)

---

### Post by AMMOnium on 2011-06-09
> **nanda108 said:**
> 
make -C /lib/modules/2.6.32-32-generic-pae/build SUBDIRS=/home/nanda/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make: *** /lib/modules/2.6.32-32-generic-pae/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2


This line indicates that "make" utility has encountered an unrecoverable error. You should not have continued to the next howto steps.
**A general rule is that when you see an error in the "make" output -- you stop and investigate what has just happened. **


The reason behind this error is that the path "/lib/modules/2.6.*/build", which is actually a symlink to "/usr/src/linux-headers-*/" is missing. And the contents of the "/usr/src/linux-headers-*/" are a part of the "linux-headers" package for your current kernel.

So please run
```
sudo apt-get install linux-headers-2.6.32-22-generic-pae 
```
and repeat the howto from the beginning.
Hope this helps.

---

### Post by Bergschreck on 2011-06-17
I have a Acer Revo 3700 running Maverick. WiFi run out of the box, but had some problems: It was loading the wrong driver (rt2860pci) which caused freezes on shutdown or reboot. I had to blacklist this driver, so rt2860sta was used. With this driver WiFi connections are very unstable, connections are often dropped.
So I tried installing the latest Ralink driver, following this very good instructions.

Compilation and installation went without problems, I replaced the  rt2860sta.ko in the staging directory with the new one, but then wifi is unusable.

According to lsmod the module is loaded:

```
Module                  Size  Used by
rt2860sta             798341  0 
binfmt_misc             6599  1 
nfsd                  240992  11 
lockd                  65605  1 nfsd
nfs_acl                 2257  1 nfsd
auth_rpcgss            34001  1 nfsd
sunrpc                193178  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3449  1 nfsd
parport_pc             26058  0 
ppdev                   5556  0 
nvidia               9329739  38 
snd_hda_codec_nvhdmi    13615  4 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
intel_agp              26566  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
serio_raw               4022  0 
agpgart                32011  2 nvidia,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
crc_ccitt               1351  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
r8169                  36521  0 
mii                     4425  1 r8169

```

But it looks like it is not detected as wireless driver, ifconfig does not show any wireless adapter:

```
eth0      Link encap:Ethernet  Hardware Adresse d0:27:88:6b:24:dd  
          inet Adresse:192.168.1.105  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::d227:88ff:fe6b:24dd/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:6741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6414 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6954997 (6.9 MB)  TX bytes:849024 (849.0 KB)
          Interrupt:43 Basisadresse:0x6000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:8508 (8.5 KB)  TX bytes:8508 (8.5 KB)

```

and iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```
What's going wrong here?

---

### Post by redmaniac on 2011-06-28
> **Sven6210 said:**
> [B]
[SIZE=4][COLOR=Red]Call four your input!!![/COLOR][/SIZE][/B]

Dear all,

Did anybody try this manual for other RaLink WiFi chip-sets and can share his experience here?
Who did try this howto with newer Ubuntu releases (Maverick, Natty) and has positive or negative experience?

[LIST]
[*]Lucid - works very well
[*]Maverick - I do not have experience
[*]Natty - tested shortly and worked well, no long term experience
[/LIST]


I have tried it with Natty and the newst driver sources for rt3090 (at the time of writing 2.4.0.4). This does not work at all and the reason is the newer kernel.

It seems that the mentioned sources use the linux header cfg80211.h, which in kernel 2.6.32-32 defines an enum named tx_power_setting.

In 2.6.38-8 this header no longer defines that enum and the build fails. I did not try to patch it because I really did not feel like rewriting the driver for this newer kernel. The frustrating thing is that the method, which causes the trouble, i.e. th (only!) one which uses this enum, seems to only return that it is not supported. Yet I can only warn anybody tempted to "quickfix" this by patching that enume (i.e. define a dummy enum). This messed my system up pretty bad and I ended up booting into runlevel 1 to get ubuntu to not load the buggy driver and remove it. 

So for now this driver seems inaccessible to people with that newer kernel.

---

### Post by Bedlore on 2011-07-16
> **Sven6210 said:**
> [FONT=Verdana, sans-serif]After having installed Ubuntu 10.04 successfully on my EeePC 900a I also wanted to use it on my EeeBox B202 which is used as a kind of media centre.[/FONT]
 ..................
 [FONT=Verdana, sans-serif]I hope it works for you as well[/FONT]

I just followed these instructions on my EEE PC 1000HE (RT2860) on the latest Natty kernel 2.6.38-10-generic and sadly it has not worked.

The default driver is problematic and works very inconsistently.  This thread should have the SOLVED removed really.

---

### Post by chili555 on 2011-07-16
> **Bedlore said:**
> I just followed these instructions on my EEE PC 1000HE (RT2860) on the latest Natty kernel 2.6.38-10-generic and sadly it has not worked.

The default driver is problematic and works very inconsistently.  This thread should have the SOLVED removed really.If you'd care to start your own new thread and PM me the link, I'd be happy to help you troubleshoot.

---

### Post by Bedlore on 2011-07-16
> **chili555 said:**
> If you'd care to start your own new thread and PM me the link, I'd be happy to help you troubleshoot.

Thanks that would be appreciated, started one here: [http://ubuntuforums.org/showthread.php?p=11055285](http://ubuntuforums.org/showthread.php?p=11055285)

---

### Post by Sven6210 on 2011-07-17
> **Bedlore said:**
> I just followed these instructions on my EEE PC 1000HE (RT2860) on the latest Natty kernel 2.6.38-10-generic and sadly it has not worked.

The default driver is problematic and works very inconsistently.  This thread should have the SOLVED removed really.


I have installed Natty on an EeePC 1015P and had to blacklist some kernel modules and after that it worked very well.

Open the terminal window and enter the following command:

```

sudo gedit /etc/modprobe.d/blacklist.conf

```In the file add the following lines at the bottom:

```

blacklist rt2x00lib
blacklist rt2800pci
blacklist rt2x00pci
blacklist rt3390sta
blacklist rt3090sta

```Then restart the laptop and try whether things work for you as well.

---

### Post by LPMusicLJ on 2011-07-19
Thank you **Sven6210** for you time and dedication to write this up.  Your writing is very clear and concise.

This worked for me on my **Asus EeePC 901**.  It appears that the only step missing was in Step 4, you did not explicitly state to s*ave and close gedit*.

I turned off my wireless card physically because it kept reconnecting once I issued the [FONT="Courier New"]sudo ifconfig wlan0 down[/FONT] command.  I then had to manually turn it on at step 7 along with the *wlan0 up* command.

I run Ubuntu 11.04.  This fixed my issue.

---

### Post by rayfitzharris on 2011-08-04
This guide works great on my eeepc 1000 ssd with 10.04 (lucid) kernel 2.6.32-33-generic.
 
with one exception: my wireless interface is now called ra0 instead of wlan0 but a quick change to wicd and all is well.
Currently connected at n speeds.

--

ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:00:F5:C0:10:00   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-53 dBm  Noise level:-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by itshis on 2011-08-09
Hi Sven,
Thank you for you complete and detailed instructions, I followed them to the letter and am now working properly.

Previously the WiFi (using the rt2800pci driver) dropped out constantly and asked me for the password then often failed to reconnect. Now I've been up and running for hours without a problem.

I'll see what happens when I upgrade the kernel but don't mind having to re-do the instructions which I've saved to PDF on my disk.

---

### Post by murphaph on 2011-08-10
EDIT: FOUND MY STUPID ERROR-Sven, it's working for me on Linux Mint 11 too and at first glance looks very good.

---

### Post by cottfcfan on 2011-08-14
SVEN6210...
Followed your instructions in 1st post on Lucid.
Works perfectly.
Thanx for the info.

---

### Post by tulipán on 2011-08-16
hi, i went through all these steps, will reread again a couple of times and then will roll up my sleeves and get to it. at the moment, it still seems frightening, but am determined to get through it!
i was so so so disappointed when the wifi didnt work on my brand new shiney hp g62 when i wiped suse off for 10.10. but now, i can have hope :)
thank you so much for all your questions and for all your patience and answers, Sven's, especially!:p

---

### Post by Kurtosis on 2011-08-19
Hey Sven, thanks so much for writing this up, been working around this problem by tethering my phone for the past several months.  This finally fixed it.  Muchos gracias!

Asus EeePC 1000HE
Ubuntu Netbook Edition 10.04
Linux 2.6.32.33-generic

---

### Post by ld114 on 2011-10-07
Just use this process to get a Belkin PCI card (using RT2860) working with an elderly Vaio VGC-M1 desktop running 10.04. (Had Natty running, but Lucid seems snappier and more stable.)

Following the instructions closely, it all worked fine. Many thanks!!

---

### Post by Roamingrickshaws on 2011-11-19
](*,)It's taken me three days of perseverense to have success getting the wireless card to communicate using Linux... Hopefully now this has been my initiation into the world of the Open Source community!

Goooooooooooooooodbye commercial software madness, and after this experience there is no other way to describe the status quo other than "MAD".

May common sense yet prevail! 

Thank you for this thread!

---

### Post by jameswm on 2011-11-22
This is driving me crazy. I'm almost ready to go back to Windows. I've been trying to get my wirless to work for the last 4 or 5 days. I can't find a method ANYWHERE. This one doesn't work either. I have a Ralink rt3090 wireless card. I downloaded the rt3090 driver from the website. I did steps 1 through 4 just fine, and I do 5 and get the following code > 
[SIZE=3][FONT=Times New Roman]james@james-Lenovo-B575:~/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO$ sudo make[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][sudo] password for james:[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make -C tools[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[1]: Entering directory `/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]gcc -g bin2h.c -o bin2h[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[1]: Leaving directory `/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools/bin2h[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]cp -f os/linux/Makefile.6 /home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/Makefile[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make -C /lib/modules/3.0.0-12-generic/build SUBDIRS=/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux modules[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  CC [M]  /home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.o[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.c: In function ‘RTMPMakeRSNIE’:[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.c:2417:1: error: expected expression before ‘WPA_MIX_PAIR_CIPHER’[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[2]: *** [/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux/../../common/cmm_wpa.o] Error 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[1]: *** [_module_/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux] Error 2[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[1]: Leaving directory[/FONT][/SIZE]

 
And then when I try to do sudo make install I get (there are line breaks because I saved to .docx in Libre for this one)> 
[SIZE=3][FONT=Times New Roman]james@james-Lenovo-B575:~/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO$ sudo make install[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][sudo] password for james: [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make -C /home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux -f Makefile.6 install[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]mkdir: cannot create directory `/etc/Wireless': File exists[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[1]: Entering directory `/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]rm -rf /etc/Wireless/RT2860STA[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]mkdir /etc/Wireless/RT2860STA[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]cp /home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]install -d /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]install -m 644 -c rt3090sta.ko /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]install: cannot stat `rt3090sta.ko': No such file or directory[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[1]: *** [install] Error 1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make[1]: Leaving directory `/home/james/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]make: *** [install] Error 2[/FONT][/SIZE]


---

### Post by cottfcfan on 2011-11-22
James..
What version of Ubuntu are you using?
Your kernel 3.0.0-12, indicates you are using 11.10, in which case you shouldn't need to compile anything.
The rt3090 chipset uses the rt2800pci module, and that should work out of the box.

---

### Post by jameswm on 2011-11-22
> **cottfcfan said:**
> James..
What version of Ubuntu are you using?
Your kernel 3.0.0-12, indicates you are using 11.10, in which case you shouldn't need to compile anything.
The rt3090 chipset uses the rt2800pci module, and that should work out of the box.

Yes, I'm using 11.10. It didn't work on 10.04, or 11.04, or 11.10. 
I don't know what to do. D:

---

### Post by cottfcfan on 2011-11-22
What do "lspci" & "lsmod" show in a terminal?

---

### Post by jameswm on 2011-11-22
> **cottfcfan said:**
> What do "lspci" & "lsmod" show in a terminal?

lspci
> james@james-Lenovo-B575:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc AMD Radeon HD 6310 GraphicsATI
00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

lsmod
> james@james-Lenovo-B575:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_conexant    62197  1 
snd_hda_codec_hdmi     32040  1 
sp5100_tco             13791  0 
joydev                 17693  0 
arc4                   12529  2 
rt2800pci              18715  0 
rts5139               351143  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
psmouse                73882  0 
binfmt_misc            17540  1 
serio_raw              13166  0 
cfg80211              199587  2 rt2x00lib,mac80211
k10temp                13166  0 
eeprom_93cx6           12725  1 rt2800pci
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
snd_seq_midi           13324  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
wmi                    19256  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
video                  19412  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29991  2 snd_pcm,snd_seq
radeon               1015995  4 
snd                    68266  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
i2c_piix4              13301  0 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236330  6 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci


---

### Post by rainbowdash443 on 2011-11-22
Why Not Run 11.10?:wink:

---

### Post by jameswm on 2011-11-22
> **rainbowdash443 said:**
> Why Not Run 11.10?:wink:

Edit: nvm, I see your re: was to someone else

---

### Post by cottfcfan on 2011-11-22
Well you're using exactly the same wireless card as me.
rt2800pci is loading which is what 11.10 is using to connect.
Don't you see any networks at all when you click your Network icon?

---

### Post by jameswm on 2011-11-22
I took a suggestion and blacklisted acer_wmi and it helped nothing. Also, "Enable Wireless" is grayed out. Also, "Enable Wireless" is grayed out.

---

### Post by cottfcfan on 2011-11-23
Looking at your lsmod & lspci, you shouldn't need to blacklist anything.
It may be though that now you have tried installing the rt3090sta driver from Ralink, you're wireless is screwed.
This guide only really works well on 10.04 with the 2.6.32 kernel.
Like I said this card should have worked out of the box in both 11.04 & 11.10.
If you boot into the live CD, and click the wireless icon, do you see any networks at all?

---

### Post by chili555 on 2011-11-23
> Yes, I'm using 11.10. It didn't work on 10.04, or 11.04, or 11.10.
I don't know what to do. D:Please let us see:```
iwconfig
sudo iwlist scan
md5sum /lib/firmware/rt2860.bin
dmesg | grep rt2
```Thanks.

---

### Post by jameswm on 2011-11-23
> **chili555 said:**
> Please let us see:```
iwconfig
sudo iwlist scan
md5sum /lib/firmware/rt2860.bin
dmesg | grep rt2
```Thanks.

james@james-Lenovo-B575:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
james@james-Lenovo-B575:~$ sudo iwlist scan
[sudo] password for james: 
Sorry, try again.
[sudo] password for james: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

---

### Post by chili555 on 2011-11-23
> **jameswm said:**
> james@james-Lenovo-B575:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
james@james-Lenovo-B575:~$ sudo iwlist scan
[sudo] password for james: 
Sorry, try again.
[sudo] password for james: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is downAnd how about the other two I requested?

---

### Post by jameswm on 2011-11-23
Oh, sorry. I copy/pasted all the commands at once and thought that would work. 

md5sum /lib/firmware/rt2860.bin
> james@james-Lenovo-B575:~$ md5sum /lib/firmware/rt2860.bin
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin

and

dmesg | grep rt2
> james@james-Lenovo-B575:~$ dmesg | grep rt2
[   34.350488] rt2800pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   34.350508] rt2800pci 0000:03:00.0: setting latency timer to 64
[   34.398508] Registered led device: rt2800pci-phy0::radio
[   34.398587] Registered led device: rt2800pci-phy0::assoc
[   34.398660] Registered led device: rt2800pci-phy0::quality
[   35.186819] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware


---

### Post by jameswm on 2011-11-23
OMG. I'm an idiot. The fix was simple. Ubuntu was set to load before the wireless card. Thank you SO much for your time, and I'm sorry you wasted it.

---

### Post by chili555 on 2011-11-23
Glad it's working and I was happy to help.

---

### Post by UnderPar on 2011-12-18
I found this thread via a search for RT2760, the wireless card in my daughter's dual-boot WinXP/Ubuntu 10.04.  

I just upgraded to the Belkin N750 DB router from the version just below it and couldn't get her card to connect, due to the WPA security setting.  The fix instructions in this thread are way above my Linux skill set, so I instead just disabled security completely, and used the MAC Address filtering to add all of the allowed devices in the house.

[INDENT]    [QUOTE=Belkin]**MAC Address Filtering**
 
The  MAC Address Filter is a powerful security feature that allows you to  specify which computers are allowed on the network. Any computer  attempting to access the network that is not specified in the filter  list will be denied access. When you enable this feature, you must enter  the MAC address of each client on your network to allow network access  to each. To enable this feature, select "Enable MAC Address Filtering".  Next, enter the MAC address of each computer on your network by clicking  "Add" and entering the MAC address in the space provided. Click "Apply  Changes" to save the settings. To delete a MAC address from the list,  simply click "Delete" next to the MAC address you wish to delete. Click  "Apply Changes" to save the settings.

 Note:  you will not be able to delete the MAC address of the computer you are  using to access the Router's administrative functions. (The computer you  are using now).[/QUOTE][/INDENT]  


This solved her connection problem, but I am wondering if there is any danger to this method.  Thanks.

---

### Post by kingcoldcuts on 2011-12-28
I guess actually I'm the idiot. Ubuntu was set to load before the wireless card? Is this a BIOS setting I would need to change?

I have been searching threads for a way to make my RT3090 work for the last week. There are lots of suggested workarounds, none of which I have been successful with.

I am running 11.10. It is a fresh install. I've seen that this card should work out of the box in this version of Linux, but it does not. The machine is a desktop, HP Pavillion p6754y and it is currently running over a wired ethernet connection.

The card seems to recognize wireless networks, but will not connect. Network Manager constantly asks me for my network password (which I have checked 1000+ times to make sure I am inputting it correctly). The connection NEVER authorizes. Wireless will lay dormant for about 5 minutes, and then the cycle will begin again.

Any help at all would be immensely appreciated.

Thank You.

---

### Post by chili555 on 2011-12-28
> **kingcoldcuts said:**
> 

I am running 11.10. It is a fresh install. I've seen that this card should work out of the box in this version of Linux, but it does not. Ubuntu version 11.10 is a different case. I believe the driver it loads is now rt2800pci. Please confirm with:```
lsmod | grep rt2
```Is your network WPA or WPA2 or the difficult and tricky mixed WPA and WPA2 mode? Can you switch it to WPA2 only before we proceed?

Are there any clues here?```
sudo cat /var/log/syslog | grep -e rt2 -e wlan -e etwork | tail -n20
```Please try this after you detach the ethernet cable and try to connect with wireless. We don't care to see a log of how beautifully your ethernet connects!

---

### Post by kingcoldcuts on 2011-12-28
Here's the output from both commands. I wish I had some idea what I'm looking at. Not my priority right now though.

                                  rt2800pci              18340  0  
 rt2800lib              48909  1 rt2800pci 
 crc_ccitt              12595  1 rt2800lib 
 rt2x00pci              14202  1 rt2800pci 
 rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci 
 mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib 
 cfg80211              172392  2 rt2x00lib,mac80211 
 eeprom_93cx6           12653  1 rt2800pci
  

 

 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <warn> No agents were available for this request. 
 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7] 
 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <warn> Activation (wlan0) failed for access point (Willman) 
 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <info> Marking connection 'Willman' invalid. 
 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <warn> Activation (wlan0) failed. 
 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0] 
 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <info> (wlan0): deactivating device (reason 'none') [0] 
 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS. 
 Dec 28 04:02:18 drew-p6754y NetworkManager[939]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS. 
 Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0] 
 Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> (wlan0): deactivating device (reason 'none') [0] 
 Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS. 
 Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS. 
 Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> (wlan0): taking down device. 
 Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> WiFi hardware radio set disabled 
 Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> WiFi now disabled by radio killswitch 
 Dec 28 13:07:59 drew-p6754y NetworkManager[939]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds) 
 Dec 28 13:08:03 drew-p6754y NetworkManager[939]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40] 
 Dec 28 13:08:03 drew-p6754y NetworkManager[939]: <info> (eth0): deactivating device (reason 'carrier-changed') [40] 
 Dec 28 13:08:03 drew-p6754y NetworkManager[939]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1051

The network is solely WPA2.

---

### Post by chili555 on 2011-12-28
> Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> WiFi hardware radio set disabled
Dec 28 04:02:23 drew-p6754y NetworkManager[939]: <info> WiFi now disabled by radio killswitch What?? Isn't this a desktop machine??? What does this tell us?```
sudo rfkill unblock all
rfkill list all
```

---

### Post by kingcoldcuts on 2011-12-28
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


Yes. It is a desktop.

---

### Post by kingcoldcuts on 2011-12-28
I am so sorry. Let's start again? I forgot that I disabled wireless in the network manager because I got tired of all the prompts to enter the network password. /facepalm

Here are the outputs form the commands given thus far:

                                  rt2800pci              18340  0  
 rt2800lib              48909  1 rt2800pci 
 crc_ccitt              12595  1 rt2800lib 
 rt2x00pci              14202  1 rt2800pci 
 rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci 
 mac80211              393459  3 rt2800lib,rt2x00pci,rt2x00lib 
 cfg80211              172392  2 rt2x00lib,mac80211 
 eeprom_93cx6           12653  1 rt2800pci 
  

 

 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0] 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0] 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Activation (wlan0/wireless): connection 'Willman' has security, and secrets exist.  No new secrets needed. 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Config: added 'ssid' value 'Willman' 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Config: added 'scan_ssid' value '1' 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Config: added 'key_mgmt' value 'WPA-PSK' 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Config: added 'psk' value '<omitted>' 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> Config: set interface ap_scan to 1 
 Dec 28 13:39:14 drew-p6754y NetworkManager[939]: <info> (wlan0): supplicant interface state: disconnected -> scanning 
 Dec 28 13:39:15 drew-p6754y NetworkManager[939]: <info> (wlan0): supplicant interface state: scanning -> authenticating 
 Dec 28 13:39:15 drew-p6754y kernel: [39853.968236] wlan0: authenticate with 00:15:e9:69:5a:ca (try 1) 
 Dec 28 13:39:15 drew-p6754y kernel: [39853.969726] wlan0: authenticated 
 Dec 28 13:39:15 drew-p6754y NetworkManager[939]: <info> (wlan0): supplicant interface state: authenticating -> associating 
 Dec 28 13:39:15 drew-p6754y kernel: [39853.984205] wlan0: associate with 00:15:e9:69:5a:ca (try 1) 
 Dec 28 13:39:15 drew-p6754y kernel: [39853.985983] wlan0: deauthenticated from 00:15:e9:69:5a:ca (Reason: 6) 
 Dec 28 13:39:15 drew-p6754y NetworkManager[939]: <info> (wlan0): supplicant interface state: associating -> disconnected 
  

  
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


My apologies.

EDIT: I feel like maybe I should start a new thread? Posting like this in a thread marked SOLVED does not seem right.

---

### Post by chili555 on 2011-12-28
> I feel like maybe I should start a new thread? Posting like this in a thread marked SOLVED does not seem right.It's your choice. I get notifications and answer here as well as anywhere.

I have read a number of posts that suggest power management may be an issue. Please try:```
sudo iwconfig wlan0 power off
```If there is improvement, we can tweak one file to make it persistent.

---

### Post by kingcoldcuts on 2011-12-28
I tried it. No joy.

If you are getting email notifications, I will stay in this thread for now. Thanks for trying to help me troubleshoot this.

---

### Post by acc1729 on 2012-01-01
I'm having an issue at step 5. I'm new to linux and would appreciate help.

I'm using LMDE, GNOME 64-bit if it helps.

```
acc@acccomp /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 $ sudo make
make -C tools
make[1]: Entering directory `/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/2.6.39-2-amd64/build SUBDIRS=/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.39-2-amd64'
  CC [M]  /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.o
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg2Action’:
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c:845:25: warning: variable ‘pHeader’ set but not used [-Wunused-but-set-variable]
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg3Action’:
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c:978:18: warning: variable ‘pHeader’ set but not used [-Wunused-but-set-variable]
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c: In function ‘PeerPairMsg4Action’:
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c:1106:25: warning: variable ‘pHeader’ set but not used [-Wunused-but-set-variable]
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c: In function ‘RTMPMakeRSNIE’:
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c:2415:2: error: expected ‘,’ or ‘;’ before ‘rsnielen_cur_p’
/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.c:2409:10: warning: variable ‘rsnielen_ex_cur_p’ set but not used [-Wunused-but-set-variable]
make[4]: *** [/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/cmm_wpa.o] Error 1
make[3]: *** [_module_/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.39-2-amd64'
make: *** [LINUX] Error 2
acc@acccomp /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 $ sudo make install
make -C /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.39-2-amd64/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/2.6.39-2-amd64/kernel/drivers/net/wireless/
install: cannot stat `rt3562sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
make: *** [install] Error 2
acc@acccomp /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 $ sudo ifconfig wlan0 down
acc@acccomp /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 $ sudo rmmod rt2860sta
ERROR: Module rt2860sta does not exist in /proc/modules
acc@acccomp /home/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 $ 

```

---

### Post by chili555 on 2012-01-01
> DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_[COLOR="Red"]2010[/COLOR]1217I don't know how or if it's possible to get this relative old-timer to work with your 2.6.39 kernel. If it were me, I'd try to get rt2800pci working; perhaps with newer firmware. Would you care to start a new thread and leave the link here?> make: *** [LINUX] Error 2For your reference and for the searchers, when you get this message, stop; everything else following will be erroneous as well. As the old saying goes, "You can't make a silk purse out of a Linux *make* error."

---

### Post by UnderPar on 2012-01-02
> **UnderPar said:**
> I found this thread via a search for RT2760, the wireless card in my daughter's dual-boot WinXP/Ubuntu 10.04.  

I just upgraded to the Belkin N750 DB router from the version just below it and couldn't get her card to connect, due to the WPA security setting.  The fix instructions in this thread are way above my Linux skill set, so I instead just disabled security completely, and used the MAC Address filtering to add all of the allowed devices in the house.

[INDENT]    [/INDENT]  


This solved her connection problem, but I am wondering if there is any danger to this method.  Thanks.
Updating to 11.10 solved the wireless card problem.

---

### Post by hoks on 2012-02-01
thanks a lot, this works like a charm.
this driver problem with my msi wind U100 netbook kept bugging me for months!!
tried many things, but only this solutions seems to work smoothly.

---

### Post by nowifi on 2012-02-13
Same problem on my machine (HP mini 110).

Note: though the following procedure is a relatively elementary and easy process to effect a Lucid UNR 10.04 Live CD wireless connection, it is manually labour intensive,  particularly step **2**. This compromises the very essence of a computer to automate tasks.

**1.** Ralink wireless driver (my RT3090 uses the RT2860 driver) does not function with Ubuntu  UNR 10.04. (run from Live CD - actually from a Live SD  write locked SD  card created as Live USB)

**2.** Once driver is functioning, connections to non-broadcasting  SSID routers fail.

These steps will make the connection ...

**1.** requires:
```

[COLOR=Navy][B]sudo su
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
exit[/B][/COLOR]
```and
**2.** requires```

[COLOR=Blue]**sudo iwconfig wlan0 essid <non-broadcast  SSID> key s:<ASCII passcode string>**[/COLOR]
```**1.**  The first command sequence fixes: 
 ```

[COLOR=Blue]**dmesg | grep RT**[/COLOR]
[   35.973068] RtmpOSFileOpen(): Error 2 opening  /etc/Wireless/RT2860STA/RT2860STA.dat
[   35.973078] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[   36.297303] RtmpOSFileOpen(): Error 2 opening  /etc/Wireless/RT2860STA/RT2860STA.dat
[   36.297312] Open file "/etc/Wireless/RT2860STA/RT2860STA.dat" failed!
[  200.006646] Read file "/etc/Wireless/RT2860STA/RT2860STA.dat"  failed(errCode=0)! 
```[B]

2.[/B] The second terminal command is needed in Ubuntu to coerce the  protocol connection from Network Manager while Dis/En-abling Wireless  Networking.

ref:

*[Ubuntu can not connect a wireless RaLink RT3090 to a  hidden network]("http://ubuntuforums.org/showthread.php?p=11662679#post11662679")*

*[Re: Can't connect to hidden wireless in Ubuntu 10.10]("http://ubuntuforums.org/showthread.php?p=11664194#post11664194")*

---

### Post by chili555 on 2012-02-13
Wouldn't it work better and permanently to actually write a .dat file with the required items in it??? For example, minimally:```
#The word of "Default" must not be removed
Default
SSID=whatever
NetworkType=Infra
WirelessMode=9
AuthMode=WEPAUTO
EncrypType=WEP
DefaultKeyID=1
Key1Type=1
Key1Str=yoursecretkey

```

---

### Post by nowifi on 2012-02-14
Perhaps - but 

[LIST=1]
[*]the Live CD would need to be recast with that personalized custom  .dat file - it would have been best if the 10.04 UNR Live CD pressing  had been  configured with the generic null /etc/Wireless/RT2860STA/RT2860STA.dat  file  present and not missing, to at least avoid the [FONT=Courier New][COLOR=Blue]**dmesg | grep RT**[/COLOR][/FONT] error
[*]the proposed .dat file has a visible machine resident clear text  copy of the pass code which is permanently there as opposed to a  transient pass code manifestation when invoking a connection via [FONT=Courier New][COLOR=Blue]**sudo iwconfig ...**[/COLOR][/FONT] - a  compromise would be to have a script with everything but the pass code  defined so that on execution the pass code is typed as a requested  parameter and thus not permanently resident in a file on the machine - an advantage to  binding the script to both NM and [FONT=Courier New][COLOR=Blue]**sudo  iwconfig ...**[/COLOR][/FONT] is that it masks the extra [FONT=Courier  New][COLOR=Blue]**sudo iwconfig ...**[/COLOR][/FONT] overhead - I require that the  pass code be typed into NM on every connect anyway
[*][FONT=Courier New][COLOR=Blue]**gconf-editor**[/COLOR][/FONT] [FONT=Courier New]**[COLOR=Blue]/system/networking/connections/ ...[/COLOR]**[/FONT]  registers Network Manager's configuration for connection attempts to non-broadcasting SSID routers and it appears to be NM's limitatons  that is the short fall which can be monitored with [FONT=Courier  New]**[COLOR=Blue]sudo iwlist scan [/COLOR]**[/FONT]though it  appears that changing the software for the RT2860 driver and not NM may  resolve the non-broadcasting SSID router connect problem - however, there is a large volume of anecdotal information about NM's failure to connect other wireless hardware with non-broadcasting SSID routers
[*]it would be best if the UNR 10.04 symbiosis of RT2860 wireless driver and NM  worked properly, circumventing the obtuse need for [FONT=Courier New]**[COLOR=Blue]sudo iwconfig wlan0 essid  <hidden SSID> key s:<ASCII password string>[/COLOR]**[/FONT]  to coerce a connection
[/LIST]

---

### Post by gdea73 on 2012-03-15
I appreciate everyone's hard work and effort regarding this problem. I tried following these instructions on my Lenovo IdeaPad Z575, with the RT3090 chipset and according drivers, and I still can't get anything to work. The "addithional drivers" dialog box tells me that the "rt3090sta" module is activated and in use, but network manager says that the "Device is not ready" under Wireless. If I run "modprobe rt3090sta," no message appears. I get no output at all. I think the wireless may be soft-blocked but I forget the command to unblock it. It is "enabled" according to the network manager's context menu, and the Additional Drivers configurator, but I can't get it to work.

edit: solved, it was kind of strange. In short I had to blacklist asus_wmi as well.

---

### Post by chili555 on 2012-03-15
Let's have a peek at:```
dmesg | grep rt2
rfkill list all
```Thanks.

---

### Post by paeuk on 2012-03-17
I just want to say a big thanks to your Sven for taking the time to write all the instructions in your post. Having had problems with my wifi on the eee-901 for many months, stumbling across your post has worked wonders! Thanks. Now I havecompletely stable wifi connection and can even connect on my Virgin Media wifi access point which wasn't possible before! One happy camper. Thanks.

---

### Post by marrs101 on 2012-05-05
Hi!
 I'm having similar problem on EEE 1000 pc with RT2860 chipset. I tried what I found at the beginning of this thread, but it didn't work. Than I opened a thread:
[http://ubuntuforums.org/showthread.php?t=1962857](http://ubuntuforums.org/showthread.php?t=1962857)
I got some help there, but still no luck. Could You have a look, and give me some advice?
 Thanks!

---

### Post by goodron on 2012-05-27
I am fairly new to Linux but have successfully applied the original fix from this thread to an Asus Eee PC 1000H with an Ralink RL2790 wireless card under Ubuntu 12.04 LTS. So this thread is still very much valid today. 

Thank you to all involved

---

### Post by Tiler on 2012-05-29
> **goodron said:**
> I am fairly new to Linux but have successfully applied the original fix from this thread to an Asus Eee PC 1000H with an Ralink RL2790 wireless card under Ubuntu 12.04 LTS. So this thread is still very much valid today. 

Thank you to all involved

I was getting my EeePC 1000 ready to sell and reinstalled 11.04 with the same result.  It worked just fine for me.  New laptop doesn't have the problem and I'm glad to be over it.  Changing it every Kernel update was tedious.

---

### Post by fatboy07 on 2012-07-18
Is this apply same procedure if I want to install a ralink usb wifi? thanks in advance.

---

### Post by chili555 on 2012-07-18
> **fatboy07 said:**
> Is this apply same procedure if I want to install a ralink usb wifi? thanks in advance.Doubtful. Please start your own new thread and post:```
lsusb
```Thanks.

---

### Post by sianm on 2012-08-06
Thank you so much, Sven, Chris, and everyone else! Another very happy customer back on her wireless...

Running Ubuntu 12.04 on an asus eee1000he

---

### Post by Mruvek on 2012-08-28
Hi, i have problem with my wifi on Asus 1015P with easypeasy. 
lspci said that i have RaLink RT3090 as my network controller. I tried follow instructions from 1st post with RT2860 but it didn't work. What should i change?

---

### Post by chili555 on 2012-08-28
Please post:```
lsb_release -d
lspci -nn | grep 0280
```Thanks.

---

### Post by Mruvek on 2012-08-29
```
lsb_release -d
Description:    EasyPeasy 1.6
lspci -nn | grep 0280
03:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
 
```

---

### Post by chili555 on 2012-08-29
Let's check (he asks knowingly) if the version of rt2860sta covers your device:> Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [[COLOR="Red"]1814:3090[/COLOR]]Please run:```
modinfo rt2860sta
```I believe it does *NOT* list in its alias fields any 3090. 

I suggest you try the package RT[COLOR="Red"]3090[/COLOR]PCIe here: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

---

### Post by Mruvek on 2012-08-29
```
Error: modinfo: could not find module rta2860sta

```

Ok, so I downloaded RTA3090PCIe, but what should i change in commands from 1st post? There are instructions for 2860.

---

### Post by chili555 on 2012-08-29
> Error: modinfo: could not find module rt[COLOR="Red"]a[/COLOR]2860staIt is actually:```
modinfo rt2860sta
```The rename of the file to extract a second time is fixed. Extract once and proceed.

You can probably skip this:> Use the find command to locate MIX_CIPHER_NOTUSE. Replace the entire line (keep on one line) with this code:
WPA_MIX_PAIR_CIPHER FlexibleCipher = WPA_TKIPAES_WPA2_TKIPAES;

Check what the file says; it's probably fixed.

You already have gcc, so skip that step.

Do *NOT* skip this step:> Step 3
Code:

gedit ./os/linux/config.mk

Use the find command to locate HAS_WPA_SUPPLICANT and make sure it is set to y for yes. It should look like this when finished:
HAS_WPA_SUPPLICANT=y


Use the find command to locate HAS_NATIVE_WPA_SUPPLICANT_SUPPORT and make sure it is set to y for yes. It should look like this when finished:
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y


Close and save this file.
Skip this step:> Step 6
Rename the old rt2860sta.ko driver file to rt2860sta.ko.dist using:

Code:

sudo mv /lib/modules/2.6.*/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist

Attention: you need to replace the * with the actual directory name of your kernel, please check the folder name with Nautilus.

Then I'd compile with:```
cd Desktop/RT3090files  [COLOR="Red"]<--or whatever you extracted[/COLOR]
sudo su
make
make install
exit
```I'll be back in a few after I actually compile it.

---

### Post by Mruvek on 2012-08-29
I can't compile:

```
root@kralkowski-laptop:/home/kralkowski/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO# make
make -C tools
make[1]: Entering directory `/home/kralkowski/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/kralkowski/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/tools'
make: *** [build_tools] Error 2
root@kralkowski-laptop:/home/kralkowski/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO# make install
make -C /home/kralkowski/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/kralkowski/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/kralkowski/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3090sta.ko /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3090sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/kralkowski/20101216_RT3090_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/os/linux'
make: *** [install] Error 2


```

---

### Post by chili555 on 2012-08-29
> make[1]: gcc: Command not foundPlease do:```
sudo apt-get install build-essential
```Then try again.

It makes for me with warnings but no errors on kernel 2.6.32 which is as close as I have to EasyPeasy. The module will be loaded with:> sudo modprobe rt3090sta

---

### Post by Mruvek on 2012-08-29
apt-get didn't worked too, but i do something in Synaptic Package Manager, then install build-essentials, compile and now I have wireless connection! Thanks A LOT, i wish everyone everywhere solve problems like you :D

---

### Post by chili555 on 2012-08-29
Thank you for your kind words! Glad it's working.

Don't forget, when a newer linux-image is installed by Update Manager, you'll need to recompile:```
cd Desktop/RT3090files  [COLOR="Red"]<--or whatever you extracted[/COLOR]
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
exit
```

---

