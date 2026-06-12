---
title: "Resolution error not totally solved"
date: 2011-05-05
forum: Multimedia Software
---

### Post by tuberculo on 2011-05-05
Hi, today the resolution in my monitor were wrong when I logged in. It was 1024x768 and the correct one is 1680x1050. I have found this page: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution). 
The command "xrandr -output DVI-0 --mode 1680x1050" almost solved the problem. I said almost because the wallpaper is weird now. The following screenshot shows the problem.
Can someone help me?

```

gabriel@principal:~$ lspci | grep VGA
04:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]

```

---

