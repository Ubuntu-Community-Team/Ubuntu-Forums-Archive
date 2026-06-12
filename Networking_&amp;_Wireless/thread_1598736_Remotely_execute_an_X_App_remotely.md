---
title: "Remotely execute an X App remotely"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by msherman123 on 2010-10-16
I am looking to see if there is any way to remotely launch a X application on a remote machine via ssh (or web cgi) via a local shell or perl script.  I would like to connect from A to B and have the app launch on B.  Doing it via standard way 'obviously' gives me the standard error of "cannot connect to X Server" or "Unable to open display".  This is expected.  But I am looking to see if there is any other way to do this.  Is there an argument I could pass to have it launch on a certain display?

VNC or Remote desktop is not an option.

Thanks!

---

### Post by SeijiSensei on 2010-10-17
Connect to the remote machine using "ssh -X".  You may need to run "xhost +" on the client machine before using ssh to permit the remote connection.

I'm assuming you want to see the application display on the client machine.  If you log in without the "-X" switch, you can launch an X application on the server, but it will display there.

---

### Post by msherman123 on 2010-10-17
> **SeijiSensei said:**
> Connect to the remote machine using "ssh -X".  You may need to run "xhost +" on the client machine before using ssh to permit the remote connection.

I'm assuming you want to see the application display on the client machine.  If you log in without the "-X" switch, you can launch an X application on the server, but it will display there.

Actually, the opposite.  Not doing standard X Forwarding.  I actually would like to see the X App launch on the remote machine.

This is specifically what I am doing.  Probably would of made sense to explain in the original message.

I use XBMC quite a bit.  My current remote control abilities work fine when XBMC is open.  But I cannot remotely start or quit XBMC.  What I wanted to do is create a web page (Running on the XBMC machine via apache) to launch a perl script to start it on that machine.  Everything is working, but I obviously get the errors noted above.

Thanks for the response!

---

### Post by msherman123 on 2010-10-17
Bump  :)

---

