---
title: "Headless server fails to load GUI without attached monitor"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by zgerrz on 2010-07-25
Hi,

I am running a server that is mostly headless, but does run the Gnome environment (I have ubuntu-desktop installed). I usually administer it via VNC over SSH.

My problem is that when I reboot the system over SSH, the system fails to fully load the GUI, which prevents me from connecting via VNC (although SSH still works). When I connected a monitor and rebooted, the system booted up fine. It appears that the GUI will not load without an attached monitor, which never happened before in previous Ubuntu versions.

I know some out there will yell at me for not learning the CLI, but I do use many commands but prefer a GUI for certain tasks and visualization of my work since my system has the resources to spare.

I would appreciate any assistance. Thanks.

EDIT: running Lucid Lynx

---

### Post by zgerrz on 2010-07-27
bump

---

### Post by P4man on 2010-07-27
You can use a GUI over ssh but that doesnt mean you need to run gnome or vnc on the headless server.

From your desktop ssh in to the headless server and start gnome:
```
ssh -X user@yourserver gnome-panel
```

or just launch a specific gui app:
```
ssh -X user@yourserver "gedit /some/file"
```

That should be faster than VNC and accomplish the same without requiring a monitor or gnome running remotely.

If you really must have gnome on the server and forward it with vnc, then the only solution i know off is a VGA dummy:
[http://www.soerennielsen.dk/mod/VGAdummy/index_en.php](http://www.soerennielsen.dk/mod/VGAdummy/index_en.php)

---

### Post by zgerrz on 2010-07-27
Thank you for the response.

I have tried in the past to use SSH to run GUI programs, but I often get the error unable to open display. I'm not sure what I need to change to be able to open GUI programs.

I'm surprised that I'm only having this issue with Lynx regarding the pc not booting up without an attached monitor. I would think there would be a more elegant solution that using a dummy VGA connector. Maybe some sort of xorg.conf option. That's just me.

---

### Post by P4man on 2010-07-27
you need to enable x forwarding to run gui programs. -X (uppercase!) switch in the ssh client and it has to be enabled on the server (on by default afaik).

As for being the only one; you arent; but usually  headless servers dont have the gui running. there is no point really. Let it boot without gnome and you can still ssh and start gnome on your client with the command above if you want a gui remotely. Locally you would pretty much never want a gui since you have no monitor.

---

### Post by i.r.id10t on 2010-07-27
IN your gdm config tell it to not start a local X server ...

---

### Post by zgerrz on 2010-07-28
Well I've figured out how to use X11 forwarding to suit my needs.

One last question. How do I set the server to boot without starting gnome or the X server? Do I need the X server to be running on the server to use X11 forwarding?

Thanks

---

