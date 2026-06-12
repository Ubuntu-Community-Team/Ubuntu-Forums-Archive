---
title: "Why does Mythwelcome start Mythfrontend after ACPI wakeup?"
date: 2008-08-04
forum: Mythbuntu
---

### Post by Markus72 on 2008-08-04
Hi,

until now I used an installation of mythtv which I did myself.
When the PC started after an ACPI wakeup only mythwelcome was started.
After the recording it automatically shut down.

Now with mythbuntu the shutdown if only mythwelcome is running works fine but after the ACPI wakeup, I detected that mythfrontend has started, too, preventing the automatic shutdown after the recording finished.

any idea?
Thanks in advance

Markus

---

### Post by laga on 2008-08-04
I think you can configure this behaviour in mythwelcome.

---

### Post by jlagrone on 2008-08-04
I believe there is only a setting that allows you to always prevent mythwelcome from starting the front end.  If that works for you, that is the easiest thing to do, press 'i' in mythwelcome to get to the menu.

Otherwise, I was having similar problems and noticed that mythwelcome was starting up before the backend was started.  Thus, when mythwelcome asked the database whether or not it was a scheduled startup it got no response.  So it apparently thought it wasn't a scheduled start up every time.

I fixed it by editing ~/.config/autostart/mythtv.desktop and creating a short script and everything seems to be working. I was also having focus issues, so you may be able to omit the session manager parts.  And of course, play around with the sleep times to see what works for you, I suspect they could be lower, but they work for me.

mythtv.desktop
```
[Desktop Entry]
Encoding=UTF-8
Name=MythWelcome
Comment=Use this session to run MythWelcome
Exec=/usr/bin/delaymyth.sh
Icon=
Type=Application 
```

/usr/bin/delaymyth.sh
```
#!/bin/sh
sleep 5
SESSION_MANAGER=""
unset SESSION_MANAGER
/usr/bin/mythwelcome
SESSION_MANAGER=""
unset SESSION_MANAGER
sleep 2
```

---

### Post by Markus72 on 2008-08-14
Hi,

jepp, there is an option preventing the immediate start of mythfrontend.. it's called "Automatically start mythfrontend"... and I found the following description:

"Normally when mythwelcome starts up it checks to see whether the system was started to record something or because of a wakeup/shutdown period. If not it will automatically start the frontend. You can disable this feature by unchecking this option."

The situation is as follows:

when checked, mythfrontend always started even if woken up by acpi to record something... that prevented the system to shut down after recording finished.

when unchecked, mythfrontend never is started. That's less comfortable especially if you start your HTPC, take a walk to the coffee machine only to find out you left the system idle for too long and it already shut down ;-)

So - any further idea? :-)

Thanks
Markus

---

### Post by volkswagner on 2009-09-27
I know this is an old thread.  I have been trying to tweak my much neglected setup.  I have not found much info on this specific setting.

The following does not specify how to modify the field.

[http://www.mythtv.org/wiki/Mythwelcome](http://www.mythtv.org/wiki/Mythwelcome)


I too have been dealing with the FE always starting even if it wakes due to a recording.  I believe I had a syntax error and am testing now.

I will update to see if the following setting works with the check box enabled for "automatically start FE".

Startup Command = /usr/bin/mythwlecome $status

I used to have 

Startup Command = /usr/bin/mythwelcome $user

---

