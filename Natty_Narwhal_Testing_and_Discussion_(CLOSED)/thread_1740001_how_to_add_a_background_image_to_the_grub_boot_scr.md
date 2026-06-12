---
title: "how to add a background image to the grub boot screen"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-04-26
has anyone done this with natty. and if so how. tks

---

### Post by VanR on 2011-04-26
Try this thread. It worked for me.
[http://ubuntuforums.org/showthread.php?t=1718521&highlight=GRUB+Background](http://ubuntuforums.org/showthread.php?t=1718521&highlight=GRUB+Background)

Basically I Copy and pasted an image (jpg I think) into the /boot/grub file (you have to be root)
Open a terminal and type sudo update-grub. Done.

But beware for some reason some images just don't want to work. So you may have to change them until you find one that will work.

---

### Post by ranch hand on 2011-04-26
Use RGB images.  I find that if you resize them to no larger than your screen pixels it is best too.  Half sized ones work fine too.

.jpg and .png work fine and what ever that silly format that we used in grub-legacy.

Check your /etc/default/grub to make sure it has;
[quote]
GRUB_BACKGROUND=/boot/grub/desktop-grub.png
[/quot]
or something like that.  That is from mine, I use a .png, and I had to add it as the file was not updated as I wouldn't let it.

I think the default language allows for several .whatevers.

---

### Post by rburkartjo on 2011-04-26
tks i have a question though how do i copy and paste into the grub i know i need to open grub with gksu gedit /etc/default/grub but how do i copy the background into grub as root. tks

---

### Post by cipherboy_loc on 2011-04-26
Try this for the copy and paste (didn't read the link but don't understand what you are doing):
```

gksudo nautilus

```


Cipherboy

---

### Post by ranch hand on 2011-04-26
> **rburkartjo said:**
> tks i have a question though how do i copy and paste into the grub i know i need to open grub with gksu gedit /etc/default/grub but how do i copy the background into grub as root. tks
You are just dumping the image into /boot/grub.  Yup, in with everything else.  It does need the name "desktop-grub.<your preference> or you need to change the line in your /etc/default/grub to match the name you choose.

I am, for instance, going to change that to "menu.png".   I already have a number of images with that name (menu.png.a, menu.png.b, etc) so that I can quickly change them on a whim or to more appeal to someone I am showing Linux to.

I will put them in a folder  /boot/grub/Holding.  I have a habit of using that folder name in several places where changes can be made and I want several pre-made options.

---

### Post by thug777 on 2011-04-27
This worked on 10.10:

Open the terminal and run:
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Then logout, and you’ll see an Appearance window pop up.
Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command
to prevent the Appearance window from opening at the GDM screen every time.

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

---

### Post by wojox on 2011-04-27
> **thug777 said:**
> This worked on 10.10:

Open the terminal and run:
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Then logout, and you’ll see an Appearance window pop up.
Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command
to prevent the Appearance window from opening at the GDM screen every time.

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

That's GDM not Grub.

---

### Post by thug777 on 2011-04-27
> **wojox said:**
> That's GDM not Grub.
Sorry, i missed that...

---

### Post by wojox on 2011-04-27
> **thug777 said:**
> Sorry, i missed that...

Your answer still works for 11.04 as well. :P

---

### Post by Harry33 on 2011-04-27
The grub background image looks good if it has the same basic colors as your Plymouth theme has.
And as far as gdm is concerned, it looks good to have the same background image in the gdm and desktop.

And, the best would be to have a xplash (no Plymouth at all).
Then you could use the same background throughout booting process (grub => xsplash => gdm => desktop).

---

### Post by rburkartjo on 2011-04-27
good info tks ya'll

---

### Post by Baldrick_NZ on 2011-04-28
> **ranch hand said:**
> 
Check your /etc/default/grub to make sure it has;
[quote]
GRUB_BACKGROUND=/boot/grub/desktop-grub.png
[/quot]
or something like that.  That is from mine, I use a .png, and I had to add it as the file was not updated as I wouldn't let it.

I tried this (though changed the pic name) with a .png file sized to fit my 1920/1080 screen, and ran sudo update-grub in terminal, then rebooted, but still I get the black grub background upon reboot.

I also run startup-manager - could that be a source of conflict?

Maybe something to do with my nVidia drivers?

I actually had to add the line 
```
GRUB_BACKGROUND=/boot/grub/desktop-grub.png
``` into the grub file. Does it matter where this line is actually placed in the script?

Any help would be much appreciated. Cheers.

---

### Post by DougieFresh4U on 2011-04-28
> **VanR said:**
> 

Basically I Copy and pasted an image (jpg I think) into the /boot/grub file (you have to be root)
Open a terminal and type sudo update-grub. Done.


 Worked great and so easy.
Thanks

---

