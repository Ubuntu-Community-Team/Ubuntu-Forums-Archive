---
title: "problems with Kodi and 14.04 upgrade"
date: 2015-09-20
forum: Multimedia Software
---

### Post by machs on 2015-09-20
I finally got around to upgrading my media box to 14.04.  I've cleaned up a few issues here and there but this one has currently got me stumped.   I've been running kodi (xbmc) on this machine since the lucid lynx days. 

I'm using lightdm to auto login a user "xbmc" with the session "kodi".  scripts below;

```
machs@electricMonk:~$ sudo cat /etc/lightdm/lightdm.conf 

[SeatDefaults]
autologin-guest=true
autologin-user=xbmc
autologin-user-timeout=10
autologin-session=lightdm-autologin
user-session=kodi
greeter-session=unity-greeter
#allow-guest=false
#default-user=xbmc


machs@electricMonk:~$ cat /usr/share/xsessions/kodi.desktop 
[Desktop Entry]
Name=Kodi
Comment=This session will start Kodi Media Center
Exec=kodi-standalone
TryExec=kodi-standalone
Type=Application

```

All this was working fine with 12.04 and kodi 15.0(helix).  I've upgraded to 14.04 and kodi 15.1 (Isengrad).  lightdm will log in someone and start kodi (woohoo!).  But it doesn't save any settings, it's like i'm running kodi for the first time each login.  

My /home/xbmc user doesn't have a .kodi directory any more.  The lightdm log files are showing some sort of guest login?  not clear what that is about, security perhaps?

```
[+11.48s] DEBUG: Opening guest account with command '/usr/sbin/guest-account add'
[+12.87s] DEBUG: Guest account guest-eQ18vJ setup
[+12.87s] DEBUG: Session pid=3859: Started with service 'lightdm-autologin', username 'guest-eQ18vJ'
[+12.93s] DEBUG: Session pid=3859: Authentication complete with return value 0: Success
[+12.93s] DEBUG: Seat: Session authenticated, running command
[+12.93s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+12.94s] DEBUG: Session pid=3859: Running command /usr/lib/lightdm/lightdm-guest-session /usr/sbin/lightdm-session kodi-standalone
[+12.94s] DEBUG: Creating shared data directory /var/lib/lightdm-data/guest-eQ18vJ
[+12.94s] DEBUG: Session pid=3859: Logging to .xsession-errors
[+12.98s] DEBUG: Activating VT 7
[+12.98s] DEBUG: Activating login1 session c6
[+12.99s] DEBUG: User /org/freedesktop/Accounts/User1000 changed
[+14.00s] DEBUG: User /org/freedesktop/Accounts/User1000 changed

```

has lightdm changed the way it handles account names?  is it running kodi and a guest account ? I'd like lightdm to login my xbmc user and run kodi with settings from the /home/xbmc/.kodi directory..

---

### Post by machs on 2015-09-20
haha,  I've solved it.  First line in the lightdm.conf file needs to be commented out, must be a new feature.

---

