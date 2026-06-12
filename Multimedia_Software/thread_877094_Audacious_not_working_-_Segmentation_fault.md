---
title: "Audacious not working - Segmentation fault"
date: 2008-08-01
forum: Multimedia Software
---

### Post by bimaljr on 2008-08-01
Hi,
I have just installed Kubuntu 8.04 via CD got from shipit.
I had ubuntu 8.04 in my system and audacious was working perfectly. But now I cannot even open it.

In Konsole I get this :
> bimal@brcreation:~/.config$ audacious
Segmentation fault
[email]bimal@brcreation:~/.conf[/email]ig$


Please help me on this... thank you

---

### Post by bimaljr on 2008-08-02
No one ???

---

### Post by NoVista on 2008-08-18
Did you get this resolved?

---

### Post by bimaljr on 2008-08-18
I have formatted my system and reistalled kubuntu... there are some other problem too...

---

### Post by NoVista on 2008-08-18
OK. I need help with Audacious on regular Ubuntu.

You might want to look at this other post:

[http://ubuntuforums.org/showthread.php?t=809511](http://ubuntuforums.org/showthread.php?t=809511)

Any version installs fine for me on Gutsy.
But the dreaded segmentation fault.. ..

---

### Post by bimaljr on 2008-08-19
I don't know if this will work for you, but try this :

1) Start **Adept Manager**.
2) Go to **Adept** menu. click **Manage Repositories**
3) In the **Kubuntu Software** tab, select first four option. Leave the last **Source Code** unchecked.
4) In the **Updates** tab, select **Important security updates** and **Recommended updates**. don't select **Pre-released updates** and **Unsupported updates**
5) close

This will update your system with stable version of all of your softwares... I have this problem in my Kubuntu 8.04. But I have some bad configuration in compiz so I had formated my system.

---

### Post by mardicas on 2012-04-08
I got it fixed with the following steps:
```

#go to your home directory
cd ~
#remove associated audacious files
#WARNING: This will clear your audacious settings!
rm -rf .config/audacious/
rm -rf .local/share/audacious/
rm -rf .cache/audacious/

```

---

### Post by howefield on 2012-04-08
Old thread closed.

---

