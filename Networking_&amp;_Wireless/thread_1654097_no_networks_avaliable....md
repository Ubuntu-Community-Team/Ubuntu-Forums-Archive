---
title: "no networks avaliable..."
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by JackC64 on 2010-12-27
i just used wubi to install ubuntu 10.04 LTS. everything is smooth  except no networks will show up to connect to. i get the wireless icon in the  notification thing with a red exclamation point on it.
ive tried two different wireless connections, the important one being a  verizon Mifi 2200 intelligent hotspot (its not usb-style, look it up).  no matter what wifi i try, nothing shows up when i click the internet  icon in the notification thing (well, the drop down bar does but there are no networks...).

please help!

---

### Post by cipherboy_loc on 2010-12-27
What is the output of:
```
sudo lspci | grep -i 'net'
```

```
lsmod
```

and

```
cat /proc/modules
```


The first command will tell us which network interfaces you have, the second one will show us which modules you have (modules are just little interfaces to get hardware to work), and the third will tell us which modules are loaded (modules tend not to work unless they are loaded. :D )


Cipherboy

---

### Post by JackC64 on 2010-12-28
> **cipherboy_loc said:**
> What is the output of:
```
sudo lspci | grep -i 'net'
``````
lsmod
```and

```
cat /proc/modules
```The first command will tell us which network interfaces you have, the second one will show us which modules you have (modules are just little interfaces to get hardware to work), and the third will tell us which modules are loaded (modules tend not to work unless they are loaded. :D )


Cipherboy
```
sudo lspci | grep -i 'net'
```[http://img704.imageshack.us/img704/6257/screenshot1gu.png](http://img704.imageshack.us/img704/6257/screenshot1gu.png)
```
lsmod
```page 1: [http://img577.imageshack.us/img577/6953/screenshotpg1.png](http://img577.imageshack.us/img577/6953/screenshotpg1.png)
page 2: [http://img264.imageshack.us/img264/6027/screenshotpg2.png](http://img264.imageshack.us/img264/6027/screenshotpg2.png)
```
cat /proc/modules
```page 1: [http://img441.imageshack.us/img441/1801/screenshot2pg1.png](http://img441.imageshack.us/img441/1801/screenshot2pg1.png)
page 2: [http://img18.imageshack.us/img18/4061/screenshot2pg2.png](http://img18.imageshack.us/img18/4061/screenshot2pg2.png)

---

### Post by cipherboy_loc on 2010-12-29
[LEFT][FONT=Lucida Sans Unicode]Try looking at and following this if you think it will work:

[http://ubuntuforums.org/showthread.php?p=10254084](http://ubuntuforums.org/showthread.php?p=10254084)

He has the same graphics card that you have, and from what I can read you need to do something of the following:

[/FONT][FONT=Lucida Sans Unicode]```

[/FONT][FONT=Lucida Sans Unicode]cd ~/Desktop
[/FONT][FONT=Lucida Sans Unicode]wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz
[/FONT][FONT=Lucida Sans Unicode]tar -xf ./iwlwifi-*.tgz


[/FONT][FONT=Lucida Sans Unicode]cd *wifi*
sudo cp iwlwifi-6050-4.ucode /lib/firmware
sudo chmod 644 /lib/firmware/iwlwifi*
sudo chown root:root /lib/firmware/iwlwifi*
sudo rmmod -f iwlagn
sudo modprobe iwlagn


sudo apt-get install linux-backports-moudules-wireless-lucid-generic[/FONT] [FONT=Lucida Sans Unicode]
sudo linux-backports-moudules-wireless-lucid-generic
--- OR, if you are using 10.10 ---
sudo apt-get install linux-backports-moudules-wireless-maverick-generic
sudo linux-backports-moudules-wireless-maverick-generic[/FONT][FONT=Lucida Sans Unicode]
[/FONT][FONT=Lucida Sans Unicode]
```[/FONT]
[FONT=Lucida Sans Unicode]
Oh, BTW, next time when you have to post lots of output, wrap it in [code] tags (paste the output into the box, select it all, then click the pound symbol). 


Cipherboy

[/FONT]
[/LEFT]

---

### Post by JackC64 on 2010-12-29
> **cipherboy_loc said:**
> [LEFT][FONT=Lucida Sans Unicode]Try looking at and following this if you think it will work:

[http://ubuntuforums.org/showthread.php?p=10254084](http://ubuntuforums.org/showthread.php?p=10254084)

He has the same graphics card that you have, and from what I can read you need to do something of the following:

[/FONT][FONT=Lucida Sans Unicode]```


```[/FONT]```
[FONT=Lucida Sans Unicode]cd ~/Desktop
[/FONT][FONT=Lucida Sans Unicode]wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz
[/FONT][FONT=Lucida Sans Unicode]tar -xf ./iwlwifi-*.tgz


[/FONT][FONT=Lucida Sans Unicode]cd *wifi*
sudo cp iwlwifi-6050-4.ucode /lib/firmware
sudo chmod 644 /lib/firmware/iwlwifi*
sudo chown root:root /lib/firmware/iwlwifi*
sudo rmmod -f iwlagn
sudo modprobe iwlagn


sudo apt-get install linux-backports-moudules-wireless-lucid-generic[/FONT] [FONT=Lucida Sans Unicode]
sudo linux-backports-moudules-wireless-lucid-generic
--- OR, if you are using 10.10 ---
sudo apt-get install linux-backports-moudules-wireless-maverick-generic
sudo linux-backports-moudules-wireless-maverick-generic[/FONT][FONT=Lucida Sans Unicode]
[/FONT]
```
[FONT=Lucida Sans Unicode]
Oh, BTW, next time when you have to post lots of output, wrap it in [code] tags (paste the output into the box, select it all, then click the pound symbol). 


Cipherboy

[/FONT]
[/LEFT]

how do i enter that in? i know in terminal but im a linux newbie, i recognize  some stuff cuz i know windows command prompt but i dont know how to enter large amounts of code in terminal...can you help me out?

---

### Post by PatchesTheCaveman on 2010-12-29
Just copy each line, and right click in the terminal and hit Paste.  You can also press CTRL+SHIFT+V to paste it into the terminal if you would like.  (You can copy with CTRL+C just like Windows.  SHIFT is only necessary in the terminal because CTRL+C and CTRL+V have special meanings on the Linux command line.)

---

### Post by JackC64 on 2010-12-29
> **JackC64 said:**
> how do i enter that in? i know in terminal but im a linux newbie, i recognize  some stuff cuz i know windows command prompt but i dont know how to enter large amounts of code in terminal...can you help me out?
well it didnt work, do you want the output? i am now almost sure i just need a driver and ive downloaded a driver off of intellinuxwireless.org, can you tell me how i could install that? its tgz.gz format.

also ive sent an email to dell...

---

### Post by PatchesTheCaveman on 2010-12-29
cipherboy_loc already explained how to install it, but there might be an easier way to do all those commands.

Go to Applications > Accessories > Text Editor on your top panel.  Copy and paste the following into the text editor:
```
#!/bin/bash
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-6050-ucode-41.28.5.1.tgz
tar -xf ./iwlwifi-*.tgz


cd *wifi*
sudo cp iwlwifi-6050-4.ucode /lib/firmware
sudo chmod 644 /lib/firmware/iwlwifi*
sudo chown root:root /lib/firmware/iwlwifi*
sudo rmmod -f iwlagn
sudo modprobe iwlagn


sudo apt-get -y install linux-backports-moudules-wireless-lucid-generic linux-backports-modules-wireless-maverick-generic
sudo reboot
```

Save it in a file called wififix in your Home Folder.  Then go to Applications > Accessories > Terminal in your top panel and just type the following:
```
bash wififix
```

That will install the driver and restart your computer to activate it all by itself.  It will ask for your password once.

---

### Post by JackC64 on 2010-12-30
it rebooted afterward and i got a white line through the wifi thing's exclamation point but i dont think that had anything to do with it. so it didnt work... heres a screenie of the whole problem.
[IMG]http://img141.imageshack.us/img141/7977/screenshot1kc.png[/IMG]
Is there a way to do it with the driver i already downloaded? or not through terminal?

---

### Post by JackC64 on 2010-12-31
guys?

---

