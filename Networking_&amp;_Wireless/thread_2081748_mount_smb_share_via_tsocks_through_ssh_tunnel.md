---
title: "mount smb share via tsocks through ssh tunnel"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by azzid on 2012-11-07
I'm trying to mount a smb share on another private network.

I've got ssh access to a internet facing machine on the remote network with the smb server.

I set up a ssh tunnel able to act as a SOCKS proxy:
```
ssh -l user -D 1080 sshserver.remote.net -N -T
```

After that I try to mount the smb share using tsocks, but it fails:
```
user@myserver:~$ tsocks sudo mount.cifs //172.16.51.3/share mount_target_folder -o user=$user,pass=$pass --verbose
mount.cifs kernel mount options: ip=172.16.51.3,unc=\\172.16.51.3\share,,ver=1,user=$user,pass=********
mount error(115): Operation now in progress

```

I've configured a path like this in tsocks.conf:
```
path {
	reaches = 172.16.0.0/255.255.0.0
	server = 127.0.0.1
	server_type = 5
}

```

Should this not work?

If I do the mount from the ssh server directly it works:
```
user@sshserver.remote.net:~$ sudo mount.cifs //172.16.51.3/share mount_taget_folder -o user=$user,pass=$pass --verbose
mount.cifs kernel mount options: ip=172.16.51.3,unc=\\172.16.51.3\share,,ver=1,user=$user,pass=********
user@sshserver.remote.net:~$ mount | grep mount_taget_folder
//172.16.51.3/share on /home/user/mount_taget_folder type cifs (rw)

```

Also, if I configure firefox to use localhost:1080 as a proxy server I am able to access http-resources on the remote network.

So the smb server and the ssh tunnel both seem to work allright.
The tsocks+smb combination however seems not to...

---

### Post by azzid on 2012-11-07
Found a workaround:
```
user@myserver:~$ ssh -l user -L 1139:172.16.51.3:139 sshserver.remote.net -N -T &
user@myserver:~$ sudo smbmount //localhost/share mount_target_folder -o user=$user,pass=$pass,port=1139
```

But I'd still very much like to know why tsocks won't work if anyone has any ideas...

---

