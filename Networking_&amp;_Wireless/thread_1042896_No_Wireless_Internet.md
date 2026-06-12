---
title: "No Wireless Internet"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by happydog500 on 2009-01-18
I have a laptop (HP ze5200). I have been using Windows 7, with no sound. Thinking I don't want to use my laptop without sound for months, I'm looking to change my OS.

Been looking at Kubuntu, but, as you all know, even some of the best Computer Guru's can't get Linux to work. 

 Windows XP, works without any problem. When I load Windows 7, Wireless works without any problem. I tried the Live CD of Kubuntu (I prefer KDE over Gnome), and, as usual, It doesn't work. 
 No internet connection. 

 I looked all over the internet on forums, all I find is people who's wireless internet doesn't work. No answers.  

 I would like to install Linux on my laptop. If Windows 7 without sound isn't bad enough, my other option is Linux without a internet connection. 
 What can I do? How do I get wireless internet to work? 
 Thank you,
 Chris.

---

### Post by Whizam on 2009-01-18
Hey Chris,

There's lots of people on this forum that are able to get Linux to work :-).

I get your frustration, but in order to help you more information is required.

When you start up the Live CD can you run the following commands in Konsole and paste the output into this thread?

```
dmesg
lspci
sudo ifconfig -a
sudo iwconfig
uname -a
```

---

### Post by superprash2003 on 2009-01-18
also output of lshw -C network

---

### Post by happydog500 on 2009-01-18
OK, there is more to the story. My laptop model is known to have a week wifi signal, which I experenced.
 I put in a Cardbus, which has worked very good. I think that's why I may be having problems?

 I've used Red Hat 9, Mepis, SuSE 10.2, Mandrake, Debian, Puppy, and a few others. It's been a year and a half since I really used Linux for more then an hour or so. I must say I was surprised at Kubuntu. The look and feel seemed very, very nice! Very nice. Nothing really surprises me anymore, but this did.  

 I wasn't used to my laptop being so responsive. 

 I would like to use this, I will get the info and post back. 
 
 Thank you for responding,
 Chris.

---

### Post by happydog500 on 2009-01-18
Boy, I sure hope this boots up quicker from the HD then the live CD. 

 I can't cut and paste, my laptop isn't on the internet yet. I'm on my desktop, with the laptop next to me. 

 I did the dmesg command and got to much to type here. I tried to cut and paste, put it on my thumb drive and paste it here, but guess what? It doesn't work. 

 The lspci command I do see cardbus listed. 

Chris.

---

### Post by happydog500 on 2009-01-18
sudo iwconfig I see "no wireless extensions" several times. 
uname -a I get 2.6.27-generic #1 SMP.....

---

### Post by happydog500 on 2009-01-18
An icon apeared in the sistray. I right clicked my connection and got three wireless connections (Windows sees 6). My wireless signal is not there. No choise to select my connection. 

 I clicked on the cafe down the street connection, I thought it was connected, but still no. 

 Now the icon is gone. 

 Chris.

---

### Post by happydog500 on 2009-01-18
OK, come on, don't leave me hanging! Any more ideas? Chris.

---

### Post by happydog500 on 2009-01-23
OK, I get it. 
 I went to a business expo, kind of like a home show for business. 
 
Several tech company's where there. I went to each one and asked how to get internet working in Linux. 

 What I learned was, Linux only works on a very narrow list of hardware. When it doesn't work, you can try and fix it, but lots of times there is nothing you can do, it will never work.  

 I realize that's why nobody answers, there is no answer. It won't work.  

 Every couple years, I go to Linux to see what's going on, if it's ready for prime time. I guess I hit a Linux Dead End. No internet, no battery. 

 Thanks for trying,
 Chris.

---

