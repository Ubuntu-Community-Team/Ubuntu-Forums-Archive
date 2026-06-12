---
title: "[SOLVED] 8.04 with Sony Bravia S32A10 Tv as monitor"
date: 2008-05-10
forum: Multimedia Software
---

### Post by vector on 2008-05-10
Hi all Having problems trying to get ubuntu to work on an LCD Tv  as a monitor. This is not dual head or TV out stuff.

error from TV is PC input "out of range"
Using a standard LCD monitor I can change things then take the box into the TV room and try it on the Bravia.
I have tried changing \System\Preferences\screen resolution to 800x640 and still nothing on the TV past the Bios screen and the linux kernal start up text. After the text the screen goes blank except for the error text.

With the LCD monitor connected I have noticed that once Im logged on, the res is indeed 800x640 but the Ubuntu start up and logon looks the same as b4 ie hi res.

I feel i am not changing the res of these splash screens thus cant see to logon and thus cant get to the 800x640 mode?

Its only my theory, I am new and not sure how to fiddle with xorg.

Motherboard is a gigabyte 81g1000 (onboard graphics card) with fresh 8.04 loaded.

The bravia says it supports a number of PC modes
Vga up to 720x400
SVGA 800x600, 60-72-75hz
XGA 1024x768,  60-70-75hz
WXGA 1280x768 60hz
There are some horz freq variables too.. 
sorry I dont really understand much of this.

I expected to just plug the monitor lead into the back of the TV and it just work :)

Im not sure what the "out of range' error on the Bravia means.

any help thoughts much appreciated.

---

### Post by vector on 2008-05-14
ok two problems. one was a faulty keyboard which wouldnt allow me to use the F keys thus It looked like I couldnt get to a command terminal. Once I could access a command terminal

of great help was
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")
summary 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom (fist save the current config)
# sudo dpkg-reconfigure xserver-xorg run autodetect 

the only problem left was the splash screens.
I fixed this by editing
# /etc/usplash.conf
to a res that my TV could handle
# BTW Read what it says.. you must run sudo update-initramfs -u to update the system.. a reboot alone is not good enough. 

Im getting good res on my screen 1028x768 looks better than 1280x768 go figure. Would be nice to match the aspect ratio of the widescreen TV but Ill worry about that another day. for now its utilising about 2/3 of the TV screen, centred.

---

