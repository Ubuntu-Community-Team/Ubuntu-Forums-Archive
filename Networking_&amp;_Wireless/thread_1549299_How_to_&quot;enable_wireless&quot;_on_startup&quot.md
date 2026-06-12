---
title: "How to &quot;enable wireless&quot; on startup&quot;"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by jackheart on 2010-08-09
My wireless works fine, but every time I boot I have to right click on the Network Manger Applet and enable wireless. Anybody know how to set this up?

---

### Post by ajgreeny on 2010-08-09
Right click and choose **edit connections**.  Highlight the active connaction and make sure the "**connect automatically**" box and "**available to all users**" are selected.  That is normally all that is needed.

---

### Post by jackheart on 2010-08-11
yeah, tried that, but all it does is make my primary home wirless connect automatically...I still have to right click every time I startup.

---

### Post by daniol on 2010-08-11
Did you mean interface is down on startup?

If that doesn't work, try to manually execute iwconfig activation command on init.d startup script

iwconfig wlan0* up

(*) whatever interface is

if you don't know how to init.d works, look for example [http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by grahammechanical on 2010-08-11
Another thing you may want to check is if you permission to use wireless in your user profile. System - Administration - Users and Groups - Advance settings - User privileges - Connect to wireless and ethernet networks. Somehow I got listed not under Administrator with access to everything but as having Custom privileges. It is possible that you are set up in the same way and not allowed access to networks. Just something to try.

regards.

---

### Post by opasnost on 2011-02-05
> try placing;
nmcli nm wifi on
in /etc/rc.local using;
sudo nano /etc/rc.local
-make sure to add the line before exit 0 in the file.
-this will instruct network manager to enable wifi on every login
-solved issue on Acer Aspire One 721, Ubuntu 10.10 x64

(looks like ([http://ubuntuforums.org/showthread.php?t=1563463](http://ubuntuforums.org/showthread.php?t=1563463)) nmcli is  only available in 10.10, I'd imagine you could accomplish the same thing  using dbus-send in other versions)

I am also using an Aspire one 721 and it worked

---

