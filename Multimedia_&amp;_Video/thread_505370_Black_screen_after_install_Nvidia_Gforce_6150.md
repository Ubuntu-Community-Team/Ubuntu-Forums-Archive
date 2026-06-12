---
title: "Black screen after install Nvidia Gforce 6150"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by nal on 2007-07-20
Ok I'm having a problem and I hope you can help.  I just downloaded Ubuntu and went to install it on my new HP pavilion dv6225us laptop, it has the Nvidia gforce go 6150 graphics card.  On live cd I get a blank screen so I restarted and used safe graphics mode.  After installation I tried to install the nvidia graphics drivers via envy but afterwards I get the black screen again. And cant use safe mode now either.  I went with a fresh install and now I'm gonna wait for help from you guys so I can get the nvidia drivers up and running perfect so hope you can help :)

---

### Post by tseliot on 2007-07-20
Does your internet connection work on Ubuntu?

If yes, then you can try Restricted Drivers Manager (which you can find in System/Administration/Restricted Drivers Manager)

---

### Post by ddrichardson on 2007-07-20
nVidia Geforce Go 6100 did this until quite recently, the restricted driver in 7.04 works perfectly. You needn't always reinstall either - try going to a another console with <CTRL><ALT><F2> (<CTRL><ALT><F7> switches back incidentally).

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Then should it all go wrong with a new driver you can go to a virtual console and:

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

Then you have X back and can try another solution.

---

### Post by nal on 2007-07-20
I tried the restricted drivers one and it did the same thing.  When I get back from work tonight I will try and use your method 2 in that walk thru you made.  Hope that helps.

---

### Post by nal on 2007-07-20
ok im a little confused so all help well be appricated.  I got home and if i run the live cd it only boots to black screen, if boot from live cd after hiting f4 and selceting 1200 by 780 it boots fine.  If install after that and try to boot i get black screen again.  So if i go to recovery mode i can get to console, I been having problems with it hanging I try to go to envy -t and install nvidia drivers, i think its due to my bcm43xx error i get for my wlan , so i do modprobe -r bcm43xx and get it reomoved the comp randomly freezes some times it freezes at boot others it freezes while trying to install the drivers via envy.  can some one please help?

---

### Post by ddrichardson on 2007-07-21
<CTRL><ALT><+> (on the numeric keypad should cycle up resolutions and <-> should cycle down. 

From [launchpad:]("https://answers.launchpad.net/ubuntu/+question/329")

> Richard Wolf  said on 2006-04-28:

I had the same error: 'bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.'

The broadcom driver needs to load some firmware before the device will work. Fortunately Dapper has a script to get this firmware for you. This worked for me:

sudo aptitude install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

Incidentally this is in the Feisty Fawn repositories too.

---

### Post by nal on 2007-07-24
thank you all so very much for your help.  Here is what finaly made it work for me.  So I hope all you guys that have this comp and is willing to try gets help from this. fist thing i did was take out my wifi card from my laptop as it made it freeze.


I installed normally by hitting f4 and choosing 1024 by 800 as my res.
After install i hit escape in grub and choose the safe mode option and it will bring ya to command prompt.
At the command prompt type apt-get install nvida-glx
After it is installed what you do is dpkg-reconfigure xserver-xorg
do manually choose graphics card.  When it asks what one you want it will be either on nv or glx i think, switch it to nvidia.
The rest is stright forward.  when it asks for memory it wants it in KB if ya dont know what it is in KB do what I do lol go to google and type in say 512 MB in KB and it will give it to ya right out.

After ya done just use the normal options for everything else.  once done do startx and ya good to go :D

hope this helps and thanks to all.

---

