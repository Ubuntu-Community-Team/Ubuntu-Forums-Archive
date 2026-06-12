---
title: "connecting to windows AD with likewise problems"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by fillip1208 on 2010-08-03
Hi all,

Im very new to ubuntu desktop/server. I've been playing with the server edition for a few weeks and have been trying to attach it to my windows domain at work. i DID manage to do this and it worked with my AD logins fine.

i removed myself from the domain to try and help someone with gettin a second machine on there and now im not able to re-join.

Im using likewise open 6, i have installed it and im using 

```
domainjoin-cli join DomainName DomainUser
```

when i run this, it thinks about joining for a couple of minutes then throws me this error message.

```
Error: LW_ERROR_ERRNO_EPIPE [code 0x00009cf9]
```

it throws this up after i've entered my AD password. 

any ideas or help would be muchly appreciated :)

Thanks,

Phil

PS; im sorry if this is in the wrong section of the forums. i wasnt sure if it would be the server section or networking

---

### Post by fillip1208 on 2010-08-07
nevermind

---

### Post by oneloveamaru on 2011-09-21
I am having this same issue but you just posted Nevermind. What was the fix?

---

### Post by oneloveamaru on 2011-09-21
I believe I figured it out. Hostname of the Linux box must be FQDN. Once I changed it to FQDN it let me join without an issue.

AND the first search domain in /etc/resolv.conf needs to be the domain you are joining.

---

