---
title: "Screen resulotion - it's all gone black"
date: 2009-11-08
forum: Mythbuntu
---

### Post by idrisdraig on 2009-11-08
Day 1 of Mythbuntu.
I was playing around with screen resolution to try and optimise the output for VDU.
I reduced resolution and the screen is now just black.
If I restart, I see the Myth logo, but when it goes there's nothing at all left.
I _think_ everything I need to get at is just off screen now, but I can't see anything to make any changes.
Any suggestions how I can reset to the default screen resolution?

---

### Post by nickrout on 2009-11-08
> **idrisdraig said:**
> Day 1 of Mythbuntu.
I was playing around with screen resolution to try and optimise the output for VDU.
I reduced resolution and the screen is now just black.
If I restart, I see the Myth logo, but when it goes there's nothing at all left.
I _think_ everything I need to get at is just off screen now, but I can't see anything to make any changes.
Any suggestions how I can reset to the default screen resolution?

How did you change it in the first place?

You could try renaming /etc/X11/xorg.conf and restarting X

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
sudo service gdm restart
```

---

### Post by idrisdraig on 2009-11-09
> **nickrout said:**
> How did you change it in the first place?Through the display panel under Accesories (IIRC). I'd change it back the same way, except I can't see the mouse pointer or the menus :(

As for doing anything with command line - [SIZE=1][COLOR=Silver](other than the nice slick user friendly interface of NeXTSTEP)[/COLOR][/SIZE] I'm in my first 24hrs as a Linux user and that's waaaaaaaaaay beyond me at the moment. I can open a terminal, but that's about it. Other than that I'm trying to get some reading done fast[SIZE=1][COLOR=Silver] ... while I pine for the slick user friendly interface of every other OS I've used since Acorn MOS. [/COLOR][/SIZE]

---

### Post by nickrout on 2009-11-09
if you can open a terminal you can surely type in the commands I suggested.

---

### Post by idrisdraig on 2009-11-09
The only way I know to open a terminal is through the menus which I can't see.
Is there another way?

---

### Post by nickrout on 2009-11-09
good point!

you should be able to get to a console by hitting ctrl-alt-f1 and then logging in with your username and password.

Alternatively you could ssh in from another machine and run the commands. If you have another linux machine simply type ```
ssh mythbox
``` in a terminal or console, where mythbox is the name or ip address of your errant myth machine.

If you only have windows and want to try ssh in then download putty, its a windows ssh client (and google will find it, small download).

If none of tyhat works you can use the live cd to access the system, post back if you need to do that, as I'll need to work out the command you'll need to type.

---

### Post by idrisdraig on 2009-11-09
Thanks.
ctrl-alt-f1 didn't get a console visiible on the screen.
I'll look into the ssh: the Myth PC isn't networked - will I need to do anything settings-wise that I'd need to be able to see the screen for or will just plugging the Myth PC into the router be enough?

[SIZE=1][COLOR=Silver](Don't take this as unapreciative of the help, but since I've not got round to do anything since installing Mythbuntu, I'm starting to wonder whether reinstalling the OS again might be the quickest option.)[/COLOR][/SIZE]

For the record, what is X?

---

### Post by nickrout on 2009-11-09
> **idrisdraig said:**
> Thanks.
ctrl-alt-f1 didn't get a console visiible on the screen.
I'll look into the ssh: the Myth PC isn't networked - will I need to do anything settings-wise that I'd need to be able to see the screen for or will just plugging the Myth PC into the router be enough?

[SIZE=1][COLOR=Silver](Don't take this as unapreciative of the help, but since I've not got round to do anything since installing Mythbuntu, I'm starting to wonder whether reinstalling the OS again might be the quickest option.)[/COLOR][/SIZE]

For the record, what is X?

OK you ARE new around here :)

X or the X Xindow System is the graphical part of unix/linux. It is the application that allows you to have pretty pictures on the screen as opposed to just text and black background (y'know, like dos)

If you haven't got very far with configuring your system, a reinstall would be an appropriate solution!

---

### Post by idrisdraig on 2009-11-10
> **nickrout said:**
> OK you ARE new around here :)So new I'm still wearing my celophane wrapper and price tag!

> **nickrout said:**
> If you haven't got very far with configuring your system, a reinstall would be an appropriate solution!Reinstalled. I HAVE PICTURES!!! Hmmmm. 

Right, what's the next preoblem .... [there will be more]
Thanks for your help anyway.

---

### Post by idrisdraig on 2009-11-11
Oh bugger!
Tried to change the screen resolution again (probably naiively) and had the same effect.
Managed to open an almost readable terminal this time with ctrl-alt-F1 and typed in the commands you suggested.
Unfortunately the screen changed for the worse. 

What should I try next? (BTW Still not networked.)
[SIZE=1][COLOR=Gray]I'd rather not have to reinstall the OS again. It seem a little sledge hammer vs wallnut.[/COLOR][/SIZE]

---

