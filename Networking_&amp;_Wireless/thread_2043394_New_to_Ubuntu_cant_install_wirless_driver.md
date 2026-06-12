---
title: "New to Ubuntu cant install wirless driver"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by Tsibert on 2012-08-16
I have a compaq 311c and am having trouble installing the drivers that are missing. what am i doing wrong.  when i try to activate i get the message ''sorry intallation of driver failed'' 


please help i really dont want to use windows on this machine.

cheers

---

### Post by albandy on 2012-08-16
Probably Ubuntu is trying to download the driver. Connect it throught network cable and try again.

---

### Post by Tsibert on 2012-08-16
I have a wired connection. but just cant seem to activate the requiered drivers just get an error message.

---

### Post by irv on 2012-08-16
> **Tsibert said:**
> I have a wired connection. but just cant seem to activate the requiered drivers just get an error message.

When you install Ubuntu there are two requirements. It tells you to be plugged into a power supply and be on the Internet.
When you installed Ubuntu did you have a Internet connection?
The reason I ask is because it sound like you might not of had this connection. If this is the case then it might be looking for the driver where you installed the OS from. (DVD or USB). If that is the case then it will not find it. You might have to start over and do it right.

---

### Post by Tsibert on 2012-08-16
I purchaced the laptop with some dodgy windows 7 copy on it and downloaded direct from the ubuntu website it automatically placed ubuntu in a partition. when using windows 7 wifi works fine.

---

### Post by irv on 2012-08-16
> **Tsibert said:**
> I purchaced the laptop with some dodgy windows 7 copy on it and downloaded direct from the ubuntu website it automatically placed ubuntu in a partition. when using windows 7 wifi works fine.

Are you running Wubi inside windows?

---

### Post by Jt00 on 2012-08-16
In the title you say wireless, but in your posts you say you have a wired connection.
If the problem is with the wireless driver, install ndisgtk (or ndiswrapper, they both do the same thing) and use that to add the windows driver. The computer should recognize your wireless device and you can now use it.
However, if this is just the wireless card in your computer, you may want to try reinstalling Ubuntu with an internet connection, as irv said.

---

### Post by Tsibert on 2012-08-16
I installed ubuntu from the ubuntu website i connected to the internet with the wifi working in windows 7. now i have ubuntu installed the wifi doesnt work and i am unable to install drivers. I am new to ubuntu and all things linux.  

thanks for all your responses and i apologise for my lack of knowledge and difficulty explaining my self

---

### Post by irv on 2012-08-16
> **Tsibert said:**
> I installed ubuntu from the ubuntu website i connected to the internet with the wifi working in windows 7. now i have ubuntu installed the wifi doesnt work and i am unable to install drivers. I am new to ubuntu and all things linux.  

thanks for all your responses and i apologise for my lack of knowledge and difficulty explaining my self

Did you download the iso file from the Ubuntu website then burn a DVD or USB?
Did you then start the DVD/USB from withing Windows and install Ubuntu (Wubi) within Window? or did you restart you computer and boot the DVD/USB and install from there?
When you say you installed from the Ubuntu website, you can not do this without downloading Ubuntu and then installing it in one of the two ways I said above.

---

### Post by Tsibert on 2012-08-16
i installed from the link  that said ''easy and safe for windows'' or somthing like that. it let me create a partiton and installed it directly.  it just downloaded and installed itself

---

### Post by irv on 2012-08-16
> **Tsibert said:**
> i installed from the link  that said ''easy and safe for windows'' or somthing like that. it let me create a partiton and installed it directly.  it just downloaded and installed itself

Do you have a link to the webpage so I can take a look at it?

---

### Post by Tsibert on 2012-08-16
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Its the ''windows installer'' on this page

---

### Post by chili555 on 2012-08-16
I hope I am not too blunt, but I am stunned that we have gone this far and *no-one has even asked what card it is!!!* Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by albandy on 2012-08-17
> **chili555 said:**
> I hope I am not too blunt, but I am stunned that we have gone this far and *no-one has even asked what card it is!!!* Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

You are right. XD

---

