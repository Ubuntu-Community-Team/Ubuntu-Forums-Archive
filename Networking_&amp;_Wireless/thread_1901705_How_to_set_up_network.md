---
title: "How to set up network"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by Big_Lebowski_2009 on 2011-12-29
Hi all.

I have two laptops with xubuntu 10.04 on both, I set up wi-fi connection on first laptop and second one, but I they can't see each other, in Gnome there is network in nautilus, but in Xfce thunar doesn't have network in leftbar.

How can see one laptop from anither?

Thanks in advance.

---

### Post by nothingspecial on 2011-12-29
Hi, make sure you have these packages installed
```

sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse
```

Then restart thunar. You should see at network option.

---

### Post by Big_Lebowski_2009 on 2011-12-29
> **nothingspecial said:**
> Hi, make sure you have these packages installed
```

sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse
```

Then restart thunar. You should see at network option.

Thanks nothingspecial, 

I installed gvfs gvfs-backends gvfs-bin gvfs-fuse but my thunar still hasn't network option.

I guess it's cause old version of Thunar - I got Thunar 1.0.1

---

### Post by nothingspecial on 2011-12-29
Hmmm, I'm not familiar with thunar but perhaps you could mount them manually. Install openssh-server on both laptops. Then set it up,

```
ssh-keygen
```

```
ssh-copy-id user@ipaddress
```

change user for your username on the other laptop and ipaddress for the ip address of the other laptop.

Create a mountpoint for the other laptop eg

```
sudo mkdir /mnt/other_laptop
sudo chown -R $USER:$USER /mnt/other_laptop
```

Install sshfs and add yourself to the fuse group

```
sudo apt-get install sshfs
sudo adduser $USER fuse
```

Then make an entry in your .bashrc like this

```
lap='sshfs -o idmap=user [COLOR="Red"]user@ipaddress[/COLOR]:/ /mnt/other_laptop'
```

note: leave the first instance as 'user' (idmap=user) but change the second instance (user@ipadress) in red for your user on the other laptop. This assumes both your users are the first users created at installation. Also change ipadress for the ipaddress of the other laptop. You may also want to change the path from / (the entire file system) to something else.

Then source .bashrc ```
. ~/.bashrc
``` and try typing ```
lap
```

You should now be able to access the other laptop at /mnt/other_laptop

After you set it up you should disable password authentication . See here

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Do the same thing on the other laptop. Any time you want to mount your other laptop you just have to type ```
lap
``` or whatever you aliased the sshfs command as.

As an example, I mount my videos directory (on my server) to my Videos folder on my laptop like this

```
alias vids='sshfs -o idmap=user nothingspecial@192.168.1.16:/mnt/data/Videos ~/Videos'
```

If just have to type ```
vids
```

---

