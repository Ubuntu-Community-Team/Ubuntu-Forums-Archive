---
title: "Linux Virgin finally loses his virginity!"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by RetroFreud on 2007-12-24
But....

Let's just say my experience is ... well, not so sure!

Installation process was pretty easy although I kept referring to this site for guide using my primary PC.

I like the design of GUI although I need to get used to it. Remind me of good old Amiga 500 GUI.

Configured Firefox to my usual setup. Easiliy done!

My uncertainty/reservation of Ubuntu revolves around setting up the graphics card driver (nvidia geforce 8600 GT).  I downloaded the driver from nvidia site after trolling this site for information. Apparently i need to use terminal to install this driver. 

So I decided that I am going to give it a rest for tonight (australian time). Tomorrow I will try to install the driver, then download and install WINE, and then download Team Fortress 2 overnight. I am hoping that I can play by the end of this week!

This is only an initial impression but I keep thinking why do I (user) have to research sites like this to set up a graphics card? I mean I am finding the process bit daunting.

Don't get me wrong, I am not criticising Ubuntu.  Just that, I am getting this lingering feeling that I might be NOT suited to it...

---

### Post by popch on 2007-12-24
> **RetroFreud said:**
> This is only an initial impression but I keep thinking why do I (user) have to research sites like this to set up a graphics card? I mean I am finding the process bit daunting..

Welcome to the club.

One of my laptops has an Nvidia card. After installation, Ubuntu very politely popped up a window telling me that there was a proprietary driver for my Nvidia card available, and if I wanted to install it. I clicked on yes, it installed, and that was it.

Try and locate an entry 'proprietary drivers' in the menu System/Administration (or some such, I do not know the exact wording in the English language version).

---

### Post by Rhubarb on 2007-12-24
This is the 2nd most easiest way to install the nvidia drivers (the most recent up to date version, not the one from the ubuntu repositories):
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Install envy, then run it from your applications menu and follow the prompts.

---

### Post by Teamgeist on 2007-12-24
You will need Envy to get your graphics going.
Only Envy will get you the newest NVIDIA driver for your 8600 GT.
Just download the .deb file from the link above and double-click to install.
You will find Envy in the "Applications"-Menu.

Have fun with Ubuntu.
I'm pretty positive that you'll love it. ;-)

---

### Post by mdsmedia on 2007-12-24
> **RetroFreud said:**
> But....

Let's just say my experience is ... well, not so sure!

Installation process was pretty easy although I kept referring to this site for guide using my primary PC.

I like the design of GUI although I need to get used to it. Remind me of good old Amiga 500 GUI.

Configured Firefox to my usual setup. Easiliy done!

My uncertainty/reservation of Ubuntu revolves around setting up the graphics card driver (nvidia geforce 8600 GT).  I downloaded the driver from nvidia site after trolling this site for information. Apparently i need to use terminal to install this driver. 

So I decided that I am going to give it a rest for tonight (australian time). Tomorrow I will try to install the driver, then download and install WINE, and then download Team Fortress 2 overnight. I am hoping that I can play by the end of this week!

This is only an initial impression but I keep thinking why do I (user) have to research sites like this to set up a graphics card? I mean I am finding the process bit daunting.

Don't get me wrong, I am not criticising Ubuntu.  Just that, I am getting this lingering feeling that I might be NOT suited to it...As a non-geek, please take my advice to keep an open mind and give it a chance. It's not always easy, but neither is Windows. The difference is we tend to allow Windows being slow, un-responsive, buggy, but when we try something different, if it doesn't work the way we want we dump it and go back to the thing we know...buggy, unresponsive, slow, Windows.

Keep an open mind and give it a fair go. You won't regret it.... well I haven't :)

---

### Post by RetroFreud on 2008-01-09
Thanks guys,

After my old monitor finally breathed its last breath, my affair with Linux was on hold until I got a replacement.

I followed your advice and downloaded Envy installer. I am stuck though, I get an error message, "dependency is not satisfiable: xserver-xorg-dev" 

What the hell am I supposed to do next?

---

### Post by frup on 2008-01-09
Opening the terminal and typing "sudo apt-get install xserver-xorg-dev" should get that dependancy solved.

---

### Post by st4rdr1ft3r on 2008-01-09
Why not just use the newest driver in gutsy? It works with a 8600gt? If the "Restricted Driver Manager" (that's what it's called in english) doesn't installed it then it's just ```
sudo apt-get install nvidia-glx-new
``` from the terminal

---

### Post by Sef on 2008-01-09
To download the latest restricted drivers:

System > Administration > Restricted Driver Management

First do, ```
sudo apt-get update
```

then do,

> 
Code:

sudo apt-get install nvidia-glx-new



---

### Post by RetroFreud on 2008-01-09
Thanks Guys,

I did goto Restricted Driver management and tried to enable it without success. So I will try the code see what happens.

---

### Post by Xbehave on 2008-01-09
remember you can always, select and middleclick / copy and paste commands. if you dont like the interface you may prefer kde (more windows like , although can be setup to be more mac like or more anything like)

---

### Post by RetroFreud on 2008-01-09
Hi, tried  'sudo apt-get install xserver-xorg-dev' and this error message occurred.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-dev

Any ideas? 

I will try the other code as suggested.

---

### Post by RetroFreud on 2008-01-09
After trying 'sudo apt-get install nvidia-glx-new' I get this message.

Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate

What could this possibly mean?

---

### Post by RetroFreud on 2008-01-09
Just one more question, should I 'reset and clear' before closing the terminal?

Sorry for the dumb question...

---

### Post by RetroFreud on 2008-01-09
Success! Of some sort anyway. I realised that I have to enable repos in software sources. So my graphic card driver is enabled.

But resolution is not right... arrrrgh

---

### Post by fatality_uk on 2008-01-09
Hi there.

Make sure that you have proprietry drivers checked in your software sources 
menu: system->Administration->Software sources
This should allow you to download the nVidia gfx drivers

---

### Post by Xbehave on 2008-01-09
im not sure what its called as im not on nvidia anymore but go into synaptic and search nvidia, theyre should be
1) the right driver
and
2) a settings program that should allow you to change nvidia settings

btw whenever people tell you to type apt-get in the command line its the same as installing through synaptic its just easier to copy a command.
ps i recommend using aptitude for installing stuff by command line as it deals with problems that apt-get installs

---

### Post by RetroFreud on 2008-01-09
Thanks to everyone! 

Now I am starting to get used to this, fixed my resolution although not perfect.

I will keep you posted about my love affair with Linux.

---

### Post by K.Mandla on 2008-01-09
Moved to Multimedia and Video.

---

### Post by Sammi on 2008-01-09
Seems like you just needed to add more repositories, so you were able to download the deb packages from them that you needed. But if your resolution is not perfect, I have three suggestions:

1. The Nvidia driver in the official Ubuntu repositories is fairly new, but  not completely up to date. You could try to update to the newest one. I do not recommend downloading it from the official Nvidia site. Instead you should use the Envy application, which is more reliable and far easier to use, than the official Nvidia install script.

2. Try using the nvidia-setting application. Just write "nvidia-settings" in a command line, and press enter.

3. Edit the xorg-conf file manually. This is kind of hardcore, but you will learns something. Here is a guide: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

