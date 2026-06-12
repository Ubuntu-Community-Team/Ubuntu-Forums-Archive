---
title: "SSH With Multiple Users."
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by Roasted on 2012-02-20
Since moving out, I'm trying to find a way to route backup traffic from my parents and brothers computers over to my file server, despite the fact it is no longer on the LAN. I have a DNS domain name set up, SSH forwarded, file server ready to go. But I'm trying to understand SSH a bit more before I go forward, as I want it to be as secure as possible. I'm curious if you guys could elaborate on a few key points to help me better understand the SSH process, private and public keys, multiple user setups, etc.

File Server - Ubuntu 11.04 - Users are Administrator, Bob, Frank, Bill, John. Administrator stays logged in 247. User accounts exist for Bob, Frank, Bill, and John because when I lived at home, they would just auto mount Samba shares for their respective accounts and back up automatically there, requiring zero input from user. Since we're dealing with a WAN now, Samba becomes more difficult, hence SSH.

The clients include an array of Ubuntu, Windows XP, and Windows 7 clients. To keep it simple, let's just work with Ubuntu vs Ubuntu only. The clients however are on 11.10.

So I run ssh-keygen and I get a public and private key. Okay, great. The private key is supposed to go to the client, whereas the public key stays on the server. From what I understand, I am to take the contents of the public key and copy it into a document called authorized_keys, which resides in ~/.ssh. I paste the contents in there from the public key. At this point, I understand I am good to go.

But wait. What .ssh folder are we dealing with? Should I be pasting it in /bob/.ssh, /frank/.ssh, and every other user's home dir .ssh? Or should I be pasting this into /administrator/.ssh only?

On top of that, let's say I correctly set up a key pair. Things are good, private and public is set. Then, I ssh into my server. The first time I connect, is it a red flag that I did not set up something correctly if it is prompting me yes or no to continue logging in? I was under the impression if I set it up right, I wouldn't get prompted. What do you guys think?

Any other help would be huge. I find this SSH thing to be really simple, but when I Google around I'm left with some questions in regard to managing the multiple SSH keys and where they should reside for optimum organization/security.

---

### Post by Perkins on 2012-02-21
Ok, to start with, there are multiple sets of keys.  Set number one is to identify the server.  That is the source of the message you get when logging in the first time.  The key for identifying the server isn't on record, so the SSH program prints it out so that you may verify that it is correct.  If you're sure it's correct, then tell it to go ahead and connect.  It will store the server's public key so that later, if somebody tries to play man-in-the-middle with your communications, you'll know.

The public key for keypair authentication goes into the ~/.ssh/authorized_keys file of the user for which you wish to use said keypair.  The ssh-copy-id program will take care of the details for you, and is the recommended way to install the key on the server.  (Just so you know, when dealing with most *NIX a ~ in a path refers to the current user's home directory.)

It is generally a good idea to use separate keys for separate users since otherwise they could all gain access to each other's stuff just by changing their login name.  If that's what you want, it's still usually better to simply set the file permissions properly.  Otherwise you might as well use only one account.

As always, when configuring automatic logins, you should really only be able to go from more secure machines to less secure machines (or, possibly, between equally secure machines) without a password.  Otherwise, somebody who compromises your least-secure machine can easily gain access to your supposedly more-secure machine.  You're only as secure as the weakest link in the chain.  If the data you're storing is sensitive in any way, then any machines that can log in automatically should be physically secured against theft, and any which cannot be so (read: laptops that you carry around) should have their drives encrypted.  Furthermore, if any machine is even suspected of having been compromised, the first thing to do is to remove its key from the authorised_keys file and generate a new one once you're sure the machine is secure again.

---

### Post by Roasted on 2012-02-21
Thank you for that information. I have heard of the ssh-copy-id but I was not aware that command automatically did the key transfer. I'll have to look it up and see how it's utilized, because when I did run across it I remember thinking it was rather confusing.

Also, are SSH keys *always* stored in a users home directory? Or is it ever stored somewhere else on the system, like /etc/ssh or something? Just curious if it's always a must or if there's other options as well.

EDIT - Now, can you run through a basic synopsis of the process behind this?

Like:

ssh-keygen (creates two key pairs, I create a password, etc.)

Then what? Do I copy the key anywhere? Or do I just leave the computer on my laptop and say ssh-copy-id jason@desktop to copy it to my desktop? Is that how it works?

---

### Post by roelforg on 2012-02-21
No like this; worked for me and my home server (i setup dns so my homeserver is server.local)
 
Server (for every user, log in as that user):
```

ssh-keygen
#hit enter, defaults are fine; even the blank pass as were gonna overwrite this

```
Try sshing in from your pc for every user, if it works then continue with these steps:
Client pc (for every user, log in as that user):
```

ssh-keygen
#just hit enter, defaults are fine; entering a password here will prompt the client for it each time and that's not what we want
ssh-copy-id <username>@<remote server>
#type yes when asked to accept the signature/cert; enter password for account on server

```
Note: you've gotta enter the pass once so the pc can log in once to copy/exchange certs; it won't ask again and is completely safe as the certs are only valid as long as their sigs match those generater on login; it's completely safe
 
Thanks to ssh's build in security this should be fine as long as you're not gonna transfer creditcard data over the connection (i advise only doing that if you've got certs issued by a CA and your security is like a black box; but that's really overkill for the everyday user and (unless you're a big corp or the gov) way to expensive/time consuming).
 
Good luck,
feel free to pm me if you've got more questions.

---

### Post by Lars Noodén on 2012-02-21
For user authentication, the keys always go in ~/.ssh/ unless the server has been configured to look elsewhere.  If you do host-based authentication then you can use keys put in /etc/ssh

I put up a description of which file go where in a wikibook on OpenSSH:
[https://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files](https://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files)

---

### Post by Roasted on 2012-02-21
So let's say this... I have a laptop and a server. I'm on my laptop and I want to create a key pair between the laptop and server.

On laptop: ssh-keygen
On laptop: ssh-copy-id jason@server

This thereby takes the public key and dumps it in the server. Correct?

Does the ssh-copy-id only do public keys? Or private keys as well?

Am I to always initiate the key pair physically on the client? (i.e. laptop in this case) Or am I doing it backwards and should be doing it from the server?***

*** if this is the case where I am supposed to initiate the key copy from the client, couldn't anybody anywhere just initiate a key pair and push it to the server? 

Also, does ssh-copy-id pose risk to "man in the middle" attacks?

Lastly, is all of the above using SSH1, or SSH2?

---

### Post by roelforg on 2012-02-21
> **Roasted said:**
> So let's say this... I have a laptop and a server. I'm on my laptop and I want to create a key pair between the laptop and server.

On laptop: ssh-keygen
On laptop: ssh-copy-id jason@server

This thereby takes the public key and dumps it in the server. Correct?

Does the ssh-copy-id only do public keys? Or private keys as well?

Am I to always initiate the key pair physically on the client? (i.e. laptop in this case) Or am I doing it backwards and should be doing it from the server?***

*** if this is the case where I am supposed to initiate the key copy from the client, couldn't anybody anywhere just initiate a key pair and push it to the server? 

Also, does ssh-copy-id pose risk to "man in the middle" attacks?

Lastly, is all of the above using SSH1, or SSH2?
SSH2 is always default; only when the client doesn't support SSH2 (think people who haven't updated in 5-10 years) it'll use SSH1.

Let me explain what ssh-copy-id does:
It'll find your priv/pub keys (client) and use SCP to copy them to the server (look SCP up if you want to know more); but you'll need to run ssh-keygen first to generate the keys on the client and run it on the server so the SCP connection is secure (otherwise the SSH server won't let you connect)

Given the fact that ssh-copy-id is only run once and uses the SSH protocol for transfers; it's as safe as SSH is.

Like i said; do it once, be done with it.

Example (as you don't trust us): My home server (works to from my friends house to my server in my house):
Logged in as my account on my server and ran:
```

ssh-keygen
#just pressed enter for every question

```Now to my pc (server.local=dns for my home server):
```

ssh-keygen
#again, just pressed enter
ssh-copy-id `whoami`@server.local
#told it to accept the signature and entered my pass
ssh server.local echo "Works!"

```The last command will log in and tell the server to echo "Works!" over the connection; worked great!
Now when i type:
ssh server.local
It'll give me my shell w/o asking for passes; try the same from my other pc (same user account names); asked for pass, like it should as i didn't do the key based auth setup on it.
FYI: the account name on the server must be the same at the one local, it's easier.
IIRC it only copy's the public key.

Let me give pub./priv. key encryption 101 to you:
anything encrypted with the public key can _only_ be decrypted with the private key from the pair.
> **Wikipedia]
The two main branches of public key cryptography are:
 
[LIST]
[*]Public key encryption: a message encrypted with a recipient's public  key cannot be decrypted by anyone except a possessor of the matching  private key — it is presumed that this will be the owner of that key and  the person associated with the public key used. This is used for [confidentiality]("http://en.wikipedia.org/wiki/Confidentiality").
[*][Digital signatures]("http://en.wikipedia.org/wiki/Digital_signature"):  a message signed with a sender's private key can be verified by anyone  who has access to the sender's public key, thereby proving that the  sender had access to the private key (and therefore is likely to be the  person associated with the public key used), and the part of the message  that has not been tampered with. On the question of [authenticity]("http://en.wikipedia.org/wiki/Authentication"), see also [message digest]("http://en.wikipedia.org/wiki/Message_digest").
[/LIST]
 An analogy to public-key encryption is that of a locked [mail box]("http://en.wikipedia.org/wiki/Letter_box")  with a mail slot. The mail slot is exposed and accessible to the  public said:**
> wax seal[/URL]. The message can be opened by anyone, but the presence of the seal authenticates the sender.
 A central problem for use of public-key cryptography is confidence  (ideally proof) that a public key is correct, belongs to the person or  entity claimed (i.e., is 'authentic'), and has not been tampered with or  replaced by a malicious third party. The usual approach to this problem  is to use a [public-key infrastructure]("http://en.wikipedia.org/wiki/Public_key_infrastructure") (PKI), in which one or more third parties, known as [certificate authorities]("http://en.wikipedia.org/wiki/Certificate_authority"), certify ownership of key pairs. [PGP]("http://en.wikipedia.org/wiki/Pretty_Good_Privacy"), in addition to a certificate authority structure, has used a scheme generally called the "[web of trust]("http://en.wikipedia.org/wiki/Web_of_trust")",  which decentralizes such authentication of public keys by a central  mechanism, substituting individual endorsements of the link between user  and public key. No fully satisfactory solution to the public key  authentication problem is known.

Now don't let the last paragraph scare you; with the key based auth method: the server and client already have eachothers keys, so only once for the max period of 3s will there be any chance for figuring this out. That period is so tiny that it's security impact is miniscule. Especially given that that 3s period is while copying the keys when setting up; because that's the only time when the server and client exchange keys (until either of them runs ssh-keygen again, than again will keys be exchanged, but that, again, is ignorable).

---

### Post by Roasted on 2012-02-21
> **roelforg said:**
> 
Let me explain what ssh-copy-id does:
It'll find your priv/pub keys (client) and use SCP to copy them to the server (look SCP up if you want to know more); but you'll need to run ssh-keygen first to generate the keys on the client and** run it on the server **so the SCP connection is secure (otherwise the SSH server won't let you connect)


I just tried to ssh-copy-id me@domain and it timed out. Then I checked here and found your response. This section quoted above caught my eye and I wondered if it could be related to why I'm timing out.

Are you saying I need to run ssh-keygen on the server and client? I know I do it on the client, but server too? That to me suggests I would have two SSH key pairs, which is more than I would need (unless I'm missing a key point). I guess I'm asking what you were referencing when you said "it" in the bold text.

Thanks again!

---

### Post by Lars Noodén on 2012-02-21
> **Roasted said:**
> So let's say this... I have a laptop and a server. I'm on my laptop and I want to create a key pair between the laptop and server.

On laptop: ssh-keygen
On laptop: ssh-copy-id jason@server

This thereby takes the public key and dumps it in the server. Correct?

Does the ssh-copy-id only do public keys? Or private keys as well?


ssh-copy-id only copies the public keys.  It does not matter where the key pairs are generated as long as they are handled securely.  On the server you are logging in to, the keys will be in [font=Courier New]~/.ssh/authorized_keys[/font] but on the client you are logging in from, they will be in a separate file.

If you might have several keys on the client for different servers or different activities, you can always give them different names to keep them straight.

```

ssh-keygen -f jason_server1_id_rsa -t rsa

```

A good place to keep them on the client is in [font=Courier New]~/.ssh/[/font]

> **Roasted said:**
> 
Am I to always initiate the key pair physically on the client? (i.e. laptop in this case) Or am I doing it backwards and should be doing it from the server?***

*** if this is the case where I am supposed to initiate the key copy from the client, couldn't anybody anywhere just initiate a key pair and push it to the server? 

Also, does ssh-copy-id pose risk to "man in the middle" attacks?

Lastly, is all of the above using SSH1, or SSH2?

There is no MITM risk unless connecting for the first time.  Then be sure to verify the server key fingerprint if it was not pre-loaded.  [ssh-copy-id](http://manpages.ubuntu.com/manpages/oneiric/en/man1/ssh-copy-id.1.html) is a shell script that uses ssh and cat to append the public key to [font=Courier New]~/.ssh/authorized_keys[/font] on the remote host.  As such, it is as secure as can be.  

Everything should default to SSH2.  Don't use SSH1 any more, but you'd have to go out of your way to use it nowadays.

---

### Post by roelforg on 2012-02-21
> **Roasted said:**
> I just tried to ssh-copy-id me@domain and it timed out. Then I checked here and found your response. This section quoted above caught my eye and I wondered if it could be related to why I'm timing out.

Are you saying I need to run ssh-keygen on the server and client? I know I do it on the client, but server too? That to me suggests I would have two SSH key pairs, which is more than I would need (unless I'm missing a key point). I guess I'm asking what you were referencing when you said "it" in the bold text.

Thanks again!

Wild guess,
ping the server, check your firewall, check if you can login via ssh normally.

Note: my ssh server won't let me login unless both server and client have ran ssh_keygen once.

---

### Post by Lars Noodén on 2012-02-21
> **roelforg said:**
> 
Note: my ssh server won't let me login unless both server and client have ran ssh_keygen once.

Something's not quite right.  That will give you an extra, redundant key pair that will sit around unused.  It doesn't matter where the keys pair is generated as long as the private key ends up on the client machine and the public key ends up on the server machine.  Usually people also keep a copy of the public key along with the private key on the client machine.

---

### Post by matt_symes on 2012-02-21
Hi

Stating the obvious, but when you have set up keys and you are confident they are working, log into the server if at the client or locally if at the server, and edit sshd_config file.

Disable password log in and then restart the SSH service on the server.

*Backup your key files*

Kind regards

---

