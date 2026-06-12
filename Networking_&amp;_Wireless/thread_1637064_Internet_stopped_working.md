---
title: "Internet stopped working"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by dudironimis on 2010-12-04
My internet just went out on me. I originally thought the wifi card stopped working. It won't even let me "Enable wireless networking." I hooked my laptop up to the router to see if I could just reinstall the drivers. It showed my cards driver as deactivated, but it won't reactivate. When I'm hooked up directly it won't let me do anything either.

---

### Post by Off Topic on 2010-12-04
Since you cant see this without the internet....

[IT_Crowd_Voice]Have you tried turning it off and on again[/IT_Crowd_Voice]

---

### Post by lisati on 2010-12-04
> **Off Topic said:**
> Since you cant see this without the internet....

[IT_Crowd_Voice]Have you tried turning it off and on again[/IT_Crowd_Voice]

:D
Could be using another machine and/or OS.....

---

### Post by dudironimis on 2010-12-04
> **Off Topic said:**
> Since you cant see this without the internet....

[IT_Crowd_Voice]Have you tried turning it off and on again[/IT_Crowd_Voice]
Yes I have tried turning it on and off, multiple times. I'm using my desktop right now.

---

### Post by dudironimis on 2010-12-04
bump
if that isn't aloud I apologize in advance.

---

### Post by dineshs on 2010-12-04
Are you using network manager?What does ```
lshw -C network
``` and ```
sudo cat /var/lib/NetworkManager/NetworkManager.state
```say?

---

### Post by dudironimis on 2010-12-04
1

---

### Post by dudironimis on 2010-12-04
> **dineshs said:**
> Are you using network manager?What does ```
lshw -C network
``` and ```
sudo cat /var/lib/NetworkManager/NetworkManager.state
```say?
for lshw it says a lot more than I want to type. For the second one it says "cat: ... no such file directory" 	
I opened it by going through the files and it says 
networkingenabled=true 
wirelessenabled=true
WWANenabled=true

---

### Post by dudironimis on 2010-12-05
bump

---

### Post by dudironimis on 2010-12-13
still doesnt work. can anyone help me?

---

