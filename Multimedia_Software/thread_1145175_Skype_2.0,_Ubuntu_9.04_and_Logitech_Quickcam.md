---
title: "Skype 2.0, Ubuntu 9.04 and Logitech Quickcam"
date: 2009-05-01
forum: Multimedia Software
---

### Post by princeofpersia on 2009-05-01
Greetings, 

I'm having problems with Skype 2.0 on Ubuntu 9.04. I managed to get the sound working, but I have problems with the webcam. The webcam is Logitech Quickcam (usb id: 046d:092d) and under Skype it just shows multicolored shivering lines on screen. The webcam works fine with Xawtv.

---

### Post by Bucky Ball on 2009-05-01
Have you added the Medibuntu repository to your sources list? You might be missing something. A more recent version is available in there and that might fix some things.

Medibuntu contains third-party apps and software which are not installed automatically. You will find Skype in Synaptics once you add the repo.

:)

* Edit! As far as I know, the Linux version of Skype has no videocall function. I have coincidentally just been looking at it. Where did you even find any controls for it in the Skype GUI?

---

### Post by princeofpersia on 2009-05-01
I forgot to give details about installation of Skype. 
I installed skype the following way: 

I added the line

*deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free*

to /etc/apt/sources.lst 

and then issued 

*aptitude install skype *

---

### Post by Bucky Ball on 2009-05-01
No videocall in Linux Skype. We've pestered them for ages.

---

### Post by Claus7 on 2009-05-01
Hello,

there is definitely video call in linux skype. And it is working as it should with some things to be refined though:

I have installed the deb file from the skype website (yes it sais that it does not support 9.04 at the moment, yet it is working).

Install the deb and then do:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and your webcam will work nice and easy. If you do not want to type all these things, go to your *(edit): ***.bashrc** file and make an alias:
alias skype='LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

so every time you type skype to open nice an easy. Hope this in the near future to be fixed.

Regards!

---

### Post by princeofpersia on 2009-05-01
So their site spreads disinformation ... 
"The latest version introduces **free video calls** to Linux."

Seriously, the version I installed this afternoon had video buttons in the interface and I guess they meant it to work. Maybe they support Debian Lenny and I hastily applied Debian howto to that Ubuntu install. I'm going to try contact their support.

---

### Post by Claus7 on 2009-05-01
Hello,

sorry, yet I do not get you. The jaunty release is new, so it is not something weird not to have released an official support for 9.04 yet. Why don't you try what I did and see if it is working? Just remove everything that has to do with skype before. 

Also oss version should work, yet you have to install it via command line. 

Regards!

---

### Post by princeofpersia on 2009-05-01
The machine is not mine, so I will try the solution first time I have the opportunity and will post follow-up reply. Thanks for the quick answers!

EDIT: I'm not native English speaker so it takes some time for me to write the messages. You reply faster than I can write.  My previous message was answer to previous post.

---

### Post by Bucky Ball on 2009-05-01
> **Claus7 said:**
> Hello,

there is definitely video call in linux skype. 

Apologies. Yes, there appears to be according to the website. But you know, I have that very same version installed and no video buttons at all.

(and yes, it took so long coming I gave up waiting and forgot about it ... )

---

### Post by TheBuzzSaw on 2009-05-01
Whenever I plug in my Quickcam, my system freezes! Even the mouse locks in place. I am running 64-bit 9.04, and I would like to do video calls with my family. :(

---

### Post by princeofpersia on 2009-05-01
You might wish to try 32 bit version just to check if it's a compatibility problem. 32 bit verison should work fine on newer architectures.

---

### Post by Claus7 on 2009-05-01
Hello,

since skype was the best program I could choose for linux in order to do video/audio chat with my friends I have to say that it is working pretty decently in all the versions that I had it installed. It is a pity that it is a little bit more buggy (according to my experience) than the previous versions, yet definitely is a good program. Undoubtedly they can do a far greater job for the linux users (the skype developers). Yet, do not get disappointed, because I have heard that the windows 4 version was a lot of buggy. Have in mind that we are less (more or less) than 5% of the total computer users, so the development of applications for us take much more time.

I do not have experience with 64 systems. If nothing else is working (either in a 64 system or not) I would advice you to go for oss version as I say above. It worked in dapper, in hardy and I hope in every version of ubuntu because it is the source code and you can compile it specifically for your system.

No apologies are needed, not anything else. I hope that all of you would find the best solution for your system. Have in mind that it is better, when you try a solution, to erase before what you have done, so as not to mess things with every trial you make.

Regards!

---

### Post by ufugu on 2009-05-01
Further per Bucky's suggestion, uninstall whatever version of Skype you are using.  Enable the Medibuntu repositories and install Skype from there.

I spent countless hours searching forums and trying to get Skype working correctly with my Logitech and got so frustrated.  Using the Medibuntu version fixed everything, works perfectly. :)

Hope it will work for you too.

---

### Post by xc3RnbFO8P on 2009-05-01
> Using the Medibuntu version fixed everything, works perfectly
In Synaptic Package Manager install:
skype-common
skype-static

---

### Post by WildeBeest on 2009-05-01
Where is the .bashrch file?

---

### Post by Claus7 on 2009-05-01
Hello,

> **WildeBeest said:**
> Where is the .bashrch file?

just open a terminal and type:
vi .bashrc

if you navigate a little bit in the file, you will see a section having aliases. There, under the last one, type the string I give (you can type it wherever you like, yet just to have it in place where the other aliases are).

The aforementioned file is a hidden one (that's why the dot in front of the name of the file) and is in your /home/user_name folder.

Regards!

---

### Post by princeofpersia on 2009-05-05
The promised follow-up for the users that read the tread later:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Worked fine!

---

### Post by tonytraductor on 2009-05-10
I also have a quickcam, and it has also locked up my desktop, when I tried to use Camorama.

Oddly, the app, Cheese, seems to work perfectly with said cam, but the camera is not working with Camorama, Kopete, gqcam, skype, etc.


Nothing in the medibuntu repo seems to make any difference.

---

### Post by Fellipec on 2009-05-10
Thank You very much Claus7, it works perfect for me!
I just made a script with this order in usr/bin called "skype-webcam", to make it easier to launch.

Regards!

> **Claus7 said:**
> Hello,

there is definitely video call in linux skype. And it is working as it should with some things to be refined though:

I have installed the deb file from the skype website (yes it sais that it does not support 9.04 at the moment, yet it is working).

Install the deb and then do:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and your webcam will work nice and easy. If you do not want to type all these things, go to your .bashrch file and make an alias:
alias skype='LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

so every time you type skype to open nice an easy. Hope this in the near future to be fixed.

Regards!

---

### Post by sockmoney on 2009-07-16
Great advice on using the following command to launch Skype:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I just put the above in a file called skype_launch.sh and used that script to add a launch icon to my top menu bar of apps.

Now it launches and the camera works!  Nice tip!   Thanks!

---

### Post by Piddell on 2009-10-22
I managed to get my logitech webcam working as follows:
Go to System - preferences - main menu]
internet - skype - properties
put the following into command
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
and the static went to a nice clean video image!

I hate to say it but its a great picture, the ekiga one is way to dark
cheese only offer updates every 3 seconds and is dark

Phill

:popcorn:

---

### Post by ajith learning da ropes on 2009-10-25
hey Claus7, sorry but i'm very new to Ubuntu.....i run 9.04 and just can't seem to find the .bashrch file u r talking about!! can u help me find it?
Thanks in advance

---

### Post by pi4r0n on 2009-10-29
**ajith learning da ropes** open gnome terminal, make sure you are in home directory by typing **cd** and then type again **ls -a**

Note: ***_-a_*** - will show you hidden folders.

In order to modify it type either **vi .bashrch** or **nano .bashrch**

Ta

pi4r0n

---

### Post by Claus7 on 2009-11-21
Hello,

Long time no see to this thread... Yet,

> **Fellipec said:**
> Thank You very much Claus7, it works perfect for me!
I just made a script with this order in usr/bin called "skype-webcam", to make it easier to launch.

Regards!

> **sockmoney said:**
> Great advice on using the following command to launch Skype:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I just put the above in a file called skype_launch.sh and used that script to add a launch icon to my top menu bar of apps.

Now it launches and the camera works!  Nice tip!   Thanks!

I can see that you did a great job with the launching thing. I had problems with that, while using the icon in my panel. Even though the .bashrc file solved the issue if I typed skype in a terminal, this was not working while launching from a panel icon.

Allow me to describe in detail the solution (with aid from here: [http://ubuntuforums.org/showthread.php?t=980787):](http://ubuntuforums.org/showthread.php?t=980787):)

```
cd /usr/bin
sudo vim mylaunch
```

and there insert
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

save and quit and then type (that way you make mylaunch an executable file):
```
sudo chmod 755 mylaunch
```

Now go to the panel icon of skype and right click it.
Go to properties and click first at the icon on the top left hand side.
There you will see a path similar or the same to:
> /usr/share/icons/skype.png
Copy that...

Now go to the command tab and insert the following:
> /usr/bin/mylaunch

This action will change the default icon of the skype launcher so in order to restore it click on the left hand side icon once again and paste the path you copied before.

Hope this was clear!
Regards to all!

PS: This is working in karmic as well.

---

### Post by sandy8925 on 2009-11-21
Isn't it .bashrc and not .bashrch ?

I have a quickcam im too and it was working earlier but it's not working now. I'm using Jaunty (Ubuntu 9.04). I compiled the 2.6.31 kernel a month or two ago and I'm currently using that so I suspect that is the problem. It doesn't work in Cheese either but it does show up in lsusb.

Bus 003 Device 003: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect

Also, I didn't have to use the LD_PRELOAD thingy to do video conversation. It worked fine here (but in my desktop I ahd to sue the LD_PRELOAD thing)

---

### Post by Claus7 on 2009-11-22
Hello,

> **WildeBeest said:**
> Where is the .bashrch file?

> **ajith learning da ropes said:**
> hey Claus7, sorry but i'm very new to Ubuntu.....i run 9.04 and just can't seem to find the .bashrch file u r talking about!! can u help me find it?
Thanks in advance

> **pi4r0n said:**
> **ajith learning da ropes** open gnome terminal, make sure you are in home directory by typing **cd** and then type again **ls -a**

Note: ***_-a_*** - will show you hidden folders.

In order to modify it type either **vi .bashrch** or **nano .bashrch**

Ta

pi4r0n

> **sandy8925 said:**
> Isn't it .bashrc and not .bashrch ?


I'm really sorry for miss-typing such a thing. Thank you *sandy8925* for pointing out.

It is: [SIZE="5"].bashrc[/SIZE] and NOT .bashrc*h*

Thank you and sorry for the inconvenience,
Regards!

---

### Post by Claus7 on 2009-11-23
Hello,

> **sandy8925 said:**
> 
I have a quickcam im too and it was working earlier but it's not working now. I'm using Jaunty (Ubuntu 9.04). I compiled the 2.6.31 kernel a month or two ago and I'm currently using that so I suspect that is the problem. It doesn't work in Cheese either but it does show up in lsusb.

Bus 003 Device 003: ID 046d:08d9 Logitech, Inc. QuickCam IM/Connect

Also, I didn't have to use the LD_PRELOAD thingy to do video conversation. It worked fine here (but in my desktop I ahd to sue the LD_PRELOAD thing)

Judging from here:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

it does not seem that you have support for higher versions of ubuntu, yet the web page might not be updated. If I were in your shoes, I would check the links from that web page.

Regards!

---

### Post by Lorac1949 on 2009-11-23
> **ufugu said:**
> Further per Bucky's suggestion, uninstall whatever version of Skype you are using.  Enable the Medibuntu repositories and install Skype from there.

I spent countless hours searching forums and trying to get Skype working correctly with my Logitech and got so frustrated.  Using the Medibuntu version fixed everything, works perfectly. :)

Hope it will work for you too.
Thank you! This really helped me, too.

---

