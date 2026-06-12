---
title: "Couple of quick &quot;how to&quot; questions"
date: 2009-10-20
forum: Mythbuntu
---

### Post by badger_fruit on 2009-10-20
Hey all
Previously I have been using Ubuntu9.04 with the added-on Mythbuntu but something went wrong with my / partition/disk and I've had to re-install.  I decided, as this was built to be a pure Myth-TV Backend server, to use Mythbuntu (the full distro as opposed to UB+MBU).

Further to this, I have a few, hopefully painless, questions I hope someone can help with:-

1. Although I selected VNC in the setup and can connect OK to it; what is the default password?  I'd also like to know how to change this please.

2. Mythweb asks for a username and password when I try to access it; I discovered it's the same as the username and password I created in the OS setup so that's fine but I want to disable it, it's on a home LAN which is secured from access via the web so authentication isn't needed.  Now, I've used apache before and familiar with the concepts of .htaccess but I can't seem to find the config files I would need to change to disable the logon request.  Anyone know where it is please?

I think that's all for now, cheers guys and happy computing!

---

### Post by elgordo123 on 2009-10-20
1. To change the vnc password, open a terminal and type vncpasswd 

2. You can disable mythweb security in the mythbuntu control center in the applications/plugins area.  This is not recommended, as many people "think" their boxes are secure when they are not.

---

### Post by badger_fruit on 2009-10-20
> **elgordo123 said:**
> 1. To change the vnc password, open a terminal and type vncpasswd 

Ah! I knew it would be something as easy as that!!

> **elgordo123 said:**
> 2. You can disable mythweb security in the mythbuntu control center in the applications/plugins area. This is not recommended, as many people "think" their boxes are secure when they are not.

Fortunately, I am not "many people" ;)  My besides, little old Mythbox is nice and safe - well away from my DMZ! Oh, finally, if "they" ever did hack it, they'd discover my secret "How clean is your house" collection and that's about it ;)

*(Damn, well, that's that secret out lol!)*
Many thanks for the hints though, much appreciated!

---

### Post by SiHa on 2009-10-21
> **badger_fruit said:**
>  Oh, finally, if "they" ever did hack it, they'd discover my secret "How clean is your house" collection and that's about it ;)


It's the fluffy rubber gloves that does it for me.

---

