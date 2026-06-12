---
title: "Can't create SSH-tunnel in script"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by erkswede on 2010-09-17
Hi al

I'm trying to run a script to execute the command
```
ssh -D *port host*
```
when my laptop connects to internet. I have placed the script in /etc/network/if-up.d/

The scripts is being run when it should, but the SSH-tunnel isn't created.

I can however run the script manually, as root, and then the tunnel is created.

Help please! Thanks!
/Erk

---

### Post by Brandon Williams on 2010-09-17
What kind of authentication are you using for the connection? If it's password-based, then this won't work. If it's key-based, then how are you specifying the key? It could be that the key is being read from your user-level key agent after you log in, and that's why the script appears to work from within a login session.

---

### Post by erkswede on 2010-09-17
It's key-based authentication. I generated the keys as root and made an key exchange procedure which placed keys in "authorized_keys2" in .ssh directory in the home directory of the root user.

If the script is actullay run as different user than root, then I guess it wouldn't work. I don't know what user or process is running this script from /etc/network/if-up.d/, but perhaps it's the currently logged in user? (Which isn't root)

---

### Post by SeijiSensei on 2010-09-17
Try naming the file simply "authorized_keys".

---

### Post by erkswede on 2010-09-18
Keys are working fine.

I think it has do with which user is running the script. How can I determine that?

---

### Post by erkswede on 2010-09-18
Nope. The scrip is run by root. Something else must be wrong here. Basic problem still the same: Script is working fine when executed manually in a terminal, but not when it's executed automatically.

I'm not that familiar with scripting under Linux, so I'm guessing here. Is this script somehow running in the background and missing stdin or out, or somthing along this line?

---

### Post by Brandon Williams on 2010-09-18
When you run the script from the command line, do you get a shell prompt on the remote machine? If so, then this may be a problem related to access to a controlling terminal. Try adding both -N and -n to your ssh command line if they aren't already there. If you are already using -f to put ssh into the background, then -n is already implied.

---

### Post by erkswede on 2010-09-19
Yep, it starts a shell prompt on the remote machine. The -N switch did the trick. Thanks!

---

