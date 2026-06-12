---
title: "help! my wireless just stopped working"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by notatoad on 2009-02-17
following the guide here [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne), i got wireless working on my aspire one.  rebooted, everything was fine.  then i scrolled down in the guide a bit further and installed alsa 1.0.19, and chmod'd rc.local as suggested.  then i rebooted again, and now i have no wireless.  

any ideas what went wrong?  i followed the same guide on a different aspire one last week, and it is still working fine.

---

### Post by dzark on 2009-02-17
Check your current permissions on rc.local with ```
ls -l /etc/rc.local
```

maybe try 

```
sudo chmod +x /etc/rc.local

```

---

### Post by notatoad on 2009-02-17
-rwxr-xr-x, which means all can execute it, which is the way it should be, right?  also, rc.local only contains a single uncommented line: exit 0.  is this the way it should be?

---

### Post by notatoad on 2009-02-17
i added !ath5k and !acer_wmi to /etc/modules, and it's working now.  i remembered something from gentoo about !name blacklisting a module, but now i remember that /etc/modules wasn't the place, there was an array somewhere.

what have i done?

---

### Post by dzark on 2009-02-17
according to [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) there's a whole bunch of stuff that should be in your rc.local.. about 4/5ths of the way down..

---

### Post by notatoad on 2009-02-17
that's just power-management stuff though, i haven't gotten to that yet.  

now my wired network doesn't connect either.  wtf?

---

### Post by dzark on 2009-02-17
you mentioned in an earlier post you blacklisted modules.

---

### Post by notatoad on 2009-02-17
did i actually blacklist modules though, or did i actually just add meaningless crap to /etc/modules?  

anyways, i undid that and still have no wired or wireless networking.  i think i'm just going to start over, reinstall.  hopefully that will fix things.

---

