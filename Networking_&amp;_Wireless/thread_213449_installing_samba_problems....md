---
title: "installing samba problems..."
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by Burritos on 2006-07-11
I can't seem to get samba to work correctly:

this is what I have done:

[I]sudo apt-get install samba
sudo apt-get install smbfs
sudo smbpasswd -a burrito
[/I]
then typed and confirmed my password

then in /etc/samba/smbusers I added this line:
*burrito = burrito*
I also tried
*burrito = "burrito"*
and (thinking maybe I had to have a different name:
*burrito = burritos*

next in: /etc/samba/smb.conf I uncommented this line
*security = user*
and added this line right below it:
*username map = /etc/samba/smbusers*

finally I added this to the end of my smb.conf file:
[I]
[music]
  comment = music folder
  path = /var/www/music
  public = yes
  writable = yes
  valid users = burrito
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nobody
[/I]

I also tried it w/o the 'valid users' directive

after saving my file I ran 'testparm' and received this for my output
[I]burrito@tacostand:/etc/samba# sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[music]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
[/I]

which looks ok to me...save the one minor warning.

I then restarted my samba services and tried to map a drive from my windows xp machine adn get this error:

"The mapped network drive could not be created because the following error has occurred:  An extended error has occurred"

I'm at a complete loss of what to try next, can anyone shed some light on this please?

---

### Post by adawson on 2006-07-17
I have the same problem can anyone help!!!

rgds,

Anthony

---

### Post by bforbes on 2006-07-17
Assuming your Linux username is burrito, you need to do this:
```

smbpasswd -a burrito

```
Then reboot your samba daemon:
```

sudo /etc/init.d/samba restart

```

---

