---
title: "Nvidia driver problem"
date: 2009-05-29
forum: Multimedia Software
---

### Post by hobobanana on 2009-05-29
I was running 8.10 and everything was fine. I then upgraded to 9.04 and my video drivers no longer work. I have an Nvidia GeForce 4 MX series card. I tried to install the latest drivers from Nvidia, but when I try to install them it says that it can't open the package. The drivers are downloaded to my desktop. Is there some other place that I should put them before trying to install them or something I need to else I need to add to the install command?

---

### Post by whoop on 2009-05-29
Did you try System-->Administration-->Hardware drivers?

---

### Post by MedellinManDem on 2009-05-29
> **whoop said:**
> Did you try System-->Administration-->Hardware drivers?

This doesn't work for me. It says downloading and installing, but nothing happens.

---

### Post by Arup on 2009-05-30
Give it time, if you see network activity, that means its downloading, then it installs, you will see that by hdd activity. Sometimes the interface would crash, don't bother, just turn it up again after sometime and it will tell you restart required, that means drivers have been installed.

---

### Post by MedellinManDem on 2009-05-30
> **Arup said:**
> Give it time, if you see network activity, that means its downloading, then it installs, you will see that by hdd activity. Sometimes the interface would crash, don't bother, just turn it up again after sometime and it will tell you restart required, that means drivers have been installed.

I can assure you this wasn't it.

My Ubuntu is in tatters on both of my PCs now, and all I did was upgrade.

Not great and I'm currently using Vista.

I'm not happy, as I believed Ubuntu was a real alternative, but it seems not.

---

### Post by whoop on 2009-05-30
> **MedellinManDem said:**
> I can assure you this wasn't it.

My Ubuntu is in tatters on both of my PCs now, and all I did was upgrade.

Not great and I'm currently using Vista.

I'm not happy, as I believed Ubuntu was a real alternative, but it seems not.

Common, this problem should be fixable :D You can also try installing envyng-qt. It is a tool that downloads and installs ati or nvidia drivers for you. Give that a whirl and tell us what comes up.

---

### Post by MedellinManDem on 2009-05-30
> **whoop said:**
> Common, this problem should be fixable :D You can also try installing envyng-qt. It is a tool that downloads and installs ati or nvidia drivers for you. Give that a whirl and tell us what comes up.

Installed, but when I try and run it from the command prompt (because I can't get to the desktop or any display) it just says:

```
kdesudo: cannot connect to X server
```

I ran

```
sudo /etc/init.d/gdm/ start
```

and it said "Starting GNOME DISPLAY MANAGER"

But still said "cannot connect to X server" when I ran envy again.

---

### Post by whoop on 2009-05-30
> **MedellinManDem said:**
> Installed, but when I try and run it from the command prompt (because I can't get to the desktop or any display) it just says:

```
kdesudo: cannot connect to X server
```

I ran

```
sudo /etc/init.d/gdm/ start
```

and it said "Starting GNOME DISPLAY MANAGER"

But still said "cannot connect to X server" when I ran envy again.

I haven't used envy for ages, but I'm sure there was a cli installer, it would be stupid if there wasn't.... It was "sudo envyng -t" or something... Try "man envyng" if I was wrong.

---

