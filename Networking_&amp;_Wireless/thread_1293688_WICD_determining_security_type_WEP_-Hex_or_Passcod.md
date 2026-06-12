---
title: "WICD: determining security type WEP -Hex or Passcode."
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by strider22 on 2009-10-17
Is there a simple way to tell whether I should choose Hex or passcode for WEP with WICD? What I should try first?
How about whether encrypted is needed?

Does anyone have a routine they follow to login on strange networks?

Why does WICD need to be told when the other O/S doesn't need to be told?

When I go to a new location I have to thrash around to figure out what type to use.
For example this Thanksgiving (Canada), I went to my sister's and although wicd said they had WEP protocol, there are 3 wep types and 2 encryption options for 6 choices. Not so bad except that they didn't quite remember the password, so I had 5 choices to try. With those 30 options, I used up more than an hour before I got it (2 hour battery life).  It was Hex+encrypted, I thought it was passcode.

I noted that the other O/S didn't need to be told hex or passcode and that the other O/S solved the which password issue. Boo! Hiss!

p.s. For some reason during the thrashing/trials, the network disappeared from wicd although it was still working for others. I could only get it back by rebooting and hence the extra time required.

---

### Post by amingv on 2009-10-17
Depends, if your password is a string of hex numbers, like:
```
0F62D47266547B3D907FD4F2CC
```
Then pick "hex". If it's the word used to generate the hex string (a normal word or string you input in your router), then use that word and "passcode".

Please have in mind, though, that WEP is deprecated and very insecure. If it's possible I'd recommend switching to WPA-PSK at least.
If for some reason you can't use WPA-PSK, I'd be good to change your WEP passcode regularly.

---

### Post by Leo Simon on 2013-01-04
Hi Strider22

Was glad to find your question from many years ago.   I have all the same issues.    Did you ever find a good way to figure out whether the security type is WEP, WPA, or whatever?    Also, I often find that I can connect using this default gnome interface (which as you note figures out the security type on its own) but not thru wicd (after trying all conceivable combinations)

---

