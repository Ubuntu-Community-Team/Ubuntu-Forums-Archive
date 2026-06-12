---
title: "ATI need help with the screen going black."
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by Maniac Matt on 2007-08-27
Hi i just got a new ATI card, to be more specific an ATI VisionTek x1550, and when i loaded Kubuntu, when i got to the x-server (log in screen) it loads and i see a terminal, but then it changes to a black screen with a little blinking underscore. 

So then i tried to reinstall Kubuntu, and after the fresh install, the same thing happens...any suggestions?


thanks, Matt.

---

### Post by hooplah on 2007-08-27
You haven't tried just typing in startx , have you? Well, it probably will just give you that blinking underscore anyways. If you want any further help, you're going to have to give more information, for example, post you're xorg.conf contents into your next post, to help better diagnose you're issue.

Regards,
Max

---

### Post by w4ett on 2007-08-28
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "vesa" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct ATI  proprietary driver.

Good Luck

---

### Post by Maniac Matt on 2007-08-28
alright... i will see what i can do.. but i need to re-install kubuntu..for i am trying sabayon..but i am not enjoying "portato" for i am so use to adept.

---

### Post by Maniac Matt on 2007-08-28
> **w4ett said:**
> From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "vesa" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct ATI  proprietary driver.

Good Luck



well.. i tried running ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and it says that there was a fatal error and no screens were found... same thing happens when i run startx ...guess i will stick with Gentoo's Sabayon, for a bit or atleast until gutsy is released.. perhaps it will work then.

thanks.

---

### Post by w4ett on 2007-08-28
Why not post your:

xorg.conf
lspci
Xorg.0.log

and let us take a look at the error.

---

### Post by Maniac Matt on 2007-08-29
the only way that i can enter any commands is in recovery mode...so, perhaps i can when i have a little bit of time.. if i copy them by hand.. but it is do able.. ill see what i can do tomorrow.

thanks. matt

---

### Post by w4ett on 2007-08-29
You can also copy the Xorg.0.log and the xorg.conf to a flash drive via the terminal....

---

