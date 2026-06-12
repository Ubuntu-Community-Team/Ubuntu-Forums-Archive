---
title: "VNC startup"
date: 2012-12-03
forum: Mythbuntu
---

### Post by whoppr on 2012-12-03
Hi...

I was curious if someone knows where and how MythBuntu starts VNC at boot?  I looked in services and rcx.d, especially rc2.d since I believe the runlevel is 2.

I currently use MythBuntu but use XBMC quite a lot and was toying with trying XBuntu and would like to replicate how Myth starts the VNC server at boot.

Thanks

---

### Post by nickrout on 2012-12-04
> **whoppr said:**
> Hi...

I was curious if someone knows where and how MythBuntu starts VNC at boot?  I looked in services and rcx.d, especially rc2.d since I believe the runlevel is 2.

I currently use MythBuntu but use XBMC quite a lot and was toying with trying XBuntu and would like to replicate how Myth starts the VNC server at boot.

ThanksI believe that it doesn't start at boot but on logon by the user that runs mythfrontend. There is no point having x11vnc running The commandline thta my (10.04 myth 0.25) runs is ```
x11vnc -rfbauth /home/nick/.vnc/passwd -rfbport 5900 -shared -forever -nowf -norc -notruecolor -bg -xkb
```

Where the hell it is run from I cannot find. I remember looking once and it was quite hard to find.

---

### Post by whoppr on 2012-12-06
Thanks for the response.  I saw the same if not similar command when I did a 'ps aux'

I just could not for the life of me figure out where it is started.  Tried init.d, rc2.d, .bashrc.  Still cant find it.  I can probably figure out how to start it but more bugged me that I could not figure out how Myth starts it.

I would imagine one of those flags allows for :0 to  be shared rather than another VNC sessions started.

Thanks again

---

### Post by steeldriver on 2012-12-06
> **nickrout said:**
> I remember looking once and it was quite hard to find.

me too (was looking for the same reason) - it's /usr/share/mythbuntu/session.sh I think - but I can't remember where in the login / session startup that gets called from

EDIT:  it's from /usr/share/xsessions/mythbuntu.desktop

```
$ cat /usr/share/xsessions/mythbuntu.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Mythbuntu Session
Comment=Use this session to boot into mythbuntu.
Exec=/usr/share/mythbuntu/session.sh
Icon=
Type=Application

```

---

