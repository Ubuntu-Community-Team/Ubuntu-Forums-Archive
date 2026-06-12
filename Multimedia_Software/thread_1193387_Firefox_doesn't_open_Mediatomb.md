---
title: "Firefox doesn't open Mediatomb"
date: 2009-06-21
forum: Multimedia Software
---

### Post by spursncowboys on 2009-06-21
> Failed to Connect - Firefox can't establish a connection to the server at 192.168.x.xxx:xxxxx.
Is what it reads when I click on my bookmark for Mediatomb. 
  I installed and used mediatomb on my ps3 and it worked perfectly. Then it did this once, and I waited a few hours and tried again and it worked. Since then, however, it has not worked. Also when I went to Applications>Sound&Videos>Mediatomb I got a > The requested operation could not be completed-Connection to Server Refused The only thing I changed in the computer was that I installed nvidia drivers and enabled 3d effects.
I attached the two screen shots.

---

### Post by markbuntu on 2009-06-21
Is the port number correct and it the port open on the server?

---

### Post by spursncowboys on 2009-06-22
> **markbuntu said:**
> Is the port number correct and it the port open on the server?
I am not sure. I am going to go back to the tuturial I used and find out.

---

### Post by spursncowboys on 2009-06-23
> **markbuntu said:**
> Is the port number correct and it the port open on the server?
Ok I just reinstalled mediatomb. Now Firefox is recognizing it. Also Ps3 is finding it. 
How do I check the port number? How do I know if it is correct? And how do I check to see if it is open?

---

### Post by AndyCee on 2009-09-06
A program called nmap is great for that.

```
sudo apt-get install nmap
```

Then type 
```
nmap localhost
```
or
```
nmap <server-name>
```

and it will show all the ports that are open on that machine.

---

