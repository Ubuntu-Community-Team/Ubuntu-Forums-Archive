---
title: "Need a download Manager"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2008-12-12
Hey,
 What are the best download managers for linux? like downloadthemall!(dta), downloadhelper add on for firefox, and firefox integrated download manager.

I need one that will allow me to use proxies or preferably TOR(although im not sure if TOR supports FTP transfers).

Reason being a certain website recently started putting a time limit on how much video you can watch with a combination of cookies and monitoring of IPs on their site. This is rather frustrating considering they host some of the best videos...

well as a solution I have found numerous ways to download their streaming videos .flv file(with some of the download managers I mentioned above)... BUT.... they dont monitor by time they monitor by how much you have gotten from there server I think. Its around 250MB or so. So downloads eventually stop before completed... 

My theory to a solution to this(and the reason why I put this thread in networking)

I have been able to use TOR and Vidalia to change my displayed IP on command. SO what I want to try is to ether get firefoxes download manager to work with TOR or some other download manager. So in theory 1)start the download. 2) before the limit is reached, pause the download and change proxy or TOR node to a different IP. 3) resume the download, and repeat till ALL of the file is completed.
I know TOR says that it can be configured with maney differnt apps by configuring it to the right localhost and port. 
I dont know much about this kind of stuff so I really dont know if my idea will work or not...
And I dont plan to do this a lot to eat the TOR networks bandwidth...

And maybe it can be done with a configuration of different transparent proxies... I dont really know.. 

So what download manager would allow me to implement and test this idea?
Thank you for your thoughts and suggestions.   :)

---

### Post by albandy on 2008-12-12
I don't know if this will help you, I use d4x, but are you sure the server that hosts the movies allow data resuming? 

When you resume a file the server needs to seek the hosted file so if there is a transfer limit and is well configured the server will count the data while seeking in the hosted file.

sudo apt-get install d4x

---

### Post by al2cane on 2008-12-12
I use Flashgot with Firefox, and DownThemAll. Works quite well for me so far.

---

### Post by Dwiman89 on 2008-12-12
I havent been able to pause and resume... I wonder if I will be able to change my tor identity while the download is in progress?

also d4x seems nice but there are a LOT if features in it, im not sure I can configure it to the TOR network....

This would probably be easer if I could see more whats going on wiht my own network...
 Is there an application to see more extensive information on my network, like port traffic and what apps are using what ports and gateways, and who and what is accessing me...

someone said something about netstat. I wasnt able to find in in synaptic...

So what apps would also allow extensive network monitoring?

---

### Post by albandy on 2008-12-12
> **Dwiman89 said:**
> I havent been able to pause and resume... I wonder if I will be able to change my tor identity while the download is in progress?

also d4x seems nice but there are a LOT if features in it, im not sure I can configure it to the TOR network....

This would probably be easer if I could see more whats going on wiht my own network...
 Is there an application to see more extensive information on my network, like port traffic and what apps are using what ports and gateways, and who and what is accessing me...

someone said something about netstat. I wasnt able to find in in synaptic...

So what apps would also allow extensive network monitoring?


For analize network traffic I use wireshark (the old ethereal). I think is one of the best network analizers.

---

