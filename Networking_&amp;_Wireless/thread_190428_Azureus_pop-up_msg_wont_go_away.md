---
title: "Azureus pop-up msg wont go away"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by NiksaVel on 2006-06-06
Hey all...


I've seen there were other posts about this problem, but I didn't really figure out how to fix it.

When an azureus pop-up msg appears, it wont go away....   pressing the hide button only marks the button, but it doesn't actually get pressed and the msg just hangs there blocking half my screen....   ](*,) 

tried with enter, same thing...

---

### Post by bluenova on 2006-06-06
Yea, I have the same thing. It would seem there are many problems with the lastest.

I havn't looked much yet, but the problems I have so far are:
Pop-up's won't close
Tab's cannot be closeed by clicking a 'x' in the tab like you used to
The taskbar icon does not display properly.

---

### Post by NiksaVel on 2006-06-06
is there an alternative quality bittorrent client for linux anyone would recommend?

---

### Post by dueyfinster on 2006-06-06
Bittornado is quite good, it may be in the repository I am not sure. EasyUbuntu and Automatix script will install it for you if not, both found on these forums.

-Thanks

---

### Post by k420 on 2006-06-06
i have had the same problem but have figured out how to fix it.  The reason it is popping up is due to azureus not closing properly.  Before you log out or close the app you must close it using the exit link on the toolbar each time that will stop the popup from popping up

---

### Post by NiksaVel on 2006-06-06
but there are also other pop-ups...  no?

---

### Post by bluenova on 2006-06-06
[QUOTE=k420]i have had the same problem but have figured out how to fix it.  The reason it is popping up is due to azureus not closing properly.  Before you log out or close the app you must close it using the exit link on the toolbar each time that will stop the popup from popping up[/QUOTE]
I don't get the icon on the taskbar, I read on another thread, that the icon is there, but it's only 1 pixel wide :D

---

### Post by !nkubus on 2006-06-06
[QUOTE=NiksaVel]is there an alternative quality bittorrent client for linux anyone would recommend?[/QUOTE]

Rufus combined with AllTray (for some reason the tray icon of Java and wxWindows don'T work on Gnome)

Just modify the Menu entry of Rufus to alltray rufus -s and youre set with the best gtk torrent app.

---

### Post by Firebirdy on 2006-07-29
So no solutions yet? It's a bit annoying since restarting azureus seems to be the only thing to fix this :)

Edit: nm, looks like this has been fixed, although there's no .deb update yet...

[https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813](https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813)

---

### Post by blackpaw on 2006-07-30
Inside the link to [launchpad]("https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813")
there is an instruction how to fix the error using a /jar file from the beta version of Azureus. It works fine here.

The debian build is already fixed so I think the fix for Ubuntu will not take long.

Just download the file mentioned there (Azureus2403-B35.jar) and copy it to
/usr/share/java/Azureus2.jar

This not only fixes the popups, it also fixes the system tray icon and the non existing "close" buttons on the tabs inside Azureus. 



have fun :)

---

### Post by vindvaki on 2006-07-30
> **blackpaw said:**
> 
Just download the file mentioned there (Azureus2403-B35.jar) and copy it to
/usr/share/java/Azureus2.jar


Thanks man! Worked like a charm :D

---

### Post by MedievalAnubis on 2006-08-09
Yea the CVS build worked perfectly.

---

### Post by bagatonovic on 2006-10-09
I fixed mine by installing the actual JRE (not the default install Java, but the package from Sun)

---

