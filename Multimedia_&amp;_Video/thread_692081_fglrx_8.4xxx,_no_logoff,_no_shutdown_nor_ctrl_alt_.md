---
title: "fglrx 8.4xxx, no logoff, no shutdown nor ctrl alt backspace"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by karhulitos on 2008-02-09
I've been missing suspend for a great time now and decided to install ATI propietary driver as they advertised it suspends w/o problems in [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

All almost good, suspend and hibernate worked just like they used to do earlier.

First shutdown revealed that I cannot end session, i.e. I cannot restart X with ctrl + alt + backspace, I cannot logoff and I cannot shutdown properly (I need to press power button for 3 secs).
I have AlwaysRestartServer=true in /etc/gdm/gdm.conf. I kinda knew this wouldn't help as I even can't restart X.
When X should shut down all I see is the background image (not black screen) left displayed with no control to the system whatsoever. System fan starts to push hot air after a while so I guess someone's looping badly but I just cannot check that.

There seems to be many related posts but I just couldn't find the one to help me.

Please help me! Wife comes back on sunday and there is no way she's going to accept to press power button as PC used power off from menu.

System is Acer Aspire 5040 WLMi with ATI X200M chip. This is Ubuntu 7.10.

---

### Post by luisromangz on 2008-02-09
It happened to me and solved it a couple of weeks ago. Look for a running process named atieventsd, and try killing it before loggin out. If this works, prevent it from loading at boot using an init sequence editor.

---

### Post by karhulitos on 2008-02-09
Cheers man, that helped me.

I did
```
 sudo /usr/sbin/update-rc.d -f atieventsd remove
```
to get rid of it.
Now I have suspend and I can logoff/shutdown the PC. Nice.
[edit] and the ATI powerstates works also which I feared to lose after nuking that hanger

---

### Post by Lukasz Tarkowski on 2008-02-10
```
 sudo /usr/sbin/update-rc.d -f atieventsd remove
```

Did id for me 2 :)

---

### Post by MrClearPore on 2008-02-11
```
sudo /usr/sbin/update-rc.d -f atieventsd remove
```

Worked for me as well.  Thanks for the tip :)
However, what are the effects of removing this service?  So far, its removal hasn't affected my system, but is this service needed for other activities?

Also, if I wanted to get **atieventsd** back, what would be the command to get all the shortcuts back?

**UPDATE**: After a little googling, I found the command that restores the **atieventsd** shortcuts:
```
sudo update-rc.d atieventsd defaults <seqno>
``` where 'seqno' is the sequence number of the **atieventsd** service (on my machine it was 20):

[B]/etc/rc0.d/K20atieventsd
    /etc/rc1.d/K20atieventsd
    /etc/rc2.d/S20atieventsd
    /etc/rc3.d/S20atieventsd
    /etc/rc4.d/S20atieventsd
    /etc/rc5.d/S20atieventsd
    /etc/rc6.d/K20atieventsd[/B]

---

### Post by karhulitos on 2008-02-17
After latest kernel update I needed to do fglrx again and it seems that atieventsd has been fixed. I have it running now and I can logoff/shutdown/suspend/hibernate.

So no problem no more!

---

### Post by killerskippy on 2008-04-30
> **Lukasz Tarkowski said:**
> ```
 sudo /usr/sbin/update-rc.d -f atieventsd remove
```

Did id for me 2 :)

Worked a treat for me shutsdown perfectly now on 8.4xxx

---

### Post by cmittle on 2008-05-19
I just updated to 8.04 a couple of weeks ago and noticed that I can not do Ctrl-Alt-Del, nor try to logoff then shut down from the display manager.  The only way to shut my computer down was sudo shutdown -h now.  This fixed my problem thank you very much.  

I'm curious as was asked above, what other affects is this going to have.  Does anyone know??

Thanks,
Cory

---

