---
title: "How do I disconnect and reconnect with this?"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by suloku on 2006-06-18
Hi all, I followed [this ]](http://www.ubuntuforums.org/showthread.php?t=144468&highlight=sagem+fast+800)guide with succes to configure mi sagem fast 800 and connect to the internet.

Actually the module for the modem is ueagle-atm and it is loaded at boot.

Then the only thing I have to do is to tipe
```
sudo modprobe pppoatm
sudo pppd call ueagle-atm
```

Then the connectio ppp0 appears and i have internet accsess, but i don't know how to stop the connection or reestart it if it goes down (or I disconnect,but since I don't know how to do it...)

Hope you can help me, thanks for the answers.

---

### Post by metafile on 2006-06-18
```
sudo killall pppd
```

---

### Post by suloku on 2006-06-18
Thanks a lot, that worked very well!

---

### Post by metafile on 2006-06-18
doublepost, sorry

---

### Post by Malac on 2006-06-19
Hi,
Just thought I'd say if you want to automate one more step just 
edit the file /etc/modules and add ```
pppoatm
``` to the bottom of the file and it will load it at boot so you won't need to type that step every time.

Also:
I think the more correct way to start and stop the connection is:
```
pon [COLOR=DarkGreen]yourproviderfile[/COLOR]
``` To start connection and :
```
sudo poff [COLOR=DarkGreen]yourproviderfile[/COLOR]
``` To stop it.
Replace [COLOR=DarkGreen]yourproviderfile[/COLOR] with the name of your file (in your case [COLOR=DarkGreen]ueagle-atm[/COLOR]).
You could create shortcuts on your desktop or menu that do these.
In which case use "gksudo" instead of "sudo" for the poff command as this will popup a gnome window to enter the password.

"killall pppd" seems a bit brute force (IMHO) :) as it kills the processes rather than just disconnecting.

Hope this helps.

---

### Post by suloku on 2006-06-20
Thanks, that rocks!

Now I'm using an script to connect, but that sounds easier and doesn't require sudo.

---

### Post by Malac on 2006-06-21
Your Welcome.
The poff command for some reason needs the sudo which I didn't realise.
So it should read.
```
sudo poff [COLOR=DarkGreen]yourproviderfile[/COLOR]
``` To stop it.
Replace [COLOR=DarkGreen]yourproviderfile[/COLOR] with the name of your file (in your case [COLOR=DarkGreen]ueagle-atm[/COLOR]).

Starting the connection with pon doesn't however need sudo. Strange but true. :confused:

I'll edit the original post.

---

