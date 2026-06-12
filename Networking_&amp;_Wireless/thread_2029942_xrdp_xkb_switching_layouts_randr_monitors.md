---
title: "xrdp xkb switching layouts randr monitors"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by andrewanswer on 2012-07-20
Hi All,

I have two problems after logging to my Ubuntu 12.04 via xrdp from standard Windows Remote Desktop.

I install xrdp as usual
```
sudo apt-get install xrdp
echo "gnome-session --session=ubuntu-2d" > ~/.xsession

```

(second line taken from [http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/](http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/) , I don't look Ubuntu taskbar without it)

1) Now I can't switch layouts us/ru: shortcuts don't work, Keybord Layouts - "+" (Add layout) and Parameters dialogs is empty.  "setxkbmap" says "XKB extension not present on :10.0".

Googling "XKB extension not present on :10.0" return something like XKB not integrated into XRDP totally.
[http://www.mail-archive.com/xrdp-devel@lists.sourceforge.net/msg01032.html](http://www.mail-archive.com/xrdp-devel@lists.sourceforge.net/msg01032.html)

Can I configure my xrdp to support switching layouts without programming, build from sources, or installing FreeNX VNC smth else?

2) Go to Monitors says "RANDR extension is too old (must be at least 1.2)" Why? These problems is linked? Please describe.

Thanks, Andrew

---

