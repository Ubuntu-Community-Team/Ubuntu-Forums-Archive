---
title: "Nova T 500 Remote"
date: 2007-10-13
forum: Mythbuntu
---

### Post by Lem on 2007-10-13
I see in the latest build there is an option for the Nova T 500 remote. However, when I try to change to it, the process hangs at the 'Configuring Remote' stage.

Is this a bug, or have I done something daft? Can I invoke this from the command line to see what's going wrong?

---

### Post by superm1 on 2007-10-13
By latest build are you meaning the latest LIRC updates?

---

### Post by superm1 on 2007-10-13
and line You can invoke via command line like this to get a backtrace:

sudo ```
/usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre
```

---

### Post by superm1 on 2007-10-13
Actually, I was able to reproduce this.  It was a bug in the last LIRC upload.  The 'main' archive is frozen now, so I added a workaround to mythbuntu-control-centre that will allow this to work correctly.

You'll see it in m-c-c 0.10-0ubuntu1.  Thanks for catching this so quick :)

[https://launchpad.net/bugs/152353](https://launchpad.net/bugs/152353)

---

### Post by Lem on 2007-10-13
Nice one Mario. My wife will no doubt be slighlty bemused to not have to control the tv with a keyboard any more!

---

### Post by Lem on 2007-10-15
Works well now - Only problem I had was that lirc generator assumes mythtv as the user, so I had to copy my lircrc across.

Use Edit Keys to add the TV, Video buttons etc. I added to my lircrc file to get the Radio button to link to Mythstream.

---

### Post by superm1 on 2007-10-15
Shouldn't assume mythtv as the user.  It should generate them for the username you're logged in as.

Can you double check that?

---

### Post by Lem on 2007-10-15
Do note however if you plan to do this that you need to compile your own v4l-dvb modules and use the newer firmware. Your remote won't work otherwise.

Follow the guide here; [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI) 
Ignore the remote control section. It's easier to use mythtv control center to set-up your remote and then tweak your lircrc file for added functions if required.

After kernel upgrades, you will need to re-install your made modules;

```
cd /home/v4l-dvb
sudo make install
sudo make load
```

There is also a new firmware out that seems to help prevent your cards disconnecting;

```
wget http://www.wi-bw.tfh-wildau.de/~pboettch/home/linux-dvb-firmware/dvb-usb-dib0700-1.10.fw
sudo mv dvb-usb-dib0700-1.10.fw /lib/firmware/dvb-usb-dib0700-03-pre1.fw
```

---

### Post by Lem on 2007-10-15
> **superm1 said:**
> Shouldn't assume mythtv as the user.  It should generate them for the username you're logged in as.

Can you double check that?

I think you are right. The lircrc file I had in mythtv was one I had made myself earlier and had more buttons enabled.
I can post up my tweaked lircrc if you think it would be useful? I changed the behaviour of some buttons - eg. back/exit now = Esc and have added alt+key combos to the TV, Radio etc buttons so that they can be mapped to functions in Edit Keys.

---

### Post by superm1 on 2007-10-15
> **Lem said:**
> I think you are right. The lircrc file I had in mythtv was one I had made myself earlier and had more buttons enabled.
I can post up my tweaked lircrc if you think it would be useful? I changed the behaviour of some buttons - eg. back/exit now = Esc and have added alt+key combos to the TV, Radio etc buttons so that they can be mapped to functions in Edit Keys.
Yes, it's too late to be included for Ubuntu Gutsy, but can be targeted for Hardy.

Please file a bug against mythbuntu-lirc-generator, and attach your ~/.mythtv/lircrc and ~/.lircrc

Most appreciated!

---

### Post by Lem on 2007-10-16
Will do. I'll also replace this thread with a step-by-step HOWTO for Nova T 500 and Mytbuntu.

---

