---
title: "video resolution problems"
date: 2014-07-27
forum: Multimedia Software
---

### Post by brian665 on 2014-07-27
Not sure if this is the right place to post this but here goes.

I recently upgraded from Ubuntu 11 to 14.  I am using an nvidia graphics card and downloaded the latest drivers for it.  However, I don't seem to be able to access any higher resolutions.   I am using Windowmaker as my preferred GUI and everything appears large, basically.  Despite researching on the web, I have been unable to find any easy means to find out what resolution my system is using and how to increase it.   Can anybody provide any help?

---

### Post by Yellow Pasque on 2014-07-27
Start with output of:
```
xrandr -q
```

---

### Post by SeijiSensei on 2014-07-27
You should be using NVIDIA's own utility for this purpose.  It's usually called "NVIDIA X Server Settings" in the menus.

---

### Post by brian665 on 2014-07-27
> **SeijiSensei said:**
> You should be using NVIDIA's own utility for this purpose.  It's usually called "NVIDIA X Server Settings" in the menus.

I cannot find that option in my Windowmaker menu.  Do you know how to start it from the CLI so that I can add it?

---

### Post by SeijiSensei on 2014-07-27
I believe it's called simply "nvidia-settings".  I can't tell at the moment since I'm not on my machine with the NVIDIA card. 

Type "nvidia" at the command prompt and hit tab.  You'll see all the possible completions.  Try ones that make sense.

---

### Post by brian665 on 2014-07-28
> **Temüjin said:**
> Start with output of:
```
xrandr -q
```

OK, I get the following
```

# xrandr -q
No protocol specified
Can't open display :0
# 

```

---

### Post by brian665 on 2014-07-28
> **SeijiSensei said:**
> I believe it's called simply "nvidia-settings".  I can't tell at the moment since I'm not on my machine with the NVIDIA card. 

Type "nvidia" at the command prompt and hit tab.  You'll see all the possible completions.  Try ones that make sense.

I found something called "xvidtune" (see attached picture).  Is this what you mean?

---

### Post by brian665 on 2014-07-28
OK, I've solved this, I think.  I logged into KDE and found nvideo-settings worked.  I am unsure why it won't work in Windowmaker but it's allowed me to change the screen resolution and from that I've found the right line in the xorg.conf file which I've now changed to the resolution I wanted 1680x1050.

Thanks all of you for your help.

---

