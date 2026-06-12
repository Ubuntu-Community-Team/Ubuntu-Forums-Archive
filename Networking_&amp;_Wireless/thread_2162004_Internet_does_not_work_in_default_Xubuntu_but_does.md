---
title: "Internet does not work in default Xubuntu but does in Unity"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by Subcomfreak on 2013-07-12
Recently I have been experiencing a rather odd error regarding my Internet connection. I Have Xubunut 12.04 installed and I love the xfce interface. But a while ago I decided to try out unity so installed it alongside xubuntu. So I have Unity and XFCE running on the same machine and I'm very happy.

Recently I noted that my network connection has been oddly spotty when running it normally with an Xubuntu session. It would connect to the network but it would not connect to the Internet. It would connect to the Internet but run at very slow speeds. Sometime it would be okay, other times it would have trouble even connecting tot he network. I was puzled by this and just resulted to connecting and reconnecting to the router until it worked.

But today I decided for some reason to boot to unity. I have no problems in unity at all. I go to unity and everything works, log out and go to xfce and I can't get Internet. It is really weird. I have no idea what it could be. Is there some conflict between the two network managers? 

So I hope there is some way to resolve the problem. I have no idea what log files or outputs you will need, I don't know much about networking and the like :). Just tell me what to post.

Ubuntu forums has always helped me in the past.

Thanks in Advance!

---

### Post by Subcomfreak on 2013-07-12
Would it be wise to try to reinstall the network manager and reinstall it? How would I do that? Is it safe?

---

### Post by Subcomfreak on 2013-07-12
Tonight the Internet "glitched" again while running xfce. So I tried to ping my phone witch was also connect to the wireless network, I also pinged my computer from my phone, so I could test upload and download. Both the phone and the computer had problems pinging each other, sometimes with incredibly long delays of over 8 seconds! 

Logged out and logged into unity, and tried the same thing... It worked perfectly, no glitches at with pinging from and to the phone. Right now I'm posting from unity fine, but in xfce I couldn't load a page. 

I have no idea what the problem could be. This is truly becoming more and more bizarre.

---

### Post by Subcomfreak on 2013-07-13
Okay, I using apt-get reinstall I reinstalled the following packages:

network-manager
network-manager-gnome
network-manager-ppt
network-manager-gnome

I'm going to see if it works.

---

### Post by Subcomfreak on 2013-07-14
Seems to be working now after the reinstall.

---

