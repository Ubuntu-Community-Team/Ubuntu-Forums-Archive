---
title: "32bit Wifi problems with Intel wireless/pro 4965 ag"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by Jrmurph3 on 2011-05-04
Hey everyone. I'm very new to this thread as well as Ubuntu.  I clean installed Ubuntu 32bit 11.04 today and I've been having problems with my wifi. I haven't tried to connect using a wired connection, but oddly I cannot connect to a hidden network with a WEP encryption though I can with an open, unprotected wireless connection.  The keys have been entered correctly and checked and checked and checked several times to verify.  Has anyone else run into this problem or can help?

---

### Post by Jrmurph3 on 2011-05-05
*bump*


Seriously? No one has an answer?

---

### Post by josephmills on 2011-05-05
welcome to the forum could you open your terminal and type in 
```
sudo apt-get update 
```
then 
```
sudo apt-get upgrade 
```
please press the y button when it asks you to. 
could we also see a 
```

iwlist auth 

```
thanks and once again welcome to ubuntu forums

---

### Post by Jrmurph3 on 2011-05-05
> **josephmills said:**
> welcome to the forum could you open your terminal and type in 
```
sudo apt-get update 
```then 
```
sudo apt-get upgrade 
```please press the y button when it asks you to. 
could we also see a 
```

iwlist auth 

```thanks and once again welcome to ubuntu forums


Ok, I really appreciate your help.  The get update command ran something but the get upgrade didn't ask me to hit y or really do much.
This was the outcome though:
john@john-HP-Pavilion-dv6700-Notebook-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Here's the iwlist auth:
john@john-HP-Pavilion-dv6700-Notebook-PC:~$ iwlist auth
lo        no authentication information.

eth0      no authentication information.

wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP

Again, I really do appreciate the help. I do plan on learning what I can and eventually contributing to the community myself. I have never touched Linux before until I decided I have time to do it now.
Thanks, John.

---

### Post by Jrmurph3 on 2011-05-05
I just noticed that the wlan0 Authentication capabilities does not show WEP.  I am using a WEP encrypted connection. I assum that could be a problem, correct?

---

### Post by josephmills on 2011-05-05
> **Jrmurph3 said:**
> I just noticed that the wlan0 Authentication capabilities does not show WEP.  I am using a WEP encrypted connection. I assum that could be a problem, correct?
could be switch it to the better wpa2 and try again I can crack a wep encryption in 25 min it takes me 4 to 5 hours with wpa/wpa2  and if you pick a password that is over 50 characters long then I cant crack it but I am a noob at this all. I am sure that it could be done but it is real hard

---

### Post by Jrmurph3 on 2011-05-05
> **josephmills said:**
> could be switch it to the better wpa2 and try again I can crack a wep encryption in 25 min it takes me 4 to 5 hours with wpa/wpa2  and if you pick a password that is over 50 characters long then I cant crack it but I am a noob at this all. I am sure that it could be done but it is real hard

It's my parent's set up and my mom refuses to listen to anything I have to say about anything so it isn't going to change. Any way to add WEP authentication to my wireless card? It does work just find using Windows.

---

