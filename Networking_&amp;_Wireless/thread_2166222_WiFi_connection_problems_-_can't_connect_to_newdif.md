---
title: "WiFi connection problems - can't connect to new/different WiFi"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by Mvrius on 2013-08-08
Hi, 

As mentioned in the title I'm having trouble connecting to my WiFi. I'm using ubuntu 12.04 (32-bit).
At my mum's house (parents are divorced) my WiFi works just fine, but recently I've been taking my laptop to my dad's and it fails to connect. The WiFi is available, the password and security settings are correct but it doesn't connect, instead it keeps asking me to authenticate by entering the password over and over.

P.S. I'm a bit of a noob when it comes to ubuntu so I'll be happy to post any info you need

---

### Post by wildmanne39 on 2013-08-08
Hi, copy and paste this command in the terminal (ctrl+alt+t) please when you are at your Dads:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Mvrius on 2013-08-08
Thank you for your quick reply. Here's the file.
[ATTACH]245184[/ATTACH]

---

### Post by wildmanne39 on 2013-08-08
Please do:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Is koeien-boven the network you want to connect too? 

It shows the router on channel 13, I am not sure that 13 is in your wireless devices range it is usually best to use 1 or 11.

You can check with:
```
iwlist chan
```
Thanks

---

### Post by ghayoor on 2013-08-11
! have the same problem and my text file is /home/ghayoor/wireless-info.txt what to do

---

### Post by ghayoor on 2013-08-11
how do i paste the file here

---

### Post by ghayoor on 2013-08-11
here is the file now what to do

---

### Post by varunendra on 2013-08-11
Which one is/are your access point(s) ? Some of the scanned ones are using WPA/WPA2 mixed mode encryption in the router. If yours is one of these, change the encryption to pure WPA2-PSK only with AES encryption, not TKIP.

Apart from that, you may try exactly the same thing that Wild Man suggested in post #4, since you are using the same driver (ath5k).

---

### Post by wildmanne39 on 2013-08-11
ghayoor are you are roommate of the OP? because you are trying to connect to the same networks he is.

I suggest you try what I stated in post 4.

varunendra is good and wireless issues so I am sure one of us can get you going, I am in and out today I have a kitten I just took to the animal hospital so my day is pretty full.

---

