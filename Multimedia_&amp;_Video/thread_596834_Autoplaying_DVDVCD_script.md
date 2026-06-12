---
title: "Autoplaying DVD/VCD script"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by tarasbulba on 2007-10-30
I don't know if this is the right place.If not, please accept my apologies and move this thread right place. I have just finished a media notifier bash script for dvds and vcds. It born from my needs.I have switched from kde to gnome.Gnome is beautiful i think.But i wanted to see a window to choose playing my DVD/VCD movies with VLC or Mplayer, like KDE's Media Notifier daemon.Then i started to write a script using zenity.Today it finished and i want to dhare it with people.I'm totally a newbie at bash scripting so there should be some mistakes in the script.Please contribute and help with suggestions.Thanks.
[[IMG]http://img508.imageshack.us/img508/2335/faciaworkssp0.th.jpg[/IMG]](http://img508.imageshack.us/my.php?image=faciaworkssp0.jpg)

---

### Post by AlexThomson_NZ on 2007-10-30
Hiya tarasbulba,

Sorry I can't see the screenie (it's a bit small to make out the details), but I do a similar thing at home.  I just brought myself a nice big LCD telly, so naturally the first thing was to connect to my linux laptop.  I made a curses-based Perl script, so using any PC or laptop around the house, we can connect to this, choose a DiVX/DVD and have mplayer run it on :1 (the TV)  Sounds like a bit of a hack (it's hard to explain) but is really quite nice (even the missus finds it easy!)

Just out of interest- anybody else here use Linux to watch DivX's/VCD/DVDs on their TV?  Any tips/tricks to share?

---

### Post by tarasbulba on 2007-10-30
Thank you AlexThomson_NZ for warning me about image. I am totally a newbie in this bash scripting stuff. As i understand from your post, your script is used for totally different thing than my scirpt. My script only provides options to run some applications when a VCD/DVD inserted.That's all...
  I need help to improve my script. I want this script to detect if blank cd/dvd inserted and add options for burner apps or detect if audio disc inserted and add options for music player/ripper apps.Problem is how this script will detect if blank disc or audio disc inserted.thank you

---

### Post by AlexThomson_NZ on 2007-10-30
Ah I misunderstood what your script does- thought it was a more generic media controller

Doesn't Ubuntu automatically open a dialog when a blank CD/DVD is inserted?

---

### Post by tarasbulba on 2007-10-31
No, Ubunutu does not automatically open a dialog when a blank CD/DVD is inserted. It just executes any application which wa described in gnome-volume-manager. I must find a way to llisten hal events and if a blank dvd/cd or audio cd inserted my scirpt recognizes this and open a dialog.Thanks any way...

---

### Post by AlexThomson_NZ on 2007-10-31
I just tried with a blank disc I got a dialog pop up...

---

### Post by tarasbulba on 2007-10-31
> **AlexThomson_NZ said:**
> I just tried with a blank disc I got a dialog pop up...

Yep, it is nautilus-cd-burner dialog. But if i want to use k3b sometimes and another day different burning application,  Ubuntu will still shows that nautilus-cd-burner dialog.
Anyway i couldn' t find how to listen hal events but i figured out let gnome-volume-manager do that for me. I just added some options to script,so it should used with some arguments. This is easy way.Just like that: i specified an -a argument in script so it shows audio cd dialog. In "removable volumes and devices" in audio cd selection, scirpt specified as "sh Facia -a" so audio cd dailog runs. Now i need command line arguments for other players/burners.Thank you...

---

### Post by tarasbulba on 2007-10-31
I made second version of the script.

*Added playing audio cd options with Rhythmbox
*Added playing audio cd options with Amarok
*Added playing-ripping audio cd options with Sound-Juicer
*Burning disc options with k3b and Nautilus
*Script working style changed,now it woorks only with arguments
 [-h] [--help] Shows Help 
 [-version] Shows Full Name and Version of the script
 [-a] Opens Audio CD Dialog Box
 [-d] Opens DVD Video Dialog Box
 [-v] Opens VCD Video Dialog Box
 [-b] Blank CD/DVD Dialog Box

---

