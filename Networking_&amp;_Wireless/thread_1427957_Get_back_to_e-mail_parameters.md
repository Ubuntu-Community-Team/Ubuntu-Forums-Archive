---
title: "Get back to e-mail parameters"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by silversurf on 2010-03-12
As a completely new user of Ubuntu 9.10 Karmic Koala, I will no doubt be asking some pretty basic questions, first. in Evolution Mail I am unable to get in or out  it merely shows waiting, as Firefox is workingI am connected to the net (hard-wired to broadband wireless router), suspect I put dud info. in the initial set-up, but cannot find how to edit or re-enter these parameters.
Secondly on looking for AVG anti-virus progs on the internet, I find that there are several prefixes which one is for this version?

---

### Post by chili555 on 2010-03-12
Edit -> Preferences. Highlight your account and a window will open with several tabs with settings for you to verify or change.> Secondly on looking for AVG anti-virus progs on the internet, I find that there are several prefixes which one is for this version?None. 99.9% or so of viruses are written for Windows. You also have Linux's inherent protection of root vs. user; that is, in order to install software the root password is needed. If you are opening dodgy emails and surfing the far end of the internet, you aren't going to willingly hand out your root password, are you?

There is an anti-virus package for Linux called clamav. You can find it in System -> Administration -> Synaptic.

I have been a Linux user since 2001 and I currently run four Ubuntu computers without anti-virus software. I have never had or even heard of a virus for Ubuntu. Your exact mileage may, of course, vary.

---

### Post by Naggobot on 2010-03-12
And of course if you want to do something really really fishy then just switch to quest session and you should be pretty well covered for the unlikely event that you are able to find linux virus. 

After the guest session is log out the user account is swept clean. 

See 

[http://www.youtube.com/watch?v=XutuGwcQ96g](http://www.youtube.com/watch?v=XutuGwcQ96g)

on how to access the session and some info

---

### Post by silversurf on 2010-03-13
Many thanks chili555, I have sorted the e-mail after your directions.

---

### Post by silversurf on 2010-03-13
> **chili555 said:**
> Edit -> Preferences. Highlight your account and a window will open with several tabs with settings for you to verify or change.None. 99.9% or so of viruses are written for Windows. You also have Linux's inherent protection of root vs. user; that is, in order to install software the root password is needed. If you are opening dodgy emails and surfing the far end of the internet, you aren't going to willingly hand out your root password, are you?
 
There is an anti-virus package for Linux called clamav. You can find it in System -> Administration -> Synaptic.
 
I have been a Linux user since 2001 and I currently run four Ubuntu computers without anti-virus software. I have never had or even heard of a virus for Ubuntu. Your exact mileage may, of course, vary.
 
 The e-mail now works a treat, for my next question, I am running Linux dual boot with XP on the initial screen when logging on the screen shows linux system first then XP (i.e. Linux is the default) can it be arranged that XP be the default. Thanks for the previous.

---

### Post by howefield on 2010-03-13
The easy way would be to install startupmanager with Synaptic Package Manager (System > Administration > Synaptic Package Manager)

This will give you options to change what is booted by default.

The harder way would be to edit your boot loader files and the instructions would depend on whether you are using grub2 or it's previous version.

---

### Post by silversurf on 2010-03-14
> **howefield said:**
> The easy way would be to install startupmanager with Synaptic Package Manager (System > Administration > Synaptic Package Manager)
 
This will give you options to change what is booted by default.
 
The harder way would be to edit your boot loader files and the instructions would depend on whether you are using grub2 or it's previous version.
 
 
Many thanks, the Startup Manager one worked well.

---

