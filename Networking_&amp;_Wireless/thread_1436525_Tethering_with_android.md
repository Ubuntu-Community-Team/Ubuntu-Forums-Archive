---
title: "Tethering with android?"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by bone2006 on 2010-03-22
I just purchased the mytouch android based phone and I've seen somethings on google, but was wondering if there's any easy tutorial out there?  I'd also prefer bluetooth if possible, because there's something about keeping the phone in your pocket, while using your laptop to work instead of having cables to it.

---

### Post by aysiu on 2010-03-22
If you want to tether MyTouch with Ubuntu (and not Windows), you need to root it:
[http://wiki.cyanogenmod.com/index.php/Main_Page](http://wiki.cyanogenmod.com/index.php/Main_Page)

If you want to tether to Windows or Mac, you can use PdaNet:
[http://www.junefabrics.com/android/index.php](http://www.junefabrics.com/android/index.php)

---

### Post by bone2006 on 2010-03-23
> **aysiu said:**
> If you want to tether MyTouch with Ubuntu (and not Windows), you need to root it:
[http://wiki.cyanogenmod.com/index.php/Main_Page](http://wiki.cyanogenmod.com/index.php/Main_Page)

If you want to tether to Windows or Mac, you can use PdaNet:
[http://www.junefabrics.com/android/index.php](http://www.junefabrics.com/android/index.php)

I saws that firmware before, but I am not sure I want to actually change the firmware.  I've seen other applications for tethering that would work on the current android firmware without changing it, but it required root as well.

I saw PDAnets, which costs money and doesn't work with Linux, so I was hoping something like that was out for Linux.

---

### Post by fatum on 2010-03-24
I have an Eris so I know what you are looking for. There is a program called proxoid in the market place that you need to download to the phone. Then you need to download the SDK for Android from Google. With both of those and a script or two on your computer (depending on which Ubuntu version you are running)and turning on USB debugging on your phone which is in Settings->Applications->Development you can create port forwarding through the phone to the computer.

If you then change the global setting in Network Proxy in Ubuntu you will be able to use all your programs in Ubuntu through the tether. I have not been able to get it working on 10.04 yet but it is still beta. I had it working with 9.04 and 9.10. 

Sorry I don't have links I will try and post them later once I can look them up again.

---

### Post by fatum on 2010-03-24
Was able to get to a place with WiFi and get my netbook out. The site that I used in the past is 

[http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Tether-an-Android-Phone-Using-Proxoid]("http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Tether-an-Android-Phone-Using-Proxoid")

I went through the steps again with my netbook running 10.04 beta I am now using my tether for posting this reply. I do not know if I was doing something wrong before or something got updated in the beta release.

Firefox worked with just changing my network proxy system settings but nothing else seems to work. Even when I change proxy in the application itself every application has said connection issues.

---

### Post by bone2006 on 2010-03-24
Ok I got it to work with proxid and thought I'd post what I've done.  I have it now, so I just type on in the terminal and it's on and off and it turns off.  The scripts below are not my own, but they were posted here [http://code.google.com/](http://code.google.com/), but the instructions on that site and almost anything I found didn't work, so I thought I'd post what I had to do.

Really happy as both http and https is working and it's as simply as typing on or off in my terminal to have it work once the program is running.

I just hope somebody can benefit from this post and thanks everybody for the help

****PHONE SETTINGS***
Install Proxoid from marketplace, then in the phone go into your settings, application, development and put a check on usb debugging.   

****UBUNTU SETTINGS***

open up a terminal and follow these commands (replace vi with your favorite text editor)

# sudo su -
# vi /etc/udev/rules.d/09-android.rules 

ADD line and save
 SUBSYSTEM=="usb", ATTRS{idVendor}=="0bb4", MODE="0666"

# chmod 755 /etc/udev/rules.d/09-android.rules 

# cd /usr/local/sbin
# wget [http://dl.google.com/android/android-sdk_r05-linux_86.tgz](http://dl.google.com/android/android-sdk_r05-linux_86.tgz)
# tar -zxvf android-sdk_r05-linux_86.tgz 
# cd android-sdk-linux_86/tools/
# ./adb kill-server
# ./adb start-server
# ./adb devices
# ./adb forward tcp:8080 tcp:8080

Now here's instructions on setting up, so everything goes through tethering


# cd
# mkdir .tethering
# vi ~/.tethering/on.sh

Past what's below into the on.sh file

*******************************
#! /bin/sh
# Routes network traffic to G1 and switches the GNOME proxy on

/usr/local/sbin/android-sdk-linux_86/tools/adb forward tcp:8080 tcp:8080

echo "Enabled forwarding."

# activate proxy
gconftool-2 -t string -s /system/proxy/mode "manual"
gconftool-2 -t bool -s /system/http_proxy/use_http_proxy true
# http settings
gconftool-2 -t string -s /system/http_proxy/host "localhost"
gconftool-2 -t int -s /system/http_proxy/port "8080"
# https settings
gconftool-2 -t string -s /system/proxy/secure_host "localhost"
gconftool-2 -t int -s /system/proxy/secure_port "8080"

echo "Enabled proxy."
*******************************

# vi ~/.tethering/off.sh

copy what's below into the off.sh file
****************************************

#! /bin/sh
# Switches the GNOME proxy off

gconftool-2 -t string -s /system/proxy/mode "none"
gconftool-2 -t bool -s /system/http_proxy/use_http_proxy false

echo "Disabled proxy."

*******************************

#sudo chmod 755 -R ~/.tethering
#sudo vi .bashrc

look where it says #alias and paste these two lines below:
alias on='~/.tethering/on.sh'
alias off='~/.tethering/off.sh'

restart your terminal and when your phone is plugged in just type on to start it and off to turn it off

---

### Post by fatum on 2010-03-24
only change that some might need to do is when starting the adb server instead of 

```

./adb start-server

```

they may need to do that with sudo so 

```

sudo ./adb start-server

```

You will know when you need to do this change if you get an error stating you do not have privileges. The privileges are for seeing the phone itself not starting the server. Easy way to see if you need this change is just to run

```

./adb devices 

```

with the phone plugged in to the computer. If output includes a string of letters and numbers then you are good. If output includes a string of question marks then you need to use sudo.

Also you may need to change the first line in the on.sh file to stat where you have the Android SDK if it was all ready installed on your system prior to trying this. That is if you did not move it to the location specified.

---

### Post by aysiu on 2010-03-24
> **fatum said:**
> Was able to get to a place with WiFi and get my netbook out. The site that I used in the past is 

[http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Tether-an-Android-Phone-Using-Proxoid]("http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Tether-an-Android-Phone-Using-Proxoid") Um, do whatever works for you, of course, but just so you know, those instructions look way more complicated than the ones I followed to root my phone.

---

### Post by fatum on 2010-03-24
> **aysiu said:**
> Um, do whatever works for you, of course, but just so you know, those instructions look way more complicated than the ones I followed to root my phone.

As stated above in my first post to the thread I have a Droid Eris which at this time has not been rooted so that is not an option for me. That said with those instructions it took 2 minutes to get things up and running, and that is not exaggerating I already had the SDK and Proxoid installed.

---

### Post by aysiu on 2010-03-24
> **fatum said:**
> As stated above in my first post to the thread I have a Droid Eris which at this time has not been rooted so that is not an option for me. That said with those instructions it took 2 minutes to get things up and running, and that is not exaggerating I already had the SDK and Proxoid installed.
bone2006, the OP of this thread, has a MyTouch, which I also have.

---

### Post by fatum on 2010-03-24
> **aysiu said:**
> bone2006, the OP of this thread, has a MyTouch, which I also have.

My mistake, with a quote from me in the reply and your phrasing I thought that reply was meant for me.

---

### Post by aysiu on 2010-03-24
> **fatum said:**
> My mistake, with a quote from me in the reply and your phrasing I thought that reply was meant for me.
I treat each support thread as an attempt to help the first post-er (aka OP).

I didn't know you were asking for help with your Eris. If you are, I would suggest you post a new thread of your own so people can help you with it.

If you are, however, trying to help the OP with a MyTouch, keep in mind that it is easier to root a MyTouch than to use those complex instructions to get a tether.

---

### Post by fatum on 2010-03-24
> **aysiu said:**
> I treat each support thread as an attempt to help the first post-er (aka OP).

I didn't know you were asking for help with your Eris. If you are, I would suggest you post a new thread of your own so people can help you with it.

If you are, however, trying to help the OP with a MyTouch, keep in mind that it is easier to root a MyTouch than to use those complex instructions to get a tether.

You have a round about way of going about it then. 

The OP has already stated that he has gotten it to work and posted the instructions he used to do so. He also stated that he all ready looked into rooting his phone and stated he was unsure of changing firmware. 

I in no way asked a question when stating that I had an Eris and led the OP to the relevant information to get what he asked for, except for the preferred use of bluetooth. I only stated the phone I had to show I too am running Android.  

Also the ease of doing something is in the opinion of the user.

---

### Post by bone2006 on 2010-03-25
> **fatum said:**
> only change that some might need to do is when starting the adb server instead of 

```

./adb start-server

```

they may need to do that with sudo so 

```

sudo ./adb start-server

```

You will know when you need to do this change if you get an error stating you do not have privileges. The privileges are for seeing the phone itself not starting the server. Easy way to see if you need this change is just to run

```

./adb devices 

```

with the phone plugged in to the computer. If output includes a string of letters and numbers then you are good. If output includes a string of question marks then you need to use sudo.

Also you may need to change the first line in the on.sh file to stat where you have the Android SDK if it was all ready installed on your system prior to trying this. That is if you did not move it to the location specified.

I'm not sure if you noticed, but I have sudo su - command, so you don't need sudo where you mentioned.  You will be logged in as sudo/root and when your done, you just need to type exit.

---

### Post by bone2006 on 2010-03-25
> **aysiu said:**
> Um, do whatever works for you, of course, but just so you know, those instructions look way more complicated than the ones I followed to root my phone.

Your lucky, because my mytouch is the newer one with the 35mm phone jack and the developers of the firmware themselves posted on March 10th that they would not recommend rooting this phone as of yet, because of issues.

---

### Post by bone2006 on 2010-03-25
> **aysiu said:**
> bone2006, the OP of this thread, has a MyTouch, which I also have.

I don't think we have the same phone, do you have the older one?  Even the website you posted advises to be careful doing the mytouch with the 35mm phone jack.  If you go on their forum, they are advising to wait and not root this phone.

[http://wiki.cyanogenmod.com/index.php/Full_Update_Guide_-_G1/Dream/Magic32A_Firmware_to_CyanogenMod](http://wiki.cyanogenmod.com/index.php/Full_Update_Guide_-_G1/Dream/Magic32A_Firmware_to_CyanogenMod)

---

### Post by aysiu on 2010-03-25
> **bone2006 said:**
> I don't think we have the same phone, do you have the older one?  Even the website you posted advises to be careful doing the mytouch with the 35mm phone jack.  If you go on their forum, they are advising to wait and not root this phone.

[http://wiki.cyanogenmod.com/index.php/Full_Update_Guide_-_G1/Dream/Magic32A_Firmware_to_CyanogenMod](http://wiki.cyanogenmod.com/index.php/Full_Update_Guide_-_G1/Dream/Magic32A_Firmware_to_CyanogenMod)
Oh, my bad. Sorry!

Yeah, I do have the older one. I didn't know there was a difference.

---

### Post by fatum on 2010-03-26
I did not notice that at the beginning. My brain must have just skipped right over it, possibly because I use su. I prefer to use sudo when needed.

---

### Post by rhythmiccycle on 2010-07-23
tether android phone (mytouch) with laptop, using proxoid. I got it to work!!

no need to root (and void your warranty) 

check out this thread for the step by step

[http://ubuntuforums.org/showthread.php?t=1441466](http://ubuntuforums.org/showthread.php?t=1441466)

---

