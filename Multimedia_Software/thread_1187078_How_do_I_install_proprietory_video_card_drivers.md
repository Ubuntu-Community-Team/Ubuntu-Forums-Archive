---
title: "How do I install proprietory video card drivers?"
date: 2009-06-14
forum: Multimedia Software
---

### Post by Si Deacon on 2009-06-14
Greetings,

I have Jaunty Jackalope as sole OS on an old Dell Optiplex GX240 and all's well. Recently I aquired a Matrox G550 dual DVI card and VGA splitter cable in the hope that I could view tutorials or forum threads, such as this, on one screen whilst tinkering in a terminal emulator on the other.

I am however a complete novice, and despite my best efforts I've had no success installing drivers for the above card.

> Binary install
==============

A working installation of XFree86 4.3.0, and X.org versions 6.7.0, 
6.8.0, 6.8.1, 6.8.2, 6.9.0, 7.0.0 is required before the binaries 
can be installed.

To extract the driver files, enter the following command where 
<mga_filename> is the name of the driver file you want to extract:

  tar xvzf <mga_filename>.tgz

  cd mgadrivers

To install the drivers, run the script as "root" with no option:

  sh install.sh

The install script prompts you to install both the XFree86 2D 
driver ("mga_drv.o") and the HAL library ("mga_hal_drv.o"). Unless 
otherwise specified, these files are placed in 
"/usr/X11R6/lib/modules/drivers".

The installation script makes a back-up copy of "mga_drv.o" and, 
if it exists, of "mga_hal_drv.o". 


Above is an extract from the text file which downloaded with the drivers from Matrox.

Any help would be much appreciated...

---

### Post by gradinaruvasile on 2009-06-14
I went to the matrox site and they have only the sources for their drivers. That needs compiling and such....

Does the card work with the default ubuntu drivers?

---

### Post by Si Deacon on 2009-06-14
Yes, I have perfectly normal display, its just that its exactly the same on both monitors. Going to System/Preferences/Display gives me a 'Display unknown' message.
Detecting monitors produces no result.

I thought the drivers I downloaded were binary, or is that the same as source?

---

### Post by gradinaruvasile on 2009-06-14
> **Si Deacon said:**
> Yes, I have perfectly normal display, its just that its exactly the same on both monitors. Going to System/Preferences/Display gives me a 'Display unknown' message.
Detecting monitors produces no result.

I thought the drivers I downloaded were binary, or is that the same as source?

Did u receive an error message when opening the display configurator?

Where did u get the drivers?

---

### Post by Therion on 2009-06-14
Did you need some additional explanation on how to compile the drivers?  

If you're new to Ubuntu I can see how those instructions might leave you a little confused.

---

### Post by Si Deacon on 2009-06-14
@gradinaruvasile

No error message, downloaded the drivers from [http://http://www.matrox.com/graphics/en/support/drivers/download/?id=143]("http://http://www.matrox.com/graphics/en/support/drivers/download/?id=143")

Oops, sorry that link doesn't work lets try again,

[www.matrox.com/graphics/en/support/drivers/download/?id=143]("www.matrox.com/graphics/en/support/drivers/download/?id=143")

---

### Post by Si Deacon on 2009-06-14
@ Therion

Very probably, its seems like a steep learning curve but I'm hooked!

---

### Post by gradinaruvasile on 2009-06-14
> **Si Deacon said:**
> @gradinaruvasile

No error message, downloaded the drivers from [http://http://www.matrox.com/graphics/en/support/drivers/download/?id=143]("http://http://www.matrox.com/graphics/en/support/drivers/download/?id=143")

Seens old... the release date is in 2006...

There is a package called "matroxset" in the repos... It sais 

"This utility can be used to map heads to outputs, change the output
mode to monitor, TV, or digital flat panel, display information about
horizontal and vertical blanking, and view or modify a number of card
specific controls."

Maybe u should install it and see if it works.

In a terminal type:

sudo apt-get install matroxset

---

### Post by Therion on 2009-06-14
> **Si Deacon said:**
> @ Therion

Very probably, its seems like a steep learning curve but I'm hooked!
Alright, lets try this.  No promises, but what the heck.  Below are the instructions, [COLOR="Red"]my comments are in red.[/COLOR]

Binary install
==============

A working installation of XFree86 4.3.0, and X.org versions 6.7.0, 6.8.0, 6.8.1, 6.8.2, 6.9.0, 7.0.0 is required before the binaries can be installed.
[COLOR="Red"]We'll assume you have a qualifying installing of XServer.[/COLOR]

To extract the driver files, enter the following command where <mga_filename> is the name of the driver file you want to extract:
[COLOR="Red"]You need to have the .tgz file you downloaded in your Home folder.  If it isn't, move it there now.

Open a Terminal.

Typein: ```
tar xvzf <mga_filename>.tgz
```
Change the <mga filename> to the name of the file you downloaded.  Don't use the < > marks, though.

Next, type in:```
cd mgadrivers
```[/color]
To install the drivers, run the script as "root" with no option:

sh install.sh[COLOR="Red"]
In your Terminal type in:```
sudo sh install.sh
```
You'll be prompted for your password. Enter it and hope that the script does it groove thaaaaang.[/color]

The install script prompts you to install both the XFree86 2D driver ("mga_drv.o") and the HAL library ("mga_hal_drv.o"). Unless otherwise specified, these files are placed in "/usr/X11R6/lib/modules/drivers".

The installation script makes a back-up copy of "mga_drv.o" and, if it exists, of "mga_hal_drv.o".
[COLOR="Red"]None of the above information is particularly relavent to you.[/COLOR]

---

### Post by Si Deacon on 2009-06-14
@ gradinaruvasile

Did as you suggested, seemed to install ok but produces:

> simon@simon-desktop:~$ matroxset
Cannot open /dev/fb1: No such file or directory
simon@simon-desktop:~$ 


?

---

### Post by Si Deacon on 2009-06-14
@ Therion

Thanks for that, all went smoothly but may need tweaking:

> simon@simon-desktop:~$ cd matrox_driver-x86_32-4.4.0
simon@simon-desktop:~/matrox_driver-x86_32-4.4.0$ sudo sh install.sh
[sudo] password for simon: 
[: 43: i686: unexpected operator
install.sh: 57: function: not found
install.sh: 69: function: not found
install.sh: 78: function: not found
install.sh: 95: function: not found

Please enter the full path to your current X11R6 directory: 
Example: /usr/X11R6

/usr/X11R6
install.sh: 141: function: not found
test: 178: ./xserver/Revision: unexpected operator
[: 178: Revision 0: unexpected operator
[: 178: Revision 0: unexpected operator
[: 178: Revision 0: unexpected operator
[: 178: Revision 0: unexpected operator
[: 178: Revision 0: unexpected operator
-e \E[31mERROR: The X server drivers included in this installation package
-e        do not support the current version of your X server.

simon@simon-desktop:~/matrox_driver-x86_32-4.4.0$ 


So do I upgrade or possibly downgrade my X server....?

---

### Post by gradinaruvasile on 2009-06-14
type:

man matroxset

It seems u have to give the program the framebuffer device and stuff...

Unluckily i have nvidia card so i cant help here.

But do the following:

in a terminal

cat /var/log/Xorg.0.log | grep /dev 

i, at least, have a line with Video bus device /dev/input/event5
if u have some output, like /dev/input/event5 (in my case)

do

sudo matroxset -f /dev/input/event5

substitute /dev/input/event5 with yours (if u have one)

---

### Post by gradinaruvasile on 2009-06-14
Wait, i may have been wrong with the /dev/input stuff. It must be /dev/fb1 or 0

Found something interesting here:

[http://ubuntuforums.org/showthread.php?t=830519]("http://ubuntuforums.org/showthread.php?t=830519")

---

### Post by Si Deacon on 2009-06-14
@ gradinaruvasile

Ah well, just tried it anyway, results below:

> simon@simon-desktop:~$ cat /var/log/Xorg.0.log | grep /dev
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
simon@simon-desktop:~$ sudo matroxset -f /dev/input/event3
[sudo] password for simon: 
ioctl failed: Invalid argument
simon@simon-desktop:~$ 


Appreciate your time and effort. I'll check that thread out too, thanks.

---

### Post by gradinaruvasile on 2009-06-14
> **Si Deacon said:**
> @ gradinaruvasile

Ah well, just tried it anyway, results below:



Appreciate your time and effort. I'll check that thread out too, thanks.

I was saying i was wrong about the /dev/input devices.
U have there a lot of /dev/dri/card lines. Most likely those are what are u looking for.

But i think that link will help u more.

---

