---
title: "mythgame issues/questions/concerns"
date: 2008-02-16
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-02-16
so reading some old threads someone mentioned its best to get the emulator working outside of myth before trying to do it with myth. well im trying to install mupen64 for a n64 emulator. i want all my games stored on the backend and for them to be accessable from the frontend (not hard). would the emulator itself need to be installed on the frontend? or can it run the emulator from the backend and just have everything outputted to the frontend? 

next up, the controller. i have a ps2(playstation) controller that ive used with a ps2->usb adapter and it worked great with project64 under windows but it seems i cant configure the buttons to work with this game controller. i really dont want to be stuck using the keyboard for console games.

also when i start the emulator from myth, it comes up behind the myth window in its own screen. how do i get it to just go straight to full screen, so that i can see it right away, so when i exit, it goes back to myth, just like watching a movie does?

thanks :)

---

### Post by gsrcrxsi on 2008-02-17
does anyone have any experience with mythgame and using a controller rather than the keyboard?

---

### Post by newlinux on 2008-02-17
> **gsrcrxsi said:**
> so reading some old threads someone mentioned its best to get the emulator working outside of myth before trying to do it with myth. well im trying to install mupen64 for a n64 emulator. i want all my games stored on the backend and for them to be accessable from the frontend (not hard). would the emulator itself need to be installed on the frontend? or can it run the emulator from the backend and just have everything outputted to the frontend? 


emulators need to be installed on frontends, and games need to be on frontend as well (can be with a mounted share from the backend)
> 
next up, the controller. i have a ps2(playstation) controller that ive used with a ps2->usb adapter and it worked great with project64 under windows but it seems i cant configure the buttons to work with this game controller. i really dont want to be stuck using the keyboard for console games.

also when i start the emulator from myth, it comes up behind the myth window in its own screen. how do i get it to just go straight to full screen, so that i can see it right away, so when i exit, it goes back to myth, just like watching a movie does?

thanks :)

Not sure about the others. I use a logitech rumblepad (wireless and wired), and the emulators I use go on top (fceu, zsnes, and psx). Perhaps look at the command line switches for the emulator you are using and see if there is a full screen option...

---

### Post by gsrcrxsi on 2008-02-17
i have some ps1 games (ff7) and was wondering if it was possible to "rip" the discs to the drive and emulate it?

and with your controller, do you configure it within the emulator? or does it just map the keys from the keyboard or something?

---

### Post by newlinux on 2008-02-18
> **gsrcrxsi said:**
> i have some ps1 games (ff7) and was wondering if it was possible to "rip" the discs to the drive and emulate it?

and with your controller, do you configure it within the emulator? or does it just map the keys from the keyboard or something?

All my psx games are on disk. My controller is configured within each emulator.

---

### Post by gsrcrxsi on 2008-02-20
well what i meant was is it possible to use mythtv to rip the game to the HD? or what software would i use to do that? id rather not download a ripped ISO when i have the disc in front of me that i could do myself.

also, it seems that mupen64 is a pretty terrible n64 emulator, and configuring an actual controller seems to not work (unless im missing something). would it be possible to run a windows n64 (project64 seems to be the best and is easy to configure a controller) emulator under wine? could myth properly run it this way? what do you think?

---

### Post by newlinux on 2008-02-20
Well, the games I have on hard disk were ripped from cds (that's what I was trying to imply) ripped them long before I used mythtv so I don't know about myth, but I see no reason they couldn't be ripped in Linux... Quick google searches will probably return anything you need on ripping psx games... I ripped my back in my windows days...

Yeah, I think with a script you could run an emulator from wine through myth. Don't know if Wine will properly run the n64 emulators.

---

### Post by gsrcrxsi on 2008-02-20
yea wine hq says it plays games fine, but when i was tinkering with it last night whenever i would try to run a game it would shut off. is there a log i can look at to see whats going on with it?

---

### Post by Ramage on 2008-08-12
Did you end up getting the wine lanucher working from the mythgame interface? 

Just trying this myself and having problems the wine launcher works great from desktop interface in mythbuntu but the mythgame launcher doesn't seem to be working with wine for me.

Found a wicked joystick to keyboard daemon **Qjoypad** but it must be compiled from source it has a couple of X11 and qt3 dependencies but once you get them installed it compiles easily and works flawlessly with mythbuntu across all interfaces and all X windows not just a specific window and it can handle more than 1 device also it can be configured per app if necessary.

---

