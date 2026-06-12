---
title: "Bad Static in all sound sources"
date: 2009-02-14
forum: Multimedia Software
---

### Post by Roving Sign on 2009-02-14
Ok - let's take a stab at my sound issue - this is the one thing I have not been able to get working.

lspci says

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

Running an old AMD Duron 1300 on a MSI KM2M combo board...

[http://www.msicomputer.com/product/p_spec.asp?model=KM2M_Combo-L](http://www.msicomputer.com/product/p_spec.asp?model=KM2M_Combo-L)

Sound seems to play - but with lots of digital static...sounds sort of like a mistracking VHS tape or a poorly tuned FM station...

I've pecked away at the sounds options an none of the OSS/ALSA etc options make much of a difference - just different levels of static...

Thanks for any help...and Im perfectly willing to accept that I might need to buy a cheap PCI sound card...if thats what it takes...

---

### Post by Aflack on 2009-02-15
this has been happening to me forever. never found out how to fix it. i also need to know how to fix, because i have installed ubuntu a few times now. everytime i install, i go to youtube and cant watch a vid or listen to music so i go to windows. eventually i stop using ubuntu so i uninstall it. im planning to stick withit, but i need a fix also. help us :)

---

### Post by Aflack on 2009-02-15
anyone?

---

### Post by Roving Sign on 2009-02-21
Bump - even a compatible soundcard recommendation would be nice...

---

### Post by markbuntu on 2009-02-21
I have just updated my guide. You can find out some info about adjusting the AC'97 driver there. Look in the bottom of the Driver section **Other Sound card and chip drivers**. There is also a lot of other troubleshooting help there

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Roving Sign on 2009-02-28
re-thanking on this one...

Here's what worked:

Order this card form TigerDirect...had sound within minutes!

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3981743&CatId=2768](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3981743&CatId=2768)

---

