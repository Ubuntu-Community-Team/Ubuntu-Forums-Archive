---
title: "NFS for beginners"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by RRahl on 2010-06-29
I can successfully work with NFS in Ubuntu 9 but 10 seems to have me in a fluster.
I want to share folders with my windows boxes,  however nfs isnt in the init.d directory and I cannot find it anywhere.  I have found mention that people use natilus.
Can someone explain to me what happened to nfs in 10?  Or how I can go about sharing folders?  Everything seems all shifted around in 10.

---

### Post by RRahl on 2010-06-29
No one? Maybe I am being impatient but I have started 3 threads over the past couple weeks trying to do file sharing in Ubuntu...is it that the 64 bit threads are dead or are there just that few people in this community?

---

### Post by jonobr on 2010-06-29
Hello

Given your lack of responses :-) Ill stick my neck out,
I was wondering given what your doing, would you try samba instead?
[Here]("http://wiki.linux-nfs.org/wiki/index.php/Comparison_of_NFS_vs._others") is a good comparison guide between CIFS (samba) and others.

---

### Post by RRahl on 2010-06-29
Thanks for sticking your neck out!
I have been down the CIFS path,  it doesnt work on my network, for some reason the encryption level just isnt right. I force NTLMv2 and I know Samba supports it but after 2 weeks I was unable to get it going.
See this thread for more:
[http://ubuntuforums.org/showthread.php?t=1510536](http://ubuntuforums.org/showthread.php?t=1510536)

So I tried iSCSI in hopes of avoiding the nastiness of CIFS I still have hope for this but see this thread:
[http://ubuntuforums.org/showthread.php?t=1514751](http://ubuntuforums.org/showthread.php?t=1514751)

Then I did NFS which worked great on Ubuntu 9.  SO I wanted to work with fuse 2.8 which I could not get installed properly on 9 so I went to 10 where 2.8 is native.  
However, everything is gone in this release so I don't know what is involved in setting up NFS shares here and samba isn't working so I am a little stuck :)
However, NFS SHOULD work great, this is linux's native communication for network shares.  Samba is just kind of a guess so NFS should be more stable anyway...right?

---

### Post by jonobr on 2010-06-29
Man it sounds as if you have been through the wars

I was just looking in Synaptic (im running 10.4 desktop with some server applications)
and I saw in synaptic a while heap of nfs things (common packages , kernel server etc)
None of them are installed on mine, 
Im using the the main, multi and universe repos,

do you see these in synaptic, are they installed?

I ask this as a rhetorical question as you sound like you know your stuff

Cheers

---

### Post by RRahl on 2010-06-29
Complete linux noob here, treat me like an idiot because I am one ;) I don't even know what synaptic is!  But I will research it. Best way to learn is to bash your head up against a wall, half the fun of being a sys admin is coming across things you know nothing about!
I know my way around networks pretty well though.  I did cut my teeth on redhat and yellow dog back in the late 90s just haven't had much reason to use linux since. I take the vantage point that you use the right tool for the right job,  not really biased either way.

That being said,  I did not see the NFS service in the init.d folder nor did I see an exports file and "find -name nfs" pulled up nothing. So I assumed that a 64bit ubuntu 10 install must have something for sharing files,  perhaps I am just approaching things the wrong way.

---

