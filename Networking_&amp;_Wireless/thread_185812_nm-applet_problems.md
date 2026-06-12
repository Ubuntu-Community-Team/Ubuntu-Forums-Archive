---
title: "nm-applet problems"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by markmcspadden on 2006-06-01
I'm running a clean install of 6.06 and am having problems getting the Network Manager applet going. From the terminal when I type "nm-applet", I just get a hanging line and nothing happens. 

What's interesting though is that I think NetworkManager is handling my connection. When I type "nm-tool" I get info about both my wireless and wired cards. It shows when my wired card is connected and even gives a scan of available wireless networks for my wireless card.

(Yes I have commented out /etc/network/interfaces and fixed /etc/default/wpasupplicant with ENABLED=0...just in case you were thinking that.)

I've tried everything on the NetworkManager wiki and no better. Any help would be greatly appreciated.

---

### Post by markmcspadden on 2006-06-01
Figured it out myself....

Apparantly everything with network manager was working just peachy...the problem was I had removed the NOTIFICATION AREA applet from my panel. 

YOU HAVE TO HAVE THIS APPLET ON ONE OF YOUR PANELS TO ACCESS THE NETWORK MANAGER GUI. Nobody ever told me that....:) Carry on.

---

### Post by Jingo on 2006-06-02
I am getting this after running nm-applet:

"The NetworkManager applet could not find some required resources.  It cannot continue."

I have the notification area in the panel!

What could be the problem?

---

### Post by edm1 on 2006-06-02
I was having a similar problem until i figured that network manager only works once you've deconfigured any ESSIDs and WEP keys in System > Admin > Networking.

---

### Post by Fush1986 on 2006-06-02
jingo i am also having the same problem. It worked fine on my desktop pc but my laptop is not working at all. 

"** (nm-applet:14182): WARNING **: Icon nm-vpn-lock missing: Icon 'nm-vpn-lock' n ot present in theme

(nm-applet:14182): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJ ECT (object)' failed"

That is what i get when i try and load the app in bash..the second part repeats its self about a dozen times

---

### Post by mdognrdog on 2006-06-02
It's a problem with the icons.  I had a different problem, and came across the fix to your problem [here]("http://nozell.com/blog/archives/2006/03/17/getting-networkmanager-to-work-on-ubuntudapper/").

> $ sudo gtk-update-icon-cache -f /usr/share/icons/hicolor

The lack of some icon cache was preventing a network configuration tool from running. Ugh.

This allowed the applet to start, but wasn’t controlling the network devices. For that, I needed to remove references to any network devices so the only thing in my /etc/network/interfaces are these lines:

# The loopback network interface
auto lo
iface lo inet loopback

---

### Post by Alex_K on 2006-06-02
[QUOTE=Jingo]I am getting this after running nm-applet:

"The NetworkManager applet could not find some required resources.  It cannot continue."
[/QUOTE]

i had the same problem today and found following solution:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

---

### Post by lanhelp on 2006-06-10
Even issuing the command above (sudo gtk-update-icon-cache  -f /usr/share/icons/hicolor) the problem persists. I receive a message "** (nm-applet:6435): WARNING **: Icon nm-vpn-lock missing: O ícone 'nm-vpn-lock' não está presente no tema"

PS. System is up-to-date.

---

### Post by Jad on 2006-06-11
I tried ```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
``` but didn't fix any

---

### Post by idn on 2007-02-11
> **Jad said:**
> I tried ```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
``` but didn't fix any

This didnt fix the problem for me either, at the moment I'm using knetworkmanager but I would prefer it if I could use the gnome version. Does anyone else know how to fix this problem? I'm using edgy

---

