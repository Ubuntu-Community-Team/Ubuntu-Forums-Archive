---
title: "help installing fglrx driver on 64-bit ubuntu"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by ernie on 2006-01-07
i have been trying to get the 64 bit ubuntu to work on my machine for a while now and i have found out what i have to do but do not know how to do it. i need to install the fglrx drivers. i have read a couple threads about doing so but because i am a newbie i dont under stand it very much if some one could give me a step by step set of directions that would be great.. my video card is an ati radeon x850 pro

---

### Post by Tuf on 2006-01-07
There are several threads on here with step by step directions on how to do it, BUT.  The X850 is not supported by the latest ATI drivers.  I didnt know this until after I ran the installer.

I did find this link and am in the process of trying to use it [http://gentoo-wiki.com/HOWTO_X850XT_ATI_Drivers](http://gentoo-wiki.com/HOWTO_X850XT_ATI_Drivers)

I am looking for a hex editor I can use in Linux.  I may just try doing it in Windows since I know my way around better there.

---

### Post by flight_master on 2006-01-07
Tuf:

```
 sudo apt-get install khexedit
``` Will install a hex-editor for you.

ernie: Here's a tip: go to ATI's website, find the driver page, and download the latest version. Make sure to read the instructions, and instead of 'installing' the driver, select 'create distribution package' (or similar wording). Once that's done, just install the created package.


Regards,
Christian

---

### Post by Tuf on 2006-01-07
Thx Flight! You da man!

You want to read the release notes before you try to install that driver on that card.

---

### Post by ernie on 2006-01-07
i need to install these driver without using that because i cannot use the GUI if i boot into ubuntu w/o the recovery mode it will show the splash screen but once it loads the system looks up and i cannot do anything there is no error message or any thing just a white horizontial line at the top left corner and if i boot in to recovery mode all i can see is kind of a command prompt, so i have to use that to install the drivers

---

### Post by ernie on 2006-01-08
someone help please

---

### Post by timboo on 2006-01-08
Hi Ernie,
i have been having the same problem for weeks and every now and then tried. i finally succeded today. hopefully this will help you. go to the how-to at 
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
and follow its steps. none of the commands there require xwindows. you can do them from the console.
if you have problems reply back and i'll try to help. good luck with the how-to!

---

### Post by timboo on 2006-01-08
just read the second reply. in my installation it said that the driver works for  the x850 card as well.
....
RADEON X850 XT Platinum Edition (R480 5D4D),
        RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52)
....
no idea what that means, but i take it to be a hopeful sign....

---

### Post by ernie on 2006-01-08
on this site [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) one of the first things it tells me to do is to change the download directory i dont know how to do that or what to change it to. and it say to change the sources file to universe and i dont know what to do there eiether
for the most part i dont know how to do any of this 
you said you did this so can you kind of walk me though it
i am a newbie at this stuff
and also i am using a wireless network card it is a wg311t will doing this install affect this card in the begining it says something about removing a linux restricted module that has the drivers for atheros wireless cards and to configure my card in the propmt i have to put in 
ifconfig "ath0" up and a few other commands to make it work

---

### Post by timboo on 2006-01-09
hi,
it says change TO the download directory, i.e. change into the directory into which you downloaded the ati-installer file....if you're a real newbie: which editor are you using to alter your files, i.e. /etc/apt/sources.list ? 

about your wireless card: i have a broadcom wlan card that is running under ndiswrapper, but i never used a predefined package but compiled the driver myself. which means that everything was left untouched. i don't really know anything about wlan cards except my own, but if it is indeed a atheros, shouldn't madwifi work for you?

---

### Post by ernie on 2006-01-09
if i download the driver i need in windows and save it to a jumpdrive that i know works with ubuntu how can i does this what directory do i need to change to is doing it this way possiable

---

### Post by ernie on 2006-01-09
it also says i will need universe enabled in my /etc/apt/sources.list file but i dont know how to enable that 
tell me how to enable it please

it also says i can use the sources.list file it has on that page but i dont know how to do that eiether

---

### Post by ernie on 2006-01-10
i still need help thing didnt change
for some reason i dont think this would be to hard for some of you people to figure outi think it is a pretty easy task i just dont know how because i am new to all this stuff

---

### Post by Antithesis on 2006-01-10
Though I don't have the same card as you, to temporarily solve the lock up of the screen, do the following:

Restart your computer
Choose recovery mode
You should get a root terminal.
Save a copy of your X11 configuration file
cd /etc/X11
cp xorg.conf xorg.conf.old (or some other name)
now,
edit xorg.cond (I'll assume you used pico, so "pico xorg.conf"
Scroll down - for the heading "Driver" You probably have ATI right now, change it to  vesa 
Save the file (Ctrl-W), Quit pico (Ctrl X), and type "exit". You should get a login - and your machine should not freeze this time.
The vesa driver is not a real driver and offers very little in terms of performance (I believe it barely even uses your video card), but you can try to play with your configuration in graphical mode.

Hope you find your answer

---

### Post by ernie on 2006-01-11
i think i have already done that but a differnt way. i ran "sudo dpkg-reconfigure xserver-xorg" and then i changed the driver to vesa. it did not freeze when i rebooted but the screens were not readable.
should i try to do it that way or is running sudo dpkg-reconfigure xserver-xorg the same thing

---

### Post by ernie on 2006-01-11
ok i have managed to get somewhere with this 
to change the sources.list file i edited it with pico and made the new one because i was able to read it with windows but now i need to download the installer w/o a gui so how do i do that
i have it saved on my jumpdrive but cant figure out how to copy the file to my hdd

---

### Post by ernie on 2006-01-12
i have managed to get the installer downloaded and now when i run the installer it says
The distribution 'ubuntu' is not supported
removing temporary dirictory: fglrx-install

how the heck can i get around this

---

