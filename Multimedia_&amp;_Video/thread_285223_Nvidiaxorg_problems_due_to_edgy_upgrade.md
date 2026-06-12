---
title: "Nvidia/xorg problems due to edgy upgrade"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by DigitalDuality on 2006-10-26
ok i upgraded to edgy.

and now.. i have no x.  nothing at all just all command line.  i have a 5500.  my xorg.conf looks right, the drivers are installed properly it seems.

everytime i go to startx i get the follow:

using config file /etc/X11/xorg.conf
failed to load module nvidia (module does not exist, 0)
No drivers available.

any idea of what to do and how to do it?

---

### Post by Perfect Storm on 2006-10-26
Try with:
```
sudo aptitude install nvidia-kernel-common
```

---

### Post by DigitalDuality on 2006-10-26
no avail there.  sorry.  the error message with starting x is the same.

---

### Post by Perfect Storm on 2006-10-26
You have nvidia card then I presume.
What about trying Nvidia binary driver instead? Or is it a no-no?

---

### Post by tseliot on 2006-10-26
and you can also try this:
```
sudo aptitude install linux-generic nvidia-glx
```

and restart your computer (so as to be sure to boot in the right kernel)

---

### Post by DigitalDuality on 2006-10-26
linux generic is already up to it's latest version.  glx is as well.

i'm not really concerned about whether the driver is binary or not, i'm just concerned about getting this puppy working.

edit:  now when i startx i'm getting

NVIDIA: No match device section for instance BUS ID PCI:1:10:0 found
No devices detected

2nd edit: after dpkg-reconfigure xserver-xorg  i'm getting this error:

NVIDIA: No match device section for instance BUS ID PCI:1:10:0 found
No devices detected

Fatal server error:
no screens found

---

### Post by Kazuhiro on 2006-10-28
make sure xorg-server is installed.

---

### Post by Philodox on 2006-10-28
Try commenting out the bus id in the device section of your xorg.conf.  When I upgraded to the edgy beta I noticed that those lines were missing.

---

### Post by weiersc on 2006-10-28
I had the same problem last night after upgrading from dapper to edgy.

I basically did the following:

1. sudo apt-get install nvidia-glx nvidia-kernel-common

This indicated that everything was fine and properly installed.

Then I said

sudo nvidia-glx-config enable

That solved my problem. I restarted Gnome with
sudo /etc/init.d/gdm restart

and everything is running fine now.

(I basically followed the instructions given at the unofficial ubuntu guide for edgy eft --> I've been told that should the above not enable the new driver, you can enable it manually by opening the X config file:

sudo gedit /etc/X11/xorg.conf

and replacing "nv" with "nvidia"

---

### Post by rouben on 2006-10-28
> **weiersc said:**
> I had the same problem last night after upgrading from dapper to edgy.

I basically did the following:

1. sudo apt-get install nvidia-glx nvidia-kernel-common

This indicated that everything was fine and properly installed.

Then I said

sudo nvidia-glx-config enable

That solved my problem. I restarted Gnome with
sudo /etc/init.d/gdm restart

and everything is running fine now.

(I basically followed the instructions given at the unofficial ubuntu guide for edgy eft --> I've been told that should the above not enable the new driver, you can enable it manually by opening the X config file:

sudo gedit /etc/X11/xorg.conf

and replacing "nv" with "nvidia"
This makes a lot of sense: it's not enough to just have the driver packages installed. Both nVidia and ATI drivers install GL libraries that conflict with their MESA counterparts. That's what happened to me when I tried to move away from the downloadable "generic" ATI drivers to Ubuntu's packages (the big advantage there is that I don't have to rebuild my binary drivers every time I upgrade my kernel).

Top cut a long story short, I ended up forcibly copying the necessary library files over, but eventually figured out the proper way to do it. Don't remember it now, but it was something similar to the above.

In any case, I hope you get your problems resolved.

---

### Post by ulriks on 2006-11-04
I had problems after upgrading nvidia-glx

After messing about a bit, this is what I did:

Log in using the console

sudo apt-get install nvidia-glx nvidia-kernel-common

Which also showed that everything was fine and properly installed.

Running

sudo nvidia-glx-config enable

Did not help, as the module apparentlz could not be loaded...

Soo... my minimal knowlegde of Vi came in handy...

I said 

sudo vi /etc/X11/xorg.conf 

and replaced "nv" with "nvidia" (after going to insert mode, by pressing the key 'i')

saved and left by typing ':wq'

After this 

sudo nvidia-glx-config enable

still complained, but this time about checksums and told me what to do.

I did as told, ran

sudo nvidia-glx-config enable

which finally worked...

I also had problems with missing displayconfig, see [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1643058]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1643058")

Ofcourse everything crashed when my screensaver ([Electris Sheep]("http://electricsheep.org/")) started

---

### Post by tseliot on 2006-11-04
> **ulriks said:**
> I had problems after upgrading nvidia-glx

After messing about a bit, this is what I did:

Log in using the console

sudo apt-get install nvidia-glx nvidia-kernel-common

Which also showed that everything was fine and properly installed.

Running

sudo nvidia-glx-config enable

Did not help, as the module apparentlz could not be loaded...

Soo... my minimal knowlegde of Vi came in handy...

I said 

sudo vi /etc/X11/xorg.conf 

and replaced "nv" with "nvidia" (after going to insert mode, by pressing the key 'i')

saved and left by typing ':wq'

After this 

sudo nvidia-glx-config enable

still complained, but this time about checksums and told me what to do.

I did as told, ran

sudo nvidia-glx-config enable

which finally worked...

I also had problems with missing displayconfig, see [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1643058]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1643058")

Ofcourse everything crashed when my screensaver ([Electris Sheep]("http://electricsheep.org/")) started
next time use "nvidia-xconfig" instead of "nvidia-glx-config enable".

It's all explained in my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

