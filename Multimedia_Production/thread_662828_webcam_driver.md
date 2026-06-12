---
title: "webcam driver"
date: 2008-01-09
forum: Multimedia Production
---

### Post by kasrawiz on 2008-01-09
Hi can any tell me where to get my webcam driver please my cam Model is CD10P4  here is the web site [http://www.made-in-china.com/showroom/winait/product-detailEDnJGWTOTxvi/China-Mini-Pen-Tpye-100k-Pixels-Digital-Camera-CD10P4-.html](http://www.made-in-china.com/showroom/winait/product-detailEDnJGWTOTxvi/China-Mini-Pen-Tpye-100k-Pixels-Digital-Camera-CD10P4-.html)
thank you in advance :D

---

### Post by linuxwizard on 2008-01-09
in terminal > type > lsusb > post results

---

### Post by sinu on 2008-01-10
i can only use my webcam only when i turn on amsn ... but when i click camaroma it says that my webcam driver is not installed ... one more thing ... my inbuilt microphone also cannt be used... i jst switched from windows to ubuntu.. so i am a bit unfriendly with it... anyone gotta sollution for me?? the model number of my laptop is hp pavilion dv6000

---

### Post by dabl on 2008-01-10
They carefully avoided naming the IC, didn't they?  You need to know it to check whether the gspca driver might work, here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

Without knowing more, if the existing USB drivers won't handle it, you're probably done.

On the microphone issue -- that's an entirely different problem.  I assume it is built in to your HP.  I would search this forum for sound issues with that HP model -- probably you can tweak the ALSA mixer and enable the microphone input channel -- it may just be muted or something like that.

---

### Post by kasrawiz on 2008-01-11
Oh thank you for your reply i typed 
lsusb :
and here are the results   > Bus 001 Device 003: ID 0979:0224 Jeilin Technology Corp., Ltd
Bus 001 Device 001: Id 0000:0000

thank you i hope i will get my drive :(

---

### Post by Anthony Bagnall on 2008-01-11
OK I used Xandros some years ago and had a bash at Fedora but they were still in infancy and for all the wrong reasons stuck to something I hated (Windoze) I have resantly had a spate of virul attacks so decided I'd had enough and have dual booted this machine with Gutsy.  I am impressed.  It has been a bit of work but I managed to get Skype Beta working (with the video function) and Avant Antivirus (to try to kill the bugs on my windows partition) and it all seems fine.  I have everything I need and am just about ready to give Gates the flick.  I only have 2 problems to solve.
1/ Webcam I have 3 different devices I could choose from a Creative Vista, A V-Gear Vx6 and a MD tech CAM-EE. I need 1 of these devices to work with Skype.  All my research has been to no avail and I am probably more confused now than when i started.  I go to terminal and tpe in isusb and get command not found......
2/ My printer / scanner an Epson cx5500 (I also have a cx4700 and can interchange)
Please where do I start, I don't think I am a complete zoob I have been playing around withthese things since MS DOS 3 and have an Associate Diploma in business computing so...... HELP[-o<
Thanks in advance Tony

---

### Post by linuxwizard on 2008-01-11
open terminal and type in > lsusb

[http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx](http://connect.creativelabs.com/opensource/Lists/Webcam%20Support/AllItems.aspx)

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

[http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm)

---

### Post by kasrawiz on 2008-01-12
hi linuxwizard

i've already posted my lsusb can you reply me please????

here is the result again >
Bus 001 Device 003: ID 0979:0224 Jeilin Technology Corp., Ltd
Bus 001 Device 001: Id 0000:0000

---

### Post by linuxwizard on 2008-01-12
kasrawiz
I didn't forget about you just trying to find something on your webcam with no luck. Have you tried Ekiga or Camorama to see if they detect your webcam ? Or you might try EasyCam see if it will find a driver. 

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by kasrawiz on 2008-01-13
Oh thank you so much i'll try that and tell you thank  you somuch once again

---

