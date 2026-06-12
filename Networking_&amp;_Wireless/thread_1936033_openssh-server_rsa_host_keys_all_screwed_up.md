---
title: "openssh-server rsa host keys all screwed up"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by deckerry on 2012-03-05
My once working ssh connection now fails every time.

I don't even know what the heck happened. One thing that I remember is that I set a static ip on my server after I setup ssh and remotely ssh-connected to it.

Oh and there is no .ssh folder so I have no idea what the heck is going on.

I've been looking on the internet and trying things that don't work for hours.

OMG I DON'T KNOW WHAT TO DO! PLEASE HELP ME!

Here is the error message:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:3
RSA host key for xxx.xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.

```

AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA!!!!!!

---

### Post by DrPotoroo on 2012-03-05
At some time you have SSHed to another computer that had the same IP that the server you are connecting to has now. So the fingerprint of your server does not match the fingerprint expected for that IP - at least, that's how I think it works.

Delete line three in the .ssh/known_hosts file (on the machine you are connecting FROM). The ':3' in the error message tells you that the third line is the one with the offending IP/fingerprint combination. You can't tell by looking at the file, because it is encrypted. Then try connecting again. If that doesn't work, you can try renaming the known_hosts file, or deleting it. If you rename/delete it then every time you SSH to something the first time you will get the 'are you sure?' message again.

---

### Post by deckerry on 2012-03-05
OMG. You know what? I've been trying for hours to do this ON THE WRONG COMPUTER!!!!

Please, please smack me in the face - really freakin' hard. I have read similar instructions on the net over and over and couldn't figure out why it didn't work.

It's cause you need to do it from the NOT-SERVER-COMPUTER.


DrPotoroo,

Thank you!!!
Thank you!!!
Thank you!!!
Thank you!!!
Thank you!!!
Thank you!!!
Thank you!!!
Thank you!!!

---

### Post by oldgeekster on 2012-04-19
> **DrPotoroo said:**
> At some time you have SSHed to another computer that had the same IP that the server you are connecting to has now. So the fingerprint of your server does not match the fingerprint expected for that IP - at least, that's how I think it works.

Delete line three in the .ssh/known_hosts file (on the machine you are connecting FROM). The ':3' in the error message tells you that the third line is the one with the offending IP/fingerprint combination. You can't tell by looking at the file, because it is encrypted. Then try connecting again. If that doesn't work, you can try renaming the known_hosts file, or deleting it. If you rename/delete it then every time you SSH to something the first time you will get the 'are you sure?' message again.Thanks for the reminder DrPotoroo - did a fresh install on the wife's notebook, wanted to re-establish SFTP with it from mine and got the heinous validation failure indication. Renamed the known_hosts file and all was well after that. :cool:

---

