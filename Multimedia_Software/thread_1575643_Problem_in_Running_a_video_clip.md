---
title: "Problem in Running a video clip"
date: 2010-09-16
forum: Multimedia Software
---

### Post by Tariq Bashir Malhi on 2010-09-16
I have ubuntu 8.04 on my PC, when ever i try to play a video clip it does not work, e.g following is the link that i can not play

[http://www.youtube.com/watch?v=w3YrUJMlzKQ](http://www.youtube.com/watch?v=w3YrUJMlzKQ)

---

### Post by garvinrick4 on 2010-09-16
> **Tariq Bashir Malhi said:**
> I have ubuntu 8.04 on my PC, when ever i try to play a video clip it does not work, e.g following is the link that i can not play

[http://www.youtube.com/watch?v=w3YrUJMlzKQ](http://www.youtube.com/watch?v=w3YrUJMlzKQ)

Install flashplayer by adobe.

---

### Post by sikander3786 on 2010-09-16
I will recommend that you install ubuntu-restricted-extras because you surely are going to run into a situation when you'll say that java is not working, certain video formats are not working. It will save you whole of the hard work in getting, flash, java, fonts, codecs etc up and running. Type in terminal,

```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

```

---

### Post by Tariq Bashir Malhi on 2010-09-16
> **sikander3786 said:**
> I will recommend that you install ubuntu-restricted-extras because you surely are going to run into a situation when you'll say that java is not working, certain video formats are not working. It will save you whole of the hard work in getting, flash, java, fonts, codecs etc up and running. Type in terminal,

```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

```

Following is the out come, after executing above command

eobi@eobi-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for eobi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 83 not upgraded.

---

### Post by sikander3786 on 2010-09-16
> **Tariq Bashir Malhi said:**
> I have ubuntu 8.04 on my PC, when ever i try to play a video clip it does not work, e.g following is the link that i can not play


It means that flash player is already installed. What do you mean by saying that the link doesn't work? It doesn't open up? Or gives a black space in place of the video? Or something else?

---

### Post by Tariq Bashir Malhi on 2010-09-16
When i click on this link, black screen appears with play button, on pressing play button black screen is replace with whiteness.......... nothing else

---

### Post by sikander3786 on 2010-09-16
See the following link for possible problems with flash.

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

(courtesy of forum member lovinglinux)

---

