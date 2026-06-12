---
title: "Listening to a remote music collection with Ubuntu as sever and Windows as end point"
date: 2010-02-05
forum: Multimedia Software
---

### Post by employeeno5 on 2010-02-05
Hi everyone!

So here's my goal. I want to be able to listen to the music collection on my home desktop which is running Ubuntu 9.10 64-bit, on my work computer which is running Windows XP.

I know little about networking. But to give you an idea of the extent of my knowledge and experience, here is what I can do: I  know how to ssh into my home computer from work. I've also (though more through following instructions than having a solid understanding) have used Fuse and sshfs to remotely mount my music folder from my desktop onto my netbook (which also running Ubuntu, and is typically only over the local network). I also understand how to configure my home computer's router for port forwarding. 

However, at work, I do not have access for any changes to be made with regards to port forwarding or anything server side if that maybe required. Though the way things are currently setup I have no problem contacting my home computer through means like ssh or VNC. 

I'm not sure what might work at all, never mind what might work best, for a non-local connection using a Windows machine on the receiving end. 

Are there a specific programs that can stream this and then something Windows based to play it back? Is this something mpd or a similar program can do? Is there a way to remotely mount files like sshfs? 


Forgive me if this is all seems very ignorant and many thanks for any help! Also forgive me if there is a good guide or something posted somewhere already. I searched around and didn't find anything. In fact, I haven't posted to these forums in so long because 99% of the time I can find information already out there that's helpful for what I'm trying to do. Today I had no luck though and look again to these fantastic forums.

Thanks again in advance for any advice.

---

### Post by markbuntu on 2010-02-05
There are some apps around that can stream to a web browser, sockso comes to mind. I think you could use mediatomb too.

---

