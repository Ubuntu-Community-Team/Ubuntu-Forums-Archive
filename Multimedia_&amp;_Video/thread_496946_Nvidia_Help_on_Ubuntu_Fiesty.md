---
title: "Nvidia Help on Ubuntu Fiesty"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by alexv305 on 2007-07-09
I enabled the restricted drivers manager on my ubuntu fiest and now it says i need to fix x-server and i get a text based login screen.

 How do i fix this or disable the nvidia driver??

plzz help

---

### Post by MightyGaz on 2007-07-09
that driver file is sentient and intent on driving us poor noobs mad! 

help to get you back to a graphic situation can be found in my ongoing quest for aid here - [http://ubuntuforums.org/showthread.php?t=496605](http://ubuntuforums.org/showthread.php?t=496605)

---

### Post by Waappu on 2007-07-09
> **alexv305 said:**
> I enabled the restricted drivers manager on my ubuntu fiest and now it says i need to fix x-server and i get a text based login screen.

 How do i fix this or disable the nvidia driver??

plzz help

Login in and type```
sudo nano /etc/X11/xorg.conf
```
change line ```
Driver         "nvidia"
```to```
Driver         "nv"
```
press Ctrl+X to quit text editor and then Y to save file.
Then type ```
startx
```and you should have GUI.

If you want install nVidia drivers use Envy
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by MightyGaz on 2007-07-09
envy failed for me with thge error Failed to lock /var/cache/apt/archives/lock

---

### Post by Waappu on 2007-07-09
> **MightyGaz said:**
> envy failed for me with thge error Failed to lock /var/cache/apt/archives/lock

Hi

I use envy this way.
I start PC and in login screen press Alt+F2.
You should be now in text mode and then login.
Type```
envy -t
```select option 6 and after that option 1. Answer Y to questons.

I hope this works for you to

---

### Post by stchman on 2007-07-09
> **alexv305 said:**
> I enabled the restricted drivers manager on my ubuntu fiest and now it says i need to fix x-server and i get a text based login screen.

 How do i fix this or disable the nvidia driver??

plzz help

What kind of Nvidia card do you have.  The 8xxx cards have poor support under Ubuntu.

---

### Post by MightyGaz on 2007-07-09
> **Waappu said:**
> Hi

I use envy this way.
I start PC and in login screen press Alt+F2.
You should be now in text mode and then login.
Type```
envy -t
```select option 6 and after that option 1. Answer Y to questons.

I hope this works for you to

nope, went through the motions, seemed to be ok, but then couldnt start the x server and i had to reconfigure it to get back to desktop.  still no openGL or 3d acceleration.

---

### Post by Waappu on 2007-07-09
> **MightyGaz said:**
> nope, went through the motions, seemed to be ok, but then couldnt start the x server and i had to reconfigure it to get back to desktop.  still no openGL or 3d acceleration.

Hi

Did you get some error ? What is your machine specs ?

---

### Post by MightyGaz on 2007-07-09
> **Waappu said:**
> Hi

Did you get some error ? What is your machine specs ?

cant remeber the exact error, but it couldnt start the x server.  card is a geforce 4 MX 440 go.  in a dell inspiron 8200, 512MB RAM and a 1.7Ghz P4m

---

### Post by Waappu on 2007-07-09
> **MightyGaz said:**
> cant remeber the exact error, but it couldnt start the x server.  card is a geforce 4 MX 440 go.  in a dell inspiron 8200, 512MB RAM and a 1.7Ghz P4m

Hi

I don't know why Envy not work for you.

Here is long guide how to manually install nVidia drivers. I hope this helps
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

---

