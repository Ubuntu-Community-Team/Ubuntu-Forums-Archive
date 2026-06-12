---
title: "VPS Refusing Key from Putty"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by th3ant on 2013-02-07
Not to sure if this is the right place to post this, let me know if I'm wrong. I'll try to go through this as quickly as possible to save your time:

[LIST]
[*]I have an Ubuntu 12.04 LTS VPS and am using ssh to connect to it.
[*]I have generated a 4096 bit SSH-2 RSA key for it with puttygen.exe and am using it within putty to connect to the server (From Windows 8 Pro).
[*]I connect with the IP and customised Port - which has been allowed in the VPS firewall - and the server has the correct public key in the default "~/.ssh/authorized_keys" file.
[*]I connect through and type in my username, and then it says "Server Refused Our Key".
[*]As the moment I now have to type my password as I have set the VPS so that I can log in without key, just VPS user credentials. Obviously I will want to remove this and make it use the key, Any Ideas?
[/LIST]


And the reaally weird thing is, if I then "Duplicate" the putty session (go to Menu -> Duplicate Session) and then log in, the key is accepted, even though the key didn't work a minute before on a brand new session! What could be going wrong?

---

### Post by steeldriver on 2013-02-07
Hello and welcome

How did you transfer the public key from puttygen to the remote host's authorized_keys file? There's a quirk with the key format which basically means you need to copy / paste the literal key from the top pane of the puttygen window - NOT use the 'Save public key' file (which is in the wrong format for openSSH)

Alternatively I believe you can use ssh-keygen on the remote host to convert the format

---

### Post by th3ant on 2013-02-07
Hi there,

Yes, I did copy the key from the puttygen program window, and copied it across via an original insecure default ssh connection.

I know the key works - or appears to work - as I said when I duplicate the session it works perfectly. Could it be a putty/ssh-server problem maybe?

---

### Post by SeijiSensei on 2013-02-07
It might be the old Unix vs Windows [line-terminator problem]("http://manpages.ubuntu.com/manpages/natty/man1/fromdos.1.html").  Try copying the key by highlighting it with the mouse up to and including the last character then pasting it into the remote authorized_users file.  Hit a return after pasting.

I don't think it matters if there are extraneous blank lines in authorized_users, but it doesn't hurt to remove them.

---

### Post by th3ant on 2013-02-08
Sorry, Still a bit new to the whole Linux command line interface so please bear with me..

I did as you suggested SeijiSensei, pasting in the code from the puttygen window and adding a new line and then saving. 

I still have the same problem that I had before.. "Server refused our key." on the first log in. If I keep that window open and then open another session with exactly the same details I get a "Authenticating with public key "rsa-key-20130206"" which is what it is meant to do!

---

