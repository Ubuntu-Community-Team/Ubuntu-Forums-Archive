---
title: "Cannot login to samba server with Windows xp"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Bigfootbuilt on 2010-12-28
I have the latest version of Samba, latest Ubuntu build, and have enabled Samba and decided to share 2 folders from my home folder on the linux box. I chose to not allow guest access and to require a password to login. The shared folders do show up on my XP box, but when I click on them and it prompts me for a username and password, the login info entered doesn't work. It just keeps asking me over and over again for a username and password. I have looked everywhere in the forums, and I have changed my smb.conf file as follows under the "authentication" section....

security = user
users = myusername

I cannot for the life of me figure out how to restart samba after saving this file, since the old commands do not work anymore, so I rebooted the pc and still get the same results. The shared folders show up on the XP box, but won't accept the login. 

Any suggestions welcome!

---

### Post by pricetech on 2010-12-28
How did you configure Samba ??  Samba configuration tool is the easiest way I've found.

Try this also;  Open a terminal and type:
```
sudo smbpasswd username
```
Substitute your username, enter your password once for sudo and twice for smbpasswd.

See if it works.

---

### Post by BbUiDgZ on 2010-12-28
try this:
backup your current config
```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.old

```

make new one
```

sudo nano /etc/samba/smb.conf

```

and add,
```

[global]
    security = share
      client lanman auth = Yes
      lanman auth = Yes

[ShareName]
    comment = your comment in here
    path = /path/to/your/share/
    read only = yes
    public = yes

```

so change "/path/to/your/share/" to whatever the path to the folder you want to share then save.

restart smbd
```

sudo stop smbd
sudo start smbd

```

now in the run box in winxp (windows key+R)
```
\\ip.of.your.server
```

---

### Post by Megadyne on 2011-02-15
Thank you PriceTech, that worked a treat. After wrestling all day to get the two PCs talking to each other, you've solved it. Thanks also to BigFootBuilt for posing the question in such a nice way that Google found this thread.  You are superstars!

---

### Post by Terry of Astoria on 2011-08-03
This worked for me. I had exactly the same problem in Natty Narwhal 11.04. I could see the shared folders from the windows machine but could not log in to the Ubuntu Samba server. 
After I followed the instructions, inserting my own shared folder address where it says
/path/to/your/share/
and adding my own comment there, 
I ended up with a samba share that worked! I could access and play my video files on my (XP) TV computer! The shared folder is titled, "Share Name" LOL!!! 
Thanks so much for posting that useful set of instructions. It took just seconds to solve that problem.

---

