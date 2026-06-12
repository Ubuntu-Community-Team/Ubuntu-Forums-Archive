---
title: "problem to connect camera by firewire"
date: 2006-01-05
forum: Multimedia &amp; Video
---

### Post by natxopinedo on 2006-01-05
hi, I have a problem with my camera ( panasonic nv-gs75) to connect by firewire

I had  read  lot's  of posts

In this moment I looked this:

the original  permissions was 
crw-rw----  1 root disk 171, 0 2006-01-05 15:34 /dev/raw1394

i changed this with chmod 777

I had loaded this modules:

video1394              18380  0
ohci1394               30644  1 video1394
raw1394   
ieee1394 909364video1394,ohci1394,raw1394,sbp2

and  turn on the camera by firewire  ,

then load kino and It can't capture

dvgrab no recognize the camera ,gscanbus too  
and   don't find /dev/sd??

I don't know whats worng with this , 
If somebady knows something about this please post it.

thank you

---

### Post by carlos.gil on 2006-01-05
I had a similar problem. All you have to do is to join the "disk" and "video" groups.
1.In your desktop  go to System>Administration>Users and Groups 
2.Write your password 
3.Go to the group tab and check the box where says show al grups and users
4.Search for the disk group edit it's properties and join the group. Do the same with the video group (It's probable that you are already a member of this group)
5. Finally, just reboot and you should be able to use it

Hope it works, it worked for me :)

Carlos Gil

---

### Post by RagonichaFulva on 2008-02-19
But can this model of camera work with Firewire? I read the manual and it doesn't say so...

---

### Post by mateuszbaranski on 2008-02-20
> **carlos.gil said:**
> I had a similar problem. All you have to do is to join the "disk" and "video" groups.


It works for me fine! THX.
Though I couldn't see disk and video groups -were hidden in gui.

It was easier for me  to use terminal and write:

```
sudo adduser <myloginname> disk
sudo adduser <myloginname> video

```

Make sure to re-login in order the changes take effect.

---

