---
title: "Gadmin-OpenVPN-Server"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by Torxed on 2010-04-26
Hi.

Have some issues with Gadmin-OpenVPN-Server,
The application works rather well for most part, it generates the dh, ta, certs and config for the server and i can activate the VPN connection just as planed and clients can connect to the port so that works as well.

The problem comes when i try to use the "Export" button to generate a config for the client and a key (cert) for the user.
If i'm not mistaken that's what the export button is ment to be used for.

I get:
"Error: Could not copy certs to client folder"


[[img]http://i43.tinypic.com/zv4uxj_th.png[/img]]("http://i43.tinypic.com/zv4uxj.png")

---

### Post by Torxed on 2010-04-26
Didn't think an edit was in place since i'm posting on behalf of another support user and this is what i received in my mail today:

[INDENT]Hi, see if you can do this in a terminal window as root:

(Put these on the same line...)
cp /etc/gadmin-openvpn/server/certs/{cacert.pem,cert.pem,dh.pem,key.pem,ta.key}
  /etc/gadmin-openvpn/server/client/certs/

It should not say that a file is missing or show some other error.

If a file is missing you need to start gadmin-openvpn-server in a
terminal window as root and then generate new certificates and check for
any errors.

Let me know how that works and send error texts if any.[/INDENT]

---

### Post by DVN428 on 2011-04-01
Any updates on this?  I've tried executing the following in terminal as root and it worked out fine.  I'm just not sure why it doesn't work within the application.

```
cp /etc/gadmin-openvpn/server/certs/{cacert.pem,cert.pem,dh.pem,key.pem,ta.key} /etc/gadmin-openvpn/server/client/certs/
```

When I start Gadmin-OpenVPN-Server in terminal as root and press the "Expert" button the following error is displayed in terminal:
```
cp: cannot stat `/etc/gadmin-openvpn/server/certs/{cacert.pem,cert.pem,dh.pem,key.pem,ta.key}': No such file or directory
```

---

### Post by DeeNewcum on 2011-05-12
This workaround worked for me:

```
touch '/etc/gadmin-openvpn/server/certs/{cacert.pem,cert.pem,dh.pem,key.pem,ta.key}'
cp /etc/gadmin-openvpn/server/certs/{cacert.pem,cert.pem,dh.pem,key.pem,ta.key} /etc/gadmin-openvpn/server/client/certs/
```You have to run the second command every time, before you click the export button.

I'm not sure what's wrong here.  The tool is using popen() to try to run this command, but the shell-expansion isn't happening for some reason.

---

