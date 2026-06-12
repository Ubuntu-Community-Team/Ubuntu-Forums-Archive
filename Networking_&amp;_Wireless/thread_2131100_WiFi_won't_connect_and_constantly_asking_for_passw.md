---
title: "WiFi won't connect and constantly asking for password"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by Lessthanzero on 2013-03-31
[FONT=arial]Hi, everyone! Recently, I've stumbled upon a problem: my laptop is in infinite loop of asking for wifi password. 
I've checked this thread [http://ubuntuforums.org/showthread.php?t=1898644]("http://ubuntuforums.org/showthread.php?t=1898644&page=4"), and changed iwl4956 to ipw2200 assuming it's the WiFi card driver (mine is **Intel 2200BG**). 
Nothing helped. It goes without saying, that I double-checked my password, and it's correct. WiFi works for other devices and for Windows XP on the same laptop. Strangely though, Ubuntu couldn't  connect to the same router when I set it for not asking password (**WPA2-PSK** to **No Security** mode). If anyone faced the same problem, please help. Cheers! [/FONT]

---

### Post by wildmanne39 on 2013-03-31
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by Lessthanzero on 2013-04-01
[ATTACH]240814[/ATTACH] Hi, here it is.

---

### Post by wildmanne39 on 2013-04-01
Hi, that is the script we need to see the textinfo file it created it will also be in the home folder.
Thanks

---

### Post by Lessthanzero on 2013-04-02
Yeah, sorry, messed up with an attachement [ATTACH]240877[/ATTACH]

---

### Post by CamPsych on 2013-04-02
Hi there, 

Check out the Known WiFi issues [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Known_Issues](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Known_Issues) I used the directions here and it sorted the same problem that I had.

[admin's note: Broadcom link may not help for an Intel interface]

---

### Post by wildmanne39 on 2013-04-02
Hi, your router is set to channel 0, please change to 1 or 11.
Thanks

---

### Post by johnmuir on 2013-05-13
[SOLVED]
This problem was driving me slightly mad. Installing the latest drivers etc. did not help. 

Then I finally found the solution: my WLAN router was using the same channel as my neighbour. This according to the googelatur causes interference (digital not analog) and is BAD. So I changed the channel for my WLAN (see your router configuration) and problem solved!

Further info: you can see which channels you and others are using by using a program such as Inssider - [http://www.metageek.net/products/inssider/](http://www.metageek.net/products/inssider/) - which works in Android, Windows or Linux up to 10.4 or WiFi Analyzer (Android) 
The channels are from 1 to 13 and channels 1, 6 and 11 are preferred due to less chance of overlap.

---

