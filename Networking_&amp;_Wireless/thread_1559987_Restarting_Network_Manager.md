---
title: "Restarting Network Manager"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by Oxwivi on 2010-08-24
Is there a way to restart the Network Manager (nm-applet) directly in one command instead of this two commands?
```

killall nm-applet
nm-applet

```

---

### Post by terdon on 2010-08-24
Just do this:
```
killall nm-applet; nm-applet
```

Alternatively, you can add an alias to your ~/.bashrc file. Just edit the file and add this line:

```
alias restart-nm='killall nm-applet; nm-applet'
```

Then open a new terminal and run```
restart-nm
```

---

### Post by Oxwivi on 2010-08-24
Thanks for the tip. Now I know how to create shortcut command as well. Thanks again!

---

### Post by terdon on 2010-08-24
You're very welcome. :)

---

