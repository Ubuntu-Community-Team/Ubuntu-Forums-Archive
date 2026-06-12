---
title: "Trouble with wireless card..... Internet speeds are extremely slow..."
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by KraizyAce on 2012-11-25
Hello all and thank you for taking the time to read this...

Just recently I installed Ubuntu 10.04 LTS on a spare HDD I had so I could have both Windows and Ubuntu on their own dedicated HDD... So far everything is working great, except my Internet speeds are really slow..... I've also had the same problem on a few copies of Windows XP, that is until I tried a copy known as "Black Edition"..... I don't know what it is but it works just fine... 

[[IMG]http://www.speedtest.net/result/2330002087.png[/IMG]]("http://www.speedtest.net")

I have an old 2004 Asus Motherboard that's using a Proprietary Wireless card... I have a couple of images of the box and the card itself..... If there's any more information I need to provide, please let me know...[IMG]http://picpaste.com/pics/38f84f234f55b6cc299fc586278ab507.1353824780.JPG[/IMG]

---

### Post by wildmanne39 on 2012-11-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by KraizyAce on 2012-11-26
Ok I did what you said.... Here's the files it created in my Home Folder...

---

### Post by wildmanne39 on 2012-11-26
Hi, wow I have never seen that device before it must be an old one.

Have you tried the driver that comes with 10.04? it is supported but it may not work well, but ndiswrapper is always the last option to use.

Also your signal strength is weak so that is effecting your connection speed.
Thanks

---

### Post by KraizyAce on 2012-11-26
I originally was using the default drivers, but then I decided to try the original drivers that came with the disc..... Still pretty much the same..... Not sure why I get better speeds in Windows XP Black Edition, but not in any other version of Windows or Ubuntu.... If there's nothing more that can be done, then I'll just have to get a better, compatible wireless card..... Thanks for the help! :KS

---

### Post by wildmanne39 on 2012-11-26
Hi, you can set your settings to match the screenshots that usually helps but that is all I know with this driver there are no parameters for it in 10.04.
Thanks

---

### Post by KraizyAce on 2012-11-30
Thanks for the help..... Used the settings you showed me, and also found the drivers that my other OS were using by default..... My connection speeds aren't super fast, but they're fast enough that I can actually stream media now..... Thanks for all the help! :P

---

### Post by wildmanne39 on 2012-11-30
Your welcome!

---

