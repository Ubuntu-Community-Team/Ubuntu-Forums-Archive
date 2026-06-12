---
title: "Samba doesn't work"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by Shotokax on 2009-09-05
Hello, everybody.

I don't know what to do to make Samba work. I've tried a lot of things but finally I've decided to delete all and configure only the basics.

I've two machines with Jaunty Jackalope: a client and a server.

In the client I've only modified these lines in smb.conf:

```
workgroup = CASA
``````
security = SHARE
```I've not installed anything, Samba client is installed by default if I don't mistake.

In the server:

```

sudo aptitude install samba samba-client smbfs smbclient
chown -R root:root /home/public
```I've also modified smb.conf like in the client and I've shared /home/public with Nautilus (as root) enabling all options and I don't get any error message.

I've rebooted both machines several times too.

Does somebody have any idea?

Thank you very much.

---

### Post by Iowan on 2009-09-05
May need to re-think the client/server relationship.  The _server_ would have the security setting and the shares.

---

### Post by theozzlives on 2009-09-05
the only thing I've EVER had to do is change the workgroup, then:
```
sudo apt-get install samba
```
then:
```
sudo smbpasswd -a <your username>
```
it'll ask for your password twice then you should be set to do your shares.

---

### Post by theitspecialist on 2009-09-06
run the update manager make sure the system is up to date than install system-config-samba from the synaptic package manager or sudo apt-get install system-config-samba in a terminal its a visual samba configuration tool that should work

---

### Post by jobst on 2009-09-06
> **Shotokax said:**
> Hello, everybody.

I don't know what to do to make Samba work. I've tried a lot of things but finally I've decided to delete all and configure only the basics.

snip

Does somebody have any idea?

Thank you very much.

If you go here [in case you are impatient ;-)]

   [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html)

It explained well.

jobst

---

