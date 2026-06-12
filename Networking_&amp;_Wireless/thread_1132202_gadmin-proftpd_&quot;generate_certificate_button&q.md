---
title: "gadmin-proftpd &quot;generate certificate button&quot;"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by Ntr0s on 2009-04-21
Hey guys, I'm currently running a home business and FTP server  with vsftpd and SSL/TLS enabled and functioning very well. 

My previous FTP server was using proftpd with gproftpd, i but I could never get TLS/SSL to work with proftpd.

While I love the simplicity and stability of vsfptd, the lack of user / througput / upload - download monitoring tools is a little frustrating.  I'm using the VsFTPd Watcher sh script found here: [https://calomel.org/vsftpd.html](https://calomel.org/vsftpd.html)  and running tail command to view the vsftpd message log in real time.  The message log prints false errors from time to time related to download / upload failures, etc.  The VsFTPd Watcher script is great but limited.

I'm now looking at gadmin-proftpd.  I loved the proftpd user monitoring tools and I'm thinking of switching back to proftpd to use these tools. 

However, when I start gadmin-proftpd for the first time, it mentions "press generate certificate button" or something like that.  The problem is, I cannot find this certificate generating button anywhere.

a. Does this button exist in the latest gadmin-proftpd located b. in the repositories?
c. How does it generate certificates?
d. What does it do exactly?
e. Has anyone had success with this feature?
f. Do i need some sort of dependency installed to enabled the use of this feature?

I tried to email the gadmin-proftpd team, but all email fails to send from the developers site.

Thanks.

---

### Post by exploding5heep on 2009-06-11
If anyone knows the answer to this, I have the same exact question. I'm using 9.04-64, and installed using "sudo apt-get install gadmin-proftpd" earlier today. Does that install process skip installing the proftpd modules needed for encryption? Did you ever figure it out Ntr0s?

---

### Post by Steel Reign on 2009-06-11
I am also having the same problem. I have tried using gadmin with 7.10, 8.04, 8.10, and now 9.04 and I am never seen this elusive "generate" button. 

Now I did install Fedora 10 on a laptop that I had and I installed gadmin there and guess what. I saw the button and it worked perfectly fine.

So why doesn't the Ubuntu version have it? I rather use 9.04 then fedora.

---

### Post by Steel Reign on 2009-06-12
I guess no one knows the answer to this huh?

---

### Post by harmlessdrudge on 2009-07-20
I have tried and failed with this.

There is no generate certificate button that I could see.

You can find instructions on generating certificates in a variety of places, e.g.

For debian: [http://www.debianadmin.com/ftp-server-setup-with-tls-transport-layer-security-on-debian.html](http://www.debianadmin.com/ftp-server-setup-with-tls-transport-layer-security-on-debian.html)

For Ubuntu 8.10: [http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10](http://www.howtoforge.com/setting-up-proftpd-tls-on-ubuntu-8.10)

I have generated the certificate and key and then configured proftpd.conf accordingly (by editing the configuration using gadmin-proftpd) but the changes made don't seem to have any effect at all. This remained so after I discovered that I was putting keys in a different directory than indicated in the /etc/gadmin-proftpd/settings.conf file and then changed the configuration to follow that.

The directive TLSLog was ignored. In fact, I couldn't see that any changes made directly to the mod_tls.c section of the config file did anything.

It seems we have a choice between usage logging and security.

---

### Post by harmlessdrudge on 2009-07-20
Check this

[http://forums.proftpd.org/smf/index.php/topic,3957.0.html](http://forums.proftpd.org/smf/index.php/topic,3957.0.html)

It looks like a solution, or at least a diagnosis. I'll confirm later.

---

### Post by harmlessdrudge on 2009-07-20
Fixed.

See 

[http://forums.proftpd.org/smf/index.php/topic,3957.0.html](http://forums.proftpd.org/smf/index.php/topic,3957.0.html)

See also

[https://bugs.launchpad.net/ubuntu/+source/gadmin-proftpd/+bug/401803](https://bugs.launchpad.net/ubuntu/+source/gadmin-proftpd/+bug/401803)

---

