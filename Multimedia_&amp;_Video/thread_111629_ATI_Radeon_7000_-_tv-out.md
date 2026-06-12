---
title: "ATI Radeon 7000 - tv-out"
date: 2006-01-02
forum: Multimedia &amp; Video
---

### Post by christooss on 2006-01-02
Has anyone of you working tv-out on Ati Radeon 7000?

I would really appriciate you anwsers

Bye

---

### Post by Chris Tucker on 2006-01-05
i have it working, but its not right, skewed and off center, cant read anything.. im trying to get it working with the proper ati or radeon driver or maybe even fglrx , but currently only the vesa driver outputs right, and you loose DRI then and a lot of performance goes down the drain.

---

### Post by kurushi on 2006-01-05
Can you please, tell us how to configure the 'vesa' driver to make ati tv-out work, please?

---

### Post by Chris Tucker on 2006-01-06
well i had to do nothing for that, besides connect my tv to the S-Vid port and sudo dpkg-reconfigure xserver-xorg and when it asks to choose from the list the type of card (ati is automatically chosen..) just pick vesa, and set everything else, the vid mem on all 7000's should be 64mb, so the number in Kb of your memory is 65536. when at monitor selection, choose "medium" and set your default to 800x600@60hz, then it should just well.. work!

---

### Post by jamesdodd on 2006-04-18
I did:

dpkg-reconfigure xserver-xorg
and follow all default steps answering everything for your monitor (not TV yet)

then:


> sudo cp /usr/etc/X11/xorg.conf /usr/etc/X11/xorg.conf.bak
> sudo gedit /usr/etc/X11/xorg.conf

and scroll down to devices and **replace** the **ati** with **vesa**

save and close...

Now set your desktop resolution to something safe 800x600 (although 1024x768 should work)
you might also want to change the default font sizes

then you can reboot the computer.


I found that my 7000 didn't work with both tv-out and vga attached, so I had to shutdown and attach only the tv-out.

It should display the bios (heck it should do this without the driver config)
then probably blank out during the loading screen

and pop back up when x has started


if it all goes tits up:

connect back to your monitor:

> sudo mv /usr/etc/X11/xorg.conf.bak /usr/etc/X11/xorg.conf



[I]Appologies now incase any of the scripts are wrong :S I'm on windows at the moment so I couldn't test them...

You might need to change the xorg.conf file location if its somewhere else,
Replace gedit with another editer if you wish[/I]

---

### Post by christooss on 2006-04-18
> You might need to change the xorg.conf file location if its somewhere else,

xorg.conf is in

/etc/X11

---

### Post by jamesdodd on 2006-05-01
[QUOTE=christooss]xorg.conf is in

/etc/X11[/QUOTE]

Ha! I knew it! damn!

I'm a pretty new to linux and when I'm on windows it doesn't help at all

---

