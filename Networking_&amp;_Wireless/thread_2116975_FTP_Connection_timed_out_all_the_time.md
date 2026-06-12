---
title: "FTP: Connection timed out all the time"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by Paddy Landau on 2013-02-17
I am getting a strange repeat error when trying to upload a file to an outside server. This is happening on two different (entirely unrelated) servers. I had the same problem yesterday.

I wonder if the wise people on this forum could help me identify where the problem lies: with my ISP, my own router, or my own computer?

I am using FileZilla. In both cases, the files keep timing out after a set number of bytes. Fortunately, FileZilla is clever enough to restart from where it left off automatically, but it means that the files take a couple of hours to upload whereas they used to take a number of minutes.

The one server consistently times out after 180,224 bytes, and the other after 262,144 bytes. The timeout happens every time after the number of seconds set in Edit > Settings > Connection > *nn* seconds (so if I set it to 20 seconds, the timeout happens after 20 seconds). But the number of bytes is always the same.

Here is the error message for one of the files (the timeout set to 10 seconds):
```
Error:    Connection timed out
Error:    File transfer failed after transferring 180,224 bytes in 11 seconds
```I have not had this problem before; the last time I tried was one month ago.

Do you have any idea what may be causing this problem?

---

### Post by sudodus on 2013-02-17
I don't know, where to find the problem, but I suggest that you try different things to eliminate some causes.

- Will it be the same problem, when you use your standard file browser to download from the ftp servers?

- What happens if you try when booted from an external drive?

- What happens if you bypass the router and connect directly to your internet connection?

- What happens if you try from another computer?

---

### Post by Paddy Landau on 2013-02-17
Thanks for the ideas.

I'll try them all, except for bypassing the router: that would be difficult.

I'll report back, probably tomorrow.

---

### Post by Paddy Landau on 2013-02-17
I'm getting the same problem from a different computer using a different application (ftp in the Terminal).

So… it's not the computer. It could be the router or my ISP. Now to figure out how to bypass the router! (I know how to do it; it's just that I have to crawl under some tight spaces.)

---

### Post by sudodus on 2013-02-17
Yes, sometimes is a almost like a plumber's job ;-)

---

### Post by Paddy Landau on 2013-03-17
I have found that this problem applies only to FileZilla.

If I connect using [FONT=lucida console]pftp[/FONT] from the command line in the terminal, everything works quickly and correctly.

That means that the problem lies specifically with FileZilla.

I have reset my FileZilla settings to the default, but that has not solved the problem.

Any ideas?

EDIT 1: It's not my firewall, as I've tested this with the firewall turned off.

EDIT 2: This seems to contradict [post=12515029]post #4[/post], but I found that using [FONT=lucida console]ftp[/FONT] (which uses active mode by default) was different from [FONT=lucida console]pftp[/FONT] (which uses passive mode). My FileZilla is indeed set to passive mode.

---

### Post by sudodus on 2013-03-17
I guess the problem is related to the handshaking of the program at your end of the line and with that of the ISP or the host computer somewhere in the internet. Will the connection behave differently with different host computers?

---

### Post by Paddy Landau on 2013-03-18
> **sudodus said:**
> Will the connection behave differently with different host computers?
Well, as described in the first post, the answer is yes and no. Yes: two different hosts both time out in exactly the same way. No: each host times out after its own number of bytes (but a consistent figure each time).

They both have the problem with FileZilla, yet both work properly with [FONT=lucida console]pftp[/FONT] in the terminal.

I'm trying to get hold of a third host to test against.

---

### Post by sudodus on 2013-03-18
I have to admit, that I don't understand why this would happen. Maybe you have to accept the work-around to use pftp instead of FileZilla.

- What happens if you browse to the host with Firefox or use Nautilus (File--Connect to server) and download files that way?

- Someone else (?!)

---

### Post by Paddy Landau on 2013-03-18
> **sudodus said:**
> What happens if you browse to the host with Firefox or use Nautilus&#8230;
I can browse there with Firefox, but I don't know how to upload using it.

With Nautilus, the process worked perfectly and quickly! So, Nautilus is easier than pftp; thank your for your suggestion.

I shall try the [FileZilla forums]("http://forum.filezilla-project.org/"). Someone there may have an answer. I'll post here if I find the solution.

EDIT: I have [posted the question]("http://forum.filezilla-project.org/viewtopic.php?f=2&t=29278") on the FileZilla forums. Let's see what happens.

---

### Post by sudodus on 2013-03-18
> **Paddy Landau said:**
> I can browse there with Firefox, but I don't know how to upload using it.
Neither do I, Firefox is only good for reading/downloading.> 
With Nautilus, the process worked perfectly and quickly! So, Nautilus is easier than pftp; thank your for your suggestion.
I'm glad you found a convenient and working solution :KS> 
I shall try the [FileZilla forums]("http://forum.filezilla-project.org/"). Someone there may have an answer. I'll post here if I find the solution.

EDIT: I have [posted the question]("http://forum.filezilla-project.org/viewtopic.php?f=2&t=29278") on the FileZilla forums. Let's see what happens.
Maybe you have found a bug ;-)

---

