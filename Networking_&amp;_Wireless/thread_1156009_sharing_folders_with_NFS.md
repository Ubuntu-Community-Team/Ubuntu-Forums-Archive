---
title: "sharing folders with NFS"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by graphicsxp on 2009-05-11
Hi,

What is the best way to share folders between two Linux machines ? (one is ubuntu, the other one is mandriva).

I've used the NFS wizard of my Mandriva machine to share folders on the network, but I was not able to see them on my Ubuntu machine until I actually mount them. I find this odd that I need to mount network folders manually... How would I know how to mount them if I was not the one who shared them !  I would expect the folders to appear automatically under Network, how can I do that ?

Also, is NFS the best way to share or could I use Samba ? (I've heard this only when sharing between Windows and Linux).

thanks !

---

### Post by coutts99 on 2009-05-11
You have to mount NFS shares to use them!

Perhaps zeroconf is what you are after?

[http://www.enterprisenetworkingplanet.com/netos/article.php/3618026]("http://www.enterprisenetworkingplanet.com/netos/article.php/3618026")

---

### Post by graphicsxp on 2009-05-11
Yes that's what I've done. But I think i'm still missing the point. Consider this :

User A decides to share /media/hd2 on the network

For User B to be able to access it, he needs to mount the NFS share, but how could he know that /media/hd2 is shared, since it's not visible until he mounts it ?

I;ll take a look at your link.

---

### Post by coutts99 on 2009-05-11
That's just how NFS works! It isn't automatic at all! :)

Try this link -:

[http://ubuntuforums.org/showthread.php?t=218630]("http://ubuntuforums.org/showthread.php?t=218630")

I've never used zeroconf ever, so not sure how it works

---

### Post by graphicsxp on 2009-05-11
Ok, in this case why is there a Network place in Ubuntu ? Could I see shared folders there, the same way as we can see shared folders in My Network Places in Windows ?

I understand it's not possible with NFS, but then what about Samba maybe ?

Basically I can't see what is the point of sharing if no one can see what you share until you tell them how to access it :)

---

### Post by coutts99 on 2009-05-11
In my network place (KDE4) I can see Network Services and Samba Shares, Samba Shares obviously goes off looking for Samba Shares, whereas Network Services goes off looking for Zeroconf stuff.

---

### Post by graphicsxp on 2009-05-11
Yes me too. Ok so I'll try to share using Samba. Is there a downside in using Samba instead of NFS when sharing between 2 linux boxes ?

---

### Post by coutts99 on 2009-05-11
No idea, possibly a little slower? But I don't know really :)

I might have a play with zeroconf when I get home tonight.

---

