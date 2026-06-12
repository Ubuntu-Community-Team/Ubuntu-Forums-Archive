---
title: "Best solution for all ipods on Ubuntu"
date: 2009-02-27
forum: Multimedia Software
---

### Post by chanyunkwan on 2009-02-27
If you really need to use iTune to Synchronize your media data to your lovely ipod, here is pretty good solution for you.
If you are satisfied with all kinds of iPod manager tool on Linux, you probably don't really need it.

As to me, I am tired of testing the iPod managers on Linux. They mostly will mess up the album cover on my ipod nano Gen4 8G.

I have a desktop computer with XP system in my house. I usually put all the music and some TV shows in the iTune library in this computer. I think it is really simple to use iTune to manage my songs and video between my computer and my ipod.
 
**Problems**
1. It's not a good idea to install iTune base on wine.
2. Dual system takes too much time to switch between ubuntu and windows.

**Target**
1. Getting the same iTune library on Ubuntu. 
2. Synchronize iPod through itune.
3. Manager all my music with itune.

Ok. Here's the solution.

[COLOR="RoyalBlue"]**Virtualbox on ubuntu**[/COLOR]

[COLOR="Green"][B]1. install virtualbox on ubuntu.

2. install xp system on the Virtual machine.

3. creat a folder for you iTune library on your ubuntu system. 

4. Add the folder you just created to the virtual machine as a sharefolder. 

5. install the newest iTune on your virtual machine and choose the sharefolder as your itune library folder.
[/B][/COLOR]
This means you can use your itune library still when your virtual machine is shut down. When you want to sychornize your ipod with your library, you can use the iTune on your virtual machine.

It's fast and convenient!!

My laptop is actually old but it's powerful enough for me.

Running the virtual machine on my laptop is way fast! Boot time for the virtual xp system is about 10-15 seconds. 

[COLOR="Red"]**NOTICE:**[/COLOR]
1. you need to assign the permission for the virtual machine to use the usb device. 
2. I choosed host interface for the network of the virtual machine.(I'm not sure if it's a necessity)
3. You'd better don't let the music player on ubuntu to edit your itune library.
[B]Yamipod is a really nice programme to manage your ipod no matter on windows or on Ubuntu.
[/B]
Too bad I can't use it on my ubuntu. Fortunately, it works great on my virtual machine.

Intel Dual core 2, 1.6G    RAM 2G
(Dual core cpu works better than a higher frequency single core cpu when it comes to running a virtual machine)

If you need more details, please let me know. I can post screenshots for instruction. 

Hope it can help you.

Thank you for your reading.

Have a nice day.

Sorry for my English.

---

