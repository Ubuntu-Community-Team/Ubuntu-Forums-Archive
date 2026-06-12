---
title: "openSSH and VNC"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by Scooter_X on 2010-02-08
So I'm still trying to get the hang of this VNC stuff and want someone to help me out a bit with it. 

I'm using the remote desktop to access my dear sweet mom's computer from wherever I am at so I can help her figure out little problems here and there without driving forever to get to her house. I understand it uses the VNC system. I also understand that the only thing that's encrypted in the VNC system is the password itself, and even then it's not that secure. I was snooping around on tightVNC.com and found that I should probably use OpenSSH or something along the lines of that protocol to secure things. So, I installed something called PuTTY (I'm at work using Windows) which I found on the OpenSSH website. It's similar in interface to tightVNC that I just used to get on my mom's computer, where it asks for the domain and all that. But here's where my questions come about:

Is PuTTY (OpenSSH) a system that lets me view my mom's desktop, or is it just something that I use to open a secure connection with and then use tightVNC to hop on that connection to then see my mom's desktop?

PuTTY said that there was a network error and couldn't connect me unless I opted for a 'raw' connection - is that possibly because I don't have anything of the SSH protocol installed on my mom's computer?


I'd really appreciate any help that anyone can give me. Thanks in advance!
 
 --Scooter_X

---

### Post by noway2 on 2010-02-08
This may be of interest to you: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX).  It is available for both Windows and Linux.  At work, I use it on a XP box to log into a Linux system.  It is a remote desktop program, that is much better than VNC with regards to security.  

Using SSH, you can get a terminal login remotely, or you can even forward an X terminal over it, though it can be a bit slow.  

You can use Putty to SSH into a remote system.  I am not sure why it said anything about a raw connection (or really what that means).  Unless the system your trying to connect to has an SSH server on it, you may not be able to connect.

---

### Post by doas777 on 2010-02-08
putty is just a client used to connect to a server that has openssh installed and running on it. 

here is a howto on installing the server on her box:[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

I strongly recomend you look into freenx, as noway2 suggested. it's far supperior except that it does not allow two users to share a session.

---

### Post by Scooter_X on 2010-02-08
Thanks you guys a bunch. That looks like it'd be very useful info. I only looked at it for a second here in class and my professor noticed I was paying attention to something besides her lecture and she got after me, so I'll have to scope it out later. Thanks again.

---

