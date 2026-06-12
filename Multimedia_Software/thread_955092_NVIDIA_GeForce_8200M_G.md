---
title: "NVIDIA GeForce 8200M G"
date: 2008-10-21
forum: Multimedia Software
---

### Post by emotionlovesyou on 2008-10-21
I'm trying to get my computer to recognize my graphics card.

I don't have immediate access to the web so Ubunto won't download the necessaries automatically. I can however use wireless internet at cafes through Windows which is still installed.

Anyway... I've tried downloading the drivers from the nvidia website, but the install program tells me i have to disable x server. That lead me though a number of rainbows with no pot of gold. One of those was using their xconf modifyer program-a-jig. I can't get it to run.

I also tried manually editing xorg.conf despite the danger. none of that worked either but I think I still had to install drivers before doing it anyway.

i guess that's it - ran out of options

case ur curious i have a compaq presario CQ50 Notebook PC

oh yea... I'll PayPal anyone who tells me how to get it working 10 bucks!!! Man of my word:)

---

### Post by Bakon Jarser on 2008-10-21
Hmmmmmm.......why can't you use Ubuntu in the internet cafe if they are on the same machine?

Anyways you will need nvidia-glx and all of it's dependencies.  

[http://packages.ubuntu.com/hardy/nvidia-glx](http://packages.ubuntu.com/hardy/nvidia-glx)

You can find all ubuntu packages here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

So I guess you'll need to make sure you have all the dependencies installed ( and the dependents dependencies) and then install nvidia-glx.  Sounds a lot harder then finding somewhere you can access the internet with Ubuntu.  Oh, I see that nvidia-settings is not a depency, it's a suggested package but you're really going to want that.  Makes changing settings a heck of a lot easier.

---

### Post by hdhrnova on 2008-10-21
> **emotionlovesyou said:**
> I'm trying to get my computer to recognize my graphics card.

I don't have immediate access to the web so Ubunto won't download the necessaries automatically. I can however use wireless internet at cafes through Windows which is still installed.

Anyway... I've tried downloading the drivers from the nvidia website, but the install program tells me i have to disable x server. That lead me though a number of rainbows with no pot of gold. One of those was using their xconf modifyer program-a-jig. I can't get it to run.

I also tried manually editing xorg.conf despite the danger. none of that worked either but I think I still had to install drivers before doing it anyway.

i guess that's it - ran out of options

case ur curious i have a compaq presario CQ50 Notebook PC

oh yea... I'll PayPal anyone who tells me how to get it working 10 bucks!!! Man of my word:) 

I have the same laptop as you.

download nvidia driver revision 177.80

sudo /etc/init.d/gdm stop

then run the nvidia installer

keep your 10 bucks. The economy sucks.. you will need it. ;-)

---

### Post by emotionlovesyou on 2008-10-23
Almost there.

I got much farther in the NVIDIA install program, but now instead of telling me to close X it tells me I need to install *libc* which I guess are c libraries.

I imagine if I just did a simple Ubuntu update it would install all that automatically. However, I have to download the files from the net then install them. (IE: apt-get install doesn't work 'cause I don't have access to the internet from within Ubuntu.)

So... I downloaded [libc6-dev_2.7-10ubuntu3_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-dev_2.7-10ubuntu3_i386.deb")
Two problems:
[LIST]
[*]I don't know if this is the correct package
[*]I don't know how to install it
[/LIST]

Thanks for your help; you guys are totally rad!

---

### Post by hdhrnova on 2008-10-23
> **emotionlovesyou said:**
> Almost there.

I got much farther in the NVIDIA install program, but now instead of telling me to close X it tells me I need to install *libc* which I guess are c libraries.

I imagine if I just did a simple Ubuntu update it would install all that automatically. However, I have to download the files from the net then install them. (IE: apt-get install doesn't work 'cause I don't have access to the internet from within Ubuntu.)

So... I downloaded [libc6-dev_2.7-10ubuntu3_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-dev_2.7-10ubuntu3_i386.deb")
Two problems:
[LIST]
[*]I don't know if this is the correct package
[*]I don't know how to install it
[/LIST]

Thanks for your help; you guys are totally rad!

try

sudo apt-get install build-essential

or just hang tight for another week and install 8.10 when it is released.
I will let you know if it works on  our laptop, when it is final, if you like.

right now it involves lots of manual tweaks.

---

### Post by Bakon Jarser on 2008-10-23
To install .deb packages just double click them and it will guide you through the install.  It's easy.  I'm not sure the package you linked is the correct one.  I think you need the non-dev one, although I have both installed.

[http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb)

---

### Post by emotionlovesyou on 2008-10-24
> **Bakon Jarser said:**
> To install .deb packages just double click them and it will guide you through the install.  It's easy.  I'm not sure the package you linked is the correct one.  I think you need the non-dev one, although I have both installed.

[http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu3_i386.deb)

Why oh why did I think it would be anymore complicated. Sometimes you just have to hang back and realize how easy Ubuntu is! :)

---

### Post by emotionlovesyou on 2008-10-24
Okay so I installed everything perfectly and I got a nice crisp 1280x800 resolution. It was beautiful but only for a second. The beauty is gone when I reboot into a nasty squarish 800x600 res.

Let me explain what I did to get it working then hopefully someone will explain how to *keep* it working.

First I disabled the restricted nVidia drivers by going to System >> Administration >> Restricted Drivers

Secondly I installed the things required by the nVidia driver installer. IE: [libc6-dev_2.7-10ubuntu3_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-dev_2.7-10ubuntu3_i386.deb") and it's dependency packages. I can't remember what exactly the latter was.

Then I rolled up my sleeves...

I logged out, changed the session to failsafe text [...somethin' or another], then typed...

```
sudo /etc/init.d/gdm stop
```

...and entered my password.

Next I pressed Ctrl+Alt+F1 and logged in.

Then after navigating to the appropriate folder I installed the nVidia drivers by entering...

```
sudo sh /NVIDIA-Linux blah blah blah
```

... and entered my password.

I followed the instructions; it compiled a kernel I guess and it updated my X configuration.

After the program closed I typed...

```
sudo /etc/init.d/restart
```

I saw the beautiful nVidia logo and Ubuntu started in a resolution that does its beauty justice. However as soon as I restarted, Ubuntu was put to shame. :( How dare they make a fool of Ubuntu!?

I did try re-enabling the driver using Restricted Drivers before rebooting but to no avail.

I may not have explained it accurately but them's the basics. Ideas + suggestions appreciated.

---

### Post by Bakon Jarser on 2008-10-24
Okay, I'm only half awake so I may have misread your post.  From what I read it sounds like you have the driver installed correctly, it just doesn't save your settings when you reboot.  Do you have the nvidia-settings package installed?  Easy way to find out, go to terminal and type

```
sudo nvidia-settings
```

This will bring up the settings manager where you can set your resolution.  when you have everything the way you want it click the save to x button and then it should remember your settings when you reboot.  I think I had a problem with it not saving my settings once when I didn't run nvidia-settings with sudo.

---

### Post by emotionlovesyou on 2008-10-24
Typing that brings up a pretty nifty little settings program. I poked around but couldn't save anything. So I closed it and rebooted. Still the unglamorous resolution :(

How do I save settings like you mentioned?

---

### Post by Bakon Jarser on 2008-10-24
Go to the 'x server display configuration' screen.  Choose the resolution you want.  Click 'apply'.  Click 'Save to X configuration file'.

---

### Post by emotionlovesyou on 2008-10-24
Did that. Perhaps it's not saving correctly.

---

### Post by fcmugen on 2008-11-11
i got the exact same problem with the Compaq CQ50. Ive tried using the command nvidia-xconfig but It still doesnt seem to save the X settings.

---

### Post by emotionlovesyou on 2008-11-14
I can't bare to work in 800x600!

... I'm ashamed to say I've given up. Bill has stole my soul and my computer. I've erased the Ubuntu partition and only use Windows now.

---

### Post by fcmugen on 2008-11-15
Ive upgrade to Intrepid and installed the Nvidia driver from their website got it installed now i got the wonderful resolution.

---

### Post by emotionlovesyou on 2008-11-15
I'm jealous. What is Intrepid?

---

### Post by ingwa on 2008-11-15
I believe intrepid is the new version of Ubuntu 8.10.

---

### Post by mckernan.kevin on 2008-11-29
Yep, Intrepid is referring to Intrepid Ibex, AKA Ubuntu 8.10.
For anyone working on this problem, try the instructions here with the current drivers:
[http://www.yaroman.com/2007/08/14/howto-install-nvidia-8600gt/]("http://www.yaroman.com/2007/08/14/howto-install-nvidia-8600gt/")
They key is to delete everything in restricted drivers that comes with Ubuntu. 

I am going to purchase a CQ50 in the next couple of weeks.:) How is the performance?

---

