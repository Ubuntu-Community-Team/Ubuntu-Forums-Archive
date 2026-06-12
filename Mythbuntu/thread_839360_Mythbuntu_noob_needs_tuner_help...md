---
title: "Mythbuntu noob needs tuner help.."
date: 2008-06-24
forum: Mythbuntu
---

### Post by bippy_b on 2008-06-24
Hi everyone,

I am switching from a self built myth box on Fedora to Mythbuntu. I tried out the Ubuntu Live CD and liked it so much that I figured it would be better for my myth box too.  Anyways... I had some install problems.. but after a couple of attempts, I figured out what to do... So I setup the tuners..  assigned the channel lineups...etc..  I scheduled a recording to test it out and it says that the tuners are "REMOTE on 192.168.10.114", but they are local?  and that the tuners are offline?  I am assuming once I figure out the whole tuners being remote, that will fix them being offline.  I am using the Happauge 500 (Dual Tuner/FM Radio) tuners.. in the setup it seemed to correctly identify them as /dev/video0 and /dev/video1.  Any pointers on logs I can look at..  Linux runs so good that it has been over 2 years since I originally setup my myth box. (Fedora 5) so I am a little rusty on where to look and googleing "REmote tuners" doesn't help because some tuners are remote.  Any help would be greatly appreciated.

---

### Post by volkswagner on 2008-06-24
This post is for multiple machines, it may still help.  Check out post #11, majoridiot gives great advice.

[http://ubuntuforums.org/showthread.php?t=754052&page=2]("http://ubuntuforums.org/showthread.php?t=754052&page=2")


Make sure you set your IP as static.  Make sure it did not change.  You may also be able to set the ip in setup to the loopback address if this is the master BE.

Any info in the logs may help.

---

### Post by bippy_b on 2008-06-25
Ahh..  as detailed as i tried to be, I forgot...  Box is setup with a reserved DHCP IP, so it is like it is static.

Which logs do I need to post/look into. (This is the rusty part that I was mentioning earlier.) 

Thanks.

---

### Post by volkswagner on 2008-06-25
> **bippy_b said:**
> Ahh..  as detailed as i tried to be, I forgot...  Box is setup with a reserved DHCP IP, so it is like it is static.

Which logs do I need to post/look into. (This is the rusty part that I was mentioning earlier.) 

Thanks.

Backend log.  It is located /var/log/mythtv/mythfrontend.log

---

### Post by DutchLoki on 2008-06-25
Is it possible you only installed the frontend on your machine? When you want to use your tuners locally you also need to install the backend. Said differently: in this case you want to use the MythBuntu installer to install a combined backend and frontend. 

the simplest way is to following the installation manual from the MythBuntu site.

---

### Post by volkswagner on 2008-06-25
Sorry, I wrote the frontend log location.  Replace "mythfrontend.log" with mythbackend.log
Just in case it was not obvious.

---

### Post by bippy_b on 2008-06-25
Thanks guys....
Not really sure what happened... I was looking at the logs...  I saw a couple of errors did some googling on them..  went into my tuners and they DID NOT SHOW!  So I thought.. hmm thats strange...  so I recreated them....  now they appear to be working properly...  they are recognized as local, but in the status page the old ones still show..  but they don't show in mythtv-setup..  I will probably just delete them from the database.

Thanks for pointing me in the right direction with the logs...  that helped a lot. (I think this might be like riding a bike..  it is all coming back to me now.)

---

