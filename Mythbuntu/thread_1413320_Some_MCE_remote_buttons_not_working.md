---
title: "Some MCE remote buttons not working"
date: 2010-02-22
forum: Mythbuntu
---

### Post by podge3 on 2010-02-22
I'm completely new to Ubuntu so please be kind. I'm quite familiar with Windoze and even did a little C programming while in College but all thats forgotten now :)
 
I've just installed Mythbuntu 9.10 on my HTPC. Installation was a breeze - faster and easier than Win7.
 
However I am finding that even the smallest alteration or task seems to take hours due to my lack of experience and I'm quite close to giving up and going back to Windoze. Please save me!!
 
So anyhoo, my immediate problem is that I cannot get the MCE remote power or start button to work in MythTV. All the other keys work and power & start also give an reading on Irw. I would like the Start button to start MythTV from the desktop and the power button to power down the PC from MythTV.
 
All help greatly appreciated.

---

### Post by superm1 on 2010-02-23
If you'd like the power or start button to work, you'll need to write a small irexec script that does it.  It needs to go in ~/.lirc/irexec.

If such a script exists, irexec starts upon login and binds the commands.

Here's a sample for irexec:
[http://tvtime.sourceforge.net/example.lircrc](http://tvtime.sourceforge.net/example.lircrc)

You just need one clause that binds it to the button you want.

You can view the possible buttons in /etc/lirc/lircd.conf (or any files it references internally).

---

### Post by podge3 on 2010-02-24
Looks like I have more reading to do!
 
Thanks for the help - think I'll stick with this Ubuntu for a while. Its getting interesting :)

---

### Post by SiHa on 2010-02-24
> **superm1 said:**
> ...

If such a script exists, irexec starts upon login and binds the commands.

...

Just one minor caveat to add to this:

Although the LIRC startup script (/etc/rc*n*.d/S19lirc) seems to look for ~/.lirc/irexec, it starts the irexec daemon like this ```
irexec --daemon /etc/lirc/lircrc
```
i.e., it's looking in /etc/lirc/lircrc for the irexec config, rather than in ~/.lirc/irexec.

On my Mythbuntu (9.10, i386, fresh install), there was no /etc/lirc/lircrc, so I had to create one with the following line:```
include /home/frontend/.lirc/irexec
```...where frontend is the name of the mythtv user.

I haven't had a chance to fully replicate this yet, if I can be sure I did nothing stoopid to remove my lircrc, I'll file a bug.

---

### Post by Neon Dusk on 2010-03-05
On a standard Mythbuntu install /etc/lirc/lircrc does not exist.

'irexec -d' is started from /usr/share/mythbuntu/session.sh which I think is called from /usr/share/xsessions/default.desktop

---

