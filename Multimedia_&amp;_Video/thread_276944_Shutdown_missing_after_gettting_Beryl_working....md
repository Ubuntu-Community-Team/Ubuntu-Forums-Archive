---
title: "Shutdown missing after gettting Beryl working..."
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by gumbald on 2006-10-13
Just got Beryl working, although rather quirkily by chance, that's another story. However, shutdown and reboot are now missing from the choices in the menu. I have to log out, then shutdown from the login screen.

Anybody got a clue why? Searches for such a problem have resulted in zero hits.

---

### Post by krazed nun on 2006-10-13
i had the same problem. this didn't bring back the shutdown and reboot back, but it helped.

I went to 'alacarte menu editor' and cliked on 'new entry' then, for the name, i put 'shutdown' and for the command i put 
```

sudo shutdown -h now
``` 

after that, u clik ok and an entry in ur main menu will be there named 'shutdown'. when u clik it, the terminal will open and ask you for ur password. after that, it will go to a login screen, but it will shutdown a few seconds after. you can also make a shorcut to it in one of ur panels. and that is how i managed to get the shutdown icon back (not in the quit thing though) 

for reboot, change the name and for command put 'sudo reboot'.
hope i helped.

---

### Post by junglepeanut on 2006-10-14
known bug

---

### Post by gumbald on 2006-10-14
> **junglepeanut said:**
> known bug

For everyone or just some setups? I've shifted from a working XGL/Compiz setup, and to my amazement it worked first time, but has since puzzled me with its behaviour. The first few times I logged in/out with Beryl present the options were available. But have since disappeared...

Sometimes Beryl doesn't work first time and I have to kickstart it, I accepted that as being part of an alpha version, but the shutdown randomly vanishing did not fit this?

---

### Post by junglepeanut on 2006-10-16
I think it has something to do with mixing libraries but I have no clue honestly just read it on the old compiz forums like 6 months ago, and I believe this is one of those things that will get fixed once it has left a lot of the gnome libs. Or they get working together better like when this happened with KDE and gnome on same system a while ago.

Sorry sometimes my mood makes answers extemely brief.

---

### Post by misha680 on 2006-10-16
I think it has to do with XGL running on display :1 (or :93 I think for non-ATI cards, but in any case it's not the main X server running on the machine because it is always running within an Xorg server). For security reasons, any X server not running on the console X server (:1) does not have a shutdown option (so random people working, say, remotely on your machine can't shut it down).

When making the menu entry I would use the gksu command, as I don't think sudo will grant rights graphically (or at least it never did before):

```
gksu halt
```

Hope that helps.

Misha

---

### Post by gumbald on 2006-10-16
It was there when I used Compiz, but not now when I run Beryl, are they on different displays? I'm using Nvidia.

---

### Post by misha680 on 2006-10-16
Hmm... it shouldn't change like that when you switch from compiz to beryl. Perhaps you should try the forums.beryl-project.org and be sure to mention that you had the shutdown option when running compiz but no longer have it in beryl. I know that I have never had it but I have an ATI card so I have to run Xgl on display :1. Maybe if you are able to run Xgl on display :0 with Nvidia it is possible not to have this problem.

Misha

---

### Post by gumbald on 2006-10-16
Is that simple? Should I just put up with it for now and wait for AIGLX in Edgy?

---

### Post by misha680 on 2006-10-16
Ok, let me make it a little clearer, there are two possibilities here:

1) Running XGL with Compiz or Beryl, you never had shutdown and reboot in the log off menu. If this is the case, then using AIGLX will fix it, other than that there isn't a fix other than making a shortcut that does gksu halt or gksu reboot (same as shutdown -h now or shutdown -r now).

2) You sometimes have these options, and sometimes don't. I don't know what would cause that, but I don't think it would be the same problem. What I would recommend to do is to go to the forums for Beryl, which are found at forums.beryl-project.org, and post this question on there except let everyone know that you did have these items with compiz and not don't have them with beryl so that they know that it is a different problem from (1).

Hope that helps.

Misha

---

### Post by gumbald on 2006-10-16
Tried a conversion to AiGLX earlier, failed. I'll try again when I'm not half asleep... When's Edgy due out with built in AiGLX?

---

### Post by misha680 on 2006-10-18
Just fyi with aiglx there is a bug where sometimes the shutdown/logout/whatever box does not appear, but it is actually there and you must click blindly on it or press escape to get out. You can fix this by editing ~/.gnomerc (the .gnomerc file in your home directory) and adding (or putting in if the file does not exist yet) the following line:

```
export GSM_NO_GRAB_SERVER=1
```

Misha

---

### Post by Cyr4x on 2006-12-04
> **misha680 said:**
> Just fyi with aiglx there is a bug where sometimes the shutdown/logout/whatever box does not appear, but it is actually there and you must click blindly on it or press escape to get out. You can fix this by editing ~/.gnomerc (the .gnomerc file in your home directory) and adding (or putting in if the file does not exist yet) the following line:

```
export GSM_NO_GRAB_SERVER=1
```

Misha

Can this work with xcompmgr? For me it doesn't.

---

### Post by Azakus on 2006-12-04
It is XGL. I had XGL and Beryl for a while and it did that. The better option is running Beryl in Edgy's native AIGLX, which allows for the shutdown and logoff options again.

---

