---
title: "mythbuntu-lircrc-generator generates empty .lircrc"
date: 2008-03-25
forum: Mythbuntu
---

### Post by theonlyandy on 2008-03-25
Hello everybody.

I just found that very handy mythbuntu-lircrc-generator script, that should generate a "sane" .lircrc file for all programs used by mythtv.

When running it it creates the .lircrc files in my home, but those are empty!

I have a lircd.conf in /etc/lirc. I had to train it for myself, because my remote controll wasn't published so far.

mythbuntu-lircrc-generator gives no output.

I'd appreciate some help - I don't want to create the lircrc for all programs by hand.

Greetings from Germany!

---

### Post by foxbuntu on 2008-03-25
One thing to note: m-l-g only knows english.

so in your Lircd.conf make sure all the buttons have english and sane names (i.e Play, Stop, FFW, ect) The only reason you would get empty output is if it is not matching any terms

---

### Post by theonlyandy on 2008-03-25
Hm. Thanks for the answer so far.

I only have english names there, but for example "ffw" is named "fwd" in my file.

Is there any documentation how to name the buttons so that m-l-g is able to generate?

---

### Post by foxbuntu on 2008-03-25
Is is no real documentation on it, I wrote the dictionary it uses though, what you can do is use one of (any is ok) the lirc supported remotes as a naming example (/usr/share/lirc/remotes) and make sure your lircd.conf is formated exatly as one of those are (I suggest using the Windows MCE Remotes as examples, they are the best supported remotes)

---

### Post by theonlyandy on 2008-03-25
Ok, thanks a lot.

I'll try to do that...

Greetings.

---

