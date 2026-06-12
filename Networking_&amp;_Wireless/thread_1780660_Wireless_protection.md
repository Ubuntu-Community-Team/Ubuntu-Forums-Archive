---
title: "Wireless protection"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by bak&#305;r on 2011-06-12
I am a relatively new user of Ubuntu and have a quite odd problem. First, I was unable to connect wireless through my modem. I am now able to connect wireless, but strangely it did not ask me to enter WEP password, which windows asks. In other words, **any** Ubuntu user can connect to my network. Is there a way to solve my security problem?

---

### Post by superduperlinuxperson on 2011-06-12
to be honest, that is the strangest problem i have ever heard!!!!!!
try going to edit connections on the Network Manager, then clicking on the wirelesss, then your network name, then the security tab and check what the password says
does it ask you for a login keyring when you start the computer and it shows you the desktop?

---

### Post by josephmills on 2011-06-12
first thing I would do is change my security setting for my router to wpa2 then I would make the password over 30 characters long using 0 instead of o and 1 instead of l and make sure that there are no words that are in dictionaries in you password that should make the difference

---

### Post by bak&#305;r on 2011-06-12
@superduperlinuxperson,

I checked: the WEP key written there is correct! By the way, I formatted and re-installed a dual boot, so it is also impossible that it was stored from a previous login. I really cannot understand.
After each restart, the system only prompts me to enter authentication password, if I want to perform a system operation. Otherwise, it does not ask anything.

I think I should also mention that I am psychologically fully normal. :p


@josephmills,

Thanks for the advice, I will change it.

---

### Post by superduperlinuxperson on 2011-06-12
theres your "problem"!!!
the authentication is the key ring which unlocks several things, including the wireless key!
hope this is right

---

### Post by bak&#305;r on 2011-06-13
Are you sure? WEP key is something that a modem demands, but the authentication key is a user-defined value during Ubuntu setup.

I also tried changing the WEP key with another computer, but Ubuntu was able to detect new password and connect!  I still cannot understand how, but my computer seems to somehow break the WEP password protection. Everything is OK with WPA, however.

---

### Post by superduperlinuxperson on 2011-06-13
i am positive, because at start up my computer asks for authentication, and if i click cancel it wont connect to the internet

---

