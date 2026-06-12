---
title: "DarwinPorts gedit"
date: 2008-04-14
forum: Mac OSX
---

### Post by DouglasAWh on 2008-04-14
So, I've got a OS X Server and I don't like the OS X text editor and as a rule hate terminal text editors.  I stumbled upon darwinports.com, but I am having some problems.  Anybody got experience with this?  Some terminal text is below.

```

$ ./port install gedit
Error: Unable to execute port: can't create directory "/opt/local/var/macports/build": permission denied
$ sudo ./port install gedit
Error: Unable to execute port: invalid command name "configure.python"


```

Thanks!

---

### Post by scramasax on 2008-04-15
> **DouglasAWh said:**
>  I don't like the OS X text editor and as a rule hate terminal text editors.

The answer for anyone who has both those requirements is TextMate.  However, that does cost.  Smultron is a nice alternative:

[http://smultron.sourceforge.net/](http://smultron.sourceforge.net/)

Not what you asked, but Smultron is likely to give you a nicer experience than something running under x11, if a GUI app is what you want.

---

### Post by DouglasAWh on 2008-04-15
> **scramasax said:**
> 

Not what you asked, but Smultron is likely to give you a nicer experience than something running under x11, if a GUI app is what you want.

Yeah, I like Smultron, but doesn't run on the Server version of OS X for some reason.  Maybe that was just Tiger server. I suppose I should try again with Leopard.

---

