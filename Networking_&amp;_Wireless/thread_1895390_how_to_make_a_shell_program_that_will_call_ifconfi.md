---
title: "how to make a shell program that will call ifconfig"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by Fertech on 2011-12-14
How can I make a lil shell program that will call ifconfig and will return back my ip address. I type echo "ifconfig" but that only prints back ifconfig. I save my with with extension .sh and type this at the command like chmod 777 and then I type ./myprogram.sh and I only get back ifconfig.

---

### Post by praseodym on 2011-12-14
IMHO the script needs to look like:

```
#!/bin/sh

ifconfig
```

---

### Post by Telengard C64 on 2011-12-14
What do you need from **ifconfig**'s output? Just the IP address?

For starters, you may try a script like this:

```
#! /bin/bash
ifconfig
```

Is this closer to what you expected?

---

### Post by Fertech on 2011-12-14
for now pretty much the ip address.

---

### Post by Telengard C64 on 2011-12-14
> **Fertech said:**
> for now pretty much the ip address.

By default, **ifconfig** prints info for all (1) your interfaces. Unless you specify the name of the interface you'll be getting all of them.

Try this in the terminal to see what I mean:

```
$ ifconfig | while read; do [[ "$REPLY" =~ "inet addr:" ]] && echo "$REPLY"; done
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
```

**_EDIT_**
If it still isn't clear to you, then I'll need to see your **ifconfig** output to grok how to parse it.

(1) **ifconfig** without any options prints all the interfaces which aren't currently *down*

---

### Post by Telengard C64 on 2011-12-14
If all you care about is the IP address of the first interface listed, then you could do something crazy like this:

```
ifconfig | while read a; do [[ "$a" =~ ([[:digit:]]{1,3}\.?){4} ]] && echo "${BASH_REMATCH% }" && break; done
```

Obviously this will fail with IP v6 addresses. It may even fail if no interfaces have assigned addresses (untested). There are probably twelve other ways it could fail (or more), but without some sample data I can't even guess.

---

