---
title: "Remove xfce desktop and boot directly to MythTV?"
date: 2008-08-17
forum: Mythbuntu
---

### Post by Flecko on 2008-08-17
I have an interesting question. Is it possible for me to remove xfce or disable it so that instead of my MythTV frontend/backend booting into xfce first and then starting MythTV to just have it go directly into MythTV?

It might sound crazy, but it'd help my bootup time on my somewhat slower MythTV box. 

Let me know if its possible.
Thanks!

---

### Post by funkydan2 on 2008-08-18
You could install a lighter window manager (e.g. Fluxbox) and set GDM up to default into fluxbox and then tell fluxbox to autostart mythtvfrontend when you boot in.

---

### Post by Loaded.len on 2008-08-18
it is absolutely possible, but beware of focus problems.

---

### Post by Flecko on 2008-08-18
So is it as easy as just removing xfce-desktop from synaptic? Or do I have to manually edit some startup files afterwards to indicate that I want to boot directly into Mythfrontend?

I guess I could always try it...because its not that hard to just re-get xfce-desktop.

If anyone has any more thoughts, let me know...but I'll try it tonight I suppose.
Thanks everyone!

---

### Post by klc5555 on 2008-08-18
> **Flecko said:**
> So is it as easy as just removing xfce-desktop from synaptic? Or do I have to manually edit some startup files afterwards to indicate that I want to boot directly into Mythfrontend?

I guess I could always try it...because its not that hard to just re-get xfce-desktop.

If anyone has any more thoughts, let me know...but I'll try it tonight I suppose.


Mythtv doesn't really need a window manager at all. You could invoke xinit directly from the CLI (with no xinitrc, of course)and use mythfrontend with its complete path as the option. See the man page for xinit.

This is actually the way I have one of my frontends load, with mythtv on top of Slackware 12.1, which is very CLI-oriented anyway. It would never occur to me to try something like this with Mythbuntu, which even under the best of circumstances, with all its graphical tools in place, seems (at least to me) to be something of a PITA to modify. I would be strongly disinclined even to try to set up a Mythbuntu box to be maintained without a window manager, say, from the CLI. There are just better options for this.

Cheers!

---

### Post by nickrout on 2008-08-18
mythtv DOES need a window manager if you are running any external programs, eg mplayer for mythvideo. Otherwise you get focus problems.

---

### Post by Tr1p on 2008-08-18
> **nickrout said:**
> mythtv DOES need a window manager if you are running any external programs, eg mplayer for mythvideo. Otherwise you get focus problems.

true, is like when u wanne use amsn whitout a windowmanager

---

### Post by Flecko on 2008-08-18
Oh right. I forgot about the focus issues...I read about that somewhere else. I use mplayer for watching my videos in myth...so hrm.

Maybe I will just try a 'lighter' weight desktop or something. My mythbox is just a smidge underpowered and I'm trying to trim down the startup process, thats all.

Thanks for the help guys.
I'll let everyone know if I make any discoveries.

---

### Post by nickrout on 2008-08-18
good choices are fluxbox, icewm, evilwm and lightest of all ratpoison.

---

