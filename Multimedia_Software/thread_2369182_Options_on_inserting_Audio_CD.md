---
title: "Options on inserting Audio CD"
date: 2017-08-19
forum: Multimedia Software
---

### Post by steveredshaw on 2017-08-19
When I insert an audio CD, the disc image burner prog automatically loads. I have RipperX installed for ripping CDs, however that does not show up under Settings>Preferred Applications>Removeable Media on the Other Applications list. If I click on Find New Applications the Software downloader runs.

How do I get RipperX on that list so I can get it to run automatically when an audio CD is inserted?

Thanks.........

---

### Post by mc4man on 2017-08-19
Doesn't quite sound like a ubuntu studio I recently looked at, there it was just a setting where one entered a command to use.
So you could try what would be needed in an Ubuntu install for ripperx which has a deficient .desktop
Open the desktop in a root text editor, ex. with nano or use whatever suits you
```
sudo nano /usr/share/applications/ripperx.desktop
```
On line 7 add %U to end of line (with a space , see screenshot
You could also add what I did on line 10 though it's value post install may be minimal.

---

### Post by mc4man on 2017-08-19
If ^ doesn't work try editing it in directly. Locate mimeapps.list. In 16.04 & newer it's location would be,
~/.config/mimeapps.list
The older location would be,
~/.local/share/applications/mimeapps.list
(some upgrade users may have both, in that case .config would be the active one

In the [Default Applications] section look for this line
x-content/audio-cdda=
If there replace whatever is after = with ripperx.desktop
If not there then add the line , i.e.
x-content/audio-cdda=ripperx.desktop

screen ex. of here

---

### Post by steveredshaw on 2017-08-20
Thanks, that worked a treat. What does %U signify?

---

### Post by mc4man on 2017-08-20
> **steveredshaw said:**
> Thanks, that worked a treat. What does %U signify?
Technically it means 'space separated urls'. 
Though in the case of gnome based context menus & default actions the Exec= line must end in a % letter to show up for selecting. 
(- %f, %F, %u would all worked as well...

---

### Post by steveredshaw on 2017-08-20
:KS Many thanks.....

---

