---
title: "Making mounted file systems available on remote machines using SSH"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2010-12-19
Hello

if this a simple question I apologise, I'm using a SSH connection to a remote machine which also has ubuntu installed, my remote machine is connected to a windows server, using <places> <Network> and clicking on the server, doing this mounts the server into my remote file system

When i look around the file system of the remote machine i'm unable to make the windows server resource available to me.

I Assume it has a service file in the /dev directory, but would not know what its called or what i would have to do with it.

In the mean time i've managed to connect directily to the server from my local machine, (which is probbialy a better solution) but is it possible to see the server via my remate machine?

Thanks

---

### Post by Rhubarb on 2010-12-19
On the remote machine try looking in your /media directory.
Most mounts (such as usb drives, etc) are automatically mounted there.

Then on your local computer just ssh into the remote machine, and navigate to its /media directory and it should be sitting in there :)

I couldn't test this myself, because I'd need a windows computer to try it out on, but it should be right.

Cheers.

---

### Post by Ceiber Boy on 2010-12-19
> **Rhubarb said:**
> On the remote machine try looking in your /media directory.
Most mounts (such as usb drives, etc) are automatically mounted there.

I couldn't test this myself, because I'd need a windows computer to try it out on, but it should be right.

Cheers.

I tried looking in my /media directory but all that contains is the file to access my DVD drive!

---

### Post by spiky001 on 2010-12-19
I have found this see if thats what you need [http://industriousone.com/blog/mounting-windows-shares-linux](http://industriousone.com/blog/mounting-windows-shares-linux)

This might be better [http://www.liberiangeek.net/2010/08/mount-windows-shares-ubuntu-10-04-lucid-lynx-terminal/](http://www.liberiangeek.net/2010/08/mount-windows-shares-ubuntu-10-04-lucid-lynx-terminal/)

---

### Post by Ceiber Boy on 2010-12-19
> **spiky001 said:**
> This might be better [http://www.liberiangeek.net/2010/08/mount-windows-shares-ubuntu-10-04-lucid-lynx-terminal/](http://www.liberiangeek.net/2010/08/mount-windows-shares-ubuntu-10-04-lucid-lynx-terminal/)


this is a much better way, 

Many Thanks.

---

