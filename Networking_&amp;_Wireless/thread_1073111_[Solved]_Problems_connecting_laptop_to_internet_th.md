---
title: "[Solved] Problems connecting laptop to internet through desktop computer"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Irihapeti on 2009-02-18
I have set up a laptop to connect with my desktop by crossover ethernet cable. The desktop is connected to the internet with dialup. There is no hardware router involved. Both machines are running Hardy 386 version. The laptop is an EeePC 900 with the standard Ubuntu install plus a few tweaks to make things work - i.e. not a netbook remix of any kind.

Here's the issue: networking is only partly working. Both machines have static IPs. I have nfs enabled & I can access the desktop with it from the laptop. Each machine can ping the other. Firefox on the EeePc will connect with the internet without fuss if I use the auto-detect option, but nothing else will. I can get synaptic to connect by going to Preferences->Network, clicking on Manual proxy configuration, then Apply, then clicking on Direct connection, then OK. I have to do this each time I open synaptic, which is a bit of a hassle but better than not being able to update.

Everything else on the laptop refuses to play. Apt-get won't run from the command line without a "connection refused" error. Software update does the same thing, and so does wget. I've tried the proxy setup with and without authentification, and it seems to make no difference.

Now, I've never set up a server before and probably something hasn't been configured properly. Can someone point me in the right direction? Maybe I need to set up another package on the desktop so that the proxying works properly. Even a link to a "Servers for Dummies" kind of article would be helpful.

Irihapeti

---

### Post by dzark on 2009-02-18
Heya fellow kiwi,

Try this: [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by Irihapeti on 2009-02-18
That looks like a pretty long thread and a useful one - I'll read through it later. Thanks.

What part of NZ do you live in, by the way?

Irihapeti

---

### Post by Irihapeti on 2009-02-18
Update: The problem was with the laptop. I tried booting it from a live USB and everything worked fine.

I'm assuming that in all my floundering around (steep learning curve and all that) I've managed to corrupt something and it was trying to connect to the proxy in a way that the latter didn't like. So I'm reinstalling at the moment. A separate /home partition makes that reasonably pain-free.

The thread was an interesting read, anyway.

Irihapeti

Later:

No joy. The proxy connection worked long enough for me to run apt-get update. Now the problem is back again. I have no idea what I did to cause it. Here's part of the error message.

```
W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_NZ.bz2  Could not connect to 169.254.11.186:8080 (169.254.11.186). - connect (111 Connection refused)

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_NZ.bz2  Could not connect to 169.254.11.186:8080 (169.254.11.186). - connect (111 Connection refused)

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_NZ.bz2  Could not connect to 169.254.11.186:8080 (169.254.11.186). - connect (111 Connection refused)

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_NZ.bz2  Could not connect to 169.254.11.186:8080 (169.254.11.186). - connect (111 Connection refused)

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not connect to 169.254.11.186:8080 (169.254.11.186). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_NZ.bz2  Could not connect to 169.254.11.186:8080 (169.254.11.186). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

I've seen messages indicating that others have had similar problems. As I've said, I can ping various servers and mount nfs shares and browse with Firefox. Anyone know of any workarounds to this? It doesn't seem to be the desktop's problem.

---

### Post by Irihapeti on 2009-02-19
Found an answer that works for me.

I didn't need to set a network proxy at all on the laptop. Once I'd removed that and set it back to direct internet connection, everything worked.

I am guessing that the programs that were working even when the proxy was set, had another way of dealing with the access problem. Interestingly, cvs and svn worked, while wget and apt-get did not.

I have the desktop set up as per the instructions in the thread that dzark linked to, but I don't have ipmasq installed because I already had a firewall that did the same thing.

Hopefully, this might be useful to someone else who's dealing with the same thing.

---

