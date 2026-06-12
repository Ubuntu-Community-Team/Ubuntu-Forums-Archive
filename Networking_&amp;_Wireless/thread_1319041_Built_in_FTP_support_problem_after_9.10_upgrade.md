---
title: "Built in FTP support problem after 9.10 upgrade"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by XeroXer on 2009-11-08
Hi all!

Did an upgrade from my 9.04 laptop to 9.10 last weekend, and have had a few problems since.
Waited a while with posting to see if an update or anything fixed the problem, but no luck.

I work with PHP programming and I am using geany as a lightweight IDE.
Only one thing missing, a better file browser with FTP support and the possibility to create files and folders, but that's another problem.
Since geany has no built in FTP support I use the "Connect to Server..." under the "Places" menu and browse the sites that way.

The problem is that since my upgrade to 9.10 this has not been working as great as it did.
If I don't use the connection for a short while it all of a sudden disconnects and if I try to open it I get a message saying:
**The folder content could not be displayed.**
Sorry, could not display all the contents of "/ on xxx.xxx.xxx.xxx": Host closed connection.

The shortcut to the connection remains on my desktop and in the "Places" menu but it doesn't work.
I get the same problem inside geany, so all of a sudden I can't save files or browse the server.
If I wait a few seconds it reconnects to the server but still it's annoying and takes up extra time.

I know the problem is not on the server side since it's my server and I have made no changes during the time period. And it still works great on my 9.04 computer.

As I see it this seems like a timeout problem but I had no such problem before the upgrade.
If anyone has any ideas on how to solve this problem I would appreciate it.

---

### Post by robwgibbons on 2009-11-12
I am having the exact same issue, and have not yet found any resolution. I use Nautilus almost every day, due to its convenient integration with the desktop (it makes for a nice, simple FTP client).

When I am connected to my FTP server, or a client's FTP server, if I remain inactive for a period of time longer than a few minutes (I'm not sure exactly how long it takes until the timeout occurs) and then attempt to upload or make alterations, I receive an error reading "Host closed connection."

My best guess is that some alterations were made to the default session timeout, and Nautilus is no longer maintaining a persistent connection to the FTP server.

I am not sure if there is a fix for this issue, or a simple means of reconfiguring Nautilus to restore the old functionality of maintaining a persistent connection to FTP servers. So far my only resolution has been to refresh the connection to the server a few times, which reestablishes the connection once again.

I would appreciate if anyone can offer any insight to this particular problem, as I use Nautilus nearly every day for my FTP needs, and would really love to not have to switch to another client.

---

### Post by lensman3 on 2009-11-12
I don't use ftp, but my ssh and sftp clients timeout.

Sounds like something changed down it the ip stack.

Sorry I don't have a fix and setting "keep alive" doesn't seem to work.

---

### Post by XeroXer on 2009-11-13
Still have the same problem but thought I'd share my temporary solution.

```
sudo apt-get install curlftpfs
```

```
vim ~/.netrc
```

```
machine ftp.example.com
login user
password pass
```

```
chmod 600 ~/.netrc
```

```
mkdir ~/ftp.example.com
```

```
sudo curlftpfs ftp.example.com ~/ftp.example.com -o allow_other -o uid=500
```

This mounts the saved ftp login on ~/ftp.example.com and I haven't noticed any timeout problem or anything. And it works better since it also creates thumbnails for images on the ftp server.

If anyone need any help with setting curlftpfs up just say so...

---

### Post by tg_nightnight on 2009-11-24
Thanks XeroXer for an old cookie cutter alternative that works, but this still does not address a solution for the case of built in nautilus-ftp support.

In 9.04, if a ftp connection timed out, it would automatically reconnect before modifying the file on the ftp server.
9.10  doesn't automatically reconnect and requires a manual reconnect (like refreshing the nautilus window) and so errors are thrown if you try to modify a file after the connection has been timed out.

Is there some config file somewhere that can make it automatically reconnect again?  Some variable that used to be true but is now false?

---

### Post by tim_bobo on 2009-11-25
I'm having the same problem...any progress?

(There appears to be a bug reported: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/410288](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/410288))

---

### Post by ambrosa on 2010-05-02
Also 10.04 has the SAME PROBLEM !!!!

Grrrrrrrrrrr

Very very very disappointed !!!

---

