---
title: "Can't connect to school network secured with WPA &amp; WPA2 Enterprise"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by PureTryOut on 2013-05-17
Using Ubuntu 13.04 I can't connect to my school network.
It is secured with WPA & WPA2 Enterprise and I have to enter my username and password school provided.
This does work on Windows 7, and it has worked with Xubuntu 12.10 in the past, but now it just won't connect.

Some screenshots of the errors:
The screen I have to enter my personal information
[IMG]http://i.imgur.com/0E1tmOC.png[/IMG]

Some kind of warning, I always choose ignore because I don't have any certificate authority file on my pc.
[IMG]http://i.imgur.com/MpXFjO0.png[/IMG]

When disconnecting from the network (even though it hasn't connected), and then reconnect without disabeling wireless
[IMG]http://i.imgur.com/B6jjD7f.png[/IMG]



So it tries to connect, and then just comes up with a screen in which I have to enter my password again. I enter my password and some time later the same screen pop-ups again.


**Edit: **Fixed
[COLOR=#000000] I made some screenshots in Windows of connection settings, and I found out Ubuntu tried to connect with the Tunneled TLS method, while Windows was connecting with Protected EAP.[/COLOR]
[COLOR=#000000]So I changed the connection to Protected EAP, entered my login, and it connected fine.[/COLOR]

---

### Post by PureTryOut on 2013-05-23
Is there nobody that knows what's wrong here? I now have to use Windows 7 every time on school just because the network is not working, even though I would like to use Ubuntu as much as I can.

---

### Post by SeijiSensei on 2013-05-23
Have you spoken to your school's IT department yet?  They are more likely to know the answer than we.

---

### Post by PureTryOut on 2013-05-24
Well the problem is they are not into Linux/Unix. My school is sponsored by Microsoft which means almost everything is Windows based.
Nobody could help me here.

---

### Post by praseodym on 2013-05-24
Off topic:

Therefore, your school is patronizing you and is dictating to the students which OS they shall use? Otherwise they are eliminating MAC- and Linux-users from network access? How much do they get from MS?

On topic: Ask the Windows users if they have the respective certificate on their computers and try to copy it.

---

### Post by Mark Phelps on 2013-05-24
You said in your first post that it works on Win7 -- then go into Win7 and see what the settings are for the CA certificate. You won't be able to connect without that.

---

### Post by PureTryOut on 2013-05-24
Could you explain to me how to do this? I don't have much experience with networking...

---

### Post by PureTryOut on 2013-05-29
OK in the meantime I fixed it myself. I made some screenshots in Windows of connection settings, and I found out Ubuntu tried to connect with the Tunneled TLS method, while Windows was connecting with Protected EAP.
So I changed the connection to Protected EAP, entered my login, and it connected fine.

Thanks for your help guys!

---

