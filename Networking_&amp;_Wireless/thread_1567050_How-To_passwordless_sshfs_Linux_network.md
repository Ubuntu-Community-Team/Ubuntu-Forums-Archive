---
title: "How-To: passwordless sshfs Linux network"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by luceerose on 2010-09-03
I have 3 computers on a home network.
One is running Ubuntu Lucid, the other 2 are running Debian Squeeze.
My service provider block's external ssh, so I use ssh for internal networking without fear of security risk.
Up until now I've been using ssh through the gnome menu's 'Connect to Server' & bookmarking the locations with Nautilus. But I wanted to make my networking just a little bit simpler. So I did a few hours of research & came up with a great system for me. I'd like to share what I did.
Ultimately, this is what I've ended up with;
On each computer, the other computers homefolders are mounted on startup.
They sit on the desktop just like removable drives. Although I can mount them without root/sudo, I don't seem to be able to unmount them without root/sudo. I don't care, I have no reason to unmount & they unmount automatically when the other computers shutdown anyway.
I have 'Connect to' Icons to reconnect when the other computer becomes unmounted from being restarted or shutdown.

It's all very simple. It means I have one-click access to any computer from any other computer without the need for passwords, menus or typing.
See attached screenshot to see the simplicity.
If you like it, here's what to do;
(replace <username> with your username, etc...)
1) Make sure you have installed openssh-client, openssh-server & sshfs. Skip this step if you know for sure they're already installed.
```

sudo apt-get install openssh-client openssh-server sshfs

```
2) Generate ssh keys. This generates a key for the computer you are on & copies it to any computers you wish to connect to.
You need to generate a key for every computer on your network.;
```

ssh-keygen

```
then
```

ssh-copy-id <other computer's username>@<other computer's ip>

```
3) Set up sshfs.
Note: Every guide I found said to do 'sudo chown **root**:fuse /dev/fuse'. But for some reason, sometimes the network folders would hang. So I did a chown for the regular user as well and I haven't had any problems since. Don't really understand why.
```

sudo modprobe fuse
sudo adduser <username> fuse
sudo chown root:fuse /dev/fuse
sudo chown <username>:fuse /dev/fuse
sudo chmod +x /dev/fuse

```
IMPORTANT: After completing step 3, You must Log Out & back In before the connection in Step 5 will work.

4) Create the folders you will be mounting the other computers into. I have used a ~/Network/ folder with subfolders for each computer. You can call these folders whatever you want.
```

mkdir Network && cd Network
mkdir <whatever name>

```
5) First time connection to test (optional);
```

sshfs <username>@<other computer's ip>:/home/<username> ~/Network/<whatever name>

```
6) Now for the main convenience:
Startup Applications & 'Connect to' Icons.
These both work on the same command;
```

sshfs <username>@<ipaddress to connect to>:/home/<username> /home/<username>/Network/<whatever name>

```

---

