---
title: "VNC on Dedicated Host"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by Keinan on 2010-07-30
I have purchased a dedicated server : AMD x2 Regor 2.8Ghz
It has Ubuntu 9.10 server installed on it


I am accessing it through PuTTY on my Windows XP machine at home. I only have access to it through SSH at the moment.


I have installed a GUI using the following command:
sudo aptitude  install --no-install-recommends ubuntu-desktop


 I need to find a VNC server that I can install, configure, and start through nothing but the SSH terminal alone, and does not require a person to be present in order to run and accept connections (as it is a box in a datacenter).


The hosting company is being less than helpful, and if possible I'd rather not pay them to do this for me (what I'm sure must be a few command lines and tinkering that their "administrative time" will charge me exorbitantly for).


Thank you so much in advance, and please let me know if there is any further information which is required to help me.

---

### Post by YesWeCan on 2010-07-30
I do exactly what you want to do. It is quite achievable.

On the Ubuntu server you need to install 'tightvncserver' (it is available in the software centre). You run the app from a command line by typing 'vncserver'. The first time you run it asks for an access password - the password you will need to supply via your vnc viewer on your Windows box. Tightvncserver exports independent desktop instances, as many as you want. These are independent of the local desktop and there is no need for a local login. You just remotely login using SSH and then run vncserver (if it isn't already running) and use your vnc viewer to see the desktop.

One caveat. VNC is not secure. So it is recommended to create an encrypted tunnel for its ports. This can either be done using "port-forwarding" which is an SSH feature or it can be done using OpenVPN. I use OpenVPN and it is bullet-proof and requires no effort once configured. The OpenVPN configuration is more complicated than port-forwarding.

Have a Google for some of these methods and post any further questions.

Brian

---

### Post by Keinan on 2010-07-30
Thank you for the help.

I somehow managed to get it to work...

I do have a question still, however, regarding xauthorization...

I am trying to run gksudo gedit so that I can test the PHP of my LAMP server, but it gives the following error:

[I]Xlib: extension "RANDR" missing on display ":3.0".

Error copying '/home/user/.Xauthority' to '/tmp/libgksu-wodlbR' permissiondenieduser@ubuntu:
[/I]

How can I fix this?

---

### Post by YesWeCan on 2010-07-31
Hi,
You need to mark this thread as "solved" in Thread Tools and open a new thread for your new question. I don't know the answer, sorry.

---

### Post by Keinan on 2010-07-31
OK! Thank you! :)

---

