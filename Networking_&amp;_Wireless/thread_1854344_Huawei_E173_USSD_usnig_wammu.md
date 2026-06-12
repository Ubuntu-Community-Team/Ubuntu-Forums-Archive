---
title: "Huawei E173 USSD usnig wammu"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by preetamk on 2011-10-04
hi,
I have been trying to send ussd through wammu. There are no options available for that in the wammu but there is one available in gammu

I tried gammu.

These are the steps I tried

1. install gammu 
sudo apt-get install gammu
2. configured .gammurc in home folder to read the following
[gammu]
port=/dev/ttyUSB2
connection=at115200
name=huawei e173
model=

(This was added by wammu when I configured to use for sms)

3. Then tried gammu with every option I had in 'man gammu'. like
gammu --identity
gammu --detect
 everytime I get the response bad option.

I don't know where I am going wrong. please help me.

I tried minicom as mentioned in some other post. It did not work. So I tried gammu 

Also there is a post on an unstable program that I do not want to risk for some importatnt files I have. Please help me with gammu

---

### Post by preetamk on 2011-10-04
I found this software
[http://utekubuntu.wordpress.com/2011/04/14/ixconn-mdma-on-linux-ubuntu/](http://utekubuntu.wordpress.com/2011/04/14/ixconn-mdma-on-linux-ubuntu/)

atleast can take care of the ussd

but still would love to do ussd with gammu...

---

