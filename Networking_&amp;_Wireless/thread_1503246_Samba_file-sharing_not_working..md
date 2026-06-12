---
title: "Samba file-sharing not working."
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by absinthe on 2010-06-06
I am at a total loss. For all intents and purposes - sharing files over a lan without a password between this ubuntu 10.04 machine and my wifes laptop (windows 7) should be trouble free.
I've installed samba, and created an smb.conf file in /etc/samba
```
[global]
workgroup = WORKGROUP
server string = Samba Server
netbios name = oak
security = share
username map = /etc/samba/smbusers
name resolve order = lmhosts wins bcast hosts
wins support = no

[Audio]
comment = Public Share
path = /mnt/media/Audio
available = yes
browsable = yes
public = yes
writable = no

[Movies]
comment = Public Share
path = /mnt/media/Visual/Movies
available = yes
browsable = yes
public = yes
writable = no

[TV Shows]
comment = Public Share
path = /mnt/media/Visual/TV Shows
available = yes
browsable = yes
public = yes
writable = no

[Incoming]
comment = Public Share
path = /mnt/media/Incoming
available = yes
browsable = yes
public = yes
writable = no
```

Furthermore, my line in FSTAB
```
/dev/sdb1 /mnt/media ntfs-3g umask=000 0 0
```

I want to note that I was using Arch Linux and this exact setup worked flawlessly. Why on earth would it not work the same in Ubuntu? Is it not the same Samba??

Help!

Thanks

---

### Post by absinthe on 2010-06-06
I tried using the built-in gnome-sharing thing but it didn't work either. I'm starting to wonder if I need to mount my drive differently.

Maybe I'll start from scratch and see how it goes.

Anyone got any ideas?

---

### Post by chiliman on 2010-06-06
If the laptop is running a firewall it might be blocking the samba server.  you might have to check the configuration of it on the windows laptop if so.  


add to global 
  guest account = nobody

and add to your shares
   guest ok = yes

not sure if this matters but i have  "wins support = yes" in my smbf.conf so could try changing that too.  thats my 2 cents worth maybe someone else might have something else to try if that doesn't work.

---

### Post by absinthe on 2010-06-06
> **chiliman said:**
> If the laptop is running a firewall it might be blocking the samba server.  you might have to check the configuration of it on the windows laptop if so.  


add to global 
  guest account = nobody

and add to your shares
   guest ok = yes

not sure if this matters but i have  "wins support = yes" in my smbf.conf so could try changing that too.  thats my 2 cents worth maybe someone else might have something else to try if that doesn't work.

Hi!

I tried this and it didn't work :(

Thanks for trying though!

---

### Post by Morbius1 on 2010-06-06
You're the second person this weekend that had a global section that small. Where is this coming from? Some HowTo somewhere or is it the result of using some GUI package?

Let me give you one example of what's wrong with it - and it's just one example:

You have no way to convert a remote user to a guest because you have a line missing in the global section: "map to guest = Bad User" which despite it's name is the only way to map a user to the guest account.
> For all intents and purposes - sharing files over a lan without a  password between this ubuntu 10.04 machine and my wifes laptop (windows  7) should be trouble freeYou should be able to do this with Nautilus-share ( right click in nautilus > sharing options ) in about 10 seconds especially since you've mounted the target with a umask=000. But not with that smb.conf. you don't have any of the parameters that nautilus-share needs to work in that smb.conf.

I would respectfully recommend you consider the same advice I gave someone else in an eerily similar situation:

[http://ubuntuforums.org/showthread.php?t=1501504](http://ubuntuforums.org/showthread.php?t=1501504) ( See post #10 )

---

### Post by Morbius1 on 2010-06-06
There is one more thing since I'm packing up for the night and it has to do with Windows 7. If you have ""Windows Live Sign-In Assistant" installed on your Windows box you might consider uninstalling it because it appears it's sole purpose is to prevent any form of print or file sharing with linux:

[http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527](http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527)

---

