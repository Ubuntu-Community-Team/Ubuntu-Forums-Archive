---
title: "Is there a way to connect to windows remote desktop?"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by Jynks on 2010-11-09
is there any apps compatible with remote desktop? So my xubuntu system can connect to my windows system using the existing set up for remote desktop... or do I need to install a new client/server or thing on both systems? I do not mind doing that if you can recommend a good client/server but would prefer to just connect to the existing remote desktop if possible

---

### Post by |{urse on 2010-11-09
Applications -> Internet -> Remote Desktop Viewer (a.k.a. vinagre)

you'll need to be running a vnc server on the remote windows machine.

Works great though ^^

Edit: duh you said xubuntu srry

> sudo apt-get install vino

and then 

> vino-preferences

---

### Post by Jynks on 2010-11-09
but that needs a new server on the other system... it doesn't connect to the existing remote desktop setup?

---

### Post by Mze on 2010-11-09
Could [Teamviewer]("http://www.teamviewer.com/download/index.aspx") be a possible option?

---

### Post by |{urse on 2010-11-09
Yes, sorry I didnt read your post more thoroughly. What you want is called rdesktop.

> sudo apt-get install rdesktop

that allows you to connect via console.

for a gui install this.

> sudo apt-get install tsclient

It uses rdp, but it's a bit slower.

---

### Post by |{urse on 2010-11-09
Oh and check this out too.

[http://www.webrdp.com/webRDP/index.html]("http://www.webrdp.com/webRDP/index.html")

Not sure how free the liscenced v is but the free beta is here.

[http://www.webrdp.com/swreport/viewForm.jsp?encDNOfReport=ou%3DBetaRequestForm,o%3Dstoneware]("http://www.webrdp.com/swreport/viewForm.jsp?encDNOfReport=ou%3DBetaRequestForm,o%3Dstoneware")

---

### Post by Roasted on 2010-11-09
I like GnomeRDP in the software center.

---

### Post by Jynks on 2010-11-09
I'm sorry... mabey my wording was unclear or something...

I know there is a bunch of optons for setting up a remote desktop using various apps..

what I am asking is ... is there an linux app that can connect to the windows application by Microsoft CALLED remote desktop. I am not woundering about a client/sever app... there is NO WAY my boss will allow me to install a new ap on every system in the company. They all have remote desktop set up, as in the windows remote desktop.

I am asking if there is a linux app that can connect to that windows app.

---

### Post by |{urse on 2010-11-09
well the protocol invoked by "Remote Desktop" in windows is rdp. So yeah, the last few solutions mentioned _do not_ require you to install anything on the windows machines.

---

### Post by tomdkat on 2010-11-10
> **|{urse said:**
> well the protocol invoked by "Remote Desktop" in windows is rdp. So yeah, the last few solutions mentioned _do not_ require you to install anything on the windows machines.
Yep, I'm using rdesktop to connect to a Windows XP system right now.  I'm using the remote desktop function built-in to XP, no special software required on the Windows side at all.

Peace...

---

### Post by PhilGil on 2010-11-10
Don't forget remmina, as well. Our production environment is remote hosted via RDP. I've been transitioning some of my co-workers to Linux, and I'm using remmina as their RDP client as the look and feel is very similar to the Windows native client application.

---

### Post by |{urse on 2010-11-10
Yeah remmina! I couldnt remember the name of it thanks ^^

---

### Post by PhilGil on 2010-11-10
> **|{urse said:**
> Yeah remmina! I couldnt remember the name of it thanks ^^
You're welcome. The only thing I've noticed about remmina is that the remote session doesn't inherit the correct time zone when I use Lubuntu or Debian (I have to set it manually after I've logged in). It works fine in Ubuntu, however (maybe a Ubuntu-specific patch).

---

