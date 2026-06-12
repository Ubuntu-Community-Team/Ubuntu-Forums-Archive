---
title: "SSH can only connect if logged in through terminal first"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by Fenris_rising on 2010-03-08
Hi All

I am having a small issue with my SSH usage. I have a main PC OS 9.10 that has a wired connection to the wireless router. My EEEPC 904HD is a wireless connection to the same router.

I use my main PC as my music store and of a night I sometimes listen to this via my EEEPC using the 'connect to server' icon. This has been the norm for some time.

Now of late my connection is being refused. Initially I thought it was to do with the SSH file of trusted connections as from time to time I have had to delete this file as rebooting of the router may have altered the IP of my machine. This usually solves the problem.

But I now have to use terminal to

```
ssh 192.168.?.?
```

I then have to confirm the connection and use the password to confirm fully. After that I can then use the GUI to get into my main PC, by inputting the IP, port, folder, user name and password,  as usual.

Am I missing something? Nothing has been changed by me to have caused this so far as I know. I also have 2 folders set to share via samba over the network which works perfectly these folders are accessible by others on my home network. I use SSH for myself to fully access my folders on my PC from the EEEPC.

regards

Fenris (Baffled)

---

### Post by Iowan on 2010-03-08
Is that a Network Manager-controlled machine? NM only activates the interfaces on login... but that doesn't really explain why it worked previously (except NM was easier to bypass...).

---

### Post by Fenris_rising on 2010-03-08
I am assuming it is NM as it is a 'default' install no tinkering by me. Is this some sort of security tightening that was deliberate then or just a consequence of changes in the latest iteration that have caused a side effect?

I think I saw you reply in a similarly phrased post that NM may now have issues/need turning off to get round the ssh glitch. I thought his issue was slightly different or did I miss understand and infact we share the same problem?

The only thing to confound this though is the fact I can ssh from the PC to the EEEPC using the connect to server GUI without issue. So the problem seems to be one sided.

regards

Fenris

---

### Post by Iowan on 2010-03-08
I've always been of the opinion that NM ignores interfaces configured via */etc/network/interfaces* - but [recent]("http://ubuntuforums.org/showpost.php?p=8936490&postcount=23") threads suggests this may no longer be true.

---

### Post by Fenris_rising on 2010-03-09
So is this some sort of conflict within Ubuntu?

Reading the thread you indicated and following some links within it am I correct in thinking that NM can be removed so long as I have the network list set up correctly.

Would this 'theoretically' stop me having to log in to my main PC via terminal so I can then use the GUI 'connect to server'?

regards

Fenris

---

### Post by Iowan on 2010-03-09
> **Fenris_rising said:**
> ... am I correct in thinking that NM can be removed so long as I have the network list set up correctly... I hate to suggest removing Network Manager - only because if networking quits, it's kinda difficult to put NM back. Dunno if [disabling]("https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager") it is adequate - or if it must be completely removed...

---

### Post by Fenris_rising on 2010-03-10
Hi there

I am not sure I fully understand what has occurred but at the root of this issue is an idiot.

My PC had a second HDD the folder string was therefore -

/media/disk/*****  <-****being the final destination folder.

This disk is gone due to hardware failure and it now looks like I was using the wrong folder string which is why I could not get in. This is what I have to put -

/home/fenris/**** 

works perfect now but doesn't explain, at least to me, why I was able to get to the final destination folder with what was obviously the wrong command string just because I had done ssh via terminal first?

I had tried to use the folder string -

/Videos which didn't work. What I don't get is I would have thought my original folder string was as above but it now looks like it should have been -

/home/fenris/media/disk/****

but only because it seems I have to use the ~/ to get into it now.

If that made any sense whatso ever please feel free to enlighten me

regards

Fenris

---

### Post by Iowan on 2010-03-10
> **Fenris_rising said:**
> I am not sure I fully understand what has occurred but at the root of this issue is an idiot.You should quit loaning out your computer... :-k
Only thing I can think of is if there was/is some link in your home folder that makes the extinct path somehow valid.:confused:

---

### Post by Fenris_rising on 2010-03-11
Except for the fact that the install is a fresh install due to The same 'idiot'. Down grading back to 8.10 because I misread the signs of a dying drive as an issue with samba. Before going back to 9.10........
Perhaps I was just using the wrong string? It's usually late at night when I'm phaffing around with this as I don't sleep well and watch/listen to stuff so it is in all likely hood me screwing it up in a daze.

Appreciate your time and input!

regards

Fenris (The idiot) =D

---

