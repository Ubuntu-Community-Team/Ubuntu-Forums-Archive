---
title: "SMPlayer 0.6.5 released"
date: 2008-11-14
forum: Multimedia Software
---

### Post by rvm4000 on 2008-11-14
[SMPlayer](http://smplayer.berlios.de) 0.6.5 has been released.

Most important changes:
> 
 * The subtitles when using the SSA/*** library can now be further customized. It's possible to select the font, size, colors, bold, italic, outline, shadow...
 * Now smplayer tries to follow the XDG Base Directory Specification for the config files. That means the now the configuration files will be saved under the directory $XDG_CONFIG_HOME/smplayer (or $HOME/.config/smplayer if $XDG_CONFIG_HOME is not defined). **If you want to keep your preferences, copy or move the files from $HOME/.smplayer to the new location.**
 * Added some options in Preferences->Interface to configure the floating control.
 * The commandline option -ini-path has been removed and replaced with -config-path, which specifies the directory where smplayer will store its data (not only smplayer.ini).
 * Added the possibility to select the adaptor for xv. Requires at least MPlayer SVN r26762.


You can download deb packages for Ubuntu Hardy, [**here**](http://smplayer.berlios.de/downloads.php).

Repositories for apt:
hardy: 
```
deb [http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) hardy main
```

intrepid: 
```
deb [http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) intrepid main
```

Note: these repositories contains updated versions of mplayer too.

---

### Post by lovinglinux on 2008-11-14
Thanks for the update and the PPA links.

The new SSA support is working like a charm.

There is an issue with the "Pause when minimized" option on Intrepid. It always pause, even when I disable this option. Then hitting pause again don't toggle the state. I have to go forward or backward a little bit to make it play again.

---

### Post by rvm4000 on 2008-11-15
> **lovinglinux said:**
> There is an issue with the "Pause when minimized" option on Intrepid. It always pause, even when I disable this option. Then hitting pause again don't toggle the state. I have to go forward or backward a little bit to make it play again.

I can't reproduce this problem. Did it happen too with 0.6.4?

Actually I'm thinking that this problem might be unrelated to the "Pause when minimized" option. What does the mplayer log say?

---

### Post by lovinglinux on 2008-11-15
> **rvm4000 said:**
> I can't reproduce this problem. Did it happen too with 0.6.4?

No.

> **rvm4000 said:**
> Actually I'm thinking that this problem might be unrelated to the "Pause when minimized" option. What does the mplayer log say?

I'm not next to the machine right now. I will post the log later.

---

### Post by rvm4000 on 2008-11-15
I think I didn't change anything related to the "Pause when minimized" option in the code from 0.6.4 to 0.6.5.

Did you update mplayer too? or changed something in the config, like the video output driver?

---

### Post by lovinglinux on 2008-11-15
> **rvm4000 said:**
> I think I didn't change anything related to the "Pause when minimized" option in the code from 0.6.4 to 0.6.5.

Did you update mplayer too? or changed something in the config, like the video output driver?

Yes, I updated mplayer. It also happens with a default config file.

---

### Post by lovinglinux on 2008-11-16
The "Disbale Screensaver" option is not working either.

---

### Post by rvm4000 on 2008-11-16
When you enable the option to stop the screensaver, smplayer just passes to mplayer the option &#8722;stop&#8722;xscreensaver, so the screensaver is actually disabled by mplayer.

Recently the mplayer developers have changed the way the screensaver is disabled, but it seems now some systems fail to stop the screensaver.

For that, they added a new option:
> **&#8722;heartbeat&#8722;cmd**
	
Command that is executed every 30 seconds during playback via system() - i.e. using the shell.

NOTE: MPlayer uses this command without any checking, it is your responsibility to ensure it does not cause security problems (e.g. make sure to use full paths if "." is in your path like on Windows).

This can be "misused" to disable screensavers that do not support the proper X API for this. If you think this is too complicated ask the author of the screensaver program to support the proper X APIs for this.

EXAMPLE for xscreensaver: mplayer &#8722;heartbeat&#8722;cmd "xscreensaver&#8722;command &#8722;deactivate" file

EXAMPLE for gnome screensaver: mplayer &#8722;heartbeat&#8722;cmd "gnome&#8722;screensaver&#8722;command &#8722;p" file

Maybe the easiest way to fix the problem is adding this line to your ~/.mplayer/config:

```
heartbeat-cmd="gnome-screensaver-command -p &"
```

---

### Post by lovinglinux on 2008-11-16
> **rvm4000 said:**
> When you enable the option to stop the screensaver, smplayer just passes to mplayer the option &#8722;stop&#8722;xscreensaver, so the screensaver is actually disabled by mplayer.

Recently the mplayer developers have changed the way the screensaver is disabled, but it seems now some systems fail to stop the screensaver.

For that, they added a new option:


Maybe the easiest way to fix the problem is adding this line to your ~/.mplayer/config:

```
heartbeat-cmd="gnome-screensaver-command -p &"
```

I guess disabling the screensaver in the system is a better alternative.

---

### Post by rvm4000 on 2008-12-19
Version 0.6.6 is expected to be released soon.

You can start to test the new features, there are available packages for hardy and intrepid (svn r2546):
[https://launchpad.net/~rvm4000/+archive](https://launchpad.net/~rvm4000/+archive) (notice that this repository is for experimental packages)

Changes since v. 0.6.5:
[http://smplayer.berlios.de/forums/viewtopic.php?id=877](http://smplayer.berlios.de/forums/viewtopic.php?id=877)

---

### Post by binbash on 2008-12-19
Thanks for the svn builds

---

