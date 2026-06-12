---
title: "Can't log in to Unity or Ubuntu Classic"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by drfox on 2011-04-04
I enabled the Gnome3 repos wanting to try Gnome-Shell (which, BTW, works fine). But now I am unable to log into Ubuntu, Ubuntu Classic, nor Ubuntu 2D. With each attempt I get a message that says "Failed to load___" or something similar. I have compiz, ccsm with Unity plugins enabled, and a GeForce 7150M / nForce 630M] (rev a2) video card. I am running nVidia proprietary drivers. I do not have nouveau installed. This has been going on for several days even after undating/dist-upgrading (natty) several times. 
Any suggestions? TIA.
Larry

---

### Post by IWantFroyo on 2011-04-04
Go to the command line (I think f1), log in from there, and install your driver with sudo apt-get install 
xserver-xorg-video-nouveau.

---

### Post by drfox on 2011-04-04
> **IWantFroyo said:**
> sudo apt-get install 
xserver-xorg-video-nouveau.

Thanks, but the problem occurred before I removed nouveau. Anyway, I just reinstalled and same problem, "Failed to load Ubuntu, Unity 2D, etc"
Larry

---

### Post by Harry33 on 2011-04-05
> **drfox said:**
> Thanks, but the problem occurred before I removed nouveau. Anyway, I just reinstalled and same problem, "Failed to load Ubuntu, Unity 2D, etc"
Larry

Installing or uninstalling nouveau does not solve anything.
If nvidia-current is installed, it will always override and infact blacklist nouveau.
To get nouveau working you need to purge nvidia-current and remove the file /etc/X11/xorg.conf. Then reinstall nouveau.

But your problem is not due to graphics drivers.
You need to install ppa-purge and then purge the Gnome3 PPA.
Have you tried recovery mode for failsafe graphics?

---

### Post by drfox on 2011-04-05
> **Harry33 said:**
> Installing or uninstalling nouveau does not solve anything.
If nvidia-current is installed, it will always override and infact blacklist nouveau.
To get nouveau working you need to purge nvidia-current and remove the file /etc/X11/xorg.conf. Then reinstall nouveau.

But your problem is not due to graphics drivers.
You need to install ppa-purge and then purge the Gnome3 PPA.
Have you tried recovery mode for failsafe graphics?

Thank you. I don't think it's a video problem either. I tried sudo ppa-purge gnome3  and ppa-purge gnome3-team
ppa-purge couldn't find the ppa
I removed the gnome3 ppas from my repos, reloaded, rebooted in safe graphics. Still get the same error: Failed to load Ubuntu.
What else can I try?

---

### Post by lucazade on 2011-04-05
You can try debugging gnome-session

from a failsafe xterm session from GDM (login page) run

```
gnome-session --debug

```

to redirect output to a file
```
gnome-session --debug 2>&1 | tee gnome-session.log

```

and look for errors!

---

### Post by drfox on 2011-04-05
> **lucazade said:**
> You can try debugging gnome-session

from a failsafe xterm session from GDM (login page) run

```
gnome-session --debug

```

to redirect output to a file
```
gnome-session --debug 2>&1 | tee gnome-session.log

```

and look for errors!

Here't the output:
GNOME_KEYRING_CONTROL=/tmp/keyring-HOk6Pd
GNOME_KEYRING_CONTROL=/tmp/keyring-HOk6Pd
GPG_AGENT_INFO=/tmp/keyring-HOk6Pd/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-HOk6Pd
GPG_AGENT_INFO=/tmp/keyring-HOk6Pd/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-HOk6Pd
GPG_AGENT_INFO=/tmp/keyring-HOk6Pd/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-HOk6Pd/ssh
Starting Dropbox...Done!
** (nm-applet:3053): DEBUG: old state indicates that this was not a disconnect 0

It any of that helpful?

---

### Post by lucazade on 2011-04-05
> **drfox said:**
> Here't the output:
GNOME_KEYRING_CONTROL=/tmp/keyring-HOk6Pd
GNOME_KEYRING_CONTROL=/tmp/keyring-HOk6Pd
GPG_AGENT_INFO=/tmp/keyring-HOk6Pd/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-HOk6Pd
GPG_AGENT_INFO=/tmp/keyring-HOk6Pd/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-HOk6Pd
GPG_AGENT_INFO=/tmp/keyring-HOk6Pd/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-HOk6Pd/ssh
Starting Dropbox...Done!
** (nm-applet:3053): DEBUG: old state indicates that this was not a disconnect 0

It any of that helpful?

Only these few lines?! :confused:
It hangs like when using "classic session", correct?

.. strange...

---

### Post by drfox on 2011-04-05
> **lucazade said:**
> Only these few lines?! :confused:
It hangs like when using "classic session", correct?

.. strange...

I'm logging out of gnome-shell to run xterm, so I believe these errors are really occurring from the gnome-shell session. I can't log in to xterm from ubuntu-classic, ubuntu, or ubuntu-2d at all. 
Do you want me to try this from a reboot?

---

### Post by osarusan on 2011-04-05
I had this exact same problem after I enabled the Gnome Shell PPA. Get  rid of that PPA and enable the updated Unity PPA, and see if that helps. You may have to reinstall any of the gnome stuff that game from the Gnome Shell PPA.

---

### Post by lucazade on 2011-04-05
> **drfox said:**
> I'm logging out of gnome-shell to run xterm, so I believe these errors are really occurring from the gnome-shell session. I can't log in to xterm from ubuntu-classic, ubuntu, or ubuntu-2d at all. 
Do you want me to try this from a reboot?

Are you using "fail safe session" from GDM login page?

You should not use xterm from a normal running session.

Attached an old screenshot of gdm and failsafe

---

### Post by drfox on 2011-04-06
Thanks for the help, everyone. The key was using ppa-purge ppa:gnome3-team/gnome3
That then broke the install and I couldn't log in to any x session. I then added LXDE-desktop, logged in to that. I couldn't install ubuntu-desktop, but it wouldn't install because the installed version of gnome-session-??? (sorry, can't remember) was too high. I uninstalled that, reinstalled ubuntu-desktop with the lower version of gnome-session, and can now run unity.
But I am very unimpressed, and will be using classic rather than Unity or Gnome-Panel for the forseeable future.

---

