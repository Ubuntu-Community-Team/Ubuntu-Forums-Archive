---
title: "How to install NVIDIA Driver 319.12 Optimus"
date: 2013-04-14
forum: Multimedia Software
---

### Post by 8YDtTGwJRd on 2013-04-14
Hi, i have an integrated(Intel HD 3000) and a dedicated(Nvidia GT 630) video card on my notebook, I installed the new drivers which are supposed tu support Optimus but i can't make them work properly because i can't configure Xorg file correctly. I should put this ```
&#8203;[COLOR=#555555][FONT=Monaco]Section "ServerLayout"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Identifier "layout"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Screen 0 "nvidia"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Inactive "intel"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Device"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Identifier "nvidia"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Driver "nvidia"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    BusID "<BusID for NVIDIA device here>"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Screen"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Identifier "nvidia"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Device "nvidia"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    # Uncomment this line if your computer has no display devices connected to[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    # the NVIDIA GPU.  Leave it commented if you have display devices[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    # connected to the NVIDIA GPU that you would like to use.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    #Option "UseDisplayDevice" "none"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Device"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Identifier "intel"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Driver "modesetting"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Section "Screen"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Identifier "intel"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]    Device "intel"[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]EndSection[/FONT][/COLOR]
``` in the Xorg file, where PCI:[COLOR=#101010][FONT=Ubuntu]01:00.0 [/FONT][/COLOR], in my case,[COLOR=#101010][FONT=Ubuntu] is the Bus ID[/FONT][/COLOR] [COLOR=#101010][FONT=Ubuntu]because, when i run lspci, i get:  [/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev a1)
When i reboot Ubuntu fails to load the drivers and i have to restore the default ones. I use Ubuntu 12.04
Thanks for your help.[/FONT][/COLOR]

---

### Post by cpu2007 on 2013-04-15
Not sure whether this is the right but because you have a dual graphic card, you might need to install bumblebee.
check it out "bumblebee" it should give you an idea whether is for you or not.

---

### Post by Mark Phelps on 2013-04-15
Here's  a link on the Bumblebee stuff:  [http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/]("http://www.omgubuntu.co.uk/2011/06/bumblebee-gets-a-ppa-brings-nvidia-optimus-graphics-switching-to-ubuntu/")

---

### Post by jawilljr on 2013-04-15
BabboDemonio, Please see [this thread.](https://devtalk.nvidia.com/default/topic/539322/linux/blank-screen-with-319-12-on-optimus-laptop/)

[Nvidia adds support for Optimus in Linux](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)

To let you know you need kernel 3.9 or higher. And those drivers are beta.

Jerry

---

### Post by 8YDtTGwJRd on 2013-04-15
thanks for your replies, i think i will give bumblebee a shot because i don't need the dedicated card after all, and these drivers, as Jerry says correctly, are still beta

---

### Post by erowlin on 2013-04-16
Hello ! 

I've wrote a little article on how to install 319.12 drivers on Ubuntu : 
[URL="http://thomas-romera.com/2013/04/16/Install-Optimus-Drivers-319-12-BETA-On-Linux/"]
http://thomas-romera.com/2013/04/16/Install-Optimus-Drivers-319-12-BETA-On-Linux/[/URL]

Hope this will help you !

---

### Post by monkeybrain2012 on 2013-04-17
Fortunately I don't have an Optimus laptop but from what I read bumblebee, when it does work, is probably better than Nvidia's intended way because by having to switch graphic card manually you have more control over which card to use, while I heard some Windows users complaining that auto switching is not very reliable even in Windows (it uses Intel while the user wants the discrete card) Also, from some posts on Phoronix 319 doesn't really support Optimus in the sense of switching graphic card on the fly, but it allows Linux users to use the Nvidia card all the time.

---

### Post by 8YDtTGwJRd on 2013-04-17
Thanks for all your support guys, i solved the problem by installing Ubuntu 13.04. This version recognises the Intel video card correctly (don't know why) so i don't have problems anymore :-)
I needed to install the drivers because i got black screens 80% of the times i turned the Pc on, but now it all seems to work.

---

