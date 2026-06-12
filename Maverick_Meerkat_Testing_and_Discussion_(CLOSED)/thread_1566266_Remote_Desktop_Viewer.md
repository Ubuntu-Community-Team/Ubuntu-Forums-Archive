---
title: "Remote Desktop Viewer"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jonny87 on 2010-09-02
I can't seem to get the remote desktop viewer to connect to another computer. I've tried connecting it to my comp with 10:04 to another laptop and to my comp at my Polytech. Each time it just comes up saying that "the connection was closed".

Although I can connect the other way from my comp with 10:04 to my laptop with 10:10. It works fine that way. 

Anyone have any ideas on this?

---

### Post by Peter09 on 2010-09-02
If you are trying to get through an organisations router and firewalls your chances are slim. Most organisations do not open Ports in firewalls for remote connections without some sort of security barrier.

---

### Post by Jonny87 on 2010-09-02
Yes I'm a wear of that and I know that this isn't the issue here as it happens at home and I have even tried turning off the firewall. It still doesn't connect. I can ssh from the terminal though. and I can connect to the comp via samba to access shared folders. This just won't connect at all.

Is anyone else having this with theirs?

---

### Post by cariboo on 2010-09-02
Use nmap to see if port 5900 is open, when you run the remote desktop client. 

One big warning when using the default remote desktop utility make sure you use a strong password, there have been many systems cracked due to the user using a weak or no password when using the remote desktop utility.

---

### Post by Jonny87 on 2010-09-02
> **cariboo907 said:**
> Use nmap to see if port 5900 is open, when you run the remote desktop client. 

One big warning when using the default remote desktop utility make sure you use a strong password, there have been many systems cracked due to the user using a weak or no password when using the remote desktop utility.

Ok I'll check i out.

Thanks for the warning, all my passwords are strong complexity passwords.
[I]An I'm sure that they'd take 8 octillion years to crack or more.


[/I]

---

### Post by Jonny87 on 2010-09-02
Just checked and port 5900 is open. even though I have the fire wall on its set to accept everything from my laptop.

So port 5900 is open, the firewall isn't whats stopping it, and I checked the remote desktop settings and its doesn't work with multiple machines.

Any other ideas??

---

### Post by cariboo on 2010-09-02
I can't get it to work either, I would suggest you report a bug against vinagre.

---

### Post by seeker5528 on 2010-09-02
I haven't messed with any VNC stuff for a while, but my best guess would be some kind of authentication failure between the newer client (Vinagre) and the older server (Vino).

I set up vino on my Lubunu (Lucid) installation and try to connect with Vinagre it gives the same result you describe, with or without having a password required.

If I connect with Xvnc4viewer, it works fine, with or without a password, same with xtightvncviewer.

Apparently they didn't see fit to package either of these with a .desktop file that makes them show on the Gnome menu, but if you have 'menu' installed and use the menu editor to enable the display of the debian menu they would show at 'applications --> debian --> applications --> network --> vnc viewer' and 'applications --> debian --> applications --> network --> communication --> xtightvncviewer'.

Later, Seeker

---

### Post by Jonny87 on 2010-09-02
> **cariboo907 said:**
> I can't get it to work either, I would suggest you report a bug against vinagre.

vigagre??
I'm new reporting bugs, so far I've just done it when Apport pops up wanting to send an error report. How would I go about generating a report for this?

---

### Post by seeker5528 on 2010-09-02
To report it open up a terminal window and type:

```
apport-bug vinagre
```

It should then collect relavant information and take you through the bug reporting steps.

Later, Seeker

---

### Post by Jonny87 on 2010-09-02
> **seeker5528 said:**
> To report it open up a terminal window and type:

```
apport-bug vinagre
```It should then collect relavant information and take you through the bug reporting steps.

Later, Seeker

Thanks, doing it now.

---

