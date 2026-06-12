---
title: "Rhythymbox hijacked my network drive file associations"
date: 2017-06-13
forum: Multimedia Software
---

### Post by EarlsFurniture on 2017-06-13
First, here's my setup:

Host: Mac Mini late 2014 running El Capitan
Guest: Xubuntu 16.04 with ubuntu-desktop added and currently active running in VMWare Fusion 8.5

Here's what I did:
I migrated my music collection temporarily from my Mac Laptop to my MacMini pending the building of a media server. I then added the Music folder from my Mac to Rhythymbox for playing. (I don't want to use iTunes right now till I get my media server set up)

Here's what went wrong:
After adding this folder to Rhythymbox, now, any time I attempt to open a network location on the host from Nautilus, it tries to use Rhythymbox to open it. I can use "open with" but I can't seem to permanently change this back to Nautilus.

I'm presuming this is a bug since apps shouldn't steal file associations without explicit permission. But until that is resolved, any idea on how to manually change it back?

I tried editing ```
~/.local/share/applications/mimeapps.list
``` with the following lines:

```
inode/directory=nautilus.desktop
x-directory/normal=nautilus.desktop
```

but no dice.

---

### Post by &amp;KyT$0P# on 2017-06-14
> **EarlsFurniture said:**
> Xubuntu 16.04 ...

I tried editing ```
~/.local/share/applications/mimeapps.list
``` 
Try editing
```
~/.config/mimeapps.list
```

---

### Post by EarlsFurniture on 2017-06-14
> **halogen2 said:**
> Try editing
```
~/.config/mimeapps.list
```

Thanks, but still no change.

Neither of those files shows anything assigned to rhythymbox.desktop that looks like it needs to be changed, and adding the aforementioned two lines assigned to nautilus.desktop seems to have no effect.

Perhaps network shares are a different type? Maybe they are specified elsewhere?

To be clear, what I'm trying to open here follows this path:

Network -> File Sharing on Mac (looks like a server rack icon)

Oddly, there are always two such icons even though there is only one machine to connect to. The first one never works. There is also a 'Microsoft Network' icon presumably because I also share the Mac's folders via samba. (I'd rather not use that method, and it also defaults to Rhythymbox)

---

