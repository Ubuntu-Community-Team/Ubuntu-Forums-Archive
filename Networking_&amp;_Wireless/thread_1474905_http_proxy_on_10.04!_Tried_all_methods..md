---
title: "http_proxy on 10.04! Tried all methods."
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by akhilbehl on 2010-05-06
Ok.. so this is really weird.

On ubuntu 10.04, I just can't get apt-get to work on the terminal behind the proxy here. The weird part is that this has just happened in 10.04.

I am something like the Linux-help around my campus, and since lucid has come out I have installed it in 5 different machines on which one was an upgrade.

Inevitably, on each of the machines the proxy is not working. Even on the one that was upgraded, it was working just before the upgrade and not after.

I have always used this method for the proxy:

Add to .bashrc and bash.bashrc:

export http_proxy="http://username:password@host:port/"

Add to /etc/apt/apt.conf: 

Acquire::http::proxy "False";

I have also tried changing "False" to direct, and also removing the file itself.

and this has _always_ worked. But now it is not working on any of the 5 machines I know.

The funnier part is that in these 5 installs, one of them was a beta2 install, 4 of them were i386 and one was a 64 bit arch, and all of them are giving the same problem, even though these 5 installs were from 3 different isos.

I have tried all sorts of hacks. Adding the http_proxy variable to the .profile and /etc/profile, /etc/environment. Even in GConf values. And it would still not work. Funny thing is that it is still working on my Arch box, that I use for my regular work using the same configuration.

Any ideas on what could be going on here?

I tried googling it but seems like this is happening only with me because nobody else seems to be complaining.

---

### Post by myk.dinis on 2010-05-06
Have you tried editing the settings under System > Preferences > Network Proxy?

I apologize if you have.  And be sure to apply system wide...

The only reason I ask is because a lot of normal locations for these type of settings get changed every-so-often in Ubuntu. Like menu.lst, etc...


Cheers!
-myk

---

### Post by akhilbehl on 2010-05-07
thanks for replying dude.. but yes I have. :( A little disappointing to see that after 40 views, nobdody has any idea why this might be happening. And nor do I anymore.

---

### Post by industrai on 2010-05-13
same problem here.. the only way i've been able to get this to work is:
```
sudo -s
export http_proxy=http://myproxy.com:8080
apt-get update
...yada yada
```

it seems that sudo doesn't recognize export http_proxy, whereas in 9.10 it did.  weird.

---

### Post by Pureferret on 2010-05-19
Hi guys, I have a similar problem (identical to the OP's) except that the the sudo trick does nothing.

I've checked the password in synaptic is the same as in my $http_proxy variable.

Any solutions?

Also something wrong with GPG(whatever that is!), tried following this: [http://systembash.com/content/apt-get-update-gpg-key-errors-and-fix](http://systembash.com/content/apt-get-update-gpg-key-errors-and-fix)

But to no avail!
```
root@Geantuser:~# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 313D312748A22A95; gpg --export --armor 313D312748A22A95 | sudo apt-key add -
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 313D312748A22A95
gpg: requesting key 48A22A95 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: directory `/home/geantuser/.gnupg' created
gpg: new configuration file `/home/geantuser/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/geantuser/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/geantuser/.gnupg/secring.gpg' created
gpg: keyring `/home/geantuser/.gnupg/pubring.gpg' created
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
```I edited the conf file to include the valid http_proxy(http-proxy as it's listed in the file) resulting in:

```
root@Geantuser:~# sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 313D312748A22A95; gpg --export --armor 313D312748A22A95 | sudo apt-key add -
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 313D312748A22A95
gpg: requesting key 48A22A95 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
gpg: /home/geantuser/.gnupg/gpg.conf:138: invalid option
gpg: no valid OpenPGP data found.
root@Geantuser:~# exit
exit
```

---

