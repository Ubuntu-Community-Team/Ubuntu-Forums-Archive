---
title: "Webcam problem in Ubuntu 11.10"
date: 2011-10-14
forum: Multimedia Software
---

### Post by Gramzivi on 2011-10-14
I have webcam Genius Eye 312, and i try to get it to work properly on Ubuntu 11.10.

Cheese recognize webcam, but Skype don't, and that is most important, i need it for Skype and Gtalk. How to configure/fix that bug ?

i tried with

> 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
- that work in 11.04 but here... nope

---

### Post by kostaya on 2011-10-15
same here. the trick with LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype worked with previous versions but with 11.10 i have more problems the camera shows very white pictue in cheese and in skype no picture at all

---

### Post by Chris Mousset on 2011-10-15
Try LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so

---

### Post by Gramzivi on 2011-10-15
Finally !!

it worked for me with command
> 
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype


---

### Post by astathios on 2011-10-16
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype 
worked for me as well 
any idea how to use this fix without the need of terminal?

---

### Post by Gramzivi on 2011-10-17
write in empty document:

> 
#!/bin/sh
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

And set in permissions : Allow file executing as a program.


Every time you need to click run... because they will ask you some things (open in console, open in notepad, run) you click run and skype will be opened without console. It's not the best way but i do  that.

---

### Post by okkadiroglu on 2011-10-17
Hi,

My webcam works with Skype and Cheese but my face is blue. (In real life I am a normal person) It was not like this before 11.10.

How can I correct this?

Many Thanks

---

### Post by astathios on 2011-10-17
the script worked thank you not bad idea!!
i have problems with the colorsand the brightness of webcam 
but there is a fast solution!!
i download from software manager the guvcview , is a software which u can adjust the cam settings.
so everytime i want to use my webcam i run this software i fix the settings and i save them . as a result i get a lets say good solution for my cam.
The system lost the settings everytime i restart my pc
i hope it helps it works for me

---

### Post by okkadiroglu on 2011-10-17
Thanks for the tip. Now I am not a green-blue person with guvcview. How can I make Skype use it?

---

### Post by astathios on 2011-10-17
if  you save the configuration u like in guvcview (save,save,replace) then the settings will load automaticaly in skype

---

### Post by Astrotrain on 2011-10-24
> **Gramzivi said:**
> Finally !!

it worked for me with command

> LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype

I`d like to add that this command will  work only if you have 32bit Oneiric installed. For 64bit  you must first:
 
```
sudo apt-get install libv4l-0:i386
```   in order to obtain required 32bit version of v4l1compat.so  . At least I had to do it.  :)

---

### Post by JoZ3 on 2011-10-25
I have the same problems with webcam colors, but when I try to open guvcview appear this error
```

guvcview 1.4.5
Fatal:g_thread NOT supported

```

The webcam colors stink!!! :(

---

### Post by Solid_Danil on 2011-11-13
> **JoZ3 said:**
> I have the same problems with webcam colors, but when I try to open guvcview appear this error
```

guvcview 1.4.5
Fatal:g_thread NOT supported

```

The webcam colors stink!!! :(

This solution was helpful for me:
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/838739/comments/16](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/838739/comments/16)

---

### Post by maryeliezka on 2011-11-16
Will it work for my problem? When i opened cheese, my pic's color became grayscale. I didn't use any effect!!!

---

### Post by kvarkno1 on 2011-11-29
1)
Add these lines to the end of the /etc/apt/sources.list file. 

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main
```2)
Run:
```
sudo apt-get update
```
3)
Install specific versions of the necessary packages from Maverick's repository:
```

sudo apt-get install ia32-libs=20090808ubuntu9 lib32v4l-0=0.6.4-1ubuntu1 libv4l-0=0.6.4-1ubuntu1
```4)
To prevent these packages to be upgraded, run these:

```
echo ia32-libs hold | dpkg --set-selections
echo lib32v4l-0 hold | dpkg --set-selections
echo libv4l-0 hold | dpkg --set-selections

```5)
Then this command is going to work and you will have webcam again in Skype. At least it's working for me. 

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype 
```6)
You can remove the added lines from /etc/apt/sources.list file.

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main
```

---

### Post by madjr on 2011-12-23
i just dragged skype icon to the desktop from the dash and added this command:

```
env LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

or just open a terminal and paste the command.

note the "env" at the start

---

### Post by mgt2000 on 2011-12-31
Thanks it works fine for me too.
If you don't want to use terminal you can put:
bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

instead:
skype

in the setting of skype in main menu

---

### Post by Carl Clark on 2012-01-25
Help !!!!
  Ubuntu 11.10 webcam not working with cheese or skype... yet, it does work with camorama... I really need it to work  with skype.

---

### Post by mörgæs on 2012-02-03
> **JoZ3 said:**
> I have the same problems with webcam colors, but when I try to open guvcview appear this error
```

guvcview 1.4.5
Fatal:g_thread NOT supported

```

It is fixed in guvcview 1.5.2

---

### Post by Katla on 2012-02-04
I, too, have the same issue. Logitech webcam works fine in Cheese, but not Skype. I have tried using the code given in the terminal (with as many variations as I've seen), but get  an error message saying it cannot be preloaded and is ignored. 

It is driving me crazy. I really need the webcam and Skype to work in tandem, but am at a loss.

---

### Post by aleoo on 2012-05-02
May I have some help troubleshooting?
This is the thread: [http://ubuntuforums.org/showthread.php?t=1936625](http://ubuntuforums.org/showthread.php?t=1936625)

---

