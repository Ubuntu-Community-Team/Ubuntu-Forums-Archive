---
title: "Solution to capturing video from a DV camecorder - Jaunty + Kino"
date: 2009-07-10
forum: Multimedia Software
---

### Post by ratmonkey on 2009-07-10
[Update - non-terminal directions for Lucid Lynx added in post #8]

Longtime Gentoo user here taking a vacation in Ubuntu-land.

Tried using Kino to capture some video via the Firewire (ieee 1394) connection on my camcorder but it didn't work out of the box on a fresh Jaunty install. All the solutions that I found through Google either didn't work at all or would only last through one restart. Lame.

Basically, what's happening is that giving user access to the module that allows Kino to read from the camcorder (raw1394) carries a security risk. The Ubuntu developers have chosen not to open this hole on the default installation. Probably the right thing to do, but it sucks for us users with DV camcorders.

Personally I'm not too worried about someone breaking into my house and hacking into my personal PC via the firewire port, so I came up with this solution that should 'just work' after it's in place. (Okay, so truth be told, I really don't know what the security flaw is, so use at your own risk.)

A system called udev manages permissions to all the devices on your system. This solution adds a new rule to udev that will allow users who belong to a new group to access the raw1394 module that is needed for Kino to talk to your Camcorder.

```
$ sudo apt-get install kino
```Install Kino.

Now plug in your camercorder and run Kino. You'll most likely get an error in the status bar at the bottom of the program window when you click on the Capture tab.

```
$ gksudo kino
```Now run it again as root. If it works this time then these instructions should work for you. If not... well then, it sucks to be you.

Shut down kino and unplug your camcorder

```
$ sudo groupadd dvcamera
$ sudo usermod -a -G dvcamera your_user_name
```create a new user group called dvcamera and add yourself to it

```
$ sudo bash -c 'echo "KERNEL==\"raw1394\", GROUP=\"dvcamera\", MODE=\"0660\"" > /etc/udev/rules.d/30-raw1394.rules'
```this writes a new user defined udev rules file that makes the raw1394 module accessible to members of the group dvcamera. The file is located at /etc/udev/rules.d/ 

```
$ sudo modprobe -r raw1394
```unload the raw1394 module in case it's already been loaded.

That's it... now plug in your camcorder, wait a few seconds, and check to see if the rule worked.

```
$ ls -l /dev/raw1394
crw-rw---- 1 root **dvcamera** 171, 0 2009-07-10 20:44 /dev/raw1394
```This shows that the module automatically loaded and is accessible to the owner (root) and members of the group dvcamera. Since you added yourself to the group when you created it, you should be able to use Kino as a regular user after you logout and back in or reboot.

Reboot (or logout and log back in) and then enjoy! 


----

If you have multiple users that you want to give access to simply add them to dvcamera group.
```
$ usermod -a -G dvcamera user_name
```or you can also add them via System -> Administration -> Users and Groups tool

---

And finally, if you would like to undo these changes for whatever reason:
```
$ sudo rm /etc/udev/rules.d/30-raw1394.rules
$ sudo groupdel dvcamera
$ sudo reboot
```

---

### Post by z0mbie on 2009-07-11
Awesome tutorial. I had to reboot then it worked fine. Thank you so much. 

BTW, you should visit us more often from the Gentoo world!

---

### Post by ratmonkey on 2009-07-12
Glad to hear it worked! 

I'm a little mystified at why the reboot is necessary at the end... I mucked around with it for a while, but never could figure out a way around it. :confused:

But my camera is working and doesn't require jumping through any more hoops, so I'm happy.

---

### Post by zekesax on 2009-11-24
By Linux standards, I'm a total newbie.  I just built a system from my old Dell Dimension case..  Intel Motherboard, 2.26 Dual Core Pentium, 1 TB HD & Ubuntu Distro.  That being said, I really know nothing about programming ( I knew msconfig, command prompt type stuff on Win).

I knew just enough to know where Terminal was and type these commands in.  I was hoping I got the spacing correct or didn't even know if it was relevant.  That being said, this thread and Ubuntu pocket guide got my dv camera working with i1394, Kino & DVGrab.

I now know how to use Synaptic Package Manager too!

I even lucked out cause it didn't "suck to be me" and it worked after the first few lines of code.  

Thank you very, very much  :)

Zeke 

P.S. My first night with Ubuntu (tried small dam linux)

---

### Post by MisFitt on 2010-03-22
> **ratmonkey said:**
> Glad to hear it worked! 

I'm a little mystified at why the reboot is necessary at the end... I mucked around with it for a while, but never could figure out a way around it. :confused:

But my camera is working and doesn't require jumping through any more hoops, so I'm happy.
I want to thank you and let you know that every time I need to install ubuntu again for whatever reason this is the only method that's worked-7 times now if I recall correctly,
THANKS!

---

### Post by OrionXIII on 2010-05-26
Process worked like a charm for me too! Thank you very much!

I've been wondering what I was doing wrong...An easy fix!

Orion

---

### Post by 73ckn797 on 2010-05-31
I tried multiple solutions to this issue and this has worked on one computer. Now I will try it on this computer and hope it works after trying several other solutions that did not work. I will get back if it works here. These computer are still using Karmic 9.10.

---

### Post by ratmonkey on 2010-06-04
Glad to hear this is working for everyone. It should continue to work as long as linux continues to use udev and the raw1394 module is used for DV Cameras with ieee1394/firewire ports.

*Here's non-terminal directions for those who are squeamish about using the terminal (using Lucid Lynx):*

1. Go to *System -> Administration -> Users and Groups*

2. Click on the *_M_anage Groups* button. The *Groups settings* window will open

3. Click on the *_A_dd* button in the *Groups Settings* window

4. If prompted, enter your password and press the *_A_uthenticate* button

5. In the resulting *New Group* window, enter the name **dvcamera** in the Group *_n_ame:* field.

6. Select the users you want to have access to the camcorder from the *Group Members* list and press the *_O_K* button. Then exit out of the *Users and Groups* tool.

7. Press ALT+F2 on your keyboard to start the *Run Application* dialog

8. In the resulting *Run Application* window enter the command **gksu gedit** and press the *_R_un* button. This starts a text editor with root (i.e. administrator) privileges.

9. Enter your password if prompted

10. A text editor window will open

11. Enter the following line in the text editor:

**KERNEL=="raw1394", GROUP="dvcamera", MODE="0660"**

12. Go to *File -> Save As*

13. In the *Name:* field type the the name **/etc/udev/rules.d/30-1394.rules** and press the *_S_ave* button

14. Close text editor, Reboot, and enjoy.

---

### Post by 73ckn797 on 2010-06-05
> **73ckn797 said:**
> I tried multiple solutions to this issue and this has worked on one computer. Now I will try it on this computer and hope it works after trying several other solutions that did not work. I will get back if it works here. These computer are still using Karmic 9.10.


Got it working! Thanks.

---

### Post by Corvair on 2011-05-06
Hello ratmonkey,

I want to thank you for the solution to running my camcorder tape recorder
with keno. I already had keno but it was not working so I entered gksudo kino to the terminal and it solved the problem. 

corvair

---

