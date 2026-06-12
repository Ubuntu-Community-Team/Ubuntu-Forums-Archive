---
title: "Mount remote SMB share for each user"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by rich86 on 2009-07-18
Hi,

Not sure if the title makes such sense but i will try to explain in more detail here.

I was wondering if it is possible to mount a specific smb share for each user at login? Currently we have an XP Pro comp with multiple users which my dad uses. We have an other comp that currently has XP Home on it and when you login to an account on that one it mounts a network drive for the data of that user. ie. i have a richards data dir shared on the XP pro machine and when i login on the Home pc it mounts z:\ as //[computer-name]/richards data. This is them the my documents directory. This is then repeated for each user. As the username and passwords are the same the share is automatically mounted with no prompts.

I was wondering what the correct procedure is for doing a similar thing in Ubuntu? 

If you need more details please ask, i probably didn't explain this that well.

Thanks,

Richard

---

### Post by capscrew on 2009-07-18
> **rich86 said:**
> Hi,

Not sure if the title makes such sense but i will try to explain in more detail here.

I was wondering if it is possible to mount a specific smb share for each user at login?

Sure there is.  The share is called [homes] in the /etc/samba/smb.conf file.  See [_[COLOR="DarkSlateGray"]here[/COLOR]_]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") for more information.

I have my homes shares on a separate partition but it this not necessary. This is what my [homes] share definition looks like```
[homes]
        comment = Home Directories
        path = /smb/home/%S
        browseable = no
        guest ok = no
        valid users = %S

```

---

### Post by swerdna on 2009-07-18
There is the option in Ubuntu to share out the home directories invisibly to the LAN. So if e.g. various family members had accounts on an Ubu machine, you could arrange for those home directories to be shared. And then user annie could connect to the directories at and under /home/annie, and so on for others. Than annie on an xp computer could arrange for her directories on the Ubu computer to mount to the Z: drive when she boots her xp computer up. Is that getting somewhere near what you want?

The shared [homes] directory is discussed here: [Setting up a Samba Server (Browsing and Sharing)]("http://ubuntu.swerdna.org/ubulanprimer.html#server"). Look for the segment titled "[homes] Users' Roaming Shares".

---

