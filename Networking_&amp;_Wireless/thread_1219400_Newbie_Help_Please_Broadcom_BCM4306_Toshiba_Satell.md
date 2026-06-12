---
title: "Newbie Help Please: Broadcom BCM4306/ Toshiba Satellite S1900-303 laptop/Ubuntu 8.10"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by Bloomie on 2009-07-21
Sorry to be thick but I have installed Ubuntu 8.10 but the wireless card isn't working AND I can't connect to internet by cable on this machine.
 
I have downloaded b43-fwcutter-009.tar.bz2 on to another laptop and copied it over to my Ubuntu where its on the desktop. I have also copied bcmwl5.sys on to my Ubuntu also on to the desktop. 
 
How do I install b43' AND how do I extract the fimware from bcmwl5 and add it to my lib/firmware folder?
 
Or am I just barking up the wrong tree and should be doing something completely different?
 
I have searched but being a non-techy I reall need step by step guidance.
 
Thanks for any and all help.

---

### Post by Metaljaz on 2009-07-21
Trying opening the Synaptic Package Manager and do a search for fwcutter. It should say b43-fwcutter. Mark for install and then apply.

If its not there try this from the terminal window:

sudo apt-get install b43-fwcutter

---

### Post by Bloomie on 2009-07-22
Thanks. I tried both. It wasn't in the Synaptic package, so I tried the sudo apt-get.
 
I got E: Couldn't find package b43-fwcutter 
 
:confused::confused::confused:

---

### Post by Metaljaz on 2009-07-22
Go to System>Administration>Synaptic Package Manager
Then click on the settings>repositories, then click
on the tab for third party software and make sure
all is checked. 

Then go to the terminal and type the following:
sudo apt-get update

then:
sudo apt-get b43-fwcutter

Should have had you do that first..

---

### Post by Bloomie on 2009-07-22
Making progress....
 
Synaptic Package Manager finds it. But trying to install it I get:
 
E: b43-fwcutter: subprocess post-installation script returned error exit 
status 1

---

### Post by Bloomie on 2009-07-22
Would I be better off downloading Ubuntu 9.04 onto a CD and reinstalling from the new CD?

---

### Post by Metaljaz on 2009-07-22
You can do that if you want. Then follow the above steps to install. 
Then go to System>Administration>Hardware Drivers and make sure the broadcom b43 wireless driver is activated.
It will work. I am using the same driver on a Dell Inspiron and my wireless is fine.

---

