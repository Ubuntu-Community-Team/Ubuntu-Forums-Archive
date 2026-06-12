---
title: "Two copies of welcome/frontend running"
date: 2010-10-27
forum: Mythbuntu
---

### Post by PhilWig on 2010-10-27
I am running Mythbuntu 9.04 on a combined frontend + backend system and use the welcome and ACPI wakup up mechanisms.  Xfce is version 4.6.0.

This week it has started running two copies of welcome and hence two frontends too. This has given wrong sound tracks on occasions and causes closedown problems – one version of welcome needs to be closed manually (Menu/Exit) before the other can close normally.

At startup the welcome system is normally started with  > Exec=/usr/bin/mythwelcome in ~/.config/autostart /mythtv.desktop – a link to usr/share/applications/mythtv.desktop.   If I change the line to EXEC=# and reboot I only get one copy of the welcome/frontend system and domestic harmony is restored but I am still puzzled as to where this rogue version is coming from.

There are no other entries in directory ~/.config/autostart with 'welcome' in them.
I've disabled an entry in ~/Desktop/Myth.desktop which I think is just related to a desktop icon for mythwelcome but still the rogue version starts and appears to be reliable.

I've made a few recent changes, none of which seem relevant:
Reset bios after it lost boot order – it loaded XP from a test disk so I had to also reset hardware clock 
Loaded an adobe pdf reader.
Configured my Hauppauge T500 remote again - software now reliable but hardware not.  Abandoned.
Configured an MCE remote and adjusted lirc settings.   

It all seemed to start after the MCE remote was configured but that's since been disabled pending resolution of this puzzle.

Any clues on how the rogue version is starting or how to diagnose this would be appreciated.  The rogue does not appear to be putting entries in /var/log/mythtv logs.

Phil

---

### Post by LowSky on 2010-10-27
possibly two instances in rc.d?

---

### Post by PhilWig on 2010-10-28
Thanks LowSky, that's set me thinking.

A recursive grep shows no instances of mythwelcome except in comment lines anywhere in the whole /etc tree so it's not being started by an rc.d mechanism.

I expected mythfrontend and mythwelcome to come from /usr/bin but I have found another copy of mythwelcome, a link named mythfrontend and a file mythfrontend.real in directory /usr/X11R6/bin.  These are indeed the source of the second 'unwelcomed' welcome process.

Now I could just rename the spurious welcome so whatever process is starting it will quietly fail and allow the proper version to run without hindrance, but I'd still like to know what process is doing it and what I did to set it going.

Phil

---

### Post by PhilWig on 2010-11-02
I've now done more investigation - 
I have inhibited the 'normal' invocation of mythwelcome (in ~/.config/autostart/mythtv.desktop) and just allowed the 'rogue' to start.

I've then replaced mythwelcome with a script to produce diagnostics to a file - a ps -f and pstree in the hope that this would show how this rogue process is started.  I've seived out the non relevant bits and what's left is:

> 
Sun Oct 31 16:28:49 GMT 2010

ps -f
phil      3571  3327  0 16:28 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
phil      3871  3571  0 16:28 ?        00:00:00 /usr/bin/xfce4-session
phil      4007  3871  0 16:28 ?        00:00:00 /bin/bash /usr/bin/mythwelcome -session 22db31e55-3f5a-4ccc-bc1a-a84a7e11bf31_1287942126_807630
phil      4011  4007  0 16:28 ?        00:00:00 ps -f




init,1
  |-gdm,3324 --config=/etc/gdm/gdm-cdd.conf
  |   `-gdm,3327 --config=/etc/gdm/gdm-cdd.conf
  |       |-Xorg,3330 :0 -br -audit 0 -dpi 100 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
  |       `-sh,3571 /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
  |           |-ssh-agent,3841 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
  |           `-xfce4-session,3871
  |               |-mythwelcome,4007 /usr/bin/mythwelcome -session 22db31e55-3f5a-4ccc-bc1a-a84a7e11bf31_1287942126_807630
  |               |   `-pstree,4012 -aAp


Unfortunately, that does not get this newbie much further.
Can any kind soul give me a clue as to where and how this mythwelcome is being started?  thanks.

Phil

---

