---
title: "Music Server Remote Control"
date: 2008-05-26
forum: Multimedia Software
---

### Post by jcr1 on 2008-05-26
Hi all,

I'm quite a n00b so sorry if this is a over-asked question.

I am thinking about setting up a server in my home, an old pc with ubuntu-server on it, which will serve as my main place to store data, which anyone can access on the network...but thats all a whole different can of worms.

My question for here is...MUSIC. remote control music playing. Here is what I envisage:

The server, hidden away, physically connected to speakers in the house. Music files all stored on the server. Someone wants to listen to music through the speakers can just log on to the server (program? web interface?) and see the list of music on there, choose a song to play and out of the speakers it comes.

I was hoping for a simple web interface program so that anyone on the network can access it with just a web browser. 

Is this feasible / possible / sensible? Open to better suggestions. Remember I am new to this stuff.

Thanks in advance!

---

### Post by cariboo on 2008-05-26
Have a look at gnump3d it is located in the repositories. It has a web interface. Just install it, edit the conf file to point to where your MP3's are located, and then point your web browser to [http://severname:8888](http://severname:8888) and your good to go.

Jim

---

