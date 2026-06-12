---
title: "Compiz not working"
date: 2011-03-31
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sudoer541 on 2011-03-31
I just installed the latest beta and Compiz seems to be gone. 
There is no way to enable it.
I went to the USC and it seems to be there, but when I right click on the desktop, there is no "effects" tab on the top. 
I downloaded the compiz control panel and when I make changes to the settings... nothing happens. 

info:
ubuntu natty Beta 64 bit (I tried 32 bit as well)
Video card: ATI 9250 @ 128MB

Anyone experiencing this?

---

### Post by 5149.5 on 2011-03-31
I'm seeing strange things with compiz as well. When I did get it to run, checking of boxes to change configuration, caused momentary blank screens. I also got an error when trying to install simple-ccsm using synaptic. The error was un-resolvable dependencies.

---

### Post by cariboo on 2011-03-31
Compiz is enabled by default in Unity. I would suggest you install compizconfig-settings-manager to make sure the Unity is enabled.

---

### Post by 5149.5 on 2011-03-31
> **cariboo907 said:**
> Compiz is enabled by default in Unity. I would suggest you install compizconfig-settings-manager to make sure the Unity is enabled.

I'm trying to do just that but there seems to be an issue with the repositories. I am getting errors in synaptic telling me to check my network connection and I noticed one of the repositories had a hashsum error.

---

### Post by 5149.5 on 2011-03-31
And here is what happens when I try to install from USC.

```
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```

---

### Post by 5149.5 on 2011-03-31
Synaptic error:

```
simple-ccsm:
 Depends: python-compizconfig but it is not going to be installed
 Depends: compizconfig-settings-manager but it is not going to be installed
```

---

### Post by cariboo on 2011-04-01
Are you using the Main Server, or one that may not be up to date? I doing an update on my netbook at the moment, and it seems to be OK.

---

### Post by 5149.5 on 2011-04-01
> **cariboo907 said:**
> Are you using the Main Server, or one that may not be up to date? I doing an update on my netbook at the moment, and it seems to be OK.

I started out using the main server and then switched to the mirror and gave that a try. I had the same results with both servers.

---

### Post by dino99 on 2011-04-01
try after cleaning the sources:

sudo rm /var/cache/apt/archives/*

then: update & sudo apt-get install -f

---

### Post by cariboo on 2011-04-01
Isn't it easier to use: 

```
sudo apt-get clean
``` 

to removed the archived packages in /var/cache/apt/archives?

---

### Post by 5149.5 on 2011-04-01
> **dino99 said:**
> try after cleaning the sources:

sudo rm /var/cache/apt/archives/*

then: update & sudo apt-get install -f  

Been there and done that. Thanks though.

---

### Post by mc4man on 2011-04-01
You need to install compizconfig-settings-manager, not simple-ccsm, there is not one available for compiz 0.9+

Been posted here a few times - 
> compiz (1:0.9.4-0ubuntu7) natty; urgency=low

  * debian/control:
    - [COLOR="Red"]breaks on old simple-ccsm until a new one for 0.9 is available[/COLOR]
  * debian/patches/029_default_options.patch: 
    - don't enable showing desktop while scale is triggered (LP: #736947)

 -- Didier Roche <didrocks@ubuntu.com>  Thu, 17 Mar 2011 17:13:32 +0100


---

### Post by ajarmoniuk on 2011-04-12
Actually, compiz is also disabled for me. After upgrading to natty, I was shown a dialog box saying my hardware does not allow me to run compiz (anymore?). 

And now I'm stuck with gnome 2 whether I choose Ubuntu or Ubuntu Classic. I can't have Unity at all, and I do have it turned on in compizconfig.

Edit: turns out I needed to go to gconf-editor and enable compositing in /apps/metacity/general

---

