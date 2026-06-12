---
title: "Grsync error with Desktop to Laptop linkup."
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-12-03
Hi.
I used to be able to use Grsync between my Desktop running Ubuntu 9.04 and my Laptop running Linux Mint 7. Then I upgraded Ubuntu to 9.10. Everything still worked perfectly with Grsync. I upgraded Linux Mint to version 8.

Now when I try Grsync I get this message:

```
*** Launching RSYNC command (simulation mode):
rsync -r -n -t -v --progress /home/rytron/ 192.168.1.11:/home/rytron/

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!

Someone could be eavesdropping on you right now (man-in-the-middle attack)!

It is also possible that the RSA host key has just been changed.

The fingerprint for the RSA key sent by the remote host is
[COLOR="Gray"]NUMBERS AND LETTERS AKIN TO A MAC ADDRESS WERE HERE[/COLOR]

Please contact your system administrator.

Add correct host key in /home/rytron/.ssh/known_hosts to get rid of this message.

Offending key in /home/rytron/.ssh/known_hosts:1

RSA host key for 192.168.1.11 has changed and you have requested strict checking.

Host key verification failed.

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(600) [sender=3.0.6]
```

Note: Both machines can ping each other.
Note: I unchecked the enabled button in Gufw on both machines.
Note: [COLOR="DarkRed"]/home/rytron/[/COLOR] refers to my [COLOR="DarkRed"]Desktop PC[/COLOR] and [COLOR="DarkSlateGray"]192.168.1.11:/home/rytron/[/COLOR] refers to my [COLOR="DarkSlateGray"]Laptop PC[/COLOR].
Note: I tried Grsync between my Ubuntu PC and external HDD. Everything works perfect on that side.

---

### Post by nothingspecial on 2009-12-04
There is a very easy way of fixing this aslong as you are just using ssh on your home network.

On the client machine

```
rm ~/.ssh/known_hosts
```

if you are using ssh to access your machine over the internet this is not safe, post back if so

---

### Post by Rytron on 2009-12-04
> **nothingspecial said:**
> There is a very easy way of fixing this aslong as you are just using ssh on your home network.

On the client machine

```
rm ~/,ssh/known_hosts
```

if you are using ssh to access your machine over the internet this is not safe, post back if so

Hi nothingspecial. 

I hope you didn't mind the pm. I am only using Grsync between my two computers and the internet is not involved.

Just a little correction to your code:
rm ~/[COLOR="Red"]**.**[/COLOR]ssh/known_hosts

I greatly appreciate your help.

By the way, do you know why I didn't get this message before in previous Ubuntu / Linux Mint releases?

---

### Post by nothingspecial on 2009-12-04
Ha,ha.

I just woke up and was checking my emails, typing in the dark with no glasses on.

It`s because you`ve installed a different linux and ssh doesn`t recognize your machine anymore, Put simply.

 Read about ssh keys for more info.

---

### Post by Rytron on 2009-12-04
Okay. Just another question. Do I rm ~/.ssh/known_hosts from my Desktop PC? Keeping in mind its the one I run Rsync from.

---

### Post by nothingspecial on 2009-12-04
The machine you are sshing from, not to, although it doesn`t really matter if you delete both.

This is not good practice btw. It is just easy, and no problem if you are just using ssh within a home network.

If you ever decide to use ssh to connect to your pc from outside, I suggest you take note of public and private keys.

In this case though, it doesn`t really matter.

This is going to come up every time you do a fresh install.

---

### Post by Rytron on 2009-12-04
Great, I will note all of this for future reference.

Just one more thing. If I remove the .ssh/known_hosts file, does this make my computer only vulnerable if I try to remotely connect to it? I mean is my PC still perfectly safe when I surf the internet from it, use Pidgin, Liferea, etc.

Edit: Your solution works like a charm, nothingspecial. Excellent.

---

