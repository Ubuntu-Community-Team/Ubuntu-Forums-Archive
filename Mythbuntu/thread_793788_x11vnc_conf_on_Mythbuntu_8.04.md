---
title: "x11vnc conf on Mythbuntu 8.04"
date: 2008-05-14
forum: Mythbuntu
---

### Post by mabiuso on 2008-05-14
I have enabled VNC in the control panel and VNC works like a charm.
Well, now how do I change the default listening port? 
I do not seem to find the startup command line or conf file anywhere.

Thanx

---

### Post by zhuqing789 on 2008-05-14
The fourth [wow power leveling](http://www.wow-powerleveling.org) latest game in [wow power leveling](http://www.xowow.com) Warcraft series is ‘[wow power leveling](http://www.powerlevelingweb.com)’. Also known as [wow power leveling](http://www.igsstar.com), it represents a [wow power leveling](http://www.wowgoldweb.com) multiplayer online [wow power leveling](http://www.powerleveling-wow.com/siteMap.asp) game, the best of [wow power leveling](http://www.powerleveling-wow.com) kind. Initially, it was [wow gold](http://www.wow-powerleveling.org) it be released in 2001, but [wow powerleveling](http://www.powerleveling-wow.com) was delayed [wow powerleveling](http://www.powerlevelingweb.com) 2004, thus [wow powerleveling](http://www.xowow.com) the 10 years of[wow powerleveling](http://www.wow-powerleveling.org) franchise of this[wow gold](http://www.xowow.com) series. The [world of warcraft power leveling](http://www.powerlevelingweb.com) was not [world of warcraft power leveling](http://www.wow-powerleveling.org/wow+power+leveling.html)fulfilling, because [wow power level](http://www.powerleveling-wow.com/siteMap.asp)problems with [wow power level](http://www.powerlevelingweb.com) server’s stability [power leveling wow](http://www.powerleveling-wow.com/siteMap.asp) performance occurred, but [power leveling wow](http://www.xowow.com) game still [power leveling wow](http://www.powerlevelingweb.com) a financial success [powerleveling wow](http://www.powerleveling-wow.com/siteMap.asp) the most [powerleveling wow](http://www.xowow.com) game of its kind. The number [cheap wow power leveling ](http://www.powerlevelingweb.com) users that play [Maple Story mesos](http://www.igsstar.com/Maple-Story-mesos-us/), exceeds 8.5 [MapleStory mesos](http://www.igsstar.com/Maple-Story-mesos-us/), worldwide.As a form [ms mesos](http://www.igsstar.com/Maple-Story-mesos-us/),recognition for [mesos](http://www.igsstar.com/Maple-Story-mesos-us/),outstanding popularity, the game [SilkRoad Gold](http://www.igsstar.com/Silkroad-Online-Gold/), received a[SRO Gold](http://www.igsstar.com/Silkroad-Online-Gold/), of awards. Now the question [eq2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), why is [eq2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), game [eq2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), popular? For anyone[EverQuest 2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), played the previous [EverQuest 2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), and [EverQuest 2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), already initiated [lotro gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the mysterious world [lotr gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the breathtaking [Lord of the Rings online Gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), this [Rolex Replica](http://www.watchreplicashop.com/) nothing but an [Replica Rolex](http://www.watchreplicashop.com/) adventure that continues the story of ‘Warcraft III: Frozen Throne’, four years after conclusion, in the world of Azeroth. The game is online role-playing, the previous versions being online and offline strategy games. The major thrills and unique features are present as in every Blizzard game.

---

### Post by leftler on 2008-05-21
I also need to know, I am using win2vnc on my client side and if it receives a bell from x11vnc it spikes to 100% cpu usage, where can i find the conf file or the script that launches it so i can add the -nobell otpion.

---

### Post by krunge on 2008-05-21
> **leftler said:**
> I also need to know, I am using win2vnc on my client side and if it receives a bell from x11vnc it spikes to 100% cpu usage, where can i find the conf file or the script that launches it so i can add the -nobell otpion.

You might also want to add the -nofb option for win2vnc use, no?

---

### Post by hillsy on 2009-01-02
I don't want to do a "me too" to an old thread, but did this ever get answered? I need to change some startup parameters for x11vnc and can't for the life of me see where the process is called from or configured. 

This is on Intrepid, with the VNC service set up via the control centre.

---

### Post by krunge on 2009-01-02
> **hillsy said:**
> I don't want to do a "me too" to an old thread, but did this ever get answered? I need to change some startup parameters for x11vnc and can't for the life of me see where the process is called from or configured. 

This is on Intrepid, with the VNC service set up via the control centre.
Does Mythtv actually have a configuration interface for x11vnc?  Usually VNC   configuration via GUI is for either vino (GNOME) or krfb (KDE).

In any event you might be able to put "x11vnc &" in your X session startup. Or "x11vnc -rfbport 5900 &" to force the port number used.

---

### Post by kpatz on 2009-02-13
There's no configuration interface in mythbuntu for VNC, other than to set the password, that I've been able to find.

I did find a way however to stop Mythbuntu from launching x11vnc automatically, so that you can launch it yourself manually with your own parameters.

Mythbuntu launches x11vnc with these options (as determined with a ps -ef):

> x11vnc -rfbauth /root/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg

To stop Mythbuntu from launching x11vnc automatically, the file /root/.vnc/passwd needs to NOT exist.  If you want to use the password, rename the file, and then when you launch x11vnc yourself, specify the new file in the -rfbauth option.

With the password file out of the way, you can use any of a number of techniques to launch x11vnc.  I used xinetd, so that x11vnc isn't running until a connection request comes in.

---

### Post by krunge on 2009-02-13
> **kpatz said:**
> 

Mythbuntu launches x11vnc with these options (as determined with a ps -ef):

x11vnc -rfbauth /root/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg


Do you know which config file has this command embedded in it?

Could you look for X start up script files named "Xsetup" or "Default" on your myth system (I don't have a myth system to check.)

The locate(1) command may help you locate them. Otherwise find(1).

At one point in time they would have been found in /etc/gdm/Init/Default or /etc/X11/xdm/Xsetup, but that may have changed.

If you find it, please post the full path to the file and the x11vnc line(s) in it.  Then people may be able to modify x11vnc settings on myth.

---

### Post by upan on 2009-02-27
> **krunge said:**
> Do you know which config file has this command embedded in it?
...
If you find it, please post the full path to the file and the x11vnc line(s) in it.  Then people may be able to modify x11vnc settings on myth.

Try /usr/share/mythbuntu/session.sh. The x11vnc line is easy to find ;-)

Look out for permissions on the password file (/root.vnc/passwd). The x11vnc is normally started as the mythtv user (whichever user you chose as the automatic login user) but the password file is under the root user.

Understand the security issues (with vnc password files) before making this more readable. A possible change could be to point the x11vnc startup to your own password file.

---

