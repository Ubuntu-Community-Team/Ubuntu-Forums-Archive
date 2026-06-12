---
title: "Can't build mplayer from source"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by SeijiSensei on 2010-09-29
Kubuntu 10.10 amd64 daily for 9/28

Just tried to build mplayer from source (something I've done in other releases) and got this

```

apt-get update returns:

Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Now try to get required source libraries, etc., to build mplayer:
apt-get build-dep mplayer

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_maverick_main_source_Sources - open (2: No such file or directory)

```

No sources available in extras?  Is this just a transitional thing that will be fixed when Maverick is released?

---

### Post by splicerr on 2010-09-29
Yeah, there's some bug in Maverick of not having the public key of extras.ubuntu.com. I ran into it myself when I wanted to install some build-deps I needed to compile some stuff from git. You can work around it with:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

```

---

### Post by SeijiSensei on 2010-09-29
Thanks!  Worked like a charm.

---

### Post by oguz_sert on 2010-09-30
> **splicerr said:**
> Yeah, there's some bug in Maverick of not having the public key of extras.ubuntu.com. I ran into it myself when I wanted to install some build-deps I needed to compile some stuff from git. You can work around it with:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

```

Thanks! Worked

---

### Post by oneofth3m on 2010-10-01
I ran into the same error when I try to compile libreoffice:


```
sudo apt-get build-dep openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_maverick_main_source_Sources - open (2: No such file or directory)

```

and the said workaround does not help. Although it looked like the import of key was successful..


```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: public key "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1

```

---

### Post by bruno9779 on 2010-10-01
what is the output of: sudo apt-get update ?

---

### Post by oneofth3m on 2010-10-01
Changed server source from India to Main, and it works.

---

### Post by keypox on 2010-10-07
> **splicerr said:**
> Yeah, there's some bug in Maverick of not having the public key of extras.ubuntu.com. I ran into it myself when I wanted to install some build-deps I needed to compile some stuff from git. You can work around it with:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

```

worked for me thanks.

---

