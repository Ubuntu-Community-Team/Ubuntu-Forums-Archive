---
title: "Minecraft"
date: 2012-07-04
forum: Multimedia Software
---

### Post by egoshk on 2012-07-04
I have downloaded java, and I have started minecraft. But after i login minecraft goes to a black screen. I have not installed any mods and forced update a couple times. Can anyone help?

---

### Post by msammels on 2012-07-04
What graphics drivers are you using?

---

### Post by egoshk on 2012-07-04
I dont think i have any graphics. I am using close to stalk hp.
Minecraft does work on windows 7

---

### Post by msammels on 2012-07-04
Are you able to enable restricted drivers?

---

### Post by egoshk on 2012-07-04
How would I enable restricted drivers. Im new to this

---

### Post by msammels on 2012-07-04
OK click the dash and type "settings" and open "System Settings", then click "Restricted Drivers".

---

### Post by cipherboy_loc on 2012-07-04
All computers have graphics with the exception of servers. To find out what type of graphics chip you have:

```

lspci | grep VGA

```


Cipherboy

---

### Post by egoshk on 2012-07-04
when i look at additional drivers it says no proprietary drivers are in use on this system. how do i add them?
And it says i have an integrated hp graphics card

---

### Post by msammels on 2012-07-04
That could be the source of your problem. Because the card is integrated, there won't be any proprietary drivers available. How much memory does your card have?

---

### Post by egoshk on 2012-07-04
[http://www.h-node.org/videocards/view/en/660/Intel-Corporation-2nd-Generation-Core-Processor-Family-Integrated-Graphics-Controller--rev-09-](http://www.h-node.org/videocards/view/en/660/Intel-Corporation-2nd-Generation-Core-Processor-Family-Integrated-Graphics-Controller--rev-09-)
Thats the info on it.

---

### Post by msammels on 2012-07-04
Apparently it *works, but without 3D acceleration*... maybe this is what is affecting you?

---

### Post by egoshk on 2012-07-04
So what can i do to get minecraft running?

---

### Post by DMGrier on 2012-07-04
go into the software center and type "i915" and make sure the driver is installed, it should be by default but you never know. I know on mine it is but there is another on for debugging symbols which I am pretty sure does not fix your problem.

---

### Post by nemodot on 2012-07-05
I had that problem using Sun Java. Moving to OpenJDK fixed it. Try it out! (delete sun java first)

---

### Post by Zvlwab on 2012-07-05
This is a bug in Minecraft

You need to download the following zip:
[https://docs.google.com/open?id=0B24pyGVnqQZmQmtlOGxicGtaZWs](https://docs.google.com/open?id=0B24pyGVnqQZmQmtlOGxicGtaZWs)

Extract it to ~/.minecraft.
If you're not sure where to place them exactly, all of those files should overwrite already existing files.

---

