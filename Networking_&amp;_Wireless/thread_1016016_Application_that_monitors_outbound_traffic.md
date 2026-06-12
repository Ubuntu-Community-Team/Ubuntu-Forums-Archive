---
title: "Application that monitors outbound traffic ?"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by bulletmike on 2008-12-19
Hi All,

I have a server running Ubuntu at home. I can connect to it through ssh from office. However, I have stopped connecting to it because company policy states that we are not supposed to connect to our home pc's. I want to hone my ubuntu skills while I have some free bandwidth at work but Im worried I might loose my job if I get caught. 
My question is, is there a way that those people monitoring the network traffic to sniff onto the packets and figure out that I am communicating with my ubuntu box. I would think not since the packets are encrypted in the first place. And Im sure there are qua trillions of data packets flying in and out of the system so it would be hard to sniff onto each one and figure out what it contains and everything. But I don't know much about networking so Im hoping if anybody versed well in this area would give me some ideas.

Thanks as always and Best regards,

-m

---

### Post by jonobr on 2008-12-19
if you like your job, no work around or suggestion is worth it.

---

### Post by bulletmike on 2008-12-19
Its worth the knowledge !

---

### Post by trubshac on 2008-12-19
Hi

I'm no expert, but this is what a knowledgeable chap once told me when I was doing a similar thing....
They should certainly not be able to decrypt the data itself, but they could determine that you are starting a ssh session.  One way to try to hide this a little more is to move the ssh port on your home pc from 22 to 443 which is normally used for https.  This way, it is less likely that the IT "packet police" will be concerned about encrypted data going out over a normal https port.

---

### Post by bulletmike on 2008-12-19
Now thats the information and tips I was looking for. Thanks trubshac!

---

