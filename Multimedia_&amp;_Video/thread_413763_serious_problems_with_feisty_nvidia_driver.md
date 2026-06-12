---
title: "serious problems with feisty nvidia driver"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by slickwilly on 2007-04-19
Ok just upgraded to Feisty, please excuse any typos i can only sometimes see my screen, otherwise its a hash, or has tons of artifacts and does not refresh properly :(
It's a problem with the 9631 driver, I know because I had the very same thing happen when I tried to download from Tselliots site a few months back for Edgy.  I have a Sony Vaio with an onboard Geforce4mx, which isn't listed as a'legacy' card, but seems to not function just the same, lovely :(  Ok I can no longer see what I'm typing at all, here is what I need, is there a way to roll back to Edgy's Nvidia driver without completely unistalling Feisty?  Or if you folks think I should try the legacy driver, how do I uinstall this driver and install it from the commandline.  Looking forward to checking out Feisty, but first I have to be able to see my screen...

Slick

---

### Post by slickwilly on 2007-04-19
Have a little more info, cant seem to go to the KDE menu without the computer rebooting, so I took the opportunity to get some chipset information.
Looks like the chipset is :  nforce-a7n266vx
If anyone out there has similar problems, and a solution, please let me know, in small words please I wont be able to refer back to this, as I'll have to reboot in safe mode and work from the command line.
Oh speaking of safe mode, when I brought up that menu last time, I had 2 other kernels still on my machine, however Edgy's GLX was working just fine, I'm wondering if perhaps that could be contributing to things being squirrely, but then again I had this exact same problem before with this version of the driver, so probably not :(


Slick

---

### Post by K.Mandla on 2007-04-19
I was looking at [this list]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html") and I think your card might fall into the same bracket as mine -- a 440 Go. You might try patching the driver against the 2.6.20 kernel and see if you get better results.

[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)

It might not apply since yours is an nforce set, but it's worth a try.

---

### Post by slickwilly on 2007-04-19
I got the legacy driver installed and now at least I can see my computer, yay!
I'll probably stick with this, as I really dont use much in the way of graphics anyhow, save
for playing NWN now and again.
Last time this happened, I got annoyed with Ubuntu and tried out Sabayon linux, and the 9631 driver (which was included on the release dvd) worked like a champ, however Gentoo is seriously not my cup of potatoes, yuck.  My point being, would be nice if this is a known problem if the Devs could perhaps fix it???  Just a thought, might not be a good one, but at least it's mine :)

Thanks for the suggestion btw, i've saved the relevant pages in case I ever have rampant patience, time and energy and decide to go ahead and plunge into patching the kernel. :)

Thanks!

Slick

---

### Post by kapampa on 2007-04-22
I've got same exact problem.. I can see my screen but I cannot enable the feisty restricted driver for Nvidia without making the xserver crash on startup. I've got same f***king Nvidia Geforce 4 Mx 
neither did work on xp!! I hope you guys fix the problem..
Ps. Ubuntu is GREAT!!!!!!!

---

