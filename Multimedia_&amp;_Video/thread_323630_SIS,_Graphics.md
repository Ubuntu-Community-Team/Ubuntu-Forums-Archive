---
title: "SIS, Graphics"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by abshirf2 on 2006-12-22
hello all, :)

can you tell me what this means: i type the command lspci and i get the following as my graphics card:

0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

and when i do this code: the xconfig.... i get:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Does it mean i am using vesa or SIS as graphics: Also with a few other commands i can change the card to ati, ....and a lot more...does it mean i have all these drivers.

Finaly, what would people suggest i do to get 3ddesktop and 3d acclerationa and direct rendering to work. 

all help will be appreciated. :)

---

### Post by lifespurpose on 2007-04-24
This appears to be a serious fault with Ubuntu (and with every Linux distro I have tried, altho that's not many): VERY poor video support. And I don't mean fancy video cards, I mean plain vanilla basic video. I have integrated SiS, which is fine for my office work. But like so many here on this forum have complained, the "set screen resolution" gadget has only 4 choices and only ONE vertical refresh rate, which is INCOMPATIBLE with some of the resolutions (I tried 800x600 @ 86 Hz and couldn't see anything; I had to reboot to restore my vision). I have gone around and around and can't find any way to directly adjust these parameters (The idea of having to text-edit an inscrutable config file (with only a dim concept of what the h_ I am doing) is incredibly primitive. Linux will never amount to anything as long as it's stuck in the 19th century.)
I've seen references to Gconf but so far I haven't found it in my Gnome desktop. Where do they hide this stuff so well? And why?
I suppose if I stuck with this without going insane, I could get to thinking this is normal. As it is, I boot into Linux only occasionally when I feel like have a very frustrating experience. Right now I'm stuck on 1280x1024 @ 86 Hz and can barely read this as I type. If I had had my LCD hooked up when I upgraded to Dapper today, I'm not sure if I could see anything. It won't go above 1024x768 @ 60 Hz. My xorg.conf file says "generic adapter and generic monitor." Breezy did a better job identifying and adjusting to my equipment. So LTS is a step back. A HUGE step back.
Is the Ubuntu moderater listening? Why are such fundamental inadequacies still tolerated?

---

### Post by masked_marsoe on 2007-04-25
The fault lies just as much with SIS (if not more). The SIS graphics cards are almost completely useless on linux, as **they don't have** OpenGL. I'm cursed with the same thing.

Change your driver to read "sis".

That's all you can really do.

---

### Post by az on 2007-04-25
Even in windows (with proper drivers), the SIS cards have poor performance.  You don't have a lot to work with.

---

### Post by az on 2007-04-25
> **lifespurpose said:**
> This appears to be a serious fault with Ubuntu (and with every Linux distro I have tried, altho that's not many): VERY poor video support. ...

 Linux will never amount to anything as long as it's stuck in the 19th century.)
...
Is the Ubuntu moderater listening? Why are such fundamental inadequacies still tolerated?

First of all, it's a bug.  Get over it.  

It's a chicken and egg situation.  Lots of hardware is still only supported for windows.  The hardware manufacturers/vendors do not have the inclination to offer support for linux because the marketshare is not there yet.  If you've been around linux for any significant amount of time, you would realize how fast this is changing.  But the fact is, until something like ten percent of computer users use free-libre software, hardware manufacturers won't take notice.

Why isn't it fixed yet?  Because you and may others have not participated enough to fix that bug.

---

