---
title: "MythTV and lirc permissions"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by pico2215 on 2007-02-20
Hey all

I'm fairly new to Ubuntu, and I just got MythTV setup with my Hauppauge PVR-150. MythTV works like a charm, but I'm having some issues with my Hauppauge remote. I read through the setup (see below), but it still won't work under my main username. The part I'm confused about is that the remote works just fine under the mythtv user. 

So I'm assuming that this is just a permissions problem. I've tried chown on ~mythtv/.mythtv/lircrc , but this doesn't seem to work. I've included the page I used to lirc setup so you can see what I've done. Thanks in advance.


[http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft](http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft)

---

### Post by wjston on 2007-02-20
> **pico2215 said:**
> it still won't work under my main username. The part I'm confused about is that the remote works just fine under the mythtv user. 

My setup works the same as yours. Why would you worry about trying to get the remote working under your user name if it works under the mythtv user? I have my system booting into the mythtv account and automatically loading mythtv.

---

### Post by pico2215 on 2007-02-20
I don't use this PC for only mythtv. I've got everything else set up under my main username, which is the user I boot into. The mythtv user was used just to set up mythtv. 

I know it would be possible to set everything up under the mythtv account, but that seems a bit pointless. What would someone do with a multi-user PC in that case?

---

### Post by wjston on 2007-02-21
> **pico2215 said:**
> I don't use this PC for only mythtv. I've got everything else set up under my main username, which is the user I boot into. The mythtv user was used just to set up mythtv. 

I know it would be possible to set everything up under the mythtv account, but that seems a bit pointless. What would someone do with a multi-user PC in that case?

I see your point. Did you setup a lirc file under your user name and save it it your home folder? If so, try linking it to MythTV. I think the command is **ln -s ~/.mythtv/lircrc ~/.lircrc**. Make sure you give yourself permissions to read/write/execute the file. Hope this helps.

---

### Post by barney_1 on 2007-02-21
I actually fixed my problem with this in a different way.  I linked the lircrc in under my username to the one under the mythtv username:
```
cd ~/.mythtv
sudo mv lircrc lircrc.backup
sudo ln /home/mythtv/.mythtv/lircrc lircrc
```

---

### Post by wjston on 2007-02-21
> **barney_1 said:**
> I actually fixed my problem with this in a different way.  I linked the lircrc in under my username to the one under the mythtv username:
```
cd ~/.mythtv
sudo mv lircrc lircrc.backup
sudo ln /home/mythtv/.mythtv/lircrc lircrc
```

Does your remote still work when you log in as mythtv user? If so, thanks for the tip.

---

### Post by pico2215 on 2007-02-21
Thanks for all the feedback. :) 

I did get mine to work. I looked in the .mythtv directories of each user, and saw that the mythtv user had a lircrc file and my main user only had a .lircrc file. I'll have to go back through the readme I used to see if I mistyped some command or if this step is simply not included. But just copying the lircrc file from one user to the other worked just fine.

Again, thanks for all the help.

---

