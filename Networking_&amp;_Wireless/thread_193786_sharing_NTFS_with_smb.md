---
title: "sharing NTFS with smb"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by fargoth on 2006-06-10
i can share my home directory just fine, but NTFS won't work...

this is what i got in my /etc/smb.conf file:
```

[C:\]
path = /media/sda1
comment = winXP's files
available = yes
browseable = yes
public = yes
writable = yes

```
tried changing the writable = yes to no, but it doesn't make any difference....
i set the permissions of sda1 to match those in my home directory (i.e. others and group can read and execute)
but for some reason the home directory opens just fine while the sda1 won't open - the other computers see it but get an error message....

does anyone know whats the problem?
ive searched the forum and someone managed to share his NTFS (on a post from yesterday), but he did nothing i haven't done.... where am i wrong?

---

### Post by Slim Odds on 2006-06-10
[quote=fargoth]
does anyone know whats the problem?
ive searched the forum and someone managed to share his NTFS (on a post from yesterday), but he did nothing i haven't done.... where am i wrong?[/quote] 
Writable NTFS in linux is not well supported and is experimental

You might want to tell us what the error message was.

---

### Post by fargoth on 2006-06-10
well, i dont care if it'll be a read-only share, thats why i changed the line
writable = yes to writable = no.
and i set the sda1 in fstab to load with 0222 so that everyone can read and execute....

i get this message on the windows computer which tries to access my drive:
[quote=message]
\\Master-desktop\C:\ is not accessible. you might not have permission to use this network resource.
contact the administrator of this server to find out if you have access permissions.

The network path was not found.
[/quote]

it can access the other directories i share though (i.e. incoming in /home/master/.mldonkey or /home/master)...

any ideas?

---

### Post by fargoth on 2006-06-10
ok, i've looked at the log files smb makes:

[quote=log.familio]
[2006/06/11 03:49:18, 0] smbd/service.c:make_connection(846)
  familio (10.0.0.6) couldn't find service c:
[/quote]

so thats the problem.... why does this happen?

---

### Post by fargoth on 2006-06-10
heh, stupid me.... i've just chosen i bad name for this share....
changed it to "C" instead of "C:\" and now it works fine!
i think the error with this name is because of the \ - windows asks for c: because the \ is interperated as just the end of the address, while linux shares c:\ and doesn't recognize c: as a shared resource.
:-D

---

### Post by epohs on 2006-06-10
should that be *umask=022* or *umask=0222* ?

---

### Post by fargoth on 2006-06-11
its 0222 (i though it should've been 222, but that didn't work... 0222 give everyone r+x)

---

### Post by Slim Odds on 2006-06-11
[quote=fargoth]its 0222 (i though it should've been 222, but that didn't work... 0222 give everyone r+x)[/quote] 
It does need the leading zero, that specifys octal. Each group of attributes is 3 bits wide.

---

### Post by epohs on 2006-06-11
[QUOTE=fargoth]its 0222 (i though it should've been 222, but that didn't work... 0222 give everyone r+x)[/QUOTE]


That worked perfectly, thank you!

---

