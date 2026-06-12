---
title: "Home networking issues"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by bobnutfield on 2006-03-05
Hi everyone,

I am having difficulty setting up my home network and issue is with the Ubuntu box.  It will not recognize anything on the network.  This is the setup

Box1:  Fedora Core 4 serving NFS, Printing and Samba
Ubuntu set up as client
WinXP laptop as Samba client

The FC4 box and WinXP communicate flawlessly, including print shares.

The FC4 box and Ubuntu are wired to an ADSL router with DHCS.  The laptop connect wireless.

The Ubuntu box is online with the net and can ping and be pinged.  The issue is that it will not recognize either of the other computers when opening network servers.  netstat returns normal results, ipconfig eth0 returns normal.
Firewalls have been disabled temporarily for testing, no result.  It does not "see" the other linux box, but does see the laptop but refuses to open it.  When trying to connect to the linux box by IP address, it returns "Connection refused.", with the same result from telnet.  Traceroute in Ubuntu returns normal rsults.

I cannot figure this one out and so far neither has anyone else.  I am trying this one more post before I throw in the towel and dump Ubuntu for a distro more network friendly.  I am hesitant to do this because it my partner's machine and she like the distro (it is very easy for her to use).

Anyone with any thoughts would be sincerely appreciated.

Bob

---

### Post by Herman on 2006-03-06
Hello, Bob, I found it the easiest to use SSH  between Linux boxes, and it's supposed to be the most secure too, providing you use good secure passwords. Here's ([my way]("http://www.users.bigpond.net.au/hermanzone/p11.htm")) to set it up. This should be sufficient for a home network. It should only take around fifteen minutes. It's not difficult at all.  :-D (Herman)

---

### Post by bobnutfield on 2006-03-06
Thank you for your reply.  I have followed your instructions and they worked very well. It is indeed a pleasure to have these issues resolved.  Oddly though, I am only connecting through Samba, even after installing OpenSSH and using that as the connection.  That is fine because all I needed was to exchange files and I am now able to do that.

Again, thank you for your help.  Your web site is very helpful.

Bob

---

### Post by bobnutfield on 2006-03-06
If I could indulge once more, I am having difficulty with the passwords.  The instructions on your site are a little vague as to where these passwords are entered and stored.  Once I can do that, I think I am home free.

Any help very much appreciated.

Bob

---

### Post by Herman on 2006-03-06
> If I could indulge once more, I am having difficulty with the passwords. The instructions on your site are a little vague as to where these passwords are entered and stored. Once I can do that, I think I am home free.
 I'll do some work on that page in the next week or so and see if I can find a better way to explain things then.

Meanwhile, say computer 'red' is the one we are sitting at, it is the 'client', the one we are making the connection from, and computer 'blue' is the 'server'. (It is the remote computer we want to access, even though it might be sitting only three feet away). Now, when I started up computer 'red', I logged into it with my regular username password. Everything is normal so far.

When someone starts computer 'blue', that someone has a user account with a username and password. let's just pretend for example it's my wife's computer, and she doesn't mind telling me her username and password, we have no secrets to keep. So looking at the example on the website, at the 6th illustration, I type in her username in the username field. I'm going to log into her useraccount. Then for the 8th illustration, I type her password, the one she uses to log into her computer when she starts it up. That will give me complete access to her files, the same access she has.

Then it asks for a password for a 'keyring' if I had the checkbox marked for that. This 'keyring' is something in my own computer uses for automatically remembering passwords. Personally, I just use my own regular login password for my own computer for a keyring password. Other people might prefer to make up a special keyring password if they wish. In the 10th illustration, it asks for a password for the keyring. I might eventually store many passwords to log in to various accounts in other computers in the house, or even in the outside world if I know someone who has an account for me that I can log into. I can have them all stored in the keyring, and once I have them stored in the keyring, all I have to remember is my keyring password.

Beyond that, it is a matter of learning how to use 'users and groups', and Linux directory permissions.  
Does this help you? :-D (Herman)

---

### Post by bobnutfield on 2006-03-07
Thank you.  That was very clear and I was able to set it up just fine.  Only issue now is that the Ubuntu program "user shares" freezes after setting this up and I have to force quit.  Something to do with permissions I'm sure.  I'll clear that up.  Thank again for your kind assistance.

Bob

---

### Post by Rikostan on 2006-04-02
Oh man!! I have been struggeling with NFS for hours on end now and this method worked in even less than the 15 minutes herman said it would.

Thank you!

---

