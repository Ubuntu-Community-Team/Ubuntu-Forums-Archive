---
title: "two-digit file names under sound juicer"
date: 2009-03-22
forum: Multimedia Software
---

### Post by fballem on 2009-03-22
When I'm extracting a CD using Sound-Juicer, I used to have an option to include a leading '0' (zero) if the Track number was a single digit. I don't see that option on the current version of Sound-Juicer (I'm running 9.04).

Can anyone tell me how to set up that option? If not, is there a CD Ripper that does have that option?

Thanks,

---

### Post by skinnymonkey on 2009-05-28
Bump for justice. I too would like this feature back.

---

### Post by Karloskar79 on 2009-06-30
Go into the Gnome Configuration Editor by running gconf-editor either from a run-box or terminal.

Go to Apps and then Soundjuicer.

Under "file pattern" you can set the leading zeros by changing this to %tN - %tt to give you 01 - Track Name

The full list of options can be seen under long description, but for completeness here they are:

%at -- album title
%aT -- album title (lowercase)
%aa -- album artist
%aA -- album artist (lowercase)
%as -- album artist (sortable)
%aS -- album artist (sortable lowercase)
%tn -- track number (i.e 8)
%tN -- track number, zero padded (i.e 08)
%tt -- track title
%tT -- track title (lowercase)
%ta -- track artist
%tA -- track artist (lowercase)
%ts -- track artist (sortable)
%tS -- track artist (sortable lowercase)
%dn -- disc and track number (i.e Disk 2 - 6, or 6)
%dN -- disc number, zero padded (i.e d02t06, or 06)

KO

---

### Post by coxc on 2010-03-28
This works, thanks, KO. As a footnote, the change you make with gconf-editor does not have any effect on the pre-set filename choices available by opening the Preferences window in Sound Juicer and selecting the Filename drop-down box. If you make the required gconf-editor changes and then later select something like "Number - Title" as a filename choice under Preferences, you will erase what you have done with gconf-editor and will have to re-do it.

---

