---
title: "mce remote + receiver / transceiver model 1039"
date: 2007-10-13
forum: Mythbuntu
---

### Post by deffcon on 2007-10-13
Hello everyone,

Could some tell me how i can setup my mce remote + receiver / transceiver for use to control my amplifier via ir jacks that comes with this mce remote blaster. the reason why i asked this is that on Microsft i could use this to control my amplifier, what do i have to do with lirc to get this to work.

Thnx in advance,

Deffcon

---

### Post by superm1 on 2007-10-13
Well two things:

1) Those remotes have three programmable buttons: Vol+/Vol-/Power.  You can avoid using the IR blasters if you don't want anything beyond these buttons.

Otherwise, you need to get a lircd.conf that represents your amplifier and append it to the existing /etc/lirc/lircd.conf

From that point forward, its just a matter of

```
irsend -d /dev/lirc0 SEND_ONCE BUTTON
```

---

