---
title: "SSH ssh_exchange_identification"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by PhilLord on 2012-08-13
I have recently upgraded to 12.04, and am now getting a very strange error. I cannot ssh into my desktop, unless I am already logged in. If I attempt to do so, I get "ssh_exchange_identification: connection reset by peer". 

Once I have logged into the machine (from the console), the ssh runs just fine, remote connections no problem. 

This is not a problem with the encrypyted home space (don't have them). I don't think it's a firewall problem (tried switching it off, no difference). 

This is a considerable problem because I used to wake-on-lan the machine, then connect from offsite. I can still wake-on-lan, but can't connect not even to shut the machine off again. 

Any help gratefully recieved.

---

### Post by Kirboosy on 2012-08-13
Are you sure that the keys didn't change when you upgraded? You may need to remove the known host file and retry to reconnect again.

Or maybe your ssh service doesn't start until the user is logged in. Did you install the openssh package?

---

### Post by asmoore82 on 2012-08-13
It sounds like Network-Manager is not connecting to the network until you log in. If you're using a "Server" variant then Network-Manager wouldn't be installed out of the box so that might blow this theory up.

---

### Post by PhilLord on 2012-08-13
> **asmoore82 said:**
> It sounds like Network-Manager is not connecting to the network until you log in. If you're using a "Server" variant then Network-Manager wouldn't be installed out of the box so that might blow this theory up.

Hmmm. Okay, so, officially, I now feel stupid. I had checked everything else, but not that logging in would actually cause the network to come up. 

Clicking on "Available to all users" on the eth0 configuration GUI seemed to solve the problem; I am a little surprised, because even logging into a console (clt-alt-F1 virtual terminal) let me ssh in, so it's I figure it was before gnome had any control. 

Still, finding out exactly why the 12.04 upgrade did this is probably not going to help me! Thanks very much for the suggestion, I'd already lost a lot of time over this and was starting to tear my hair out. Not good, as I am already mostly bald. 

Phil

---

