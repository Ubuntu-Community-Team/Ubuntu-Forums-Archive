---
title: "How To: Easy Nvidia and Beryl..."
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by yurtboy on 2007-02-08
Two places I got the most help for this.
Before this I spent hours of trying...
Don't ask not sure why it took so long.
The end was two steps...
Go here and download and run his script
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Then follow the settings on 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)
for beryl and aiglx ONLY the part about the xorg lines and of course install beryl....

That was it for me I rebooted to play it safe, no mouse at first till I rebooted....

Well hope this helps someone.
Al

---

### Post by MetalMusicAddict on 2007-02-08
A "How-To" is not just linking to other guides.

---

### Post by yurtboy on 2007-02-08
Your right I will rename it...

---

### Post by nojobbob on 2007-02-08
I ran into some problem when I attempted to install Beryl.

pc@Big-Ubuntu:~$ sudo apt-get install beryl emerald-themes
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: libberyldecoration0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
         Depends: beryl-manager but it is not going to be installed
  emerald-themes: Depends: emerald (>= 0.1) but it is not going to be installed
E: Broken packages

I don't understand why the dependencies won't install also.

It seems to become an even bigger problem when I take, say the emerald package and install that seperate, then I get an entire new list of dependencies, that  "not going to be installed"

I don't quite understand what the meaning is or how to go about fixing so I can install Beryl.

TIA

---

### Post by yurtboy on 2007-02-09
did you follow the directions in the Unofficial Guide to adding repositories to your /etc/apt/sources.list?

---

