---
title: "Running FE on other screen"
date: 2008-04-05
forum: Mythbuntu
---

### Post by zeke@moeraki.com on 2008-04-05
I have two screens on my system and I'd like to start the myth FE on screen :0.1 but I can;t figure out where the command is that modifies the startup of the FE. I can run the mythfrontend command from a terminal with the -display :0.1 option and it works find but where is the command to start the myth FE otherwise.

Thanks

john

---

### Post by .nedberg on 2008-04-05
This can be set via a setting in the frontend. Don't remember where though. But if you do not find it I have it set on my system and can look into it if you have problems.

Think it is called Xinerama screen or somthing like that

---

### Post by johnl648 on 2008-04-05
Please send me the info cause I haven't been able to figure this out at all.

Thanks

john

---

### Post by .nedberg on 2008-04-05
It is in Settings->Apperance, on the second page

Also have a look at [this page]("http://www.mythtv.org/wiki/index.php/Running_MythTV_Dual_Headed#Xinerama_.28One_X_server.2C_two_displays.29"), as you might (or might not) get mplayer on the wrong screen. Easy to fix though.

---

### Post by finlay648 on 2008-04-05
I figured out that mythbuntu uses a mythfrontend script that should pull additional options from /etc/mythtv/session-settings. Adding MYTHFRONTEND_OPTS="-display :0.1" as an option didn't work because the /usr/bin/mthfrontend script has a bug in it that prevents the options from being passed as multiple words. The fix is to change mythfrontend:

 exec /usr/bin/mythfrontend.real "$@"

to:

 exec /usr/bin/mythfrontend.real $@

John

---

