---
title: "Playing content from Windows machine on Mythbuntu machine"
date: 2008-03-22
forum: Mythbuntu
---

### Post by Superorb on 2008-03-22
I am trying to play content from a Windows PC on a Mythbuntu HTPC box. How can I go about doing that?

---

### Post by freymann on 2008-03-22
> **Superorb said:**
> I am trying to play content from a Windows PC on a Mythbuntu HTPC box. How can I go about doing that?

 I think you'd have to copy the files from the Windoze machine to the Mythbuntu machine.

 From that point, there are a few ways to go from MythBuntu to Windoze... like simple file shares, maybe the uPNP device?

---

### Post by Superorb on 2008-03-22
The XP box has all my movies, music, and pictures. I'd like to view them on my Mythbuntu HTPC box in the other room with a small HD. I've been banging my head the past few hours trying to connect to the XP shares, but nothing will work. I've bene usung Ubuntu for over a year, but XFCE is giving me the hardest time. I know tons of people acess their media collection on a XP box FROM a mythbuntu box, but I can't figure out how to do it.

Ideas?

---

### Post by freymann on 2008-03-22
> **Superorb said:**
> The XP box has all my movies, music, and pictures. I'd like to view them on my Mythbuntu HTPC box in the other room with a small HD.


 You would have to share your media folders on the XP box. I assume you know how to do this? At the very minimum, right click the folder and click Sharing and just open it up. Whatever share name you use, don't use spaces!

 Then on the MythBuntu box "mount" those shares using a samba client. This is a lot easier to do with the Ubuntu desktop (Places > Connect to Server). I'm not all that familiar with the XFCE desktop so I'm not sure what you'd do.

 Maybe some magic with mount_smbfs ?

 Perhaps somebody else will chime in with a few tips. 

 I would just search the forums for info on accessing windoze shares from ubuntu. It's a common question and I'm sure there are dozens of answers.

 Your next issue would be getting your media shares into MythBuntu. This is easier if you don't have any local files on the MythBuntu box, as you would just point it to the XP box. Otherwise, I think you'd have to symlink the Xp content into the directories MythBuntu is looking in.

 Remember that MythBuntu lets you specify an individual path to your music, to your photos, and to your movies. Make them point to however you have mapped into the Xp box and you're all set.

---

### Post by Superorb on 2008-03-22
Yeah, I'm used to Ubuntu, but xfce is just missing so much stuff that Ubuntu does. I found how to add the share, I just can't find an easy was to "reconnect at login" like XP has.

---

### Post by freymann on 2008-03-22
> **Superorb said:**
> Yeah, I'm used to Ubuntu, but xfce is just missing so much stuff that Ubuntu does. I found how to add the share, I just can't find an easy was to "reconnect at login" like XP has.

 You can still use the Synaptic Package Manager to add things you need ;-)

 To reconnect at login, you'll need to play with /etc/fstab

 Depending what you did to add the share, most likely very similar commands would be used in /etc/fstab.

 Make a backup of fstab first.

 Editing will require 'sudo' of course.

 Again, the forums are full of samples on how to do this. It's easier if your XP box has a static IP as you can use the IP in the command, but if not, you'll have make sure you're using the same workgroup name on both machines and then you'd map to the Xp box by workgroup and machine name.

 You've made great progress so far, you should likely be fine with that last step!

---

### Post by prosonik on 2008-03-23
Hi there,

If you don't want to ediit the fstab manually or.  If you dont want to switch into gnome, you can install  pyNeighborhood. run it with gksu and iit seems to do an okay job. It does not write the fstab though., so it loks like the moiunts are only per session. 

Personally, I pefer WEBMIN. I think every mythbox should have it installed by default. It allows you to do all sorts of admin stuff from a web browser, and it has a great fstab editor. I personally use it for setting up any nfs, cifs or samba shares.

you can apt-get it, but i think it may be an old version. you can actually just update it to a recent version right inside the program, or just grab the latest and greatest from the webmin website [http://www.webmin.com/download.html](http://www.webmin.com/download.html)

here is an older article, but it should give you a good idea 
[http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)

prosonik

---

### Post by Superorb on 2008-03-23
I use webmin at work, I totally forgot about that. I'll give it a shot.

Thanks for the help everyone :)

---

