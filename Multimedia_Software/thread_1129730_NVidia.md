---
title: "NVidia?"
date: 2009-04-19
forum: Multimedia Software
---

### Post by JMan152 on 2009-04-19
How do I determine what version of NVidia I want to install?

Thanks!

JMan152

---

### Post by doas777 on 2009-04-19
> **JMan152 said:**
> How do I determine what version of NVidia I want to install?

Thanks!

JMan152

is the restricted drivers manager offering multiple versions? if so give the latest one a try.

what kind of card do you have?

---

### Post by inobe on 2009-04-19
> **JMan152 said:**
> How do I determine what version of NVidia I want to install?

Thanks!

JMan152

```
dpkg -l | grep nvidia
```

or```
glxinfo
```


or```
nvidia-settings -q NvidiaDriverVersion
```

---

### Post by JMan152 on 2009-04-19
Thanks for the help this led me down the path and I figured it out.  However now I'm having a really hard time finding how to change the font size for text such as the internet address bar, roll over text, etc.  Do you know where that setting is?

---

