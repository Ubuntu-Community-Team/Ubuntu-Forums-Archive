---
title: "ATI Radeon HD 4870 1GB Driver Needed"
date: 2009-05-09
forum: Multimedia Software
---

### Post by isa.k on 2009-05-09
I have Jaunty 64 installed on:

- Intel Q8200 2.33GHz Core 2 Quad CPU
- ATI RADEON HD 4870 Video Card 1GB
- 8GB RAM

And am looking for a driver for the video card.

I found one at:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

However, I can't seem to be able to install it... Sooo frustrating...

Any help to get it running full specs? Plskthx :)

---

### Post by Operan on 2009-05-09
What errors you got?

First, download that driver into your hard drive.
Then install it:
sudo ./your_driver_filenam.run
That't all!

---

### Post by isa.k on 2009-05-09
> **Operan said:**
> What errors you got?

First, download that driver into your hard drive.
Then install it:
sudo ./your_driver_filenam.run
That't all!
Woops!

Sorry, I forgot to put up the images:

I double clicked on the package and got this:

[[IMG]http://img7.imageshack.us/img7/7180/screenshotatidriverinst.png[/IMG]](http://img7.imageshack.us/my.php?image=screenshotatidriverinst.png)


Then I changed the character coding to **Western (ISO-8859-15)**:

[[IMG]http://img301.imageshack.us/img301/7180/screenshotatidriverinst.png[/IMG]](http://img301.imageshack.us/my.php?image=screenshotatidriverinst.png)

I will try the fix you offered :) and post back the result once I get a result (pos or neg) :)

---

### Post by isa.k on 2009-05-09
Seems like it failed :(

```
isa-ubuntu64:~$ sudo ./ati-driver-installer-9-4-x86.x86_64.run
[sudo] password for isa: 
sudo: ./ati-driver-installer-9-4-x86.x86_64.run: command not found
```

---

### Post by Dsha on 2009-05-09
The correct command to install that is :

sudo sh ./your_driver_filename.run

Good Luck

---

### Post by isa.k on 2009-05-09
Thank you for your effort, but it seemed to fail again :(

> isa-ubuntu64:~$ sudo sh ./ati-driver-installer-9-4-x86.x86_64.run
[sudo] password for isa: 
sh: Can't open ./ati-driver-installer-9-4-x86.x86_64.run


---

### Post by Arup on 2009-05-09
Save yourself the hassle, install envyng-core by typing sudo apt-get install envyng-core. Get out of GDI by hitting ctrl+alt+F1 and then login to tty, after that type sudo /etc/init.d/gdm stop

Then type envyng -t and it will isntall latest ATI driver from the ATI site, setup your xorg and after reboot you will have your driver.

---

### Post by isa.k on 2009-05-09
> **Arup said:**
> Save yourself the hassle, install envyng-core by typing sudo apt-get install envyng-core. Get out of GDI by hitting ctrl+alt+F1 and then login to tty, after that type sudo /etc/init.d/gdm stop

Then type envyng -t and it will isntall latest ATI driver from the ATI site, setup your xorg and after reboot you will have your driver.
You know what?

I found the command online to install envyng-core, and when I hit CTRL+ALT+F1, I went into text screen/command prompt mode... Something I am terribly unfamiliar with in the Linux world!

I could not get back to the GUI to see what I had to do next, and so I reboot with CTRL+ALT+DEL...

That was not the worst of it... The worst of it is, I am now writing to you this post from the live CD version of Ubuntu!

Why?

Well, when I rebooted, my screen looked like a screen full of fine static!

i.e. black and white grains across the whole friggin screen!

I appreciate your help, but next time please, pretty please, with cherries on top, let the person you are helping know that this will happen and ask them to either print out, or write the instructions on a piece of paper...

Phewh!

Now... with that off my chest... How can I get my screen back to normal with my installed version of Jaunty working like it was before the installation of envygng-core and hitting CTRL+ALT+F1???

Please respond asap...

As I am really worried that this is going to be a drawn out process, and it is 10:30pm here, and I need to get up early tomorrow...

Anxiously awaiting a solution.

**isa**

---

### Post by Arup on 2009-05-09
Sorry you had to go through that, install envyng-core and envyng-gtk via synaptic. When you hit ctrl+alt+F1 you went into a tty that is terminal, futher you have to type sudo /etc/init.d/gdm stop to switch off GUI completely, then you enter envyng -t and follow instructions.

---

### Post by isa.k on 2009-05-09
> **Arup said:**
> Sorry you had to go through that, install envyng-core and envyng-gtk via synaptic. When you hit ctrl+alt+F1 you went into a tty that is terminal, futher you have to type sudo /etc/init.d/gdm stop to switch off GUI completely, then you enter envyng -t and follow instructions.
I do not mind, as long as I can get my system up and running again...

Now pray tell, how would I do that with a screen looking like black and white sand?

---

### Post by Bobber76 on 2009-05-09
Just have to chmod the downloaded file, like this:

sudo chmod 777 filename.run

then:

sudo ./filename.run

This will work for sure.

---

### Post by Arup on 2009-05-09
> **isa.k said:**
> I do not mind, as long as I can get my system up and running again...

Now pray tell, how would I do that with a screen looking like black and white sand?

If the screen has no text then there is seriously wrong somewhere. Ideally when you hit the ctrl+alt+F1 you should see a text based login.

---

### Post by isa.k on 2009-05-09
For everyones enlightenment, my screen when Ubuntu splash screen's line fills up, turns into this:

[[IMG]http://img239.imageshack.us/img239/2116/litsscreen.png[/IMG]](http://img239.imageshack.us/my.php?image=litsscreen.png)

I am asking, how would I then type ANYTHING, with zero visibility?

Also, I have tried pressing the NumLock key to see if the keyboard works, and no lights come on, or switch off... So, I guess I would have to do something before that screen comes up?

Possibly something in GRUB?

I do not know what GRUB is even, just that when I boot up, before the Ubuntu splash screen pops up, that is the last thing that it says: ***Press ESC to enter GRUB in *seconds countdown here* seconds.***

---

### Post by Legace on 2009-05-09
Try this:

> **gocek said:**
> Reboot PC and select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.


And this is the real way to do the FGLRX (ATi driver) setup: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by isa.k on 2009-05-09
Thank you **Legace** :)

We have a saying back home, when roughly translated, goes something like this:

"Whoever falls into the sea (starts drowning), will even clutch at seaweed for help!"

Somehow, I feel like that guy now :roll:

Here goes nothing, I will try what you have quoted in your post.

In the name of God...

---

### Post by isa.k on 2009-05-09
**Legace**! You beauty!

Thank you so much!

I really started panicking and thought that a fresh install was iminent for a moment there!

Now to the rest of your post :)

Thank you once again **Legace** :D

---

### Post by isa.k on 2009-05-09
SOLVED :D

Thank you ever so much **Legace** :D

Here, have some popcorn :D

:popcorn:

Now onto fixing my CLP-310 and getting VirtualBox to work :D

---

