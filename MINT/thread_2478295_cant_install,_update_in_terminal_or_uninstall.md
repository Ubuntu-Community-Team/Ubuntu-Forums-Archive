---
title: "cant install, update in terminal or uninstall"
date: 2022-08-22
forum: MINT
---

### Post by trevster99 on 2022-08-22
im so lost right now ive searched and searched on what to do but everything i try fails.  i have a couple problems.  here is the error message i get when i try anything with terminal.


E: Type '“deb' is not known on line 7 in source list /etc/apt/sources.list
E: The list of sources could not be read.

im using linux mint (cinnamon)

my second issue has to do with booting 


[COLOR=#232629][FONT=ui-monospace]ata4: COMRESET failed (errno=16)  i get 4 of these errors.

[/FONT][/COLOR]im newish to this. so i hope you can take it easy on me

---

### Post by &amp;KyT$0P# on 2022-08-22
> **trevster99 said:**
> here is the error message i get when i try anything with terminal.


E: Type '“deb' is not known on line 7 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Please post the output from running this command in Terminal -
```
cat /etc/apt/sources.list
```

---

### Post by trevster99 on 2022-08-22
#deb cdrom:[Linux Mint 20.3 _Una_ - Release amd64 20220104]/ focal contrib main
# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
&#8220;deb [https://assets.checkra.in/debian](https://assets.checkra.in/debian) /&#8221;

---

### Post by howefield on 2022-08-22
Thread moved to the "*MINT*" forum.

---

### Post by &amp;KyT$0P# on 2022-08-22
That looks very wrong.  I would suggest backing up your important data and doing a completely new, clean install of the OS.

---

### Post by ajgreeny on 2022-08-22
Not sure if this will help but see what is in **/etc/apt/sources.list.save**

There may be nothing there but in my Xubuntu 22.04 it looks to be very similar to **/etc/apt/sources.list**

It may require some edits to get absolutely correct but it could be a starting point for you.  My only question would be; if that file is missing or incorrect, what else was also corrupt when you installed?

---

