---
title: "Help! I've killed X!"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by jiggling_john on 2007-04-24
I just tried installing the nvidia drivery with Envy and it has murdered my installation of ubuntu (7.04).

I can no longer start the x server. I've tried running envy from command prompt, doing a remove and reintsall but still no joy. The error i get is "failed to start the x server - it is likely that it is not set up correctly"

How can I fix this without reinstalling ubuntu and losing my setup?!

---

### Post by sisco311 on 2007-04-24
code:
```
sudo dpkg-reconfigure xserver-xorg
```
select the nv driver

---

### Post by dannyboy79 on 2007-04-24
calm down. everything is fixable.

try this and just accept the defaults, this will at least get you back to using vesa so you have your gui (x-server)

sudo dpkg-reconfigure xserver-xorg

then if you're still at the command line, then you would type

startx

---

### Post by jiggling_john on 2007-04-24
neither of the above work....

i get one of 2 erros. the first being "etc/init.d/kdm command not found"

or

unable to find a valid frame buffer device
screens found, but none have a usable configuration

what now?!

---

### Post by dannyboy79 on 2007-04-24
ok, so you're currently trying that within a command line verison of you feisty upgrade correct?? if not, than that's what you need to do, not frmo a livecd!

also, did you try 

sudo /etc/init.d/kdm start
and then the 
sudo dpkg-reconfigure xserver-xorg

also, what does the file within your home directory look like called .Xsession-errors. or /var/log/Xorg.log or something like, it may even be in a seperate folder within /var/log/

---

### Post by jiggling_john on 2007-04-24
I ran envy from the command prompt, did a manual install of the new legacy nvidia driver... this seemed to work, gnome booted up... so i tried a restart of the system and... broken X again... what's going on?!

---

### Post by dannyboy79 on 2007-04-24
it could be that you have a .Xauthority file hanging around or that X is reading the incorrect xorg.conf? did they move the location of where xorg.conf gets stored in feisty? did you try what I suggested?

---

### Post by jiggling_john on 2007-04-24
im abuot to try the things you suggested, bear with me...

---

### Post by jiggling_john on 2007-04-24
sudo /etc/init.d/kdm start gives me
"sudo : /etc/init.d/kdm: command not found"

The right nvidia drivers are now installed - they must be because gnome comes up when i installed them... its just after a reboot it wont work again..... how can I check its using the correct xorg.conf?

---

### Post by sisco311 on 2007-04-24
envy creates a backup of your xorg.conf file
```
ls /etc/X11/xorg.conf*
```
if you have a file called xorg.conf.backup or something similar :
```
sudo cp /etc/X11/**xorg.conf.backup** /etc/X11/xorg.conf
```
replace **xorg.conf.backup** with your backup file name
startx

---

### Post by jiggling_john on 2007-04-24
the xorg log says

"failed to initialise the nvidia kernel module!"

I tried copying the backup xorg.conf and i now get the error

fatal server error : no screens found.

Xauth: error in locking file /home/.../.Xauthority

any ideas?

---

### Post by slimdog360 on 2007-04-24
now retry the sudo dpkg-reconfigure ... thingy and it should work

---

### Post by jiggling_john on 2007-04-24
nope... get exactly the same error.... :(

---

### Post by jiggling_john on 2007-04-24
is there no way that i can just reinstall some packages so it goes back to a default setup or something?! I really dont want to lose my setup now! Maybe reinstallation is the only way?! is it possible to repair an installation of ubuntu with the live cd if I cant get this sorted?

---

### Post by dannyboy79 on 2007-04-24
relax, I know exactly what's wrong, this happened to me. you need to install

xserver-xorg-dev
(NOTE: it is something with dev in it and it's for your xserver. so if that name isn't it, do a 

sudo aptitude search *xserver*

and then just install that stuff. also, did you try to temporarily rename the .Xauthority file? ands or are the permissions correct for your home directory? sometimes if  a file can't be written to your home dir (.Xauthority) then this will prevent your xserver frmo starting.

I have also read this within this bug report ([https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/103118](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/103118))
Previously, I also had a problem on this computer where it couldn't find the nvidia kernel module. This problem is resolved now -- I believe that this was fixed somehow when I installed linux-restricted-modules-generic, even though I'm actually using the -386 kernel. Previously there was no nvidia.ko in /lib/modules/2.6.20-13-386/volatile/, now there is. (I don't really know the reason why.)



OR

Ok, it seems to work now...

two things I did, not sure which one fixed it:
1) installed both restricted modules, generic and 386.

2) added a line to /etc/X11/XvMCConfig, now it looks like this

Code:
libXvMC.so.1
libXvMCNVIDIA_dynamic.so.1One of the two seems to have fixed the problem, I'm guessing it's the second.

---

### Post by jiggling_john on 2007-04-24
did that, said it was already installed... did a reinstall... same problem with the lock file... tried copying then renaming the lock file, no luck... my permissions must be set ok, i'ev not touched them...

---

### Post by slimdog360 on 2007-04-24
try this ```
sudo nano /etc/X11/xorg.conf
```
then run down to the bit which says Section "Device", there should be a bit intented in that which says driver "nvidia", or maybe "nv". Change the bit in the quotes to "vesa".  Thn press ctrl+x, save the changes and then type startx into a terminal.

---

### Post by jiggling_john on 2007-04-24
well, i added that line into the XvMCConfig file, which got rid of the lockfile problem

now when i startx i get

fatal server error: no screens found
X10 : fatal io error 104

---

### Post by jiggling_john on 2007-04-24
> **slimdog360 said:**
> try this ```
sudo nano /etc/X11/xorg.conf
```
then run down to the bit which says Section "Device", there should be a bit intented in that which says driver "nvidia", or maybe "nv". Change the bit in the quotes to "vesa".  Thn press ctrl+x, save the changes and then type startx into a terminal.

doing this made gnome boot up...  now what shuold I do to make sure i can install the nvidia drivers without killing everything again?!

---

### Post by slimdog360 on 2007-04-24
Are you on fiesty? If so just go into the 'System' --> 'Administration' --> restricted drivers section and install that way.

If your on edgy or earlier, go into synatpic and search for 'nvidia' and install that way. If you do this you will have to enter a command (it says it in synaptic, I can't remember it off of heart). If the command fails just do what I said just before and with the xorg.conf file and change it from "vesa" to "nvidia".
Then of course ctrl+alt+backspace to restart X.

---

### Post by dannyboy79 on 2007-04-24
according to this here: [http://ubuntuforums.org/showthread.php?t=388378&page=2](http://ubuntuforums.org/showthread.php?t=388378&page=2)

the solution is just to not use Envy as I am not sure what's going on with why it isn't working. Per this guide: [http://ubuntuforums.org/showthread.php?t=336412&highlight=Hub](http://ubuntuforums.org/showthread.php?t=336412&highlight=Hub)

---

### Post by jiggling_john on 2007-04-24
thanks for all your help guys, at least i can boot gnome now...

but my problem is now even if i install the nvidia drivers using the restricted package manager, it kills X again... should i uninstall some packages using apt and reinstall them or something? I'm pretty sure my card gf6200 uses the modern-legacy nvidia driver.

what should i do now?

---

### Post by dannyboy79 on 2007-04-24
i use the 6200, and it doesn't use the legacy driver, it uses the latest and greatest. did you follow the link I provided? if that doesn't work, than apparently something in feisty is preventing that. just use the driver just prior to 9755.

---

### Post by slimdog360 on 2007-04-24
try this
```
sudo apt-get update && sudo apt-get install linux-image-2.6.20-15-386
```
then once its installed reboot, make sure this is the chosen kernal option at the grub screen, it should be by default though. Once ubuntu has loaded try installing the nvidia drivers again.

---

### Post by jiggling_john on 2007-04-24
im already running linux-image-2.6.20-15-386...

---

### Post by dannyboy79 on 2007-04-24
maybe you need the sources for that kernel image in order to compile the latest nvidia correctly?? have you tried installing the source files for that kernel, and then trying to manually compile the 9755 nvidia driver?

---

