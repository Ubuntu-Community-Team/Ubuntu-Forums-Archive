---
title: "Network Drive"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by blackangelpr on 2012-04-30
Greetings, Since the beta i have been unable to connect my network drive;
If this had happened to anyone else please share what you guys or girls did it to fix it

NAS Administration settings screen shot is on attachment session.

Thanks in advance...:KS

---

### Post by blackangelpr on 2012-05-02
Aquick Update:  Today there was an update and i also notice even with it the internal card reader writer do not mount any memory plugged in unless its a usb ,,, none of the SD, micro sd etc mount when plug it in,,, still the light blink.. Any idea?:confused:

---

### Post by blackangelpr on 2012-05-02
I found a similar problem and it worked out:

 [http://ubuntuforums.org/showthread.php?t=1970533&highlight=smb](http://ubuntuforums.org/showthread.php?t=1970533&highlight=smb)

by typing on the terminal:
```
 nautilus smb://NAS_CRISTOBAL/PUBLIC 
```thanks to Mr. JRV who posted on the link above...

now still have two issues pending the auto mount of it and the sd card reader ....;)

---

### Post by blackangelpr on 2012-05-02
Prof of mounted driver...  

i had try the following: 

```
//NAS_CRISTOBAL/PUBLIC /opt/share cifs -o username=admin, password=PASSWORD
 
```

and with the actual ip adress

```
//192.168.1.101/PUBLIC /opt/share cifs -o username=admin, password=PASSWORD
 
```

---

### Post by blackangelpr on 2012-05-04
> **blackangelpr said:**
> I found a similar problem and it worked out:

 [http://ubuntuforums.org/showthread.php?t=1970533&highlight=smb](http://ubuntuforums.org/showthread.php?t=1970533&highlight=smb)

by typing on the terminal:
```
 nautilus smb://NAS_CRISTOBAL/PUBLIC 
```thanks to Mr. JRV who posted on the link above...

now still have two issues pending the auto mount of it and the sd card reader ....;)


Update: The code below have been able to fix the auto mount for my NAS even if i rebooted my computer, start my NAS after ubuntu was running etc... i will call this Solved...

---

