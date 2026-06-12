---
title: "SSH/SCP issue"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by NR1224 on 2011-05-22
I'm rather new to this whole ssh deal, but I'm taking it in stride, I apologize in advice if my lack of understanding inhibits my ability to correctly explain my issue.

Heres the situation:
I have recently gotten access to a (legal) seedbox. It is a debian server that I can ssh into, and upon putting the torrent files in question into the correct folders, a rtorrent daemon picks them up and adds them. The issue I'm having stems from my seeming inability to SCP the torrent files in question to the server without getting a 'permission denied' response. 
My first question is: is it better form to SCP from my computer, sending the file TO the server, or to log into a shell in the server and grab the file FROM my computer? I ask because I have the same issue either way. 

If I assume that I'm supposed to start at local host and send the file TO the server, this is what I put in to the cmd line, and what I get

nathan@nathan-T900:~$ sudo scp /home/nathan/Downloads/test.torrent [email]xxx@xxxxxx.com[/email]:/home/media/xxx/audio

[sudo] password for nathan: 

[email]xxx@xxxxx.com[/email]'s password: 

scp: /home/media/xxx/audio/test.torrent: Permission denied



Why is permission denied, and what do I do?

---

### Post by gmargo on 2011-05-22
If you are able to **ssh** into the server, then you should be able to **scp** a file to it.

> 
scp: /home/media/xxx/audio/test.torrent: Permission denied
"Permission denied" in this case means that some portion of your destination filename is not accessible, which includes intervening directories.

Does the /home/media/xxx/audio/ directory exist?  Does it have suitable permissions and ownership for the xxx user?

---

### Post by NR1224 on 2011-05-22
The directory most certainly exists, and I believe I have permissions...how do I check?

---

### Post by gmargo on 2011-05-22
ssh into the system and use "ls -l" to inspect the ownership & permissions.

---

### Post by noidian on 2011-05-22
1st Question: Either way is ok as long as you have the access to server. 

I believe you want to ssh the files to your server. In that case, ensure the directory on the server has all the permissions chmod 777 driectory (though not typically recommended giving everybody permission).

I suppose your pc permissions are ok.

---

### Post by NR1224 on 2011-05-22
The output of ls -l

xxx@debian:/home/media/xxx/audio$ ls -l
total 0

The issue with changing the permissions on the server itself are that I'm not sure I have the power to do that...when I try to chmod it, it wont let me...i suppose i could chmod my downloads directory and do teh second method of pulling from my local computer though...right?

---

### Post by gmargo on 2011-05-22
Sorry, I should have said "ls -la" so we can see the permissions of the current directory.

---

### Post by noidian on 2011-05-22
yup just the directory to which you have access in your server you should chmod.

---

### Post by NR1224 on 2011-05-22
xxx@debian:/home/media/xxx/audio$ ls -la
total 8
drwxr-xr-x 2 media root 4096 May 19 17:36 .
drwxr-xr-x 5 media root 4096 May 19 17:35 ..

I have no idea what that means...
I can't chmod any directories on the server. I can chmod anything on my local computer.

---

### Post by noidian on 2011-05-22
d=directory r/w/x read write execute.

split in 3 user, group, others . essentially you have read write execute permission for that directory.

you don't need to chmod or do anything there then.

Ensure your scp is to the right directory.

---

### Post by NR1224 on 2011-05-22
problem solved thanks!

---

