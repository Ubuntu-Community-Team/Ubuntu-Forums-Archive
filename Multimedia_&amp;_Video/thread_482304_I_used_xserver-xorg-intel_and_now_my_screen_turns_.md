---
title: "I used xserver-xorg-intel and now my screen turns off on login!"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by adamdawkins on 2007-06-23
Hi,

So I've been trying to get my 1440x900 resolution screen to work for a while, and I saw something that said install xserver-xorg-intel. I did, and when my machine restarted I got a beautiful widescreen login screen. I log in, I get the ubuntu 'logging in' sound, and then my monitor auto powers off and says there is no signal input!

Any thoughts? - I've checked out my xorg.conf and there doesn't seem to be any problems there - I find it odd that it all works until login.

at the moment I've had to resort back to using my laptop, because I can only log-in to the text-console.

Please help!

Thanks,

Adam

---

### Post by reimmer on 2007-06-23
Hey, I'm having the same problem too. I'm not too familiar with Linux, so can u tell me exactly what command u type? I'll try the same..pls..

---

### Post by adamdawkins on 2007-06-23
> **reimmer said:**
> Hey, I'm having the same problem too. I'm not too familiar with Linux, so can u tell me exactly what command u type? I'll try the same..pls..

I'd love to help, but  I can't, because I've only had Linux a few days. We'll have to wait for someone with experience to come along I suppose! it's a bit annoying though, I thought I'd cracked it when my login screen went widescreen - evidently not :(

---

### Post by reimmer on 2007-06-24
> and I saw something that said install xserver-xorg-intel. I did

I just want to know what command u used to install  xserver-xorg-intel. Thanks.

---

### Post by NilsE on 2007-06-24
I think what he is saying he installed was

```
xserver-xorg-video-intel
```
which is in package manager and when selected it will replace the old i810 driver.

To the OP problem:

When you get to the text screen run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This should rebuild your xorg.conf to the new driver when you select intel at it's prompt

---

### Post by adamdawkins on 2007-06-24
I tried to reconfigure using dpkg reconfigure the other day and it didn't help. Now when I get to the login screen, Ctrl+Alt+F1 doesn't even take me to the text screen so I'm pretty screwed at the moment. I don't think it's the driver, because I have intel as the driver now anyway, the screen says "input out of range" when I login, so I think it's the refresh rate. Any more thoughts?

Thanks.

---

### Post by Gremlinzzz on 2007-06-24
Was it sudo apt-get install xserver-xorg-video-intel
Thats the command from the guide works for my computer which monitor is 1440 x 900 but in the guide it says doesn't work for everone.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by adamdawkins on 2007-06-25
All,

Thank you for your help. After a lot of tinkering with the X-config and so on (including dpkg reconfigure which was very helpful) I decided to create a new user - when I logged in as this user it all worked fine, so it must have been my previous tinkering with xorg.conf that screwed it up - I don't fully think that's it as I don't think xorg is different for each user, but either way, something was up with that account. Unforunately I'm only running at 16-bit colour at the moment thought but don't have the guts to spend another two evenings fixing it again.

Anyway, if all else fails and you have this problem, create a new user (either get in as root and do it or run:

```
sudo adduser USERNAME
```

in the command line).

If you do that, don't forget to do 

```
sudo adduser USERNAME admin 
```

afterwards which will add the user to the admin group if it's your only log-in!

Thanks again,

Adam

---

