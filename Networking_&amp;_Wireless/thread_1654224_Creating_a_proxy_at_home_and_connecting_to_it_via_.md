---
title: "Creating a proxy at home and connecting to it via the college internet. Help?"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by cracker89 on 2010-12-28
I am home. And before this I was in college. At hostel infact. With our hostel making life hell for us, in the sense that the provided wifi system there is limited to surfing a measly 100 mb a day. Which, I hope many will see, is unreasonable. And along with this, there are restrictions as to what you can serve. With my ever growing interests and hobbies, this is just not working out, and hardly has potential to. 

At the same time, here back home, I have an unlimited broadband connection, which came pretty cheap too. Say I want to be able to connect from the college net to my home connection (its a static IP) and then continue to surf the net from the broadband at home. Can it be done?

To put it simpler, A is my home broadband. B is my college ISP. X is my laptop, this is what I want to do;

X connects to B and through B connects to A, and A becomes sort of like a proxy. 

That would still leave the problem of 100 mb limits, but that can be worked around to stretch it a bit, thats all I know how to do, but can this ^^^^ be done???

Guidance?

Thankings. Merry X-mas and Happy new year to you all. Hope ur all as lucky as me to be home. :)

---

### Post by Baneblade on 2010-12-28
As I understand it, your 100MB limit is a data cap, rather than a protocol specific cap (http in your post). This being the case, using a proxy would not help you since you are still sending/receiving the same data.

---

### Post by cracker89 on 2010-12-28
Right. Thats correct. But I've found a very flimsy way to delay this realisation of the 100mb cap on the colelge server, to the effect that it usually clocks out around say 170-200 mb. This project is not to counter the 100 mb cap. Just interest and knowledge. Also, the limits on what you can and cant access is again ridiculous. 
Help?

---

### Post by Rasa1111 on 2010-12-28
a bump to get this thing to the top,
can anyone help brother cracker?   lol

 He is great peoples and I would love to help here if I knew more about it.. 

But I do remember well,
my little brother coming home from college on breaks and whatnot..
and us having conversations about he and his mates doing things like this.
 (getting around the data cap)

I am going to email this thread to him, 
See if he can't enlighten me/us a bit. lol

 Happy Holidaze, cracker. <3

---

### Post by K.J. on 2010-12-28
Like was said before, not much you can do to get beyond the hard data cap (unless they are strictly measuring http traffic). There are a few things you can do to stretch the cap. Disabling images by default and then only viewing them when necessary will make 100MB last seemingly forever.

As for the "proxy." The easiest thing is to install an Ubuntu box at home. It can be a vanilla install, just install openssh-server when you're done. I recommend changing the port though and using strict gpg protection, but that's probably overkill if that's all it's being used for.

You'll need to forward port 22 or whatever your ssh port is on your home router.

Now it's a simple matter of creating a socks tunnel for your web traffic. If you're in linux, ssh -D 8080 username@ip-address-of-ssh-server. Then set your browser or any other web application to use the socks proxy localhost:8080. If you're in Windows, you can use Putty to set up the tunnel.

If you have a dynamic IP at home, you may want to consider setting up a dynamic dns service to constantly update when your ip changes. I personally, use a quick script I whipped together that checks my IP address once an hour and emails it to me if it changed.

---

### Post by howefield on 2010-12-28
Your provider is most likely not "making life hell" for you on purpose. 

There are in all probability reasons for the restrictions that you do not make clear in your post, so ask them to help you get round the "problem" - not here.

Thread closed.

---

