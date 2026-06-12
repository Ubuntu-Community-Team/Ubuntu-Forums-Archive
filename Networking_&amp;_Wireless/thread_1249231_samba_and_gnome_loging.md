---
title: "samba and gnome loging"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by pthriskos on 2009-08-25
Being a newbie at Linux I apologize if this is a foolish question.

Q1) I've installed samba on a machine and have set it up as a domain member (security = domain). I'm able to login to my machine using winbind. I've created a share in smb.conf that I want other machines (running windows/linux) to access it. But I want them to authenticate using a PDC as the password server.  Any ideas how to do that ?

My smb.conf

[global]
netbios name = Client
server string = Samba client
workgroup = somedomain.com
security = domain
password server = *

idmap uid = 6000-7000
idmap gid = 8000-9000

domain logons =no
domain master = no
local master = no
prefered master = no
os level =0
encrypt passwords = yes

winbind trusted domains only = yes
winbind use default domain = yes

[mydir]
path = /mnt/test
valid users= someuser
browseable = yesQ2) When in GNome I can browse our network using Places->Network. But when I try to logon to the file server I'm constantly asked for a password. I can of course enter it and ask GNome to permantly save it. Is the a way to acomplish single sign-on. After all I've keyed in my password when I've loged on the first time.



Thank you in advance for any help :P

---

