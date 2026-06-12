---
title: "Compiz at bootup?"
date: 2009-08-10
forum: Multimedia Software
---

### Post by beak02 on 2009-08-10
Hi,

I can't quite pinpoint when this problem started so wondered if anyone had experienced anything similar in the past.

I have Avant Window Management installed and recently it refuses to run at bootup.  In addition, my desktop effects disable at bootup.

Rather strangely the situation can be resolved by opening up a terminal and runing 'compiz' or 'compiz -fusion'.

Any suggestions as to what to do to resolve this?  It's inconvenient to compiz at the every bootup.

Thanks in advance.

Luke

---

### Post by aimata on 2009-08-10
I would love to know a solution to this as I have the same problem:(

---

### Post by Raffles10 on 2009-08-10
You can load compiz at boot using the compiz fusion icon:

```
sudo apt-get install fusion-icon
```

'Description: tray icon to launch and manage Compiz Fusion. This package contains a tray icon that allows you to easily enable, disable and restart Compiz, and change the currently used window manager and/or window decorator.'

Add it to your startup applications and it sits in your sys tray.

---

### Post by mcduck on 2009-08-10
Make sure you have desktop effects enabled in System/Preferences/Appearance.

If it's enabled but Compiz still doesn't load on startup, go to System/Preferences/Startup Applications and add "compiz --replace" to startup programs.

---

### Post by aimata on 2009-08-11
awesome that work for me thanks :)

---

### Post by popper668 on 2011-10-07
what is the command would I add at "add startup program"?

[ATTACH]203755[/ATTACH]

thank you in advance.

---

### Post by beew on 2011-10-07
> **popper668 said:**
> what is the command would I add at "add startup program"?

[ATTACH]203755[/ATTACH]

thank you in advance./usr/bin/compiz

"compiz --replace" means you start some other wm first and then replace it with compiz, it is unnecessary long winded if you want to use compiz only anyway.

---

### Post by popper668 on 2011-10-07
i am only trying to launch the compiz fusion icon at startup. just lookink for what i would enter in the command line.

---

### Post by beew on 2011-10-07
> **popper668 said:**
> i am only trying to launch the compiz fusion icon at startup. just lookink for what i would enter in the command line.

The command is ```
fusion-icon --no-start
```

Don't ask me why it seems to say the opposite.

---

### Post by popper668 on 2011-10-07
thank you beew ;)

---

