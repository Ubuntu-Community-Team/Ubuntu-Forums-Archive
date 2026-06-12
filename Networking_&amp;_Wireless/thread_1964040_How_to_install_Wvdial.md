---
title: "How to install Wvdial ?"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by tusharkoshti on 2012-04-23
I want to install wvdial for my CDMA2000 HSIA Modem. Can anybody tell me the steps ?
Thanx in advance.

---

### Post by chili555 on 2012-04-23
It is in the Ubuntu repositories; so, with an internet connection, open a terminal and do:```
sudo apt-get install wvdial
```

---

### Post by tusharkoshti on 2012-04-23
Sorry I forgot to tell....I have just installed Ubuntu 11.10. And I don't have internet connection. 
I know something regarding this like ..... 
1st we have to install some packages ...but i m not gettting that packages. 
So plz help me in this case.

---

### Post by codemaniac on 2012-04-23
Wvdial is a old school art .You can try Ubuntu's Mobile broadband connection creation wizard .
[http://daksh21ubuntu.blogspot.in/2012/02/how-to-establish-mobile-broadband.html](http://daksh21ubuntu.blogspot.in/2012/02/how-to-establish-mobile-broadband.html)

or Sakis3G .
[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

### Post by codemaniac on 2012-04-23
> **tusharkoshti said:**
> Sorry I forgot to tell....I have just installed Ubuntu 11.10. And I don't have internet connection. 
I know something regarding this like ..... 
1st we have to install some packages ...but i m not gettting that packages. 
So plz help me in this case.

So you have just got your new shiny Ubuntu 11.10 up and running but without internet connectivity !!
Please plug in your device and floow the new Mobile broadband connection creation wizard , steps are provided in the link of my earler post ..

---

### Post by chili555 on 2012-04-23
I was afraid of that. You can go here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Be sure to select Oneiric, which is 11.10, search for wvdial. Be careful of your architecture, either 32- or 64-bit. Please see the red dots that indicate that wvdial is dependent on several other packages; for instance, debconf. See if the package is already installed on your system with:```
sudo dpkg -s debconf
```'s' is for status. If it is installed, you'll see this:> Package: debconf
Status: install ok installed
<snip>Any dependencies that are not installed, you must also get as above. Drag and drop them from a USB key or similar to your desktop. Install:```
sudo dpkg -i wvdial*.deb
sudo dpkg -i <some_other_dependencies>*.deb
```Post back if you get stuck.

---

### Post by tusharkoshti on 2012-04-26
@ Codemaniac 

I tried but all was in vain. I got these options.

home n/w 
New Mobile Broadband (CDMA) connection 
Enable Mobile Broadband
VPN connection

( 1st was disabled)

---

### Post by tusharkoshti on 2012-04-26
@chili555 

Sorry but I couldn't understand u.

---

### Post by chili555 on 2012-04-26
> **tusharkoshti said:**
> @chili555 

Sorry but I couldn't understand u.What part do you not understand?

---

### Post by tusharkoshti on 2012-04-26
@chili555

I did what u said for the packages, ( I got that for wvdial we have to install following packages in the same order. ) 

libxplc0.3.13
libwvstreams4.4-base
libwvstreams4.4-extras
libuniconf4.4
wvdial_1.60.1+nmu2_i386

but i got error. So I thought I couldn't get what u wanted to say. 

[ I couldn't show u o/p of the command bcoz when i m in ubuntu , i copy the o/p, in file , then switch to XP and use that o/p but in this Ubuntu's version (11.10) I can't see the o/p which i have copied when i was in Ubuntu , in XP. ( prior to this I used to see the o/p perfectly ) ] 

Can u tell me how to install these packages and how to solve my 2nd problem ? ( simply double click on packages is also not working (  Install tab is disabled )

---

### Post by codemaniac on 2012-04-26
> **tusharkoshti said:**
> @ Codemaniac 

I tried but all was in vain. I got these options.

home n/w 
New Mobile Broadband (CDMA) connection 
Enable Mobile Broadband
VPN connection

( 1st was disabled)

Under the tab "Mobile Broadband" , you should be having a add button to create a new connection .Sometimes when you plug in your USB modem it is auto detected and an wizard will let you create a new connection .

---

### Post by chili555 on 2012-04-26
It's hard to know how to solve the first problem if I can't see the error. I suggest you open the text editor gedit. Leave it open while you try to install the packages. Copy and paste from the terminal to gedit. Save the text as something like *error.txt*. Drag and drop the file to a USB key and open it in Windows and copy it here.

---

### Post by tusharkoshti on 2012-04-26
@[codemaniac]("http://ubuntuforums.org/member.php?u=997189") :

I have created new connection. For that i guess there 3-4 steps , u have to give ur service provider name  , plan etc..... 

After doing that , i m getting above o/p. 

I have ticked  connect automatically but still not connecting. ( user name and pass field remained blank )

---

### Post by tusharkoshti on 2012-04-26
[@ chili555 :]("http://ubuntuforums.org/member.php?u=35909")

Hi, 

I have copied ( in fact write all o/p in gedit and opened in Win,  through Notepad.  Right click of my mouse is not working, and I think shortcuts r not allowed for Terminal. But I guess before , I used to copy through Ctrl + c but now it is also not working. Is it a problem in my pc or in me don't know ? :mad: )

o/p is : 

$ sudo dpkg -s libxplc0.3.13_0.3.13-3ubuntu1_i386.deb
$ [sudo] password for tushar :
Package 'libxplc0.3.13_0.3.13-3ubuntu1' is not installed and no info is available.

Package 'i386.deb'is not installed and no info is available.

[]("http://ubuntuforums.org/member.php?u=35909")

---

### Post by codemaniac on 2012-04-27
> **tusharkoshti said:**
> @[codemaniac]("http://ubuntuforums.org/member.php?u=997189") :

I have created new connection. For that i guess there 3-4 steps , u have to give ur service provider name  , plan etc..... 

After doing that , i m getting above o/p. 

I have ticked  connect automatically but still not connecting. ( user name and pass field remained blank )

Mate , you can select your interner service provider from the list after selecting your region/country .
If your isp or their plan is not listed you need provide the attributes like APN address , dialing number manually which you will get from your operator .

---

### Post by chili555 on 2012-04-27
I believe codemaniac has you headed in the right direction. Please continue.

---

