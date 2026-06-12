---
title: "Goobox installation"
date: 2008-07-31
forum: Multimedia Software
---

### Post by YoungCthulhu on 2008-07-31
I have installed Goobox but cannot get it to appear on my main menu.  I have used both Synaptic and sudo apt-get install goobox.  Both install it or rather, re-install it so I guess it is in its right location.

System > Preferences > Main Menu tool can't find it and I have tried a couple of times to create a launcher for it by right clicking on the desktop.

I get the following message when I try to run it:

> Details: Failed to execute child process "/usr/share/menu/goobox" (Permission denied)

I tried to locate the goobox file that makes the whole thing go, but the choice is rather large:  :lolflag:

> stuart@GORT:/$ locate goobox
/usr/bin/goobox
/usr/share/goobox
/usr/share/app-install/desktop/goobox.desktop
/usr/share/app-install/icons/goobox.png
/usr/share/application-registry/goobox.applications
/usr/share/applications/goobox.desktop
/usr/share/doc/goobox
/usr/share/doc/goobox/NEWS.gz
/usr/share/doc/goobox/README.Debian
/usr/share/doc/goobox/changelog.Debian.gz
/usr/share/doc/goobox/changelog.gz
/usr/share/doc/goobox/copyright
/usr/share/gconf/schemas/goobox.schemas
/usr/share/gnome/help/goobox
/usr/share/gnome/help/goobox/C
/usr/share/gnome/help/goobox/ca
/usr/share/gnome/help/goobox/es
/usr/share/gnome/help/goobox/sv
/usr/share/gnome/help/goobox/C/goobox.xml
/usr/share/gnome/help/goobox/C/legal.xml
/usr/share/gnome/help/goobox/ca/goobox.xml
/usr/share/gnome/help/goobox/es/goobox.xml
/usr/share/gnome/help/goobox/sv/goobox.xml
/usr/share/goobox/glade
/usr/share/goobox/glade/cover_chooser.glade
/usr/share/goobox/glade/extract_dialog.glade
/usr/share/goobox/glade/format_dialog.glade
/usr/share/goobox/glade/preferences.glade
/usr/share/goobox/glade/properties.glade
/usr/share/goobox/glade/ripper_dialog.glade
/usr/share/icons/hicolor/48x48/apps/goobox.png
/usr/share/locale/ar/LC_MESSAGES/goobox.mo
/usr/share/locale/bg/LC_MESSAGES/goobox.mo
/usr/share/locale/ca/LC_MESSAGES/goobox.mo
/usr/share/locale/cs/LC_MESSAGES/goobox.mo
/usr/share/locale/da/LC_MESSAGES/goobox.mo
/usr/share/locale/de/LC_MESSAGES/goobox.mo
/usr/share/locale/dz/LC_MESSAGES/goobox.mo
/usr/share/locale/el/LC_MESSAGES/goobox.mo
/usr/share/locale/en_CA/LC_MESSAGES/goobox.mo
/usr/share/locale/en_GB/LC_MESSAGES/goobox.mo
/usr/share/locale/es/LC_MESSAGES/goobox.mo
/usr/share/locale/eu/LC_MESSAGES/goobox.mo
/usr/share/locale/fi/LC_MESSAGES/goobox.mo
/usr/share/locale/fr/LC_MESSAGES/goobox.mo
/usr/share/locale/hu/LC_MESSAGES/goobox.mo
/usr/share/locale/it/LC_MESSAGES/goobox.mo
/usr/share/locale/ja/LC_MESSAGES/goobox.mo
/usr/share/locale/ko/LC_MESSAGES/goobox.mo
/usr/share/locale/lt/LC_MESSAGES/goobox.mo
/usr/share/locale/lv/LC_MESSAGES/goobox.mo
/usr/share/locale/nb/LC_MESSAGES/goobox.mo
/usr/share/locale/ne/LC_MESSAGES/goobox.mo
/usr/share/locale/nl/LC_MESSAGES/goobox.mo
/usr/share/locale/oc/LC_MESSAGES/goobox.mo
/usr/share/locale/pa/LC_MESSAGES/goobox.mo
/usr/share/locale/pl/LC_MESSAGES/goobox.mo
/usr/share/locale/pt/LC_MESSAGES/goobox.mo
/usr/share/locale/pt_BR/LC_MESSAGES/goobox.mo
/usr/share/locale/ru/LC_MESSAGES/goobox.mo
/usr/share/locale/rw/LC_MESSAGES/goobox.mo
/usr/share/locale/sq/LC_MESSAGES/goobox.mo
/usr/share/locale/sv/LC_MESSAGES/goobox.mo
/usr/share/locale/vi/LC_MESSAGES/goobox.mo
/usr/share/locale/zh_CN/LC_MESSAGES/goobox.mo
/usr/share/locale/zh_TW/LC_MESSAGES/goobox.mo
/usr/share/man/de/man1/goobox.1.gz
/usr/share/man/man1/goobox.1.gz
/usr/share/menu/goobox
/usr/share/omf/goobox
/usr/share/omf/goobox/goobox-C.omf
/usr/share/omf/goobox/goobox-ca.omf
/usr/share/omf/goobox/goobox-es.omf
/usr/share/omf/goobox/goobox-sv.omf
/usr/share/pixmaps/goobox.xpm
/var/lib/dpkg/info/goobox.list
/var/lib/dpkg/info/goobox.md5sums
/var/lib/dpkg/info/goobox.postinst
/var/lib/dpkg/info/goobox.postrm
/var/lib/dpkg/info/goobox.prerm
stuart@GORT:/$ sudo apt-get install goobox
[sudo] password for stuart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
goobox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
stuart@GORT:/$   

Can anyone tell me please:
 
[LIST=1]
[*]Where is the script/executable file that I should point the launcher to?
[*]How can I invoke a program launcher from the command line?
[*]Is it a matter of just running the launcher as root and if so, how?
[*]Should I be looking somewhere else entirely?
[/LIST]

Thankyou in advance for any suggestions or advice you may have.

Cheers

---

### Post by aeiah on 2008-07-31
what happens when you just run goobox from the terminal, or from the run dialog (alt+F2)?

---

### Post by YoungCthulhu on 2008-08-27
Thanks aeiah,

Finally managed to get around to try that and it worked :) .  I was looking for an executable file or a script to feed to the program launcher, but it worked with just "goobox".

Cheers

---

