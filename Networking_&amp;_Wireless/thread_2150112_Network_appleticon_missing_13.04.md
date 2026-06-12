---
title: "Network applet/icon missing 13.04"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by benbaker79 on 2013-05-31
Hello all, first time poster here.

I have upgraded from 12.10 to 13.04 and my network/wifi icon is missing in top panel. This also happened to me in 12.10 from 12.04 but after trawling through threads and google i managed to fix it. No such luck this time and it is doing my head in. Why is this crucial applet missing from upgrades and why is it not in system preferences?

I try my best to spruik Linux, but sometimes.......!!!!

Please help. 

P.S. I'd like to say i have tried all the 'usual' fixes : nm-applet, sm-disable etc

:mad:

---

### Post by rick_james on 2013-06-17
I have the same problem, except this problem never began for me until 13.04.

The nm-applet will disappear from the notification area after minutes or hours.

Rebooting brings it back.

I also edited my NetworkManager.conf to change 'managed=false' to 'managed=true':

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=true

This made no difference.

I think I've figured out the reason why the applet disappears. Try typing this in the command line:

nm-applet

That will start it up and make it appear in the notification area near the clock.

Eventually it crashes, complaining about UTF-8 characters.  

I notice when clicking on the nm-applet icon that it sometimes displays
non-Latin characters... jibberish characters actually. Other times it will
display nonsense such as 'connected to [www.inkscape.org](www.inkscape.org)' instead of the ISP I specified in the settings.
Other times it displays the jibberish characters.

This caused the applet to crash.

Prior to 13.04 it never displayed jibberish characters or the wrong name for my ISP.

I think this may be your problem too but there seems to be no solution.

It never occurred prior to 13.04 and I've tried 11.10, 12.04 and 12.10 without a single problem.

We should go to AskUbuntu and put all the details there if no one knows how to help here.

If anyone is reading this and has this problem please let me know.

I greatly appreciate it and hope we can get this alleged bug fixed.

I can't print screen when I have the nm-applet clicked. Right now it says [www.inkscape.org](www.inkscape.org) (Fren EVDO)
next to the signal strength in nm-applet. Later it will say XX9DK (Fren EVDO) or rectangle shapes.

I updated my ATI video drivers and that didn't fix it.

Are you using ATI/AMD proprietary drivers?

---

### Post by richardsdma on 2013-10-15
the same problem here man! nm-applet crash and it seems to complain about utf-8 characters. 
mine is crashing when i use EVDO connection. 
i have little hope that this bug will be solved in 13.10....just wait and see. on 12.04, it works fine. this is tha bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1179070](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1179070)

i also use an AMD x1270 video card.

---

### Post by houstonbofh on 2013-10-16
I have noticed it just randomly abandoning it's post as well.  Makes firing up a VPN a bit tough.  So I made a script...

nmcli con up id vpn-name

Once run, the icon is back.  Look at the nmcli docs for more options.

---

### Post by richardsdma on 2013-10-18
here is what i get when i start nm-applet from terminal after it crashes. 

> rich1974@rich1974-Inspiron-1521:~$ nm-applet
** Message: applet now removed from the notification area


** (nm-applet:2478): WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries


(nm-applet:2478): GLib-CRITICAL **: g_variant_new_string: assertion 'g_utf8_validate (string, -1, NULL)' failed


and i found this, but i don't know what it means!
[https://mail.gnome.org/archives/commits-list/2012-April/msg00906.html](https://mail.gnome.org/archives/commits-list/2012-April/msg00906.html)
[https://mail.gnome.org/archives/gtk-devel-list/2008-October/msg00075.html](https://mail.gnome.org/archives/gtk-devel-list/2008-October/msg00075.html)

is there any solution for this problem?

---

### Post by houstonbofh on 2013-10-18
Is it really crashing, or is it just missing from the taskbar?

ps -ef | grep nm-applet

---

### Post by richardsdma on 2013-10-19
no, it is crashing, it does not show in "processes" tab from system monitor.

the network manager is still running.

---

### Post by prashanta2 on 2014-02-11
In my case it is just missing. When I run nm-applet from terminal I get the icon back to its place. The issue is that I cannot close terminal, for if I do, the icon goes missing again. Everytime I reboot, the icon is never there...

---

### Post by houstonbofh on 2014-03-12
In your case, it is probably trying to start too soon.  You could launch it detached. "nm-applet&"  That way you can close the shell.

---

### Post by ken0069 on 2014-07-27
I see this problem is not new and goes back a few years but there doesn't seem to be any solution that works?  Reason I bring that up is because I've been searching over the past couple of days and all I've found on the internet is stuff that sometimes works and sometimes doesn't.  I haven't seen anything that has been done directly by the developers to correct this as it seems to have shown up in Ubuntu 12 and it's still around in 14.04??  

Having said that, I've got 4 linux systems here in my house.  One has Ubuntu 14.04 with Mate and the other 3 are Linux Mint 17 with Mate.  Two of these systems are suffering the missing Network Manager icon in the system tray, one Ubuntu and one Mint.  With Ubuntu I can start Network Manager via terminal running nm-applet but this doesn't work in Mint 17?  

So does anyone know of a fix for this problem on both these Ubuntu based systems?

Thanks,

Ken

---

