---
title: "Connection to Ubuntu server freezes from public wifi"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by penakoski on 2012-05-07
Having little bit strange problem at hand, search didn't show any similar issues.

When opening SSH connection (using putty) to server, everything works normally. If I execute any command (example 'ls -al') that prints multiple lines of text, connection freezes immediately.

Same thing when trying to access to apache web server. Browser starts to load data but then it just stops. I took a trace and noticed that server sends 404 error when trying to load favicon icon (favicon.ico not found in server).

Again same thing with SFTP (WinSCP), connection is opened but it freezes when trying to fetch directory list.

DynDNS hostname is used (tried also with straight IP).

This whole thing is only happening when using one hotel wi-fi connection (Staying here quite long so this is quite annoying). If I go to any other internet hotspot, everything works normally.

I know there's definitely something wrong with hotel wi-fi but still I believe there's something that can be done in server side to prevent this? I mean I can access to other servers with no issues at all.

Thanks already.

---

### Post by penakoski on 2012-05-14
I have identified that SSH sessions hangs immediately when server sends "*too much*" data to my SSH client. Wireshark trace shows that when connection hangs, if I enter some commands in putty window, those are sent to server, but no answer is coming back.

Example if I run command '*ifconfig*' connection stays up, when running '*ifconfig -a*' it hangs immediately. Same thing example with irssi, if I decrease the size of putty window, I can open irssi screen, if size of window is "normal", SSH session hangs.

Some similar cases are reported, usually people have been talking MTU sizes, but really no final answer exist what's causing this.

---

### Post by roelforg on 2012-05-14
Idea:
Go to another place with internet and see if it works from there.
If not, it's a problem at your server internet connection
If it does, your hotel is giving you problems.

---

### Post by penakoski on 2012-05-14
Connection works normally from all other places. And I know there's something "wrong" in my hotel's connection. Strange thing is that I can connect other servers with SSH with no issues.
So there has to be something that can be done also in my server.

I was suspecting that there's some MTU problem but I can rule it out now, same MTU used in working and not working scenarios.

---

