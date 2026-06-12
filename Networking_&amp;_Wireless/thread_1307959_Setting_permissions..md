---
title: "Setting permissions."
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by pearldrums on 2009-10-31
Hi, so I'm having a little bit of trouble transfering files between two ubuntu systems. For reference I'll call one computer "main" and the other "netbook".

I have a shared folder on both main and netbook where I turn all options such as "allow users to read and write" on. I am transfering music files from a windows partition, I know you might wonder why I don't just store my music in ubuntu, but the reason is that if I am running windows I can still access the files (and also so can ALL users on ubuntu). If take a file from main and put it directly into the shared folder on the netbook the file will have no owner file and thus nobody can modify that file. I can get around this because I still am able to modify the contents of that file (despite the fact that permissions to them are also given to nobody), but I'd rather do without this inconvienence. Another way to do it is to put the file into my ubuntu shared folder on main and access it via the network from the netbook. If I do that the permissions are given to root. And I can do whatever I want, but then I'm constantly switching between computers.

I'll try to map this out a little more visually if that all didn't make sense:

folder on windows partition on main -> moved to shared folder on netbook (folder permissions are given to nobody)

folder on windos partition on main -> moved to shared folder on main <- accessed from netbook (permissions given to root)

Does that all make sense? Heres a little quirk that might mean something, when I access my main computers folder from the netbook I get prompted for a password, I don't get prompted when I access the netbooks shared folder from the main. Well what I would like to do is be able to just drop a file right into the netbook's shared folder and give the permissions to root. Is this because I'm going directly from a windows partition? Would it be different if i were moving a file not an entire folder. Am I just going about this the wrong way? Is the cause of my main computer requiring a password also the cause of the permissions issue? Should I have posted this in the complete newbie section?

thanks for all of your help
Pearldrums

---

### Post by Captain Kremmen on 2009-10-31
Hey.. (yep, should have been newbie forum :))

I'm new as of yesterday too and this was one of the first things I had to solve..

Linux is very security conscious so you can't just paste and copy whereever you want.. 

You'll be prompted for your admin password whenever you want to change linux structure, so...

Open the terminal, and type..

```
gksudo nautilus
```

The sudo part gives you root access and the gk part is for graphical representation..

So what the command will do, after you have been prompted for password, is open a window that will be alowed to be altered, you can navigate normally and paste to that window.

Sorry it might not be as clear an explantion as I'd want to give, but I'm still getting used to it myself.

---

### Post by Captain Kremmen on 2009-10-31
Oh.... one other thing.

If you do get a solution on the forums, then it help GREATLY to mark your post 'solved'.

There are so many questions asked and answered here that re-labling your post means it won't have to get attention again from the gurus.. instead of them having to wade through all of the answered posts and taking time away from looking for solutions to new problems..

(Easier said than done though, I'm still trying to figure out how to re-lable one of mine :/)

---

### Post by pearldrums on 2009-11-01
thanks for your help. BTW you can click on thread tools and there is a link for marked solved!

---

