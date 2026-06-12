---
title: "Nautilus can't connect to win7 share"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by eddified on 2010-01-17
My Ubuntu Desktop (9.10, 64-bit) VM can't connect to my Windows 7 (64-bit, Ultimate) File Share using Nautilus. I enter "smb://<comuterName>" in the address bar and then it comes up with a password dialog (see screenshot) and then after entering the correct login info, the dialog disappears for a second or two but then reappears again. The dialog always comes back up and the share is never mounted.

[LIST]
[*]Connecting from an XP box on the network to the windows 7 share works just fine.
[*]Connecting from the Ubuntu machine to the windows 7 share using the appropriate 'smbmount' command works just fine.
[*]Connecting from the Ubuntu machine (using the nautilus GUI) to the XP box (password protected) works just fine.
[*]Then I turned off password protection in Win7, rebooted the win7 machine, and still all of the above tests turned out the same. And the Ubuntu machine still doesn't connect to the windows share using the nautilus GUI, and still displays the password dialog even though no password is required anymore.
[*]I tried using smbclient to view the shares, here is the output (not sure if I should be trying something else using the smbclient program):
[LIST]
[*]eddie@eddie-ubuntu:~$ smbclient -L eddie-win7
Enter eddie's password: 
session setup failed: SUCCESS - 0
[/LIST]
 
[/LIST]

I'd like to know how to connect Ubuntu to the windows 7 share using the nautilus GUI. If it's a bug, I'd like to file it (I think it is). But first I would like some direction trouble-shooting to make sure it is in fact a bug. (I think I read elsewhere on this forum that someone connected Karmic to win7 share, so maybe it's not a reproducible bug. But then again, maybe they weren't using 64-bit Karmic...)

---

### Post by eddified on 2010-01-17
[attach]143985[/attach]

---

### Post by eddified on 2010-01-17
I've tried both "forget password immediately" and "remember password utill you logout".

I've also tried the Nautilus menu "File -> Connect to Server..." method and that didn't work either.

---

