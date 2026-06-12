---
title: "Nvidia GeForce 6800 no TV detected via S-Video"
date: 2010-05-21
forum: Multimedia Software
---

### Post by lil_niles on 2010-05-21
I have thrown together a frankenstein of spare parts to stream video onto my TV. The GPU is a NX6800GS (geforce 6800). I have used the restricted driver tool to intsal the recommended driver. The VGA output works fine.

My problem is that when using the nvidia tool to set up my TV through S-Video on the graphics card, the TV is not detected. This puts me at a dead end, as every how to guide on this forum assumes the nvidia control panel can detect the TV. Can i force video to play over the S-Video port? Do i need some magical unicorn drivers for the card? Any help is appreciated (even a simple "this setup will never work").

---

### Post by lil_niles on 2010-05-21
just to clarify, i'm using a fresh install of Ubuntu 10.04, and there are three available drivers through Ubuntu's restricted driver tool. i chose the driver labeled "recommended." i've kept searching around and i'm still at a dead end here

---

### Post by lil_niles on 2010-05-21
Still searching for a fix, and i came across this thread: [http://ubuntuforums.org/showthread.php?t=785166&highlight=s-video+6800](http://ubuntuforums.org/showthread.php?t=785166&highlight=s-video+6800)

seems like a very similar problem to mine (with no solution of course). i'll try a complete reinstall later on today if i get no other suggestions.

---

### Post by Jose Catre-Vandis on 2010-05-21
What resolution will your TV run at? Drop the resolution for your vga output to that resolution and then see if you can get TV going. You might need to try 640x480, 800x600,1024x768. Try also with Clone first. Once you get it going like that you can fiddle away to get where you want to go.

Also will you TV work if it is the only output device? Disconnect vga and see what happens?

---

### Post by lil_niles on 2010-05-21
> **Jose Catre-Vandis said:**
> What resolution will your TV run at? Drop the resolution for your vga output to that resolution and then see if you can get TV going. You might need to try 640x480, 800x600,1024x768. Try also with Clone first. Once you get it going like that you can fiddle away to get where you want to go.

Also will you TV work if it is the only output device? Disconnect vga and see what happens?

thank you for the reply! I just now tried booting with only the S-video connection, and the TV remained black (the screen flashed white for a split second when i powered on my computer). I then connect the VGA monitor (a 5 year old dell CRT) and found that ubuntu had booted to the shell and had not started the X server.

i rebooted with the VGA input and set the res to 640x480 and there was absolutely no change in the lack of TV detection.

Remember, i've got my tv connected via S-Video and i'm getting zero detection of any kind whatsoever of a tv being connected. i've got to go to work but now but i'll check back on this thread later and continue fiddling. thanks again for any help

---

### Post by Jose Catre-Vandis on 2010-05-21
What are you seeing in nvidia-settings? Is everything OK there?

Also you could try:

1. Have vga and svideo outputs connected.
2. Stop your xserver:
2a.Switch to a console (CTRL+ALT+F1/2/3) and login
2b.**sudo service gdm stop**
2c **sudo nvidia-xconfig**
2d restart the xserver **sudo service gdm start** or simply reboot

---

### Post by lil_niles on 2010-05-22
> **Jose Catre-Vandis said:**
> What are you seeing in nvidia-settings? Is everything OK there?

Also you could try:

1. Have vga and svideo outputs connected.
2. Stop your xserver:
2a.Switch to a console (CTRL+ALT+F1/2/3) and login
2b.**sudo service gdm stop**
2c **sudo nvidia-xconfig**
2d restart the xserver **sudo service gdm start** or simply reboot

Ok, when running the command "sudo nvidia-settings" i get this error:

ERROR: The control display is undefined; please run 'nvidia-settings --help' for usage information.

If i run this command while X is running, then it opens up the nvidia control panel, and everything is the same as it has been. nothing looks goofy in here, just no TV is detected. To clarify, i only get the error with this command when the X server is turned off from your steps.

Then i followed steps 2b-c but on step 2c, i got a warning saying the data in my xorg.conf file was incomplete. I rebooted before copying the warning exactly, and after following your steps again now it reads:

Using X configuration file: /etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Is there a setting i need to add to my xorg.conf file to enable svideo and/or detect my tv?

---

### Post by lil_niles on 2010-05-22
I went for a reinstall, still had no progress with the nvidia card. I've moved on to an old radeon X1300 (the pci-e version). Now with the new ATI card, if i plug in S-video and nothing else, it works! well almost works. I can see the post just fine, then when it goes to the splash loading screen, still fine.

when i get to the login screen, i see many white horizontal lines covering the screen. i've written an xorg.conf file to try various resolutions at 60hz refresh rate (this is the rate found in the manual for the TV). 

After much fiddleing and rebooting, i tried booting from the ubuntu 10.04 CD. this does pretty much the same deal; post is fine, splash is fine, then seriously messed up from the splash on. 

If i can't solve this by tomorrow, my media server will happily run windows xp. I know for a fact i can have xp up and running and doing exactly what i want in a matter of hours. I hate to go there, but i will if forced.

---

### Post by lil_niles on 2010-05-22
You can mark this thread as solved (whoever has the power). The solution? I installed windows xp pro. At the risk of sounding like an ***, it worked perfectly right from word "go."

I will come back to this issue of s-video not working (on 3 different graphics card, one of which is nvidia) and i will figure out why it wasn't working. I still envision a day where all of my desktops and laptops will be running linux...

Thanks for the help too, i at least learned a bit more about X and how it works (and how to tweak it a bit).

---

### Post by Jose Catre-Vandis on 2010-05-22
Sorry you couldn't get it working with Linux. If you want to try something different, download Geexbox 1.2.4 (not, for now, the new 2.02 version) I had excellent results from this live cd just recognising everything and running two screens in clone view off my 6800 (AGP).

You can make this thread solved yourself, see Thread Tools

---

### Post by DJYoshaBYD on 2011-08-01
ok ok ok.. dont flame me.. lol.. i KNOW this is an old thread.. but this is EXACTLY the same issue I had, doing the same exact thing, on the same exact version of Ubuntu.....

I changed the S-Video cable.. instantly fixed the problem.. I have run into this before where the svideo-to-rca adapter works for some cards, and not others.. was using it with the adapter, then my dumb *** checked to see if my tv had an s-video in, and it did.. I changed the cable, and it worked just fine..

Just something to suggest for a fix, in case this happens to someone else. :D

again, sorry for the resurrection, but at least I found a solution..

---

