---
title: "How to resume SSH session after disconnecting?"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by Donny Bahama on 2010-03-07
I'm currently using putty on my laptop to control my headless server (both Ubuntu 8.04.) I'm running an rsync job that ran all night long and still going all day today so far. 

I need to restart my laptop, but if I do, I'll break the SSH connection. If I SSH back in, I won't see the same thing (rsync is showing me each file it's copying) that I'm seeing now. (At least I think that's true. Please correct me if I'm wrong.)

So I guess my questions are...

[LIST=1]
[*]Is there some way to restore my SSH session when reconnecting? (So I can resume seeing which file is being copied and - more importantly - when the rsync job (finally) finishes?
[*]If not, how else can I know when the rsync job finishes?
[/LIST]
Thanks for your time and consideration. :)

---

### Post by memilanuk on 2010-03-07
Try 'screen'

---

### Post by jfparis on 2010-03-07
There is nothing really you can do NOW to avoid killing the commands running within your ssh session. When you gonna restart the laptop they will be killed.

Now everything is not dark there are a few bright points

**First one**
Next time you might want to use "screen". When you start screen it creates a persistent session. you can then detach it from your tty and kill you ssh connection. When you reconnect, you can reattach to your screen with 

```
screen -r
```Screen is really easy to use but you really need to read the doc so 

```
man screen
```**Second one**
You are using rsync and rsync does incremental copies. So let's assume you kill it now to restart your laptop. When you gonna restart the command within "screen" or after reconnecting, it is not going to copy again the files that where already copied.

---

### Post by Donny Bahama on 2010-03-07
> **memilanuk said:**
> Try 'screen'Thanks! (I think...) I installed it and took a look at the man page. WOW. Learning to use screen looks like a pretty big project for a noob.

---

### Post by Donny Bahama on 2010-03-07
> **jfparis said:**
> There is nothing really you can do NOW to avoid killing the commands running within your ssh session. When you gonna restart the laptop they will be killed.

Now everything is not dark there are a few bright points

**First one**
Next time you might want to use "screen". When you start screen it creates a persistent session. you can then detach it from your tty and kill you ssh connection. When you reconnect, you can reattach to your screen with 

```
screen -r
```
Am I supposed to run screen from the server (which I'm controlling via SSH) or from my laptop/SSH client? I'm guessing from the server.

> **Second one**
You are using rsync and rsync does incremental copies. So let's assume you kill it now to restart your laptop. When you gonna restart the command within "screen" or after reconnecting, it is not going to copy again the files that where already copied.That's good to know. I'm puzzled by how long it's taking, though. It's been running for at least 12 hours and still hadn't finished rsyncing a 96GB directory. (And I still have another 300+ GB to sync after that!) Is that normal?! The two drives are both external USB 2.0, and when I ran rsync, I did ```
rsync -av sourcedir destdir
```

---

### Post by memilanuk on 2010-03-07
You log in via ssh to the server as per normal, then run 'screen' there.

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

[http://www.google.com/search?btnG=1&pws=0&q=screen+tutorial](http://www.google.com/search?btnG=1&pws=0&q=screen+tutorial)

Well worth the time to learn.  Sorry about being so terse before... I had a complete reply typed out, then my network connection dropped and I was too lazy to re-type it ;)

---

### Post by Donny Bahama on 2010-03-07
> **memilanuk said:**
> You log in via ssh to the server as per normal, then run 'screen' there.

[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

[http://www.google.com/search?btnG=1&pws=0&q=screen+tutorial](http://www.google.com/search?btnG=1&pws=0&q=screen+tutorial)

Well worth the time to learn.  Sorry about being so terse before... I had a complete reply typed out, then my network connection dropped and I was too lazy to re-type it ;)
Awesome. Thanks very much! :)

---

### Post by Donny Bahama on 2010-03-07
Well, I took the lazy (actually, I prefer to think of it as the "Let's see how intuitive this is") route...

I putty'd in, ran screen, did some stuff, closed putty, putty'd back in, and ran "screen -r".

It popped right back up where I had left it. AWESOME!!!

Thanks **very** much for this!

---

### Post by memilanuk on 2010-03-07
I used to have a shell acount @ Panix, that I accessed via dial-up (56k only on a *good* day) and I used screen set up with slrn in one window and mutt in another...  it was very nice having screen with an unreliable connection like that!  Nowadays its more of a convenience issue... though sometimes my wifi gets a little flaky at times :(

---

