---
title: "Can open program from terminal but can't get a link on desktop"
date: 2015-08-05
forum: Multimedia Software
---

### Post by melissa4 on 2015-08-05
Hello,

I just recently installed Packet Tracer 6.2 on my 140.04 LTS Ubuntu laptop. I am able to successfully launch the program from the terminal, but wish to have either a desktop icon or a quick launch button on the launcher for the program. I am unsure how to do this (just started using Linux a month ago). Any help would be greatly appreciated! Thanks!

-MJ

PS:
I apologize if this isn't the right thread. First time posting, so I am still getting used to things.:KS

---

### Post by howefield on 2015-08-05
Do you see the icon in the dash? 

If so, click and drag it onto the launcher.

---

### Post by melissa4 on 2015-08-05
No, it isn't showing up there. When I go into nautilus, I can find it in my apps under usr/.../applications. I tried making a shortcut from that one and sending it to the desktop, but that was a no go, too.

---

### Post by howefield on 2015-08-05
> **melissa4 said:**
> No, it isn't showing up there. When I go into nautilus, I can find it in my apps under usr/.../applications. I tried making a shortcut from that one and sending it to the desktop, but that was a no go, too.

By that, do you mean you can see the *.desktop file for the packet tracer application in usr/share/applications ? If so, try logging out and back in or rebooting to make the icon appear in the dash.

---

### Post by melissa4 on 2015-08-05
I am able to find it in usr/share/applications through running  gksu nautilus.  The type listed is desktop configuration file (application/x-desktop). When I try to launch the program from there, I get "There was an error launching the application." I have it checked as "Allow executing file as program" under the properties, but still get the same error message.

---

### Post by melissa4 on 2015-08-05
Restarted and nothing showed up upon reboot.

---

### Post by mc4man on 2015-08-05
When you installed it where you prompted something like this - 
read -p "Should we create a symbolic link \"packettracer\" in /usr/local/bin for easy Cisco Packet Tracer startup? [Yn] " 
If so what did you answer?

open the .desktop in a text editor & post the contents
(- open gedit & just DnD the .desktop into the gedit window to read.

---

### Post by melissa4 on 2015-08-05
I did get that. I answered yes. 

Sorry to edit so much. I just realized what you needed me to do. Here are the contents of the file:
[Desktop Entry]
Exec=PacketTracer6
Icon=pt6
Type=Application
Terminal=false
Name=Packet Tracer 6.2

---

### Post by mc4man on 2015-08-05
you need to edit the Exec= line in that .desktop, it's wrong.
It needs to be - 
```
Exec=packettracer
```
So to edit the one in /usr/share/applications you need to do so as root
Ex. 1 with nano - 
```
sudo nano /usr/share/applications/pt6.desktop
``` 
Use the keyboard arrow keys to go to and backspace away PacketTracer6, then type in or paste packettracer
Then on keyboard
 ctrl+o
press enter key
ctrl+x

Ex. 2 with gedit
```
sudo -H gedit /usr/share/applications/pt6.desktop
```
make the line correct, save, close gedit

So your .desktop would be like - 
```

[Desktop Entry]
Exec=packettracer
Icon=pt6
Type=Application
Terminal=false
Name=Packet Tracer 6.2
```

IF there was any reason to have it available in the context menu then you'd make your .desktop look like this, ie. adding the blue (a  line & %f
```
[Desktop Entry]
Exec=packettracer [COLOR="#0000CD"]%f[/COLOR]
Icon=pt6
Type=Application
Terminal=false
Name=Packet Tracer 6.2
[COLOR="#0000CD"]MimeType=application/x-pkt;application/x-pka;application/x-pkz;[/COLOR]
```

---

### Post by melissa4 on 2015-08-05
Thank you!

---

