---
title: "Help me understand wordlists (aircrack)"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by thehandtruck on 2009-10-08
My goal was to learn enough about to networking/linux/aircrack-ng to break into my own wireless network and use it. After a few weeks I've finally been able to get to the point in aircrack where I've captured the 4-way handshake but I can't figure out how to crack it. 

Now, the router's password is badtimes12 which of course isn't in the sample 'password.lst' that comes with aircrack. When I edit password.lst and added 'badtimes12' it "cracked" the password and says "key found" so I know my procedures/commands are correct.

What I don't understand is how can you get a wordlist big enough to have not only every word, but every combination of words and numbers. Can anyone explain how wordlists work or how to get mine to work?

I tried downloading wordlists that had every word in the dictionary in them. They included 'bad' and 'times' seperately but even when I added 'badtimes' it didn't work, it needs the *exact* password ("badtimes12") to work. How is it possible to even have a wordlist big enough to crack simple passwords like 'badtimes12'?

What am I missing here?

---

### Post by scorp123 on 2009-10-09
> **thehandtruck said:**
>  What I don't understand is how can you get a wordlist big enough You add those words to the list. Done :D

> **thehandtruck said:**
>  but every combination of words and numbers.  More words = bigger list.

> **thehandtruck said:**
> What am I missing here? Wordlists can get as big as 8 GB and beyond. I have such files here. There are even bigger ones that are available from commercial providers.

Another method would be to have a program auto-generate words and wordlists and then pipe the output of the program to aircrack ...

I have once seen a real pro hacker do this (he was paid by us --his victims-- to do conduct a real-life security audit ...). His program was written like a worm and it would fetch words it wanted to try from the Internet. The nice thing being that he could adapt his program to try words in other languages. So when he tried to crack our password he realised that one of our guys was of Russian origin ... So he guessed: Could the password be a Russian word? Or a combination of Russian words? So he told his program to go and scan all *.ru web pages for words, and he used those collected words against our password ....

And it sure worked. The password was Russian, yes, but that alone didn't help. It was still too weak.

That was quite a wake-up call.

Since then I use **"pwgen"** in paranoid-mode to generate passwords for me.

```
pwgen -s -y 32
```

---

