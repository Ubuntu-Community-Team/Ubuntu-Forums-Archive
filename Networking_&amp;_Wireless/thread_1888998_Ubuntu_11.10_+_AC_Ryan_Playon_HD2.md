---
title: "Ubuntu 11.10 + AC Ryan Playon HD2"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by grandani on 2011-11-30
Hey everyone,

I'm a relative newbie to Ubuntu, so please bear with me if I make any silly comments :).
I recently purchased an AC Ryan PlayOn HD2 media player. This media players is connected to a switch, to which my laptop (which is a dual boot, with both Ubuntu and Windows 7) is also hooked up. So, I decided I wanted to share files over the network so the AC Ryan could stream them over the network. I have this working via Windows, but have a minor problem with sharing from Ubuntu. Every time I try to access the files on the AC Ryan, I have to enter my admin password for my laptop, which is quite annoying when having to enter user name and password with a remote control. In the sharing options of the folder I want to share I ticked both the "Allow others to create and delete files in this folder"  and the "Guest access" options, but to no avail. The AC Ryan itself actually runs some custom form of Linux I think, the network sharing appears to use Samba...
Anyway, I hope you guys might be able to help me solve this trivial yet quite annoying problem :).

---

### Post by lakosshoots on 2011-12-28
Hi there.

First I suggest that you update the firmware of AC RYAN, which you can find here

[http://www.playonhd.com/en/?upn=support]("http://www.playonhd.com/en/?upn=support")

I own a AC RYAN HD 2 years now and every update gives something more every time.

I have had several problems with SAMBA every time I update Ubuntu.

Make sure that the samba packages are ok and the 2 sabma services are up and running. Go to the software center and and type system-config-samba package. If you dont have it, I suggest you donwload it.

Remember that for samba, workgroup is important, so make sure you work on the same workgroup in the AC RYAN and as do for the rest of the network. Through system-config-samba you ; ll be able to set it.

Check that the samba services are up
```

sudo ps -C smbd
sudo ps -C nmbd
```

If everything fails then you can always use ftp to transfer files with AC RYAN.

Good luck.

Lakosshots
[www.just-more-thoughts.blogspot.com](www.just-more-thoughts.blogspot.com)

---

### Post by Wysiwug on 2012-11-16
I know this is a long shot, but do you still have any firmware versions for the ac ryan playon!hd2.. As the site is down and rumour says they have gone bust!
The problem i have is i have upgraded my amplifier and cant use TrueHd or DTS HD sound until i upgrade the firmware.. If you can help it would be appreciated, thanks in advance. :-)

---

