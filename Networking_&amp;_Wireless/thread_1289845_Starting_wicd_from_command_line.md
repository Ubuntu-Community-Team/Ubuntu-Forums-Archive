---
title: "Starting wicd from command line"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by IceCap on 2009-10-12
I connect remotely to my MythTV (Mythbuntu) media center through ssh -X for various maintenance work.
  The mediacenter is using wicd and I can't figure out how to invoke wicd network dialog from the command line.  It looks like it is sort of a background program that just comes to the foreground.  I'm sure this is something very simple, I'm just missing it (besides being a Linux newbie).

 Thanks

  IC

---

### Post by falconindy on 2009-10-12
wicd has 2 main components -- a daemon (wicd) and a front end graphical client (wicd-client). There is no command line based utility for wicd. If you want to modify network parameters or connect to a network from the command line, wicd isn't what you want to be using.

---

### Post by IceCap on 2009-10-12
I may not have been clear on what I want to do.  I don't want to setup the network connection from the command line of the remote computer.  I want to open the frontend graphical client, wicd-client, on my remote machine (I log in to the mediacenter using "ssh -X" allowing me to run the x-client remotely (OK, the verbage here may be incorrect)).

  If I run "wicd-client" from the command line, it doesn't open up the graphical client for the wicd.  What is the comment to do that in the menu?

  Thanks

  IC

---

### Post by falconindy on 2009-10-13
> **IceCap said:**
> I may not have been clear on what I want to do.  I don't want to setup the network connection from the command line of the remote computer.  I want to open the frontend graphical client, wicd-client, on my remote machine (I log in to the mediacenter using "ssh -X" allowing me to run the x-client remotely (OK, the verbage here may be incorrect)).

  If I run "wicd-client" from the command line, it doesn't open up the graphical client for the wicd.  What is the comment to do that in the menu?

  Thanks

  IC
Well, I may still be unclear on what you're trying to accomplish. Launching `wicd-client` drops the GUI in the notification section of gnome-panel (assuming you're using gnome).
[img]http://i33.tinypic.com/2gwx3z6.jpg[/img]
That icon on the left is wicd. I think by default, it adds itself to your list of startup applications on installation.

---

### Post by IceCap on 2009-10-18
Running wicd-client from the terminal just adds another icon (daemon) to the menu bar.  It doesn't open up the graphical user interface of wicd, which I'm trying to do (from the terminal).

  So here is my problem.  I need to have my mediacenter (mythtv) switch from using my old wireless network/router to my new one (Airport Express).  In order for me to do that I need to ssh into the media center (using my xubuntu laptop that still is using the old wireless router) to change the settings in the wicd graphical user interface.  After that, I can remove my old wireless router from the network.

  So, how can I bring up the graphical user interface for wicd from the terminal?

  Thanks

  IC

---

### Post by falconindy on 2009-10-18
```
wicd 1.5.9
wireless (and wired) connection daemon front-end.

Arguments:
	-n	--no-tray	Run wicd without the tray icon.
	-h	--help		Print this help information.
	-a	--no-animate	Run the tray without network traffic tray animations.
```
The -n flag looks like it might be of interest to you.

---

### Post by IceCap on 2009-11-01
That's it.  Running wicd-client -n opens up the dialog to control the network for wicd.

  Thanks

  IC

---

