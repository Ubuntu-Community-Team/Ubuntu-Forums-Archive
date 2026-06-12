---
title: "[SOLVED] How do I uninstall realplayer 11?"
date: 2008-09-08
forum: Multimedia Software
---

### Post by kierpaul on 2008-09-08
Hi everyone, I am running Hardy Heron and I installed Real Player 11 just to try it out. I cannot get it removed now. I followed these directions from this website:  
[http://onlyubuntu.blogspot.com/2008/05/how-to-install-realplayer-on-ubuntu.html](http://onlyubuntu.blogspot.com/2008/05/how-to-install-realplayer-on-ubuntu.html)

This is what I have for a location: locate realplay
/usr/share/icons/HighContrastLargePrintInverse/48x48/apps/realplay.png

I also tried to dpkg it and this did not work: dpkg -r realplayer
dpkg: requested operation requires superuser privilege

I do not understand this as I am the administrator of this OS. Any help would be greatly appreciated and thank you ahead of time. I will check this post later on!

---

### Post by rainwalker on 2008-09-08
To invoke admin privileges with commands, you have to use the "sudo" prefix, so:
```
sudo dpkg -r realplayer
```
would invoke admin rights, and ask for your password. Type it in (the characters won't show up, it's a security measure), and it should work.
Make sure you know exactly what you're doing before you invoke sudo, though

---

### Post by kierpaul on 2008-09-09
Rainwalker,


Thanks for your reply...I forgot to put sudo in front of the command. Sometimes I am not with it. Anyways, I did this and this is my results:

 sudo dpkg -r realplayer
[sudo] password for kierpaul: 
dpkg - warning: ignoring request to remove realplayer which isn't installed.
kierpaul@kierpaul-desktop:~$ 

This is weird, considering Realplayer 11 is in my applications menu under sound and video and I can open it up? Any suggestions?

---

### Post by rainwalker on 2008-09-09
How did you install it?

Also, please don't send me private messages about posts, I get email alerts of new ones :)

---

### Post by kierpaul on 2008-09-09
Rainwalker,

I installed realplayer from the terminal. I did exactly like this with the results I have pasted...Sorry about personal message: 

wget [http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin)

chmod a+x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin

Extracting files for Helix installation........................

Welcome to the RealPlayer (11.0.0.4028) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...

You have selected the following RealPlayer configuration:

Destination: /opt/real/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]:

Copying RealPlayer files...Path setup done.
Succeeded.
installing application icons resource...
installing document icons resource...
....Succeeded.
Configuring Mozilla...
Installing .mo locale files...
Setting selinux context...
Succeeded.

RealPlayer installation is complete.
Cleaning up installation files...
Done.

---

### Post by rainwalker on 2008-09-09
No worries :)

Hm...it looks like you're just running a .bin rather than installing anything, but I'm not sure. You could try manually deleting that "/opt/real/RealPlayer" that it installed to, but I don't know if that's the proper/clean way to do it.

---

### Post by kierpaul on 2008-09-09
How would I go about removing "/opt/real/RealPlayer" ?   I am a pretty new user, but I am learning fast with a lot of the small problems I am encountering. Thank you ahead of time!

---

### Post by kierpaul on 2008-09-11
This is still perplexing me. Any suggestions anyone???

---

### Post by kierpaul on 2008-09-11
Thanks everyone. I had to do some commands from the terminal window and I will not repeat them here because they could do damage if you do not know what you are doing. I was walked through it.

---

