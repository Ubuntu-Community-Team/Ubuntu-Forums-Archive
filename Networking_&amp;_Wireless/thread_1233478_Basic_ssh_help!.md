---
title: "Basic ssh help!"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by huggies15 on 2009-08-06
Hi,
At uni we have a supercomputer on which we do all our computational analysis of chemicals. To access it we have to use an ssh client, and then we can drag files onto our allotted space and 'ssh' them to the correct place on the supercomputer. Now what i want to do is be able to access the data from home as well. i know that ubuntu has built in ssh via the terminal, and i have been able to access my allotted space and check how stuff is doing. 
What i dont understand how to do is how to get stuff on/off the supercomputer itself. in windows we just drag and drop it in, but i cant find a gui or anything like that for ubuntu.

So basically what im asking is how do i get my stuff from my pc at home to the uni pc to then move around as normal?

Sorry if that seems an easy and obvious answer, but i did google, and had a quick check on here first, but people seem to already understand how it works.

Cheers,
Steve

---

### Post by huggies15 on 2009-08-06
OK, i figured it out... i was being stupid... just ftp to the uni pc using filezilla...
Is there a way of doing this in the terminal tho? just fewer open windows on my screen makes me happier :)

---

### Post by Sub101 on 2009-08-06
A simple way is in Nautilus to go to File => Connect to Server. And enter the relevant info there. 

A command line option would be scp which is like the normal copy command, but works over ssh.

---

### Post by jaxxstorm on 2009-08-06
You can use the wonderful SCP (which stands for Secure Copy)

its sytax is as follows

```

scp user@host:directory/SourceFile TargetFile

```

So lets say you have the file you want in the directory /home/huggies15 on the university computer and you want it to go to /home/huggies15athome

its just
```

scp huggies15@unicomputer:/home/huggies15/fileiwanttoget /home/huggies15athome/newfilename

```

---

