---
title: "rsync 20 times slower than Samba?"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by ragtag on 2011-12-12
I have a small NAS box (ReadyNasDUO, runs Debian) that I use for backing up. I used to have a slow 100M/bit switch, so never wondered about why backups were taking forever. Now I've switched to a gigabit switch, and am getting very slow speeds over rsync, while I'm getting ok speeds over Samba.

If I try to rsync one big file from the NAS to my machine, I get around 1.3Mb/s, while dragging it across in Nautilus gives me 25-30Mb/s. Is there a reason for the huge performance hit when using rsync? And is there anyway I can fix this?


p.s. Yes, I know, it's should be possible to get over twice the Samba speed I'm getting, but first I would like to figure out how to get rsync up to similar speeds as Samba. :)

---

### Post by SlugSlug on 2011-12-12
thats a pretty big difference, I would expect rsync to be slower due to the checks and logs it does, but not that much. Am also interested as to why.. hence my pointless post to subscribe :)

---

### Post by papibe on 2011-12-12
How are you using rsync?

Are you using it over ssh, or locally over mounted samba shares?

Regards.

---

### Post by ragtag on 2011-12-12
Just direcly, like:

rsync -av --progress root@readynas:/c/media/bigile .

---

### Post by papibe on 2011-12-13
Yes. It looks like you are using it over ssh.

In my 100Mb LAN, I can get get 11.5MB/s (close to the hardware limit of 12.5MB/s). While using nautilus over samba is around 8-9MB/s.

1.3MB/s looks like a very slow connection, almost like regular speeds of a wireless G connection.

Are both copies being used over a wired connection?

Did you follow [this]("http://www.readynas.com/?p=2032") procedure to enable rsync over ssh?

Just a few thoughts.
Regards.

---

### Post by ragtag on 2011-12-13
Both are over from the ReadyNas to the same machine over the same cable. Neither the machine nor the ReadyNas has a wireless card, so it's not accidentally going over wifi.

I didn't set up rsync the way it's described in your link. I just rooted the ReadyNas, and created local Debian users on it, so it functions pretty much like a Debian server. I have full root access to it over ssh. :)

First, I thought it was my network card driver for the Realtek 8111/8169b, so updated those, but the speed didn't change. Then I realized I was getting much better speeds with Nautilus, than with rsync. So figured, there was something else going on here.

The processor in the ReadyNas is quite weak, and rsync requires more CPU than Samba, but I wouldn't think it made that much of a difference.

---

