---
title: "MythTv script...load at startup???"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by Rictus on 2007-04-21
Hi, I'm trying to make a script to make Mythtv to load at the start of my server. But when I try to save the script it says:
Error writing /user/local/bin/mythtv.sh: No such file or directory

I'm using this guide here.

Create a script, /usr/local/bin/mythtv.sh that will be spawned when you login to your MythTV session. Place these contents into that file: 

gnome-screensaver
mythfrontend&
exec openbox
If you are running lirc and using irexec for any of your key detection, you probably also want to add this section. It will be sure that if X is ever restarted, irexec doesn't spawn multiple instances 

killall irexec
irexec -d
If you are running an nvidia graphics card, you should add: 

nvidia-settings -l
If you are planning on running the myth transcoding daemon for ripping dvds, you will want to add: 

mtd -d
If you come up with anything else for your custom startup script, /usr/local/bin/mythtv.sh will be the place to add it. 

Thanks,
Rick

---

### Post by Titus A Duxass on 2007-04-21
Did you create this file "mythtv.sh" in the directory  /user/local/bin/ ? 
This is described in the how-to.

---

### Post by Rictus on 2007-04-21
I'm sure I'm not doing it right. It doesn't say how to create it. I just used sudo nano like I did on the previous file. But this says create a script. Not sure if there is a difference between creating a file and creating a script. Maybe the file I made before already had a directory (/usr/share/xsessions/mythtv.desktop) so thats why it worked.
So how do I create a directory if that is what the problem is? mkdir didn't seem to work earlier but maybe I was doing something wrong then too.
Thanks.

---

### Post by Titus A Duxass on 2007-04-21
Creating the Script and creating the file are one in the same thing.

Simply do "sudo nano /user/local/bin/mythtv.sh" and paste:

gnome-screensaver
mythfrontend&
exec openbox

Then exit and save with Ctrl+x, hit "Y" to save changes.

Then don't forget to change the permissions of "mythtv.sh"

---

### Post by Rictus on 2007-04-21
Thanks, figured it out. Typo...do you see it?

It's /usr not /user

Thanks, if you didn't tell me to do exactly what I was already doing then I wouldn't have know I was doing it the correct way. Leading me to look very carefully at everything. If I was doing it like you said then it must have been something stupid. haha

Rick

Awe I spilled the beans.

---

### Post by Titus A Duxass on 2007-04-21
Oops, didn't see that!

Still glad you've fixed the problem.

How has the rest of the install gone?

---

### Post by Rictus on 2007-04-21
Still having video card problems (ATI 9800PRO) and it appears MythTV isn't seeing the backend or something. I gotta get some sleep and I'll try later.
But thanks.

---

### Post by superm1 on 2007-04-21
Rictus, before you get too involved doing this all with Edgy, have you considered using Feisty instead?  Its a lot more pain free and requires less command line interaction.

---

### Post by Rictus on 2007-04-22
Whoa, the man himself if I'm not mistaken. I been reading your guide for 3 days now lol.
I read so many people looking for help for Feisty I thought it was loaded with problems, but maybe just because everyone is useing it.
 I'm gonna do this. I've got it messed up now anyway. I changed the resolution and now myth's homepage is black. 
So it's time to cut my losses and start anew.
Thanks for the feedback.

---

### Post by Titus A Duxass on 2007-04-22
Rictus,
I've just done a new build using Feisty and SuperM1's how-to, it's almost pain free!

---

### Post by Rictus on 2007-04-22
Just to let you guys know Fiesty was much easier. So far looks like everthing is working.
Only thing is the remote doesn't seem to work. Oh well off to find out about that. I'm hopeing it's the batteries.

---

### Post by superm1 on 2007-04-22
I'm assuming you set up lirc and all?  Or is this a remote that is native to linux?

---

### Post by Rictus on 2007-04-23
It's a built in remote with my Hauppauge TV-PVR 250. I've managed to get it set up but some of the buttons were not testing right. i.e. when I push up it would say radio etc., but some were ok.
I found a lircd.conf file that was listed as 2/350 remote, and hand edited my lircd.conf file to make it right. Then ran the test again but it was the same. I haven't actually tried it in myth yet and I haven't had a chance to try it again since then. I'm hopeing when I start it back up it will work. 
I'll let you know. 
Rick.

---

