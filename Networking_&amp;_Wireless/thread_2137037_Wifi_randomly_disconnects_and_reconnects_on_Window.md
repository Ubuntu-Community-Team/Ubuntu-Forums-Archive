---
title: "Wifi randomly disconnects and reconnects on Windows 8 laptop with Ubuntu 12.10"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by rephaelhermon on 2013-04-19
I have a Lenovo Windows 8 laptop. I started get bored with Windows 8 and much more interested in Ubuntu again and now Ubuntu Touch. Anyways, long story short. I downloaded Ubuntu 12.10 on a DVD to try it out first then as I noticed how much more faster Ubuntu is on this laptop than Windows 8 itself, and all the open-sourced goodness, I installed Ubuntu 12.10 alongside- WIndows 8. I may installed Ubuntu 12.10 solely on here too if all goes well. Only issue is that my Wifi is randomly cutting off when the Wifi is still on in the house but I get the notification above saying it's disconnected etc, then reconnects. While typing this post, it's disconnected 5 times already. Please help me! Thanks!

---

### Post by wildmanne39 on 2013-04-19
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by rephaelhermon on 2013-04-21
Thanks so much! Here is the netinfo.txt attached. [ATTACH]241631[/ATTACH][ATTACH]241631[/ATTACH]

---

### Post by wildmanne39 on 2013-04-21
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Let us know if that helps.

Part of the informaton in that file is missing and couple of things did not look right.
Thanks

---

### Post by rephaelhermon on 2013-04-21
well I tried to run the first text into the terminal again and I got another netinfo file that was larger but it won't let me upload to attach it. And tried the 2nd text in the terminal and I got an error saying 

tee: invalid option --'r'
Try 'tee --help' for more info

---

### Post by wildmanne39 on 2013-04-21
Please just copy and paste the commands one line at a time into the terminal for accuracy, and just post the contents of the file here.
Thanks

---

### Post by wildmanne39 on 2013-04-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by rephaelhermon on 2013-04-21
This is a newbie question but how do you copy and paste into and from a terminal? I tried with the basic keyboard shortcuts but won't work. I understand the rest of what you requested regarding the code. Thanks!

---

### Post by wildmanne39 on 2013-04-21
Hi, highlight the text then right click copy, then click in the terminal and right click paste.
Thanks

---

### Post by rephaelhermon on 2013-04-28
Hey, sorry it's taken so long. It's just frustrating that everytime I try to get something done, I get disconnected. I even managed to shrink the partition with Windows 8 and reinstalled Ubuntu 13.04 into a much larger partition to maybe help. 

I just ran the 3 lines of code you gave me above into the Terminal and Wi-fi seems more stabel for the moment. It's been about 5 minutes and no disconnect, which is rare lately lol. I'll let you know if anything else transpires. If you want me to I can paste in code form, the netinfo.txt as well, which I ran before the 3 lines of code.

---

### Post by rephaelhermon on 2013-04-28
It's now been right under 2 hours and no sign of disconnection. This seems to have helped it, so far. Could you tell me what those 3 lines of code represented and did so I know for learning purposes? Thank you much!

---

### Post by rephaelhermon on 2013-04-28
I just now tried to downloaded an app from the Software Center and wifi disconnected for the first time since using the terminal but it reconnected right away.

---

### Post by rephaelhermon on 2013-04-28
It now won't hold a decent connection at all. I moved the router out from behind our TV and maybe now it will work better but I doubt that's the problem because our phones and xbox connect no problem. I'm even able to walk down the street nearby and have a good signal.

---

### Post by wildmanne39 on 2013-04-28
Hi, glad it helped!

The code disables hardware encryption and switches it to software encryption and in many cases improves the signal as well as stops disconnects.
Thanks

---

