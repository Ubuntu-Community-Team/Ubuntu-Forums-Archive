---
title: "Installation of 12.04 stopped by missing Broadcom driver"
date: 2012-04-27
forum: Networking &amp; Wireless
---

### Post by gefalu2008 on 2012-04-27
I have not been able to install Ubuntu 12.04 Precise Pangolin to my Acer Aspire 3620 which currently runs 11.10.

The installation always stops showing the "Ubuntu" text & the 5 red dots below.

The code below seems to indicate what is wrong:

[B]* Starting Mount network filesystems
* Stopping Mount network filesystems
[   102.329548] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   102.331605] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   102.329548] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware]("http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware") and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/B]

I have checked the ISO file & the cd I burned by their MD5sums.

a) Is this a bug that should be addressed by Canonical
b) Probably I should disable networks or at least the in-built wlan-card before or during the installation, but how should I do that?
c) Or how should I proceed with the installation?

I enjoy my old 11.10 very much and soon hope to start 12.04 as well.

---

### Post by westie457 on 2012-04-27
> **gefalu2008 said:**
> I have not been able to install Ubuntu 12.04 Precise Pangolin to my Acer Aspire 3620 which currently runs 11.10.

The installation always stops showing the "Ubuntu" text & the 5 red dots below.

The code below seems to indicate what is wrong:

[B]* Starting Mount network filesystems
* Stopping Mount network filesystems
[   102.329548] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   102.331605] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   102.329548] b43-phy0 ERROR: [COLOR="Red"]You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware]("http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware") and download the correct firmware for this driver version. Please carefully read all instructions on this website[/COLOR].[/B]

I have checked the ISO file & the cd I burned by their MD5sums.

a) Is this a bug that should be addressed by Canonical
b) Probably I should disable networks or at least the in-built wlan-card before or during the installation, but how should I do that?
c) Or how should I proceed with the installation?

I enjoy my old 11.10 very much and soon hope to start 12.04 as well.

You could try plugging an ethernet cable and follow the suggested solution.

---

### Post by gefalu2008 on 2012-04-27
Thank you for your suggestion.

An ethernet cable is plugged. The suggested lines of action are many. I do not know which one to follow.

Please add further hints.

---

### Post by gefalu2008 on 2012-04-27
You see, I cannot add the driver to the 12.04 system because the system cannot be installed and launched.

I have the correct driver in the old 11.10 system (and it works fine) but that system will be run over by the new one. (Actually I intend to install the new system alongside the old one.)

So at the moment I do not know how to proceed.

Thanks again for your consideration.

---

### Post by cooper14 on 2012-04-27
I had the same problem with a Dell Latitude D610.

For me it worked out to put the b43 broadcom driver to the blacklist by entering the following to the kernel comand line:

b43.blacklist=yes

Then I installed 12.04 using an ethernet connection and installed the braodcom driver afterwards.

---

### Post by gefalu2008 on 2012-04-28
Thank you very much! I had some difficulty in understanding where to write "b43.blacklist=yes". The solution is given in a quote below. It involves the use of the F6 key which was something completely new to me. 


"Insert your device into your computer containing the installation ISO of Ubuntu (Whether CD, DVD, USB stick or whatever), wait for appearance of this screen

and Immediately press a button. Choose the language of the installer and press enter. You will see something similar to this:

at this point position yourself to "Try Ubuntu without installing" or "Install Ubuntu" (Is irrelevant) but DO NOT PRESS ENTER: instead the press F6, Immediately followed by the ESC key: You should be able to write in a textbox. Now go (in the textbox) more to the right that can, leave intact the existing text and write, Appended to it (and being careful that after the two dashes there is a space), the string

    b43.blacklist=yes

after that press Sending.

system installation will start and will not hang over!"

Source: [http://linux-software-news-tutorials.blogspot.com/2012/04/installing-ubuntu-1204-crashes-because.html](http://linux-software-news-tutorials.blogspot.com/2012/04/installing-ubuntu-1204-crashes-because.html)

---

### Post by p_motch on 2012-04-29
The "b43.blacklist=yes" solution worked perfectly! I was having the same issues others were describing when I was installing 12.04 64bit desktop. The laptop is a HP Pavilion dv5135nr.

---

### Post by notesetter on 2012-05-04
I have the same problem with a Compaq laptop and PCMCIA BCM 4318. I've already installed Ubuntu Studio 12.04 and downloaded a ton of software. I don't want to scrap the partition and start over.

Is there a way to fix this without starting a fresh install?

I've already installed the firmware-b43-installer package but Ubuntu still crashes as soon as I insert the card or on startup if I boot with the card already inserted.

For what it's worth, Debian 6 has worked flawlessly with the card.

---

### Post by gefalu2008 on 2012-05-06
If a missing Broadcom driver prevents you from launching your 
computer, you can proceed as follows:

1. Type or copy the following command into the terminal:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

2. Add the following line at the end of blacklist.conf document:

```
blacklist b43
```

Save the document and close it.

3. Remove needless Broadcom drivers by the following two terminal commands:

```
sudo apt-get purge broadcom-sta-common broadcom-sta-source bcmwl-kernel-source
```
```
sudo apt-get purge b43-fwcutter firmware-b43-installer
```

4. Restart the computer

5. Install the appropriate drivers for the 12.04 system by typing

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

6. *Remove* this line at the end of sudo gedit /etc/modprobe.d/blacklist.conf

```
blacklist b43
```

Save the document and close it

7. Restart the computer

8. Open the following settings by typing

```
sudo gedit /etc/modules
```

9. Add the following short line at the end of the document:

```
b43
```

Save the document and close it.

Let us know if these steps were useful.

---

### Post by notesetter on 2012-05-06
gefalu2008, this method worked like a champ. Thanks.

Should it be a sticky?

---

### Post by JauntyJack on 2012-07-01
> **gefalu2008 said:**
> If a missing Broadcom driver prevents you from launching your 
computer, you can proceed as follows:

1. Type or copy the following command into the terminal:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```2. Add the following line at the end of blacklist.conf document:

```
blacklist b43
```Save the document and close it.

3. Remove needless Broadcom drivers by the following two terminal commands:

```
sudo apt-get purge broadcom-sta-common broadcom-sta-source bcmwl-kernel-source
``````
sudo apt-get purge b43-fwcutter firmware-b43-installer
```4. Restart the computer

5. Install the appropriate drivers for the 12.04 system by typing

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```6. *Remove* this line at the end of sudo gedit /etc/modprobe.d/blacklist.conf

```
blacklist b43
```Save the document and close it

7. Restart the computer

8. Open the following settings by typing

```
sudo gedit /etc/modules
```9. Add the following short line at the end of the document:

```
b43
```Save the document and close it.

Let us know if these steps were useful.

This worked perfectly! I recently upgraded to 12.04 and my wireless  stopped working. I have the Broadcom 4318 card. Thanks for such clear steps. I had tried many other solutions from the forum, but only this one worked. Thanks again. Cheers!

---

### Post by alexperez on 2012-07-15
Great tuto. I got mad about this issue with an old Toshiba Satellite Pro 6110 and Lubuntu 12.04. Now it's all running fine.
Thnx.

---

### Post by KittyCatHerder on 2013-03-24
Hello. This is my first post at ubuntuforums. I posted in another ubuntu forum before but this one seems much better organized and populated. I cam to this thread from a referral by [http://ubuntuforums.org/showthread.php?t=1974496](http://ubuntuforums.org/showthread.php?t=1974496), which was created because a 12.04 user got an error when issuing ```
ifconfig wlan0 up
```. I get the same error on my 12.04 Acer netbook with broadcom WiFi. I followed the instructions on this thread and now I am unable to connect to WiFi. The WiFi antenna/signal icon on the upper dock now shows 'empty', and issuing ```
ifconfig wlan0 up
``` returns the same error as before.

My question is, should I try to reverse the process outlined in this thread in order to reverse its effects? Or is there something else I need to do to get my WiFi working again? I would like my WiFi card to identify correctly but that is secondary to it actually functioning to connect to my network.

Also, since the instructions here didn't work for me, is there another technique for getting my broadcom card to be 'recognied' (I've only been using Linux for about a year or so so my terminology, and just regular knowledge, is still coming).

---

### Post by matt_symes on 2013-03-24
Thread moved to **Networking and Wireless**.

@[**[COLOR=#000000]KittyCatHerder[/COLOR]**]("http://ubuntuforums.org/member.php?u=1803188"). Welcome to the forums :D

I would start a new thread in the Networking and Wireless subforum stating your problem and referencing this thread (put a link to this thread in your new thread)

This thread has been marked as solved and was started in April 2012, so it may not be looked at by people who could help you.

---

### Post by KittyCatHerder on 2013-03-24
> **matt_symes said:**
> Thread moved to **Networking and Wireless**.

@[**[COLOR=#000000]KittyCatHerder[/COLOR]**]("http://ubuntuforums.org/member.php?u=1803188"). Welcome to the forums :D

I would start a new thread in the Networking and Wireless subforum stating your problem and referencing this thread (put a link to this thread in your new thread)

This thread has been marked as solved and was started in April 2012, so it may not be looked at by people who could help you.

Thanks, matt_symes. I will do that. I thought I should post here since I've read a few threads which other members don't seem to appreciate due to the issue cited having already been addressed. I will go now and post a new thread. I miss Ubuntu! Using Windows sort of feels like walking through a history museum after being on Ubuntu.

---

### Post by sureshvv on 2013-03-30
When I try to install firmware-b43-installer, I get:

firmware-b43-installer: Depends b43-fwcutter (>= 1:015-9) but it is not going to be installed

How do I get around this?

---

### Post by chili555 on 2013-03-30
> **sureshvv said:**
> When I try to install firmware-b43-installer, I get:

firmware-b43-installer: Depends b43-fwcutter (>= 1:015-9) but it is not going to be installed

How do I get around this?On another thread, you are having trouble installing the STA driver. They are not interchangeable and not for the same devices. Please start your own new thread and include:```
lspci -nn | grep 0280
```

---

### Post by ottabaub on 2013-05-27
> **gefalu2008 said:**
> If a missing Broadcom driver prevents you from launching your 
computer, you can proceed as follows:

1. Type or copy the following command into the terminal:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

2. Add the following line at the end of blacklist.conf document:

```
blacklist b43
```

Save the document and close it.

3. Remove needless Broadcom drivers by the following two terminal commands:

```
sudo apt-get purge broadcom-sta-common broadcom-sta-source bcmwl-kernel-source
```
```
sudo apt-get purge b43-fwcutter firmware-b43-installer
```

4. Restart the computer

5. Install the appropriate drivers for the 12.04 system by typing

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

6. *Remove* this line at the end of sudo gedit /etc/modprobe.d/blacklist.conf

```
blacklist b43
```

Save the document and close it

7. Restart the computer

8. Open the following settings by typing

```
sudo gedit /etc/modules
```

9. Add the following short line at the end of the document:

```
b43
```

Save the document and close it.

Let us know if these steps were useful.

Excellent, well-detailed procedure. It would be nice if everyone posted clear explanations like this one.  
While my computer (Dell Latitude D610) was working fine, I couldn't get the wireless to run. After trying several other suggestions found in searches, this one worked like and charm and got the wifi up and running.
Many thanks.

---

### Post by Ultra Cronic on 2014-03-15
[https://www.youtube.com/watch?v=j9PJYIfEpSw&hd=1#t=24](https://www.youtube.com/watch?v=j9PJYIfEpSw&hd=1#t=24)
This is for those who like a visual hands on demo of a quick driver load without the ndis wrapper Bovine Sovereinity.
This worked like a champ on a Dell latitude d630 with a broadcom 3905 mini card using a bcm4311 chip. Ubuntu 12.04 

This video explains a real easy install and a manual startup probe command.  

Keep in mind most people are blacklisting the b43,  Mine would NOT run without it. As a matter fact I ran the exclusive b43 drivers explained in the video.
This methoud from what I can see does not use a blacklist file.

Downside;  This does not automatically start when booting up:-(  you have to involk a sudo command to fire up your wifi card, however a quick search on google brought me to a site that shows you how to edit one line in your rc.local file in the etc folder witch will execute the probe command on start up. This is by far the neatest, quickest and easy way to fire up a peace of combative hardware. The b43.zip file for ubuntu [google it] did the trick placed extracted files in the \lib\firmware  folder. then run the command sudo modprobe -v b43

My internal broadcom wifi fired up.  Now if it works [this is important to test first in a terminal]. Add the line " modprobe -v b43 " in the etc\rc.local file use gedit in sudo mode to do this. [no quotes].  make sure the line exit 0 is the last line in your rc.local file or you will through a handfull of evil flying monkeys into your OS deeming it quite useless after that.
DO NOT use the expression " sudo " in a rc.local file.

One last thing, I am an amature, a puts, a tinkerer and a net technician, so blowing my stuff up is a fun experience, for some of you it's a disaster, so keep in mind, I tried other things before this and failed. For instance I apt-get installed a wrapper driver that did not work, however did this combination of events lead to my sucess? We don't know, I am under the impression the previous attempts did not do squat, and another note, this is basically a "Firmware" driver similar to a "Chipset" driver in Windoze, moreso on a hardware level. 
Maybe the combination of this and the previous apt-get installs worked together. It's a damn shame I did not do a clean wipe and remove before trying this DO THIS AT YOUR RISK. 
It's not idiot proof and I am just the idiot to prove it.

---

