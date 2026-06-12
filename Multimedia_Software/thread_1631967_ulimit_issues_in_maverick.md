---
title: "ulimit issues in maverick"
date: 2010-11-27
forum: Multimedia Software
---

### Post by Jay105 on 2010-11-27
hey guys
 
upgraded to maverick and really actually quite like it. my problem is  when i came to set it up for audio work. i downloaded the stuido audio  package through synaptic, but when i load up ardour it greys out and  become unresponsive. i messed with some jackqtl settings but that didnt  fix it. i googled my problem and found the command
 
 **ulimit -l**
 
which is to check the memory available to lock down. it came out at 64 [IMG]http://www.linuxforums.org/forum/images/smilies/eek.gif[/IMG], thats **kilobytes**!  i then tried **ulimit -l unlimited** to boost it to usable levels, only to get [B]james@james-desktop:~$ ulimit -l unlimited
bash: ulimit: max locked memory: cannot modify limit: Operation not permitted[/B]. i tried sudo before, root, loads of other things but no good. any ideas?

---

