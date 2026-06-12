---
title: "Desktop effects could not be enabled!"
date: 2008-04-25
forum: Multimedia Software
---

### Post by Galban on 2008-04-25
Hi every one! Even though the fact that a pop-up is giving me headaches, I'm happy like at every new version release for Ubuntu... but, there we go again, new version of Ubuntu released means for me new issues to be fixed after install. Like most of the time at past, can't  direct rendering be enabled right out the box. This time, after a fresh install of Hardy, I tried to enable visual effects (compiz) at System> Preferences> Appearance>  Visual Effects. After pressing at "normal" a pop-up come-up telling me about the need to enable the use of the restricted drivers for my Nvidia GeForce 6200 in order to be able to activate the Visual Effects and I did it. After reboot came back to System> Preferences> Appearance>  Visual Effects and pressing on "normal" just give me a pop-up that says [COLOR="Blue"]Desktop effects could not be enabled![/COLOR].What I can say is that, just before enabling the restricted drivers for my Nvdia, I did a "glxinfo" and the direct rendenrig part says "NO". Now after restrstricted were enabled a glxinfo command is giving me this: 

```
rodolfo@amdasus:~$ glxinfo
name of display: :0.0
Illegal instruction
rodolfo@amdasus:~$ 

```


Is happening exactly the same thing when I was using the "beta" release of Hardy and the fresh install of Hardy (full release) didn't changed nothing for me about this. Envy and many thing I tried didn't give me better results. 

Any, any ideas in how can I fix this will be truly appreciated.!!! Thanks in advance.[COLOR="Black"][COLOR="Black"][COLOR="Black"][SIZE="2"][/SIZE][/COLOR][/COLOR][/COLOR]

---

### Post by Galban on 2008-04-27
It's this thread going to be my first one without answers. Well in any case it seems that  i'm not the only one and everything points towards a mayor bug on Hardy. Check this out 
[https://answers.launchpad.net/ubuntu/+question/30999]("https://answers.launchpad.net/ubuntu/+question/30999")

Please cry high and strong if you are having this problem, maybe this way Ubuntu developers will be acknowledging it.:confused:

---

### Post by lessgov2007 on 2008-05-05
Galban I've tried everything but my 6200 is still useless... I still have no OpenGL or Compiz...

Somehow I managed to have a few days of my GPU working with Hardy...  If I figure something out (not very likely but it sounds good) I'll let you know...

---

### Post by Galban on 2008-05-07
Copy that lessgov2007. Same here, if nerver I get this "cancer" fixed, i'll let you know!

---

### Post by Catalyst2Death on 2008-05-07
what video card are you using?!  some of them are blacklisted by compiz, which causes this error.  I personally don't use compiz anymore, but this is what I had to do to kill the error.  It may be unrelated as I don't recognize the glxinfo error...

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#3D_desktop_effects)

I know its for ati/gutsy, but the relevant commands are:
```

sudo gedit /usr/bin/compiz
```
find the line that says:
```

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"
```

you want to add the name of whatever driver is appropriate...

and make sure that none are explicitly blacklisted:

```
# blacklist based on the pci ids 
# BLACKLIST_PCIIDS="$T"
BLACKLIST_PCIIDS=""

```

there are some more notes in the wiki page that you should also read if you go this route.

---

### Post by MikeCheck on 2008-05-10
> **Galban said:**
> Hi every one! Even though the fact that a pop-up is giving me headaches, I'm happy like at every new version release for Ubuntu... but, there we go again, new version of Ubuntu released means for me new issues to be fixed after install. Like most of the time at past, can't  direct rendering be enabled right out the box. This time, after a fresh install of Hardy, I tried to enable visual effects (compiz) at System> Preferences> Appearance>  Visual Effects. After pressing at "normal" a pop-up come-up telling me about the need to enable the use of the restricted drivers for my Nvidia GeForce 6200 in order to be able to activate the Visual Effects and I did it. After reboot came back to System> Preferences> Appearance>  Visual Effects and pressing on "normal" just give me a pop-up that says [COLOR="Blue"]Desktop effects could not be enabled![/COLOR].What I can say is that, just before enabling the restricted drivers for my Nvdia, I did a "glxinfo" and the direct rendenrig part says "NO". Now after restrstricted were enabled a glxinfo command is giving me this: 

```
rodolfo@amdasus:~$ glxinfo
name of display: :0.0
Illegal instruction
rodolfo@amdasus:~$ 

```


Is happening exactly the same thing when I was using the "beta" release of Hardy and the fresh install of Hardy (full release) didn't changed nothing for me about this. Envy and many thing I tried didn't give me better results. 

Any, any ideas in how can I fix this will be truly appreciated.!!! Thanks in advance.[COLOR="Black"][COLOR="Black"][COLOR="Black"][SIZE="2"][/SIZE][/COLOR][/COLOR][/COLOR]


I am having the same problem with Compiz.  Also, Emerald does nothing when I select different themes.

---

### Post by Galban on 2008-05-10
It's SOLVED :). Thanks to our friend lessgov2007. PLEASE: go and read his thread, there he explains how to.

[http://ubuntuforums.org/showthread.php?t=780425]("http://ubuntuforums.org/showthread.php?t=780425")

---

