---
title: "gksu error with Rhythmbox"
date: 2009-02-25
forum: Multimedia Software
---

### Post by Lunx on 2009-02-25
Hi Folks,I'm pretty new to Linux and Ubuntu, so been trying to learn to run things from the command-line. I'm hoping someone can explain a warning message I got when trying to run Rhythmbox from the command-line.

```

pete@pete-ubuntudesktop:~$ gksu rhythmbox

(rhythmbox:21133): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
pete@pete-ubuntudesktop:~$ 
```

Rhythmbox did run after this came up, but it opened differently to usual (ie, I had none of my music show up, radio streams etc.) I closed it down and opened it from **Applications > Sound and Video > Rhythmbox** and all was fine with the world again. Curious to know why using gksu command opens a different version (version is not the correct terminology I guess, but very tired and brane ain't workin' properly)

So why did it happen, and how do I get it to open correctly from command-line

Thanks
Pete

---

### Post by yoyoned on 2009-02-26
Why are you using gksu to run rhythmbox

---

### Post by Revo___ on 2009-02-26
Normally there should be no need to run that music program as root.

You must know that by default gksu executes the program as user root.
Possibly root hasn't set up any Rythmbox-Keys then.

Does this error occur also, when you leave gksu out?

---

### Post by Therion on 2009-02-26
In short you don't need the "gksu".  

Just type in *rhythmbox* and you're good to go.

I imagine you got the funky version you did using gksu because the the "gk" is used to call up a graphical front-end to the "su", which is used to invoke root privileges.  

Neither of which are needed for this.

---

### Post by Lunx on 2009-02-27
> **Therion said:**
> In short you don't need the "gksu".  

Just type in *rhythmbox* and you're good to go.

I imagine you got the funky version you did using gksu because the the "gk" is used to call up a graphical front-end to the "su", which is used to invoke root privileges.  

Neither of which are needed for this.

Thanks for that (and thanks for everyones replies)

I realise I don't need to run it that way, just that I was playing around following a tutorial and figured I'd try it out as I didn't think it would be something that would do much damage. I'll run it in the normal fashion in future ;)

---

