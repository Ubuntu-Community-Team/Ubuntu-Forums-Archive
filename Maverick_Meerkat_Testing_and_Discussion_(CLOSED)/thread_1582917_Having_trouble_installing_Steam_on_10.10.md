---
title: "Having trouble installing Steam on 10.10"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by RickJC on 2010-09-27
Morning all,

I upgraded to 10.10 this weekend and am loving it, makes my laptop feel a lot faster. Trouble I'm having is I can't get steam to install and I'm wondering if anyone else has had trouble or managed to get it working?

I've read around and it appears you have to use Wine to install it, which is fine, I've downloaded and installed the Wine Tricks package also but the problem I'm getting is when I'm trying to install Steam. I keep getting an error message saying unable to execute file.

I've tried doing it with Wine and the msiexe thing but same message. I'll post the full error message when I get home but just wondered if anyone else had trouble with it in 10.10?

---

### Post by s.fox on 2010-09-27
Thread moved to [Maverick Meerkat Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=385")

---

### Post by mc4man on 2010-09-27
I have an old steam account though have long since forgotten the username/password so can't test how it runs. As far as installing steam it seems straightforward, no need for winetricks ect.
Just cd to the folder holding the installer and this worked fine here

```
wine msiexec /i SteamInstall.msi
```
I guess you could enable the x-bit in the permissions of the installer though no need to if run with wine versus the  by default hobbled 'wine windows program loader' (easily reverted if desired

---

### Post by RickJC on 2010-09-27
> **mc4man said:**
> I have an old steam account though have long since forgotten the username/password so can't test how it runs. As far as installing steam it seems straightforward, no need for winetricks ect.
Just cd to the folder holding the installer and this worked fine here

```
wine msiexec /i SteamInstall.msi
```
I guess you could enable the x-bit in the permissions of the installer though no need to if run with wine versus the  by default hobbled 'wine windows program loader' (easily reverted if desired

That's for your reply, I've tried this also but getting the same message. Will try again when I get in and post the error message I'm getting.

---

### Post by meborc on 2010-09-27
go the this page - [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444) and scroll down... you can see suggestions below!

---

### Post by RickJC on 2010-09-28
Thanks for the suggestions but none of these helped, I already looked at WinHQ for an answer and no one was getting the error I was.

I managed to get it installed in the end (late last night) and what I had to do was get Wine to install it in window mode! Simple. It installed fine and it works...ok, only a few little glitches but I'm ok with it.

Thanks again for the help.

---

