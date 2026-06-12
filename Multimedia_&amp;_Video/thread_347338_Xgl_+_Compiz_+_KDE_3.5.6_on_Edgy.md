---
title: "Xgl + Compiz + KDE 3.5.6 on Edgy"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by tintix on 2007-01-27
Have seen the Xgl + Compiz on Mandriva 2007 - looks fantastic! :D  Wann smth like this on my Kubuntu Edgy too! But how to install everything that it works so fine like on Mandriva 2007??? :confused: 
Recently I've upgradet from KDE 3.5.5 to KDE 3.5.6 un Edgy. The guys from kde.org say that the KDE 3.5.6 has better support for Compiz. So I had an idea to install Compiz instead that lagging beryl (have an FX5200)...
Did these steps like the guys from [go-compiz.org]("http://go-compiz.org/index.php?title=Ubuntu_Installation_Guide") said:
1. installed Xgl (gl-xserver);
2. sudo apt-get install compiz compiz-plugins compiz-extra compiz-extra-plugins compiz-kde
3. ran on console compiz-tray-icon, BUT there's no compiz-tray-icon!:confused: Seems not to be installed...
4. OK, have downloaded and sudo dpkg -i compiz-settings_0.07-2_i386.deb
5. Logged in Xgl session and entered on console compiz --replace and... whoops - where are my title bars gone??? :confused:
Anything seems to be working... SO WHRE CAN I FIND A COMPIZ HOW-TO FOR MY KDE 3.5.6 ON EDGY?????????????!!!

---

### Post by usergentoo on 2007-01-27
I just upgraded to 3.5.6 and yesterday Beryl and Xgl was working great but now xgl dosent seem to be working, and the only updates that was installed was the updates for kde.

---

### Post by mrmcd on 2007-02-02
tintix,
your title bars might have disappeared because "compiz-kde" was never actually installed.  try typing
```

sudo apt-get install compiz-kde

```
and see what it says afterwards.
the problem might be that gandalfn's repository does not have a version of compiz-kde (or other parts) compiled for your machine.  (for instance, there are things missing for my amd64 version of kubuntu edgy)

---

### Post by AJL on 2007-02-09
I see the same behavior.  I installed all the packages for KDE

sudo apt-get install compiz compiz-plugins compiz-extra compiz-extra-plugins compiz-kde

i even did one at a time to be sure they actually installed, now when I try to run compiz-tray-icon it says it doesn't know what that is  **compiz-tray-icon: command not found**

Any help would be great

---

### Post by markr on 2007-02-20
I have exactly the same problem.  compiz-kde installed (and the other compiz stuff except gnome related stuff), NVidia drivers updated and configured.

I can issue the command compiz --replace, but I loose my title bars, no cube or anything.

Anybody resolved this issue?

Mark.

---

### Post by tintix on 2007-02-24
So does anybody care for **KUBUNTU** users in this forum?????!!!!!!!
The Gnome users got their fun... :( 

I'm testing now the Fiesty Herd 4. Have tried both Beryl and Compiz.
The Beryl is lagging (on nvidia drivers, any XGL/AIGLX), and I the Kicker isn't working.

Have tried Compiz. Did install **desktop-effects** and then **kompiz-kde**. Have tried on console this:
         ** kde-window-decorator -replace**
Got this out:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
:confused: 

Then tried just **compiz --replace**. Result: launched compiz, but Kicker isn't working again!! :( 
So what should I do??????? Switch to Gnome????? :confused:

---

