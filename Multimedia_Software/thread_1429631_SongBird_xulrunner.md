---
title: "SongBird xulrunner"
date: 2010-03-14
forum: Multimedia Software
---

### Post by Adams87 on 2010-03-14
Hi. I am new to linux, I've been playing around with Ubuntu and I'm really liking it. I have to tried to install SongBird from the tar I have it my home directory, but when I try to run it with ./songbird it gives me this error

could not find compatible GRE version between 1.9.0 and 1.9.0.*.

I have done a lot of searching before posting and I haven't been able to come up with a solution. One place I was looking I seen something about xulrunner but I have no idea what that is but when I type xulrunner -v I get

Mozilla XULRunner 1.9.1.8 - 20100214235958

Thanks in advance,
Adam

---

### Post by n0dix on 2010-03-14
Do you have installed java-jre?

---

### Post by Adams87 on 2010-03-14
I dont think so. When I search for java-jre in synaptic it doesn't find it. Is that my probem? Where would I get it or what repository would I need to add to get it?

---

### Post by Arkitekt on 2010-03-14
have you tried adding the getdeb repo and installing it from apt?

---

### Post by Adams87 on 2010-03-14
> **Arkitekt said:**
> have you tried adding the getdeb repo and installing it from apt?

I'm not sure exactly how to do that, as I am very new to linux and the terminal although I have been trying to use the terminal as much as I can because I would like to to become proficient at it.

How would I do that? Sorry, I'm trying not be such a newbie.

---

### Post by n0dix on 2010-03-14
```
$ sudo apt-get install sun-java6-jre 
```

---

### Post by Adams87 on 2010-03-14
> **n0dix said:**
> ```
$ sudo apt-get install sun-java6-jre 
```

I found that I do have sun-java6-jre installed, I was searching for java-jre... haha

I added the getdeb repo and installed songbird from there and it works perfectly thanks :).

I still don't understand why it wouldn't work from the .tar, o'well. Thank you for your help.

---

### Post by n0dix on 2010-03-14
Please, mark the thread as Solved.

---

