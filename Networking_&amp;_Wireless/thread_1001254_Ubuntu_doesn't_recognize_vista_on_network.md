---
title: "Ubuntu doesn't recognize vista on network"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by inxygnuu on 2008-12-03
Hello, I am currently trying to network vista and Ubuntu together, but Ubuntu wont recognize the vista machine. i had the network going with my vista(so I know most networking basics), but I cant see it with Ubuntu. How can i configure Ubuntu to recognize the vista machine?:confused:

---

### Post by theozzlives on 2008-12-03
> **inxygnuu said:**
> Hello, I am currently trying to network vista and Ubuntu together, but Ubuntu wont recognize the vista machine. i had the network going with my vista(so I know most networking basics), but I cant see it with Ubuntu. How can i configure Ubuntu to recognize the vista machine?:confused:

are you using samba?

---

### Post by doas777 on 2008-12-03
Vista uses NTLMv2 exclusively for authentication.

I usually install samba ([https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)) and then edit the configuration:
```
gksu gedit /etc/samba/smb.conf
```

and under the authentication section i add the line:
```
client NTLMv2 auth = yes

```

save, exit and run:
```
sudo /etc/init.d/samba restart
```

then you should be able to login to your vista shares. unfourtunatly getting point and click browse is somewhat tricker.

have fun

---

### Post by inxygnuu on 2008-12-03
> **theozzlives said:**
> are you using samba?

yes.

---

### Post by inxygnuu on 2008-12-03
> **doas777 said:**
> Vista uses NTLMv2 exclusively for authentication.

I usually install samba ([https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)) and then edit the configuration:
```
gksu gedit /etc/samba/smb.conf
```

and under the authentication section i add the line:
```
client NTLMv2 auth = yes

```

save, exit and run:
```
sudo /etc/init.d/samba restart
```

then you should be able to login to your vista shares. unfourtunatly getting point and click browse is somewhat tricker.

have fun

what authentication section, and how do i logon?:confused:

---

### Post by doas777 on 2008-12-03
ok, lets start from the top.
first open a terminal from Programs -> Accessories -> Terminal

first type:
```
 gksu gedit /etc/samba/smb.conf
```
a text editor should pop up.

it doesn't matter where you place the line in your file. in the default ubuntu smb.conf it has a number of sections. it doesn't matter if yours doesn't.

add the this line to the file, whereever you wish:
```
client NTLMv2 auth = yes
```

then save and exit. restart samba as above.

now to access your share, open a nautilus window, and make sure your using a "text-based Location bar", then type:
```
smb://serverIP/sharename
```
if you have a DNS or wins server, you can connect with servername instead of IP.
if the share requires authentication, (and it prolly does), then a login window will pop up. give it a username and password valid on the server, and it should let you right in.

---

### Post by inxygnuu on 2008-12-03
when i type "smb://INXYGNUU%20CORP./" nothing pops up, and I know i sound dumb, but i don't know what a share is. Thanks though!;)

---

### Post by doas777 on 2008-12-03
> **inxygnuu said:**
> when i type "smb://INXYGNUU%20CORP./" nothing pops up, and I know i sound dumb, but i don't know what a share is. Thanks though!;)

you will need to know a share name at this point. if you have an admin account on the server, you can use c$ for your share. 

do you have a DNS or wins server? if not, you will need to kwno the IP address of the host, not just it's name. the name looks a touch off as well.

---

### Post by inxygnuu on 2008-12-03
to answer you question, It is a Netgear wireless router. All i need to do is access the printer on the vista computer to print some homework.

---

### Post by doas777 on 2008-12-03
> **inxygnuu said:**
> to answer you question, It is a Netgear wireless router. All i need to do is access the printer on the vista computer to print some homework.

that is a horse of a different color. do you know the printer share name on vista? I havn't had too much luck with samba printing thus far (no lin drivers for my printer) so I can;t help you there. 

good luck

---

### Post by inxygnuu on 2008-12-03
yes, all I need to do is access the computer and it should be able to find the printer.;)

one step at a time though, and this one is first...

---

