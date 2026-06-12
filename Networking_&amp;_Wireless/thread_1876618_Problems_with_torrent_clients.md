---
title: "Problems with torrent clients"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by Friwise on 2011-11-06
Hi!!
I was using deluge until today. Today I decided to leave it for transmission because the first could not work properly. For some reason I could not download anything eventhough I knew there were many seeds.
Now I have transmission and the same problem exists so I guess the problem is not the client but something else. Can you help me?

Thanks in advance

---

### Post by haqking on 2011-11-06
> **Friwise said:**
> Hi!!
I was using deluge until today. Today I decided to leave it for transmission because the first could not work properly. For some reason I could not download anything eventhough I knew there were many seeds.
Now I have transmission and the same problem exists so I guess the problem is not the client but something else. Can you help me?

Thanks in advance

we cant help with a statement of its "its not working"

what are the error messages if any ?

Does your ISP block the common ports for torrenting ?

are you running a firewall ?

are the ports blocked on your router ?

ad nauseum ad infinitum

---

### Post by Friwise on 2011-11-06
I am sorry for not being more specific.

A. There is no error message.
B. For the other questions I have no idea. 
I am sure I never installed any kind of firewall

I hope it is a bit clearer now

---

### Post by haqking on 2011-11-06
> **Friwise said:**
> I am sorry for not being more specific.

A. There is no error message.
B. For the other questions I have no idea. 
I am sure I never installed any kind of firewall

I hope it is a bit clearer now

well what does not download anything mean.

You add a torrent, it appears in the list, the percentage stays at 0% ?

Are any seeders online ?

does it download at all ?

does this happen for any torrent ?

try one of these [http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt) and post a screen dump of your torrent client whilst trying to download one of these

---

### Post by Friwise on 2011-11-06
I add a torrent. It appears in the list. I have the option to choose what parts, files of it I will need to be downloaded. There are so many seeders online but still it cannot find them and it does not download. This happens with all torrent files I try.

---

### Post by haqking on 2011-11-06
> **Friwise said:**
> I add a torrent. It appears in the list. I have the option to choose what parts, files of it I will need to be downloaded. There are so many seeders online but still it cannot find them and it does not download. This happens with all torrent files I try.

are you forcing encryption ?

got your torrent settings set up right ?

opened port on firewall/router ?

have you downloaded torrents on this connection with your ISP before ?

---

### Post by Friwise on 2011-11-06
Hi again!!!!
Your questions help me searching for my problem from the properties of the programme and on google. 
For some reason the port was 58261 as it should be but something else. I changed it to that and now it works.

However, I still don't get it how can the port change. I had not even idea about ports. I am sure I did not manually changed it and I am sure I was downloading regularly until 3 days ago.

Thanks again! 
I hope this 58261 information might be helpful to other people too!

---

### Post by haqking on 2011-11-06
> **Friwise said:**
> Hi again!!!!
Your questions help me searching for my problem from the properties of the programme and on google. 
For some reason the port was 58261 as it should be but something else. I changed it to that and now it works.

However, I still don't get it how can the port change. I had not even idea about ports. I am sure I did not manually changed it and I am sure I was downloading regularly until 3 days ago.

Thanks again! 
I hope this 58261 information might be helpful to other people too!

the port depends on your client and the router/firewall

i use a random port each time

glad you got it sorted.

Remember to use thread tools to mark as solved.

Cheers

---

### Post by Friwise on 2011-11-06
Can you please explain how to do that with firewall?
I did not know that there is firewall on linux

---

### Post by haqking on 2011-11-06
> **Friwise said:**
> Can you please explain how to do that with firewall?
I did not know that there is firewall on linux

well i wont get into the whole firewall on Linux thing as it is not enabled by default.

Though it should be, see here[ DangerTux on Ubuntu Firewall]("http://ubuntuforums.org/showthread.php?t=1876124")

What i meant is if you are behind a router it is likely to have its own firewall, and so for torrents to work sometimes you need to enable that on your router, which depends on your router.

---

### Post by wojox on 2011-11-06
Try this [BitTorrent optimization and troubleshooting guide ]("http://ubuntuforums.org/showthread.php?t=1259923")

---

### Post by Friwise on 2011-11-06
I run the command ```
deluge
``` and it gave me that error

[ERROR   ] 22:46:28 config:439 Error backing up old config..

---

