---
title: "ssh question"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by macey on 2010-05-29
Ok, I can set-up an ssh tunnel from machine A to Machine B:-

fred@my-linux:~$ ssh -P myport   [email]fred@myserver.homelinux.com[/email]

I can successfully logon to machine A to Machine B.

My question is,  at what address and port will my tunnel 'appear' on machine B?
I want to send a stream back from B to A up the encrypted tunnel, not over the open network. 


Help much appreciated.

---

### Post by wheredidrealitygo on 2010-05-29
You can use scp to do secure file copying.

```
scp /path/to/localfile -P [port] fred@myserver.homelinux.com:/path/to/remotefile
```

and it will be encrypted and go over the same ssh tunnel. hope this helps.

---

### Post by macey on 2010-05-29
> .......hope this helps.

Not really, but thanks anyway.
I want to stream (using VLC) from B to A. Need to know address and port on B.

---

### Post by wheredidrealitygo on 2010-05-29
Specifying things like playing a video with VLC would help, maybe be a bit more specific next time.

Try this from machine A: Go to Places, Connect to Server. Change the Service type to SSH, and put machine B as the server, put the port in and user name, then hit connect. It'll prompt for password. Then everything in that window will be encrypted, and if you open a video file from that window it will also be going over the encrypted ssh tunnel. Hopefully this is a bit easier.

---

### Post by macey on 2010-05-29
> **wheredidrealitygo said:**
> Specifying things like playing a video with VLC would help, maybe be a bit more specific next time

Thanks again, I think I have been very specific, I want to now how to get the address & port of my ssh tunnel at the B machine. I am fully familiar with your 'solution' which does not help me in this case.

---

### Post by macey on 2010-05-30
Think I've answered my own (stupid?) question.

On machine B :-
netstat |grep {ssh port}

---

