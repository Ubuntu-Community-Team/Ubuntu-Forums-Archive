---
title: "Wifi Issue"
date: 2012-11-22
forum: Networking &amp; Wireless
---

### Post by Mcover3 on 2012-11-22
Hi!

I recently downloaded Ubuntu 12.10 onto my acer laptop which was running on windows vista, when Ubuntu had finnished downloading I went to set up my wifi network however I was unable to find how to do it.

I went on the help page and followed the instructions, it said 
'Click the network menu bar in the  menu bar' and so on but in my menu bar there was no 'network menu' was there. I then found a solution on how to solve the problem and followed instructions. But none of these worked either and kept coming up with the same message 
'Network disconnected- you are now offline' 

So I looked for forums on the Internet and found this, also seeing the comment on how you fixed it. It may sound stupid but how did you fix it using the sudo ifconfig thing, so would you be able to explain how to do this I.e: go onto the terminal and type ___ in.

Thanks!

---

### Post by wildmanne39 on 2012-11-22
Moved to own thread!

---

### Post by wildmanne39 on 2012-11-22
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

