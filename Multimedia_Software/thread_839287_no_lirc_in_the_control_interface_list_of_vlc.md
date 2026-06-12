---
title: "no lirc in the control interface list of vlc"
date: 2008-06-24
forum: Multimedia Software
---

### Post by 8yun on 2008-06-24
As shown on the attachment, the option of infrared remote control interface is disappeared in VLC preference. does anyone know how to get it back? I just want to use lirc to control vlc. I have reinstalled vlc and lirc many times, but no help at all.

Thanks in advance.
Roger

---

### Post by wolfen69 on 2008-06-24
from [HERE]("https://help.ubuntu.com/community/InstallLirc/Hardy")

Mythbuntu LIRC generator

The Mythbuntu Team has developed a python script that will generate a sane remote control mapping to use or at least start from. It grabs all of the possible buttons and remotes from /etc/lirc/lircd.conf and maps them over for MythTV, Xine, MPlayer, VLC, Totem, & Elisa. 

Install the application as follows:
```
sudo apt-get install mythbuntu-lirc-generator
```
To run, simply run:
```
mythbuntu-lircrc-generator
```
By default, all 6 application configurations are generated for the currently logged in user. Any old configurations will be renamed.

---

### Post by terry_gardener on 2008-06-24
this happened to me, it the text box just type "lirc" without the " and save. 

close vlc and then reopen. 

lirc should now work if the lircrc file has been setup.

---

### Post by 8yun on 2008-06-24
Thanks terry_gardener and wolfen69. I have followed you suggestions both and got the codes for my remote from the website but the lirc is still not working with vlc. irw can shows my remote keys correctly. it seems that only vlc is not cooperating. the command "vlc -I lirc" also can't help.

The same remote control has been installed on other PC successfully and works fine with vlc. but this one doesn't. It is very frustrated as I spent a lot of time on this.

---

### Post by kzutter on 2009-04-28
I could not figurethis out until I found that the -I in "vlc -I lirc" is a CAPITAL I as in Ink, not a lower case l as in love.

Also vlc opens in hidden (no skin) mode, which made it even more confusing.

I now use the command "vlc -I lirc cdda://" to launch an audio CD. There is still no visable interface, but that is OK with me.

---

### Post by jis on 2009-08-02
You can run "vlc --control lirc", instead, if you want to have the usual GUI, too.

---

### Post by jis on 2009-08-02
.. or add line 
```
control=lirc
```
in ~/.config/vlc/vlcrc to make the choice default. However, sometimes it has occured that VLC rewrites the file by no obvious reason.

---

### Post by mc4man on 2009-08-02
> However, sometimes it has occured that VLC rewrites the file by no obvious reason. 

vlcrc is an 'odd' file, some changes in there will stick, most will revert when vlc is started. It is more reflective of changes made in the gui -> Tools -> Preferences

(( in this case I believe 'show settings - all', interface -> control interfaces

Many times a choice is entered into a dialog box where add. parameters sometimes can be added ( somewhat risky

---

