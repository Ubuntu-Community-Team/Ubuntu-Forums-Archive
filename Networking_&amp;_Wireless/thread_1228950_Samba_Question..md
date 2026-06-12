---
title: "Samba Question."
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-08-01
I have a Samba desktop with several shares on it. I'm questioning the differences to which Ubuntu connects to Samba + Windows connects to Samba.

If I use Windows to connect to the Samba server - I go to start - run - \\SambaServerNameHere and it asks me for a password. I type it in. Based on that login information, it'll allow/deny me access to certain shares depending on the access settings on the Samba server.

If I use Ubuntu to connect to the Samba server - I go to Places - Network - Select the Samba Server - Double click share - type in my information - BAM. I have access. Okay, great. But maybe I didn't mean to click on the storage share (which I just logged into) and I wanted to get into public. So I go back one, double click public - oh wait. I have to log in again?

On Windows when you connect it seems to remember your ID to that server so I can bounce to each share that I have access to accordingly.

On Ubuntu when you connect it seems to have to ask "Wait, who are you?" each time you click on a new share.

Why is this?

EDIT - Wow. I'm an idiot. You know that neat little feature that comes up asking you if you want to forget the password immediately, remember till you log out, or remember permanently? Yeah. I should have known. That was my issue.

Duuuuuuuur!!

Another Edit - here's one question I do have that I didn't have an answer for - When I connect to the Samba server on my Windows computer, I see all of the shares. When I connect to the Samba server on the Ubuntu computer, I see all shares but one - I checked my Samba configuration manager and they're all set up fine and that other share that's missing on Ubuntu is checked as visible. What gives?

EDIT again - I noticed the share that wasn't showing up was the only one with an underscore in the name. I did some testing. The actual path still has an underscore, but the display name for that folder... if it has an underscore or a dash, Ubuntu doesn't read it. Windows does, but Ubuntu does not. So I have the path still with an underscore in it, but instead of Spare_Storage (path) you see SpareStorage (display name) and it works fine.

It seems as if it's just Ubuntu Karmic Alpha 3 that doesn't detect it. Ubuntu Hardy finds it just fine with the dash and underscore.

---

