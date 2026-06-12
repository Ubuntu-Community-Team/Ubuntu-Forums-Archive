---
title: "Problem with USB headphones"
date: 2011-06-17
forum: Multimedia Software
---

### Post by Gikoskos on 2011-06-17
I know it requires a process to connect properly USB headphones on UBUNTU
but i need some help.
I 've been searching a lot for this issue and all the solutions i've found
where only for older UBUNTU versions and they just caused more 
problems on the OS.
For example before i do some things the system recognized the USB headphones,
it just wasn't able to produce any sound.
Now when i click on Control Center-->Sound it just pops out the message:
''Waiting for sound system to respond''
I click 'ok' and that's it. Nothing.:(
I've searched older problems with USB headphones on this forum but all the solutions
were for the older UBUNTUs.
Anyone willing to provide help or instructions for my problem is welcome and
i thank on behalf all of you who respond on my problem:).

---

### Post by lidex on 2011-06-18
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by Gikoskos on 2011-06-18
> **lidex said:**
> Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```**Reboot**
* Ignore any 'No such file or directory' errors*
Thanks it worked!
You guys are awesome! I will definitely contribute in this project:P

---

