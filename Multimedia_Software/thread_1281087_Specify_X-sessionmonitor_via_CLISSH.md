---
title: "Specify X-session/monitor via CLI/SSH"
date: 2009-10-02
forum: Multimedia Software
---

### Post by JesusH8sMe on 2009-10-02
I have been trying to find the specific syntax but it could be I don't know the search terms I should be using. I have a dual monitor environment using gnome and nvidia drivers under Ubuntu 8.04 and they are each a separate X session. I do this because one is a monitor and the other is a projector in my living room for movies and such, I don't want anything to span both screens. I use this as a media server of sorts and can access it via my phone and laptop via SSH to manage most things, but this has stumped me. What I am trying to do is load different applications via SSH and be able to specify which X session/monitor it would load on. I could use some help identifying what controls this behavior, even if you can point me in the right direction to where I can read up on this that would be great. 

I'd be glad to post any configuration files you may need to help answer this, but I didn't think any would be relevant to the question. 

Thanks in advance for anything you can provide.

tl;dr - do you know how to port to monitor 1 or monitor 2 via CLI?

---

### Post by Tootoot222 on 2009-10-14
export the display you wish to use:

```
export DISPLAY=:0; gedit
```

you'll probably need 0:0 or 0:1, but :1 might work as well (can't say for sure, as i don't have a dual monitor)

---

### Post by JesusH8sMe on 2009-10-16
> **Tootoot222 said:**
> export the display you wish to use:

```
export DISPLAY=:0; gedit
```

you'll probably need 0:0 or 0:1, but :1 might work as well (can't say for sure, as i don't have a dual monitor)

Thanks! That specific syntax isn't working for me but this helps me a lot with my search terms. Much appreciated.

---

