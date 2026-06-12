---
title: "Virtual Terminals not displaying"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by exif on 2006-08-09
Hi,

On a fresh Ubuntu install I downloaded the nvidia-glx package and it's dependencies and changed my xorg.conf to use "nvidia" rather than "nv" I now have direct rendering but when I try to use a VT (ctrl-alt-F1) my screen just goes black and my num lock goes off.

My laptop has a nVidia 6800 go.

I've tried going through the regonfigure thing in the console and I set everything that I knew and left anything else default.

Am I missing a setting somewhere? It looks like my display can't display the console. I have 640x480 800x600 1200x800 and 1920x1200 (all are possible with my monitor and work well using the gnome resolution changer).

Any help would be great.

---

### Post by computergroove on 2006-08-09
If you change the driver back to "nv" does the VT work?

---

### Post by exif on 2006-08-10
Yes, it works like a charm. But I'd like to have direct rendering.

---

### Post by edantes on 2006-08-10
I am also using the Nvidia driver in a Dell Inspiron 8100.  The virtual terminals are displaying, but shifted two lines down. The active command line is always off the screen.  

Could the two problems be related?

---

### Post by karthikp on 2006-08-20
Same problem here. I'm on a dell inspiron 9300 and running Kubuntu Dapper. Interestingly, my graphics card is the same as exif's (Nvidia GeForce Go 6800). After installing the nvidia driver, the virtual terminals are gone.

Well, not exactly. They're located off-screen. I can blindly login and create a newfile in my home directory and it shows up. It's just that I can't see any of it...sort of an extreme version of edantes' problem.

During the installation of the nvidia-glx package, something interesting happened, too. First, I did

sudo apt-get install nvidia-glx

Then, I did,

sudo apt-get install nvidia-settings

But, it said it was going to remove nvidia-glx. I said no. Perhaps that has something to do with it?

In any case, I'd like to know if there's a config file that I can edit to adjust the position of the virtual terminal on the screen. Is that possible?

---

### Post by kxs on 2006-08-24
same problem. i work on asus A6JC laptop with NVIDIA 7300 GO. after installing nvidia-glx and changing nv to nvidia in xorg.conf direct rendering works fine but there are no terminals under Fn keys. anyone solved it? :confused:

---

### Post by exif on 2006-08-24
I've gotten mine to work by adding vga=791 to the grub kernel options and they display now, 791 is 1024x768 if i remember well. I also got them to work in 1920x1200 using vga=838 but it's pretty small writing at that resolution.

---

### Post by kxs on 2006-08-25
it`s working now with this line in /boot/grub/menu.lst :
```
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda6 ro vga=0x315 quiet splash

```
thanks :)

---

### Post by karthikp on 2006-10-21
> **exif said:**
> I've gotten mine to work by adding vga=791 to the grub kernel options and they display now, 791 is 1024x768 if i remember well. I also got them to work in 1920x1200 using vga=838 but it's pretty small writing at that resolution.

That fixed it, thanks! :-D 

So,
vga = 791 sets the resolution to 1024x768
vga = 838 sets the resolution to 1920x1200

Any suggestions on where I can find more resolution options like above? (Spare me the google/wiki suggestion - already tried it) :)

---

