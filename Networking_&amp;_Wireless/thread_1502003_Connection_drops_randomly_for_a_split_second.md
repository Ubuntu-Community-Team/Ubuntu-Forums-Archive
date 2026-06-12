---
title: "Connection drops randomly for a split second"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by peterataylor on 2010-06-05
Hi all.
I could not find a solution to this problem anywhere. I use a ubuntu server to play (stream) mp3s and movies to other computers on my network.  It works most of the time, but sometimes in the middle of a movie or a song it will drop/hiccup--saying it is "not reachable".  

I am not overtasking the server at all, and merely playing an mp3 that takes up less than 10% of the bandwidth, yet it drops it for a split second.

I have a WRT160N router (DD-WRT of course) with 4 clients connected (2 of which are wired).  The ubuntu server is connected via ethernet and all machines have the same issue.  It can't be the router because another Windows machine works just fine for streaming these files.

I just can't understand how it can lose connection for a second or so.  It may just be the file-system or some service that is hiccuping, but I have no idea...

Please help, thank you!
-Peter

---

### Post by peterataylor on 2010-06-05
I believe I have found a fix.  In the /var/log/samba/log.desktop there were lines like this every time it hiccup'd:

> process_usershare_file: stat of /var/lib/samba/usershares/incoming failed. Permission denied
So I looked up what "stat" meant, and found that this might actually be some wacky permission issue.  Mind you, I made all of my shares through the GUI.  So I erased the directory /var/lib/samba/usershares (I probably could have just set the permissions to 777 but was lazy) and instead made the shares old-school in /etc/samba/smb.conf and so far it's been about a half hour and there has not been a glitch.  I won't mark it as solved yet, but there seems to be hope that it was a permissions error and not hardware or Samba at fault.

Any information on this would be helpful :)
:guitar:

---

