---
title: "question about processes initiated over ssh"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by Lacitsym on 2011-01-31
I am a relative beginner and I have a basic question that I'm not sure where to post.  But here's my situation:

I have a headless ubuntu server with my DVD burner attached and a ubuntu laptop with a wireless connection that I administer the server with.

I connect the laptop to the server via ssh and run the growisofs command to write to a dvd.  In the console on the laptop I can see the progress of the dvd burn.

My question is, does the network have any impact on the performance of the dvd write or is the process performed entirely on the Server and the progress reported independently?  If my laptop with the ssh console went down, would the dvd continue to burn on the server?

Should I instead log in via vncviewer and run the command that way?

Thanks for any input! :)

---

### Post by gmargo on 2011-01-31
> If my laptop with the ssh console went down, would the dvd continue to burn on the server?
Maybe, but probably not.  Depends on the code.  (It'll only cost you one dvd to find out the easy way.)

If **growisofs(1)** is a text mode program, you could run **screen(1)** on the server and growisfs within it.  That would allow you to detach safely and reattach.  Or you could run growisofs in the background under **nohup(1)** and redirect the stdout and stderr.

---

### Post by Lacitsym on 2011-02-02
That's just the solution I needed!

Thanks gmargo! :guitar:

---

