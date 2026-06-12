---
title: "Multiple remote button clicks per actual click"
date: 2011-10-24
forum: Mythbuntu
---

### Post by koma77 on 2011-10-24
After upgrade from Mythbuntu 11.04 to 11.10 everytime I press a remote button it is interpreted (at least) twice.

This makes navigation in the menus almost impossible.

This is the case for my Logitech Harmony one remote, but also (to a bit lesser degree) to the origial Hauppauge remote.

Has something like this changed in lirc?

What can I try?

---

### Post by ian dobson on 2011-10-24
Hi,

I had exactly the same problem with my serial/hauppage 350 remote setup, and ended up manually editing the lirc config file.


Open your lircd.conf file in /etc/lirc and see what files are included (in my case /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge) and then edit the file deleting all remotes, other than the one you actually have.

To find which remote you have/lirc it using start a terminal window then run sudo irw and then press afew keys on the remote.

Regards
Ian Dobson

---

### Post by s13_mills on 2011-10-26
Hi there,

I had a similar issue to this in 11.10 and found changing the delay and repeat period in ir-keytable was the fix, but if you have not had to deal with ir-keytable at all it might be a different issue.

Hope this is helpful!

Cheers,

Andrew

---

### Post by koma77 on 2011-10-26
Interesting!

What is the ir-keytable, and where can I find one?

---

### Post by s13_mills on 2011-10-29
Hi There,

```
sudo ir-keytable
```

Will show you the properties you currently have set.

```
sudo ir-keytable --delay 500
sudo ir-keytable --period 50
```

Would set the delay before repeating to 500ms, and the repeat period to 50ms. You can have any value from 1 to 1410065407 (as far as I can tell).

Note that with your Harmony One, it may be repeating the signal itself after a certain delay, but this won't affect the Hauppauge remote, so you can use that to troubleshoot.

---

