---
title: "kopete webcam is green!"
date: 2006-02-07
forum: Multimedia &amp; Video
---

### Post by joey111 on 2006-02-07
kopete 0.11.1. using kde 3.5.1;
sitecom easycam VP-003
Device SN9C10x PC camera
USB
hi , anybody has an idea what i could do :
my cam works,:mrgreen:  but it gives completely green pics;so ican see myself but i  green..lol. the built -in configuration tools (saturation etc.)dont help  .
i know its difficult to get appropriate drivers for webcam i like this, i havent found them yet; 
anybody any idea (i down want to switch to win evrytime i wanna videochat)
thx:mrgreen:

---

### Post by fannymites on 2006-02-07
Not sure if you've seen this thread or not but someone a few posts down mentions their SN9C10x cam is working after following the guide.
[http://www.ubuntuforums.org/showthread.php?t=75284&highlight=webcam](http://www.ubuntuforums.org/showthread.php?t=75284&highlight=webcam)

[EDIT]  I just remembered I have an SN9C102 cam and I plugged it in and tried it with Kopete and also got the green screen.  The thread I linked to didn't work for me so let me know if you figure it out.

---

### Post by joey111 on 2006-02-07
which prog do u use to videochat ( if u haven't noticed the green screen till now)
->maybe easier to switch the application for me, but 'll try the how-to above

---

### Post by fannymites on 2006-02-07
I have 2 webcams, one is an sn9c102 and I can't remember the other off-hand.
Both work perfectly on aMSN, which is what I normally use but neither will work kopete.  The sn9c102 gives a green screen and the other gives a sort of warped zig-zaggy pattern, a bit like an old telly with loads of interference.

---

### Post by joey111 on 2006-02-07
do u know how i can install amsn through synaptic? which repository?
i never get it installed right manually (i tried couple of times)

---

### Post by joey111 on 2006-02-07
hmmm its even worse now, the green is brighter and ic cannot recognize my face any:evil: :evil: more;

desperate..

---

### Post by fannymites on 2006-02-07
You may find aMSN in the backports repos, have a look in the backports forum section, I installed manually against tk/tcl cvs so I'm not sure if a breezy version has webcam support.
I'm not getting anywhere with kopete either though I have read somewhere while searching that kopete has problems with a lot of video4linux2 cams.
I'm getting the same problem on suse as well so it's not a problem with the kubuntu/ubuntu version.

---

### Post by joey111 on 2006-02-11
i tried now amsn (0.95 and 0.96b) with a new webcam that actually works with linux (camorama), (kopete is difficult again) and i can see the other guy I am talkin too but it says to me bidirectional webcam support is not possible yet.so my question is can u really talk to ur friend like in windows with msn (u and ur partner talking via video at the same time?
i dont get it it never works with linux to get a real video conversation.
any idea?
thanx guys

---

### Post by tioneb on 2006-02-15
to solve the green problem in kopete change the palette of the ov511 module
unplug the cam
```
sudo modprobe -r ov511
```
```
sudo modprobe ov511 force-palette=13
```
```
tail /var/log/syslog
```
you should see the ov511 loaded

---

### Post by fannymites on 2006-02-15
Didn't work for me.  It's now gone from a light green but some picture still visible to vivid green and nothing else visible at all.

---

### Post by tioneb on 2006-03-08
by the way before adding the new ov module you must remove the previous ov511

---

### Post by tioneb on 2006-03-17
@joey111
yep it works for me with a f** jpeg webcam with ov519_decomp and aMSN
@fannymites
try other palette..

---

### Post by fannymites on 2006-03-17
Changing the pallette takes away the green but it's still too distorted and full of wavy lines to see anything.
It's always worked on aMSN.

---

### Post by umuro on 2007-05-08
It worked for me. I have Hercules WebCam Classic. using ov51x-jpeg

So I modified the instructions:
```

sudo modprobe -r ov51x-jpeg
sudo modprobe ov51x-jpeg force-palette=13 
tail /var/log/syslog

```

Now I am able to send and recieve perfect video with msn users on Kopete. :)

---

### Post by umuro on 2007-05-10
However, I am having to do that after every reboot. How to fix that?

---

### Post by j800r on 2008-06-30
i tried the method, and it worked a little. i think the green tint to it now is just because of low light conditions. i shall check again in the daytime

---

