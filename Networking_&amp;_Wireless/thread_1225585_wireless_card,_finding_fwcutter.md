---
title: "wireless card, finding fwcutter?"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by jamle on 2009-07-28
hi, been having problems with my wireless card on my laptop finally getting there only im unable to find the fw-cutter tool i need to make use of the wireless driver ive copyed from the windows partition

guide i been tryin 3 use
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

ive tried all sorts of combinations an i cant get it to appear its not coming up when i serch in the package manager or try the terminal line
sudo apt-get install bcm43xx-fwcutter
just says E: Couldnt find package bcm43xx-fwcutter

i remember u need to select something in symnatic package settings but cant see what ive selected and unselected stuff and cant get the fwcutter to appear!

PLEASE HELP!

---

### Post by chili555 on 2009-07-28
Please try:```
sudo apt-get install b43-fwcutter
```

---

### Post by Ayuthia on 2009-07-28
If you have a working connection in Ubuntu, you will will need to run the update in Synaptic and then try to install b43-fwcutter.  Or you can do it from the Terminal:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
This should get your wireless up and running without the need of the Windows driver.

EDIT: I just noticed that chili555 beat me to the response.

---

### Post by jamle on 2009-07-28
as i put in my first post ive tried this and it didnt work i get this result
reading package lists. . . Done
building dependency tree
Reading state information. . . Done
E : Couldn't find package b43-fwcutter

---

### Post by jamle on 2009-07-28
ello? where every1 go lol, ive already tried what u guys suggested. ive not had wireless for over a week on my home laptop because of ubuntu, i hate having to use vista now lol, luckily my asus eee pc with ubuntu works perfectly (this is how im able to use internet and its not ideal!

---

### Post by jamle on 2009-07-29
bump for help! all i need is fwcutter to make use of my wireless drivers and im away! (in theory) please help!

---

### Post by kerry_s on 2009-07-29
are you plugged in connected to the internet? otherwise those commands will do no good.

---

### Post by jamle on 2009-07-29
no im not pluged in at all sorry forgot to say, also the laptop will connect all normal on my vista partitio as normal duno if that helps.

---

### Post by chili555 on 2009-07-29
Please go here on your Vista partition and download the .deb file: [http://packages.ubuntu.com/jaunty/i386/b43-fwcutter/download](http://packages.ubuntu.com/jaunty/i386/b43-fwcutter/download)

Move it over to Ubuntu on a USB drive and install it with:```
sudo dpkg -i b43-fw*
```

---

### Post by jamle on 2009-07-29
brilliant thanks 4 responce when i get in from work in hours time ill give it a bash

---

### Post by jamle on 2009-07-29
dam i really dont have the linux gods on my side! went to ur link saved one of the europe ones to usb, pasted onto my desktop in ubuntu, tried installing it and it wouldn't work got the error in terminal which was:

dpkg: error processing b43-fw* (--install):
cannot access archive: no such file or directory
Errors were encountered while processing:
   b43-fw*


does it matter which one of the europe ones u download on the list? i couldn't see anything that looked like uk or english or anything so picked [gr.archive.ubuntu.com/ubuntu]("http://gr.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-5_i386.deb")

not sure which one i should use adn if it makes any difference im in england

Thanks again Jay

---

### Post by chili555 on 2009-07-29
> pasted onto my desktopWhen you just open a terminal, you are in your /home/user directory. That's not the place you put the .deb file! Let's try:```
cd Desktop
sudo dpkg -i b43-fw*
```Let us know the outcome, please.> does it matter which one of the europe ones u download on the list? Not one bit.

---

### Post by jamle on 2009-07-29
uhhhh i tried the code in the terminal n dont know how to put a line in under another i just presume that means the next step so did it first line, then did the second line once it had desktop at the start of the new line and got this code, i see last bit says errors so i presume it didnt work :-(

  	 	 	 	 	 	  jay@jay-laptop:~$ cd Desktop sudo dpkg -i b43-fw*  
 jay@jay-laptop:~/Desktop$ sudo dpkg -i b43-fw*  
 (Reading database ... 165435 files and directories currently installed.)  
 Preparing to replace b43-fwcutter 1:011-5 (using b43-fwcutter_011-5_i386.deb) ...  
 Unpacking replacement b43-fwcutter ...  
 Setting up b43-fwcutter (1:011-5) ...  
 --2009-07-29 15:49:09--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)  
 Resolving downloads.openwrt.org... failed: Name or service not known.  
 wget: unable to resolve host address `downloads.openwrt.org'  
 dpkg: error processing b43-fwcutter (--install):  
  subprocess post-installation script returned error exit status 1  
 Processing triggers for man-db ...  
 Errors were encountered while processing:  
  b43-fwcutter

---

### Post by chili555 on 2009-07-29
Well, it's trying to out on the internet to grab some files! If we could get to the internet, we wouldn't need the firmware!!!

Let's try this. Download these two files in your Windows partition and drop them onto your desktop: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 

Right click the second one and select 'extract here.' Then do:```
cd ~/Desktop
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```Please let us know.> i just presume that means the next step so did it first line,Correct. It means do each command in order.

---

### Post by jamle on 2009-07-29
right i did that and it said it couldnt open the wl apsta thing BUT ive realised im being a clot and unplugged the internet wire (ethranet?) from my xbox 360 and stuck it in the side of my laptop and it now has internet wooooop

so i presume this will make life alot easir for getting it wireless? so whats the next step to getting this baby on line wirelessly now i have internet on the laptop through hard wire!

EDIT: just tried this code now im "online"
sudo apt-get install bcm43xx-fwcutterstill saying E: couldn't find package bcm43xx-fwcutter

---

### Post by chili555 on 2009-07-29
Please try:```
sudo apt-get install b43-fwcutter
```

---

### Post by jamle on 2009-07-29
brillaint now that worked (didnt last time i tried because it been trying to put in bcm43xx-fwcutter) the guide im using on the first post says to use that followed by 
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.oto get the firmware to work but when i substituted the bcm43xx-fwcutter for b34-fwcutter it didnt work said it couldn't open file..

---

### Post by chili555 on 2009-07-29
> brillaint now that worked If it worked, then you now have the firmware in place and do not have to do any other steps, except to check *iwconfig* to see if you have a wlan0 interface and then use the Network Manager icon to connect. Disconnect the ethernet cable first.

---

### Post by jamle on 2009-07-29
aww this is frustrating, nochange to the network manager, still wont show wireless connections its grey'd out. typed iwconfig and says no extensions to lo, eth0 e and pan0,eth1 however says
 IEEE 802.11 Nickname:""
Acess point: Not-Associated
Link quality: 5 signal level:199  Noise level:180
Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by chili555 on 2009-07-29
Please try:```
sudo modprobe b43
sudo ifconfig wlan0 up
iwconfig
```Now, do you have a wireless interface?

---

### Post by jamle on 2009-07-29
right next error:(

here's what happened when i did what u said, i still cant thankyou enough for sticking with me im sure we can get to the bright wireless future ubuntu has waiting for me!

jay@jay-laptop:~$ sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
jay@jay-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
jay@jay-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:180
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

jay@jay-laptop:~$

---

### Post by jamle on 2009-07-29
so im confident ive got the b43fwcutter installed but that doesnt seemed to do anything lol. something about adding stuff to the /lib/  ?

---

### Post by chili555 on 2009-07-29
Well! It looks like it attached as eth1 instead of the more common wlan0. You do have a wireless interface! Let's try a few things:```
sudo iwlist eth1 scan
```Do you see networks? Yours?```
sudo iwconfig eth1 essid <Your_Network_ESSID>
sudo dhclient eth1
```Any signs of life? It it trying? Any networks seen in Network Manager?

---

### Post by jamle on 2009-07-30
quickly tried it b4 work, the first command said failed to read scan data : invalid argument

But when i turned the lap top on it asked me to connect etc etc with the ssid and hex key entered only this stopping it from what i can see is the wireless card wasnt lighting up its button, when i psh the button to turn it on it doesnt do anything

---

### Post by jamle on 2009-07-30
the wireless manager is brilliant everytime i turn laptop on it pops up giving me the network details everything only it cant connet because it doesnt seem to want to turn the wireless card on and even when turned on manualy it wont do anything with it!

---

### Post by jamle on 2009-07-30
like to thank chilli for being freekin awesome and sorting this issue out! the key wasnt right and fo some reason although surposed to have letters in caps lowercase was difference between it working and not!

---

