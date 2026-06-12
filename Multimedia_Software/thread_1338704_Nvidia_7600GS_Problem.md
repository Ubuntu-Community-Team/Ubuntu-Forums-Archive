---
title: "Nvidia 7600GS Problem"
date: 2009-11-26
forum: Multimedia Software
---

### Post by Jerry N on 2009-11-26
My Nvidia GeForce 7600GS works fine with Windows but most of the Linux "live disk" distributions I have tried give me only garbage on the display.  With Ubuntu, I can boot the live disk in the safe mode and the video works, albeit at low resolution.  I can then install Ubuntu on the hard drive and let it install the Nvidia driver.  From that point, it seems to work like normal, even allowing me to use dual displays with only about an hour of fiddling to get them the way I want.  Is this a known problem with the 7600GS?  I know the Nvidia 5500 (AGP) does not have this problem.

Jerry

---

### Post by Jerry N on 2009-11-27
Bump

---

### Post by PariahVayne on 2009-11-27
What kind of monitor do you have?

---

### Post by Jerry N on 2009-11-27
Two monitors, Samsung 19 inch on the DVI connection and Samsung 17 inch on the VGA connection.  Computer is dual core AMD3800 with 2gb DDR2. I got Ubuntu 9.04 to work (with both monitors) with a safe boot on the live CD.  After installation to the HD, I let it load the appropriate nvidia driver and then everything was OK.

I haven't been able to display anything but garbage with puppy linux.  I could get PartitionMagic 4.3 to work at 600 x 800 resolution -- good enough for Gparted.  LinuxMint live CD displays garbage.  I don't know that I need a solution, I would just like to know what is going on.  

Jerry

---

### Post by pmiller1 on 2009-11-27
i just starterd useing ubuuntu with a niniv nb and 8600 gt 1 gig  had to go to niviv sight and look for drivers then start with sound vid still no tright cant find a text/ html decoder that will work with Div x web player video is jummpy  im new at this stuff so maby good maybe not  but i miss stagev and a couple of others that use the same playergood hunting pk

---

### Post by inobe on 2009-11-27
> **Jerry N said:**
> Two monitors, Samsung 19 inch on the DVI  I would just like to know what is going on.  

Jerry

the live cd is no comparison to an actual hard drive install, first' you cannot enable the nvidia driver in system> administration> "hardware drivers" because you need to reboot in order to complete the process, then of course all is lost when a live session is restarted !

try the wubi install, it installs like a program in windows, if you don't like it you can remove it later from "add and remove programs"

---

### Post by oldfred on 2009-11-28
When I set up this computer about 3 years ago I had the 7600gts version. It was the gs with the gt memory or something. I had issues with most upgrades every 6 months getting the drivers to work but it worked with every version. About 6 months ago I heard a pop but the computer kept working. Next morning my wife said computer was not working and it was dead as a doornail. It turned out to be bad capacitors on the video card and I found pictures on the Web that looked just like my caps with the tops just opened. Now I am running a 9600GT and it installed and worked with the 7600 configuration without any problem. Installs of 9.10 worked but I immediately downloaded the nvideo drivers.

---

### Post by mc4man on 2009-11-28
> you cannot enable the nvidia driver in system> administration> "hardware drivers" because you need to reboot in order to complete the process,.......

In 9.04 & 9.10 you can install and load restricted drivers while using the live cd.
(9.10 has nvidia drivers on the live cd, but I always use the repo ones anyway.

Just boot to live cd (easiest not to enter a username or password, just push enter on keyboard), and get an Internet connection.

Then in System -> Software sources, enable all the repo's under the main Ubuntu Software tab.
Disable the 'cdrom' source, click close and reload.

Install the restricted drivers, when done, **log out** and after logging back in the drivers will be loaded. ( if you didn't enter a username and password then then login name is ubuntu, the password is enter key on keyboard.

Actually gives you a good idea how they'll perform on a real install

---

### Post by inobe on 2009-11-28
> **mc4man said:**
> In 9.04 & 9.10 you can install and load restricted drivers while using the live cd.
(9.10 has nvidia drivers on the live cd, but I always use the repo ones anyway.

Just boot to live cd (easiest not to enter a username or password, just push enter on keyboard), and get an Internet connection.

Then in System -> Software sources, enable all the repo's under the main Ubuntu Software tab.
Disable the 'cdrom' source, click close and reload.

Install the restricted drivers, when done, **log out** and after logging back in the drivers will be loaded. ( if you didn't enter a username and password then then login name is ubuntu, the password is enter key on keyboard.

Actually gives you a good idea how they'll perform on a real install


thanks :)

---

### Post by PariahVayne on 2009-11-28
> **Jerry N said:**
> Two monitors, Samsung 19 inch on the DVI connection and Samsung 17 inch on the VGA connection.  Computer is dual core AMD3800 with 2gb DDR2. I got Ubuntu 9.04 to work (with both monitors) with a safe boot on the live CD.  After installation to the HD, I let it load the appropriate nvidia driver and then everything was OK.

I haven't been able to display anything but garbage with puppy linux.  I could get PartitionMagic 4.3 to work at 600 x 800 resolution -- good enough for Gparted.  LinuxMint live CD displays garbage.  I don't know that I need a solution, I would just like to know what is going on.  

Jerry

Hmmmmm, it may be a card issue. I bought a 7300 GT a while ago that had a whole ton of problems with Windows XP and then just died. So I stuck with my ancient 5700. It's old but it works. Tbh unless you can't play some game because the card is too slow I would stick with the 5500 AGP. They are pretty reliable compared to the newer Geforce stuff.

---

