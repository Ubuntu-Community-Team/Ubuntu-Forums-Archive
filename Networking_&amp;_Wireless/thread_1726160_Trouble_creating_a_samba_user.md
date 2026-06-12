---
title: "Trouble creating a samba user"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by wagoner on 2011-04-10
I have a simple home network with about three pc's.  I have a samba share on desktop #1 (adam) running Kubuntu Lucid, another desktop with Win XP Pro, and a laptop with Win7 Home (Joyce).  I got the share to work with 
```
force user = adam
```

I would prefer to add Joyce as a samba user to Kubuntu desktop so I tried:
```
adam@dell16:~$ sudo useradd -s /bin/false Joyce
adam@dell16:~$ sudo smbpasswd Joyce
New SMB password:
Retype new SMB password:
Failed to find entry for user Joyce.

```
(I suppose I don't need this really, but I feel the need to tinker with this ;))  [B][COLOR="RoyalBlue"]Why didn't it find the entry for Joyce?
[/COLOR][/B]
I am trying to keep the Kubuntu box as uncluttered as possible, so I included the -s /bin/false in the useradd command.

---

### Post by bab1 on 2011-04-10
> **wagoner said:**
> I have a simple home network with about three pc's.  I have a samba share on desktop #1 (adam) running Kubuntu Lucid, another desktop with Win XP Pro, and a laptop with Win7 Home (Joyce).  I got the share to work with 
```
force user = adam
```

I would prefer to add Joyce as a samba user to Kubuntu desktop so I tried:
```
adam@dell16:~$ sudo useradd -s /bin/false Joyce
adam@dell16:~$ sudo smbpasswd Joyce
New SMB password:
Retype new SMB password:
Failed to find entry for user Joyce.

```
(I suppose I don't need this really, but I feel the need to tinker with this ;))  [B][COLOR="RoyalBlue"]Why didn't it find the entry for Joyce?
[/COLOR][/B]
I am trying to keep the Kubuntu box as uncluttered as possible, so I included the -s /bin/false in the useradd command.

Where did you **[COLOR="Red"]look for[/COLOR]**  **[COLOR="RoyalBlue"]the entry for Joyce?[/COLOR].**

---

### Post by Morbius1 on 2011-04-10
It's getting late in the day for me so perhaps I'm reading this wrong but you just created a local user joyce and did a "sudo smbpasswd joyce".

smbpasswd without an argument will attempt to change joyce's samba password. Joyce isn't in the database yet because you didn't add her yet:

```
sudo smbpasswd -a joyce
```The "-a" will add and enable a "joyce" entry in the database.

---

### Post by wagoner on 2011-04-10
Yes.  That fixed it.  Forgot the "-a"

---

