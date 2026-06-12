---
title: "Need help connecting a Creative Zen Mozaic 4GB"
date: 2008-09-20
forum: Multimedia Software
---

### Post by Dakan on 2008-09-20
Hi Folks

I looking for some help to connect my MP3 player. I have installed Gnomad2 and Amarok. But neither will connect to the player.

Wikipedia say the Mozaic was only released in Aug 2008 so maybe there is no Ubuntu support for it yet. Does anybody know if this is the case?

Any way when I type in sudo mtp-detect it recognizes that it is a Creative Zen Mosaic

Device info:
   Manufacturer: Creative Technology Ltd
   Model: Creative ZEN Mozaic
   Device version: 1.03.01_1.03.04

But other than that I can't get anywhere with it.
Any help is appreciated. 

Thanks
Dakan

---

### Post by mattze on 2008-09-20
you can try running gnomad2 with root privileges. ```
gksu gnomad2
```

---

### Post by Dakan on 2008-09-21
Brilliant!
Thanks a lot mattze, that worked straight away.

U :guitar:

---

### Post by Lomz on 2008-10-17
I try to use gnomad2, using it with gksu, but I dont seem to get it to transfer the files onto the Mosaic, anything spesific I should try?

---

### Post by RaQua on 2008-10-31
Thanks!!! The solution of just running gnomad2 as a root worked! 

But why is that? i mean your main account belongs to the root group right?Sorry for the silly question but i am rather new to linux.

---

### Post by salvatordarling on 2008-11-01
Hi.  I have the same player, but it's a 2GB.  I'm having MAJOR problems connecting it at all.  I've tried the sudo mtp-detect command and it says 'command not found'.
I've also tried running gnomad 2 but nothing happens.  It doesn't recognise that the player is plugged in.

I'm running Ubuntu 8.10, but I don't know an awful lot about coding and commands etc...
If anyone could help, that would be great.

---

### Post by Karma_Police on 2008-11-26
You can access it with amarok.

In the amarok options go to the Media Devices section and select add new device. Choose MTP Media Device as a plugin, and give it any name you want.

Then, in the devices section of amorak connect to the device and you should see the files inside it.


@salvatordarling, You need to install the mtp tools. Open synaptic, search for "mtp-tools" and install that.

---

### Post by BeBoBli on 2008-11-30
This was working great for me yesterday, but this morning the gnomad 2 program crashed on me and in the process caused my mp3 player to become frozen and I can't turn it off. The terminal message says my device is null.

---

### Post by Karma_Police on 2008-11-30
Hi BeBoBli,

Mine has a small reset button on its left side. Just press it until it turns off.

---

### Post by BeBoBli on 2008-12-01
Yeah,sorry.  I figured that out very soon after I posted. Only bad part is that I had to reload some of the files back onto it.

---

### Post by cupevampe on 2008-12-14
WHat I would like to understand is which mp3 player actually works with no hassle with Linux and Amarok or Rythmbox... I have to buy a new mp3 player, i've always used iPods and Macs but now I use Linux and I'd like something that works  :)  any suggestion is mOST welcome.

---

### Post by slymi2005 on 2008-12-14
My sister's sony walkman nwz-s615f, the older one not the newest ones, works on ubuntu, it is just drag and drop through the file browser. Have not tried it using amarok but I'm sure it would work fine.

---

### Post by KaiTheory on 2008-12-23
Firstly make sure you have libnjb5. Open a terminal as root (or use sudo) and type apt-get install libnjb5 gnomad2. This will install gnomad2 and the library files for Creative mp3 players. Once you plug in the device it should pick it up right away. If you're using Amarok then you'll need to configure a new MTP device (if your Zen handles video).

---

### Post by KaiTheory on 2008-12-23
Not sure what you mean by "no hassle." Imagine if media players didn't come with a proprietary upload software package via cd like those designed for windoze.

---

### Post by ok67 on 2008-12-24
As long as root is running gnomad2 (sudo gnomad2) it works OK. But as a regular user I am not able to connect to the ZEN Mozaic (8GB). I assume that some rights needs to be set somewhere, anyone knows what to change to be able to access the Mozaic as a regular user?

---

### Post by Psychopump on 2009-04-14
> **mattze said:**
> you can try running gnomad2 with root privileges. ```
gksu gnomad2
```

Great advice! Worked for me too!
Just remember to edit the Gnomad2 entry in the menu.

---

### Post by azrockytop on 2009-04-15
I was reading all these posts, trying to figure out how to connect with my zen nano V and tried every trick listed here and more. . . . and then finally figured out you have to unmount from the device before gnomad2 or most any other music player will find it.   I hope this helps someone!!!  

Cheers

---

### Post by juicelubes on 2009-08-22
Right you will all have to forgive me for being thick but this is driving me chuffin mad! My daughter got given one of these creative zen mosaic 4gb for xmas and I just cannot get it to work. I have installed Amorak 2 and can't find a Media Devices section at all. I have downloaded "MTP Tools" all to no avail.
I also have Gnomad2 but dont know anything about sudo commands or what Im meant to be doing. Can someone point me in the right direction to an easy to follow (for an idiot) guide as to how I set this ruddy device up! Sorry and Thanks:confused:

---

### Post by juicelubes on 2009-08-22
OK sussed how to open terminal and typed in sudo command. Gnomad2 now see's the player and I can import and export music. However Gnomad2 see's avi files on the player but not on the cpu, which means i can't transfer films on to it. What am I doing wrong?
Ireally love ubuntu I really hate Creative zen products. Any tec manufacturer in the modern age who still only rigs their players up for windows doesn't deserve to sell any!

---

### Post by tylersontag on 2009-10-13
i have libmtp8 installed but i get a 'no jukebox found" error when i open up gnomad2 as sudo or not, device mounted or not.   same with another app i found 'kzenexplorer'

i tried reinstalling libnjb... not having much luck.

MTP-Tool's mtp-detect does not see any device, though it is plugged in and will mount.

---

### Post by theinnercityhippy on 2009-12-30
Hi all

The problem here is that the Creative Zen Mosaic is fairly new and the library that is required to use it - libnjb5 - is not very actively maintained anymore from what I can gather. The solution to this is fairly simple and requires the editing of one file as root.

In brief, the problem lies with the system that Ubuntu uses to mount USB devices which is called UDEV. This system gets a uniquely identifying serial number from the device when it is plugged in and matches it with a set of rules in the folder /etc/udev/rules.d/

Since this is quite a new player, a rule for it doen't exist and so the system doesn't know what to do with it, hence the only way that it can be mounted is as the root user which is a really bad idea and causes a security risk to you.

The solution is as follows. First of all we need to to open a terminal by going to Applications > Accessories > Terminal

Now we need to check out what the serial number of the device is. This is easily done by typing the following into the terminal and pressing enter (with the audio player plugged in:

```
lsusb
```

This gave me the following, remember we are looking for the Creative Zen player:

```
Bus 001 Device 013: ID 041e:4161 Creative Technology, Ltd
```

Make a note of the two numbers seperated by the colon, ie in this case 041e:4161 as we will need these in a moment.

Now we need to edit the UDEV rule that will allow this player to be mounted by myself. The file can be edited by typing the following into the terminal:

```
sudo gedit /etc/udev/rules.d/45-libnjb.rules
```

You will be prompted for your password since you must have root permissions to edit this file.

Now you need to add the following two lines to the bottom of the list, just above where it says LABEL="libnjb_rules_end"
. Note that the output from lsusb gave me the numbers 041e:4161 where 041e is the idVendor and 4161 is the idProduct that is in the snippet below. If your numbers were any different to these, adjust the next line accordingly (these numbers occasionally change with new models, so this should work with future models as well).

Add the following line:

```
# Creative Zen Mosaic
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4161", MODE="660", GROUP="audio"
```

(the # symbol in front of the first line is important as it tells ubuntu to ignore that line - it is there so you can easily see what it refers to)

Save the file when you have done this which should drop you back to your terminal window. Finally, you need to enter the following into the terminal once only:

```
sudo /etc/init.d/udev restart
```

Now, when you plug the player in and start gnomad2 it should be recognised and you will be able to transfer files back and forth.

I've tried emailing the developer to get this fix added to the package so hopefully it will appear in updated versions soon. Note also that udev is restarted every time you boot your computer so it should work fine from now on without any further command-line-fu.

Hope this is helpful, best wishes,

JimDog

---

### Post by SinglespeedJarv on 2010-01-15
Gnomad2 and libnjb5 installed, checked through files and found that "45-libnjb5.rules" doesn't contain the code for my MP3 player. So I tried to carry out the following:
> Now we need to edit the UDEV rule that will allow this player to be mounted by myself. The file can be edited by typing the following into the terminal:

     Code:
     sudo gedit /etc/udev/rules.d/45-libnjb.rules 
You will be prompted for your password since you must have root permissions to edit this file.However, the "45-libnjb5.rules" file isn't located under /etc/udev, just under file system/udev. But when I run the above code without the /etc I get the message: "no such file or directory"

---

### Post by heroes on 2010-02-06
with Gnomad2 installed, it should be fairly easy to get zen mozaic to connect to linux. or the problem could be the zen mozaic itself. try to reset it and select the cleanup option. then try to connect it again

---

### Post by dragonlemur on 2011-02-06
im having the same issue i have a zen 4 gb moziac lx and i cant get in to work. im using gnomad2 and i tried amorak but still nothing and my system is ubuntu 8.04 i think im not sure but i really need help im new to linux

---

### Post by twoflatfish on 2011-02-16
> **heroes said:**
> with Gnomad2 installed, it should be fairly easy to get zen mozaic to connect to linux. or the problem could be the zen mozaic itself. try to reset it and select the cleanup option. then try to connect it again

I have been using my Zen (Mozaic) with Nautilus file manager which will recognise and mount the Zen. You can 'drag and drop' to add items and delete items. 'Movie Player' will play the sound files if your Zen is usb attached. It's not perfect because there are other file systems on the Zen that are specific to the "Creative" system that Ubuntu does not recognise but I basically just use the MP3 sound format and don't need the missing files which are administration issues any way.
SJF

---

### Post by twoflatfish on 2011-02-16
I have been using my Zen (Mozaic) with Nautilus file manager which will recognise and mount the Zen. You can 'drag and drop' to add items and delete items. 'Movie Player' will play the sound files if your Zen is usb attached. It's not perfect because there are other file systems on the Zen that are specific to the "Creative" system that Ubuntu does not recognise but I basically just use the MP3 sound format and don't need the missing files which are administration issues any way.
SJF


I should have added that I am running Ubuntu 10.10

---

### Post by A_M_S on 2011-02-17
I'm using my Zen Mozaic 8GB  with Rhythmbox (whith 10.04) without problems after enabling the option "Use crossfading backend" in the 
Edit->preferences->playback window.



I think this is a bug that is posted somewhere in the internet.
(can't remember where :( )

---

### Post by Waltr on 2011-07-01
[QUOTE=
However, the "45-libnjb5.rules" file isn't located under /etc/udev, just under file system/udev. But when I run the above code without the /etc I get the message: "no such file or directory"[/QUOTE]

the "45-libnjb5.rules" didn't exist at all on my disks. When i entered the line code to edit it my computer was very helpful with creating it as an empty file.

Maybe this is alo why Gnomad2 doesn't run properly??????
When on various moments it just closes.

In Amamrok I can not find any devices as stated before, my amarok seems to be only a mp3-player. Is there any onter instalation????????

Rythmbox could show that my mozaik was there, even some information on its hardware, but no way it will conect. :(

Anyone know a solution on any of these ad facts??

---

