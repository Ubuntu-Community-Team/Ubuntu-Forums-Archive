---
title: "Can't Use Samba Share on Vista to Ubuntu 10.10"
date: 2011-04-14
forum: Networking &amp; Wireless
---

### Post by NatHarari on 2011-04-14
Hi there,

I'm completely stumped. I can't get Samba share to work with windows or anything else when trying to authenticate a user. It does work when I force all to a certain user and allow guests, but if I want to protect a directory with a password, it doesn't work.

I'll include everything below.


What DOES work:

[STORAGE]
        comment = STORAGE
        path = /media/Storage
        browseable = yes
        writeable = yes
        valid users = nat, nobody
        available = yes
        public = yes
        create mask = 0777
        directory mask = 0777
        force user = nat
        force group = nat


Unfortunately, that doesn't protect my directory with a password. I want to change it so that only certain people can access it.


What DOESN'T work:


[Design]
        writeable = yes
        wide links = no
        path = /media/Storage/GraphicDesign
        only user = yes
        write list = nat,graphicdesign,@nat,@graphicdesign
        force group = graphicdesign
        revalidate = yes
        force user = graphicdesign
        comment = GraphicDesign for the GD Team
        valid users = nat,graphicdesign,@nat,@graphicdesign
        user = nat,graphicdesign,@nat,@graphicdesign
        create mode = 0777
        directory mode = 0777
        available = yes
        public = no
        browseable = yes

I checked and SMB Passwords have been added, as well as SMB Users (I did all this in webmin as well as the command line)...

When trying to log in from Vista, I have to add the Domain:

DOMAIN\nat
"password"

And I cannot, for the life of me, log in. I have no idea why.

I get the following error in the log at /etc/log/samba:


[2011/04/14 10:22:31.864161,  1] smbd/service.c:678(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED



I've googled this for hours and I cannot find any solution that works for me. Either I'm overlooking something incredibly simple and will feel like a complete idiot when it's pointed out, or there's something I haven't done that I have to do and don't understand yet what it is....

I'm hoping somebody can help.

Thanks for any info.

---

