---
title: "VLC that can not be removed, purged and terminal does not see it"
date: 2018-09-28
forum: Multimedia Software
---

### Post by dougcumiskey123 on 2018-09-28
I have an installation of VLC that is coursing multiple problems. It is crashing the computer, it can not be removed, purged, controlled or quit, to stop it I have to power off the computer.

Please can some one help me?

---

### Post by QIII on 2018-09-28
Hello!

It might be helpful to those who wish to help if you could post the exact command(s) you are using and the resulting messages.

Thanks.

---

### Post by ajgreeny on 2018-09-28
I trust you are not still using Ubuntu 12.04 as your user information shows?

If you are now using 18.04 perhaps you have installed the snap version of VLC.
Use command ```
snap list
``` to show what snap packages you have installed on your system.

---

### Post by dougcumiskey123 on 2018-09-29
Thank you for your reply's 

First let me say that even though I have been using ubuntu since ubuntu 8, I am very much a novice, and normally when I have a disaster like this I reformat the disc and start again but that option is not open to me at the moment as I am away from home and will be until December.

I have used many sites of information. IE 
[https://askubuntu.com/questions/497584/how-to-remove-a-third-party-software-that-is-installed-but-cannot-be-located](https://askubuntu.com/questions/497584/how-to-remove-a-third-party-software-that-is-installed-but-cannot-be-located)
[https://ubuntuforums.org/showthread.php?t=1674247](https://ubuntuforums.org/showthread.php?t=1674247)
[https://askubuntu.com/questions/716764/completely-remove-and-reinstall-vlc-on-my-system](https://askubuntu.com/questions/716764/completely-remove-and-reinstall-vlc-on-my-system)

And probably made the problem worse. at one stage I had 2 copies of VLC at the same time but removing the second one was not a problem.

Sorry I cant be more helpful

The symptoms are on boot up the computer some time's crashes up to 4 times with a error report that there is a "fault with the graphic card", but when it is running no graphic problems are present.  Neither the terminal or ubuntu software recognize the presence of this VLC

The VLC is still working but it looks nothing like a normal version, no top tool bar, the text is very small and not normal, sometimes I have to de-power to get out of the program.

When not booting or running VLC every thing else is working fine.

Regards Doug

---

### Post by dougcumiskey123 on 2018-09-29
snap list
Name  Version  Rev   Tracking  Publisher   Notes
core  16-2.35  5328  stable    canonical&#10003;  core
vlc   3.0.4    555   stable    videolan&#10003;   -
doug@doug-ThinkPad-T410:~$

---

### Post by mc4man on 2018-09-29
> **dougcumiskey123 said:**
> snap list
Name  Version  Rev   Tracking  Publisher   Notes
core  16-2.35  5328  stable    canonical&#10003;  core
vlc   3.0.4    555   stable    videolan&#10003;   -
doug@doug-ThinkPad-T410:~$
Run,
```
sudo snap remove vlc
```

```
sudo apt update && sudo apt install vlc
```
See if that vlc works any better

---

### Post by dougcumiskey123 on 2018-09-30
Thank you mc4man, That fixed it and every thing is working perfectly now, I owe you one. I have marked the tread as SOLVED. Once again THANK YOU, Doug.

---

