---
title: "Having problems with Envy and Automatix."
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by enopepsoo on 2006-09-16
Hello,

I am installing a new system with a NVidia 6500 pci-e (if that makes any difference) card.

First I tried the NVidia driver in automatix, upon the restart, I got the blue screen sating that X would not be starting. :roll:   So I copied the backup xorg.conf over the broken one, and I was back up and running.

Then I tried the envy script, and got a much boringer error.  The anonymous user access did not work for the ftp. ](*,) Does anyone have any advice for setting up the 6500 cards?

Thanks, all.

---

### Post by arnieboy on 2006-09-16
> **enopepsoo said:**
> Hello,

I am installing a new system with a NVidia 6500 pci-e (if that makes any difference) card.

First I tried the NVidia driver in automatix, upon the restart, I got the blue screen sating that X would not be starting. :roll:   So I copied the backup xorg.conf over the broken one, and I was back up and running.

Then I tried the envy script, and got a much boringer error.  The anonymous user access did not work for the ftp. ](*,) Does anyone have any advice for setting up the 6500 cards?

Thanks, all.

can u please paste the result of the following command?
```
lspci -n | grep "0300" | cut -d " " -f3 | sed s/.*://
```

---

### Post by enopepsoo on 2006-09-16
> **arnieboy said:**
> can u please paste the result of the following command?
```
lspci -n | grep "0300" | cut -d " " -f3 | sed s/.*://
```

Hello,

The response is "0160".

I did get envy to work, but I am not sure that it installed proper drivers.  I went into google earth and the rendering was slow and weird.  I would have little antarcticas and south americas all over the place, instead of the proper terrain.  Also, a much bigger deal was that envy removed my amd k8 smp headers and, when I reinstalled them via synaptic, X stopped working.

Right now I am using the nvidia driver in xorg.conf and it works, but no gl.

Thanks for any help!  :lol:

---

### Post by tseliot on 2006-09-17
> **enopepsoo said:**
> Hello,

The response is "0160".

I did get envy to work, but I am not sure that it installed proper drivers.  I went into google earth and the rendering was slow and weird.  I would have little antarcticas and south americas all over the place, instead of the proper terrain.  Also, a much bigger deal was that envy removed my amd k8 smp headers and, when I reinstalled them via synaptic, X stopped working.

Right now I am using the nvidia driver in xorg.conf and it works, but no gl.

Thanks for any help!  :lol:

post the result of this command:
```
glxinfo | grep direct
```

---

### Post by enopepsoo on 2006-09-17
> **tseliot said:**
> post the result of this command:
```
glxinfo | grep direct
```

Hello!  It said this:

```
eno@ubuntu:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Sorry if this was not the info you were looking for.  I am sure it means something though :grin: 

Thanks again,

---

### Post by tseliot on 2006-09-17
> **enopepsoo said:**
> Hello!  It said this:

```
eno@ubuntu:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Sorry if this was not the info you were looking for.  I am sure it means something though :grin: 

Thanks again,
There's a problem.

Try using Envy's "uninstall" function and then use the "install" function

---

### Post by enopepsoo on 2006-09-17
now "glxinfo | grep direct" says "direct rendering: Yes."  Thanks for your help.  I do have a couple of questions, though.

[LIST=1]
[*]I have noticed that installing using envy removes my amd k8 smp headers.  Is this bad?
[*]In google earth, the textures just pop up in random places and I can't see anything.  This is probably something for a different thread, but I just though I would mention it because it may indicate a problem with the nvidia driver.
[/LIST]

Thanks to both of you for your help!  :grin:

---

### Post by tseliot on 2006-09-17
> **enopepsoo said:**
> now "glxinfo | grep direct" says "direct rendering: Yes."  Thanks for your help.  I do have a couple of questions, though.

[LIST=1]
[*]I have noticed that installing using envy removes my amd k8 smp headers.  Is this bad?
it removes the restricted modules. And no, it's not bad

> **enopepsoo said:**
> [*]In google earth, the textures just pop up in random places and I can't see anything.  This is probably something for a different thread, but I just though I would mention it because it may indicate a problem with the nvidia driver.
[/LIST]

Thanks to both of you for your help!  :grin:
I wouldn't know how to help you with that.

---

### Post by enopepsoo on 2006-09-17
thanks for writing the script, and for your help.  If you are ever in Toronto, I will buy you a beer!:-)

---

### Post by Odinist on 2006-09-17
> **enopepsoo said:**
> thanks for writing the script, and for your help.  If you are ever in Toronto, I will buy you a beer!:-)

I think he's pretty much guaranteed beer anywhere he goes, so long as there's an Ubuntu user that has an NVIDIA card in their computer. =)

---

