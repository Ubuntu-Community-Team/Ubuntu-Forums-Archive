---
title: "WPA password weirdness - cache large passwords?"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by webkris on 2009-03-25
Wireless working fine.
Able to connect to my home, clients, and friends WiFi.

Last night went to another friends house to show off my Dell Mini.
He's a bit of a security freak and had this LONG WPA passkey.
Like 52 something hex characters long. 'effa2f43gacc376b243...... etc'

Okay... He pops it onto a USB key and I copy it into my machine.
I connect to his wireless and have no issues. :D

This morning it so happens I'm at a new client and they have WPA WiFi setup. I click to connect and it asks me for the WPA password. I type in the 14 character password and hit connect.

nothing...
nothing....
waiting.....

Dialog box pops up - wrong password try again.
**Now for the weirdness:**
The 14 character password I typed in there is NOT there.
The 52 character password from the night before is in the field.

I delete it out and type in the 14 character pass again.
nothing...

Then I restarted my machine.
Same deal - this weird cached password is stuck in my WPA?
Super frustrated this morning that I have to type this on a Windows box... :p

Thanks!
- Kris

---

### Post by brianchidester on 2009-03-25
Are you making sure to enter it into the correct encryption type? (eg wpa v wep or passkey v passphrase)

---

### Post by webkris on 2009-03-25
> **brianchidester said:**
> Are you making sure to enter it into the correct encryption type? (eg wpa v wep or passkey v passphrase)

It's WPA-PSK. I setup the Pre-Shared Key.
Here's what I get:

[IMG]http://planetkris.com/misc/Screenshot-Wireless Network Authentication Required.png[/IMG]

For a password example I had "happy2wifi1" in there before.
Now it gives me this 64 (it's gotta be 64) character long deal.
Where is it storing this?
- Kris

---

### Post by brianchidester on 2009-03-25
I would almost bet that it is not the key you entered previously, it seems to be a quirk in this version of network manager -it automatically converts your entered password to hex. Have you not been able to connect to the wpa network at all since then (or ever)?

---

### Post by rdumas on 2009-03-25
I have had the same problem.  I originally set it up with my pass key, but every now and then when I boot up it say connection failed and in the box is this 64 digit key, I replace it with my own and I am back on.
What up with that?

---

### Post by webkris on 2009-03-25
> **brianchidester said:**
> I would almost bet that it is not the key you entered previously, it seems to be a quirk in this version of network manager -it automatically converts your entered password to hex. Have you not been able to connect to the wpa network at all since then (or ever)?

hmm - well it is true that I have never connected to this network.
I'm going to try WPA on a home router to see if I can get connected to a 'new' device or maybe it was problems with this access point.
-Kris

---

### Post by webkris on 2009-04-05
**Followup -**
This happened to me again and I gathered some more info.
I was helping a friend setup a secure wireless access point.
He enabled the AP and changed some settings while my computer was on.
I put in the password and it exhibited the same behaviour (in that I had a clear-text password in there and it was replaced with hex)
I couldn't connect and re-typed in the password 3+ times.

I restarted and logged on as soon as the wifi manager came up.
Restarting an OS to fix (anything) is not the Linux way. :|
- Kris

---

