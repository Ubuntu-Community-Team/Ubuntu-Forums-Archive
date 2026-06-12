---
title: "Trouble antec fusion VFD, IR, and HDMI sound"
date: 2008-12-13
forum: Mythbuntu
---

### Post by jfenton78 on 2008-12-13
What are current methods to get the VFD and IR working on the Antec fusion? I've tried the following for each with no luck:

VFD:
Edit LCDd.conf and changed driver to imon. 
Restarted lcd by /etc/init.d/LCDd restart

IR
I'm getting a signal via mode2 but nothing via irw

---

### Post by utar on 2008-12-15
What version of the Antec case are you using (the silver or black one)?

---

### Post by jfenton78 on 2008-12-16
I'm using the silver version. Its version 2 I believe. But it does have the IR and VFD...I know the silver case has caused confusion in the past. Basically I've tried following the wiki and forum post regarding the VFD and IR, but most are outdated. 

It looks like to get the VFD working the LCDd.conf file needs edited and then restart LCDd, but that's not working for me. I'm not sure if I've missed something in piecing the info together. 

As for the IR, I've never really had any luck. I'm using a RC-6 Silver Gateway Media center remote. This remote has the "My" buttons on the top and no colored buttons. From my take, if its being recognized by mode2, then the IR is working, but the IRW shows not output because the remote has not been configured. So would I have to do a irrecord? In my hardware config (I think that was the file) I did specify the location and proper remote config that is supplied with LIRC. Is there a better config for this remote? Also once I have the remote "programmed" how do I link it to MythTV?

As for the HDMI that more a mobo problem. I'm not sure where to start with that. alsaplay -l shows my sound to be a alc883, but its actually a 889a. I'm not sure if thats causing the problem or not. 

Oh I'm running Mythbuntu 8.1. Thanks for helping.

---

### Post by utar on 2008-12-16
I can't help with the remote (I use the one that came with my Nova T-500) and the HDMI issue.

However LCDd worked out of the box for me on Mythbuntu 8.10 on my silver Antec.  This is what I did:

1) Installed LCDd from the package manager
2) Editted /etc/LCDd.conf and changed the driver line frpm "driver=curses" to "driver=imon"
3) restarted LCDd with "sudo /etc/init.d/LCDd restart"

If you have tried compiling LCDd from source after following the wiki I would uninstall this first.

---

### Post by jfenton78 on 2008-12-17
Thanks for the confirmation on the VFD. At least some has confirmed that the I did it right. Any ideas how to troubleshoot the VFD?

---

### Post by utar on 2008-12-17
In the first instance I would uninstall LCDd completely from the package manager (use the purge option) and then reinstall.

If that doesn't work can you type the folling into a terminal window and post the output:

LCDd -f -r 5 -s 0

---

### Post by jfenton78 on 2008-12-19
I never compiled LCD proc from source. I just used the one available in the ibex repository. I did a complete removal in synaptic before editing the config file. Here is the output from LCD -f -r5 -s 0:

Server running in foreground
sock_create_inet_socket: Could not bind to port 13666 at address 127.0.0.1 - Address already in use
sock_init: Error creating socket - Address already in use
Critical error while initializing, abort.

Thanks for the continued help.

---

### Post by jfenton78 on 2008-12-19
I never compiled LCD proc from source. I just used the one available in the ibex repository. Here is the output from LCD -f -r5 -s 0:

Server running in foreground
sock_create_inet_socket: Could not bind to port 13666 at address 127.0.0.1 - Address already in use
sock_init: Error creating socket - Address already in use
Critical error while initializing, abort.

Thanks for the continued help.

---

### Post by utar on 2008-12-20
Stop LCDd first with:

sudo /etc/init.d/LCDd stop

You will still get an error message when you then run LCDd -f -r 5 -s 0  but the output will be more helpful.

Also when you type lsusb what device id do you get for the LCD?

---

### Post by jfenton78 on 2008-12-20
Well the dang VFD just started working after a shutdown. I don't know what happened. I never changed anything, but what I've posted. Thanks for the help utar. At least I've learned a few linux command.  Now onto my remote.

---

