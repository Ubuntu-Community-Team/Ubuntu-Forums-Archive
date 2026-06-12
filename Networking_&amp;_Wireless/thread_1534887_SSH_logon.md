---
title: "SSH logon"
date: 2010-07-20
forum: Networking &amp; Wireless
---

### Post by rick_au on 2010-07-20
Hi everyone,

I wasn't sure which board to post this so feel free to move it. 

first of all, when ever I have had a problem with ubuntu google always leads me here, and there has almost been a solution for all of my problems on this website. So thank you ubuntuforums! 

Basically I want to connect to a SSH tunnel on my webserver hosted with dreamhost. 

I found a guide which is relevant to me here  [http://antrix.net/journal/techtalk/ssh_tunnel.comments](http://antrix.net/journal/techtalk/ssh_tunnel.comments)

The first part was entering 

```
alias ssh-tunnel='ssh -N -v -D 8080 mydomain.com'
```followed by
```
 ssh-tunnel
```once i run this, it gets a response from the server and wants my to type in my SSH password. 
```
rick@XXXXXXXXXX.com's password: 

```the only problem is that my SSH logon is actually " rickssh ". 
I have attempted to create a SSH key, however defaults as "rick"(which is my local ubuntulogon" 

Is there anyway of getting around this? 

Thanks :)

---

### Post by rick_au on 2010-07-20
I new the answer would be simple! 

it was just adding rickssh@ before the address in ```
alias ssh-tunnel='ssh -N -v -D 8080 mydomain.com'
```

---

### Post by iponeverything on 2010-07-20
try this instead:

```
alias ssh-tunnel='ssh -N -v -D 8080 rickssh@mydomain.com'
```

edit:

you beat me to it!

---

### Post by rick_au on 2010-07-20
Yep it all works :D

Where i actually want to use it, the internet connection is behind a restrictive proxy. Port 22 is the only port open which does not need proxy authentication. Will this do the trick?

---

### Post by robsablah on 2010-07-20
> **rick_au said:**
> Yep it all works :D

Where i actually want to use it, the internet connection is behind a restrictive proxy. Port 22 is the only port open which does not need proxy authentication. Will this do the trick?

if the ssh server is listening to port 22 i believe

---

