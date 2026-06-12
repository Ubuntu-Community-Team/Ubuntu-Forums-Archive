---
title: "Hardy Heron ATI x1400 slow"
date: 2008-04-25
forum: Multimedia Software
---

### Post by JayeD on 2008-04-25
Hi, I upgraded to Hardy from Gutsy last night and trying it this morning I've found that it is really slow. I tried opening up Stellarium and I have to sit and wait before anything I do is done. I tried getting rid of the proprietary ati driver and then things are even worse. Scrolling in firefox just takes an age.

I'm running Hardy on a Dell 6400/E1501(?) with an ATI x1400 mobility, Under Gutsy everything was nice and smooth. I don't use any of the advanced desktop effects, however I did under Gutsy and they were very smooth. Any ideas on how to fix it? I'm kinda regretting the upgrade now.

---

### Post by xtremesupremacy3 on 2008-04-25
Hey there, your not the only person to experience this.
I use the same laptop as you and same ATI and have the same slowness. With me I noticed it going relatively well but a game just is slowmo...From what I can tell the Hardy release is far from perfect.

Just to check though, have you tried ```
glxgears
```?

with me that runs perfect, I'm running AWN, screenlets, compiz and the CPU and RAM seems normal, so I am with you here. Something isn't right:mad:

---

### Post by JayeD on 2008-04-25
Hi, I just got back from work and found that xserver-xgl was installed. It must have still been there from Gutsy or something. Anyway, uninstalled that and all seems dandy.

glxgears was about 100fps before, now it's around 2000, and stellarium runs properly now too. The whole desktop is far more responsive. Hope that helps anyone.

---

### Post by mjantz on 2008-04-26
I have an ATI X1400 and I am having the exact same problem. However, if I uninstall xserver-xgl, the X server won't boot. When I try to log in, I get a message saying my session lasted less than 10 seconds, and it gives me some details in the ~/.xsession-errors file. This file says:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
/usr/local/bin/startxgl.sh: 2: Xgl: not found

(gnome-session:9046): Gtk-WARNING **: cannot open display: :1


Is anybody else getting these errors, and does anybody know what I need to do to be able to remove xserver-xgl?

---

### Post by peter_pilgrim on 2008-05-31
> **JayeD said:**
> Hi, I just got back from work and found that xserver-xgl was installed. It must have still been there from Gutsy or something. Anyway, uninstalled that and all seems dandy.

glxgears was about 100fps before, now it's around 2000, and stellarium runs properly now too. The whole desktop is far more responsive. Hope that helps anyone.

Removing xserver-xgl causing Compiz to fail. 

So how do you get Compiz back again?

Ta:popcorn:

---

### Post by JayeD on 2008-05-31
> **peter_pilgrim said:**
> Removing xserver-xgl causing Compiz to fail. 

So how do you get Compiz back again?

Ta:popcorn:

Well, I don't actually like Compiz so I switch it off, but if you edit xorg.conf you can set the composite option to 1 instead of 0. Worked for me, but like I say, I turn it off anyway.

Section "Extensions"
	Option		"Composite"	"1"
EndSection

---

