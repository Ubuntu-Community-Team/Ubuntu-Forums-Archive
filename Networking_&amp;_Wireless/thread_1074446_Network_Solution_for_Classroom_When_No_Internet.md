---
title: "Network Solution for Classroom When No Internet"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by LaneLester on 2009-02-19
I'm putting the finishing touches on an 8-computer network in my classroom. I'm the science teacher at a small low-budget private school, and I'll have a DSL modem, router, and two switches connecting the 8 Ubuntu machines. A ninth computer will be on my desk and connected wireless.

When connected to the Internet, there is no shortage of useful goodies. But sometimes the Internet is not available, and I'd like to have a **simple** way for my computer to communicate with the student machines and for them to respond. For example, I'd like to be able to present an assignment to them and have them submit their work.

I'd rather not set up my computer as a server through which all the student machines connect to the Internet. Do you have a suggestion for me?

Lane

---

### Post by xtreme35967 on 2009-02-19
Well If you have internet on all of the computers you could always just use e-mail to assign work and let them e-mail their work back to you. 

You said that some times the internet is not available, do you mean that you are not going to allow the internet on the network all the time? If that is so then e-mail may not be a good route either. 

If you dont think that e-mail is the way to go you could use file sharing. You could set up the folders on you PC and then share them with the others. Each folder would need to have permissions set up so that only you and the student that the folder belongs to will have access to it. It not too hard to do but it will take you a little bit of time to set these up.

---

### Post by insineratehymn on 2009-02-19
Yeah! Great to see a school getting on the open-source ship and **not** paying those ridiculous license fees!

Anywho, you're computer can still be a server without being a gateway.

I don't know how much networking you know, so I'll keep it layman.

You can set up a samba share on your computer, that way if a student brings in a personal laptop from home or something (or something with windows on it) they will still be able to see the share. You would be able to see his share just fine, just not the other way around. 

Since all of your computers are on the same subnet, the small network containing the 9 computers on your side of the router (technical: demarcation), they will all be able to see the whole network just fine.

They are ran into the switches, then into the router, then out into the cloud; so everyone can see everyone, and nothing outside of that.

You can simply add any files into that samba share you want and they will be able to pull them out as they please.

If you don't wanan do samba, and want something more secure (like, anyone with a wireless card can't see it) then you can look at sshfs. It actually mounts a pseudo-partition on the system that is ssh secured and locked.

Hope this helps. =)

---

### Post by LaneLester on 2009-02-19
Thanks for the suggestions, guys. I plan to have the Internet available all the time and use email or something fancier like Moodle. But ISPs sometimes fail to keep the Internet available, and what I'm seeking here is a backup solution.

I think the samba shares might be the easiest way to go. I was thinking it would be only good for document submissions, but I could put a document with the assignment in the shared folders for the student to pick up.

I'm running out of time to get this set up, so please excuse this newbie question. I see how to set up the shares on my computer, but where will the student find it on his computer? If they click the "Places" menu item, will the share be presented there, or is something more complicated needed?

Lane

---

### Post by insineratehymn on 2009-02-19
No problem with the questions, dude. 

Places -> Network
That will open up a folder, double click on the share and it should actually mount it for you and place an icon on the desktop.

I know you're on a short time table, but you really should think about things like... what happens if billy doesn't like tommy and decides to delete everything he just put in Mr. Lester's folder?

Oh! And openSSH everything. Log into their computer, give a quick "top" on the command line, and you can figure out whos doing a sudoku puzzle or playing the worm game. BTW, Linux games are AMAZING; totally craps on Minesweeper and Solitaire.

---

### Post by xtreme35967 on 2009-02-19
> **insineratehymn said:**
> 

I know you're on a short time table, but you really should think about things like... what happens if billy doesn't like tommy and decides to delete everything he just put in Mr. Lester's folder?



Correct me if I am wrong but can't you setup user permissions on each folder so that only the teacher and the student that the folder will belong too can access it? I am a little new with Linux but I know this is possible in Windows. That way you can see what ever is in their folders so instead of having them copy and paste the work back in Mr. Lester's folder you could just go to their folders and get the work yourself.

---

### Post by insineratehymn on 2009-02-19
You suuuuuuurrreee can. =) Just make it something like 711 or 700 and then only user and sudo have access, you just gotta be careful with the general "world" folder. sshfs will allow him to set up each student with a login script that will match them to their own folder, securely. And, if a kid gets itchy, he can just disconnet that one folder from the share very easily. Ahhh... ssh is amazing.

Something like this:
```
sshfs -o allow_other billy@teacherscomp.localnet:/media/storageHD/billysfolder /home/Billy/classWork
```

---

### Post by LaneLester on 2009-02-19
Thanks for all the tips, guys! I'm planning separate folders for each of the four classes, but separate ones for each student would be too much fiddling, I think. But I see what you're saying about security and will give that some more thought.

I arranged the monitors so they're all facing the center of the room. That should make it easier to keep the students "on track." ;)

My desk computer has a fresh Ubuntu install, and it said it needed to install the Windows sharing stuff. Unfortunately, I don't have the Internet connected yet, so the package couldn't be fetched.

I dual booted to Windows 7 and set up a share which the Linux machines were able to find. So it looks like I'm good to go Monday when the kids return from break.

Lane

---

### Post by insineratehymn on 2009-02-20
> **LaneLester said:**
> Thanks for all the tips, guys! I'm planning separate folders for each of the four classes, but separate ones for each student would be too much fiddling, I think. But I see what you're saying about security and will give that some more thought.

I arranged the monitors so they're all facing the center of the room. That should make it easier to keep the students "on track." ;)

My desk computer has a fresh Ubuntu install, and it said it needed to install the Windows sharing stuff. Unfortunately, I don't have the Internet connected yet, so the package couldn't be fetched.

I dual booted to Windows 7 and set up a share which the Linux machines were able to find. So it looks like I'm good to go Monday when the kids return from break.

Lane

Awesome! If you need any help, PM me or something. I've done similar projects for similar situations, so hit me up.

---

### Post by LaneLester on 2009-02-23
Well, Samba sucks... at least for me. I got everything set up on the "server" computer. Sure enough, in a client computer I can migrate to where the shared folders show up in Nautilus. But when I try to open one of them, I get this message:"Unable to mount location."

So I Googled for Ubuntu and that message, and what I got was a flock of bug reports. According to the posts, the bug first appeared in Hardy

I wish I had time to pursue this, but I don't. I may have to rely on the Internet for file-sharing.

Lane

---

