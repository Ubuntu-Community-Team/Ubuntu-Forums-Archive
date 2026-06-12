---
title: "pandora over ssh"
date: 2013-05-24
forum: Multimedia Software
---

### Post by lister king of smeg on 2013-05-24
I often use pithos, a Pandora desktop client for Linux, to stream music to my ubuntu laptop (12.04 lts x86_64), my problem is though some overly enthusiastic net admin at my college has blocked all traffic to Pandora (as well as drop-box and a number of other sites I regularly use), they have not however blocked ssh. I have a Debain ssh server at home I use as a sftp/ssh server. I was wondering how I would go about tunneling my pithos clients connection over ssh? any help would be appreciated.

---

### Post by Lars Noodén on 2013-05-25
I can't really test Pandora because it won't let me sign up:

> 
We are deeply, deeply sorry to say that due to licensing constraints, we can no longer allow access to Pandora for listeners located outside of the U.S., Australia and New Zealand. We will continue to work diligently to realize the vision of a truly global Pandora, but for the time being we are required to restrict its use. ...


If you net admin is fine with SSH, there could be two possibilities.  However, without being able to try them, they are only guesses.  

One might be tunneling X.  That would allow the program to run on your remote Debian machine yet display locally on your desktop's X server.

```

ssh -X 192.0.43.10 /usr/bin/pithos

```

I'm not sure if that works with sound, too.  The down side is that tunneled apps can be a bit slow if the network is slow or has a lot of latency.

Another option, if Pithos supports SOCKS proxies, is to set up a proxy connection using ssh.  Then connect Pithos to the proxy on the localhost on the port you specify (e.g. 7890 below).

```

ssh -nNfD 7890 192.0.43.10

```

See the manual page for [ssh](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh.1.html) for more about those options.

---

### Post by lister king of smeg on 2013-05-26
I tried tunneling x over ssh and that didn't work the sound comes out over the speakers of the one you remoting into rather than the client. I read a bit about tunneling pulseaudio over ssh but its not that easy to do as pulse a pain to get working properly localy let alone remotely. I will have to try setting up a sock proxy as I have not tried that one yet.

---

### Post by lister king of smeg on 2013-08-22
I have found a solution to this problem. As Pithos does not support sock proxying I founda package call proxychains which forces all of a applications network traffic through a proxy set in its (proxychains) .config file. I set the proxy to 127.0.0.1:8888 [has to be 127.0.0.1 NOT localhost] then created ssh tunnel between my server and laptop (ssh -C -D 8888 user@server) then issue the command (in another terminal tab) "proxychains pithos". Pithos lauches and all traffic is proxied through the ssh tunnel to my server and around the horrible network firwall.

---

