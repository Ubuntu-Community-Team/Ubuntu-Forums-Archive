---
title: "suggestions for a good tv player for ubuntu"
date: 2009-10-08
forum: Multimedia Software
---

### Post by jarrah-95 on 2009-10-08
i have just got my dvb-t tuner to work again (after about 6 months of it failing) and i now cant remember any good programs that will let me watch tv and record it does anyone know any good ones 
also if you are going to suggest mythtv then can u tell me how to set it up and use the sql that it needs as that was a major problem last time and im using the gigabyte u8000-rh

---

### Post by amoeba801 on 2009-10-09
Hi Jarrah,

I am very happy using Kaffeine with my Leadtek/Winfast DBT Dongle Gold. Some may not like it because it's a KDE app and doesn't fit in too well with gnome, but I don't care about that as it works so well.

just the ticket for watching Kramer, Seinfeld and Hey Hey Reunion 'Encores' on our new Go! channel :-(

---

### Post by tghe-retford on 2009-10-09
Standalone apps I would recommend would be:
[LIST]
[*]**Kaffeine:** Darn good Digital TV application for KDE (but can of course be used with Gnome and when I last used Gnome, integrated well with the GTK+ engine). The application is currently undergoing the transformation from KDE3 to KDE4, but the DVB part of the program has been completely rewritten. I don't use Kaffeine at the moment because deinterlacing is no longer available. Kaffeine uses Xine for DVB...
[*]**Xine:**  ...which also comes as a standalone app, but in my view isn't as easy to get DVB working and maintain.
[*]**Me-TV:** A Gnome application for watching digital television. It is making great progress for the time I have been following it. I did find some bugs which caused it to crash when I used the EPG though. May have changed since, I haven't tested it for a bit since I transitioned to KDE4.
[*]**VLC:**The dark horse and the one I am using for now whilst I await Kaffeine to reintroduce its deinterlacing option. You'll need to install dvb-apps and use scan to generate a 'channels.conf' file so that VLC knows where to tune into for digital TV to work, but VLC more or less works flawlessly (and the default video output plugin doesn't exhibit the screen tear bug that everything else suffers from on my dual monitor setup).
[/LIST]

I did use MythTV on my computer, but I found it overkill and somewhat slow for my needs.

---

### Post by jarrah-95 on 2009-10-11
ok tahnkyou i wa looking at kafine and i liked the look of it but ended up going for me tv as i have used i before (altough it did stop working when i tryed to use it back then) an i dident know vlc did it i whould have just used it a i have liked that app since i started using ubuntu and i had to use w_scan to make a channels.conf for me tv anyway
thanks

---

