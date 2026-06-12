---
title: "[HOWTO] Mount sshfs automatically at login"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by Znupi on 2009-02-20
We just got a new server and I thought it would be a good idea not to infect it with samba (samba is great, but the protocol is Microsoft proprietary cr*p). I wanted to share files with the server as seamless as possible, so I wanted to make my desktop automatically mount the ssh share on the server at login time. I found that quite a bit tricky, so I'm posting this how-to here. If it belongs in some other place, feel free to move it.

[SIZE="5"]Getting a password-less login[/SIZE]
**Note:** this is considered unsafe. It is important for you to understand exactly how safe it is. You will generate unique keys that only you will own and without them no one will be able to login to your server. But if anyone somehow finds your keys, you're done for. The reason you have to do this is because you can't tell sshfs to use a certain password.
Ok, let's do it.
[LIST=1]
[*]Generate your keys by running:
```
ssh-keygen -t rsa -b 4096
```
This will generate 4096-bit RSA keys, which are quite safe and near to impossible to bruteforce. Just press Enter at all prompts (don't enter a passkey).
[*]Append the file on your local machine from **~/.ssh/id_rsa.pub** to your server to **~/.ssh/authorized_keys**. If there's no such file, create it.
[/LIST]
At this point, you should be able to log in without a password. Just run `ssh <server>' (where <server> is your server's address) and it should automatically log in. While this looks terribly unsafe, it is not. Without the keys in ~/.ssh/id* no one will be able to log in.

[SIZE="5"]Mounting the share[/SIZE]
First, you have to install sshfs (on the desktop, of course):
```
sudo apt-get install sshfs
```
Now, run this command:
```
sshfs <user>@<server>:<srvdir> <localdir>
```
<srvdir> is the directory on the server which you want to mount. It can be "/".
<localdir> is the directory on your local machine where you want the share to be mounted. This directory has to exist and you have to be its owner. Hopefully no errors occured and you can check (with ls or a graphical file manager) if the files are where they should be.

Now, many users (like me) will be very tempted to try and make an **/etc/fstab** entry. This is wrong and will not work, because the **mount** command that parses /etc/fstab is run as root and thus the share will be mounted under the root account and you will not be able to access it. The solution I found was to add the line of code we ran earlier (sshfs ...) to ~/.bashrc.
That's it! From now on, when you log in, the shared files will be there just as if they were on your own PC.

Sources:
[AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH) - for generating RSA keys.
[SSHFS](https://help.ubuntu.com/community/SSHFS) - for how to use sshfs.

The reason why I posted this is because I saw other users with similar problems while searching for solutions, and I am hoping to help them.

**Edit:** there's [a bug](https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/298628) in Intrepid (don't know about older versions) which makes nautilus see an empty folder where the share was mounted. This is corrected by installing a newer sshfs package from Jaunty: [i386](https://launchpad.net/ubuntu/jaunty/i386/sshfs/2.1-1) [amd64](https://launchpad.net/ubuntu/jaunty/amd64/sshfs/2.1-1).

---

### Post by viktro on 2009-09-13
> The solution I found was to add the line of code we ran earlier (sshfs ...) to **~/.bashrc**.

It's better to mount sshfs in **~/.bash_profile**. It is run only when you login, while **~/.bashrc** is run whenever you open a terminal.

---

### Post by onetruejp on 2009-10-20
If you login graphically (automatically or through GDM), then you should use .profile instead of .bash_profile as Ubuntu doesn't automatically run the .bash_* scripts without editing /etc/gdm/Xsession.

[http://benakiva.blogspot.com/2006/09/ubuntu-bashprofile-does-not-get-run-at.html](http://benakiva.blogspot.com/2006/09/ubuntu-bashprofile-does-not-get-run-at.html)

---

