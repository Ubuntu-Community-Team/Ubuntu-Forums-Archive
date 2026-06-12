---
title: "Videos Context Menu Doubled"
date: 2019-01-08
forum: Multimedia Software
---

### Post by Daveski17 on 2019-01-08
Hello,

I was experimenting opening &#8216;Videos&#8217; (Totem) from a context menu in Ubuntu 16.04 LTS. I noticed that there are two context choices of Videos. Either will open and run a file. I don&#8217;t know why they are doubled like this. As far as I know there is only one copy installed on my laptop. Is this a bug?

Thanks

[ATTACH=CONFIG]282152[/ATTACH][ATTACH=CONFIG]282153[/ATTACH]

---

### Post by mc4man on 2019-01-08
Likely because there are 2 different filename .desktops that have the same Name= & Exec= lines.   
I know in 18.04 there is org.gnome.Totem.desktop & totem.desktop, not sure about 16.04
run this, see what turns up
```
grep --include=\*.desktop -rnw '/usr' -e "Name=Videos"
```
And if need be ck. your home directory
```
grep --include=\*.desktop -rnw '/home' -e "Name=Videos"
```

---

### Post by Daveski17 on 2019-01-09
Thanks. I've since discovered this is a known problem. There is only one Videos in the context menu now after I ran mpv player. Edit: It's mysteriously back. #-o

---

