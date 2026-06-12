---
title: "view ubuntu from windows pc"
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by mannock on 2006-05-16
so far so good, i''ve installed ubuntu on my spare pc,  i can use the email and internet progs,  and even connect to my windows xp machine and copy files both ways.  but from my xp,   i cannot see my ubuntu machine.  looking in the help section it goes on about remote/local machines,  is this relevant,  is a machine on a local network a 'local'  one or remote?   i'm afraid the help is just not friendly enough,  i am a complete newb,   only ever used windows.
i forgot to mention,  from xp i can view my other machines as long as they are running xp.  (one of them dual boots with ubuntu)

---

### Post by AndyCooll on 2006-05-16
I'm assuming you've got Samba working and that both boxes are on the same domain, and that your user names are the same?

A few questions:
1). Have you got samba and samba-common installed? 
2). Have you enabled some shares on your Linux box?
3). Have you set your Samba password?

```
smbpasswd -a yourusername
```

:cool:

---

### Post by mannock on 2006-05-17
hi AndyCooll,  well i've got samba installed,  but samba common?  don't know.
i've enabled shares,  at least i've set some folders to share.
samba password,  no i've seen no mention of it.
how can i tell if samba common is installed,  and is that code you mentioned just typed into a terminal to set the password,  and does the password have to be my ubuntu username?   thanks.

---

### Post by mjm115 on 2006-05-17
Maybe [this]("https://wiki.ubuntu.com/SettingUpSamba") can help.  It's a tutorial on samba.

---

### Post by mannock on 2006-05-18
thanks for that link,  but i've come unstuck at the first hurdle.   what do i put in the 'domain'  box.  what's a domain and how do i know what mine is?

---

### Post by AndyCooll on 2006-05-18
Your domain name is essentially the name of your network/workgroup. For instance, if you've used the default MSHOME on your XP machine then you want to use this here too.

:cool:

---

### Post by AndyCooll on 2006-05-18
You can tell whether samba-common is installed by using Synaptic. Do a search for "samba", the result will highlight what Samba software is installed. Either that or type into acommand line 

```
sudo apt-get install samba-common
```

If it's already installed it will tell you so.

Yes you copy and paste the code I've typed in, replacing "yourusername" with your Ubuntu/XP username. And yes the password should be the same as your Ubuntu/XP password. It's easiest if everything is the same/common to all OS's and linking software.

:cool:

---

### Post by mad_dog369 on 2006-05-19
Hello.
I have been using ubuntu (breezy badger) for about a week now and I am surprised at how better  it can perform tasks than windows but I am having trouble with the network, I can use the internet send email and even go on my msn account but I can't share files with my xp pc, I can see the ubuntu computer there and it says ubuntu but when I try to open it prompts for a username and password to log onto ubuntu I have tried all the usernames and password I have on my systems but still I cant access it. this is the the same on the ubuntu pc it prompts for the password to log into ubuntu and it accepts it then it will ask for another password to log onto my username with @ after it then with my ip.

please help me i will love to use a different os to microsofts hell wholes!

---

### Post by mad_dog369 on 2006-05-19
i am still waiting for a reply from anyone that can help me get my samba and network sharing files working, i wont be back on till the morning.

---

### Post by mannock on 2006-05-19
i think i'm completely out of my depth here,  i got so frustrated with the network prob,  i deleted everything in the network setup windows hoping to start with a clean sheet,  only to find on the next boot that many of my basic applications would not work.  can't think how i could have caused that.  and i could not find a nice easy  'system restore'   so i booted with xp and deleted the ubuntu partitions and reinstalled.  this time i'm going to be more careful and research each step first.  thanks for the help so far folks.  i'm going to the absolute beginners room!

---

### Post by mad_dog369 on 2006-05-19
I am still having trouble with my network and I think the reason I can't share anything is because of samba and it think I have to make an account on samba but not shore how. If any one does know how please help.:confused:

---

