---
title: "ATI Remote Wonder worked during installation but not after first reboot"
date: 2010-12-30
forum: Mythbuntu
---

### Post by bludshot on 2010-12-30
I just installed Mythbuntu 10.10, and during the installation it asks you about your remote. I chose the ATI option in the drop down (it has some other stuff listed like ATI/x10/whatever?), but it's the only one that says ATI. As soon as I did that, the remote was functioning - like *during* the rest of the install.

I could use the directional pad on the remote to move the mouse around the screen. (And I should mention I was hugely impressed by this!)

Then when the install was complete it reboots (or asks for a reboot, I forget) so I rebooted to start mythbuntu for the first time. But the remote didn't work anymore. (oddly!)

I checked my settings and the remote was still set to the same one. It doesn't work anymore and I don't know how to fix it. :confused:

---

### Post by BigPacks on 2010-12-30
I have a weird error with my Mythbuntu 10.04 setup with my ATI Remote Wonder.  It might apply to you.

Whenever I enter the Mythbuntu Control Center, the remote always disables itself.  You have to reselect it every time.

---

### Post by bludshot on 2010-12-30
How do you "reselect it" exactly?

---

### Post by BigPacks on 2010-12-30
From within the Mythbuntu Control Center in the Infrared tab.  I keeps unselecting itself.

I don't know if this is your problem, but I have to make sure it's selected every time I apply changes from the MCC.

---

### Post by bludshot on 2010-12-30
Oh.. yeah, that's what I meant when I said "I checked my settings and the remote was still set to the same one"; when I go to MCC it is still set on the ATI remote. So I have a different problem than you, thanks though.


Sort of additional info: My remote has *never* worked upon booting up into mythbuntu (it's not like it works sometimes and turns off other times), BUT, it *did* work *during* the installation process before the reboot.

---

### Post by bludshot on 2010-12-31
I found a page that supposedly tells you how to get the ATI Remote Wonder working in Mythbuntu 10.10 [http://www.mythtv.org/wiki/ATI_Remote_Wonder](http://www.mythtv.org/wiki/ATI_Remote_Wonder)

It says
> 
Mythbuntu 10.10 without lirc

In order to control the mouse with the mouse-buttons on the remote (outside of MythTV of course, because there is no mouse in MythTV), one should **use the ati_remote driver**. This has additional benefits, namely that there is no delay in using the same button again, so you can scroll very fast. This driver sees the remote as a keyboard. This driver loaded automatically on my box, but **I removed lirc first**. I don't know if that is neccesary. If you can use your mouse-move buttons, you know the module ati_remote is loaded. The only problem this driver has, is that some buttons do not work: channel up and down, TV, DVD, and the OK button. This is because these keys have a keycode higher than 255 and thus X cannot read them (see [http://bugs.freedesktop.org/show_bug.cgi?id=11227](http://bugs.freedesktop.org/show_bug.cgi?id=11227)). 

How do I "use the ati_remote driver"? I need detailed instructions because I don't have the first clue how to do that, I'm a linux noob.

Also, while he says if it works by then then you don't need to, how do you "remove lirc"?

---

### Post by bludshot on 2010-12-31
I fixed it. I had to edit the file /etc/modules and add the line "ati_remote"

(so, you go into terminal, cd /etc   sudo nano modules)


**Note: doing this will cause a new problem where MythTV will freeze and crash when you try to exit it. To solve that problem you have to uninstall lirc. I uninstalled liblircclient0, lirc, and mythbuntu-lirc-generator. But uninstalling liblircclient0 will uninstall VLC which you obviously want to keep, so I reinstalled VLC (ie: you might want to not uninstall liblircclient0, also I doubt if you need to uninstall mythbuntu-lirc-generator)

---

