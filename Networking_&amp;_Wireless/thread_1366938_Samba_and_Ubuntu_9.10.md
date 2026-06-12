---
title: "Samba and Ubuntu 9.10"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by crx686 on 2009-12-29
Hi

  I have 2 PC'S running ubuntu 9.10. I have a network hard drive which is in a enclosure running off my network. Its not hooked up to a computer. It has a web based software and its running a smb server. The problem i am having is in order to connect to it. I go to place then connect to server and connect and it connects I can view the files and write to it but when i try to listen to music off the network drive with XMMS or any media player it doesn't allow me to. in order for it to play I have to copy it to my home dir. I have 2 question 1. How do I make it stick to my desktop with out having to connect to it every time and 2nd how can i play music from the network drive without copying it to my computer. this is what i've done so far I installed samba smbclient smbfs and this is what my smb.conf looks like


[global]
workgroup = KNIGHTRR
netbios name = KIT
server string = musicserver
local master = yes
preferred master = yes
os level = 20

[Music]
path =/home/crx686/Music
comment = Music On %L
read only = no
writeable = yes
browseable = yes


[Photo's]
path =/home/crx686/Pictures
comment = Photo's on %L
read only = no
writeable = yes
browseable = yes
printable = yes


  The other thing is when i go to network i get a error saying unable to mount location Failed to retrieve share list from server. I have 2 other XP machine that connect to the network drive and it works fine, not trying to get XP to see my 2 ubuntu machines. If anyone can help that would be great thanks for your time
Ben

---

### Post by dmizer on 2009-12-29
Please see the 6th link in my sig.

---

### Post by crx686 on 2010-01-01
I still can't play music from my network drive thou and I still can't browse

---

### Post by dmizer on 2010-01-01
If you want a music server, why not just install a program built to do it. Something like [mediatomb]("http://mediatomb.cc/"). It's available in the repositories so it can be installed via synaptic.

---

### Post by crx686 on 2010-01-03
Its music / file server its a Vantec enclosure that has a SMB Sever built in. I don't have to leave a computer on. I can see where your going with this and it looks like I have to do it that way cause I can't seem to get it to work right. I bought the enclosure for this purpose so my wife can access her files and music without me leaving on my computer. The other main thing i got it for is if we have a fire and we need to leave I can just take that enclosure with all of our personnel files. Sorry for me going on. I would like for it to work.

---

### Post by dmizer on 2010-01-03
> **crx686 said:**
> Its music / file server its a Vantec enclosure that has a SMB Sever built in. I don't have to leave a computer on. I can see where your going with this and it looks like I have to do it that way cause I can't seem to get it to work right. I bought the enclosure for this purpose so my wife can access her files and music without me leaving on my computer. The other main thing i got it for is if we have a fire and we need to leave I can just take that enclosure with all of our personnel files. Sorry for me going on. I would like for it to work.

If the enclosure has a Samba server on it, why are you trying to configure a samba server on your Ubuntu box then?

You should be able to access the enclosure after following my "fix samba browsing" thread ... 6th link.

---

### Post by crx686 on 2010-01-03
I didnt think i was configuring as a server i thought i was configuring as a client? does the client still use the smb.conf? I go through the 6th sig again. I'm kinda of wondering what do i need on my ubuntu boxs to use shares on a SMB server then? Thanks for your help

---

### Post by crx686 on 2010-01-04
I got my browsing to work, i had to uninstall everything that dealed with samba and just installed samba and winbind again and i can see all of my windows machines. as for playing music over the network I just changed what player i was using, for some reason xmms wont play anything on a smb share. Apparently its a known problem with xmms and toem. Thanks for your help

---

