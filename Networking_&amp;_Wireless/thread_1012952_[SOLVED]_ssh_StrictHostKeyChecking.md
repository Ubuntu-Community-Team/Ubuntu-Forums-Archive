---
title: "[SOLVED] ssh StrictHostKeyChecking"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by msewing on 2008-12-16
With ssh (hardy) to a remote host, I am getting login rejected because of Host ID change. (below)  Fine, I can edit my known_hosts, but I'd rather override this check.  In my .ssh/config I have "StrictHostKeyChecking no".  In /etc/ssh/ssh_config, it claims that the default is "... ask".  I also tried "ssh -o 'StrictHostKeyChecking no'", but same result.  ssh is behaving as if it is hardwired to "StrictHostKeyChecking yes".

What is wrong with this picture?

TIA - Martin

-----------
example:
~$ ssh -o "StrictHostKeyChecking no" [email]username@host.doma[/email]in
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
82:e7:bc:0c:6d:cc:3c:e2:c7:de:ee:2a:b2:af:31:f9.
Please contact your system administrator.
Add correct host key in /home/myacct/.ssh/known_hosts to get rid of this message.
Offending key in /home/myacct/.ssh/known_hosts:5
Password authentication is disabled to avoid man-in-the-middle attacks.
Keyboard-interactive authentication is disabled to avoid man-in-the-middle attacks.
Permission denied (publickey,gssapi-with-mic,password).

---

### Post by nixscripter on 2008-12-16
I've been frustrated by this myself. There is no way to make it allow you to type a password, since there is in fact a security risk -- however hypothetical it might be.

My solution is a bit of a hack, but give it a try. Make the known hosts file unwritable: ```
chmod -w ~/.ssh/known_hosts
```

Whenever you get the message, look at the line number in the file for the key, and delete it.

This will make "forget" the keys, and ask if they're okay every time, since it won't write them to the file.

It helps me, since I'm on a network with constantly changing IPs, and (at the risk of sounding geeky ;-) ) have learned to identify hosts by their key fingerprint.

---

### Post by nixscripter on 2008-12-16
I've been frustrated by this myself. There is no way to make it allow you to type a password, since there is in fact a security risk -- however hypothetical it might be.

My solution is a bit of a hack, but give it a try. Make the known hosts file unwritable: ```
chmod -w ~/.ssh/known_hosts
```

Whenever you get the message, look at the line number in the file for the key, and delete it.

This will make "forget" the keys, and ask if they're okay every time, since it won't write them to the file.

It helps me, since I'm on a network with constantly changing IPs, and (at the risk of sounding geeky ;-) ) have learned to identify hosts by their key fingerprint.

---

### Post by msewing on 2008-12-16
Thanks for the suggestion.  I suppose it would be one solution.

I'd like an answer to a specific question, though.  Which is true:

1.  Ubuntu's ssh overrides StrictHostKeyChecking preference expressed by user or by /etc/ssh/ssh_config.  This would be a lousy policy - especially if undocumented, or

2.  I am doing something wrong.

or perhaps both?

---

### Post by nixscripter on 2008-12-17
No, and no.

From the man page:
> 
ssh(1) obtains configuration data from the following sources in the fol&#8208; 
lowing order:

      1.   command-line options
      2.   user&#8217;s configuration file (~/.ssh/config)
      3.   system-wide configuration file (/etc/ssh/ssh_config)

For each parameter, the first obtained value will be used. 


So your user config file will override the system one.

As for the second one, you're not doing anything wrong. It's just the way strict key checking works. Again, from the man page:

> 
StrictHostKeyChecking

             If this flag is set to &#8220;yes&#8221;, ssh(1) will never automatically add
             host keys to the ~/.ssh/known_hosts file, and refuses to connect
             to hosts whose host key has changed.  This provides maximum pro&#8208;
             tection against trojan horse attacks, though it can be annoying
             when the /etc/ssh/ssh_known_hosts file is poorly maintained or
             when connections to new hosts are frequently made.  This option
             forces the user to manually add all new hosts.  If this flag is
             set to &#8220;no&#8221;, ssh will automatically add new host keys to the user
             known hosts files.  If this flag is set to &#8220;ask&#8221;, new host keys
             will be added to the user known host files only after the user
             has confirmed that is what they really want to do, and ssh will
             refuse to connect to hosts whose host key has changed.  The host
             keys of known hosts will be verified automatically in all cases.
             The argument must be &#8220;yes&#8221;, &#8220;no&#8221;, or &#8220;ask&#8221;.  The default is
             &#8220;ask&#8221;.


In other words, that nasty warning is always printed, and there are three options:

1. Yes -- make the user manage their own host keys file. If a key doesn't match, blindly refuse to connect.

2. No -- assume that changes in the host key file are a benevolent mistake if they don't match, and add new ones.

3. Ask -- ask the user every time between yes or no.

However, there is an additional footnote on "no", which is what you and I are running into. ssh assumes that there really, always, hypothetically could be a man-in-the-middle attack going on. As a result, **it will not allow you to authenticate with your user password if they key doesn't match**, just in case someone is watching. But, **it will allow other authentication methods, which are safer (see below)**. As far as I can tell, if you wanted to change that behavior, you'd have to patch the source of ssh.

A commonly used alternative authentication method is to use Public Key Authentication. This is a way of trusting you by which computer and user you are connecting from, instead of requiring you to type your password. However, be warned that it makes all logins automatic from your user to that user on your machine to that machine; if you are in a shared enviornment or paranoid, you might not want that. But if you set this up, and set *StrictKeyChecking* to *no*, it will warn you, and then let you in based on your other credentials.

Info on public key authentication can be found here: [http://sial.org/howto/openssh/publickey-auth/](http://sial.org/howto/openssh/publickey-auth/)

Hopefully, I have answered your questions.

EDIT: If you really wanted to be clever, you could change the authentication method order to create a rather interesting behavior: if the key did match, you could authenticate by password. If the key didn't match, you would get in automatically. It seems like you're making the worst case easiest from a security point of view, but if you don't care, you could do it. ;-)

SECOND EDIT: The instructions shown demonstrate that, actually, you **can** set a password to login if you set a password on the key. My assumption above assumes you chose an empty key password.

---

### Post by msewing on 2008-12-17
Nixscripter:

Thanks, you've explained it well.  I had recalled that a host switch to a new key was handled "correctly" (i.e., reported, but with known_hosts automatically updated) for me in the past, but now I realize I must have been using the public key method.

There must be a better way to manage host changes like this, but it seems we'd have to take it up with the ssh people.

Cheers

---

