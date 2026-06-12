---
title: "trying to network share with win7 prompts me for password"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by haran_elessar on 2010-02-19
I'm having problems trying to access windows 7 through my home network when using ubuntu 9.10; when I try to access the win7 computer it asks me for a password and I have no idea which password to enter. I tried using the same password I've been using with other win7 computers in my home network but it doesn't work. Is anyone else experiencing this issue? what should I do?

---

### Post by haran_elessar on 2010-02-20
I don't know if this helps but here is a screenshot so that you can see the password prompt I'm talking about; as I said before I never set any password for this and I've tried the password win7 gives me for sharing with other computers and it didn't work.

[IMG][[img]http://www.ubuntu-pics.de/thumb/43476/screenshot_FElINV.png[/img]](http://www.ubuntu-pics.de/bild/43476/screenshot_FElINV.png)[/IMG]

---

### Post by johnson.d on 2010-02-24
You can probably try mounting the share using the command line as it will tell you the error for the failure of access. You can do this by using the following command:

```
$ mount  -t  cifs  //<ip-address>/<Share-name>/  /<mount-point>/  -o  user=<user-id>
```

---

### Post by coskierken on 2010-02-24
Put in the same password that you use to log into the Win7 machine.  In Win7 (I know I am giving advice on Win7 ](*,)), you can set it to not require password for sharing.

---

### Post by youngdaddytc on 2010-03-05
> **coskierken said:**
> Put in the same password that you use to log into the Win7 machine.  In Win7 (I know I am giving advice on Win7 ](*,)), you can set it to not require password for sharing.

same problem, changing the settings in win7 for requiring password has no effect.  i read on another forum that this is a bug, but was hoping someone would have found the solution.

---

