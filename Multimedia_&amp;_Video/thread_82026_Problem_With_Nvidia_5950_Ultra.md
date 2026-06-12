---
title: "Problem With Nvidia 5950 Ultra"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by Breezy Badger on 2005-10-25
I have an Nvidia GeForce FX 5950 Ulta card and let me tell you ubuntu does not like it at all.  If you install ubuntu with this card it will skip the part where you select your resolution, then finish installing.  When it is done installing and tries to start for the first time you are screwed, it just wont work on the stock graphics setup.

Good news is that I know it will work with the Nvidia drivers installed (long story)....

So now I reinstalled ubuntu with another, older Nvidia card and it went through and worked smooth as can be.  Now I finally come to my problem....I tried to install the Nvidia drivers, worked fine on my roommates computer, got the drivers on there great..they work.

On my computer it gives an error in the file, something to do with ATI or API not matching with the kernal, I have never seen it before its weird.

I can take a shot of the screen, but I have never done it at the start up, can someone tell me how, or has anyone had a similar problem?

thanks

Badger

---

### Post by rpgcyco on 2005-10-25
Are you trying to install the NVIDIA drivers from the Ubuntu repository? If so, then disregard the rest of my post. If your trying to install from the official file from NVIDIA, then keep reading. :)

Are your friends using Ubuntu Breezy or another distro (or older Ubuntu even)?

It's probably telling you that your trying to compile the driver module with GCC4, when the kernel itself was compiled with GCC 3.4 (for various reasons).

The way to combat this is to install GCC 3.4.

```
sudo apt-get install gcc-3.4
```

Then, before you run the NVIDIA install type the following into the terminal.

```
CC=gcc-3.4

export CC
```

Hope that helps.

- Rpg Cyco

---

### Post by Breezy Badger on 2005-10-25
Thanks for the help, I have already done that.

You see the problem is this, I get this error after the drivers have been installed.  I have already had to go through the process you told me just to get them to install, now the problem I have is that they are installed and wont work due to said error

Badger

---

### Post by rpgcyco on 2005-10-25
Oh, I see, sorry about that. :)

Do you have multiple kernels installed? Maybe you accidently installed the driver while using a different kernel, than the one you wish to use?

- Rpg Cyco

---

### Post by Breezy Badger on 2005-10-25
well I have only done the intital install so far, basic...so I assume that I only have the one kernel

---

