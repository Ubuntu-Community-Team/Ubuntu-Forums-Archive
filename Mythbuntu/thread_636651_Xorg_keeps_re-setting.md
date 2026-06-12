---
title: "Xorg keeps re-setting"
date: 2007-12-10
forum: Mythbuntu
---

### Post by ebike on 2007-12-10
Hi All,

I installed mythbuntu fine on my mythtv box (I had previously used ubuntu with a manual installation of mythtv, but thought I would try Mythbuntu this time).

During the install and subsequently I have had several times where my X session has died and I am presented with a new login screen.

It seems to happen most often at the moment when I am watching some old recordings from my previous mythtv installation (I had saved the mysql database and restored ..)

I have had a look at the xorg log file, and there is nothing reported.
I notice in the log file that composite support is enabled, is there a possibility that that is the problem? If so, how do I disable it.

Any suggestions most welcome ...:-k

---

### Post by superm1 on 2007-12-10
Do you have proprietary drivers activated yet?  If not, do so.

---

### Post by ebike on 2007-12-12
Yes, I do. I have nvidia drivers installed. I will go back to the "nv" driver to see if it is nvidia that is the problem ..

---

### Post by superm1 on 2007-12-12
Check out your dmesg and /var/log/Xorg.0.log* see why its crashing.

---

### Post by ebike on 2007-12-12
As I stated in my original post (please read again. .) There was no error reported in the xorg log file .....:confused:

---

### Post by superm1 on 2007-12-12
> **ebike said:**
> As I stated in my original post (please read again. .) There was no error reported in the xorg log file .....:confused:
Sorry, mixing up threads and forgetting thread history :)
This is awfully bizarre.  Now its possible that you were always looking /var/log/Xorg.0.log.  This log is renamed to /var/log/Xorg.0.log.old and then a fresh one started every time you start X.

So you checked the '.old' one too?

I'm reluctant to say that composite would have been causing issues.  At least I haven't seen complaints out of anyone particularly because of it.

---

### Post by ebike on 2007-12-16
Yes, checked all versions of the log file. When it happens again, I will repeat to see if there is anything new.

Can anyone tell me how to turn of Composite, to see if that is the problem?

---

