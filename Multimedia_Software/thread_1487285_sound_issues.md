---
title: "sound issues"
date: 2010-05-18
forum: Multimedia Software
---

### Post by linuxnoob40 on 2010-05-18
when i first boot up everything is fine but if i try to listen to any audio, be it streaming or otherwise, it works fine for a few minutes then i get a loud click and thats it. then its either dead silence or i get what sounds like a helicopter. now if i happen to be watching a movie, again be it streaming or off my hard drive, again a loud click then again either dead silence or the helicopter sound and the movie stops. now if i move it ahead a little the movie will play and then stop but the only way to fix it is to reboot. i upgraded from 9.10 to 10.04 this weekend and this is when the problems started it all worked fine before this. i have tried several fixes all have been futile. is this a bug in the new build that i will have to live with till its fixed or is it something that can be fixed?
i would pull my hair out but i don't have any left

also i don't know if its related but if i try to use do anything with skype it causes the break to happen as well

---

### Post by lidex on 2010-05-20
Try this. Using a Terminal="Applications->Accessories->Terminal"
```
sudo pulseaudio --kill
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by linuxnoob40 on 2010-05-20
this is what i get



>  sudo pulseaudio --kill
E: core-util.c: Home directory /home/steven not ours.
E: main.c: Failed to kill daemon: Permission denied


---

### Post by Rumpty on 2010-05-20
Is it possible the command that doesn't work stumbles on your "steven not ours" user name?

---

### Post by lidex on 2010-05-20
Using nautilus, right click on your user folder under /home and select 'properties'. On the 'Permissions' tab, at the top, who is the owner?

---

### Post by rao1984 on 2010-05-20
I too have ended in same error message..... I had installed Ubuntu 10.04 in a partition created through Windows 7... does this prevents from executing the command "sudo pulseausio --kill".
I am new to Ubuntu OS 
Thanks in advance

---

### Post by rao1984 on 2010-05-20
I cross checked in the permissions tab... its showing 2 names with a "-" character in between like "pramod-Pramod Rao" ,
I had 2 doubts here
1) when I start Ubuntu my username is shown only as "Pramod Rao"  
2) why does owner name given so much importance as we specify correct account password ??

sorry for my doubts,

thank you

---

### Post by Emmental on 2010-05-31
To restart pulseaudio, do not use sudo. You should just be able to do...

```
pulseaudio --kill
```

Also note that this doesn't just kill pulseaudio, it restarts it also.

Sorry I can't help any further with your actual problem, as this is about all I know regarding pulseaudio. :p

---

