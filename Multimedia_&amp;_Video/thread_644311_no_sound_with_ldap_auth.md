---
title: "no sound with ldap auth"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by saulo2 on 2007-12-18
Hi everybody

This is my first post here in Ubuntu Forums.

I work in a government school in my country; We have some info labs and I'm installing ubunto 7.10, with gnome, on it's machines; I have choose ubunto and gnome for it's simplicity, usability, this makes it ideal for first time users, and also the expert ones.

I have also installed an smb server, to provide common disk space for the users, and a ldap server to provide a central authentication.

I's working, authenticating on ldap and mounting home folders using samba filesystem.

But I have a problem with sound, because my users are not local users, are not in the sound group, and cannot use sound device... I created a sound group in the ldap server, I can see it when I command 'getent group', and placed an ldap user inside it; but it didnt work... that user still cant use soud.

is there something in Ubuntu I can do to solve this?

Thanks a lot

Saulo

---

### Post by mbradlcu on 2008-03-17
seems today is the day my head broke through the wall, 
this fix worked for me, edit:
> 
/etc/udev/rules.d/40-permissions.rules


add the following so the file looks like:
> 
# Sound devices
SUBSYSTEM=="sound",			GROUP="audio"
SUBSYSTEM=="sound",		MODE="0666"


please let me know if you have any questions

---

