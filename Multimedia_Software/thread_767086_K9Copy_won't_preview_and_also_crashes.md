---
title: "K9Copy won't preview and also crashes"
date: 2008-04-25
forum: Multimedia Software
---

### Post by TRANQU111TY on 2008-04-25
When I try to preview a titleset on my the DVD using K9Copy, my DVD burner whirs but no preview. I just decided to go ahead and burn it anyway. It then starts extracting titles after a few minutes it totally lags out my computer then crashes. I also had a problem with K9Copy taking more then 5 minutes to load up.

Please help.

---

### Post by TRANQU111TY on 2008-04-27
Bump

---

### Post by brewstah on 2008-04-27
It's possible k9copy ran into one of the newer protection schemes it can't handle.  Your best bet would be to use another app to copy the files to your hard drive first.  Assuming your intent is to make a legitimate fair-use backup for personal use:

1) Install WINE from Synaptic (Adept if you're using KDE)
2) Create a directory called temp in ~/.wine/drive_c
3) Download the winetricks script linked to in this thread:
[http://ubuntuforums.org/showthread.php?t=544502]("http://ubuntuforums.org/showthread.php?t=544502") to ~/.wine/drive_c/temp and run it.
3) Download DVDFab HD Decrypter to ~/.wine/drive_c/temp and install it using WINE.

The freeware version will only copy the files to your hard drive; removing the nasties.  Then you can use k9copy to do what you need.

---

### Post by TRANQU111TY on 2008-04-27
I'm using 8.04 now but it worked properly when I was using Ubuntu 7.10. Maybe its a compatibility issue?

---

### Post by TRANQU111TY on 2008-04-27
> **brewstah said:**
> 
2) Create a directory called temp in ~/.wine/drive_c


I assumed this directory would be hidden in my home directory but it isn't.

---

### Post by mc4man on 2008-04-27
you can do a straight up install of DVDFab HD Decrypter - no need for temp
just make sure in winecfg version is set to windows nt.4.0 or xp

edit ; ongoing thread
[http://club.cdfreaks.com/f116/dvdfab-hddecrypter-linux-220283/index5.html](http://club.cdfreaks.com/f116/dvdfab-hddecrypter-linux-220283/index5.html)

---

### Post by mc4man on 2008-04-27
@TRANQU111TY
While i almost never use defab there are rare instances where it's useful. there may be an issue with latest free release in wine. If you didn't pick up yet go here and grab 4.1.2.0 while still available just in case 5.0 is a bust (use green dl icon)  [http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

edit ; just ck. 5.0.0.0 is not a free ver. yet so you should be good to go on free 4.1.2.0

---

