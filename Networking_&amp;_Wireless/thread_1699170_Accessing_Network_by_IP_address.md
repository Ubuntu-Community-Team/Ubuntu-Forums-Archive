---
title: "Accessing Network by IP address"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by amir786_z on 2011-03-03
Hi there guys.. can someone tell me how can I access the network share by an IP address if I know the IP address of that particular computer.. 

thanks:)

---

### Post by amir786_z on 2011-03-06
OMG so many views but no one suggested anything:(:(:confused:

---

### Post by JRV on 2011-03-06
To access a Windows share from the command line use:
```
nautilus smb://000.000.000.000/SHARENAME
```

---

### Post by amir786_z on 2011-03-06
Thank u sir for the reply i will check it out.. :):)..

---

### Post by amir786_z on 2011-03-07
> **JRV said:**
> To access a Windows share from the command line use:
```
nautilus smb://000.000.000.000/SHARENAME
```

sir i tried to run this code in the terminal
```
nautilus smb://192.168.001.004/umair
```

umair is the host name of the above PC and is using windows 7.


but it gave an error "Failed to mount Window share. Please select another viewer and try again"

---

### Post by Morbius1 on 2011-03-07
> umair is the host name of the above PC and is using windows 7The syntax of the line can be either:

nautilus smb://ip-address/share-name
OR
nautilus smb://host-name/share-name

What you did was:
nautilus smb://ip-address/host-name

There is no such thing.

---

### Post by amir786_z on 2011-03-07
> **Morbius1 said:**
> The syntax of the line can be either:

nautilus smb://ip-address/share-name
OR
nautilus smb://host-name/share-name

What you did was:
nautilus smb://ip-address/host-name

There is no such thing.

Thanks for the reply.
i have tried both the commands that u said
```
nautilus smb://ip-address/share-name
```
```
nautilus smb://host-name/share-name
```

giving the same error that "Failed to mount Window share. Please select another viewer and try again"

---

### Post by SeijiSensei on 2011-03-07
Are you replacing "share-name" with the actual name of the exported share on the Windows computer?  Are you sure you've set up browsing correctly in Windows?

---

### Post by Morbius1 on 2011-03-07
Let's try this to avoid any misunderstanding:

```
 nautilus smb://192.168.1.4
```

What should happen is that nautilus will open up to 192.168.1.4 and show you a list of available shares on that box.

---

### Post by amir786_z on 2011-03-07
> **Morbius1 said:**
> Let's try this to avoid any misunderstanding:

```
 nautilus smb://192.168.1.4
```What should happen is that nautilus will open up to 192.168.1.4 and show you a list of available shares on that box.

thank u so much sir it worked :P:):):P. cheers!!

---

